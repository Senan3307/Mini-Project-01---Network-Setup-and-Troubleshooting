# Mini-Project-01---Network-Setup-and-Troubleshooting

# Step-by-Step Configuration Guide
**Objective**

**Use Cases**

One use case would be at LMU. LMU has multiple local area networks spanning across multiple buildings and they ultimately connect to the main servers in University hall. All of this would not be connected if it wasn't for established connections of networks. While the scale of LMU's network is much larger than what we can replicate in classes, the overall foundation of the architecture is similar to what we can replicate in packet tracer and class. 

Another use case could be tech giants such as Google. Google has offices and data centers all around the world. This is connected through networks on a larger scale. 

**Choose software and hardware**
  
  Decide what the objective is. In this case, it would be to create a network between multiple LANs and establish communciation between various devices. Thus, we would require switches, routers, end devices, WAP, ethernet cables, servers, etc. 

**IP assignments**
  
  It would be most efficient to assign IPs beforehand to minimize confusion and human error. For this project, network ranges 192.168.0.0/26 and 172.16.0.0/24 have been assigned. 
Device  | IP  | Default Gatway | Subnet Mask
------------- | ------------- | -------------- | ------------
Router 0 (Gig0/0)  | 192.168.0.1  | 
PC0  | 192.168.0.2  |  192.168.0.1 |  255.255.255.192
PC1  | 192.168.0.3  |  192.168.0.1 |  255.255.255.192 
PC2  | 192.168.0.4  |  192.168.0.1 |  255.255.255.192 
Tablet PC1  | 192.168.0.5  |  192.168.0.1 |  255.255.255.192
Smartphone  | 192.168.0.6  |  192.168.0.1 |  255.255.255.192
Router 0 (Gig0/1)  | 172.16.0.1  |  
Server 0  | 172.16.0.2  |  172.16.0.1 |  255.255.255.0
Server 1  | 172.16.0.3  |  172.16.0.1 |  255.255.255.0 

**Add end devices (PCs/laptops/printers/tablets/etc)**
  
  Once an end device (Laptop, PC, etc) has been added, as seen in the image, you would then manually assign the IP address. On a Mac, you would go to system settings -> network -> details -> TCP/IP -> set configure IPv4 to "Manual" -> enter IP address and subnet mask as listed in the table above. 
![Alt text](IP_Assignment_PC.png)
  You would also need to assign the default gateway to establish communication between the end device and the eventual addition of a router. Otherwise, the end device would not be able to recognize which channel to communicate through once a network has been established among multiuple LANs. To do this, change "router" to the assigned value as listed int he above table. 
![Alt text](Default_Gateway_Assignment_PC.png)

**Add switch**

  You then connect the end devices to the switch using the ethernet cables. It will take a little bit of time for the switch to boot and connect to the end devices. The switch must be connected to a power outlet in order for it to turn on. The switches we have been using does not have a on-off button so it should automatically turn on once plugged in. 
  The green triangles in packet tracer indicated successful communication between the switch and the end device. 
![Alt text](PC_to_Switch_Ethernet.png)

**Add WAP**

  As shown in the image, a WAP has been added. However, without ethernet cables it is not connected to the switch, which means it isn't connected to the network. 
![Alt text](WAP.png)

**Connect WAP to a switch**

  Now, using an ethernet cable, the access point is communicating successfully with the switch, as indicated by the green trianlge. 
![Alt text](Accesspoint_switch.png)

**Add mobile devices**

  Now, mobile devices have been added. 
![Alt text](Access_point_mobile_devices.png)

**Set IP address on end devices (mobile devices included)**
  
  Similar to what I have done before, I have configured the IP addresses of all end devices. 
![Alt text](IP_Assignment_End_Devices.png)

**Add a router to talk to different networks**

  A router has been added, however, it is currently disconnected from the network. The router must also be connected to a power outlet and, contrary to the switch, it should have a on-off switch so make sure to turn the router on. 
![Alt text](Added_Router.png)

**Configure IPs on router**

  It will take a moment for the router to boot up as well. Once the router is turned on, you must first connect a ethernet cable to the port labeled "console" to configure the IP address on the router. 
  Once the IP address for the router itself has been configrued, the IP address for each specific LAN port on the router must also be configured. 
  Once the port has been configured, connect the switch to the router using an ethernet cable. Make sure to connect the ethernet cable to the correct port as assigned earlier. 
  I have configured the IP on the router. However, it is still not communicating with the switch. 
![Alt text](Config_Router0.png)

**Connect the switches to the router with ethernet cables**

  It will take a moment for the router to boot up as well. Once the router is turned on, you must first connect a ethernet cable to the port labeled "console" to configure the IP address on the router. 
![Alt text](Router_Added_Network.png)

**LAN Added**

  I have now added another LAN using the same exact steps as before, however, using different network ranges. I have added a new switch and two servers. 
![Alt text](Added_LAN.png)

**Set default gateway to all end devices**

  As done in the "Add end devices" step, I have configured all the default gateways on the network. However, we have to be careful of which router port used in order to configure default gateways. 
![Alt text](Added_LAN.png)


# FAQ 

1. What do I do to check if my devices are successfully connected to a LAN?
   Try to ping the other device using "terminal" if operating on a mac. On terminal, type "ping [IP address]" and if you get a response detailing ping, your device is successfully connected to the LAN. If the ping times out, check to see if the ethernet cables are securely connected to the switch and devices. If those are connected as well, check to see if the IP and subnet mask are configured properly on each device. There may be a typo error with the numbers or you may have made an error with the subnet mask. By configuring these correctly and ensuring the ethernet cables are connected, the devices should be able to communicate with each other.

2. I can't connect my devices across different LANs. What do I do?
   First, check to make sure the router is turned on. There should an on-off switch. If that's not the issue, make sure the ethernet cables are connected to the right gigabit ports. When configuring the router, you should have configured a specific port with a specific default gateway IP. You may also want to carefully check the IP values again to see if there are no typos. You also want to check if the default gateway is assigned on each of your end devices. Finally, if that is not the case make sure all the cables are securely connected with no loose ends and if this is not the issue you may have to reconfigure the router.

3. Making IP assignments more clear and concise
   As I have done so in the step-by-step configuration guide, it is good practice to make a table of all the devices in a network and assigning the IP/subnet masks beforehand. By doing this, it eradicated human error as well as being able to identify the IPs of each specific device easily. Further, a common mistake occurs when one forgets to leave the first IP address open for the default gateway. By creating a table, you are able to account for this beforehand and eradicate this mistake.

4. Setting-up / maintaining networks
   One good practice for setting-up / maintaining a network is to always have the main objective/idea before setting up the hardware. This is because various hardware and cables can get messy and inefficient without having a clear idea fo what you are trying to do. One of the ways we have done this is through creating the network in packet tracer beforehand. By making the network virtually, you are able to clearly visualize what needs to be connected to what and the actions needed to be taken to complete the network.

5. Modifying hardware
   One safety hazard to not is that unlike virtual networks on packet tracer, physical hardware has electricity running through them with high energy output at times due to the various devices connected to them. Thus, when disconnecting wires or cables from devices such as switches or cables, ensure that they are turned off. This way, it minimizes any hazards.

6. Firewall/security settings
   On mac it usually isn't an issue but with other operating systems, there are occasions where a website won't open due to firewall settings. For example, once different LANs have been connected, you may try to open a website from another device. However, with a firewall, this may be blocked, Thus, ensure that firewalls are blocked if you have any issues with opening up websites across devices.

7. Slow speeds
   Slow connectivity issues can be attributed to various factors such as outdated hardware, network traffic, bandwidth limitations, and many more. One issue which is encountered frequently is network traffic in which too many devices are trying to connect at once increasing traffic. One way to handle this is by simply decreasing the number of devices trying to connect to a network. Another solution is to increase the hardware so that the network capacity increases.

# Retrospective 


