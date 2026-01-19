# Intune Autopilot + Microsoft Entra Hybrid Join Lab (Hyper-V)

This project documents a hands-on lab that simulates an enterprise Windows provisioning workflow using **Microsoft Intune**, **Windows Autopilot**, and **Microsoft Entra hybrid join** (Hybrid Azure AD Join) — validated using a **Windows 11 Hyper-V VM**.

The goal is to demonstrate understanding of the hybrid onboarding path: identity + provisioning + security enforcement + validation across **AD / Entra ID / Intune**.

---

## What This Lab Demonstrates
- Windows Autopilot-style provisioning (OOBE simulation on Hyper-V)
- Hybrid identity configuration using **Microsoft Entra Connect** (AAD Connect)  
- **Service Connection Point (SCP)** setup for hybrid registration discovery
- **Offline Domain Join (ODJ)** via the Intune Connector for Active Directory
- Device registration and hybrid join behavior (GPO-based device registration)
- Enrollment Status Page (ESP) configuration
- Intune configuration + compliance policies
- Conditional Access requiring compliant devices
- Win32 app packaging and deployment
- Troubleshooting and validation methods for hybrid provisioning

> Note: Autopilot device registration via hardware hash is designed for physical devices. In this lab, Autopilot flows are validated in a Hyper-V VM environment; hash import may vary depending on VM identifiers and configuration.

---

## Architecture Overview
**Workflow (lab simulation on Hyper-V):**  
Windows 11 VM reset → OOBE → Autopilot profile assignment → ODJ domain join → **Microsoft Entra hybrid joined** → Intune enrollment → Compliance → Conditional Access → App deployment

Diagrams are stored in: `/architecture-diagrams`

---

## Proof / Evidence (Screenshots)
Screenshots are stored in: `/screenshots`  
Naming format: `<step#>-<component>-<short-description>.png`

### Completed (so far)
- Entra-friendly UPN suffix configured in AD  
  `screenshots/00-ad-upn-suffix-added.png`
- Test user UPN set to `@jmcnairtech.com`  
  `screenshots/00-ad-test-user-upn-set.png`

### Planned milestone proof (added as each step is completed)
- Entra Connect SCP configured: `screenshots/02-entra-connect-scp-configured.png`
- Intune Connector for AD (ODJ) active: `screenshots/04-intune-connector-odj-active.png`
- Autopilot profile assigned: `screenshots/06-autopilot-profile-assigned.png`
- Intune Domain Join profile (OU path): `screenshots/07-intune-domain-join-profile-settings.png`
- Validation “Big 3”:
  - AD device object in correct OU: `screenshots/11-ad-device-in-ou.png`
  - Entra device shows **Hybrid joined**: `screenshots/11-entra-hybrid-joined.png`
  - Intune device shows **Managed/Compliant**: `screenshots/11-intune-managed-compliant.png`

---

## Key Concepts (What I’m Proving I Understand)
- **SCP (Service Connection Point):** how domain-joined devices discover the correct Entra tenant for registration
- **ODJ (Offline Domain Join):** why Hybrid Autopilot requires the Intune Connector for Active Directory
- **Device Registration GPO:** how hybrid registration is triggered after domain join
- **Validation:** confirming success across AD, Entra ID, and Intune (including `dsregcmd /status`)

---

## Lab Notes
- Lab prerequisites and environment details: `lab-setup/00-prereqs-and-lab-environment.md`
- Screenshot index + naming: `screenshots/README.md`

---

## Blog Post
A full write-up with screenshots and explanations will be published on **jmcnairtech.com**:
https://jmcnairtech.com
