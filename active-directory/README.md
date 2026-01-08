# Active Directory Home Lab

## Overview
Built a Windows Server domain environment to practice user management, group policies, and common Help Desk tasks.

## Environment
- **Domain Controller:** Windows Server 2022
- **Client Machine:** Windows 10/11 Pro
- **Virtualization:** Nested Hyper-V architecture

## Tasks Completed

### User Management
- Created organizational units (OUs) for departments
- Added user accounts and assigned to security groups
- Performed password resets and account unlocks

### Group Policy
- Configured password policies

### Troubleshooting
- Resolved account lockouts
- Fixed domain join issues

## Screenshots & Walkthroughs

### Infrastructure Setup

**Identity: Renamed Server to DC01 and configured a static IP**

![Rename & IP](../screenshots/generic-server-name.png)
![Rename & IP](../screenshots/change-server-name.png)
![Rename & IP](../screenshots/change-server-name-dc01.png)
![Rename & IP](../screenshots/dc01-correct-ipconfig.png)

Set server static IP to 192.168.1.10. Servers must have a permanent "address" so other computers can always find them.
Preferred DNS server: 127.0.0.1 -- This tells the server to look at itself for DNS once AD is installed. 

**Installing Active Directory Domain Services**

![AD DS Installation](../screenshots/ad-installation.png)

Installed the AD DS role through Server Manager and promoted the server to a Domain Controller for the `guslab.local` forest.

---

**Promoting Server to Domain Controller**

![Promote to DC](../screenshots/promote-dc-notification.png)

Clicked the notification flag in Server Manager and promoted the server to a Domain Controller, creating a new forest.

---

**Organizational Units Structure**

![OUs in Active Directory](../screenshots/ad-ous.png)

Established a department-based Organizational Unit (OU) structure to facilitate the application of granular Group Policy Objects (GPOs).

---

### User Management

**Creating a New User in ADUC**

![Adding users in ADUC](../screenshots/new-users-it.png)

Created user accounts and assigned them to appropriate OUs—a daily Help Desk task for onboarding.

---

### Centralized Administration via Group Policy (GPO)

**Account Lockout Policy**

![New GPO](../screenshots/new-gpo.png)
![Account lockout GPO](../screenshots/account-lockout-group-policy.png)

Configured account lockout thresholds to protect against brute-force attacks while minimizing unnecessary lockouts for users.

---

**Enfored the Update**

![gpupdate](../screenshots/gpupdate-force.png)

Forced the client to download the new rules immediately using gpupdate /force in the Command Prompt.

---

### The Endpoint (The CLIENT Side)

**DNS Pointing**

![Preferred DNS on Client Machine](../screenshots/correct-clientvm-ipconfig-setup.png)

Configured the correct Network Settings on the Client Machine to enable communication with the Domain Controller.

---

**Verified the Connection** Verified end-to-end connectivity by aligning Client DNS settings with the Domain Controller's static IP

![Ping Domain Controller](../screenshots/successful-dc-ping.png)

Open Command Prompt on the Client and typed ping 192.168.1.10. Successful connection.


**Joined Domain**

![Join Domain Screen](../screenshots/join-domain-clientvm-screen.png)
![Domain Join](../screenshots/successful-domain-join-from-clientvm.png)

Successfully joined the Client Machine to the Domain Controller.

**Successfully Logged Onto CLIENT Machine**

![First domain login](../screenshots/clientvm-login-first-attempt.png)

**Password Change on First Login:**

![Password change prompt](../screenshots/clientvm-login-change-pw.png)

**Lesson Learned:** Document credentials securely. In production, use a password manager or privileged access management (PAM) solution.

### Troubleshooting 

#### Problem 1: Client VM Couldn't Communicate with Domain Controller

**The Issue:** Left DHCP enabled on the client VM, which assigned it to a different subnet than the DC. The machines couldn't see each other.

**Before (Auto DHCP):**

![DHCP causing subnet mismatch](../screenshots/change-auto-dhcp-clientvm.png)

![Domain could not be contacted error](../screenshots/dns-error-cannjot-join-domain.png)

**Verified the Server's Identity** Opened Command Prompt inside the Server and used ipconfig /all

![DC ipconfig /all](../screenshots/dc01-ipconfig-all.png)

**The Fix:** Configured a static IP on the client and pointed the DNS server to the DC's IP address (192.168.1.10).

![DNS pointing to DC](../screenshots/clientvm-dns-config.png)

**Lesson Learned:** Always verify network settings before attempting domain joins. DNS must point to the DC.

---

#### Problem 2: Couldn't Remember DC Admin Credentials During Domain Join

**The Issue:** When prompted for credentials to join the domain, I couldn't recall the exact admin username format.

**What I Did:**
1. Logged back into the DC
2. Opened ADUC to verify the administrator account
3. Returned to client and successfully joined using `lab.local\Administrator`

**Checked DC User logon name**

![ADUC DC UN](../screenshots/confirm-dc-username.png)

**Password Change on First Login:**

![Password change prompt](../screenshots/clientvm-login-change-pw.png)

**Lesson Learned:** Document credentials securely. In production, use a password manager or privileged access management (PAM) solution.

## What I Learned
- How Active Directory structures users and resources
- Real-world Help Desk tasks like password resets, account management and resolving DNS Resolution failures
- Group Policy fundamentals for managing multiple machines
