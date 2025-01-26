# Azure-Network-Protocols

   ![image](https://github.com/user-attachments/assets/859d9d95-971e-432b-817a-3f42db915b5e)

 Networking Lab (Creating our Resources in Azure)

## Network Security Groups/ Inspecting Traffic Between Azure Virtual Machines

## Environments and Technologies Used

Microsoft Azure (Virtual Machines/Computer)

Remote Desktop Connection

Wireshark

Active Directory Domain Services

PowerShell

## Operating Systems Used

* Windows 10 (21H2)
  
* Ubuntu Server 20.04

## High-Level Steps

* Observe ICMP Traffic , SSH Traffic, DHCP Traffic, DNS Traffic, RDP Traffic

  
## Part 1: Create a Windows 10 Virtual Machines

1. Create a Resource Group
2. Create a Windows 10 Virtual Machine (VM)
   
    a. While creating the VM, select the previously created Resource Group
   
    b. While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet
4. Create a Linux (Ubuntu) VM
   
    a. While creating the VM, select the previously created Resource Group and Virtual Network—the Virtual Network MUST BE THE SAME.
   
    b. Authentication type: Username/Password
6. Ensure both VMs are in the same Virtual Network / Subnet
7. End the lab, but keep both VMs for Part 2!

## Sample Images while creating a Linux Virtual Machine

![image](https://github.com/user-attachments/assets/7ffa7abe-faa7-4e35-96eb-cdea2663a77f)

![image](https://github.com/user-attachments/assets/d2746f47-c7e9-40c1-aee7-288642a7fb31)


## Testing Connection of VM IP address on my pc using Remote Desktop Connection

![image](https://github.com/user-attachments/assets/90bce0ea-672f-4c73-a0b7-a071ff350924)

Successful Display after Logging In

![image](https://github.com/user-attachments/assets/4640fed5-1bac-49bf-a100-0be4a0a5a8b0)



## Part 2

https://portal.azure.com/
(Observe ICMP Traffic)

6. If using Mac, install Microsoft Remote Desktop.
   
7. Use Remote Desktop to connect to your Windows 10 Virtual Machine
   
8. Within your Windows 10 Virtual Machine, Install Wireshark (To track all the Network Traffic coming and going trough the Virtual Machines)
    
9. Open Wireshark and start packet capture
    
10. Within Wireshark, filter for ICMP traffic only

![image](https://github.com/user-attachments/assets/6103bd9d-2b99-49c0-b0e5-ccb8515a48b5)

    
11. Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM
    
    a. Observe ping requests and replies within WireShark
    
    Live Pinging Linux-VM to check if the connection is successful:
    
    ![image](https://github.com/user-attachments/assets/4897fea9-3cef-4da7-856f-7feb88c65c35)

    
12. From The Windows 10 VM, open the command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in Wireshark.


## Part 3
* (Configuring a Firewall [Network Security Group])
  
13. Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM (Ping + IP Address + space + -t)
    
    a. Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
    
    ![image](https://github.com/user-attachments/assets/91af2f84-4e0e-4eb8-ac31-fe9e9f569773)

    
    b. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
     
    ![image](https://github.com/user-attachments/assets/1fe747cf-906e-4848-9f32-469b483b8245)

    
    c. Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is
    
    d. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)

    ![image](https://github.com/user-attachments/assets/e1e74883-300b-4371-a5cd-ed7aee66a603)

    
    e. Stop the ping activity


* (Observe SSH Traffic)
14. Log back into the windows-vm

15. Back in Wireshark, start a packet capture up

16. Filter for SSH traffic only

17. From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)

18. Open PowerShell, and type: ssh labuser@<private IP address>

    a. Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
    
    b. Exit the SSH connection by typing ‘exit’ and pressing [Enter]


* (Observe DHCP Traffic)
19. Back in Wireshark, filter for DHCP traffic only
20. From your Windows 10 VM, attempt to issue your VM a new IP address from the command line
    a. Open PowerShell as admin and run: ipconfig /renew
    b. Observe the DHCP traffic appearing in WireShark

* Observe DNS Traffic)
21. Back in Wireshark, filter for DNS traffic only
22. From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are
    a. Observe the DNS traffic being show in WireShark

![image](https://github.com/user-attachments/assets/5397ac74-527b-4278-9781-7742bad5e4ea)

* (Observe RDP Traffic)
23. Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)
24. Observe the immediate non-stop spam of traffic? Why do you think it’s non-stop spamming vs only showing traffic when you do an activity?
    a. Answer: because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted

* Lab Cleanup (DON’T FORGET THIS)
25. Close your Remote Desktop connection
26. Delete the Resource Group(s) created at the beginning of this lab
27. Verify Resource Group Deletion



