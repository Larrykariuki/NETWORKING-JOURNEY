# My practical Networking Journey
## About the journey
This repository documents my  journey of learning networking from the beginning,
My goal is to build a strong networking foundation from scratch that i can use in cybersecurity
## Learning Goals
-Understanding how computer networks operates,
-understanding how routers and switches operates,
-understanding ip address and mac address,
-learning ARP and other important network protocals,
-understanding and learning subnetting,
-learning practical networking troubleshooting skills,
-practice using networking tools,
-lean packet analysis with Wireshark,
-build practical networking labs,
-use the networking knowledge as a foundation for cybersecurity
## Learning Progress
-[x] What is a computer network?,
-[x] Network devices and nodes,
-[x] Ip addresses,
-[x] Mac addresses,
-[x] Packets,
-[x] Ethernet frames,
-[x] ARP,
-[X] Routers and switches,
-[] Subnetting,
-[] CIDR notation,
-[] Routing,
-[] VLANs,
-[] DHCP,
-[] DNS,
-[] Wireshark and packet analysis
## What is a Computer Network?
Is a group of interconnected electronic devices communicating with each other and can share data or resources with oneanother
### Example
A phone connects to a wifi and communicates with a router or a computer they form part of a network
### What i learned
A network allow electronic devices to communicate with each other and share data or resources
## Network Devices and Nodes
node is any device that can send or receive data in a network
examples include: computers, printers, servers, routers, switches, phones
### What i learned
A node is a gadget on the network can be a phone,printer or a laptop that participates in network communication
## IP Addresses
logical address assigned to a network interface (a device home address/location and which can change depending on the network or the configuration) and helps to know where network traffic should be sent
### Example
a device home address/location- like the address of a house ,if i need to send something to another house i need to know the address/location of the house same way network devices use ip addresses to send data to the correct destination
## MAC Adresses
a device fingerprint/identity and cannot change used for communication on the local network but sometimes can be spoofed or changed in software
### Example
MAC address is like a device's local network identifier, when data needs to travel from a device to another device in the same local area network the ethernet uses the mac address to deliver the data to the specific correct destination
### What I Learned
IP addresses helps to identify the destination of the network while MAC address is used to identify the specific device on the local area network
## Packets 
is the basic unit of data in the network layer and has an IP header which has information such as the source and the IP address(destination) and with the data 
### Example
like a small envelop that carries part of your data  and it has a sender's address and a destination address
### What I learned 
Packets carry data to their destinations and contain the address information that help routers to forward the data to their destination
## Ethernet frames
Is the unit of data  on the Ethernet network used for communication and has an ip packet inside it and uses mac addresses for local  delivery
An ethernet frame contains information such as the mac address of the source and the destination, ip packet and error checking information
### Example
It is like an envelope carrying another package and uses the mac address to deliver the Package (data) to its destination across the local area network(LAN)
### What I Learned 
IP packet contains the addressing information while ethernet frames contains/carries the packet using a MAC address across the local area network
## ARP
stands for address resolution protocol and is a protocol that is used in a network to discover the devices mac address that is associated  with a local ip address 
### Example
If a device knows the ip address of another device but does not know the mac address of the device on a local area network then the device shall use the ARP protocal
### What I Learned 
ARP helps the device to discover mac addresses in a ipv4 local area network
## Routers and switches
### Router
connects electronic devices on different networks and forwards packets to their intended destinations,like a post office that decides where ur packets go to next based on their ip adress(destination)
### Switch
connects electronic devices on a local network and uses mac address to forward ethernet frames to their intended destination/correct device
### What I Learned 
A router connects different networks using IP address while a switch connects devices in the local area network using mac addresses
## TCP and UDP 
These are the network layer protocals used to move data between applications 
### TCP
Makes sure that data arrives perfectly toward its destination by keeping track of what was received and requests missing data, it helps provide: Reliability, Connection Management, Correct ordering and retransmission of lost data
### UDP
Faster but less reliable protocal used in videos and prioritizes speed  and low delay over guaranteed delivery and is used in videos
### Example
TCP is like a messenger that makes sure and double checks if everything is correct before delivery while UDP is like a messenger that doesnt care as long as the message arrives as fast as it can
### What I Learned 
TCP is used when priority is given to the reliability of the data while UDP is used when speed and low delay of the data are priorities
### Network ports
It is a logical number given to a service or an application running on a device  and they work together with IP addresses and transport protocals such as TCP and UDP 
### Example
An IP address is the address of the building while the port is the room number inside the building
for example
HTTP PORT 80,
HTTPS PORT 443,
SSH PORT 22,
DNS PORT 53.
### What I Learned 
An IP address helps idenify the location of the device or its network interface while the port helps identify the application or service that should be receiving network traffic
## How Data moves across the network
when I send data from my computer to another several things happen in between on the network
### The flow of how data travels from one device to another across the network
An application creates the data, the TCP and UDP takes care of the transportation of the data to its destination, the IP adds the source and the destination of the address of the devices on the packets,by using the ARP protocal the ethernet creates an ethernet frame using mac addresses, the switch forwards the frames on the local area network, a router forwards the packets to another network when it needs to 
### What I Learned 
different network layers are used to transport data between devices and applications across  a network
## Subnetting
Dividing a network into smaller networks called subnets 
### Importance of subnetting 
Organize networks,
Reduce unnecessary network traffic,
Use IP adresses  more efficiently
seperate groups of devices
improve network  management and security
### Example
A Large neighbourhood divided into different streets
### What I Learned 
Subnetting is the process of dividing a network into smaller more manageable networks for efficiency called subnets
e.g, a /24 network can be divided into multiple /26 networks
For /26
0......63,
64......127,
128......191,
192.......255,
where there are 64 total addresses,62 usable host addresses,1 network address and 1 broadcast address,
I learned how to identify subnet boundaries 
192.168.10.0/26, 192.168.10.64/26, 192.168.10.128/26, 192.168.10.192/26,
## Network Segmentation
is the process of dividing a network into seperate segments or security zones
Organizations can use network segmentation to:
control network traffic, Restrict access  between systems,
Reduce unnecessary exposure,
limits lateral movement after a compromise,the firewall or rules for routing can controll what traffic is allowed between the segments
### What I want to learn next 
I want to move from networking theory into practical networking labs,eventually using linux and wireshark to see the concepts I am learning in real network traffic.
My goal is to build practical cybersecurity skills and document my progress on github
       

 
