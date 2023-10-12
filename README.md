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

![Image](

Begin by going to your DC-1 virtual machine settings. click Network Settings, the hyperlink that follows Network interface (for my case: dc-1101_z1,) IP configurations, ip config 1, switch Allocation from Dynamic to Static, Save.
