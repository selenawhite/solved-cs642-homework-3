Download Link: https://assignmentchef.com/product/solved-cs642-homework-3
<br>
In this part, you will find four packet traces (pcap files) that can be read by the WireShark tool (among other tools). You will need to investigate these traces to answer the questions below. To get started you will want to understand how to use WireShark’s filtering capabilities. Your solution will be a

file solutions.txt<sub>)</sub> with answers to the questions below.

Trace 1: HTTP (10 pts)

<ol>

 <li>Give three websites (domain name and IP addresses) visited from source IP address 168.0.100.</li>

 <li>Give three search queries and the domain of the site for each query made from source IP address 192.168.0.100.</li>

</ol>

Trace 2: FTP (10 pts)

FTP is the file transport protocol. There is a lot of information about it on the internet.

<ol>

 <li>What is the username and password used to connect to the FTP server?</li>

 <li>List any (and all) files that were downloaded from the FTP server.</li>

 <li>List the full path for two files (in different directories) on the FTP server that were NOT</li>

</ol>

Trace 3: Traceroute (lOpts)

Traceroute is a tool used to determine the route between two IP addresses. You can find information about it on the internet.

<ol>

 <li>Briefly describe how the traceroute tool works including which network protocols are in use.</li>

 <li>Give the source IP address that issued the traceroute command and the destination IP address.</li>

 <li>List the IP addresses on the route between source and destination.</li>

</ol>

Trace 4: POP (10 pts)

The post-office protocol (POP) is used for email.1. What is the POP username and password?

3/14/2020                                                                                                                                                                                                                                                                                                                                                            HW3

<ol start="2">

 <li>How many emails are in the user’s mailbox?</li>

 <li>Give the contents of from, to, subject, and date for one email message.</li>

 <li>What email client (application) and operating system is this person using to send and receive email?</li>

</ol>

Part 2 (60 pts)

In this part, you will write a simple intrusion detection system to detect potential attacks or dangerous behavior in network activity.

Here are three pcaps with example attacks in folder 2:

<ol>

 <li>pcap includes ARP spoof attacks.</li>

 <li>pcap includes TCP SYN port scans.</li>

 <li>pcap includes TCP SYN floods.</li>

</ol>

Your job is to write a software IDS (a Python script named <a href="http://scanner.py">scanner.py</a>) that takes as input a pcap trace and looks for all the above malicious behaviors. The local network you are protecting is configured with two machines (192.168.0.100 with MAC address 7c:d1:c3:94:9e:b8 and 192.168.0.103 with MAC address d8:96:95:01:a5:c9) and a router (192.168.0.1 with MAC address f8:1a:67:cd:57:6e). Your scanner should:

<ol>

 <li>Detect ARP spoofing attempts. (20 pts)</li>

</ol>

Output a warning including the content of the spoofing packet. The format of your output should be:

ARP spoofing!

Src MAC: XX:XX:XX:XX:XX:XX Dst MAC: XX:XX:XX:XX:XX:XX Packet number: XX

Packet number should respect the default packet order in pcap file and start from 0. Please print the MAC address in hexadecimal format with small letters.

Your program should generate the above message every time it detects a spoofing packet. No empty line between two successive ARP spoofing messages.

<ol start="2">

 <li>Detect port scans. (20 pts)</li>

</ol>

A port scan is defined to occur whenever TCP SYNs or UDP packets are sent to a 100 or more different ports on a target system. The scanner should output a warning including the victim destination IP address and the offending packet numbers. The format of your output should be:

Port scan!

Dst IP: XX.XX.XX.XX

Packet number: XX, XX, XX, XX

Packet number should respect the default packet order in pcap file and start from 0.




3/14/2020                                                          HW3

Your program should generate one above message per IP. For every victim port, you only need to report the smallest offending packet number related to that port. Make sure the reported packet numbers per message are in ascending order.

No empty line between two messages.

<ol start="3">

 <li>Detect TCP SYN floods. (20 pts)</li>

</ol>

Your tool should detect when the number of TCP SYNs to a particular destination (that are not associated with completed handshakes) exceeds 100 per second. The scanner should output a warning including the victim destination IP address, and the offending packet numbers. The format of your output should be:

SYN floods!

Dst IP: XX.XX.XX.XX

Dst Port: XX

Packet number: XX, XX, XX, XX

Packet number should respect the default packet order in pcap file and start from 0.

Your program should generate one above message per IP and port. For every victim port, you only need to report the first 101 packets within a second which are detected as a SYN flood attack. Make sure the reported packet numbers per message are in ascending order.

No empty line between two messages.

Your program should take as input the filename of a pcap file that contains captured network packets, for example:

python <a href="http://scanner.py">scanner.py</a> example.pcap

The output of your program will be the warning messages as described above. You should first output all the messages related to ARP spoofing, then messages related to port scanning, finally SYN flooding.

Please also write a README to explain <em>how to run your code </em>and <em>give one line of description of each </em><em>kind of your scanners.</em>

<em>We </em>will test your program on new pcap files other than the three we provide.

A grading script will be release shortly for this part to help you check the output style.

<em>Notes:</em>

You are required to use dpkt (v. 1.9.2) library for reading pcap files and scanning through different packet headers. Your program should be compatible with Python3.6. You can simply run<u> (— </u>

pip install

dpkt==1.9.2 to install the dpkt library in the virtual environment used for HW1.

Deliverables:




3/14/2020                                                                                                                                                                                  HW3

Submit 3 seperate files:

<ol>

 <li>txt wrt theist part,</li>

 <li>py wrt the 2nd part,</li>

 <li>README explaining <em>how to run your code and giving one line of description of each kind of your </em></li>

</ol>




HW3 Rubric

Criteria

Part 1: Trace 1 Part 1: Trace 2 Part 1: Trace 3 Part 1: Trace 4 Part 2: ARP spoofing README

Part 2: ARP spoofing implementation

Part 2: Port scan detection README

Part 2: Port scan detection implementation Part 2: SYN flood detection README

Part 2: SYN flood detection implementation