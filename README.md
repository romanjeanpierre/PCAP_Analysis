<H1> PCAP Analysis w/ Wireshark</H1>

<h2>Brief Description</h2>
This project involves the analysis of  packet capture files (PCAP) using Wireshark. The objective is to identify suspicious or malicious activities by extracting crucial information from the network traffic.</p>

<h2>Investigation Scenarios</h2>
 <h3>PCAP 1 - Unusual Network Activity:</h3>
    <p><strong>Objective:</strong> Investigate unusual activity on a /24 subnet, identify its source, and discern the attacker's intentions.</p>
    <p><strong>Questions:</strong> Identify host discovery scanning, malicious port scanning, and FTP server-related information.</p>
    <h3>PCAP 2 - Suspicious File Download:</h3>
    <p><strong>Objective:</strong> Export and analyze a suspicious file downloaded onto a system, collecting indicators for potential threat hunting.</p>
    <p><strong>Questions:</strong> Determine source IP, source and destination ports, file name, and various attributes of the downloaded ZIP file.</p>
    <h3>PCAP 3 - FTP Server Under Attack:</h3>
    <p><strong>Objective:</strong> Analyze network traffic to determine if an FTP server is successfully attacked, identifying the attacker's actions.</p>
    <p><strong>Questions:</strong> Identify the IP running the FTP server, successful login time, credentials used, and details of the downloaded file.</p>
    <h2>Key Activities:</h2>
    <ul>
        <li>Analyzing ARP traffic for host discovery.</li>
        <li>Identifying and interpreting port-scanning activities.</li>
        <li>Extracting information from FTP traffic, including user limits and login attempts.</li>
        <li>Exporting and analyzing files from HTTP traffic, including ZIP files.</li>
        <li>Determining source and destination details of file downloads.</li>
        <li>Calculating MD5 hash values for extracted files.</li>
        <li>Analyzing FTP server activities, login times, and user credentials.</li>
    </ul>
    
<h2>Project Walk-Through</h2>

<h3> <Strong> PCAP 1</Strong></h3>

<h3> Identify evidence for Host Discovery Scanning</h3>
<p> First PCAP shows (ARP) traffic, 192.168.56.1 is asking every IP on the same subnet for their associated MAC address</p>
<p> This is a form of recon that allows a threat actor to identify Online systems within the same network when an ARP request has been replied to </p>
<img src="https://imgur.com/z3KrDPD.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<P> We can see a threat actor port scanning a target system hence this information may be used for a connection attempt. Statistics > Conversations </P>
<img src="https://imgur.com/eOkVdav.png" height="80%" width="80%" alt="FTK Imager Memory Capture">

<h3> FTP Traffic </h3>
<p> Filtering FTP traffic, we can identify active session capacity</p>
<img src="https://imgur.com/8RXM6qA.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<p> Brute Forcing Credentials, Right Click Packet > Follow > TCP Stream</p>
<p> We can see that the user has failed to login </p>
<img src="https://imgur.com/h4C3y5V.png" height="80%" width="80%" alt="FTK Imager Memory Capture">

<h3> Filter HTTP Traffic & 404 Error</h3>
<p> Retrieve web server 192.168.56.111 HTML file used to generate 404 webpage that 192.168.56.1 will see. </p>
<p> File > Export Objects > HTTP > Save to Desktop > Open to see web server properties </p>
<img src="https://imgur.com/bkOV4Tf.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<img src="https://imgur.com/0WuZB19.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<img src="https://imgur.com/k9XIXnu.png" height="80%" width="80%" alt="FTK Imager Memory Capture">








<img src="https://imgur.com/ByceLRL.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<img src="https://imgur.com/ByceLRL.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<img src="https://imgur.com/ByceLRL.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<img src="https://imgur.com/ByceLRL.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<img src="https://imgur.com/ByceLRL.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<img src="https://imgur.com/ByceLRL.png" height="80%" width="80%" alt="FTK Imager Memory Capture">


