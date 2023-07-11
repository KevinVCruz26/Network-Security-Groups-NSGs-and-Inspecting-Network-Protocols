<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


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

- (Observe ICMP Traffic)
- (Observe SSH Traffic)
- (Observe DHCP Traffic)
- (Observe DNS Traffic)
- (Observe RDP Traffic)
<h2>Actions and Observations</h2>

<h1>Observe ICMP Traffic</h1>

![image](https://github.com/KevinVCruz26/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/139089937/e0b40087-4557-45c3-8787-2d96f45da1d1)

-Use Remote Desktop to connect to your Windows 10 Virtual Machine

![image](https://github.com/KevinVCruz26/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/139089937/71e8eab7-5027-4de2-9dcf-72b2ff983e63)

-Within your Windows 10 Virtual Machine, Install Wireshark

-Open Wireshark and filter for ICMP traffic only

![image](https://github.com/KevinVCruz26/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/139089937/aa176fbd-ec67-4a58-9206-fa8dffcb1d05)

-Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM

-Observe ping requests and replies within WireShark

-From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and -observe the traffic in WireShark

![image](https://github.com/KevinVCruz26/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/139089937/42d06fe0-382c-4e04-bea7-c5ddd8f5f2b3)

-Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM

-Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic

-Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity

-Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using

-Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)

-Stop the ping activity


<h1>Observe SSH Traffic</h1>

![image](https://github.com/KevinVCruz26/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/139089937/6645b583-adc1-4109-81de-319b7cbef78b)

-Back in Wireshark, filter for SSH traffic only

-From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)

![image](https://github.com/KevinVCruz26/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/139089937/94558671-2372-4ad5-9672-7020f6ac29cc)

-Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark

-Exit the SSH connection by typing ‘exit’ and pressing [Enter]

<h1>Observe DHCP Traffic</h1>

![image](https://github.com/KevinVCruz26/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/139089937/37993fc0-a586-45be-b6e1-d806ba18ca2e)


-Back in Wireshark, filter for DHCP traffic only

-From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)

-Observe the DHCP traffic appearing in WireShark

<h1>Observe DNS Traffic</h1>

![image](https://github.com/KevinVCruz26/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/139089937/045a3427-1967-4eaa-8fac-1d7135163d2d)

-Back in Wireshark, filter for DNS traffic only

![image](https://github.com/KevinVCruz26/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/139089937/190acb2a-3dc5-474e-aff2-4c2dc63c0fa2)

-From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are

-Observe the DNS traffic being show in WireShark

<h1>Observe RDP Traffic</h1>

![image](https://github.com/KevinVCruz26/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/139089937/35ecf081-aecd-49d1-b0d0-8ec878aa42ab)

-Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)

-Oserve the immediate non-stop spam of traffic? Why do you think it’s non-stop spamming vs only showing traffic when you do an activity?

-Answer: because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted

