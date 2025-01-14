# Azure_Resources

 Networking Lab (Creating our Resources in Azure)
 
## Part 1: Create a Windows 10 Virtual Machines

![image](https://github.com/user-attachments/assets/859d9d95-971e-432b-817a-3f42db915b5e)


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

Successful Display after Loggin In

![image](https://github.com/user-attachments/assets/4640fed5-1bac-49bf-a100-0be4a0a5a8b0)



## Part 2

https://portal.azure.com/
(Observe ICMP Traffic)

6. If using Mac, install Microsoft Remote Desktop.
   
7. Use Remote Desktop to connect to your Windows 10 Virtual Machine
   
8. Within your Windows 10 Virtual Machine, Install Wireshark
    
9. Open Wireshark and start packet capture
    
10. Within Wireshark, filter for ICMP traffic only
    
11. Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM
    
    a. Observe ping requests and replies within WireShark
    
12. From The Windows 10 VM, open the command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in Wireshark.

