## DNS 
Stands for Domain Name system it translates the human readable domain names into IP addresses that computers use to communicate across the network, instead of one remembering an IP Address he/she can us a domain name
### How the DNS work
When I enter a domain name in a browser,the device needs to find Its IP address www.example.com-------DNS------93.184.216.34-------server.The browser and the operating system first checks the local caches and other sources that are configured  and if the answer is not available then the device sends a query to a recursive DNS resolver that is provided by an organization or network operator or the public DNS service and if the resolver does not have the catched answer then it can query the DNS heirachy,the DNS does not establish the web connection but provide the information that the browser can use to connect to a service 
### DNS records
It uses different types of records for different purposes
### A record
Maps a domain name to an IPV4 address e.g example.com------192.0.2.10,
### AAAA record
Maps a domain name to an IPV6 Address e.g example.com-----IPV6 address
### CNAME record
creates an alias from one domain name to the other e.g www.example.com--------example.com
### MX record
An MX also known as mail exchange record identifies mail servers responsible for receiving email for a domain e.g example.com-------Mail server
### DNS and PORTS
Traditional DNS quries use the UDP PORT 53 because UDP has low overhead and does not need a connection first to be established, A DNS query and its responses are exchanged as seperate UDP datagram, and also the DNS uses TCP port 53 whereby the TCP is used for zone transfer and queries when a response is too large for the available UDP exchange,There are also encrypted DNS protocals which include (DOH) DNS over HTTPS that carries DNS messages over HTTPS, Using TCP PORT 443 OR HTTP/3, transport and DOT that stands for DNS over TLS which uses TCP PORT 853 these protocals encrypt DNS traffic between client and its selected resolver but they do not change DNS record types
### WHY DO DNS MATTER IN CYBERSECURITY
It matters because internet connections in systems rely on name resolution, given that the security professionals want to investigate the Domain names that are suspicious ,DNS requests that are not expected, Domains that are compromised and malicious,DNS tunnelling, DNS Configuration problems, Reputation of the domain and infrastructure and the unusual record changes. Lets say if a computer is compromised contacts a suspected or unusual domain then its DNS Queriies can provide the evidence,the DNS logs can show which hosts requested a name when it made the request and which resolver handled the request but also note that the DNS alone does not proof that a connection was established successfully 
### WHAT I LEARNED
DNS is a distributed naming system that translates the domain names into IP addresses and mail server details 



