<p> With this room we will learn ways to manually exploit vulnerabilities, because you can't always rely on Metasploit and other tools ! </p>
<h3> I.Enumeration and Recon :</h3>
<p><b>Nmap scan results</b></p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/blaster1.png"></p>
<p>It seems like there is a web server running, it's the ISS windows server, a web server that runs on the Microsoft .NET platform on the Windows OS</p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/blaster2.png">
<p>Let's run dirbuster and look for hidden directories</p> 
<p>Apparenlty there is an interesting /retro directory, </p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/blaster3.png">
<p>Let's give it a tour : see what we can find</p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/blaster4.png">
<p>So far, we have a username, and what appears to be the passwod (the user mentioned that he kept spelling the name of wade's avatar wrong whenever he logged it) !</p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/blaster5.png">
<p>As advices in the room, let's use these credentials to Log into the machine via Microsoft Remote Desktop (MSRDP), for that we will use "remmina" simply instal it <b>"apt install remmina"</b> then launch it</p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/blaster6.png">
<p> We're in !</p>

<h3> II.Escalation :</h3>
<p>On the room, they asked to get a CVE the user searched for, so i went to IE history, haven't found anything !! i searched abit more here and there, then i *cheated* from another writeup, 
there was a "CVE-2019–1388" on the history ! maybe someone deleted it ? </p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/blaster7.png">
<p>The executable file for this CVE is on the user's desktop</p>
<p><b>Now, let's try to exploit it ! </b></p>
<p>Instead of boring you with details, here is a youtube video i followed that explains how to exploit it => https://www.youtube.com/watch?v=3BQKpPNlTSo </p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/blaster8.png">

<h3> III.Exploiting with Metasploit :</h3>
<p>We will use Metasploit in order to gain a persistance remote shell access ! </p>
<p> In metasploit, use <b>'exploit/multi/script/web_delivery'</b> which is a <b>web delivery exploit</b>, which fires up a web server that serves a payload, after choosing a payload, the provided command  will allow for the payload to download and execute. The main purpose of this module is to quickly establish a session on a target machine when the attacker has to manually type in the command: e.g. Command Injection, RDP Session, Local Access or maybe Remote Command Execution. </p>
<p> For the target we choose <b>powershell</b>, the payload <b>'set payload windows/meterpreter/reverse_http'</b>
<p>Once we get the command, we either manually enter in the CMD (with RDP), or host a simple python web server (python3 -m http.server), put it in a text file and serve it to the victim, to make copy/paste easier ! </p>
<p><b>Leaving a backdoor on the machine :</b></p>
<p>If the service you initially exploited is down or patched, you can still gain access to the system. Metasploit has a Meterpreter script <b>persistence.rb</b> that will create a Meterpreter service that will be available to you even if the remote system is rebooted.</p>
  <b>run persistence -X</b>
<p> It will give options to work with it</p>
