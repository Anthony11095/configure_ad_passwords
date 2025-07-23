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
![your account has been disabled msg, from AD lab](https://github.com/user-attachments/assets/73f68e42-2c02-45c7-9f89-3e3bdc67ae3a)

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
![observing default domain policy logs, AD lab](https://github.com/user-attachments/assets/1e140e7d-a227-44a6-9514-002c766f1e10)

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
