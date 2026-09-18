# Shutdown Diagnosis

This document records the investigation into a reported ~2-minute post-boot shutdown observed during the Windows setup attempts, and the post-install hardening steps performed after the device was reprovisioned with Linux Mint.

---

# Issue 1 - Unexpected Shutdown ~2 Minutes After Boot

## Problem

The device consistently powered off approximately two minutes after reaching the post-boot screen during the Windows setup attempts.

## Investigation

Three hypotheses were considered: battery health degradation, thermal shutdown, and a marginal AC adapter/DC jack connection. Battery and thermal were tested directly.

### Battery Health

```text
$ upower -i $(upower -e | grep BAT)
energy-full:         50.9 Wh
energy-full-design:  57.02 Wh
charge-cycles:       345
capacity:            89.2669%
state:               discharging
```

89% capacity at 345 charge cycles is healthy for an 8-year-old battery. Meaningful degradation is typically flagged well below 80%.

**Ruled out.**

### Thermal

```text
$ sudo apt install lm-sensors -y
$ sudo sensors-detect --auto
Driver `coretemp`:
  * Chip `Intel digital thermal sensor` (confidence: 9)

$ sensors
coretemp-isa-0000
Package id 0:  +36.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +36.0°C
Core 1:        +34.0°C
Core 2:        +35.0°C
Core 3:        +36.0°C
thinkpad-isa-0000
fan1:          0 RPM
CPU:           +36.0°C
nvme-pci-3e00
Composite:     +25.9°C  (high = +74.8°C, crit = +79.8°C)
```

All temperatures were in idle range, well below throttle or critical thresholds. The fan sitting at 0 RPM is expected behavior at this temperature, not a fault.

**Ruled out.**

### System Logs

```text
$ journalctl -b -1 -p err
```

Reviewed errors from the previous boot session. Findings were limited to a Bluetooth feature-read failure, a SAP driver init failure, an expected live-USB checksum service failure, and a couple of mistyped-password screensaver auth failures — nothing indicating a kernel panic, ACPI power-loss event, or thermal trip.

## Resolution

The device ran an extended live troubleshooting session (multiple `apt install` commands, sensor detection, firewall configuration) with zero unexpected shutdowns.

## Result

Battery and thermal causes were both ruled out with direct evidence. The shutdown has not reproduced under sustained real-world Linux use. The most plausible explanation is that it was specific to Windows Setup's load pattern (OOBE driver installation and disk I/O are heavier than idle desktop use), possibly combined with a marginal AC adapter/DC jack connection that only manifested under that load spike. This was not independently confirmed, since re-testing under Windows was not a productive use of time, but the issue is not present under how the device is actually being used now.

**Status:** Monitoring, not actively blocking. If the shutdown recurs under normal Linux use, next steps would be an AC adapter swap test and a `powertop` power-draw check.

---

# Issue 2 - Firewall Disabled by Default

## Problem

Linux Mint ships with UFW installed but inactive by default.

## Steps Attempted

```text
$ sudo ufw status
Status: inactive

$ sudo ufw enable
Firewall is active and enabled on system startup

$ sudo ufw default deny incoming
Default incoming policy changed to 'deny'

$ sudo default allow outgoing
sudo: default: command not found

$ sudo ufw default allow outgoing
Default outgoing policy changed to 'allow'

$ sudo apt install gufw
gufw is already the newest version (24.04.0-2)
```

## Resolution

UFW was enabled with a deny-incoming / allow-outgoing baseline. The `sudo default allow outgoing` line was a typo (`default` is a `ufw` subcommand, not a standalone command); re-running it with `ufw` in front resolved it. `gufw` was already present, giving the end user a GUI toggle without needing the terminal.

## Result

Firewall active with a sane default baseline.

---

# Issue 3 - Wireless Driver Verification

## Problem

Confirming the correct driver was bound for the device's wireless card (Intel Wireless 8265/8275), since some laptop wireless chipsets need a proprietary driver installed manually.

## Steps Attempted

```text
$ lspci -k | grep -A 3 -i network
3d:00.0 Network controller: Intel Corporation Wireless 8265 / 8275 (rev 78)
	Subsystem: Intel Corporation Dual Band Wireless-AC 8265 [Windstorm Peak]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
```

## Result

`iwlwifi` was already bound and active. Intel wireless cards use this in-kernel driver natively on Linux, so no further action was needed.

---

# Skills Practiced

- Systematic troubleshooting (hypothesis → test → verify → document)
- Battery health diagnostics (`upower`)
- Thermal diagnostics (`lm-sensors`)
- System log review (`journalctl`)
- Firewall configuration (`ufw`, `gufw`)
- Driver verification (`lspci`)

---

# Lessons Learned

- Ruling out causes with direct evidence converts an unexplained intermittent symptom into a confirmed non-issue under current use, which is the practically useful outcome even without full certainty on the original trigger.
- Linux Mint's firewall is present but inactive out of the box; enabling it is a manual first step, not a default.
- Intel wireless chipsets generally work out of the box on Linux through the in-kernel `iwlwifi` driver, unlike some other vendors' cards.
