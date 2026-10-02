### Network ports
It is a logical number given to a service or an application running on a device  and they work together with IP addresses and transport protocals such as TCP and UDP, the TCP and UDP use port numbers ranging from 0-65535. 0---1023(well-known ports), 1024-----49151(Registered ports),  49152----65535(Dynamic/private ports), a client will use a dynamic or private port when connecting to a server
### Example
An IP address is the address of the building while the port is the room number inside the building
for example
80 TCP HTTP PORT web traffic,
443 TCP HTTPS PORT Encrypted web traffic,
22 TCP SSH PORT Secure remote administration,
53 TCP/UDP DNS PORT Domain name resolution,
25 TCP SMTP Email transmision,
3389 TCP RDP Remote Desktop.
### What I Learned 
An IP address helps idenify the location of the device or its network interface while the port helps identify the application or service that should be receiving network traffic, port numbers identify the endpoints at the transport layer but alone does not guarantee that a particular application or a service is actually running there,a network connection can be regarded as using an IP address and a port, for instance given that 192.168.1.20:443 this means that the IP address 192.168.1.20 is listening at port 443 which is associated at many times with HTTPS. A network traffic contains both a source port and a destination port for instance given that a client uses 192.168.1:52344-----TCP-----192.168.1.20:443 this means that the client is using a temporary source port while a server listens on a configured port 443,A service can listen on a port waiting for the network traffic that is intended for the service,A listening port means that a service is ready to receive traffic on that port and does not mean that it is vulnerable
### Why do ports matter
Ports matter because they help cybersecurity professionals to understand the networks that are exposed to the public,during a controlled security testing or network administration the professionals identify open ports, services that are listening on the network or ready to receive traffic, services that are not expected within the network, their versions and the unnecessary services that are exposed,every service that is available and reachable represents a part of the systems attack surface so it is important for organizations to know what they are exposing and why.
