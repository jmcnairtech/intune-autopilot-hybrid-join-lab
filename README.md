# Intune Autopilot + Hybrid Microsoft Entra ID Join – Enterprise Endpoint Lifecycle Lab

This repository documents a full enterprise endpoint lifecycle simulation using:

- Active Directory Domain Services (AD DS)
- Microsoft Entra ID (Hybrid Join)
- Microsoft Intune
- Windows Autopilot (Hybrid Microsoft Entra ID Join)
- Offline Domain Join (ODJ)
- Security baseline configuration
- Win32 application packaging and deployment
- Compliance policies
- Conditional Access enforcement
- Structured troubleshooting methodology

The lab replicates how a modern enterprise provisions, secures, and manages Windows endpoints in a hybrid identity environment.

---

## Lab Environment

- Hyper-V
- Windows Server Domain Controller (`jmcnairtech.local`)
- Windows 11 Enterprise VM (Autopilot test device)
- Microsoft Entra tenant with Intune

---

## Project Objectives

This project demonstrates practical, hands-on understanding of:

- Hybrid identity architecture (AD DS + Microsoft Entra ID)
- Service Connection Point (SCP) configuration
- GPO-based automatic device registration
- Intune Connector for Active Directory (ODJ)
- Windows Autopilot (Hybrid Join deployment model)
- Enrollment Status Page (ESP) configuration
- Security baseline implementation (BitLocker / Defender / WHfB if used)
- Win32 application packaging and deployment (.intunewin)
- Device compliance configuration
- Conditional Access enforcement based on device state
- Cross-system validation and troubleshooting (AD / Entra / Intune)

The focus is lifecycle management, not just configuration.

---

## Provisioning & Management Flow Simulated
```
Windows 11 Device (OOBE)
↓
Autopilot Device Registration (HWID)
↓
Autopilot Deployment Profile Assignment
↓
Offline Domain Join (Intune Connector)
↓
Computer Object Created in Active Directory
↓
Device Reboot
↓
Hybrid Microsoft Entra ID Join Finalized
↓
Intune Enrollment
↓
Enrollment Status Page Processing
↓
Baseline Security Policies Applied
↓
Win32 Applications Deployed
↓
Compliance Evaluation
↓
Conditional Access Enforcement
```


---

## Repository Structure

### `/lab-setup`

Step-by-step implementation of:

- Infrastructure prerequisites
- AD OU and user structure
- Entra Connect + SCP configuration
- GPO hybrid registration
- Intune Connector (ODJ)
- Autopilot device registration
- Deployment profile configuration
- Domain Join profile (ODJ)
- Enrollment Status Page (ESP)
- Baseline configuration profiles
- Win32 app deployment
- Compliance + Conditional Access
- Validation & troubleshooting

### `/architecture-diagrams`

Logical identity and provisioning flow diagrams.

### `/screenshots`

Evidence screenshots referenced throughout the lab.

---

## Skills Demonstrated

- Hybrid identity integration (AD DS + Entra ID)
- SCP discovery configuration
- Automatic device registration via GPO
- ODJ architecture using Intune Connector
- Autopilot Hybrid Join deployment design
- Enrollment Status Page tuning for hybrid scenarios
- BitLocker policy deployment and validation
- Windows Hello for Business configuration (if implemented)
- Microsoft Defender baseline configuration
- Win32 packaging using `IntuneWinAppUtil`
- Detection rule and requirement rule design
- Compliance policy configuration
- Conditional Access requiring compliant devices
- `dsregcmd` validation and device state analysis
- Structured hybrid troubleshooting methodology

---

## Validation Philosophy

Hybrid provisioning and endpoint lifecycle management are validated across three systems:

- Active Directory  
- Microsoft Entra ID  
- Microsoft Intune  

Validation methods include:

- `gpresult`
- `dsregcmd /status`
- AD computer object verification
- Intune device state confirmation
- Entra device registration state
- Compliance state validation
- Conditional Access behavior testing

---

## Scope

This lab focuses on realistic hybrid endpoint provisioning and management patterns found in enterprise environments.

It demonstrates:

- Identity plumbing
- Provisioning control
- Security enforcement
- Application deployment
- Device compliance governance
- Troubleshooting across identity boundaries

---

## Blog Write-Up

A detailed walkthrough with screenshots and expanded explanations will be published at:

https://jmcnairtech.com
