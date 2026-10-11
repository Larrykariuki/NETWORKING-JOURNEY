## The basics of firewall and my investigations
My objective is to understand the purpose of a firewall and investigate the tools and rules of the firewall that are available on my kali linux operating system. The tools to be used in this experiment are the kali linux terminal, UFW, nftables, iptables and ip6tables
## Commands Tested
### check ufw status
### 1 sudo ufw status
ufw stands for the uncomplicated firewall management tool or a simplified firewall management tool and my observation was that the terminal returned ufw: command not found meaning that the ufw was not available 
### inspect nftables rules
### 2 sudo nft list ruleset
nft stands for netfilter tables and is the is the inbuilt system in linux kernel that organizes rules, my observation with this command is that was no rules displayed in the nftables ruleset
### 3 Inspect IPV4 firewall rules
### sudo iptables -L -n -V
which stands for sudo run as admin, iptables is the linux firewall tool, -L lists the rules, -n shows IPS and ports as numbers instead of looking up names then -v, verbose which adds packet and byte counters plus the network interfaces
### 4 Inspect IPV6 Firewall rules
### sudo ip6tables -L -n -v
this is for IPV6 networks and the observation was the same with iptables showing empty chains with a default of ACCEPT policy
## Lessons Learnt 
A firewall uses security tools that are configured to filter network traffic, ufw, nftables, and iptables are tools that are used to manage the linux firewall configuration, the IPV4 and IPV6 firewall rules need to be examined in seperate ways, An accept default policy allows packets unless another rule or a security mechanism blocks the traffic , an empty ruleset does not mean that every firewall is inactive
## My conclusion
I investigated the firewall configuration visible on my kali linux system without changing any rules, the displayed IPV4 and IPV6 chains had the ACCEPT default policies and no filtering rules, this practical exercise has improved my understanding of the linux firewall and the defensive network security and I did not change the default settings of the firewall during the learning as a safety procedure


