# IT Service Ticket

**Ticket #:** HWD-2026-001
**Date Opened:** September 17, 2026
**Date of Service:** September 17, 2026
**Status:** 🟡 In Progress — Pending Parts

---

## Device Information

| Field | Detail |
|---|---|
| Device Type | Laptop |
| Make / Model | ASUS Vivobook 15 (F1502ZA / X1502ZA family) |
| Device Owner | Teacher's Son |
| Reported By | Teacher residing at our institution & Mr. Delamarter (Instructor) |
| Technician(s) | Ja'Maurian Williams, Michael Brown, Jaden Humberton |

---

## Reported Issue

Customer stated that when her son opened the laptop, the display would not show any image — however, the keyboard backlight indicated the unit was powered on.

---

## Diagnostic Steps

1. **External display test** — Connected the unit to an external monitor and powered it on. Video output projected successfully to the external monitor.
   - **Conclusion:** Ruled out the display port and GPU/motherboard video output as the cause, since video signal was confirmed functional.

2. **Physical inspection during handling** — While closing the laptop lid during testing, the screen became detached, prompting further physical inspection.

3. **Bottom panel disassembly** — Opened the bottom panel of the chassis to inspect internal components.
   - **Finding:** The internal display cable was visibly pinched at the hinge area.

4. **Reference video followed** — Located and followed a disassembly video for the ASUS Vivobook 15 (X1502) series to safely proceed with further teardown.

5. **Front bezel removal** — Removed the front display bezel per the referenced disassembly procedure to gain direct access to the display cable and its connectors.
   - **Finding:** Confirmed the display cable itself was damaged and required replacement (not just a reseating).

---

## Root Cause

Internal display (eDP/LVDS) cable damaged from being pinched at the hinge flex point, consistent with the reported symptom pattern (display failure tied to opening/closing the lid).

---

## Resolution / Action Taken

- Diagnosed root cause as a damaged display cable, not the external port or GPU.
- Replacement cable ordered by instructor.
- Repair currently on hold pending parts arrival.

## Next Steps

- [ ] Receive replacement display cable
- [ ] Reinstall/replace display cable
- [ ] Reassemble unit (front bezel → bottom panel)
- [ ] Power-on and functional test (including lid open/close cycle to confirm fix holds)
- [ ] Return unit to customer

---

## Notes / Lessons Learned

- Testing with an external monitor is a fast, non-invasive way to isolate a display port/GPU issue from an internal panel or cable issue before opening the chassis.
- A symptom that correlates specifically with the lid opening/closing motion is a strong early indicator of a hinge-area cable problem rather than a port or panel failure.
