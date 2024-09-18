# Mini-Project-01---Network-Setup-and-Troubleshooting

# Step-by-Step Configuration Guide
**Objective**

The goal of this project is to create a network that connects multiple LANs and allows communication between various devices. We'll be simulating this setup using both hardware (routers, switches, cables) and software (e.g., Packet Tracer) to replicate a multi-LAN network environment.

**Use Cases**

Campus Networks

Universities and schools such as LMU typically have multiple buildings and departments, each with its own LAN. These LANs are connected through a central network infrastructure.

Example: A university campus like Loyola Marymount University (LMU) connects multiple local networks in different buildings (e.g., libraries, labs, dormitories) to a central server in University Hall.

Benefits:
- Facilitates access to shared resources such as databases, academic tools, and online libraries.
- Provides seamless internet access and communication across departments.
- Enables secure collaboration between students, staff, and faculty.


Corporate Networks
  
Large corporations with offices and data centers around the world use networks to connect their global operations.

Example: Google’s global network infrastructure connects its offices, data centers, and cloud services across continents, allowing employees to collaborate and access resources from anywhere.

Benefits:
- Ensures data availability and redundancy across regions.
- Enables remote work and global collaboration.
- Provides centralized data storage, management, and security.

**1. Choose software and hardware**
  
To achieve the objective of connecting multiple LANs and establishing communication between devices, the following components are required:

Switches – To connect multiple devices within a LAN.

Routers – To connect different LANs.

End Devices – PCs, laptops, printers, tablets, etc.

Ethernet Cables – For connecting devices to switches and routers.c. 

**2. IP assignments**
  
  IPs are essential in identifying each device as well as allowing them to communicate with other devices. However, one of the most common issues with assigning IPs is IP address conflicts where two or more devices have the same IP. To prevent this, it would be most efficient to assign IPs beforehand to minimize confusion and human error. 
  
  For this project, networks 192.168.0.0/26 and 172.16.0.0/24 have been assigned. 
  
Device  | IP  | Default Gatway | Subnet Mask
------------- | ------------- | -------------- | ------------
Router 0 (Gig0/0)  | 192.168.0.1  |  -------------- |  255.255.255.192 
PC0  | 192.168.0.2  |  192.168.0.1 |  255.255.255.192
PC1  | 192.168.0.3  |  192.168.0.1 |  255.255.255.192 
Router 0 (Gig0/1)  | 172.16.0.1  |  -------------- |  255.255.255.0   
PC2  | 172.16.0.2  |  172.16.0.1 |  255.255.255.0
PC3 | 172.16.0.3  |  172.16.0.1 |  255.255.255.0 

**3. Add end devices (PCs/laptops/printers/tablets/etc)**
  
  Once an end device (Laptop, PC, etc) has been added, as seen in the image, you would then manually assign the IP address. 
  
  On a Mac, you would go to system settings -> network -> details -> TCP/IP -> set configure IPv4 to "Manual" -> enter IP address and subnet mask as listed in the table above. 
  
  You would also need to assign the default gateway to establish communication between the end device and the eventual addition of a router. Otherwise, the end device would not be able to recognize which channel to communicate through once a network has been established among multiuple LANs. To do this, change "router" to the assigned value as listed int he above table. 

<img width="715" alt="Screenshot 2024-09-17 at 16 58 22" src="https://github.com/user-attachments/assets/951b1072-ed31-43f1-a069-e5525751742f">

**4. Add switch**

  You then connect the end devices to the switch using the ethernet cables. It will take a little bit of time for the switch to boot and connect to the end devices. The switch must be connected to a power outlet in order for it to turn on. The switches we have been using does not have a on-off button so it should automatically turn on once plugged in. A switch connects various devices on a network, allowing them to communicate with each other and share resources. In this case, without the switch, PC 0 would not be able to communicate with PC 1. 

**5. Add a router to talk to different networks**

  A router helps connect devices to the internet and connect the devices to each other. In this project, the router allows devices from one LAN to communicate with devices from another LAN. The router must also be connected to a power outlet and, contrary to the switch, it should have an on-off switch so make sure to turn the router on. It will take a moment for the router to boot up as well. Once the router is turned on, you must first connect a console cable to the port labeled "console" to configure the IP address on the router. 

<img width="478" alt="Screenshot 2024-09-18 at 16 30 29" src="https://github.com/user-attachments/assets/6cc7d6b6-7b43-4623-b2a5-fef6f38d73e4">

<img width="532" alt="Screenshot 2024-09-17 at 17 04 50" src="https://github.com/user-attachments/assets/f870dcbf-6edb-4940-8be3-033848a0ac90">


**6. Configure IPs on router**

  Firstly, IPs have to be configured on the router because we want to identify the router within a network. Moreover, as the router, in this case, will be the default gateway, each gigabit port has to be configured so that the end devices know the pathway it has to take to reach another device. 

Once you open terminal on your mac, you need to be in the right mode to make changes. As seen in the image below, you have to begin by accessing the user exec mode by typing "Router>". This will give you access to limited commands for viewing system information. 

Then, you have to enter privileged EXEC mode by typing "enable". This gives you access to all status and configuration commands. You will know you have entered the mode if terminal is showing "Router#" on the command line. It should look like the image below

<img width="133" alt="Screenshot 2024-09-18 at 15 17 09" src="https://github.com/user-attachments/assets/e3a16ff3-92a9-4a84-bf0b-7b3515cb6547">

Once privileged exec mode is enabled, you are able to enter the global configuration mode by typing "configure terminal" or "config t". You are successfully in global configuration mode if the command line shows "Router (config)#". It should look like the image below

<img width="334" alt="Screenshot 2024-09-18 at 15 18 11" src="https://github.com/user-attachments/assets/b3326263-a242-4540-8611-b1a01ac62890">

From there, you should have access to giving the device a name. So type "hostname router01" and it should change the name of the router. You can see that the name of the host changed from Router to router01 in the image. 

<img width="322" alt="Screenshot 2024-09-18 at 15 18 50" src="https://github.com/user-attachments/assets/87fce906-822a-48ab-a8bf-2e434392b060">

Additionally, we want to now configure the router interface. 

Type "interface gigabitEthernet 0/0/0" then press enter. Then type "ip address 192.168.0.1  255.255.255.192". 

Press enter then type "description ## to switch 01 ##". 

Press enter then type "no shutdown". 

This has now configured the gigabitEthernet 0/0/0 port with the IP and subnet. 

<img width="310" alt="Screenshot 2024-09-18 at 16 18 58" src="https://github.com/user-attachments/assets/6dbd752d-475c-4f59-87f2-e216df2295ac">

To view the running configuration to ensure the information entered is correct, exit the global configuration mode with ctrl+z then type "show running-config" in privileged exec mode to check whether the information is correct (it should give you information such as the image below). 

Then save the configuration to NVRAM by typing "write memory". By saving it to the RAM, you no longer have to reconfigure the router every time because it will be saved in the memory. 

<img width="216" alt="Screenshot 2024-09-18 at 16 27 16" src="https://github.com/user-attachments/assets/f9595444-3459-448c-a9f8-68072d79c484">

Once the port has been configured, connect the switch to the router using an ethernet cable. Make sure to connect the ethernet cable to the correct port as assigned earlier. 

**7. Add LAN**

  Follow the exact same steps from the beginning to set up another LAN and configure another gigabit Ethernet port on the router. 

**8. Set default gateway to all end devices**

  As done in the "Add end devices" step, you now have to configure the default gateways of all devices. However, you must be careful which IPs are being used for the default gateway. If the LAN is connected to the router through one specific gigabitEthernet port, that specific IP must be used for the default gateway. 

**9. Test the network**

Finally, test to see if the router is working by pinging a device from one LAN to a device on another LAN. 

To do this, go to terminal and type "ping [any IP from another LAN]". If you get a ping response, your netork is communicating successfully. 


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

The project presented several unexpected challenges, particularly during the configuration process with Packet Tracer, which turned out to be more difficult than anticipated. While virtual simulations often seem straightforward, transitioning the configurations into real-world setups revealed the complexity and unpredictability of both hardware and software systems. For example, we encountered multiple issues such as typos in configuration scripts, firewalls on certain computers that had to be manually disabled, and malfunctioning hardware that disrupted the network setup. These obstacles underscored the reality that, while virtual environments simplify network building, real-world hardware and software integration is much more complicated.

One key challenge was the number of configuration errors caused by minor mistakes like typos. These seemingly small issues created significant delays, as they often went unnoticed and required tedious troubleshooting to resolve. Additionally, some computers had firewalls that blocked network connectivity, forcing us to go in and manually disable them—a step we hadn’t anticipated. To make matters worse, some of the hardware devices malfunctioned or were improperly connected, highlighting the physical limitations that virtual simulations like Packet Tracer don’t fully address. This was a clear reminder that even though setting up a network virtually might seem simple, real-world setups can be highly unpredictable.

This experience gave me a deeper appreciation for the challenges of managing both software and hardware in a network environment. In virtual simulations, making connections is easier and more straightforward. However, real-life implementation exposed problems that software alone couldn’t fix, such as hardware malfunctions and manual error corrections. It made me realize that thorough preparation and testing are crucial when transitioning from a simulated network to real-world infrastructure.

Through this process, one of the most important lessons I learned was the value of staying organized and maintaining a clear focus on the project’s objectives. At times, we became overwhelmed by the sheer number of tasks required to configure the network, which made the process feel chaotic. To mitigate this, I found it helpful to take a step back and re-examine the project goals. Without a clear sense of the objective, the steps needed to create a functional network often became unclear. I realized that working backward from the desired outcome is crucial for understanding what needs to be done.

Being organized was also essential for managing IP configurations. Ensuring that each part of the network was properly connected and assigned the correct IP addresses required attention to detail and thorough documentation. Without careful labeling and regular checks, it would have been easy to mix up addresses or connect devices incorrectly. I learned that methodically recording every step of the process and frequently verifying connections saved time and made troubleshooting more efficient.

Reflecting on the project, one key improvement that could have significantly streamlined the process is the use of Dynamic Host Configuration Protocol (DHCP). Most of the issues we encountered were tied to manually configuring IP addresses, which led to typos and misplacements. Automating this process with DHCP would have greatly reduced the margin for human error and accelerated the configuration process. Instead of focusing so much energy on fixing configuration mistakes, we could have focused on optimizing other aspects of the network. In future projects, I plan to leverage DHCP, especially when configuring large networks, to ensure smoother and faster implementation.

Another area for improvement would be testing hardware components before starting the software configuration. By verifying that all hardware is functioning correctly from the outset, we could prevent unnecessary delays caused by malfunctioning devices. This will allow the team to focus more on solving higher-level network issues rather than being distracted by hardware malfunctions.

In conclusion, this project highlighted the complexities involved in real-world network configuration, even when starting with virtual simulations like Packet Tracer. It emphasized the importance of being organized, maintaining clear objectives, and systematically verifying each step in the process. Additionally, I learned the significant time-saving benefits of using DHCP for IP configurations and the importance of ensuring that hardware is fully functional before diving into the software side of network setup. These lessons will undoubtedly influence how I approach future projects, allowing for more efficient and streamlined configurations.
