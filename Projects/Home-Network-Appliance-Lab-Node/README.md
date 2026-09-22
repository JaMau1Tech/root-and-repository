# Home Network Appliance & Lab Node

This project documents converting a repurposed Lenovo 300e 2nd Gen ("MintJammer," previously documented in [HWD-2026-002](../Hardware-Help-Desk/TICKET-lenovo-300e-touchpad-repair.md)) into a dual-purpose stationary machine: a household DNS-filtering appliance and an isolated sandbox for hands-on Linux administration, scripting, and intentional break/fix practice.

The device is stationary (its built-in touchpad is non-functional per HWD-2026-002) and standalone — not joined to the `jamaursec.lab` Active Directory domain used in the numbered Home Lab sequence — so that experimentation on this machine carries no risk to the AD lab environment.

---

# Project Status

**Status:** ⏳ Planned — Not Started

---

# Objective

- Deploy AdGuard Home as a household DNS-filtering appliance
- Assign a static IP reservation so the appliance is reliably reachable on the home network
- Establish an isolated layer (containers or equivalent) for experimentation, separate from the appliance service, so testing does not risk taking down household DNS
- Use the isolated layer for hands-on practice: shell scripting/automation, firewall rule configuration (UFW/iptables), and deliberate break/fix exercises
- Document the reasoning behind separating a production-style service from an experimentation environment on constrained, single-host hardware

---

# Project Structure

```text
Home-Network-Appliance-Lab-Node/
├── README.md
├── docs/
│   ├── adguard-setup.md
│   └── isolation-strategy.md
└── screenshots/
    └── README.md
```

---

# Tools Used (Planned)

- Linux Mint Cinnamon (existing install)
- Docker
- AdGuard Home
- `ufw` / `iptables`
- Shell scripting (Bash)

---

# Planned Approach

AdGuard Home will run as the stable, always-on service handling DNS filtering for the home network. Experimentation — scripting practice, firewall rule changes, and deliberate break/fix scenarios — will happen in a separate, isolated layer (containerized or otherwise sandboxed) so a failed experiment affects only that layer, not the DNS service the household depends on. This mirrors a real sysadmin practice: keeping production services isolated from development/test environments, even on a single physical host.

---

# Skills to Practice

- DNS-level filtering/appliance deployment
- Docker container isolation
- Static IP reservation and network appliance configuration
- Shell scripting and automation
- Firewall rule configuration (UFW/iptables)
- Service isolation / blast-radius containment on constrained hardware
- Deliberate break/fix troubleshooting methodology
