# Intune Autopilot + Microsoft Entra Hybrid Join Lab (Hyper-V)

This repository documents a hands-on enterprise simulation of the Windows provisioning lifecycle using:

- Windows Autopilot  
- Microsoft Intune  
- Microsoft Entra ID (Hybrid Join)  
- Active Directory Domain Services  

This project replicates a real-world hybrid endpoint modernization scenario, including identity integration, Autopilot provisioning, Offline Domain Join (ODJ), compliance enforcement, and structured troubleshooting.

Lab Environment:

- Hyper-V  
- Windows Server Domain Controller (`mcnairtech.local`)  
- Windows 11 Enterprise client VM  

---

## Project Objectives

This lab demonstrates practical understanding of:

- Hybrid identity (AD DS + Microsoft Entra ID)  
- Windows Autopilot (Hybrid Azure AD Join) provisioning flow  
- Offline Domain Join (ODJ) using the Intune Connector for Active Directory  
- Enrollment Status Page (ESP) configuration and tuning  
- Device configuration profiles and compliance enforcement  
- Conditional Access requiring compliant devices  
- Win32 application packaging and deployment  
- Enterprise troubleshooting across Active Directory / Entra ID / Intune  

The focus of this project is identity plumbing, provisioning lifecycle validation, and operational troubleshooting — not just configuration.

---

## Skills Demonstrated

- Microsoft Intune device configuration and policy deployment  
- Windows Autopilot (Hybrid Azure AD Join) architecture  
- Offline Domain Join (ODJ) with Intune Connector  
- Active Directory + Entra ID hybrid identity integration  
- Service Connection Point (SCP) configuration  
- GPO-based device registration  
- Conditional Access policy enforcement  
- Device compliance management  
- Win32 app packaging (IntuneWin) and deployment  
- Cross-platform troubleshooting methodology (AD / Entra / Intune)

---

## Architecture Scope

The lab includes:

- Entra Connect configuration (device options + SCP)
- Hybrid join discovery via Service Connection Point
- GPO device registration configuration
- Intune Connector for Active Directory (ODJ processing)
- Autopilot device registration and deployment profile (Hybrid Join)
- Domain Join profile with OU targeting
- Enrollment Status Page configuration
- Baseline device configuration policies
- Compliance policies
- Conditional Access enforcement
- Win32 app packaging and deployment
- End-to-end validation and troubleshooting methodology

---

## Provisioning Flow Simulated

## Provisioning Flow Simulated

```
Windows 11 Device (OOBE)
↓
Autopilot Profile Detection
↓
Device Registers to Microsoft Entra ID
↓
ODJ Request Sent to Intune Connector
↓
Computer Object Created in mcnairtech.local
↓
Device Reboot
↓
Hybrid Azure AD Join Completed
↓
Intune Policies + Apps Applied
↓
Compliance + Conditional Access Enforcement

```


---

## Repository Structure

`/lab-setup`  
Step-by-step configuration notes with validation checkpoints and required screenshots  

`/architecture-diagrams`  
Identity and provisioning flow diagrams  

`/screenshots`  
Deployment evidence referenced by each lab step  

---

## Documentation Approach

Each lab step includes:

- Defined goal  
- Configuration summary  
- Validation steps  
- Required screenshots  
- Troubleshooting notes  
- Clear "Done Criteria"  

This ensures repeatability and structured validation at every stage of the provisioning lifecycle.

---

## Validation Philosophy

All configurations are validated across three core systems:

- Active Directory  
- Microsoft Entra ID  
- Microsoft Intune  

This “AD / Entra / Intune” validation model ensures accurate hybrid join state, device compliance, and successful lifecycle provisioning.

---

## Blog Write-Up

A detailed walkthrough with screenshots and expanded explanations will be published at:

https://jmcnairtech.com
