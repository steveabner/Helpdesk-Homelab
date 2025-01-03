# Helpdesk Homelab

Welcome to my Helpdesk Homelab project! This setup demonstrates a simulated IT helpdesk environment using **VirtualBox**, **Windows Server 2019**, and **Active Directory**. It showcases core IT administrative skills, such as user account management, group policy configuration, and basic troubleshooting techniques, all designed to replicate real-world scenarios.

![Helpdesk Diagram drawio](https://github.com/user-attachments/assets/8f702151-2c27-45c6-87da-01b321d7d5ad)

---

<!--## 🖥️ Hardware Used
For the hardware setup, I am using a Beelink Ser6 Mini PC as the domain controller, while my main PC and an older MSI gaming laptop will act as user devices. To preserve the original operating systems on all systems, I will utilize VirtualBox to create virtual machines on each device.-->

<!--<details>
<summary> Here are a couple of pictures for nerds, like me 😊</summary>

  ![1000001973](https://github.com/user-attachments/assets/f65b355a-97fa-4618-8f96-78643b99318b)
  ![1000001972](https://github.com/user-attachments/assets/6957e9d5-d26d-48c4-9ef7-ad7b1bc7d492)
</details>-->

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








## 👥 Active Directory Users and Computers

As part of my Active Directory setup, I will utilize the Active Directory Users and Computers (ADUC) tool to create and manage user accounts. Specifically, I will create a Helpdesk Admin account with elevated privileges for administrative tasks and Helpdesk Support user accounts with restricted access tailored for day-to-day support operations.

<details>
<summary>👥 Creating An Admin Account</summary>

## 👥 Active Directory Users and Computers

1️⃣ Access Active Directory Users and Computers
- On the Server Manager dashboard, click `Tools` and select `Active Directory Users and Computers`.

  ![Screenshot 2024-12-31 130031](https://github.com/user-attachments/assets/6b067f12-b5e0-463c-a109-22d47ff88de4)

- I will pin ADUC to my taskbar by right-clicking the icon and selecting `Pin To Taskbar`.

  ![Screenshot 2024-12-31 130320](https://github.com/user-attachments/assets/d63ddf3c-5f44-4b69-80c9-ac53b42f100f)

---

## 👥 Create A New Organizational Unit

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





<!-- 1️⃣2️⃣3️⃣4️⃣5️⃣6️⃣7️⃣8️⃣9️⃣🔟 -->

<!--## 👥 Create The Helpdesk Admin

2️⃣ Create A New Admin User
- In the left pane of the ADUC window, I will expand `goodcorp.com` and select `Users`.

  ![Screenshot 2024-12-31 133217](https://github.com/user-attachments/assets/3b05a51d-5795-4c76-ab0d-69e14870aa47)

- Since we already have an admin account, I'll just right-click `Administrator` and click `Copy`. (Copying makes life easier)

  ![Screenshot 2024-12-31 133617](https://github.com/user-attachments/assets/535df790-7557-43c4-ba2b-fc386e17a4f2)

- A `Copy Object - User` window will appear, I'll set the First name to `Helpdesk` and the User logon name to `Helpdesk` then click `Next`

  ![Screenshot 2024-12-31 134330](https://github.com/user-attachments/assets/4590eb2f-2c9c-46ca-b467-f6eb1441f760)

- Input a password, and make sure `Password never expires` is checked, then click `Next`, and `Finish`

  ![Screenshot 2024-12-31 134731](https://github.com/user-attachments/assets/374df034-fff4-4ced-adb0-76ac60d982cc)

- I now have an administrative user named Helpdesk.

  ![Screenshot 2024-12-31 134840](https://github.com/user-attachments/assets/3d25a144-6469-4d9a-af28-c0d01cd87508)

</details>

<details>
  <summary>👥 Creating My Personal Admin Account</summary>

## 👥 Active Directory Account Creation

1️⃣ Access Active Directory Users and Computers
- Open `Active Directory Users and Computers`, expand `goodcorp.com` then select `Users`

  ![Screenshot 2025-01-02 104236](https://github.com/user-attachments/assets/c070f0f4-adeb-41a2-ac35-fafe21d08fd3)
-->

  

</details>











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
- Ethernet 2 has an Autoconfiguration IPv4 Address and lacks a Default Gateway or DNS server. This indicates that Ethernet 2 attempted to obtain an IP address from a DHCP server but couldn't find one.

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






## 🖥️📶 RAS, NAT, and DHCP Configuration
In this section of my homelab project, I will configure Remote Access Service (RAS), Network Address Translation (NAT), and DHCP to provide client devices with internet access through the domain. This setup includes enabling RAS for remote connectivity, configuring NAT for IP address translation, and setting up DHCP to dynamically assign IP addresses to client devices.

<details>
<summary>🖥️📶 Installing Remote Access Service (RAS) </summary>

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


<details>
  <summary>🖥️📶 Configuring NAT</summary>

### Configure NAT
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

