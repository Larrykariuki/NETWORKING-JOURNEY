## TCP and UDP 
These are the network layer protocals used to move data between applications 
### TCP
Stands for transmission control protocal is desinged for reliabity and ordered delivery of data,
Makes sure that data arrives perfectly toward its destination by keeping track of what was received and requests missing data, it helps provide: Reliability, Connection Management, Correct ordering and retransmission of lost data
### UDP
Stands for user user datagram protocal,
Faster but less reliable protocal used in videos and prioritizes speed  and low delay over guaranteed delivery and is used in videos
### Example
TCP is like a messenger that makes sure and double checks if everything is correct before delivery,when i connect to a website using HTTPS the application uses TCP as its transport protocal while UDP is like a messenger that doesnt care as long as the message arrives as fast as it can used by DNS for quaries, if a response does not arrive the DNS application retries or decides how to handle timeouts
### What I Learned 
TCP is used when priority is given to the reliability of the data while UDP is used when speed and low delay of the data are priorities,when lets say a cybersecurity professional wants to investigate traffic or scan a network he/she may need to determine which transport protocal is being used,which ports are involved,services or applications running or communicating,is a connection established or is there an unusual traffic at the momment 
