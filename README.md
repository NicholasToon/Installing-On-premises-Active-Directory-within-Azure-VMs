![Image](https://i.imgur.com/W141e1T.png)

## Active Directory Installation 

With this tutorial, we will install Active Directory on-premises within Microsoft Azure. The process will involve using two virtual machines that operate on the same VNet. For now, we will utilize VM1, which will host the Active Directory and be configured as the Domain Controller. VM2 will serve as the client to simulate the everyday use of a computer in scenarios such as a business or school environment.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection (RDC)
- Active Directory Domain Services

## Operating Systems Used

- Windows Server 2022
- Windows 10 (21H2)

## Installation

Before we configure the Domain Controller's ip, we will need to create the Domain Controller itself (DC-1). The Process is quite simple. Create a virtual machine as we have done in previous turtorials, set it as Windows server 2022 for the image, Make sure to keep track of your login credentials!

Azure will inherently set the IP address of the VM to dynamic. This is not conducive to our exercise involving the client because if both VMs have dynamic IPs, they will be unable to communicate with each other. So, to ensure that the client will be able to join the domain created on DC-1 in the future, we will switch the IP configuration from dynamic to static.

![Image](https://i.imgur.com/P6oe87S.png)

![Image](https://i.imgur.com/xYqLawL.png)

Begin by going to your DC-1 virtual machine settings. Click on **Network Settings**, then the hyperlink that follows **Network interface** (in my case: dc-1101_z1). Next, navigate to **IP configurations**, select **IP config 1**, and switch the **Allocation** from **Dynamic** to **Static**. Finally, click **Save**.

![Image](https://i.imgur.com/DNngp7N.png) 

Next, we shall set the Cient's DNS settings. Copy the private IP address of DC-1. This will allow us to manually ensure our VMs are linked for the active directory process.

![Image](https://i.imgur.com/kUbptyu.png)

Follow the previous stpe for navigation to Client's network interface settings, instead of IP configurations, we will be clicking DNS servers, click Custom under DNS servers, and input the private IP that we copied from DC-1, and Save. Return to the Overview of Client (not the Client's Network interface) and restart the VM to allow the changes to take effect. 

