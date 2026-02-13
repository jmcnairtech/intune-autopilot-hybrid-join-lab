# Lab Setup – Hybrid Autopilot Build Steps

This directory contains the staged implementation of a Hybrid Microsoft Entra ID Join + Windows Autopilot lab environment.

Each file represents a milestone in building a working Hybrid Autopilot provisioning pipeline in a controlled Hyper-V lab.

The sequencing mirrors enterprise rollout logic: identity foundation → hybrid registration → ODJ plumbing → Autopilot targeting → provisioning control → validation.

---

## Step Index

### 00 – Prereqs and Lab Environment  
`00-prereqs-and-lab-environment.md`

Defines:
- Accounts and licensing requirements
- Hyper-V networking and NAT configuration
- DNS assumptions
- VM layout
- Naming conventions

Establishes the foundational lab infrastructure.

---

### 01 – On-Prem AD, DNS, and OU Structure  
`01-onprem-ad-dns-ou-structure.md`

Builds:
- Active Directory OU structure
- Test users with Entra-compatible UPNs
- DNS validation for domain and internet resolution

Prepares identity structure for hybrid integration.

---

### 02 – Entra Connect Device Options + SCP  
`02-entra-connect-device-options-scp.md`

Configures:
- Microsoft Entra Connect device options
- Service Connection Point (SCP) for hybrid join discovery

Enables domain-joined devices to discover the Entra tenant.

---

### 03 – GPO Device Registration (Hybrid Join)  
`03-gpo-device-registration-hybrid-join.md`

Introduces:
- Device registration policy configuration
- Validation of domain join state prior to automatic registration

---

### 04 – GPO Automatic Device Registration  
`04-gpo-automatic-device-registration.md`

Enables:
- Automatic device registration via Group Policy
- Validation using `gpresult` and `dsregcmd /status`

Triggers hybrid registration behavior for domain-joined devices.

---

### 05 – Intune Connector for Active Directory (ODJ)  
`05-intune-connector-for-ad-odj.md`

Installs and validates:
- Intune Connector for Active Directory
- ODJ blob generation capability

Bridges cloud provisioning with on-prem Active Directory.

---

### 06 – Register Windows 11 VM as an Autopilot Device (HWID)  
`06-autopilot-device-registration-hwid.md`

Covers:
- Hardware hash (HWID) collection
- Import into Windows Autopilot devices

Enables Autopilot profile targeting.

---

### 07 – Autopilot Device Group and Hybrid Deployment Profile  
`07-autopilot-device-group-and-hybrid-profile.md`

Creates:
- Dynamic Autopilot device group (ZTDId rule)
- Hybrid Microsoft Entra ID Join deployment profile

Controls OOBE provisioning behavior.

---

### 08 – Domain Join Configuration Profile (ODJ)  
`08-domain-join-profile-odj.md`

Defines:
- Intune Domain Join profile
- Target OU for computer object creation
- Assignment to Autopilot device group

Enables Offline Domain Join during Autopilot OOBE.

---

### 09 – Enrollment Status Page (ESP) Configuration  
`09-enrollment-status-page-esp.md`

Configures:
- ESP behavior for Hybrid Autopilot
- Non-blocking provisioning settings for lab reliability

Prepares environment for full end-to-end Autopilot testing.

---

### 10 – Hybrid Autopilot OOBE Execution and Validation  
`10-hybrid-autopilot-oobe-validation.md`

Executes:
- Device reset to OOBE
- Autopilot provisioning flow
- ODJ processing
- Hybrid join confirmation

Validates device state using:
- `dsregcmd /status`
- Active Directory computer object verification
- Intune device enrollment confirmation

---

### 11 – Validation and Troubleshooting  
`11-validation-and-troubleshooting.md`

Documents:
- Common Hybrid Autopilot failure scenarios
- ODJ errors
- ESP timeouts
- SCP misconfiguration
- Device object mismatches

Provides structured troubleshooting methodology across:

- Active Directory
- Microsoft Entra ID
- Microsoft Intune

---

## Validation Philosophy

Hybrid provisioning must be validated across three systems:

- Active Directory  
- Microsoft Entra ID  
- Microsoft Intune  

The lab emphasizes:

- Clear goal definition per step
- Configuration transparency
- Measurable validation checkpoints
- Screenshot evidence
- Defined “Done Criteria”

---

## End State

Upon completion, the lab supports:

- Hybrid Microsoft Entra ID Join
- Offline Domain Join via Intune Connector
- Windows Autopilot provisioning
- Controlled OOBE experience via ESP
- Structured hybrid troubleshooting
