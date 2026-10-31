## Packet analysis
This is the capturing and examining of network packets in order for someone to understand how the devices are communicating across a network, it helps us to troubleshoot network connectivity, identify suspicious traffic and understand the network protocols
## The tools used for packet analysis
### Wireshark
This is a graphical tool that is used to capture the packets in the network and can help us to identify the source and the destination of IP addresses, the communication protocals, the tcp and udp ports, the dns requests and responces and unusual traffic
### Tcpdump
This is a command line tool in that is used to capture and inspect the traffic in the network and is very useful when u are working with a linux terminal like kali linux or ubuntu and other linux machines
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
## Practical lab 3: Observing the DNS traffic with tcpdump
### My Objective
My objective is to observe the DNS requests and responces on my kali linux machine and to understand the dns queries that are reapeting 
### The command used
The command used being sudo tcpdump -i wlan0 -nn -c 10 'port 53'which means the command is using tcpdump to capture and display the live network traffic this command captures the first 10 DNS packets that are moving across the wlan0 interface showing a raw and numerical format what each of the command does.
sudo this is the super user or admin privilleges meaning it is running the command at the highest level as it is required to interact directly with the network driver, tcpdump is the packet analysis tool for cmd, -i wlan0 this specifies the network interface to listen on wlan0, -i representing the interface, -nn disables the names and the service resolution, -c 10 sets the packet count limit ,instead of running continously and terminating with ctrl c u can set the packets limit to 10 to  cancel out the process of packet capture ,and the 'port 53' tells the tcpdump to only capture traffic where the source and destination is on port 53 which is the standard port that is used for the dns querries and responces,the nslookup example.co is what we are going to use as the dns server the command helps in network troubleshooting.
![10 packets capture](labs/01-network-troubleshooting/screenshots/capturing-10-packets.png)
## My Observations
The observation from my terminal is that the machines ip address was 10.80.205.104, the dns resolver was 10.80.205.129, the dns traffic used port 53, An A query requested an IPV4 address for example.com, the response contained 104.20.23.154 and 172.66.147.243, repeated A queries appeared before a response, and the capture completed with 4 captured packets instead of the 10 maximum
## My lessons learnt 
The tcpdump can capture DNS traffic on a network interface that has been selected wether is etho for ethernet or wlan for wifi, dns queries that are repeated is an indication that the retries are caused by delays or responces missing but does not automatically indicate dangerous activity. An analyst should look at the packet timing,responses, destination names and the network sorrounding before he or she decides if the traffic is suspicious 
## My Conclusion
This exercise has helped me observe the DNS requests and the responces and practise to interprete packet captures , i have also learnt that the packet counts depends on the traffic that is observed and whether the capture is stopped or halted before the configured limit in the command
## Practical lab 4: Live DNS monitoring 
### My objective
The objective of this lab  is to monitor live DNS traffic on my kali linux machine and to see the queries for the different domain names the examples to be used are example.com and google.com
### Commands used
The command to be used are sudo tcpdump -i wlan0 -nn -l 'udp port 53' which listens for incoming and outgoing traffic of the dns and prints back the packets as they are arriving and may show less detail than verbose capture moreover as the tcpdump is listening we open another terminal to generate the DNS queries and the command to be used are nslookup example.com and nslookup google.com
![DNS MONITORING](labs/01-network-troubleshooting/screenshots/DNS-QUERY-NAMES.png)
![DNS MONITORING](labs/01-network-troubleshooting/screenshots/DNS-MONITORING.png)
### My observation 
The Capture ran on the wlan0 network interface, the filter selected the udp traffic using port 53, the DNS activity for example.com and google.com  were captured in my terminal
### Lessons Learnt
Tcpdump monitors DNS traffic as it is occuring by generating DNS requests, one can observe and see how the domain names  appear in packet captures. An unusual domain name and a repeated DNS request may be suspicious but neither all of them actually proved that a device has been compromised
### My Conclusion 
This lab has helped me to practise live DNS monitoring and to understand how defenders can investigate domain lookups, suspicious patterns in the captured packets  are clues that more evidence is required before one assumes malicious intent
## Practical lab 5: Inspecting Active Network connection
### My Objective
The objective is to identify active TCP connections, the application associated and the registered remote IP addresses of the organizations
### The commands used
The built in tool command in linux is ss. Open the terminal and run ss-tun the command will then display the TCP and UDP sockets to show the remote endpoints in kali the command used is ss-tnp which displays the tcp sockets numerically and show process information. The output of the command identified 3 tcp connections linked to firefox and all 3 remote endpoints used port 443 which is associated with HTTPS
### Whois command
This command is used to identify the IP address discovered during the display of servers in the network. The commands are (a) whois 140.82.112.26, (b) who is 34.107.243.93 and (c) who is 151.101.1.91. The findings I saw was that (a) is registered to github inc, (b) is registered to google LLC and also the whois noted that ggogle cloud customers use addresses in this allocation and the last one i checked was 151.101,1,91 that is registered to fastly
### Lessons Learnt
ss-tnp shows established TCP connections,remote and local ip addresses, port numbers and their processes. Whois identifies the organization that is associated with an IP address range, the port 443 indicates HTTPS traffic and the organizations such as google and fastly provides the infrastructure that is ued by other services
### My security takeaway 
One should relate the network connections with the dns info, app activity and many other evidences before he or she decides whether a connection is malicious
![ACTIVE-NETWORK-INSPECTION](labs/01-network-troubleshooting/screenshots/ACTIVE-NETWORK-INSPECTION.png)
![WHOIS](labs/01-network-troubleshooting/screenshots/WHOIS.png)
![WHOIS2](labs/01-network-troubleshooting/screenshots/WHOIS2.png)
## Practical lab 6: DNS to Connection investigation
### My objective
I am going to observer the DNS resolution and compare it with the active TCP connections. The tools i will be using are nslookup which will be used to query DNS records, tcpdump that will be used to capture DNS packets, ss that will be used to inspect TCP connections and whois will be used to identify the organizations associated with IP address ranges
### The Commands used
The commands to be used are nslookup github.com, sudo tcpdump -i wlan0 -nn -l 'udp port 53', ss -tnp and whois 140.82.112.26
### My observations
The DNS resolver was 10.80.205.129 that was listening on the DNS port 53 and the DNS A querry for github.com returned 20.87.245.0, the AAAA query received a response with no IPV6 address records in its answer section, ss-tnp showed established firefox TCP connections to remote endpoints using 443 and whois associated the observed IP ranges with organizations including Github, Google and Fastly 
### Lessons learnt 
The dns translates domain names into IP adrresses, tcpdump captures the DNS queries and the responses and the ss displays active network connections. I have also realized that a result of the DNS and a connection that is active to an IP address are seperate observations and matching them requires careful correlation, A DNS lookup by itself does not proof that the hostname created a particular connection
### Security takeaway
Before assuming that a network activity is suspicious one should collect evidence, compare timestamps and endpoints and distinguish confirmed observations from assumptions before assuming
![DNS to connection investigation](labs/01-network-troubleshooting/screenshots/DNS-CONNECTION-INVESTIGATION.png)
## Practical Lab 7: Inspecting the HTTPS and the TLS Certificates
The objective here is to look a servers TLS certificate and understand how it helps to secure HTTPS connections, the TLS is the security protocol for HTTPS connections
### The Command
The command to be used is openssl s_client -connect github.com:443 -servername github.com </dev/null. This command means as follows openssl s-client connects to the TLS server and displays the handshake and the certificate information
![Inspecting https and tls certs](labs/01-network-troubleshooting/screenshots/TLS-AND-HTTPS-CERTIFICATE.png)
### Extracting the certificate details 
The command used is openssl s-client-connect github.com:443 -servername github.com <dev/null 2>/dev/null | openssl x509 -noout-subject-issuer-dates where the openssl x509 extracts the fields from the certificate
![CERTIFICATE EXTRACTION](labs/01-network-troubleshooting/screenshots/CERTIFICATE-EXTRACTION.png)
### Observation from the results
The certificate subject which is the certificate named subject is CN=github.com, The certificate issuer is sectigo public server Authentication CA DV E36, the certificate validity began in september 1,2026 and ends in november 29,2026, TLS version is TLS 1.3 and the certificate verrified a return code:0 (ok)
### Lessons Learnt 
TLS helps to protect the data exchanges between a client and a server in HTTPS connections, the TLS Certificate helps to verify the identity of the server and it contains its public key, the certificate authorities sign the certificates and the clients validate the certificate chain against their configured trust stores, the openssl command can inspect a TLS connection and extract the certificate information, including its subject, the issuer and the dates valid
### Security Takeaway
Verrification of a certificate is an important part of a secured communication 
## Practical Lab 8: Inspecting HTTPS traffic in wireshark
### The objective
My objective of this lab is to capture HTTPS traffic and inspect the TLS handshake information using wireshark tool 
### The Command to capture HTTPS traffic 
The command being sudo tcpdump -i wlan0 -nn -s 0 -w/tmp/https-lab.pcap 'tcp port 443' captures and saves the file to pcap; I opened github  in firefox while the capture was running and after stopping it the tcpdump reported 3898 captured packets 
![CAPTURING HTTPS TRAFFIC](labs/01-network-troubleshooting/screenshots/CAPTURING-HTTPS-TRAFFIC.png)
### Inspecting the capture of 3898 packets 
The command being wireshark /tmp/https-lab.pcap opens the captured file via wireshark then displays the filter by applying the command tls which filters the TLS packets, including client hello server hello, and the application data
![INSPECTING PACKETS ](labs/01-network-troubleshooting/screenshots/INSPECTING-PACKETS.png)
### 3 Inspecting a client hello packet 
When observing frame 9 i saw the source ip, destination ip, source port, destination port, the TLS handshake and the length of the handshake
## Lessons learnt 
The https uses port 443, the Tls uses handshake to establish security parameters before the application data that is protected is exchanged, A client hello begins the tls handshake, wireshark displays packet metadata and TLS handshake information even when the application data is encrypted, the version feilds in a TLS 1.3 client hello can contain legacy values for compatibility, A missing SNI field does not by itself prove that there is something wrong 
## My Conclusions
The HTTPs traffic was successfully captured and the TLS packets were inspected with tcpdump in wireshark, the exercise has helped me to understand how packet analysis can reveal connections
## Practical lab 9: Coorelating HTTPS connections with reverse DNS 
### Objecives
The purpose is to see active HTTPS connections and compare their remote IP addresses with the reverse DNS results:
### 1 The Command:
The command being ss-tnp inspects the active connections available then i observe 2 established TCP connections that were associated with firefox. ESR:- 10.80.205.104:43750-------34.107.245.93:443 and 10.80.205.104:58420--------140.82.113.26:443, both connections used the remote port 443 that is commonly associated with HTTPS
![ss-tnp ](labs/01-network-troubleshooting/screenshots/SS-TNP.png)
### 2 Investigating the 1st remote IP:
The command being nslookup 140.82.113.26 the DNS results came to lb-140.82.113.26.iad.github.com: the hostname is associated with the github infrastructure 
![nslookup 140.82.113.26 ](labs/01-network-troubleshooting/screenshots/nslookup140.82.113.26.png)
### 3 Investigating the 2nd remote IP 
The command being nslookup 34.107.243.93 the reverse dns result came to 93.243.107.34.bc.google user content.com the hostname is under googles googleusercontent.com domain indicates the google associated infrastructre
![nslookup-34.107.243.93](labs/01-network-troubleshooting/screenshots/nslookup140.82.113.26.png)
### Lessons Learnt
The ss command helps us to identify established TCP connections and their processes, reverse DNS is used in PTR records to associate the ip addresses with hostnames,A browser can maintain simultaneous connections to different remote services, reverse DNS provides the clues about an infrastructure: In network investigations they are stronger when multiple observations are coorelated, including the DNS records, TCP connections, the TLS information and the application context
### My Conclusion
I have used ss and nslookup to investigate the 2 active HTTPS connections from my kali and compared the remote IP addresses with their reverse dns names and i learnt how these observations helps in network investigation
## Practical lab 10: Capturing and Analysing the DNS traffic
### The Objective
The purpose is to capture DNS queries and responses using tcpdump and to  understand how a computer resolves domain names to IP addresses
### 1 DNS capture 
The command being sudo tcpdump -i wlan0 -nn -l 'udp port 53' uses wlan0 interface to monitor UDP traffic on port 53
![dns capture](labs/01-network-troubleshooting/screenshots/DNS-CAPTURE.png)
### 2 Generate DNS query 
The command being nslookup example.com the capture showed my laptop 10.80.205.104 sending DNS queries to the resolver 10.80.205.129 the command returned the following addresses
![DNS QUERY](labs/01-network-troubleshooting/screenshots/DNS-QUERY.png)
### IPV4 addresses
That is 172.66.147.243 and 104.20.23.154
### IPV6 addresses 
That is 2606:4700:10::ac42:9343 and 2606:4700:10::6814:179 a in which the results matched the A and AAAA records that were observed in the tcpdump capture
## Lessons Learnt 
tcpdump monitors DNS traffic on a network interface selected, DNS uses UDP port 53, A record contains IPV4 address, AAAA record contains IPV6 address, DNS query IDS helps one to associate responses with their requests
## Conclusion 
tcpdump and nslookup together enables one to observe DNS traffic and verify the return addresses, observed both A and AAAA queries and I have learnt how DNS help devices to obtain IP addresses for domain name
## Practical lab 11: DNS Caching and TTL
### Objective
The purpose is to understand why DNS answers can be reused and why they can change with time, TTL stands for time to live and in which in DNS it tells a resolver how long a DNS record may be cached before being refreshed 
### Step 1: Query the DNS records 
The command being dig example.com from my observations the TTL was 226 seconds, IPV4 addresses returned 104.20.23.154 and 172.66.147.243, the TTL of 226 seconds is the remaining cache lifetime reported by the resolver
### Step 2: Comparing the TTL values across 2 queries
When I ran dig example.com 2 times using the configured DNS resolver 10.80.205.129, the first query 2 A records with a TTL of 226 seconds. The 2nd query in 4 min and 23 seconds later returned the same 2 IPV4 addresses with a TTL of 244 seconds, the TTL increased instead of decreasing which indcates that the resolver refreshed the records
![DNS RECORDS QUERY](labs/01-network-troubleshooting/screenshots/DNS-TTL-RECORDS.png)
### My Observations 
When I queried the A records for example.com using the configured DNS resolver at 10.80.205.129 using the command dig@10.80.205.129 example.com A +noall +answer the queries returned the 2 IPV4 addresses that is 104.20.23.154 and 172.66.147.243, this command is a more controlled command to identify the TTL values. So the TTL values that I observed were 67,229,157,154 and 142, the TTL decreased from 157 to 154 to 142 seconds between 3 observations, however there was increase between earlier queries which may mean a different cache state or a refreshed DNS answer
![DNS TTL OBSERVATIONS](labs/01-network-troubleshooting/screenshots/DNS-TTL-OBSERVATIONS.png)
## Lessons Learned 
DNS TTL is expressed in seconds and indicated just how long a DNS record may remain cahed before it has to be refreshed, A remaining TTL decreases as time passes but then a later query can return a higher TTL if a fresh answer is obtained by the resolver. I have learned and understood that DNS answers can remain the same even though their TTL values can differ
## Practical lab 12: Investigating HTTPS connections and TCP states 
### My Objective
The purpose of this lab is to inspect live TCP connections on kali, identify connections used for HTTPS and observe the TCP  connection states
### Step 1: Inspecting the TCP connections
The command being ss -tnp: Initially the command showed no TCP  connections but after opening a webpage in firefox it displayed TCP connections that were associated with the firefox-esr process
![TCP CONNECTION INSPECTION](labs/01-network-troubleshooting/screenshots/TCP-CONNECTION-INSPECTION.png)
### Step 2: Identifying HTTPS-related connections 
The output produced ESTAB 0 0 10.80.205.104:39546 34.107.243.93:443 
### from Observations
10.80.205.104 is my laptops IP address, 33586 is the temporary TCP port, 34.107.243.93 is the remote IP address, 443 is the remote TCP port used for HTTPS connections, ESTAB means the TCP  connection is established and the receive and send ques were both 0
### Step 3: Filtering Connections by port destination
The command is ss -tnp '(dport = :443)' the output filtered displayed TCP connections whose port destination was 443(HTTPS) and the results included established connections which could chaange as firefox opens and closes connections
![FILTERING HTTP CONNECTION](labs/01-network-troubleshooting/screenshots/FILTERING-HTTP-CONNECTION.png)
### Observing Live Connection states
The Command being watch -n 1 'ss -tnp' is used for live display which showed an established connection from 10.80.205.104:39546 to 34.107.243.93:443, in an earlier output i saw SYN-SENT and FIN-WAIT-1 states
![LIVE CONNECTION STATES](labs/01-network-troubleshooting/screenshots/LIVE-CONNECTION-STATES.png)
## Lessons learned
The ss command usually displays TCP connection information, ESTAB means that the TCP  connection is established, SYN-SENT means a connection attempt is waiting a response, FIN-WAIT-1 means the local endpoint started the TCP  clossing process, The ports 80 and 443 are for HTTP and HTTPS respectively, the watch command helps to observe how network connections can change over time in real time, if a TCP connection is established it does not mean necessarily that data is flowing continously 
## My conclusions
ss and watch can be used to inspect TCP connections that are created while browsing in firefox, I have identified HTTPS associated connections, observed different TCP states and i have confirmed that one connection remained established across repeated observations
## Practical lab 13: Capturing the HTTPS Traffic and observing the TCP handshake
### My Objective:
I want to capture the TCP traffic that is asociated with HTTPS using tcpdump tool and to identify the TCP 3-way handshake
### Step 1: Capture TCP traffic on port 443
Step 1 is to capture the TCP traffic on port 443, the command being sudo tcpdump -i wlan0 -nn -c20 'tcp port 443', the observation is that the capture showed packets travelling between my kali machine of IP address 10.80.205.104 and remote servers using TCP port 443, the output displayed TCP flags, sequence numbers, acknowledgement numbers,payload lengths
![CAPTURE-TCP-CONNECTION](labs/01-network-troubleshooting/screenshots/CAPTURE-TCP-CONNECTION.png)
### Step 2: Filter for TCP C onnection setup packets
The command is sudo tcpdump -i Wlan0 -nn -c 30 tcp port 443 and (tcp[tcpflags] & (tcp-syn|tcp-ack) !=0) from my observation is that the first attempt produced a filter syntax error. After I corrected my command, the tcpdump tool successfully captured 30 packets. The output included packets that are associated with the connection between 10.80.205.104 and 151.101.193.91
![CAPTURE-CONNECTION-SETUP](labs/01-network-troubleshooting/screenshots/CAPTURE-CONNECTION-SETUP.png)
### Step 3: Identify the TCP 3-WAY handshake
The capture showed these following sequence for the connection using local port 39264 and remote port 443, (1) SYN - Means that my laptop requested a TCP connection, SYN-ACK - Means that the remote endpoint responded with SYN and ACK flags and ACK - Which means that my laptop acknowledged the responce and completed the 3 way handshake 
### Step 4: Interpreting the other packet details 
Flag - This indicates PSH and ACK flags are set, Length0 - Means the packet contains 0 TCP payload bytes, seq and ack are TCP sequence and acknowledgement numbers, 443 is the TCP port used for  HTTPs, the final capture reported 30 packets captured and o packets dropped by the kernel
## Lessons Learnt 
Tcpdump Captures  real TCP traffic and display the information that is needed to investigate network connections, A TCP connection known as a 3-WAY handshake begins with SYN, SYN-ACK and ACK packets , once a TCP is established the endpoints can then proceed with TLS negotiation and encrypted HTTPS connection, I have also learnt that a packet filter must use correct syntax and that TCP flags help to distinguish connection setup packets from other traffic 
## My Conclusion 
The TCP  traffic was successfully captured on port 443 and I identified the packets that were corresponding to the 3-way handshake, this lab exercise has helped me to connect the TCP states that I have observed with ss to the actual packets visible in tcpdump. The capture showed TCP connection activity, but did not reveal the contents of encrypted HTTPS application data
## Practical lab 14: Observing both DNS and HTTPS together 
### My Objective 
The purpose of the lab is to observe the DNS queries and responses and to inspect TCP connections that are associated with HTTPS
## Step 1 : Capturing DNS traffic:
The command being sudo tcpdump -i wlan0 -nn -c 10 ;port 53', from my capture I saw that DNS queries from my kali linux machine of IP address 10.155.169.104 to the resolver at 10.155.169.127:53. The queries included A and AAAA records for mozilla related domain names, and the responses included IPV4 addresses, IPV6 addresses and CNAME records
![DNS TRAFFIC CAPTURE](labs/01-network-troubleshooting/screenshots/DNS-TRAFFIC-CAPTURE.png)
## Step 2: Inspecting HTTPS-related connections
The command being ss -tnp dport:443, the output showed an estaablished connection Estab 0 . 0 10.155.169.104:45470, 34.107.243.93:443, the connection was associated with firefox ESR. The remote port is 443 used for HTTPS 
![VERRIFY-HTTPS-CONNECTION](labs/01-network-troubleshooting/screenshots/VERIFY-HTTPS-CONNECTION.png)
## Step 3: Capturing the DNS and TCP Observations
The DNS captured showed the answers for many mozilla-related domain names, while the tcp connectionshowed was to 34.107.243.93.443. The remote IP address did not match the IPV4 address returned for mozilla .map.fasltly.net in the captured DNS response because the capture contained queries for multiple names and DNS answers and TCP connections were observed seperately, I failed to establish which DNS response led to this particular connection
## Lessons Learnt
The DNS helps applications to obtain addressing information while TCP establishes connections to remote endpoints. HTTPS uses TCP port 443, followed by TLS negotiation when using TCP based HTTPS. Observing DNS and TCP traffic seperately helps one to investigate network activity, but correlating a particular DNS answer with a connection requires matching the relevant domain, IP address, timing and connection evidence 
## Conclusion
I have captured DNS traffic and have inspected and established HTTPS associated TCP connection on kali linux. The lab exercise has helped me to understand how name resolution and net connections relate, while recognizing the limits of evidence gathered in seperate screenshots
## Practical lab 15: Investigating HTTP traffic
### My Objective
The purpose for this lab is to capture the HTTP traffic using tcpdump packet analysis tool and inspect a readable HTTP request and a server response 
### Step 1: Capture the traffic on port 80 (HTTP)
The command is sudo tcpdump -i wlan0 -nn -c 10 'port 80' the capture reveled  traffic between my kali laptop at 10.155.169.104 and the remote server at 172.66.147.243 using TCP port 80 (HTTP)
![HTTP-TRAFFIC-INVESTIGATION](labs/01-network-troubleshooting/screenshots/HTTP-TRAFFIC-INVESTIGATION.png)
### Step 2: Observing the TCP handshake 
The output showed SYN, SYN-ACK, and ACK packets for the connection using local port 39634 and remote port 80. These packets represents the normal TCP 3-WAY handshake
### Step 3: Inspecting the HTTP request 
The capture includes HTTP:GET/HTTP/1.1, this was a request for the root resource at /. The request was visible in the packet capture because ordinary HTTP does not encrypt its app data
### Step 4: Inspecting the HTTTP response 
Where the capture included HTTP:HTTP/1.1 200 OK, the response shows that server successfully handled the HTTP request. The Captured response packet contained 756 bytes TCP payload , which may be part of the HTTP response
## Lessons Learnt 
HTTP uses TCP port 80 and its application  requests and responses can be readable in a packet capture. The TCP  handshake establishes the connection before the HTTP data is exchanged. A get request  asks for a resource, while an HTTP  200 ok status shows a successful response. HTTP  uses TCP port 443 and protects applicaton data using TLS which makes its application requests and responses unreadable in a packet capture, though some connection metadata may still remain visible
## Conclusion
I have successfully captured a HTTP traffic and I have identified the TCP handshake, a get request, and an HTTP 200 OK response. This lab exercise has helped me to understand the difference between a readable HTTP trafic and a TLS-protected HTTPS traffic 
## Practical lab 16: Inspecting the HTTP headers
### Objective
The purpose of this lab is to capture the HTTP traffic and identify requests and response headers using tcpdump tool
### Step 1: Capturing the HTTP traffic
The command being  sudo tcpdump -i wlan0 -nn -A -s 0 -c 20 'tcp port 80'
![INSPECTING-HTTP-HEADRES](labs/01-network-troubleshooting/screenshots/HTTP-HEADERS.png)
### Observations
The capture showed HTTP traffic between the kali machine at 10.155.169.104 and the remote server at 104.20.23.254 on TCP port 80
### Step 2: Inspect the http request 
The request included:GET/HTTP/1.1, Host:example.com, user.Agent:Mozilla/5.0.......firefox/140.0, Accept Language:en-us, en: q=0.5, Accept-Encoding: gzip, deflate, connection:keep-alive. The GET method requested the root resource, The Host header identified example.com, while the user agent and other headers described browser capabilities and preferences
### Step 3: Inspecting the Server response
The capture showed HTTP/1.1 304 not modified which the status means that the server had considered the cached resource still valid under the requsts validation conditions and so the browser could reuse its cached copy rather than downloading the resource again
## Lessons Learnt
HTTP headers carry information about requests,browser capabilities, content preference and connection behaviour because ordinary ordinary HTTP does not provide TLS encryption. The headers can be readable in a packet capture, I have also learnt that HTTP status code 304 is related to cache validation and does not really indicate a server error
## Conclusion
I captured successfully the HTTP traffic and identified the request headers and server response.This lab has helped me understand how HTTPS is important for protecting that information in transit
## Practical lab 17: Comparing HTTP and HTTPS packets
### My Objective
The purpose is to compare HTTPS and HTTPS using tcpdump packet analysis tool and see the effects of the TLS encryption
### Step 1: Capturing the HTTP traffic
The Command being sudo tcpdump -i wlan0 -nn -A -s 0 -c 20 'tcp port 443'
![COMPARING-HTTP-HTTPS](labs/01-network-troubleshooting/screenshots/HTTP-TRAFFIC-INVESTIGATION.png)
### My Observations
The Capture recorded 20 packets that involves my machine at 10.209.157.104 and a remote endpoint at 34.149.226.178:443
### Step 2: Inspecting the packet output 
The output displayed printable characters including TCP flags, IP addresses, temporary ports, sequence and acknowledgement numbers and packet payloads
### The Hostname
The content.signature.2.cdn.mozilla.net was shown in the output. This shows that some hostname-related info can be visible in a captured traffic
### Step 3 : Comparing with the HTTP capture 
In lab 16, I could read the request line GET/HTTP/1.1, the host header, and the servers HTTP response but in this HTTPS capture, I did not see the HTTP request headers displayed as readable plaintext. HTTPS protects HTTP application data using TLS after encryption begins
## Lessons Learnt 
I have Learnt that packet captures reveal IP addresses ports, TCP flags and connection metadata even when an application uses HTTPS. Unlike ordinary HTTP, HTTPS encrypts application data using TLS, making HTTP requests and headers unreadable as plaintext in a normal capture of encrypted traffic. Some TLS handshake information or hostname-related metadata can still be visible depending on the protocol and the configuration 
## My Conclusion 
I have successfully captured HTTPS traffic and compared its visibility with the HTTP traffic from lab 16. The Lab exercise has helped me to understand the difference between visible network metadata and encrypted application content.
## Practical lab 18: Investigating TCP connection states
## My Objective 
The objective of this lab is to inspect TCP sockets on kali linux and identify established connections and locally listening services 
### Step 1 : Inspecting TCP sockets
The command being ss -tan, the output identified 2 TCP socket states: that is LISTEN on 127.0.0.1:11434, ESTAB from 10.209.157.104:58380 to 34.107.243.93:443
![INSPECTING-TCP-SOCKETS](labs/01-network-troubleshooting/screenshots/INSPECTING-TCP-SOCKETS.png)
### Step 2 : Investigating the Listening port
I identified that the listening port 11434 was Ollama which is a local AI model service, the address 127.0.0.1 is the loopback address. Binding to this address means that the listener accepts connections through the local machines loopback interface instead of listening directly on all network interfaces
### Step 3 : Interpreting the connections established
The connection from 10.209.157.104:58380 to 34.107.243.93:443 was in the ESTAB state. Port 443 is used for HTTP connections, The Recv.Q and send.Q values were all 0 which means no data was queued in the socket during the inspection
## Lessons learnt
ss -tan displays TCP socket states and endpoint. LISTEN indicates a listening socket, while ESTAB indicates an established TCP connection, I have also learnt that identifying the process behind a listening port helps us to distinguish between known services from unknown  ones. A local service that is listening on 127.0.0.1 is not directly listening on all network interfaces
## My Conclusion
I have used ss -tan  to inspect TCP connections and identified ollama as the service that is listening on localhost port 11434. This exercise has helped me to practice and to understand basic network - service identification and TCP connection state analysis 
## Lab 19: Inspecting listening Network Services
### Objective
My objective is to inspect the listening TCP and UDP sockets on kali linux and to identify the processes using them
### Step 1: Listing listening Sockets
The command being sudo ss -lntup lists the listening sockets  and the output showed Ollama listening on TCP port 11434 and several UDP Sockets owned by a python process with PID 7193
![INSPECTING-LISTENING-NETWORK-SERVICES](labs/01-network-troubleshooting/screenshots/INSPECTING-LISTENING-NETWORK-SERVICES.png)
### Step 2: Identifying the python process
The command being ps-fp 7193, the output identified the process as python 3/usr/bin/wsdd....no-host--discovery ---listen/run/user/1000/gvfsd/wsdd. Which confirmed that the python process was running wsdd that stands for web services Dynamic discovery daemon which is used to find devices on the local area network
### Step 3: Understanding the Network activity
The UDP sockets included port 3702 and multicast address such as 239.255.255.25 and (ff02::c) which are consistent with WS-Discovery traffic that helps devices to discover compatible services on a local network. Ollama was listening on : 127.0.0.1:10434 which means that its TCP service was bound to the loopback interface and was listening for connections from the local computer 
## Lessons Learnt
I have learnt how to inspect listening TCP and UDP sockets using ss, How to identify which process owns a network socket, UDP sockets can appear as UCONN because UDP is connectionless, WS-Discovery uses UDP port 3702 for local network discovery, 127.0.0.1 refers to the local computer, an open or listening port does not automatically mean there is malicious activity going on
## My Conclusion 
I have successfully inspected the listening network services on kali linux and identified the processes behind the sockets. I have also found out that the UDP discovery traffic belonged to wsdd, while ollama was listening on the local loopback interface, the exercise has taught me why cybersecurity analysts should first identify and understand network services before deciding whether there is suspicious activity
## Practical lab 20 : Investigating a TCP connection to a remote HTTPS Service
### Objective
To investigate an active TCP connection, identify the application that is responsible for it, and to capture the packets exchanges with a remote HTTPS service
### Step 1 : Investigating active TCP connections
The command being ss -tn the output showed 3 established TCP connections from my kali machine to remote IP addresses using destination port 443, the ESTAB state indicates that the TCP connection has been established
![INVESTIGATING-TCP-CONNECTION-TO-REMOTE-SERVICE](labs/01-network-troubleshooting/screenshots/INVESTIGATING-TCP-CONNECTION-TO-REMOTE-SERVICE.png)
### Step 2 : Identify the applications 
The command being sudo ss -tnp the output showed firefox ESR as the application that is responsible for the connections. The process ID was 4334. Firefox had multiple established connections to remote HTTPS services
### Step 3 : Capturing the HTTPS traffic
The command being sudo tcpdump -i wlan0 -nn 'tcp port 443' -c 15 the capture showed packets exchanged between my kali machine of 10.209.157.104 and a remote server of 151.101.129.91 on TCP port 443. The first 3 packets showed the TCP 3-WAY handshake that is SYN - whereby my computer requested a TCP connection, SYN-ACK - The remote server accepted and acknowledged the request, ACK - whereby my computer acknowledged the servers response. After the handshake the packets containing application data were exchanged in both directions, the capture showed 15 packets captured and 0 dropped by the kernel
## Lessons learnt
I have learnt how to inspect active TCP connections using ss -tn, how to identify the applications responsible for a connection using ss - tnp, how to capture HTTPS-related TCP traffic using tcpdump, How to recognize the tcp 3-WAY handshake,How to interprete SYN, SYN-ACK, ACK, PSH and ACK flags, a packet capture can reveal connection metadata and traffic patterns without necessarily reavealing encrypted app content
## Conclusion
I have successfully investigated active TCP connections on my kali linux machine, identified firefox ESR as the application responsible for them captured the packets exchanged with a remote HTTPS service, I have observed the TCP 3-WAY handshake and the subsequent data exchange. The lab exercise has helped me understand how applications communicate with remote services and how network analysts can investigate those connections using linux networking tools





