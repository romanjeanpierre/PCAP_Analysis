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
<br/>
<p align="center">
    <img src="https://imgur.com/FGCS8us.png" height="80%" width="80%" alt="Project Overview Image">
</p>
<h2>Utilities Used</h2>
<ul>
    <li><b>Windows File Analyzer</b> - https://www.mitec.cz/wfa.html</li>
    <li><b>PECmd - Eric Zimmerman's tools</b></li>
    <li><b>JumpList Explorer - Eric Zimmerman's tools</b></li>
</ul>
<br/>
<h3>Analyze .LNK files in Shortcuts folder w/ Windows File Analyzer</h3>
<p>Full file path of PlageRat file </p>
<img src="https://imgur.com/ByceLRL.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<h3> Identify ZIP files containing PlagueRat </h3>
<br/>
<img src="https://imgur.com/qt8dZ9b.png" height="80%" width="80%" alt="ProcDump Directory Change">
2020_Summer_Photos, Invoice
<h3> Analyze CMD.exe-89305D47.pf in PlagueRat file using PECmd.exe</h3>
Go to Prefetch files directory and view running programs
<br/>
<img src="https://imgur.com/QYJ7Q2F.png" height="80%" width="80%" alt="ProcDump Directory Change">
Analyze Prefetch files using PECmd.exe
<br/>
<code>PECmd.exe -f "C:\Users\BTLOTest\Desktop\Windows Investigation One\Prefetch\CMD.EXE-89305D47.pf" </code>
<br/>
<br/>
<img src="https://imgur.com/JjX9HJZ.png" height="80%" width="80%" alt="ProcDump Directory Change">
<br/>
<p>Full file name and path of PlagueRAT in CMD.EXE-89305D47 </p>
<img src="https://imgur.com/PCd3sT7.png" height="80%" width="80%" alt="ProcDump Directory Change">
<h3> Cross-Reference the prefetch files from PlagueRat.ps1 from earlier</h3>
This will open all .pf files asssociated with the string "plaguerat.ps1"
<br/>
Command => <code> PECmd.exe -k “plaguerat.ps1” -d "C:\Users\BTLOTest\Desktop\Windows Investigation One\Prefetch\" </code>
<br/>
<br/>
<p>1 of 2 Applications used: Notepad.exe</p>
<img src="https://imgur.com/OBgo8lB.png" height="80%" width="80%" alt="ProcDump Directory Change">
<img src="https://imgur.com/M5hwcPY.png" height="80%" width="80%" alt="ProcDump Directory Change">
<p>Files Referenced:</p>
<img src="https://imgur.com/gu9vfNt.png" height="80%" width="80%" alt="ProcDump Directory Change">
<br/>
<p>2 of 2 Applications used: Powershell.exe </p>
<img src="https://imgur.com/p9LrckB.png" height="80%" width="80%" alt="ProcDump Directory Change">
<p>Files Referenced: </p>
<img src="https://imgur.com/JK9mpEu.png" height="80%" width="80%" alt="ProcDump Directory Change">
<h3> Identify website that was access by user W/ Jumplist Explorer</h3>
Browser type & Domain visited
<img src="https://imgur.com/eVbpDZW.png" height="80%" width="80%" alt="PID Results Output">
Discord, Edge Browser
<h2>Conclusion</h2>
<p>Our digital forensics investigation uncovered a user downloading the PlagueRat malware. Using tools like Windows File Analyzer, PECmd, and JumpList Explorer, we tracked the user's actions through system artifacts.

Our main focus was on identifying a downloaded ZIP file containing PlagueRat. We pinpointed the full file name, ZIP details, and its contents on the compromised Windows OS.

Our investigation revealed that the user acquired the malicious payload via Discord and Microsoft Edge, emphasizing the need to monitor unconventional attack vectors.

Specialized tools helped us analyze prefetch files, exposing the PlagueRat process. Cross-referencing this with the suspect's digital footprint confirmed their involvement.

Examining the user's Jump List shed light on websites accessed through Discord and Edge, deepening our understanding of the user's actions.

By tracing the malware's origin and execution, our investigation provides practical insights for cybersecurity, emphasizing the importance of ensuring employees adhere to their respective AUP (Acceptable Use Policy). </p>

