## Firewalls-and-Network-Filtering
A firewall is a security control policy that monitors network traffic and allows or blocks the traffic according to the rules configured, A firewall helps to protect companies or networks from unwanted connections, for example a firewall can allow web browsing and still block unauthorized attempts to connect to sensitive service on the network of the company 
## How does a Firewall work 
A firewall evaluates packets, flows or connections against configured rules depending depending on the design and the operating context, the rules may consider, Source IP address: where traffic comes from, Destination IP address where the traffic is going, protocols such as TCP,UDP or ICMP, source and destination ports,connection state, such as whether traffic belongs to an established connection network interface or other information depending on the firewall type then the firewall applies the actions of rejecting, logging or dropping the traffic 
## Inbound and Outbound traffic 
Inbound traffic enters a device or a network from another system while outbound traffic leaves the device or network towards another system for instance a firewall may block unexpected inbound connections to a laptop while allowing the laptop to initiate an outbound HTTPS connection and permitting the response traffic, the behaviour depends on the rules configured and the location of the firewall. Not every firewall blocks automatically all the inbound traffic or allows all outbound traffic 
## Statefull and Stateless Firewalls
Stateful Firewalls maintains the state information about the flows or the connection using  details such as source and destination address, ports and the type of protocol for instance it can know response traffic belonging to a connection that an internal computer initiated and allows it without treating it as a new connection if the rules configured allows that behaviour while a stateless firewall evaluates each packet independently against its rules and does not maintain connection state in the same way, to permit a bidirectional exchange, rules need to account explicitly for traffic in both directions and for the return packets, stateless  filtering is simple and efficient but requires a more detailed rules, both approaches are usefull and other systems combine both 2 firewall mechanisms to enhance security 
## Common Firewall Rules
A  rule can allow https traffic to a web server e.g Destination: approved web server, protocal: tcp , Destination port: 443 and action: Allow another one is a rule can block unauthorized access to SSH e.g Destination: protected server, Protocol:TCP, Destination port:22 source: Untrusted network, Action: Deny or drop and these are just simplified examples, A real configuration must account for the network design, traffic direction,rule order, default policy, connection state, and existing rules
## The Principle Of Least Priviledge
It means allowing only the access required for a task, for firewall configuration this means avoiding unnecessary broad rules for instance if only adminisistrators need SSH access, it is safer to restrict to the approved administrator addresses or networks instead of exposing it to everyone, the firewalls rules should be reveiwed and tested to avoid accidentally blocking legitimate services or leaving unecessary access open
## Difference between Firewall and NAT 
NAT translates network addresses and in some cases also the transport layer port numbers, the PAT also known as port address translation used in home routers can allow multiple internal hosts to share one public IPV4 address, while a firewall controls traffic by allowing, rejecting or dropping traffic according to rules, A home router performs both functions but are not the same thing, NAT affects which connections are directly addressable but NAT alone is not a complete security policy, fire wall rules matter
## Basic Firewall Inspection on Kali Linux
nftables on kali is a framework used to configure packet filtering and other network functions, the current rules can be inspected by sudo nft list ruleset if the command says no ruleset exists then it means there are no nftable rules configured in that environment but it does not prove that every other firewall or security control is absent, some systems also use ufw which is a simple interface for firewall management but before changing the firewall rules one should first understand the existing configuration because a careless change could interupt network access 
## Firewalls in Cybersecurity 
They help defenders reduce exposure of unecessary services, restrict access to sensitive systems, seperate trusted and untrusted network zone. Limit the spread of some attacks, record or investigate suspicious traffic when logging is enabled but however a firewall can not prevent each and every attack, compromised credentials, malicious files, vulnerable applications and insider threats may require additional security measures 
## What I have Learnt 
A firewall controls network traffic using configured rules based on information such as IP address, protocols, ports and connection state, stateful firewalls track connections while stateless firewalls evaluate packets without connection tracking, good firewall rules follow least privillege and should be reveiewed very carefully 
## My Key Takeaways
Firewall allows, drops and blocks traffic based on the rules configured , Inbound traffic enters a device or a network while outbound traffic leaves it, Stateful firewalls track connection state while stateless firewalls evaluate packets without tracking the connection state, least privillege means granting only the access that is needed, NAT and firewall filtering serve different purposes, firewalls are one layer of defence and is not a complete security solution, inspects the existing rules before changing the settings of the firewall 


















































































































