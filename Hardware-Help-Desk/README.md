# Hardware / Help-Desk Ticket Log

Running index of hands-on hardware repair and help-desk tickets documented in this repo. Each entry links to its full ticket file.

## Ticket Numbering Convention

`HWD-YYYY-###`
- `HWD` = Hardware / Help-Desk category
- `YYYY` = year the ticket was opened
- `###` = zero-padded sequential number, resetting each year (e.g., `HWD-2026-001`, `HWD-2026-002`, ...)
| Ticket # | Date Opened | Device | Issue Summary | Status | Ticket File |
|---|---|---|---|---|---|
| HWD-2026-001 | Sept 17, 2026 | ASUS Vivobook 15 (F1502ZA/X1502ZA) | No display output on lid open; keyboard powers on | 🟡 In Progress — Pending Parts | [TICKET-asus-vivobook-display-repair.md](./TICKET-asus-vivobook-display-repair.md) |
| HWD-2026-002 | Aug 24, 2026 | Lenovo 300e 2nd Gen (82GK) | Touchpad non-functional after fresh Linux Mint install | 🟢 Closed — Workaround Applied | [TICKET-lenovo-300e-touchpad-repair.md](./TICKET-lenovo-300e-touchpad-repair.md) |
| HWD-2026-003 | Sept 20, 2026 | HP Laptop 15-dy2xxx (446R4UA#ABA) | New NVMe drive not detected in Windows Setup (Intel VMD driver missing) | 🟢 Closed — Resolved | [TICKET-hp-15-nvme-vmd-driver.md](./TICKET-hp-15-nvme-vmd-driver.md) |
| HWD-2026-004 | Sept 21, 2026 | HP t620 Thin Client (G4U29UA#ABA) | No power — dead AC adapter; storage upgrade for Xubuntu install; onboard Wi-Fi unsupported by kernel driver | 🟢 Closed — Resolved | [TICKET-hp-t620-charger-storage-upgrade.md](./TICKET-hp-t620-charger-storage-upgrade.md) |

---

## Status Key

- 🟢 Resolved / Closed
- 🟡 In Progress
- 🔴 Blocked / Awaiting Parts or Info
- ⚪ Open / Not Started
