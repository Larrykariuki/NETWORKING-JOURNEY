## Packet analysis
This is the capturing and examining of network packets in order for someone to understand how the devices are communicating across a network, it helps us to troubleshoot network connectivity, identify suspicious traffic and understand the network protocols
## The tools used for packet analysis
### Wireshark
This is a graphical tool that is used to capture the packets in the network and can help us to identify the source and the destination of IP addresses, the communication protocals, the tcp and udp ports, the dns requests and responces and unusual traffic
### Tcpdump
This is a commandl-ine tool in that is used to capture and inspect the traffic in the network and is very usefull when u are working with a linux terminal like kali linux or ubuntu and other linux machines
### Example: DNS traffic investigation 
Lets say my laptop is making some unexpected DNS requests then i can use a packet analysis tool such as tcpdump or wireshark to investigate which domains names are communicating on the network, which dns are being requested and the time the requests are occuring 
## Importance of packet analysis in security 
It helps us to troubleshoot network connectivity,identify suspicious traffic, and support incident investigation
## Lessons learnt
Packet analysis involves the examining of the network packets in order to understand how the devices are communicating across the network. Wireshark is a tool for packet analysis and it provides a graphical user interface for inspecting packets while tcpdump provide the command-line packet capture and inspection. Packet analysis is very usefull for troubleshooting networks and investigating security instances
## Practical lab 1: Capturing the DNS traffic with tcpdump
The objective is to capture and inspect DNS requests and responses on my kali linux machine machine. The tools to be used are kali linux operating system, tcpdump, and nslookup 
## Commands used
### checking the network interface
the command used to check the network interface are ip -br  address
![network interface](labs/01-network-troubleshooting/screenshots/ip-br-address-1.png)
ip - is the tool for managing network on linux, address means show the ip addresses and -br means breif in that the computer prints one short line per connection
the output is eth0 which is the interface for ethernet cable is down, wlan0 is the wifi and the lo is the loopback interface which is the computer talking to intself, 10.80.205.104/24  is the ipv4 address the first 3 numbers identify the network while the last one identifies the device that is what /24 means the interface to capture is wlan0 because it is the only one that is carrying traffic
### Capture the DNS traffic
the command being sudo tcpdump -i wlan0 -nn -vv port 53
![DNS traffic capture](labs/01-network-troubleshooting/screenshots/dns-traffic-capture.png)
this command records the DNS traffic going through my wifi, sudo means run it as the administrator, tcpdump is the too for packet analysis in cmd, -i wlan0 listens on the wifi interface, -nn this shows the raw IP and the numerical port numbers, -vv this one gives extra details, port 53 shows only the DNS traffic, because 53 is associated with DNS in the output the > is when u can tell queries from replies if the 53 port is on the right of the arrow it is ur request going to the server and if it is vice versa it is the server answering back to you
### Save a packet capture
sudo tcpdump -nn -vv -r /home/kali/dns-capture.pcap this command replays a packet that has been captured by the command sudo tcpdump -i wlan0 -nn port 53 -w dns-capture.pcap and also i noticed that u can filter while reading, for instance tcpdump -nn -r dns-capture.pcap port 53
![save packet capture ](labs/01-network-troubleshooting/screenshots/save-packet.png)
![DNS traffic capture](labs/01-network-troubleshooting/screenshots/read-saved-capture.png)
### Generating a DNS lookup
the command being nslookup example.com asks a DNS server the ip address for example.com then prints the answer and also noted that the A and AAAA queries and replies  i captured are what nslookup triggers
![DNS LOOKUP](labs/01-network-troubleshooting/screenshots/nslookup.png)
## My observations
The wireless interface is wlan0 with IPV4 address 10.80.205.104/24 where the 3 numbers identify the network and the last number represents the device, the DNS resolver was 10.80.205.129 using udp port 53 and i observed a DNS A record querry for the example.com,the resolver returned an IPV4 address including 172.66.147.243 and also saw an AAAA record querry for an IPV6 address then i saved the packets captured to .pcap file and read the file with tcpdump
## Lessons that i learnt 
tcpdump captures live traffic of the network and also can read the save captured file for analysis or troubleshooting or investigations, i have also learnt how to identify the DNS queries, responces, ip source and destination, ports and A AND AAAA records
## Conclusion
Now i have understood how the DNS works in packets and how analysing the packets helps in trouble shooting networks and investigating security incidences
## Practical lab 2: Inspecting the DNS packets with wireshark
### My objective
The objective is tu use wireshark which is the graphical user interface tool for capturing packets and to inspect the DNS queries and responces that were captured with tcpdump in and saved in .pcap file, the tools i will be using are kali linux machine, wireshark 4.6.6 and a saved captured packet(dns.capture.pcap)
### The Procedure
Open the captured packets saved file in wireshark then enter the display filter at the top of the panel, click the DNS A query for the example.com, inspect the DNS querry name and the record type, examine the responces in the answeres section then lastly select an AAAA query to identify the IPV6 record type
## My Observations
The name of the dns querry was example.com, the A querry requested an IPV4 address that is associated with, the response from the DNS contained 2 IPV4 address that is 172.66.147.243 and 104.20.23.154, the AAAA query requested an IPV6 address and the dns filter helps to filter and show only the dns packets for analysis
## Lessons I have learnt
Wireshark is a graphical tool for packet analysis that inspects packets visually, with it i can see and find out DNS querries and responces and see their record types and addresses that are returned by the dns resolver. An A record is associated with IPV4 and AAAA record is associated with IPV6,and also a DNS response can have multiple addresses for one domain
## My Conclusion 
I have understood how the DNS resolution can look like in a packet capture and that tcpdump and wireshark can be used together to troubleshoot networks and investigate security incidents, a packet capture can contain very sensitive information so i will be hiding some information on my screenshots before sharing it publicly
![wireshark capture](labs/01-network-troubleshooting/screenshots/wireshark-dns-capture.png)
![DNs filtering](labs/01-network-troubleshooting/screenshots/dns-filter-traffic.png)
![Inspecting dns query](labs/01-network-troubleshooting/screenshots/dns-query-inspection.png)
![Inspecting dns responce](labs/01-network-troubleshooting/screenshots/DNS-RESPONSE-INSPECTION.png)
