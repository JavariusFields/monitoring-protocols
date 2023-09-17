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
5. Now we are goint to retrieve the private ip address for virtual machine 2 so we can ping the linux machine from our windows virtual machine. Then, open up the command line or powershell and ping 10.0.0.5 (or whatever your private ip is for VM-2) to ping the Ubuntu (linux) machine. We should notice that the ping from the windows machine sent 4 packets with zero loss which tells us that the ping was successful.
6. Now, we will initiate a perpetual ping to VM-2 the same way we pinged in either Powershell or the command line. we can do the same steps to ping except we will add '-t' after the ping command. A perpetual ping will ping non-stop. We will then deny incoming ICMP traffic from inside the settings in the Azure portal.
7. To deny incoming ICMP traffic, we need to go into the Azure portal, click networking, then select "add inbound rule". Then, we need to click "ICMP", "deny", and change the priority to 200 so this will make it the higher priority and it will work. Notice how as our rule goes into effect and the ping request is not longer going through. To stop the perpetual ping, use command (ctrl) C
</p>
<img <img width="767" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/8a134b3b-37b5-4dbf-9e89-c98eadcb589b">
</p>
<img <img width="899" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/4bcea8bb-7caa-492d-833d-af4da7383870">
</p>
<img <img width="1157" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/765fd378-55f5-423b-8b1a-bcfbcb989b23">
</p>
<img width="896" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/be5afa14-3e39-402f-a9c6-6f78a6303fbe">
</p>
<img width="1076" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/d2702780-9d65-40b8-8e51-187cec9fc038">
</p>
8. Now we will observe SSH traffic. In Wireshark, we now want to filter for SSH traffic only. We now need to SSH into the Ubuntu machine from the Windows virtual machine. In Powershell or command line type "ssh username@ the private ip address from VM-2. Type yes and it will then ask for the password. Be mindful that as you enter the password, you wont be able to see it because of the nature of sshing into a device and press enter. If done correctly, we should see traffic inside of Wireshark. To exit the ssh connection, type "exit"
</p>
<img width="1236" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/c0fccf83-bf5e-4542-ad41-1ea20f43ec17"> 
</p> 
9. In Wireshark, we can now filter for DHCP traffic. Now, inside command line (or Powershell), we can see DHCP traffic by trying to issue the Windows VM a new IP so we will type ipconfig /renew. You may lose connection and it should fail but, you should be able to observe some DHCP traffic in Wireshark
</p>
<img width="1222" alt="image" src="https://github.com/JavariusFields/monitoring-protocols/assets/144845191/30e2651d-4ee1-4c77-885e-9656b9b16ed6">
</p>
10. In Wireshark, we can now filter for DNS traffic




