
# Lab Setup (Step-by-Step)

This folder contains the full build guide for the **Intune Autopilot + Microsoft Entra hybrid join** lab.

## Lab goal
Provision a Windows device using **Autopilot**, perform **on-prem domain join**, register the device in **Microsoft Entra ID**, enroll in **Intune (MDM)**, then enforce **compliance + Conditional Access** and deploy apps.

---

## Folder map

Follow the guides in order:

1. **00-prereqs-and-lab-environment.md**  
   Accounts, licenses, network/DNS assumptions, VM layout, naming conventions.

2. **01-onprem-ad-dns-ou-structure.md**  
   Domain setup (jmcnairtech.local), OU design, users/groups, DNS sanity checks.

3. **02-entra-connect-device-options-scp.md**  
   Configure Microsoft Entra Connect **device options** and create the **SCP** for hybrid join.

4. **03-gpo-device-registration-hybrid-join.md**  
   Enable device registration using GPO and verify scheduled tasks + event logs.

5. **04-intune-connector-for-ad-odj.md**  
   Install and configure the Intune Connector for Active Directory (ODJ).

6. **05-autopilot-enrollment-hardware-hash.md**  
   Collect hardware hash and import into Autopilot.

7. **06-autopilot-profile-hybrid-join.md**  
   Create and assign the Autopilot deployment profile (Hybrid join).

8. **07-domain-join-profile-odj.md**  
   Create the Intune Domain Join profile (ODJ), specify domain + OU.

9. **08-esp-and-baseline-policies.md**  
   Enrollment Status Page (ESP), baseline configs (BitLocker, WHfB if used).

10. **09-compliance-and-conditional-access.md**  
   Compliance policies + Conditional Access requiring compliant devices.

11. **10-win32-app-packaging-deployment.md**  
   Win32 app packaging + deployment (detection rules, install behavior).

12. **11-validation-and-troubleshooting.md**  
   Validation checks + common failures (ODJ, ESP timeouts, device object mismatch).

---

## Screenshot references
Each lab step includes a **Screenshots** section linking to the relevant images in `/screenshots`.

Naming format used:
`<step#>-<area>-<short-description>.png`

Example:
`02-entra-connect-scp-configured.png`
