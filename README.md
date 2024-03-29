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
<P> We can see a threat actor port scanning a target system hence this information may be used for a connection attempt.</P>
<p> Statistics > Conversations </p>
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

<h3> PCAP 2 </h3>
<h3> Identify the IP address that downloaded the .zip file</h3>
<p> Most likely protocol to be HTTP, Filter to HTTP traffic, File > Export Objects > HTTP</p>
<p> If the file does not show up, Filter to different protocols such as SMB, SFTP, etc then repeat. </p>
<img src="https://imgur.com/kFBox3F.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<img src="https://imgur.com/A2Peaz5.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<p> Result: cr4ckx0r.zip file found </p>
<p> To view entire conversation better, right-click packet > Follow > TCP Stream</p>
<img src="https://imgur.com/FmC4XuP.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<p> <Strong> Red Section</Strong> GET request from client 192.168.56.1 </p>
<p> <Strong> Blue Section </Strong> OK with 200 response from server 192.168.56.111 </p>

<h3> Calculate MD5 Hash value of zip file and its contents</h3>
<img src="https://imgur.com/jEbJyxM.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<img src="https://imgur.com/iWYWzi9.png" height="80%" width="80%" alt="FTK Imager Memory Capture">

<H3> PCAP 3 </H3>
<H3> Analyze FTP server activities</H3>
<p> Filter to FTP and retrieve information on response code 220 </p>
<p> <code> ftp.response.code == 230 </code></p>
<img src="https://imgur.com/s7GRk18.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
Right Click > Follow > TCP Stream
<img src="https://imgur.com/ydzEMRn.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<p> Credentials used to log into FTP server and timestamp </p>
<img src="https://imgur.com/P3WlwFq.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<p> Scroll down to see files threat actor retrieved </p>
<img src="https://imgur.com/aja4vlZ.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<p> RETR password.backup</p>

<h2> Conclusion </h2>
Our PCAP Analysis project with Wireshark uncovered critical insights into network security threats through focused investigations.
<ul>
        <li>By analyzing ARP traffic, we identified host discovery scanning and potential connection attempts. FTP analysis revealed unsuccessful brute-force attempts, highlighting the importance of robust authentication.
.</li>
        <li>We successfully traced the source of a suspicious ZIP file through HTTP traffic analysis. Calculating the MD5 hash added a layer of security, aiding threat hunting and future incident response.
</li>
        <li>Detailed scrutiny of FTP activities unveiled successful logins, credentials, and retrieved files, such as 'password.backup,' providing a timeline for forensic analysis.





