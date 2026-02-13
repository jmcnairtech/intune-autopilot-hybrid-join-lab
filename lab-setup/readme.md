# Lab Setup – Hybrid Autopilot + Enterprise Endpoint Lifecycle (Intune)

This directory contains the step-by-step implementation of a Hybrid Microsoft Entra ID Join + Windows Autopilot lab environment, expanded to include enterprise endpoint management capabilities (security baseline, app deployment, compliance, and Conditional Access).

The sequencing mirrors enterprise rollout logic:

Identity foundation → hybrid registration → ODJ plumbing → Autopilot targeting → provisioning control → baseline configuration → app deployment → compliance → Conditional Access → validation/troubleshooting.

---

## Step Index

### 00 – Prereqs and Lab Environment  
`00-prereqs-and-lab-environment.md`

Defines:
- Accounts and licensing requirements
- Hyper-V networking and NAT assumptions
- DNS requirements and forwarders
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

### 03 – Domain Join the Windows 11 VM (Lab Client)  
`03-domain-join-win11-vm.md`

Validates:
- Domain join capability
- DNS pointing to the Domain Controller
- AD computer object creation

Prepares the client for GPO-based hybrid registration.

---

### 04 – GPO Automatic Device Registration (Hybrid Join)  
`04-gpo-automatic-device-registration.md`

Enables:
- Automatic device registration via Group Policy

Validates:
- Policy application via `gpresult`
- Hybrid join state via `dsregcmd /status`

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

Prepares the environment for full end-to-end Autopilot testing.

---

### 10 – Hybrid Autopilot OOBE Execution and Validation  
`10-hybrid-autopilot-oobe-validation.md`

Executes:
- Device reset to OOBE
- Autopilot provisioning flow
- ODJ processing and reboot
- Hybrid join confirmation

Validates device state using:
- `dsregcmd /status`
- Active Directory computer object verification
- Intune enrollment confirmation

---

### 11 – Baseline Configuration Profiles (Security + Endpoint Settings)  
`11-baseline-configuration-profiles.md`

Implements baseline controls such as:
- BitLocker disk encryption policy (recovery keys escrowed)
- Windows Hello for Business configuration (if used)
- Microsoft Defender baseline settings (minimum viable hardening)

Validates baseline enforcement on the enrolled device.

---

### 12 – Win32 App Packaging and Deployment  
`12-win32-app-packaging-deployment.md`

Covers:
- Converting an installer to `.intunewin`
- Creating install/uninstall commands
- Detection rules and requirement rules
- Deployment as Required / Available
- Installation verification and troubleshooting

---

### 13 – Compliance Policy and Conditional Access  
`13-compliance-and-conditional-access.md`

Implements:
- Device compliance policies (e.g., BitLocker required)
- Conditional Access requiring compliant devices for access

Validates:
- Compliant access allowed
- Non-compliant access blocked (controlled test)

---

### 14 – Validation and Troubleshooting  
`14-validation-and-troubleshooting.md`

Documents:
- End-to-end validation checks across AD / Entra / Intune
- Common Hybrid Autopilot failure scenarios:
  - ODJ failures
  - ESP timeouts
  - SCP / discovery issues
  - Device object mismatch
  - Connector offline scenarios
- Structured troubleshooting workflow and evidence collection

---

## Validation Philosophy

Hybrid provisioning and lifecycle management are validated across three systems:

- Active Directory  
- Microsoft Entra ID  
- Microsoft Intune  

Each step includes:
- Goal
- Configuration summary
- Validation checkpoints
- Required screenshots
- Clear “Done Criteria”

---

## End State

Upon completion, the lab supports:

- Hybrid Microsoft Entra ID Join
- Offline Domain Join via Intune Connector
- Windows Autopilot provisioning with controlled ESP behavior
- Baseline endpoint security configuration (BitLocker/Defender/WHfB as applicable)
- Win32 application packaging and deployment
- Compliance enforcement and Conditional Access validation
- Structured troubleshooting and repeatable validation methodology
