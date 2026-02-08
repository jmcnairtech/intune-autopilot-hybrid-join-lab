# 06 - Register Windows 11 VM as an Autopilot Device (HWID)

## Goal
Register the Windows 11 lab VM as a **Windows Autopilot device** by collecting and importing its **hardware hash (HWID)** into Intune.

## Why this matters
Windows Autopilot profiles only apply to devices that are registered as Autopilot devices.
Importing the HWID creates an Autopilot record that allows Intune to:
- target the device with a **Hybrid Autopilot deployment profile**
- apply a **Domain Join (ODJ)** configuration during OOBE

This step bridges the gap between **hybrid identity readiness** and **Autopilot-driven provisioning**.

---

## Prereqs
- Steps 01–05 completed
- Intune Connector for Active Directory shows **Active**
- Windows 11 VM has internet access
- Intune permissions to import Autopilot devices

---

## What was done

- Collected the Windows Autopilot hardware hash (HWID) from the Windows 11 VM
- Imported the HWID into Intune under **Windows Autopilot devices**
- Verified the device appears in the Autopilot device list

---

## Validation

- HWID successfully generated on the Windows 11 VM
- Device appears in **Windows Autopilot devices** in Intune
- Import completed without errors
- Device shows **Assigned: No** prior to profile assignment

---

## Screenshots to Capture (Step 06)

Minimum:
- `06-hwid-export-powershell.png`
  - PowerShell output showing successful HWID export
- `06-autopilot-device-imported.png`
  - Autopilot device visible in Intune

Optional:
- `06-autopilot-device-details.png`
  - Device details page showing assignment state

---

## Notes
- The Windows 11 VM was already Hybrid Azure AD joined at the time of HWID collection.
- Autopilot testing will require resetting the VM back to **OOBE** after profile assignment.
- Recreating the VM may change the hardware hash; wiping the existing VM is preferred for repeat testing.

---

## Done Criteria (to move to Step 07)
- HWID imported successfully
- Device visible in Autopilot devices list
- No import errors
