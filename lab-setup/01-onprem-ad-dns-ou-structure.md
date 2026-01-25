# 01 - On-Prem AD, DNS, and OU Structure

## Goal
Build the on-prem Active Directory foundation used by Hybrid Autopilot:
- OU structure for users/devices
- Test users (cloud-friendly UPN from Step 00)
- DNS sanity checks (clients can resolve AD + internet through the DC)

---

## Starting State (from Step 00)
You should already have:
- `Lab-DC01` running AD DS + DNS
- DC IP: `10.0.0.10` on `10.0.0.0/24`
- DHCP scope active and issuing leases to Win11 VM
- UPN suffix added (example: `@jmcnairtech.com`)

---

## Step 01 Tasks

### 1) Create OUs (ADUC)
Open **Active Directory Users and Computers** and create:

**Users**
- `Lab Users`

**Devices**
- `Lab Devices`
  - `Autopilot Devices`

Recommended DN targets (used later in the ODJ/Domain Join profile):
- `OU=Lab Users,DC=jmcnairtech,DC=local`
- `OU=Autopilot Devices,OU=Lab Devices,DC=jmcnairtech,DC=local`

> Keep OU names simple and consistent—these OUs will be referenced later by Intune.

---

### 2) Create test users (standard users)
Create at least 2 test users inside **Lab Users**:
- `testuser1`
- `testuser2`

**Account tips**
- Make them standard users (not Domain Admin)
- Set a known password for lab use
- Optionally check “Password never expires” (lab-only convenience)

---

### 3) Set UPN on the test users (cloud-friendly sign-in)
In ADUC:
- Open each test user → **Account** tab
- Set the UPN suffix to:
  - `@jmcnairtech.com` (preferred)

Example:
- `testuser1@jmcnairtech.com`
- `testuser2@jmcnairtech.com`

---

### 4) DNS sanity checks (DC + client)
#### On Lab-DC01
Run:
- `nslookup jmcnairtech.local`
- `nslookup www.microsoft.com`

#### On WIN11 VM
Confirm it’s using the DC for DNS:
- `ipconfig /all` (DNS server should be `10.0.0.10`)

Then run:
- `nslookup jmcnairtech.local`
- `nslookup www.microsoft.com`

If internet name resolution fails, confirm DC forwarders are configured (Step 00 optional).

---

## Screenshots to Capture (Step 01)

Minimum:
- `01-ad-ou-structure.png`
  - ADUC tree showing **Lab Users**, **Lab Devices**, and **Autopilot Devices**
- `01-ad-test-users-in-lab-users.png`
  - ADUC showing test users inside **Lab Users**
- `01-ad-test-user-upn-set.png`
  - User properties → Account tab showing UPN set to `@jmcnairtech.com`

Optional:
- `01-win11-dns-sanity-nslookup.png`
  - Win11 cmd/PowerShell showing successful `nslookup` for domain + internet

---

## Done Criteria (to move to Step 02)
You’re ready to proceed when:
- OUs exist: **Lab Users**, **Lab Devices**, **Autopilot Devices**
- At least 2 standard users exist in **Lab Users**
- Test users have UPNs set to `@jmcnairtech.com`
- Win11 VM can resolve:
  - `jmcnairtech.local`
  - external DNS names (e.g., `www.microsoft.com`)

---

## Notes
Step 02 will configure **Microsoft Entra Connect device options** and set the **SCP** so domain-joined devices can discover the Entra tenant for hybrid join.
