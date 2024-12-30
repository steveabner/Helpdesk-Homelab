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

   - I named my Virtual Machine `Server 2019`
   - I selected the Windows Server 2019 ISO image that I downloaded earlier.
   - I chose `Desktop Experience` from the `Edition` dropdown menu to ensure the GUI interface was installed.
  
     ![Screenshot 2024-12-30 095613](https://github.com/user-attachments/assets/7a8b04a4-6bd0-46f5-98c1-3d043a868d77)

4. **Unattended Guest OS Install Setup:**
   - I entered a username and password
   - Then set the Hostname to `GOODCORP` and the Domain Name to `goodcorp.com`, then clicked next.

   ![Screenshot 2024-12-30 101237](https://github.com/user-attachments/assets/ea3b3df5-d84e-4ac9-8416-0d0fee97a8e9)

5. **Configure Virtual Machine Hardware Settings:**  
   - I adjusted the processor to have `4 CPU cores` and set the base memory to `4GB`, then clicked next

     ![Screenshot 2024-12-30 102327](https://github.com/user-attachments/assets/061c035b-8fd4-4f57-9bf2-ee66c5dde676)

   - I set the virtual hard disk size to `50.00GB`, then clicked next

      ![Screenshot 2024-12-30 103255](https://github.com/user-attachments/assets/0b1a7605-65f7-4893-bb85-e39973ebf9c4)

   - Then click Finish

     ![Screenshot 2024-12-30 103317](https://github.com/user-attachments/assets/947730a2-d6cb-45da-8d7f-3970f32a3ad2)

6. **Install Windows Server 2019:**  
   - Once the virtual machine was set up, it started and automatically installed Server 2019.

     ![Screenshot 2024-12-30 103410](https://github.com/user-attachments/assets/42b09384-e1f8-4815-a280-d2bf32a2b8a1)

   - If you are following along and your virtual machine does not start automatically, just select your VM and click `Start`
  
     ![Screenshot 2024-12-30 104134](https://github.com/user-attachments/assets/7edc6fc4-1556-4406-96ee-de5e4400a55a)

   - Now my Virtual Machine is set up and operating properly.
     ![Screenshot 2024-12-30 111039](https://github.com/user-attachments/assets/f7e23cec-1efd-4d81-92c8-125c7e41b602)

</details>

<details>
<summary>Troubleshooting laggy mouse and scaling issue</summary>

   - Now that the virtual machine is configured and operating properly, I noticed the mouse was laggy and the display scaling was a bit off.

     ![Screenshot 2024-12-30 111039](https://github.com/user-attachments/assets/f7e23cec-1efd-4d81-92c8-125c7e41b602)

   - To fix this, I clicked `Devices` and selected `Insert Guest Additions CD images...`

     ![Screenshot 2024-12-30 111509](https://github.com/user-attachments/assets/7b1684a1-5a8a-4f5a-91d1-82541c3ba5c1)

   - Then I opened `File Explorer` and opened `This PC`
   - Under `Devices and Drives` I opened `CD Drive (D:) VirtualBox Guest Additions`

     ![Screenshot 2024-12-30 112400](https://github.com/user-attachments/assets/c9a9d62d-d1fd-4068-bcc2-89b45c5ddf77)
   
   - Within this drive, I opened and installed `VBoxWindowsAdditions-amd64`

     ![Screenshot 2024-12-30 112416](https://github.com/user-attachments/assets/18c984f6-9eb0-4a0c-b46d-3f75ad092226)

   - Then I rebooted the virtual machine.
   - Now my mouse isn't laggy and I can resize the virtual machine window to my liking. 😊


<!--## Setting up VirtualBox with Windows Server 2016

<details>
<summary>VirtualBox Server 2016 Intial Setup</summary>
  
---  

This section outlines the configuration of VirtualBox to host a Windows Server 2016 virtual machine, which serves as the domain controller. The server is configured with role-based features, including Active Directory Domain Services (AD DS), to simulate a fully functional domain environment. This setup provides a foundation for demonstrating user account management, group policy implementation, and other key administrative tasks.



---

</details> -->
