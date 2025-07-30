# Azure Networking Lab: VM Deployment & Traffic Analysis

---

##  Part 1: Deploy Azure Virtual Machines

### Create Resources

- Log in to Azure Portal  
- Create a Resource Group  

### Create Virtual Machines

#### Windows 10 VM

- Use the created Resource Group  
- Allow it to create a new Virtual Network and Subnet  

#### Linux Ubuntu VM

- Use the same Resource Group and Virtual Network/Subnet  
- Auth: Username & Password  

 Ensure both VMs are in the same VNet/Subnet.

---

##  Part 2: Observe ICMP & Network Traffic

- Remote into Windows VM  
- Use Microsoft Remote Desktop (Mac users must install it)  
- Connect using the VM's public IP  

### Install & Use Wireshark

- Start packet capture  
- Filter: icmp  
- Ping the Ubuntu VM's private IP from the Windows VM  
- Observe ICMP request/reply in Wireshark  
- Ping a public site (e.g., www.google.com)  
- Observe ICMP traffic to external site  

---

## Part 3: Network Security Group & Protocol Observation

### Block/Allow ICMP

- Start a continuous ping from Windows → Ubuntu  
- In Azure, open the Network Security Group (NSG) for the Ubuntu VM:  
  - Block inbound ICMP  
  - Observe ping failures in Wireshark & terminal  
  - Re-enable ICMP  
  - Observe ping resumes  

---

### Observe SSH Traffic  
- Wireshark filter: ssh  

- From Windows VM, SSH into Ubuntu VM:

- ssh labuser@<private-ip>


- Type commands, observe SSH packets  

---

### Observe DHCP Traffic  
- Wireshark filter: dhcp  

- In PowerShell (admin), run:

- ipconfig /renew


- Observe DHCP traffic in Wireshark  

---

### Observe DNS Traffic  
- Wireshark filter: dns  

- Use nslookup to resolve domains:

- nslookup google.com
- nslookup disney.com


---

### Observe RDP Traffic  
- Wireshark filter:

- tcp.port == 3389


- Observe continuous RDP traffic  

- RDP is a live stream protocol, causing constant data flow.
