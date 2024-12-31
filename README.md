# Helpdesk Homelab

Welcome to my Helpdesk Homelab project! This setup demonstrates a simulated IT helpdesk environment using **VirtualBox**, **Windows Server 2019**, and **Active Directory**. It showcases core IT administrative skills, such as user account management, group policy configuration, and basic troubleshooting techniques, all designed to replicate real-world scenarios.

---

## 📦 VirtualBox & Server 2019 Setup

<details>
<summary>💻 Steps to Configure VirtualBox and Install Server 2019</summary>

### 1️⃣ Download and Install VirtualBox
- To start I visited the [VirtualBox website](https://www.oracle.com/virtualization/technologies/vm/downloads/virtualbox-downloads.html) and downloaded the latest version.  
- Follow the installation wizard to complete the setup.

### 2️⃣ Download the Windows Server 2019 ISO
- To download the Server 2019 ISO, I went to the [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/) and searched for "Windows Server 2019."

### 3️⃣ Create a New Virtual Machine
- Open VirtualBox and click `New`.
  
  ![New VM Screenshot](https://github.com/user-attachments/assets/7116c63c-d6a3-4a0d-a759-9df440eea598)

- I named the virtual machine `Server 2019`.  
- Select the downloaded Windows Server 2019 ISO image.  
- I checked `Skip Unattended Installation`, then I clicked `Next`
  
  ![Screenshot 2024-12-30 220652](https://github.com/user-attachments/assets/83a81a79-8a1f-4da3-b21a-3ae4fcd8a7fe)

### 4️⃣ Configure Virtual Machine Hardware Settings
- Next, I allocated `4 CPU cores` and `4GB of RAM`.  

   ![Hardware Configuration Screenshot](https://github.com/user-attachments/assets/061c035b-8fd4-4f57-9bf2-ee66c5dde676)
  
- Next, I set the virtual hard disk size to `50GB`.  

  ![Hard Disk Size Screenshot](https://github.com/user-attachments/assets/0b1a7605-65f7-4893-bb85-e39973ebf9c4)
  
- Click `Finish` to complete the setup.  

  ![Screenshot 2024-12-30 222023](https://github.com/user-attachments/assets/54dd2892-fd6b-47fd-91b5-7c71a06cd88a)

### 5️⃣ Install Windows Server 2019
  
- Open VirtualBox, select the Server 2019 VM, and click `Start`.  

  ![Start VM Screenshot](https://github.com/user-attachments/assets/7edc6fc4-1556-4406-96ee-de5e4400a55a)

- Once installed, the VM will be ready and operational!  

  ![Completed Setup Screenshot](https://github.com/user-attachments/assets/f7e23cec-1efd-4d81-92c8-125c7e41b602)

</details>

## 🛠️ Troubleshooting: Laggy Mouse and Display Scaling Issues

<details>
<summary>🖱️ Fixing Mouse Lag and Scaling Issues</summary>

### Issue Observed
With the virtual machine running, there were noticeable issues with mouse lag and improper display scaling.  

  ![Mouse Lag Screenshot](https://github.com/user-attachments/assets/f7e23cec-1efd-4d81-92c8-125c7e41b602)

### Solution
1️⃣ Go to `Devices` in the VirtualBox menu and select `Insert Guest Additions CD image...`.  
   
   ![Insert Guest Additions Screenshot](https://github.com/user-attachments/assets/7b1684a1-5a8a-4f5a-91d1-82541c3ba5c1)
   
2️⃣ Open `File Explorer` within the VM and navigate to `This PC`.  

3️⃣ Under `Devices and Drives`, open the `CD Drive (D:) VirtualBox Guest Additions`.  
   
   ![Guest Additions Drive Screenshot](https://github.com/user-attachments/assets/c9a9d62d-d1fd-4068-bcc2-89b45c5ddf77)

4️⃣ Run `VBoxWindowsAdditions-amd64` and complete the installation.  
   
   ![Guest Additions Installer Screenshot](https://github.com/user-attachments/assets/18c984f6-9eb0-4a0c-b46d-3f75ad092226)

5️⃣ Reboot the VM.  

### Result
The mouse now moves smoothly, and the display scaling adjusts correctly, allowing for a better user experience. 😊  
  
  ![Fixed Issues Screenshot](https://github.com/user-attachments/assets/f9d96384-69ab-4fc2-8c42-b7196732c051)

</details>

---

## 🌐 Active Directory Domain Services (AD DS)

Active Directory Domain Services (AD DS) is a critical role for managing user identities, groups, and resources in a centralized domain. To install AD DS on Windows Server 2019, I used the Server Manager to add the role, configured it as the primary domain controller, and set up the domain goodcorp.com. This step establishes the foundation for centralized management and security in the lab environment.

<details>
<summary>🌐 Installing Active Directory Domain Services</summary>

---

## 🛠️ 1. Open Server Manager & Start Installation

1️⃣ Launch Server Manager  
- Open the VM, click `Start`, and select `Server Manager`.  

  ![Server Manager](https://github.com/user-attachments/assets/38ee87c4-8674-400e-bbfe-615c5cc283c3)

2️⃣ Add Roles and Features  
- On the Server Manager dashboard, click `Manage` → `Add Roles and Features`.  

  ![Add Roles and Features](https://github.com/user-attachments/assets/9be5e3e2-1c64-4147-838f-749d3fef7465)

---

## 🖱️ 2. Use the Installation Wizard

3️⃣ Begin Installation  
- When the installation wizard appears, click `Next`.  

  ![Installation Wizard](https://github.com/user-attachments/assets/e6f552f3-af02-446c-8879-afba8f498b86)

4️⃣ Select Installation Type  
- Choose `Role-based or Feature-based Installation`, then click `Next`.  

  ![Installation Type](https://github.com/user-attachments/assets/73e08efb-b176-4a52-8d19-78769956c37f)

5️⃣ Pick the Destination Server  
- Select `A server from the server pool` and click `Next`.  

  ![Destination Server](https://github.com/user-attachments/assets/7a214833-6591-4b29-a9fd-68eea3139cda)

---

## 🧩 3. Add the AD DS Role

6️⃣ Add the Role  
- Select `Active Directory Domain Services`, click `Add Features`, then click `Next`.  

  ![AD DS Role](https://github.com/user-attachments/assets/aacaaec9-f312-43c4-8bf3-b265e8ff67de)

7️⃣ Review Features  
- On the Features tab, leave everything as is, then click `Next`.  

  ![Features Tab](https://github.com/user-attachments/assets/ad15bf3e-25a3-4ebd-97f5-bf094347d04d)

8️⃣ Confirm Installation  
- On the AD DS tab, click `Next`, then `Install` on the Confirmation tab.  

  ![Confirmation Tab](https://github.com/user-attachments/assets/368b274c-91bf-4bae-872d-2ec3fde34ff2)

---

## 🌳 4. Promote to Domain Controller

9️⃣ Start Promotion  
- After installation, click `Promote this server to a domain controller`.  

- Add a New Forest: I chose to use `goodcorp.com`.  
  ![Add Forest](https://github.com/user-attachments/assets/37d8898a-2e16-4140-96f2-cab44caf2007)

🔟 Set Domain Controller Options  
- Input a password and click `Next`.  
  ![Domain Controller Options](https://github.com/user-attachments/assets/fe8cc402-6b68-4f18-bf8f-d44549f21b7d)

---

## 🔗 5. Configure Additional Settings

- DNS Options: Leave unchecked and click `Next`.  
  ![DNS Options](https://github.com/user-attachments/assets/8ad70ae0-355c-4053-a979-dbed3285a9f4)

- NetBIOS Name: Leave as is and click `Next`.  
  ![NetBIOS Name](https://github.com/user-attachments/assets/e9b7b17f-c5ba-4379-a8fc-d20ce6578d4d)

- Paths Tab: Keep defaults and click `Next`.  
  ![Paths Tab](https://github.com/user-attachments/assets/3b4c5adb-c728-4cf3-b68d-8110341e2bf5)

- Review Tab: Click `Next`.  
  ![Review Tab](https://github.com/user-attachments/assets/e0e265e5-aa25-4e6d-bdb6-02794982ebb3)

- Prerequisites Check: Click `Install`.  
  ![Prerequisites Check](https://github.com/user-attachments/assets/abfb3074-a958-4c4c-9385-5edd5b859208)

---

## 🔄 6. Final Steps

✅ Installation Complete  
- Once the installation completes, the VM will automatically restart.  

  ![Restart](https://github.com/user-attachments/assets/7eeefc23-2ad1-47ff-a921-f47941e80350)

---

</details>

