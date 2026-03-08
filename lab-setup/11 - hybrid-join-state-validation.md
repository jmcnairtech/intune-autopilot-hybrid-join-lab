# 11 - hybrid-join-state-validation

## Goal
Validate that the Autopilot‑provisioned device has successfully completed the **Hybrid Microsoft Entra ID Join** process and is now fully recognized by:
- Active Directory (on‑prem)
- Microsoft Entra ID
- Microsoft Intune

This confirms the identity trust chain is functioning end‑to‑end after OOBE.

---

## Why this matters
Hybrid Join finalization occurs *after* Autopilot OOBE completes. Even if ESP succeeded, the device may still fail to:
- Apply the Offline Domain Join (ODJ) blob
- Register with on‑prem AD
- Sync its identity to Entra ID
- Obtain an Azure AD Primary Refresh Token (PRT)
- Complete MDM enrollment

This step ensures the device is properly joined to both directories and ready for Conditional Access, compliance policies, and app deployments.

---

## Prereqs
- Step 10 completed successfully
- Device has rebooted into the user desktop
- Network connectivity to domain controller + internet
- Azure AD Connect sync is healthy
- Intune Connector is Active

---

## What was done
- Logged into the Autopilot‑provisioned VM
- Opened an elevated Command Prompt
- Ran `dsregcmd /status` to validate join state
- Checked AD DS for the computer object
- Verified device presence and join type in Intune

---

## Validation

### Hybrid Join State (`dsregcmd /status`)
Expected values:
- **DomainJoined : YES**
- **AzureAdJoined : YES**
- **AzureAdPrt : YES**
- **TenantName** matches the lab tenant
- **DeviceId** populated

These values confirm the device is fully Hybrid Joined and capable of SSO + Conditional Access evaluation.

---

### Active Directory Object
In **Active Directory Users and Computers**, confirm:
- Computer object exists
- Located in the correct OU:  
  `OU=Autopilot Devices,OU=Lab Devices,DC=jmcnairtech,DC=local`
- Timestamp aligns with Autopilot deployment
- Object is **Enabled**

---

### Intune Enrollment
In **Intune Admin Center → Devices → Windows**:
- Device appears as **Managed**
- **MDM** = Microsoft Intune
- **Join Type** = Hybrid Azure AD Joined
- **Primary User** assigned
- **Compliance** = Pending or Compliant

---

## Screenshots to Capture (Step 11)

Minimum:
- `11-dsregcmd-status.png`
- `11-ad-computer-object.png`
- `11-intune-device-hybrid-joined.png`

Optional:
- `11-entra-device-record.png`
- `11-intune-mdm-details.png`

---

## Notes
- Hybrid Join may take several minutes after first login to fully register.
- If `AzureAdPrt` = NO, check time sync, user sign‑in method, and Entra connectivity.
- If the device does not appear in Intune, validate MDM enrollment settings and ESP behavior.

---

## Done Criteria (to move to Step 12)
- `dsregcmd /status` confirms Hybrid Join
- AD DS computer object exists in correct OU
- Device appears in Intune as Hybrid Azure AD Joined
- Azure AD PRT is issued
