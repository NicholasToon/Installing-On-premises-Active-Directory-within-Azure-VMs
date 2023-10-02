<p align="center">
<img src="https://i.imgur.com/CtGfsq8.png" alt="osTicket logo"/>
</p>

# Building Intuition for DNS
In this tutorial, let's simplify things and make it easy to understand DNS. We'll explore DNS A-Records on a server, creating and deleting records. We'll also dive into concepts like CNAME records and Root hints.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Command Line
- Microsoft Active Directory

## Operating Systems Used

- Windows 10 (21H2)

## List of Prerequisites

- Active Directory Virtual Machine
- Client Machine joined to your domain
- Microsoft Azure with two pre-configured VMs: Client-1 and DC-1
- Microsoft Active Directory installed on DC-1 and promoted to a domain controller

## Video Demonstration
To make it even easier for you to understand DNS concepts and the exercises we'll be doing, we've prepared a video demonstration. This video will guide you visually through the steps involved in building intuition with DNS.  Further down there are some notes and screenshots provided for highlights of some or all of the material.

### [Building Intuition with DNS](https://drive.google.com/file/d/1hh8iskP98lgcyR_fRVLUTXlAIvu7UoWn/view?usp=drive_link)

Now, let's jump into the lab exercises and explore DNS A-Records, DNS caching, and CNAME records.

## Lab Steps

**A-Record Exercise**

First, let's take a look at DNS A-Records on the server. A-Records are mappings from hostnames to IP addresses. Follow these steps:

1. Log in to DC-1 as your domain admin account (mydomain.com\jane_admin).
2. Log in to Client-1 as an admin (mydomain\jane_admin).
3. From Client-1, try to ping "mainframe." You'll notice that it fails.
4. Use nslookup to check "mainframe" and observe that there is no DNS record.
5. Create a DNS A-record on DC-1 for "mainframe" and point it to DC-1's private IP address.
6. Go back to Client-1 and try to ping "mainframe." You'll see that it works now.

![image](https://github.com/JasonDelahoussaye/BuildingIntuitionWithDNS/assets/106440235/75f4bdec-4518-4e0e-9480-1ce355c3958f)


**Local DNS Cache Exercise**

1. Go back to DC-1 and change the record address of "mainframe" to 8.8.8.8.
2. Return to Client-1 and ping "mainframe" again. Notice that it still pings the old address.
3. Check the local DNS cache using the command `ipconfig /displaydns`.
4. Flush the DNS cache using the command `ipconfig /flushdns`. Observe that the cache is now empty.
5. Try to ping "mainframe" again. You'll see that the new record address is now shown.

![image](https://github.com/JasonDelahoussaye/BuildingIntuitionWithDNS/assets/106440235/c1c1002f-3aac-4dfc-b518-ce9da96b578a)
![image](https://github.com/JasonDelahoussaye/BuildingIntuitionWithDNS/assets/106440235/f90770ef-8fec-45d1-b492-c51c159fad16)


**CNAME Record Exercise**

1. Go back to DC-1 and create a CNAME record that points the host "search" to "www.google.com."
2. Return to Client-1 and attempt to ping "search." Observe the results of the CNAME record.

![image](https://github.com/JasonDelahoussaye/BuildingIntuitionWithDNS/assets/106440235/2532e52e-84d7-4d3a-b9c1-3968ff5f96c9)


3. On Client-1, use `nslookup` to query "search" and observe the results of the CNAME record.

By following these steps, you'll develop a better understanding of DNS, A-Records, DNS caching, and CNAME records.
