# 07 - Autopilot Device Group and Hybrid Microsoft Entra Join Deployment Profile

## Goal
Create a dynamic **Autopilot device group** and assign a **Hybrid Microsoft Entra ID Join (formerly Azure AD Join)** Autopilot deployment profile so registered devices receive the correct provisioning configuration during OOBE.

## Why this matters
Autopilot profiles are applied based on **device group membership**.
Using a dynamic group ensures that any device registered as an Autopilot device is automatically targeted without manual assignment.

This step enables Intune to:
- identify Autopilot-registered devices
- apply a Hybrid Entra Join deployment profile
- control the OOBE experience during provisioning

---

## Prereqs
- Step 06 complete (HWID successfully imported)
- Device visible in **Windows Autopilot devices**
- Intune permissions to create groups and Autopilot profiles

---

## What was done

- Created a dynamic security group for Autopilot devices
- Configured a Hybrid Microsoft Entra ID Join Autopilot deployment profile
- Assigned the deployment profile to the Autopilot device group
- Verified the device shows the profile as **Assigned**

---

## Configuration Details

### Autopilot Device Group
- Group type: Security
- Membership type: Dynamic Device
- Membership rule:
