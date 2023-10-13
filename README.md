![Image](https://i.imgur.com/ipDQ03z.png)

## Active Directory Installation 

With this tutorial, we will install Active Directory on-premises within Microsoft Azure. The process will involve using two virtual machines that operate on the same VNet. For now, we will utilize VM1, which will host the Active Directory and be configured as the Domain Controller (DC-1), while VM2 will serve as the client (CLIENT) to simulate the everyday use of a computer in scenarios such as a business or school environment.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection (RDC)
- Active Directory Domain Services

## Operating Systems Used

- Windows Server 2022
- Windows 10 Pro (22H2)

## Set-Up

Before we configure the Domain Controller's ip, we will need to create the Domain Controller itself (DC-1). The Process is quite simple. Create a virtual machine as we have done in previous turtorials, set it as Windows server 2022 for the image, Make sure to keep track of your login credentials!

Azure will inherently set the IP address of the VM to dynamic. This is not conducive to our exercise involving the client because if both VMs have dynamic IPs, they will be unable to communicate with each other. So, to ensure that the client will be able to join the domain created on DC-1 in the future, we will switch the IP configuration from dynamic to static.

![Image](https://i.imgur.com/P6oe87S.png)

![Image](https://i.imgur.com/xYqLawL.png)

Begin by going to your DC-1 virtual machine settings. Click on **Network Settings**, then the hyperlink that follows **Network interface** (in my case: dc-1101_z1). Next, navigate to **IP configurations**, select **IP config 1**, and switch the **Allocation** from **Dynamic** to **Static**. Finally, click **Save**.

![Image](https://i.imgur.com/DNngp7N.png) 

Next, we shall set the Cient's DNS settings. Copy the private IP address of DC-1. This will allow us to manually ensure our VMs are linked for the active directory process.

![Image](https://i.imgur.com/kUbptyu.png)

Follow the previous steps to navigate to DC-1's network interface settings for Client. Instead of selecting **IP configurations**, click on **DNS servers**. Then, choose **Custom** under DNS servers and input the private IP that you copied from DC-1. Save your settings. After making these changes, return to the **Overview** of Client (not the Client's Network interface) and restart the VM to allow the changes to take effect.

![Image](https://i.imgur.com/hifXrhU.png)

![Image](https://i.imgur.com/RhVDpYE.png)

Lastly, we will enable ICMPv4 on the DC-1 Windows Firewall. Type **wf.msc** in the DC-1's search bar to open Windows Defender Firewall (or simply type **Windows Defender Firewall**). Navigate to **Inbound Rules**, scroll down to find **Core Networking Diagnostics - ICMP Echo**, and enable the rule. After enabling the rule, return to the Client, and pinging will be received, whereas it would have been previously time out.

---

## Installation 

![Image](https://i.imgur.com/7JXGzmP.png)

![Image](https://i.imgur.com/H3Lo618.png)

![Image](https://i.imgur.com/pIgbfty.png)

Back on DC-1, open **Server Manager** (if it is not already open). Click on **Add roles and features**. Proceed through the next screens by clicking **Next** three times. Under **Server roles**, check **Active Directory Domain Services** and also click **Add Features.** Click **Next** three more times, and then click **Install**.

To finish installing Active Directory, click on the flag with a caution sign adjacent to it. Choose **Promote this server to a domain controller**. Select the deployment operation: **Add a new forest**. Enter a name for your domain (for example, "mydomain.com") and press **Next**. Enter a password (you can use any password as it will not matter for the rest of the process). Click **Next** five more times, and then click **Install**.

![Image](https://i.imgur.com/PEx7SOp.png)


After installation has concluded you will be booted out of the VM so the server can be finalized. To reconnet, you will do as you have done before, but when it comes to the credentials, your previous login will not suffice for DC-1 henceforth. Instead, you will need to login the the context of the domain indicated in the text. What does this look like? Well, for me it will be User name: mydomain.com\Labuser, Password has not changed from generation.

After the installation has concluded, you will be logged out of the VM so the server can be finalized. To reconnect, follow the same steps you've done before, but when it comes to the credentials,  your previous login will not suffice for DC-1 henceforth. Instead, you will need to log in with the context of the domain indicated in the text.

This login would look something like this: For me, it will be:

- User name: mydomain.com\Labuser
- The password has not changed from generation.

Please replace "mydomain.com" with the actual domain name you specified during the setup, and "Labuser" with your specific username. Use the same password you originally set during the virtual machine's generation.

---
This concludes the setup and installation of Active Directory. From [here](https://github.com/NicholasToon/Configuring-On-premises-Active-Directory-within-Azure-VMs), we will configure the directory to enable us to explore topics such as DNS and file sharing.

Thank you for your time.









