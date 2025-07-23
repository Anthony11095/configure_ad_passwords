<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed:Enable, Unlock, Reset (Azure)</h1>
This tutorial outlines enabling, unlocking accounts, and resetting paswords, on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services


<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

## 🔧 Prerequisites

Before starting this lab, make sure you meet the following requirements:

- **Azure Virtual Machines**
  - Ensure that `DC-1` and `Client-1` VMs are available in the Azure Portal.
  - Power them on if they are turned off.

- **User Account**
  - A user account must already exist (created during previous labs or setup).

- **Administrator Access**
  - You must have admin rights on both the Domain Controller and Client machine.

- **Active Directory**
  - Active Directory Domain Services (AD DS) should be properly configured on `DC-1`.

- **Group Policy Management**
  - Group Policy Management Console (GPMC) should be installed and accessible to configure account lockout settings.

- **Internet Connectivity**
  - Required for accessing external resources and documentation:
    - [How to Configure Account Lockout Threshold in Group Policy](#)
    

- **Working Knowledge of the Following Concepts:**
  - Account lockout policies
  - Enabling/disabling user accounts in AD
  - Viewing security logs in both Domain Controllers and client machines

- **Cost-Saving Reminder**
  - Do **not** delete the VMs after finishing the lab.
  - To save on Azure costs, stop/turn off the VMs if you're done for the day.

<h2>Deployment and Configuration Steps</h2>

<p>
Account Lockout and Unlock (https://github.com/user-attachments/assets/3e7fa2c2-838a-4ccc-9039-72d69046e0c0)

</p>
<p>
## 🔐 Account Lockout and Unlock – Lab Snapshot

### 🖼️ What’s Shown

The screenshot displays the **Active Directory Users and Computers (ADUC)** interface, specifically the **user properties dialog** of a locked-out account. The message confirms:

> _"Unlock account. This account is currently locked out on this Active Directory Domain Controller."_

This screen is used to manually unlock the user account.

---

### 🧭 How We Got Here – Summary Steps

1. **Logged into the Domain Controller (`DC-1`)**
2. **Created or selected a test user account**
3. **Simulated a lockout** by attempting to log in multiple times (e.g., 5 or more) with an incorrect password
4. **Observed the lockout** message indicating the account was locked via AD
5. **Opened ADUC** → Navigated to the user's properties → Observed the account lockout status

---

### ✅ Summary

This image confirms a successful **account lockout simulation in Active Directory**. It visually verifies the lab's goal of demonstrating how incorrect login attempts trigger account lockout and how administrators can identify and unlock accounts via ADUC.
</p>
<br />

<p>
Your account has been disabled messege (https://github.com/user-attachments/assets/73f68e42-2c02-45c7-9f89-3e3bdc67ae3a)

</p>
<p>
## 🚫 Account Disabled – Login Error (Client-1)

### 🖼️ What’s Shown

This screenshot shows a **login failure message** on `Client-1` due to a **disabled user account**. The system displays:

> _"Your account has been disabled. Ask your admin or tech support for help."_

Additional details:
- **Error Code**: 0x2823  
- **Extended Error Code**: 0x0

---

### 🧪 How We Got Here (Steps)

1. Logged into the **Domain Controller (DC-1)**.
2. Opened **Active Directory Users and Computers (ADUC)**.
3. **Purposely disabled** a test user account to simulate a real-world lockout scenario.
4. Switched to `Client-1` and attempted to log in using the disabled account.
5. The login failed, triggering the account-disabled message.

---

### ✅ Summary

This was an intentional test to demonstrate how **disabling an Active Directory account** immediately blocks login attempts. This method is often used by IT admins for security, offboarding, or account control.
</p>
<br />

<p>
Observing default domain policy logs (https://github.com/user-attachments/assets/1e140e7d-a227-44a6-9514-002c766f1e10)

</p>
<p>
## 🛡️ Group Policy Management – Default Domain Policy

### 🖼️ What’s Shown

The screenshot displays the **Group Policy Management Console (GPMC)** on the Domain Controller. The **Default Domain Policy** is selected, and details like domain name, creation time, and GPO status are visible.

---

### 🧪 How We Got Here (Steps)

1. Logged into the **Domain Controller (DC-1)**.
2. Opened **Group Policy Management**.
3. Navigated to **Group Policy Objects** under the domain (`mydomain.com`).
4. Selected the **Default Domain Policy** to review or modify settings (e.g., account lockout policy).
5. As part of the lab, also began **observing system and security logs** to monitor the effects of these policies in:
   - **Event Viewer** on the Domain Controller
   - **Event Viewer** on `Client-1` for user-level events

---

### ✅ Summary

This part of the lab focuses on understanding how **Group Policy settings** like account lockout thresholds are applied across the domain. Observing logs in **Event Viewer** helps confirm that the policy changes are working and provides insight into login attempts, lockouts, and other security events.
</p>
