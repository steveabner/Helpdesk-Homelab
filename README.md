# Virtualbox Server 2019 Helpdesk

# Introduction
This project demonstrates a simulated IT helpdesk environment using VirtualBox, Windows Server 2019, and Active Directory. The setup showcases core administrative skills, including user account management, group policy configuration, and basic troubleshooting techniques, designed to replicate real-world scenarios.

---

# Inital Set Up

<details>
<summary>Steps to Configure VirtualBox and Install Server 2019</summary>

1. **Download and Install VirtualBox:**  
   - Visit the [VirtualBox website](https://www.oracle.com/virtualization/technologies/vm/downloads/virtualbox-downloads.html) and download the latest version for your operating system.  
   - Follow the installation wizard to complete the setup.

2. **Download the Windows Server 2019 ISO:**  
   - To download the Server 2019 ISO, I went to the [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/) and searched for "Windows Server 2019."  

3. **Create a New Virtual Machine:**  
   - Open VirtualBox and click `New`.
     
     ![Screenshot 2024-12-30 095417](https://github.com/user-attachments/assets/7116c63c-d6a3-4a0d-a759-9df440eea598)

   - I named the virtual machine `Server 2019` and selected the Windows Server 2019 ISO image, then clicked `Next`.
    
     ![Screenshot 2024-12-30 095613](https://github.com/user-attachments/assets/7a8b04a4-6bd0-46f5-98c1-3d043a868d77)

4. **Unattended Guest OS Install Setup:**
   - I entered a username and password
   - Then set the Hostname to `GOODCORP` and the Domain Name to `goodcorp.com` then clicked `Next`.

   ![Screenshot 2024-12-30 101237](https://github.com/user-attachments/assets/ea3b3df5-d84e-4ac9-8416-0d0fee97a8e9)

5. **Configure Virtual Machine Hardware Settings:**  
   - I adjusted the processor to have 4 CPU cores and set the base memory to 4 GB, then clicked `Next`

     ![Screenshot 2024-12-30 102327](https://github.com/user-attachments/assets/061c035b-8fd4-4f57-9bf2-ee66c5dde676)

6. **Install Windows Server 2019:**  
   - After setting up the virtual machine, it started and installed Server 2019 automatically.

     ![Screenshot 2024-12-30 103410](https://github.com/user-attachments/assets/42b09384-e1f8-4815-a280-d2bf32a2b8a1)

   - If you are following along and your virtual machine does not start automatically, just select your VM and click `Start`
  
     ![Screenshot 2024-12-30 104134](https://github.com/user-attachments/assets/7edc6fc4-1556-4406-96ee-de5e4400a55a)

   
<!--## Setting up VirtualBox with Windows Server 2016

<details>
<summary>VirtualBox Server 2016 Intial Setup</summary>
  
---  

This section outlines the configuration of VirtualBox to host a Windows Server 2016 virtual machine, which serves as the domain controller. The server is configured with role-based features, including Active Directory Domain Services (AD DS), to simulate a fully functional domain environment. This setup provides a foundation for demonstrating user account management, group policy implementation, and other key administrative tasks.



---

</details> -->
