# Analyze_packets_with_Wireshark

<h1>Lab 6</h1>

<h2>Description</h2>
Scenario<br>
In this scenario, I will be investigating traffic to a website.<br>

I will analyze a network packet capture file that contains traffic data related to a user connecting to an internet site. The ability to filter network traffic using packet sniffers to gather relevant information is an essential skill as a security analyst.<br>

I will filter the data in order to:<br>

identify the source and destination IP addresses involved in this web browsing session,<br>
examine the protocols that are used when the user makes the connection to the website, and<br>
analyze some of the data packets to identify the type of information sent and received by the systems that connect to each other when the network data is captured.<br>
This how I’ll do this:<br> First, I’ll open the packet capture file and explore the basic Wireshark graphic user interface.<br> Second, I’ll open a detailed view of a single packet and explore how to examine the various protocol and data layers inside a network packet.<br> Third, I’ll apply filters to select and inspect packets based on specific criteria.<br> Fourth, I’ll filter and inspect UDP DNS traffic to examine protocol data.<br> Finally, I’ll apply filters to TCP packet data to search for specific payload text data.<br>
<br />


<h2>Languages and Utilities Used</h2>

- <b>Wireshark</b> 

<h2>Environments Used </h2>

- <b>Windows virtual machine  (Provided by Coursera [Google Cybersecurity course])</b>

<h2>Program walk-through:</h2>

<p align="center">
Launch and open sample : <br/>
<img src="https://imgur.com/Xj6F4d6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 Explore data with Wireshark<b><b> 
   1. Open the packet capture file by double-clicking the file called sample on the Windows desktop. Wireshark starts.<b>
   2. Double-click the Wireshark title bar next to the sample.pcap filename to maximize the Wireshark application window.<b> <br/>
<img src="https://imgur.com/i6swcAY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<br />
<br />
     
Apply a basic Wireshark filter and inspect a packet<b>
In this task, I’ll open a packet in Wireshark for more detailed exploration and filter the data to inspect the network layers and protocols contained in the packet.<b>
1. filter for traffic associated with a "142.250.1.139" IP address, iwayn a  that...<b>
The list of packets displayed is significantly reduced and contains only packets where either the source or the destination IP address matches the address "142.250.1.139". <b>
only two packet colors are used: light pink for ICMP protocol packets and light green for TCP (and HTTP, which is a subset of TCP) packets.<br/>
<img src="https://imgur.com/UJvpF47.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 

2. Double-click the first packet that lists TCP as the protocol.<b>
This opens a packet details pane window:<b>
The upper section of this window contains subtrees where Wireshark will provide various parts of the network packet. <b>The lower section of the window contains the raw packet data displayed in hexadecimal and ASCII text.<b> There is also placeholder text for fields where the character data does not apply, as indicated by the dot(“.”)<b/>
<img src="https://imgur.com/fiDAfNF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> <br />

Double-click the first subtree in the upper section which starts with the word "Frame".<b>
This provides you with details about the overall network packet, or frame, including the frame length and the arrival time of the packet.<b> 
It basically contain information about the entire packet of data.<b/>
<img src="https://imgur.com/riaxeBp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><b> <br />

double-click the Ethernet II subtree.<b>
This item contains details about the packet at the Ethernet level, including the source and destination MAC addresses and the type of internal protocol that the Ethernet packet contains.<b/>
<img src="https://imgur.com/ji6NWHg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><b>

double-click the Internet Protocol Version 4 subtree.<b>
This provides packet data about the Internet Protocol (IP) data contained in the Ethernet packet. It contains information such as the source and destination IP addresses and the Internal Protocol (for example, TCP or UDP), which is carried inside the IP packet.<b>
The source and destination IP addresses shown here match the source and destination IP addresses in the summary display for this packet in the main Wireshark window.<b/>
<img src="https://imgur.com/VDvyPPw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><b>

double-click the Transmission Control Protocol subtree.<b>
This provides detailed information about the TCP packet, including the source and destination TCP ports, the TCP sequence numbers, and the TCP flags.<b>
The source port and destination port listed here match the source and destination ports in the info column of the summary display for this packet in the list of all of the packets in the main Wireshark window.<b/>

<br/>
<img src="https://imgur.com/3spRDyu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Use filters to select packets <b>
1. filter to select traffic for a specific source IP address only.<b>
A filtered list is returned with fewer entries than before. It contains only packets that came from 142.250.1.139.<b/>
<img src="https://imgur.com/Bkse3zI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />

2. filter to select traffic for a specific destination IP address only:<b>
A filtered list is returned that contains only packets that were sent to 142.250.1.139.<b>
<img src="https://imgur.com/DMdDUkK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

3. filter to select traffic to or from a specific Ethernet MAC address. This filters traffic related to one MAC address, regardless of the other protocols involved:<b>
Double-click the first packet in the list. Then Double-click the Ethernet II subtree.<b>

The MAC address you specified in the filter is listed as either the source or destination address in the expanded Ethernet II subtree.<b>
<img src="https://imgur.com/niiFDks.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

4. Double-click the Internet Protocol Version 4 subtree to expand it and scroll down until the Time to Live and Protocol fields appear.<b>

The Protocol field in the Internet Protocol Version 4 subtree indicates which IP internal protocol is contained in the packet. Then check TIME TO LIVE<b>
<br/>
<img src="https://imgur.com/alU0VfY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><b>
 
<img src="https://imgur.com/ZmOu5Xo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><b>

<br />
<br />

Use filters to explore DNS packets<b>
In this task, I’ll use filters to select and examine DNS traffic. Once you‘ve selected sample DNS traffic, I need to drill down into the protocol to examine how the DNS packet data contains both queries (names of internet sites that are being looked up) and answers (IP addresses that are being sent back by a DNS server when a name is successfully resolved).<b>
1.  filter to select UDP port 53 traffic. DNS traffic uses UDP port 53, so this will list traffic related to DNS queries and responses only.<b>
<img src="https://imgur.com/XkaWDLp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
STEPS:<b>
Double-click the first packet in the list to open the detailed packet window.<b>
double-click the Domain Name System (query) subtree to expand it.<b>
double-click Queries.<b>
The name of the website that was queried is opensource.google.com.<b />
<img src="https://imgur.com/nexBgXy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><b>

Double-click the fourth packet in the list to open the detailed packet window.<b>
Scroll down and double-click the Domain Name System (query) subtree to expand it.<b>
Scroll down and double-click Answers, which is in the Domain Name System (query) subtree.<b>
The Answers data includes the name that was queried (opensource.google.com) and the addresses that are associated with that name.<b>
<br/>
<img src="https://imgur.com/pRUcBTo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

Use filters to explore TCP packets<b> 
In this task, I’ll use additional filters to select and examine TCP packets.<b> I’ll learn how to search for text that is present in payload data contained inside network packets. This will locate packets based on something such as a name and others.<b>
1. filter to select TCP port 80 traffic. TCP port 80 is the default port that is associated with web traffic:<b>
Quite a few packets were created when the user accessed the web page http://opensource.google.com.<b>
<img src="https://imgur.com/hXuBoSi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

2. Double-click the first packet in the list. The Destination IP address of this packet is 169.254.169.254.<b>
 The Time to Live value is 64. This property is contained in the Internet Protocol Version 4 subtree, which is the third subtree listed in the detailed packet inspection window.<b>
 <img src="https://imgur.com/c0qAkbZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<b />
 The Frame Length is 54 bytes. This property is contained in the Frame subtree, which is the first subtree listed in the detailed packet inspection window.<b>
 <img src="https://imgur.com/CUd7qOr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<b />
 The Header Length is 20 bytes. This property is defined in the Internet Protocol Version 4 subtree, which is the fourth subtree listed in the detailed packet inspection window.<b>
 <img src="https://imgur.com/mdbb76g.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<b />
 The Destination Address is 169.254.169.254. This property is defined in the Internet Protocol Version 4 subtree, which is the third subtree listed in the detailed packet inspection window.<b>
<img src="https://imgur.com/AptFRO4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<b />

4. filter to select TCP packet data that contains specific text data<b>
This filters to packets containing web requests made with the curl command in this sample packet capture file.<b>
<br/>
<img src="https://imgur.com/qhhk79Q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
