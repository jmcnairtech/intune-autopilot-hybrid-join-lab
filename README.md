# Intune Autopilot + Hybrid Azure AD Join Lab

This project demonstrates a full end-to-end modern device lifecycle using **Windows Autopilot**, **Intune**, and **Hybrid Azure AD Join**.  
It simulates how an enterprise provisions, enrolls, secures, and manages Windows devices using cloud-based and hybrid identity.

---

##  What This Lab Covers

- Collecting and importing Autopilot hardware hashes  
- Creating and assigning Autopilot deployment profiles  
- Configuring Hybrid Azure AD Join (Cloud Sync or AAD Connect)  
- Setting up the Service Connection Point (SCP)  
- Enabling device registration via GPO  
- Enrollment Status Page (ESP) configuration  
- Intune compliance policies  
- Conditional Access based on device compliance  
- Win32 app packaging and deployment  
- Troubleshooting Autopilot and Hybrid Join issues  

---

##  Architecture Overview

**Workflow:**  
User unboxes device → Autopilot → Hybrid Join → Intune MDM enrollment → Compliance → Conditional Access → App deployment.

This mirrors a real enterprise onboarding experience.

---

## 📌 Blog Post

A full write-up with screenshots and explanations will be published on [jmcnairtech.com](https://jmcnairtech.com).
