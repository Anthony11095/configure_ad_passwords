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

## ✅ Prerequisites

Before beginning the installation of osTicket, ensure the following prerequisites are met:

- **Operating System**
  - Windows 10 or Windows Server (for VM setup)

- **Virtualization Platform**
  - Azure Virtual Machine (or alternative virtualization environment)

- **osTicket Software**
  - osTicket installation zip file (latest version from official site)

- **Web Server**
  - IIS (Internet Information Services) installed and configured

- **Database Server**
  - MySQL (or MariaDB) installed and running

- **Scripting Language**
  - PHP (version compatible with osTicket)

- **Other Tools**
  - Web browser (e.g., Chrome, Firefox)
  - Text editor (e.g., Notepad++, VS Code)

- **Access Requirements**
  - Administrator access to the VM or local machine
  - Active internet connection

- **Optional**
  - phpMyAdmin (for easier database management)
  - Mail server setup (if testing ticket email functionality)

## 🛠️ Installation Steps: Account Lockout, Disable/Enable, and Group Policy

Follow the instructions below for configuring account lockout, disabling/enabling accounts, and applying Group Policy settings. Insert your screenshots exactly where indicated.

---

### 1. Configure Group Policy for Account Lockout
 (https://github.com/user-attachments/assets/1e140e7d-a227-44a6-9514-002c766f1e10)
- Log into `DC-1`
- Open **Group Policy Management**
- Edit the **Default Domain Policy**
- Navigate to:
  `Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy`
- Set:
  - **Account lockout threshold**: 5 invalid attempts  
  - **Lockout duration**: 15 minutes  
  - **Reset account lockout counter**: 15 minutes


---

### 2. Simulate an Account Lockout
(https://github.com/user-attachments/assets/73f68e42-2c02-45c7-9f89-3e3bdc67ae3ao)
- Pick a test user account (e.g., `dudut.r`)
- On `Client-1`, try logging in with the wrong password **more than 5 times**
- The account will lock out
- Go back to `DC-1`, open **Active Directory Users and Computers**
- Search for the user and open their **Properties**
- Verify the "Account is locked out" checkbox is active

> 📸 **Insert Photo 1 here** — *This shows the locked-out account status in ADUC for user `dudut.r`.*

---

### 3. Unlock the Account
 (https://github.com/user-attachments/assets/1e140e7d-a227-44a6-9514-002c766f1e10)
- On the same **Properties** window
- Check the **Unlock account** box
- Optionally reset the password
- Click **Apply** and **OK**

✅ The user can now log in again.

---

### 4. Disable the Account and Attempt Login

- Go to **Active Directory Users and Computers**
- Right-click the user account and select **Disable**
- On `Client-1`, try logging in as that user again
- You should see an error saying:  
  *“Your account has been disabled.”*

---

### 5. Re-enable the Account

- Back in ADUC, right-click the account and select **Enable**
- Try logging in again — it should succeed now.

---

### ✅ Wrap-Up

- Confirm that Group Policy lockout is enforced
- Verify that disable/re-enable functions correctly
  

