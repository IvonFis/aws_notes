# OSI MODEL - Open System Integration Model


- How are data is transfered from one computer to another in the computer network?
---

Let's review the basic form of connection between two computers. The image below shows two computers connected through a LAN cable 
and connectors sharing data with help of a NIC (Network interface card). 

![image](https://user-images.githubusercontent.com/33365899/170174042-e69ca880-a2d8-430b-b571-66265f4a5e5c.png)

However, for different opperative systems, a new model has to be stablished (ISO 1984), that consists in seven layers:

![image](https://user-images.githubusercontent.com/33365899/170175055-1b2c630b-c645-4f35-a151-51c8d3647319.png)

## Application Layer

Used by network applications (app that uses internet), they depend of application layers to function. . For example, a web browser uses application layer 
protocols such as HTTP, HTTPS. [see more](https://www.geeksforgeeks.org/protocols-application-layer/)

1. TELNET: **TEL**etype **NET**work, port number **23** It helps in terminal emulation 
2. FTP: File Transfer Protocol, port **20** for data and **21** for control. It promotes sharing of files via remote computers with reliable and efficient data transfer.
3. TFPT: The Trivial File Transfer Protocol (TFTP), port **69*, simpliflied version of FTP, the protocol of choice if you know exactly what you want and where to find it
4. NFT: Network File System, PORT **2049**,  It allows remote hosts to mount file systems over a network and interact with those file systems as though they are mounted locally
5. SMTP: Simple Mail Transfer Protocol, port **25**,  It is a part of the TCP/IP protocol. Using a process called “store and forward,” SMTP moves your email on and across networks.
6. LPD: Line Printer Daemon, port **515**, printer sharing
7. X window: port **6000**, increases by 1 for each server, for the writing of graphical user interface–based client/server applications
8. SNMP: Simple Network Management Protocol, port **161** TCP and **162** UDP, t is a way that servers can share information about their current state, and also a channel through which an administrate can modify pre-defined values. 
9. DNS: Domain Name System, port **53**, DNS service must translate the name into the corresponding IP address
10. DHCP: Dynamic Host Configuration Protocol (DHCP), port **67** and **68**, It gives IP addresses to hosts

## Presentation Layer

It receives data from application layer. Converts strings to binary, reducing the number of bit to represent the original data. Ex. ASCII - > EBCDIC. Consists of Translation, Data Compression (lossy or lossless data), before transmission data is encrypted (SSL, Secute Sockets Layer protocol)

## Session Layer

Session layer protocols helps in setting up and managing connections, enabling sending and receiving data followed by termination of sessions or connections. Ex. APIs, NETBIOS. Before a connection is stablished authentication and authorization process must be performed. It also keeps tracks of which data package (files within the page) belongs to which file, called session management. 

## Transport Layer

Controls the reliability of communications through 

- Segmentation: Data is divided in segments, having each a Port Number (direct the segment to the correct application) and Sequence Number (assamble segments in the correct order). 
- Flow Control: Controls the amout of data being transmited and,
- Error control: data control (automatic repeated request adding a group of bits called checksum )
- Connection and connectionless transmission

The protocols are:

- TCP: Transmission Control Protocol
- UDP: User Datagra Protocol

### Connection and conectionless transmission

|Protocol	|Service	|Advantages	|Ex
| -------|--------|----------|-------|
|TCP: Transmission Control Protocol|	Conection-Orientes Transmission	|Lost data can be re-transmited	|Video games, Songs
|UDP: User Datagra Protocol|	Connectioless Transmission|	Faster because it doesn't provide any feedback|	Email, WWW

## Network Layer

Transport layer passes data segments to the Network Layer. The network layer works for the transmission of the received data segments from one computer to another located in different networks. Data units in the network layer are called **packets*, it is in the layer where routers recide. 

The network layer functions are:

- Logical addressing - IPV4, IPV6 Every computer in the network has an unique IP adress, Network layer assigns an IP to the receiver and the sender to each segment to form an Packet (IP adresses are assigned to ensure that each data package can reach the correct destination).
- Routing - A method of moving data packed from source to destination based on the logical adress format (IPv4, IPv6).
- Path determination - Choose the best possible path to data delivery from source to destination. The protocols are OSPF - Open Shortest Path First, BGP - Border Gateway Protocol and IS-IS - Intermidiate system to intermidiate system. 

![image](https://user-images.githubusercontent.com/33365899/170197049-7ba88b60-46dc-48b0-9d59-ed740210a388.png)


## Data Link Layer

Data Link receives data packet from the network layer. This data packages contain IP adresses of the senders and receiving. 

- Local adressing : done at network layer where senders and receivers IP adresses are assigned to each segment to form a data packet, 
- Physical adressing : done at data link layer, where MAC adresses (12 digit alphanumeric number embedded in the NIC) of sender and receiver are assigned to each data package to form a Frame (data unit in a data link layer is called frame). 

The data link layer is embeddes as software in the network interface card, NIC. Its basic funtions are

1. Allows upper layes to access media (software) using techniques such as Framing, 
2. Controls how data is placed and received from media using techniques such as MAC, and error detection.

## Physical Layer

![image](https://user-images.githubusercontent.com/33365899/170199292-03b0f4ff-0b6f-4628-ae61-633f5b8e5d30.png)

The physical layer converts the binary sequence from the data link layer into signals ands trnsmited over local media. The signals are converted into bits, and pass to the data link layer as a Frame, and decapsulated throguh the highest layers to the application layer. 




