# 10 - Hybrid Autopilot OOBE Validation

## Goal
Run an end-to-end **Hybrid Autopilot** deployment from OOBE and confirm the device successfully:
- detects the Autopilot deployment profile
- processes Offline Domain Join (ODJ)
- completes Hybrid Microsoft Entra ID Join
- enrolls into Intune
- creates the computer object in the correct AD OU

---

## Why this matters
Hybrid Autopilot depends on multiple components (SCP, GPO, Intune Connector, deployment profile, ESP).
A configuration may appear correct in Intune but still fail during OOBE if one dependency is misconfigured.

This step validates the full provisioning pipeline across:
- Active Directory
- Microsoft Entra ID
- Microsoft Intune

---

## Prereqs
- Steps 01–09 completed
- Autopilot deployment profile assigned
- Domain Join (ODJ) profile assigned
- ESP assigned to `GRP-Autopilot-Hybrid-Join-Lab`
- Intune Connector shows **Active**
- Windows 11 VM has internet connectivity

---

## What was done
- Confirmed Autopilot device record shows Assigned = Yes
- Reset the Windows 11 VM back to OOBE
- Signed in with synced Entra test user
- Observed ESP behavior during provisioning
- Validated Hybrid join state and device enrollment

---

## Validation
- `dsregcmd /status` shows:
  - DomainJoined : YES
  - AzureAdJoined : YES
- Computer object exists in:
  - `OU=Autopilot Devices,OU=Lab Devices,DC=jmcnairtech,DC=local`
- Device appears in Intune as managed
- (Optional) Entra device record shows Hybrid joined

---

## Screenshots to Capture (Step 10)

Minimum:
- `10-autopilot-device-assigned.png`
- `10-oobe-autopilot-detected.png`
- `10-esp-in-progress.png`
- `10-dsregcmd-status.png`
- `10-ad-computer-object-ou.png`
- `10-intune-device-record.png`

Optional:
- `10-intune-connector-active.png`
- `10-entra-device-hybrid-joined.png`

---

## Notes
- Hybrid Autopilot may take longer than cloud-only provisioning due to ODJ processing and domain join timing.
- If provisioning appears stalled, validate Connector health, OU DN accuracy, and ESP configuration first.

---

## Done Criteria (to move to Step 11)
- Autopilot OOBE completes successfully
- `dsregcmd /status` confirms Hybrid join
- Computer object exists in correct OU
- Device appears in Intune as managed
