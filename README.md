# Active Directory Help Desk Lab

Welcome to my Helpdesk Homelab project! This setup demonstrates a simulated IT helpdesk environment using **VirtualBox**, **Windows Server 2019**, and **Active Directory**. It showcases core IT administrative skills, such as user account management, group policy configuration, and basic troubleshooting techniques, all designed to replicate real-world scenarios.

![Helpdesk Diagram drawio](https://github.com/user-attachments/assets/8f702151-2c27-45c6-87da-01b321d7d5ad)

---

## 📦 VirtualBox - Server 2019 & Windows 10 Setup

<details>
<summary>💻 Steps to Configure VirtualBox and Install Server 2019 & Windows 10</summary>

### 1️⃣ Download and Install VirtualBox
- To start I visited the [VirtualBox website](https://www.oracle.com/virtualization/technologies/vm/downloads/virtualbox-downloads.html) and downloaded the latest version.  
- Follow the installation wizard to complete the setup.

### 2️⃣ Download the Windows Server 2019 & Windows 10 ISO
- To download the Server 2019 ISO, I went to the [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/) and searched for "Windows Server 2019."
- To download the Windows 10 ISO I went to [Microsoft Software Download Page](https://www.microsoft.com/en-us/software-download/windows10)

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

  ![Screenshot 2024-12-30 222155](https://github.com/user-attachments/assets/aea67364-b653-4e10-a01c-7224353797f1)

- Once the VM boots, I'll set my Language, Time and currency format, and Input method, then click `Next`

  ![Screenshot 2024-12-30 222422](https://github.com/user-attachments/assets/7f843eda-bf00-448a-b989-69419e93d474)

- On the Windows setup screen, I'll click `Install Now`

  ![Screenshot 2024-12-30 222436](https://github.com/user-attachments/assets/6c0f8e19-4b0f-4724-8fe5-67449d19eb45)

- On the next page, I'll make sure to select `Desktop Experience`, then click `Next`

  ![Screenshot 2024-12-30 222801](https://github.com/user-attachments/assets/e6746f98-533b-47cc-a1b8-075ce4e1152c)

- Accept the License terms, then click `Next`

  ![Screenshot 2024-12-30 223212](https://github.com/user-attachments/assets/471b37db-b583-4a97-b7cd-81bd2ea4c1bf)

- On the next page, I'll select `Custom Install`

  ![Screenshot 2024-12-30 223219](https://github.com/user-attachments/assets/27856ea1-6fac-4f08-9ccc-4507187cc1ff)

- On the Disk Allocation page, select the 50GB drive, then click `Next`

  ![Screenshot 2024-12-30 223224](https://github.com/user-attachments/assets/b759346e-a54e-49df-a344-df8de5d71bdc)

- Windows will begin the installation process.
 
  ![Screenshot 2024-12-30 223251](https://github.com/user-attachments/assets/b60d5f85-1425-45fd-8a05-ae7e90379c59)

- Once prompted, I'll input a password, then click `Finish`

  ![Screenshot 2024-12-30 223851](https://github.com/user-attachments/assets/44d64ac8-147b-4ac5-873b-f26b38713821)

- When at the Windows login screen, press `right ctrl + del`, then enter the password to log in.
- NOTE: you have to use ctrl+del since this is a VM. You could also go to `Input` → `Keyboard`, then click `Insert Ctrl-Alt-Del` to achieve the same thing.

  ![Screenshot 2024-12-30 224856](https://github.com/user-attachments/assets/9db6dc9f-c7cd-42dc-8826-ae1b05abcea8)

✅ Installation Complete
- The VM is now ready and operational! Just repeat the process to create a Windows 10 Virtual Machine.

  ![Completed Setup Screenshot](https://github.com/user-attachments/assets/f7e23cec-1efd-4d81-92c8-125c7e41b602)

</details>




<!-- 1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟 -->




## 📦 VirtualBox - Setting up an Internal Network Adapter
The Server 2019 VM will have two NICs set up in VirtualBox: one external NIC for internet access and one internal NIC for communication within the domain and with local machines.

<details>
<summary>📦 Setting Up the VirtualBox Network</summary>

- On the host machine, I'll launch VirtualBox, select the Server 2019 VM, and click `Settings`.

  ![Screenshot 2024-12-31 205055](https://github.com/user-attachments/assets/5775fb11-80c9-4811-a548-2d58790a5d20)

- On the Settings window, switch to `Expert Mode` in the top left corner.

  ![Screenshot 2024-12-31 205116](https://github.com/user-attachments/assets/6c65c99c-5760-4cbf-a0a6-c7403fbcd184)

- Select `Network` from the menu to the left. Make sure Adapter 1 is enabled and set to `NAT` or `Bridged`

  ![Screenshot 2024-12-31 205130](https://github.com/user-attachments/assets/9fab0c51-00d1-46d1-a2bf-326bf6376dfd)

- Click the Adapter 2 tab and check `Enable Network Adapter` then select `Internal Network` and click `OK`

  ![Screenshot 2024-12-31 205154](https://github.com/user-attachments/assets/0081597c-bb98-42d1-b84a-88767b17aeb2)

- The VirtualBox network adapters are now set up properly. This will allow me to have static ips on one nic, while still giving access to the internet from the other.

</details>




<!-- 1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟 -->




## 🛠️ Troubleshooting: Laggy Mouse and Display Scaling Issues

<details>
<summary>🖱️ Fixing Mouse Lag and Scaling Issues</summary>

### Issue Observed
With the virtual machine running, there were noticeable issues with mouse lag and improper display scaling.  

  ![Mouse Lag Screenshot](https://github.com/user-attachments/assets/f7e23cec-1efd-4d81-92c8-125c7e41b602)

### Solution
1️⃣ Go to `Devices` in the VirtualBox menu and select `Insert Guest Additions CD image...`.  
   
   ![Insert Guest Additions Screenshot](https://github.com/user-attachments/assets/7b1684a1-5a8a-4f5a-91d1-82541c3ba5c1)
   
2️⃣ Within the VM, Open `File Explorer` and navigate to `This PC`.  

3️⃣ Under `Devices and Drives`, open the `CD Drive (D:) VirtualBox Guest Additions`.  
   
   ![Guest Additions Drive Screenshot](https://github.com/user-attachments/assets/c9a9d62d-d1fd-4068-bcc2-89b45c5ddf77)

4️⃣ Run `VBoxWindowsAdditions-amd64` and complete the installation.  
   
   ![Guest Additions Installer Screenshot](https://github.com/user-attachments/assets/18c984f6-9eb0-4a0c-b46d-3f75ad092226)

5️⃣ Reboot the VM.  

### Result
The mouse now moves smoothly, and the display scaling adjusts correctly, allowing for a better user experience. 😊  
  
  ![Fixed Issues Screenshot](https://github.com/user-attachments/assets/f9d96384-69ab-4fc2-8c42-b7196732c051)

</details>




<!-- 1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟 -->




## 🌐 Active Directory Domain Services (AD DS)

Active Directory Domain Services (AD DS) is a critical role for managing user identities, groups, and resources in a centralized domain. To install AD DS on Windows Server 2019, I used the Server Manager to add the role, configured it as the primary domain controller, and set up the domain goodcorp.com. This step establishes the foundation for centralized management and security in the lab environment.

<details>
<summary>🌐 Installing Active Directory Domain Services</summary>

## 🛠️ Prepare the Server

### Change the Computer Name  
- Go to System Properties, by opening `File Explorer` right-click `This PC`, then select `Properties`.

  ![Screenshot 2024-12-30 233825](https://github.com/user-attachments/assets/c35254c2-8989-48e3-8e4d-c041222bf78a)

- Next to Computer Name click `Change Settings`

  ![Screenshot 2024-12-30 234145](https://github.com/user-attachments/assets/1f375b22-e8cc-45ab-a64c-0766477394d5)

- Click `Change` then set the computer name, I'll use `GoodCorp-DC`, click `OK` then restart the server.

  ![Screenshot 2024-12-30 235134](https://github.com/user-attachments/assets/a5a1191f-5e26-49ee-a184-be7d5c9f7094)

- Once restarted, go to system properties again to verify the name has changed.

  ![Screenshot 2024-12-30 235519](https://github.com/user-attachments/assets/2a4f91fb-63a5-4e54-82a4-bc3c7196f6a1)

---

## 🛠️ Open Server Manager & Start Installation

1️⃣ Launch Server Manager  
- Open the VM, Server Manager should start automatically. If not, click `Start`, and select `Server Manager`.  

  ![Server Manager](https://github.com/user-attachments/assets/38ee87c4-8674-400e-bbfe-615c5cc283c3)

2️⃣ Add Roles and Features  
- On the Server Manager dashboard, click `Manage` → `Add Roles and Features`.  

  ![Add Roles and Features](https://github.com/user-attachments/assets/9be5e3e2-1c64-4147-838f-749d3fef7465)

---

## 🖱️ Use the Installation Wizard

3️⃣ Begin Installation  
- When the installation wizard appears, click `Next`.  

  ![Screenshot 2024-12-31 000254](https://github.com/user-attachments/assets/7a82862c-b490-4c80-bdbf-91d54251bd5a)

4️⃣ Select Installation Type  
- Choose `Role-based or Feature-based Installation`, then click `Next`.  

  ![Screenshot 2024-12-31 000345](https://github.com/user-attachments/assets/d018a402-c014-481d-883b-b39e03ea8c36)

5️⃣ Pick the Destination Server  
- Click `Select a server from the server pool` and click `Next`.  

  ![Screenshot 2024-12-31 000419](https://github.com/user-attachments/assets/01baa936-5ab2-43d9-9773-808b8b11b77f)

---

## 🧩 Add the AD DS Role

6️⃣ Add the Role  
- Select `Active Directory Domain Services`, click `Add Features`, then click `Next`.  

  ![Screenshot 2024-12-31 000520](https://github.com/user-attachments/assets/1dcd19c7-97e7-4b31-9850-4d68bbcc8b23)
  ![Screenshot 2024-12-31 000525](https://github.com/user-attachments/assets/3c728739-f489-430c-9f91-09a4bba1588d)
  ![Screenshot 2024-12-31 000536](https://github.com/user-attachments/assets/985b3299-65b1-4d3f-9d14-df927c03b9c8)

7️⃣ Review Features  
- On the Features tab, leave everything as is, then click `Next`.  

  ![Screenshot 2024-12-31 000542](https://github.com/user-attachments/assets/78136f6a-6a4f-4b78-b347-479015962083)

8️⃣ Confirm Installation  
- On the AD DS tab, click `Next`, then `Install` on the Confirmation tab.  

  ![Screenshot 2024-12-31 000547](https://github.com/user-attachments/assets/25a8f8d0-fde5-43c7-946e-9b8758cd5a8f)
  ![Screenshot 2024-12-31 000558](https://github.com/user-attachments/assets/2925c475-10e1-4182-a63f-54b793c11751)
  ![Screenshot 2024-12-31 000637](https://github.com/user-attachments/assets/b2f79e7e-40ed-4bab-ac77-b59394cfbf12)

---

## 🌳 Promote to Domain Controller

9️⃣ Start Promotion  
- After installation, click `Promote this server to a domain controller`.  

  ![Screenshot 2024-12-31 001444](https://github.com/user-attachments/assets/61a5b6f4-e561-4610-b780-62916663398d)

- Add a New Forest: I chose to use `goodcorp.com`.  

  ![Screenshot 2024-12-31 001609](https://github.com/user-attachments/assets/c52bdb0f-9b8d-4518-a96d-34e85b6d1cd8)

🔟 Set Domain Controller Options  
- Input a password and click `Next`.  

  ![Screenshot 2024-12-31 001704](https://github.com/user-attachments/assets/68ed86d6-8756-4b97-99a0-2a014152423b)

---

## 🔗 Configure Additional Settings

- DNS Options: Leave unchecked and click `Next`.  

  ![Screenshot 2024-12-31 001802](https://github.com/user-attachments/assets/a5e73027-9c07-474e-b6e2-8c4db2cd0a68)

- NetBIOS Name: Leave as is and click `Next`.  

  ![Screenshot 2024-12-31 001819](https://github.com/user-attachments/assets/126cedc0-4881-49fb-a9b7-afc20d7e1b71)

- Paths Tab: Keep defaults and click `Next`.  

  ![Screenshot 2024-12-31 001829](https://github.com/user-attachments/assets/15aae331-8cc1-4401-92e8-e2af55f0d473)

- Review Tab: Click `Next`.  

  ![Screenshot 2024-12-31 001841](https://github.com/user-attachments/assets/023c6f47-42bc-4d32-ba3a-3c5b452b8f94)

- Prerequisites Check: Click `Install`.  

  ![Screenshot 2024-12-31 001859](https://github.com/user-attachments/assets/31db2f43-57ce-481f-bf0a-a7d890b8e4cc)

---

## 🔄 Final Steps

✅ Installation Complete  
- Once the installation is complete, the VM will automatically restart.  

  ![Screenshot 2024-12-31 001941](https://github.com/user-attachments/assets/865bf457-60eb-4ef9-aa66-86d8d6727a7c)

---

</details>




<!-- 1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟 -->




## 👥 Active Directory Users and Computers

As part of my Active Directory setup, I will utilize the Active Directory Users and Computers (ADUC) tool to create and manage user accounts. Specifically, I will create a Helpdesk Admin account with elevated privileges for administrative tasks and Helpdesk Support user accounts with restricted access tailored for day-to-day support operations.

<details>
<summary>👥 Creating An Admin Account & Organizational Unit</summary>

## 👥 Create an Admin Account

1️⃣ Access Active Directory Users and Computers
- On the Server Manager dashboard, click `Tools` and select `Active Directory Users and Computers`.

  ![Screenshot 2024-12-31 130031](https://github.com/user-attachments/assets/6b067f12-b5e0-463c-a109-22d47ff88de4)

- I will pin ADUC to my taskbar by right-clicking the icon and selecting `Pin To Taskbar`.

  ![Screenshot 2024-12-31 130320](https://github.com/user-attachments/assets/d63ddf3c-5f44-4b69-80c9-ac53b42f100f)

---

## 🗂️ Create A New Organizational Unit

2️⃣ Create the Admin Organizational Unit
- I'll right-click `goodcorp.com` go to `New` and select `Organizational Unit`.

  ![Screenshot 2025-01-02 105043](https://github.com/user-attachments/assets/ad381f64-64b1-404f-b226-796f8b68381c)

- I'll name the OU `ADMINS` and uncheck `Protect container from accidental deletion`, then click `OK`.

  ![Screenshot 2025-01-02 105303](https://github.com/user-attachments/assets/faa2f277-2318-4b13-a493-09029c170a12)

---

## 👥 Active Directory Account Creation

3️⃣ Account Creation

- Now that I have an `ADMINS` folder. I'll right-click the folder and select `New` then `User`.

  ![Screenshot 2025-01-02 105554](https://github.com/user-attachments/assets/9849c68b-4dd9-4bc4-b837-91482ae745f5)

- I'll input my name `Stephen Abner`, set the User logon name to `a-sabner`, then click `Next`.

  ![Screenshot 2025-01-02 105824](https://github.com/user-attachments/assets/5dc1d58f-036c-4da5-95dd-604d5b340f7f)

- On the next screen I'll input a password, uncheck `User must change password at next logon`, and check `Password never expires`, then click `Next` and `Finish`.

  ![Screenshot 2025-01-02 110117](https://github.com/user-attachments/assets/f27dafd7-b0ec-40d0-a0fe-c422d31710b7)

---

## 👥 Promote User To Admin

4️⃣ Give User Domain Admin

- Now I have my personal account created inside the ADMINS folder, But I still need to give the account admin privileges. 

  ![Screenshot 2025-01-02 110310](https://github.com/user-attachments/assets/7ac6ec2a-59af-4486-8f07-992c8236a434)

- To grant the account admin privileges, I'll right-click on the user and select `Properties`.

  ![Screenshot 2025-01-02 114236](https://github.com/user-attachments/assets/ec2286ca-a535-4d50-9380-6f308cf83aa5)

- In the properties window, I'll click `Member Of`, then click `Add` 

![Screenshot 2025-01-02 114405](https://github.com/user-attachments/assets/c6ad8ed0-2012-4ef2-9a0e-4bf920bcb15d) ![Screenshot 2025-01-02 114417](https://github.com/user-attachments/assets/da3c82ac-522e-42e1-bd58-5d08e5fc6a51)

- In the `Enter the object names to select` section, I'll input `domain admins`, then click `Check Names`

  ![Screenshot 2025-01-02 114942](https://github.com/user-attachments/assets/8dbc6656-3d01-40db-ae77-7324badc9e1e)

- After clicking `Check Names` domain admins will become underlined, click `OK` 

  ![Screenshot 2025-01-02 114959](https://github.com/user-attachments/assets/eb1c2eba-b17b-4742-8b2d-9d5e1d878dae)

- The user has now been added to `Domain Admins`. Click `Apply`, then `OK`.

  ![Screenshot 2025-01-02 115854](https://github.com/user-attachments/assets/8f33d90c-1d84-4ba4-8287-5481a1c49eb6)


</details>

<Details>
  <Summary>🗂️ Creating Department Organizational Units</Summary>

In this section, I will create the HR, and IT OU's for the users that I'll be creating later in my project.

- I'll Open Active Directory Users and Computers, right-click `goodcorp.com` then go to, `New` -> `Organizational Unit`

  ![Screenshot 2025-01-11 162812](https://github.com/user-attachments/assets/7328493a-d279-4ff3-9a1d-961ab070b6b3)

- I'll name the OU `HR`, and uncheck `Protect Container from accidental deletion`, then click `OK`.

  ![Screenshot 2025-01-11 163134](https://github.com/user-attachments/assets/a2511621-c150-448e-a4e6-94399cc61610)

- Now I'll repeat the process above and create the `IT` OU.

  ![Screenshot 2025-01-11 163255](https://github.com/user-attachments/assets/d4b8c8f9-87d6-490f-a809-22b0fa0aa2bf)

- The HR and IT OU's have been created.

  ![Screenshot 2025-01-11 163930](https://github.com/user-attachments/assets/a3222535-ec3f-4664-ac1d-eb5070cb44cb)

</Details>

<!-- 1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟 -->




## 🖥️ Configuring a Static IP
This section focuses on configuring a static IP address and performing domain joining on a Windows Server 2019 instance. The goal is to establish a stable network connection and integrate the server into an Active Directory domain for centralized management

<details>
<summary>🖥️ Configure a Static IP For The Domain</summary>

### 1️⃣ Assigning a Static IP
- To access the network adapters within the VM. I'll right-click `Start` and click `Network Connections`

  ![Screenshot 2024-12-31 223203](https://github.com/user-attachments/assets/9f9aef50-e65c-4939-8609-a7f1bc285842)

- In the Network Connections window, click `Change Adapter Options`

  ![Screenshot 2024-12-31 223220](https://github.com/user-attachments/assets/34dd4bcc-465c-45f2-b19f-42f1c1e1a931)

### 2️⃣ Identifying the Internal Adapter 

- I'll now identify the internal network adapter by right-clicking `Ethernet` and `Ethernet 2` and selecting `Status`.

  ![Screenshot 2024-12-31 224601](https://github.com/user-attachments/assets/0ab866e8-3723-4094-aaf3-dbc8a70868ca)
  ![Screenshot 2024-12-31 224626](https://github.com/user-attachments/assets/ccc3c678-332a-4efb-837a-f1ae1995e118)

- By examining the `IPv4 Connectivity` and `Sent and Received Activity`, it's clear which adapter is internet-facing and which is internal. Ethernet shows `IPv4 Connectivity: Internet`, while Ethernet 2 displays `No Network Access`.

  ![Screenshot 2024-12-31 225150](https://github.com/user-attachments/assets/8c2c5410-9ae0-45ef-87f1-48e65caa7a6f)

### 3️⃣ Verifying the Details 

- To verify, I'll click `Details` on each adapter.  
  
  ![Screenshot 2024-12-31 230549](https://github.com/user-attachments/assets/b33fa348-8062-4968-8f3a-bcda4a86af41)

- Ethernet has a valid IPv4 address, along with a Default Gateway, DHCP, and DNS servers.
- Ethernet 2 has an APIPA Address and lacks a Default Gateway or DNS server. This indicates that Ethernet 2 attempted to obtain an IP address from a DHCP server but couldn't find one.

  ![Screenshot 2024-12-31 230513](https://github.com/user-attachments/assets/76f2e1a9-2ce3-4e4b-8892-d12bc48707d4)

### 4️⃣ Renaming the Adapters

- To clarify things, I'll rename both adapters: I'll right-click on Ethernet and rename it to `Internet`, then right-click on Ethernet 2 and rename it to `Internal`.

  ![Screenshot 2024-12-31 232146](https://github.com/user-attachments/assets/1ac63a47-a75a-4928-91d0-9d1490e9fc8b)
  ![Screenshot 2024-12-31 232220](https://github.com/user-attachments/assets/6976eaf0-1c35-4076-87e2-d0510c33af4c)
  ![Screenshot 2024-12-31 232247](https://github.com/user-attachments/assets/1c07f649-976b-4dd5-be1b-18058e177b09)

### 5️⃣ Configuring the IP Settings 

- Now that the adapters have been identified and renamed, I'll right-click `Internal` and click `Properties`

  ![Screenshot 2024-12-31 232431](https://github.com/user-attachments/assets/638923fd-b16f-4915-82c1-ca97389bca8b)

- In the properties window, I'll double-click `Internet Protocol Version 4 (TCP/IPv4)`

  ![Screenshot 2024-12-31 232532](https://github.com/user-attachments/assets/95694d0c-9925-462d-b1ff-37fafa366e0c)

- I'll select `Use the following IP address` and set the IP address to `172.25.0.1`.
- The subnet mask will be configured as `255.255.255.0`.
- Finally, I'll set the Preferred DNS Server to the loopback address, `127.0.0.1`.

  ![Screenshot 2024-12-31 233719](https://github.com/user-attachments/assets/c36681dc-3bce-4b92-a29f-477083248d40)

### 6️⃣ Finalizing the Configuration

- I'll click `OK`, then restart the VM.

---

### 7️⃣ Verifying the Settings

- After the VM restarts, I'll return to Network Connections and check the Details of the internal adapter to verify that the static IP and subnet mask have been updated.

  ![Screenshot 2024-12-31 235042](https://github.com/user-attachments/assets/537c92d1-3cf5-4fef-b20a-c021c1f97cb1)

- ✅ Everything looks good!
  
</details>




<!-- 1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟 -->




## 🖥️📶🗂️ RAS, NAT, and DHCP Configuration
In this section of my homelab project, I will configure Remote Access Service (RAS), Network Address Translation (NAT), and DHCP to provide client devices with internet access through the domain. This setup includes enabling RAS for remote connectivity, configuring NAT for IP address translation, and setting up DHCP to dynamically assign IP addresses to client devices.

<details>
<summary>🖥️ Installing Remote Access Service (RAS) </summary>

### Installing RAS
- Open Server Manager, click `Add Roles and Features`, then click `Next`.

  ![Screenshot 2025-01-02 154407](https://github.com/user-attachments/assets/f8bc3fd0-befe-4c44-aad0-f624ffec59b8)
  ![Screenshot 2025-01-02 154459](https://github.com/user-attachments/assets/42bc5c89-e263-4dd1-a9d3-a55ff96215b2)

- Select `Role-based or feature-based installation`, then click `Next`.

  ![Screenshot 2025-01-02 154514](https://github.com/user-attachments/assets/292675bd-9bd6-4fa5-90b3-8b03d85c55ec)

- Select `Select a server from the server pool`, then click `Next`.

  ![Screenshot 2025-01-02 175613](https://github.com/user-attachments/assets/15658f6d-44d3-4d22-9003-e02dbb9f5e45)

- For roles, check `Remote Access`, then click `Next`.

  ![Screenshot 2025-01-02 154619](https://github.com/user-attachments/assets/b8c017ac-c97d-460f-9779-e496c3b95ab2)

- Leave as is, click `Next`.

  ![Screenshot 2025-01-02 154652](https://github.com/user-attachments/assets/1b2b1a07-5047-4ed1-ac74-a399b5afb787)
  ![Screenshot 2025-01-02 154710](https://github.com/user-attachments/assets/a50e21f3-5f72-4981-8170-b14a7706e7bf)

- Select `Routing`, then click `Add Feature`, `DirectAccess and VPN` will become checked automatically, click `Next`.

  ![Screenshot 2025-01-02 154757](https://github.com/user-attachments/assets/1fd97f61-1dc2-497e-8edf-2f626a745a87)
  ![Screenshot 2025-01-02 154738](https://github.com/user-attachments/assets/78c86947-87ec-4d3b-a7b6-bd430e37ccc4)

- Leave as is, click `Next`.

  ![Screenshot 2025-01-02 154817](https://github.com/user-attachments/assets/d947cd35-2582-4118-bfd9-cbabf9468386)

- Leave as is, click `Next`.  
 
  ![Screenshot 2025-01-02 154834](https://github.com/user-attachments/assets/4581ef11-783d-4499-b5d4-ebdfaa5f0731)

- Click `Install`, when the installation is complete, then click `Close`.

  ![Screenshot 2025-01-02 154850](https://github.com/user-attachments/assets/9ce8f0d5-0660-4b9b-9ab3-21f6d55e5c88)
  ![Screenshot 2025-01-02 154938](https://github.com/user-attachments/assets/afcf27c3-88d4-4e75-b61c-bb10109566fa)

</details>




<!-- 1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟 -->




<details>
  <summary>📶 Configuring Network Address Translation (NAT)</summary>

### 📶 Configure NAT
- Open Server Manager, go to `Tools` and select `Routing and Remote Access`.

  ![Screenshot 2025-01-02 155307](https://github.com/user-attachments/assets/02022e44-7a97-4edf-88e8-b8fa0d81aba7)

- I'll right-click my domain controller `GOODCORP_DC`, then click `Configure and Enable Routing and Remote Access`.

  ![Screenshot 2025-01-02 155412](https://github.com/user-attachments/assets/d3033524-33b0-4f03-8b55-386b2f4603c3)

- When the install wizard appears, click `Next`.

  ![Screenshot 2025-01-02 155431](https://github.com/user-attachments/assets/9b00e80e-f9f5-4c7f-8679-0d755317ff3a)

- Select `Network address translation`, then click `Next`.

  ![Screenshot 2025-01-02 155500](https://github.com/user-attachments/assets/b763aa99-d2e2-4788-b5fc-70a6458d15b3)

- I'll select `Use this Public Interface to connect to the Internet`, then I'll select the `Internet` adapter that I renamed in the `Configuring A Static IP` section. then click `Next`.

  ![Screenshot 2025-01-02 193404](https://github.com/user-attachments/assets/3bc646b4-8f3f-4a56-9c6c-dc3bf9ad3333)

- Click `Finish` to complete the setup.

  ![Screenshot 2025-01-02 194213](https://github.com/user-attachments/assets/aaa8f8ad-3d0a-4427-bb1f-6625da805dc6)

- Now the `GOODCORP-DC` domain has a green UP arrow and is configured properly.

  ![Screenshot 2025-01-02 194504](https://github.com/user-attachments/assets/7be210e3-4ca9-4ac1-add8-24863cfac367)

</details>




<!-- 1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟 -->




<details>
  <summary>🗂️ Configuring Dynamic Host Configuration Protocol (DHCP)</summary>

### 🗂️ Installing DHCP features
- Open Server Manager, click `Add roles and features` then click `Next`.

  ![Screenshot 2025-01-02 200721](https://github.com/user-attachments/assets/0ce2c226-0884-4880-8857-2ef51f6a1d4a)

- Select `Role-based or feature-based installation`, then click `Next`.

  ![Screenshot 2025-01-02 200844](https://github.com/user-attachments/assets/bf4d9a7d-67f4-44b5-89c2-0092ff365c52)

- Click `Select a server from the server pool`, then click `Next`.

  ![Screenshot 2025-01-02 201003](https://github.com/user-attachments/assets/77e037f8-a8a9-488b-993e-5e118279e280)

- For roles, select `DHCP Server` then click `Add Features`, then click `Next`.

  ![Screenshot 2025-01-02 201135](https://github.com/user-attachments/assets/71bb4d4c-93b5-42e9-a811-5a73bf196835)
  ![Screenshot 2025-01-02 201146](https://github.com/user-attachments/assets/e950e4c2-e552-419c-a403-bb87fbdb3ccd)

- Leave features as is, click `Next`

  ![Screenshot 2025-01-02 201347](https://github.com/user-attachments/assets/735841a3-2bad-45f4-8687-0353dab4aad7)

- Click `Next`

  ![Screenshot 2025-01-02 201430](https://github.com/user-attachments/assets/ddab1078-6afc-4b43-8316-eeb659ae166e)

- And finally, I'll click `Install` and wait for the installation to complete, then click `Close`

  ![Screenshot 2025-01-02 201529](https://github.com/user-attachments/assets/bafc33f3-f505-458a-a366-9e8189774965)
  ![Screenshot 2025-01-02 201605](https://github.com/user-attachments/assets/0eef400e-6e2d-42f8-aaae-9e4b90755638)

- Setup complete! In the next section, I'll set up the DHCP scope.
  
</details>




<!-- 1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟 -->




## 🗂️ DHCP Scope Setup
With RAS, NAT, and DHCP set up, the next step is to configure the DHCP scope. The DHCP scope defines a range of IP addresses that the server can assign to client devices on the network. These IP addresses will be dynamically allocated to devices as they connect to the network.

<details>
  <summary>🗂️ DHCP Scope Setup</summary>
  
### 🗂️ Access DHCP Control Panel
- I'll Open Server Manager, go to `Tools` and click `DHCP`.

  ![Screenshot 2025-01-02 202021](https://github.com/user-attachments/assets/dbbf90bd-a939-4e09-8607-81b4a4398ab6)

- Within the control panel, I'll expand `goodcorp-dc.goodcorp.com`. Notice that `IPv4` and `IPv6` have a red down arrow.

  ![Screenshot 2025-01-02 204621](https://github.com/user-attachments/assets/99516fe8-a540-40d0-b714-36c1a8c3102e)

- I'll right-click `IPv4`, click `New Scope`, then click `Next`.

  ![Screenshot 2025-01-02 205926](https://github.com/user-attachments/assets/3d622416-a3a0-4802-be4e-fabbf37c16ec)

- I'll name the scope `172.25.0.100-200`, then click `Next`.

  ![Screenshot 2025-01-02 210130](https://github.com/user-attachments/assets/273f132d-ed15-4232-a0f1-805da7e37a38)

- For the range, I'll set
  - Start IP Address to `172.25.0.100`
  - End IP Address to `172.25.0.200`
  - I'll set the length to `24` so the subnet mask is `255.255.255.0`
- Then click `Next`

  ![Screenshot 2025-01-02 210757](https://github.com/user-attachments/assets/6196be07-625d-43eb-9596-b23918fd7b8a)

- I don't need exclusions, so I'll click `Next`.

  ![Screenshot 2025-01-02 211036](https://github.com/user-attachments/assets/18398b92-7b58-4bb0-bf4a-994f8a371774)

- I'll leave the lease duration at `8 Days`, then click `Next`.

  ![Screenshot 2025-01-02 211201](https://github.com/user-attachments/assets/30b98662-57b7-4833-98cd-0c0b59c0021c)

- On the next window, I'll select `Yes, I want to configure these options now` then click `Next`.

  ![Screenshot 2025-01-02 211322](https://github.com/user-attachments/assets/0084d5e1-6f3b-4dd6-9f2b-229bfb0a471e)

- Since the clients will use the Domain Controller's Internal NIC as the default gateway, I will input the Domain Controller's IP address, click `Add` then click `Next`.

![Screenshot 2025-01-02 211910](https://github.com/user-attachments/assets/1d07b5c3-7791-4489-b3ab-4ba8020fa343)

- The goodcorp.com domain and DNS is already there, so I'll click `Next`.

  ![Screenshot 2025-01-02 212320](https://github.com/user-attachments/assets/335ffaac-cd80-4db6-9bad-ca907b632eb0)

- I'll skip WINS Servers, and click `Next`.

  ![Screenshot 2025-01-02 212409](https://github.com/user-attachments/assets/6dc37d9f-ece2-4570-93c4-a077d55563eb)

- I'll make sure `Yes, I want to activate this scope now` is selected, click `Next`, and `Finish`.

  ![Screenshot 2025-01-02 212434](https://github.com/user-attachments/assets/33b4d60c-3dc2-44b9-a621-92139c1d3b36)

- I noticed IPv4 and IPv6 still had a red down arrow

  ![Screenshot 2025-01-02 212704](https://github.com/user-attachments/assets/8aff448b-322f-45fd-97ae-e43f160d1553)

- To fix this, I'll right-click the domain, and select `Authorize`. Then right-click again, and select `Refresh`.

  ![Screenshot 2025-01-02 212749](https://github.com/user-attachments/assets/a77738eb-40c7-49a2-8609-8deefd9f29ca) ![Screenshot 2025-01-02 212811](https://github.com/user-attachments/assets/e9160bff-f20f-4265-b186-3757676b5ec9)

- IPv4 and IPv6 now have green checkmarks! The DHCP scope and DNS are set up properly. 

![Screenshot 2025-01-02 212839](https://github.com/user-attachments/assets/1802ad18-589d-44a5-8f8a-5eb99dfc7d20)

</details>




<!-- 1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟 -->



 
## 👥 Configure Admin User, Install RSAT Tools, and Join PC to GoodCorp Domain
This section outlines the process of setting up an administrative user, joining a client PC to a domain, and installing Remote Server Administration Tools (RSAT) to manage Active Directory components.

<details>
  <summary>👥 Configure the Admin User</summary>

### 🖥️ Enable the Admin Account

- I'll open Virtualbox and start the Windows 10 VM.

- Open File Explorer, right-click `This PC` then click `Manage`.

  ![Screenshot 2025-01-03 113518](https://github.com/user-attachments/assets/f76ecbda-01c3-487c-9694-e6a469964828)

- Within Computer Management, I'll expand `Local Users and Groups` and select `Users`.

  ![Screenshot 2025-01-03 113601](https://github.com/user-attachments/assets/05721956-3564-452d-87ec-806ca529cce7)

- I'll right-click `Administrator` and select `Properties`.

  ![Screenshot 2025-01-03 113624](https://github.com/user-attachments/assets/fc68a576-5aa4-4d56-97fa-a620b719ca5f)

- Uncheck `Account is disabled` then click `Apply` and `OK`.

  ![Screenshot 2025-01-03 113657](https://github.com/user-attachments/assets/64f0347d-a792-40f4-981b-269d06bda450)

- Right-click `Administrator`, then click `Set Password`.

  ![Screenshot 2025-01-03 113735](https://github.com/user-attachments/assets/060170f9-c513-4069-8802-a92c9fd71886)

- click `Proceed`.

  ![Screenshot 2025-01-03 113746](https://github.com/user-attachments/assets/2c5561b6-6cf5-4ab0-9da8-ee2a1387e183)

- I'll set a password, then click `OK`.

  ![Screenshot 2025-01-03 113816](https://github.com/user-attachments/assets/c9a2bbf8-924e-423d-81f4-d2c494947dc2)

- Right-click the start button, then sign out of the VM.

  ![Screenshot 2025-01-03 120734](https://github.com/user-attachments/assets/0a64b373-f268-4560-8afa-9266f1f05344)

- At the sign-in screen, click `Administrator` input the password, then log in.

  ![Screenshot 2025-01-03 120912](https://github.com/user-attachments/assets/408b7362-6254-4a0d-812e-769de928b02a)

- I'll uncheck everything, then click `Accept`.

  ![Screenshot 2025-01-03 121333](https://github.com/user-attachments/assets/43e2e3c4-2f98-476d-94fe-b03cb9320b07)

- I've been informed that Nick Burns has finally been fired, so I'll remove his account.
  - Back at `Computer Management`, I'll right-click the user `Nick Burns` click `Delete`, `Yes`, then `OK`.

    ![Screenshot 2025-01-03 121854](https://github.com/user-attachments/assets/c61ac8c4-442e-45fb-a33f-8f456ee33947)
    ![Screenshot 2025-01-03 122937](https://github.com/user-attachments/assets/0298aac1-25be-455d-824d-a123e5a16033)

- All jokes aside, the admin user has been successfully configured. Next, I’ll install RSAT tools to enable the admin user to manage Active Directory directly from this Windows 10 machine.

</details>




<!-- 1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟 -->




<details>
  <summary>🖥️ Installing RSAT Tools</summary>

### 🖥️ Install RSAT Tools

- Within the Windows 10 VM, right-click `Start` and go to `System`.

  ![Screenshot 2025-01-03 124021](https://github.com/user-attachments/assets/1c732f39-2554-4287-8a48-ea94798e0d57)

- On the left pane, scroll down and click `Optional Features`.

  ![Screenshot 2025-01-03 124146](https://github.com/user-attachments/assets/61b225ea-2af3-4d85-8b7a-383f120edbb8)

- Click `Add a feature`.

  ![Screenshot 2025-01-03 124251](https://github.com/user-attachments/assets/165732d3-2834-4f92-b088-8e8714ba3a43)

- I will select the following features:
  - RSAT: Active Directory Certificate Services tools
  - RSAT: Active Directory Domain Services and Lightweight Directory Services Tools
  - RSAT: DHCP Server Tools
  - RSAT: DNS Server Tools
  - RSAT: Group Policy Management Tools
  - RSAT: Remote Desktop Services Tools
  - RSAT: Server Manager

  ![Screenshot 2025-01-03 124531](https://github.com/user-attachments/assets/d4d11e6a-fee9-423b-aa49-30544705453d)
  ![Screenshot 2025-01-03 124551](https://github.com/user-attachments/assets/22ff1608-9cc7-47c4-9aed-6efa95b78413)
  ![Screenshot 2025-01-03 124602](https://github.com/user-attachments/assets/9e19f05b-b71c-45bd-a0ad-6bf8db30743a)

- Once selected, I'll click `Add`, then everything will begin installing.

  ![Screenshot 2025-01-03 125309](https://github.com/user-attachments/assets/987af641-01af-4718-b638-7398b0e9558b)
  ![Screenshot 2025-01-03 125333](https://github.com/user-attachments/assets/f9a4f68e-1f07-46d0-94d2-aadd377af6fd)

- When the installation is complete, I'll restart the VM.
  
- Now I can see all the tools by clicking `Start` and going to `Windows Administrative Tools`.

  ![Screenshot 2025-01-03 131424](https://github.com/user-attachments/assets/c2a3d2f4-8788-4312-96c1-9305016ade69)

- RSAT Tools is now installed! In the next section, I'll join the computer to the GoodCorp Domain.
  
</details>

<Details>
  <summary>🖥️ Joining Admin PC to the GoodCorp Domain</summary>

### 🖥️ Joining Admin PC to the Domain

- On the Windows 10 VM, I'll open CMD, click `Start` and type `CMD` then press `Enter`.

  ![Screenshot 2025-01-03 134008](https://github.com/user-attachments/assets/b648085d-32fe-40c3-8540-fa8bcb6cdf0b)

- Within CMD, I'll type `ipconfig`. The DC has given this PC the IP `172.25.0.100`. And the Gateway is the DC IP Address `172.25.0.1`.

  ![Screenshot 2025-01-03 134113](https://github.com/user-attachments/assets/c971bc0d-0f4a-417b-8683-18a556327ceb)

- Now I'll add the pc to the domain. Right-click `Start` and click `System`.
  
  ![Screenshot 2025-01-03 141901](https://github.com/user-attachments/assets/37259482-38b4-43c4-a444-06864ed3a66c)

- On the System window, I'll scroll down and click `Rename this PC (advanced)`.

  ![Screenshot 2025-01-03 141942](https://github.com/user-attachments/assets/2368bded-0751-4413-a186-2b570df445b5)

- Within System Properties, I'll click `Change`.

  ![Screenshot 2025-01-03 142227](https://github.com/user-attachments/assets/68d42e32-4637-454b-870d-7e74a3954166)

- I'll change the Computer name to `SABNER`, then I'll select `Domain` then input `goodcorp.com` and click `OK`.

  ![Screenshot 2025-01-03 142505](https://github.com/user-attachments/assets/bfeb7a50-03b8-4329-aa01-68c29e9d59be)

- A login window will appear, I'll input the user name `a-sabner` and password of the admin account that I created earlier, then click `OK`.

  ![Screenshot 2025-01-03 142737](https://github.com/user-attachments/assets/0512a4ed-8b99-43be-b1b9-6f0b4d47e422)

- I'll get a welcome screen, click `OK`.

  ![Screenshot 2025-01-03 142834](https://github.com/user-attachments/assets/3a50e673-3656-481e-b475-e63ea94bf50d)

- Then I'll get a prompt to restart the machine, click `OK`, then restart the VM.

  ![Screenshot 2025-01-03 142846](https://github.com/user-attachments/assets/5e205f41-80fb-480f-9141-1c865774b1ec)

- On the Sign In screen, I'll click `Other user`, we can now see the GOODCORP Domain and how to sign in.

  ![Screenshot 2025-01-03 153831](https://github.com/user-attachments/assets/4a9772c8-6cc8-4cc0-9a67-a66c277c0817)

- I'll input the admin account `a-sabner`, enter the password, then click `Enter`.

  ![Screenshot 2025-01-03 143638](https://github.com/user-attachments/assets/14c5c3fe-6617-403c-beb4-88b26d11915d)

- When logged in, I'll click `Start` Scroll down to `Windows Administrative Tools` and open `Active Directory Users and Computers`.

  ![Screenshot 2025-01-03 154205](https://github.com/user-attachments/assets/dc291cbb-cd81-45dd-872b-4f7db03a5899)

- Now I have access to the goodcorp.com domain and corresponding folders.

  ![Screenshot 2025-01-11 171138](https://github.com/user-attachments/assets/3c922a41-9aba-4eb2-8e60-aed00c65e684)

</Details>

<Details>
  <summary>👥 Create Users and Join PCs to the GoodCorp Domain</summary>

### 👥 Create New Users

- On the `a-sabner` admin machine, I'll click `Start`, scroll down to `Windows Administrative Tools` then click `Active Directory Users and Computers`. Also, I'll go ahead and pin it to the taskbar.

  ![Screenshot 2025-01-03 154205](https://github.com/user-attachments/assets/3438dd8e-f125-439e-9adf-d3cac90c8892)

- I'll Expand the goodcorp.com domain, right-click the `Users` folder, go to `New` and click `User`.

  ![Screenshot 2025-01-11 171400](https://github.com/user-attachments/assets/36027764-5f29-4a4d-be65-5be9449be3bd)

- I'll name the user `John Smith` and set the User logon name to `jsmith`, then click `Next`.

  ![Screenshot 2025-01-03 174207](https://github.com/user-attachments/assets/f662eaac-8ebc-4024-9991-68edcbdf46d3)

- I'll set a password and uncheck `User Must change password at next logon`, then click `Next` and `Finish`.

  ![Screenshot 2025-01-03 174500](https://github.com/user-attachments/assets/4c2c3d17-1553-43ba-937d-8918d2c2ac10)

- John Smith has now been added to users.

  ![Screenshot 2025-01-11 171423](https://github.com/user-attachments/assets/efedba54-33d2-4d10-be34-0cf9b3e4e094)

- I could have initially created John Smith in the IT OU, but I wanted to demonstrate the ability to drag and drop users between OUs.

- To move John Smith to the IT OU, simply drag and drop his account. When the confirmation pop-up appears, click `Yes`.

  ![Screenshot 2025-01-11 175012](https://github.com/user-attachments/assets/0b0c7fde-8ec3-434c-8c92-990efef83639)
  ![Screenshot 2025-01-11 175028](https://github.com/user-attachments/assets/4c275982-2bd1-4bd9-9017-1793d7ae9aa3)

- John Smith is now in the IT OU.

  ![Screenshot 2025-01-11 175449](https://github.com/user-attachments/assets/8d128daf-6a63-42a0-ba81-115b6b41f0b4)

- Now I will create another user in the `HR` OU. I'll Right-click `HR`, go to `New`, then `User`.

  ![Screenshot 2025-01-11 183851](https://github.com/user-attachments/assets/06a5e1c5-6493-4b2a-8371-102b03feef41)

- I'll name this user `Jane Doe`, and set the user logon name to `janedoe`, then click `Next`.

  ![Screenshot 2025-01-11 184045](https://github.com/user-attachments/assets/86d70f4e-fc01-43ac-933d-7463bd3028be)

- Next, I'll create a password, then uncheck `User must change password at next logon`, and check `Password never expires`, then click `Next` and `Finish`.

  ![Screenshot 2025-01-11 184319](https://github.com/user-attachments/assets/97ab16a9-0544-4f81-bb43-14f127842364)

- Jane Doe has not been added to `HR`.

  ![Screenshot 2025-01-11 184458](https://github.com/user-attachments/assets/54b8a3be-bc4c-4210-b3e9-03cf1ed6b29f)

### 🖥️ Join the User PC to the Domain

- I set up new Windows 10 VMs in VirtualBox for John Smith and Jane Doe. Next, I'll start John's VM.

- On John Smith's machine, I'll right-click `Start` and click `System`

  ![Screenshot 2025-01-03 191946](https://github.com/user-attachments/assets/92bd1253-d5c1-4026-97e9-deae399779cc)

- On the System settings window, I'll click `Rename this PC (advanced)`

  ![Screenshot 2025-01-03 192139](https://github.com/user-attachments/assets/c412c3e1-62e9-4e9c-b5bf-3b6c28f49ae3)

- On the System Properties window, click `Change`

  ![Screenshot 2025-01-03 192315](https://github.com/user-attachments/assets/4a071a5b-fb56-4b07-80a8-92799093f73f)

- I'll set the computer name to `jsmith`, click `domain` then input `goodcorp.com`, then click `OK`.

  ![Screenshot 2025-01-03 193910](https://github.com/user-attachments/assets/8dcf8a75-abcf-4afb-a654-685fb851da32)

- I'll input the username `jsmith`, enter the password, then click `OK`.

  ![Screenshot 2025-01-03 205253](https://github.com/user-attachments/assets/1d58178c-ed1f-4ae9-afb2-eaed3ded087e)

- I'll get a welcome screen, click `OK`.

  ![Screenshot 2025-01-03 142834](https://github.com/user-attachments/assets/3a50e673-3656-481e-b475-e63ea94bf50d)

- Then I'll get a prompt to restart the machine, click `OK`, then restart the VM.

  ![Screenshot 2025-01-03 142846](https://github.com/user-attachments/assets/5e205f41-80fb-480f-9141-1c865774b1ec)

- On the sign in screen, click `Other user`, input the username `jsmith`, enter the password, then click `Enter`.

  ![Screenshot 2025-01-03 215321](https://github.com/user-attachments/assets/cc14d677-2f6d-4955-ab14-50c46003a386)

- John Smith now has a computer.

</Details>



<!-- 1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟 -->

