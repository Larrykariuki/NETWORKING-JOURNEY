## DHCP
Stands for dynamic host configuration protocal and it automatically provides devices with the network settings that they need to communicate, without it someone needs to configure the settings manually on every device, when i need to connect my laptop to a wifi network then the DHCP will assign IP address and provide the other network settings such as the subnet mask and others. The DHCP Server provides (a) IP address which identifies the device on the network, (b) Subnet mask which shows which part of the IP address represents the network, (c) default gateway which is the routers address that the device uses to reach other networks and (d) DNS Server which the devices uses to look up the domain names 
## How The DHCP Server Works
The DHCP uses a 4 step process called DORA which stands for (a) Discover: This is whereby a client searches for a DHCP server, (b) Offer: This is whereby a DHCP server offers an IP address and network settings (c) Request: This is where the client requests the offered address then (d) Acknowledge is where the server confirms the assigned address
### Example
I want to join a wifi network using my laptop then my laptop asks is there DHCP Server? then the server replies; you can use this IP address then the laptop requests the address and the server confirms the assigned address hence the name DORA which describes the initial DHCPV4 Process.
## DHCP Lease
This is a temporary assigned IP address given to a client, the client will need to renew the lease before it expires and if it can not be renewed then the client will need to obtain a valid network configuration again, leases help network to be reusing addresses when the device has disconnected
## Why DHCP matters in Cybersecurity
It makes the network administration easier as it carries out its function of assigning IP addresses automatically to devices connecting to the network but the truth is an attacker can also abuse it
## Rogue DHCP Server
This is a server that is not authorized and  provides network settings to devices, it can supply a malicious default gateway or a DNS server and redirect the traffic or interfeer with the communications across the network
## DHCP Starvation 
Is an attack whereby you flood the address pool by sending many DHCP requests and preventing the other devices that should be receiving the address from receiving
## Defensive Measures
The network admins can reduce these risks by restricting which switch ports are allowed to provide responses to the DHCP server, Monitoring the logs of the DHCP server and request addresses that are suspicious or unusual, protecting the network equipements and limiting the attack surfaces and unauthorized physical access,using DHCP snooping on managed switches and keeping accurate record of authorized DHCP servers
## DHCP and Static IP addresses
DHCP-assigned address: Are designed automatically by a DHCP Server while a static IP Config is whereby network settings are entered  manually by an admin or user,DHCP is convenient for most of the client devices while the static config also known as DHCP reservations are useful for selected infrastructure or services
## What I have learned
The DHCP automatically provides devices on the network with IP addresses and other network settings, the process of DHCPV4 is (DORA) which stands for Discover,Offer,Request and Acknowledge. DHCP leases allow the addresses to be reused and a DHCP Server that is not authorized can provide dangerous network settings so securing DHCP helps protect the security of a network



