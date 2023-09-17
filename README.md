<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- https://www.loom.com/share/Observing-Traffic-in-Azure-9b27b543c1874f25913cc90f0c029ad1?sid=70783a40-c505-43b9-8c71-98e87768b117

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

<p>
  1. First, we need to go to portal.azure.com (assuming you already have an account (the free one works for this one)) and create a resource group. We are going to put our virtual machines inside of this resource group. Once you appropiately name it, you can just click "review and create". We can now make our virtual machines. We will first make our Windows virtual machine. We need to click virtual machine to start the process of creating the machine. Make sure to put it in the same resource group that we created prior. Also, be mindful of the region that you put eveything in. Some regions are limited by what services you can create. For these installations steps, we will be using West 3. We will name the first virtual machine "VM-1", make sure the image is Windows 10 with 2 screens, choose a username and password, and make sure that you don't forget to click the acknowledgement box at the bottom of this first page. Finally, we will click next until we get to the netweirking page so that we see that a virtual network and subnet created automatically for us then click review and connect
<p>
<img <img width="757" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/6c39e97e-da36-4643-be80-507bd64a960a">
</p>
<img <img width="701" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/a762340d-a3da-484e-b935-25eae42a1335">
</p>
<img <img width="728" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/de3b1837-ab77-465c-86e0-655e7775361c">
</p>
<img <img width="736" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/6d2e84a2-0ff2-41e1-8f5a-3ff747119b9e">
</p>
<img <img width="796" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/3fd07a1d-fed2-41e2-ab03-6ed77864cc9b">
<p>
2. Now, we need to make our second virtual machine. We can click on virtual machine and create a new virtual machine. Make sure to put it into the same resource group we created earlier and this time, we will keep the image as Ubuntu for our Linux virtual machine. Instead of picking ssh key, we will click password so that we can make our username and password like we did with the first virtual machine. Click review and create and now we have our second virtual machine.
<p>

<p>
<img <img width="738" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/e17d73c1-37c1-4be1-be6e-a6c34b409071">
</p>
<img <img width="744" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/a90fec43-34e0-486f-b72a-9a3e6c58e313">
<p>
3. Now we need to log into our Windows virtual machine using Microsoft Remote Desktop. Once we are inside of our virtual machine, we are going to download and install Wireshark.
"Wireshark is a network protocol analyzer, or an application that captures packets from a network connection, such as from your computer to your home office or the internet."
</p>
4. Open Wireshark. Once it's open, click the blue ethernet button in the top left and then filter for ICMP traffic.
</p>
<img <img width="767" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/8a134b3b-37b5-4dbf-9e89-c98eadcb589b">
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
