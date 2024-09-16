# Mini-Project-01---Network-Setup-and-Troubleshooting

Choose software and hardware
  Decide what the objective is. In this case, it would be to create a network between multiple LANs. Thus, we would require switches, routers, end devices, WAP, ethernet cables, servers, etc. 

IP assignments
  It would be most efficient to assign IPs beforehand to minimize confusion and human error. For this project, network ranges 192.168.0.0/26 and 172.16.0.0/24 have been assigned. 
Device  | IP  | Default Gatway 
------------- | ------------- | --------------
Router 0 (Gig0/0)  | 192.168.0.1  | 
PC0  | 192.168.0.2  |  192.168.0.1 
PC1  | 192.168.0.3  |  192.168.0.1 
PC2  | 192.168.0.4  |  192.168.0.1 
Laptop  | 192.168.0.5  |  192.168.0.1 
Router 0 (Gig0/1)  | 172.16.0.1  |  
Server 0  | 172.16.0.2  |  172.16.0.1 
Server 1  | 172.16.0.3  |  172.16.0.1 

Add end devices (PCs/laptops/printers/tablets/etc)
Once an end device has been added, as seen in the image, you would then assign the IP address. The subnet mask will automatically be assigned in packet tracer after assigning an IP. 
![Alt text](IP_Assignment_PC.png)

Add switch

As seen in the image below, you then connect the end devices to the switch using the ethernet cables. It will take a little bit of time for the switch to boot and connect to the end devices. The green triangles in packet tracer indicated successful communication between the switch and the end device. 
![Alt text](PC_to_Switch_Ethernet.png)

Add mobile devices

Add WAP

Connect WAP to a switch

Set IP address on end devices (mobile devices included)

Add a router to talk to different networks

Connect the switches to the router with ethernet cables

Configure IPs on router

Set Port Status to ON on router

Set default gateway on all end devices/hosts
