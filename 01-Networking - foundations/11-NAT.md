## NAT
Also known as Network address protocol is a technique used by routers and other network devices to translate IP addresses as packets pass between the networks,In a home network NAT allows multiple devices using private IP addresses to share one public IPV4 address when accessing the internet,devices on a network can have different private IP addresses but share a public IP address for internet access
### Example
(Laptop-----192.168.1.10,phone-------192.168.1.20,PC-------192.168.1.30)------Router------public IP 2020.113.10------Internet.
The devices use private addresses inside the local network, the router performs NAT so their outbound traffic can use the public IP address
### How NAT works
My Laptop sends a packet to a server on the internet then the packet leaves my laptop with its private source IP address then the router translates the source address to its public IP address then the router tracks the translation so it can associate returning traffic with the correct device and when a reply comes the router translates the destination information back and forwards it to my PC.Many home routers can also translate port number(PAT) which stands for port address translation or also known as NAT overload
### Why NAT is useful
They conserve public IPV4 addresses,
They allow many private devices on a home network to share a public IPV4 address,
Connect private networks to the internet,
They keep internal addressing seperate from addresses used on the public internet
### NAT and Cybersecurity
NAT is not like a firewall it translates address information while a firewall applies rules to permit or block traffic.A home router uses both NAT and firewall rules to manage internet connections,Private IP addresses are not directly routable across the public internet but does not mean that NAT alone can guarantee safety or security
### What I have learned
NAT is not the same as a firewall it translates ip address information as traffic moves between networks.In a home network many devices use private IP adresses and share a public IPV4 address when accessing the internet.(Private IP------Router performs NAT--------Public IP-------Internet) NAT helps to conserve public IPV4 addresses while firewall rules provide a seperate layer of traffic controll on the network
