# Isolation Strategy

**Status:** ⏳ Planned — Not Started

This document will cover how the experimentation/lab layer on MintJammer is kept isolated from the AdGuard Home appliance service, so that break/fix practice, scripting, and firewall testing cannot disrupt household DNS.

---

## Planned Scope

- Define the isolation boundary (e.g., separate Docker containers/networks, a dedicated user account and directory scope, or a separate OS-level sandbox — approach to be finalized during implementation)
- Document how the AdGuard Home container/service is protected from changes made in the experimentation layer
- Document the recovery process if an experiment does affect the host (e.g., snapshot/backup strategy, reinstall plan)
- Record the reasoning behind the chosen isolation method, including trade-offs considered

## Notes

This section is a placeholder outline only. It will be filled in with the actual isolation method chosen, configuration details, and reasoning once implemented — consistent with this repository's standard of not documenting steps or results before they've actually been completed.
