# Intune Autopilot + Microsoft Entra Hybrid Join Lab (Hyper-V)

This repo documents a hands-on lab that simulates an enterprise Windows provisioning lifecycle using **Windows Autopilot**, **Microsoft Intune**, and **Microsoft Entra hybrid join**.

The goal is to demonstrate understanding of:
- Hybrid identity (AD DS + Entra)
- Autopilot provisioning flow
- Offline Domain Join (ODJ) with the Intune Connector for AD
- Policy, compliance, and Conditional Access enforcement
- App deployment and troubleshooting

> Lab environment: **Hyper-V** (Windows Server DC + Windows 11 client VM)

---

## What this project covers
- Entra Connect device options + SCP (hybrid join discovery)
- GPO device registration (hybrid join prerequisites)
- Intune Connector for Active Directory (ODJ)
- Autopilot registration + deployment profile (Hybrid Join)
- Domain Join profile + OU targeting
- Enrollment Status Page (ESP)
- Baseline policies + compliance
- Conditional Access requiring compliant devices
- Win32 app packaging/deployment
- Validation + troubleshooting (“Big 3”: AD / Entra / Intune)

---

## Repo structure
- `/lab-setup` — step-by-step build notes and configuration screenshots required per step
- `/architecture-diagrams` — diagrams for the identity + provisioning flow
- `/screenshots` — evidence screenshots referenced by the lab steps

---

## Progress
This lab is being built and documented incrementally. Each step includes validation points and screenshots.

---

## Blog Post
A full write-up with screenshots and explanations will be published on **jmcnairtech.com**.
