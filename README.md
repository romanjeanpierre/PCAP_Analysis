<H1> PCAP Analysis w/ Wireshark</H1>

<h2>Brief Description</h2>
<p>
Project Title: CMD & PowerShell Analysis

Project Description:
This project involves the analysis of system processes and user accounts using Command Prompt (CMD) and PowerShell. The goal is to perform a thorough examination of the system's processes, user accounts, and related configurations to identify potential security risks and suspicious activities.
This project provides a practical scenario for digital forensics professionals to uncover critical evidence, aiding in the conviction of a malicious hacker. The investigation delves into multiple aspects of system artifacts, showcasing the utilization of advanced tools and methodologies to achieve a comprehensive understanding of the suspect's activities.</p>

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

