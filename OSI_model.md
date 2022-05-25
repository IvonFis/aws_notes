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
