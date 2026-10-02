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
IP packet contains the addressing information while ethernet frames contains/carries the packet using a MAC address across the local area network.At the router,the frame coming is removed,the ip packet is processed and placed into a new frame for the next layer/link the mac address of the frame can change at every routed hop while the ip addresses source and destination usually remain the same from end to end unless NAT changes them,understanding packets and frames  helps in interpreting packet captures,troubleshoot network communication,and to learn how tools like wireshark display network traffic
