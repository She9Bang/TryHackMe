<h3>Ice room walkthrough and explanation ! </h3>
<p> I won't be putting much screenshots and step by step commands, as you can find that in many other writeups ! i will focus more on explaning the logic and details behind each step </p>

<h3>I.Recon and exploitation : </h3>
<p>Let's run Nmap ! </p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/icenmap1.png">
<p>We notice that on port 8000 there is the "icecast streaming media server" service running, let's check if there is any vulnerabilities that fit with out system description (Windows7)</p>
<p> Just from googling "icecast streaming media server windows 7 exploit" i found a Rapid7 link, i often explore Rapid 7 first, because it means there is a metasploit module for it !
After getting the CVE code from Rapid7, i searched it on cvedetails.com, it turned out to be an Execute code overflow attack ! </p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/rapid7.png">
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/cve.png">

<p>Now that we know the exploit that might work, let's fireup Metasploit, search for the exploit, set the options, and launch it ! we got a Meterpreter Shell as the user "Dark"  !! </p> 
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/shell.png">

<h3>II.Priv Escalation : </h3>
<p> First step is to do some basic Recon to try out some Priv escalation exploits ! From the previous screenshot, we can see that the windows build is 7601, the process is running on an x64 architecture </p>
<p> To search for exploits that might work, we run the command <b>'run post/multi/recon/local_exploit_suggester'</b></p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/priv0.png">
<p>Let's try the first exploit, set the eoptions and run it, It works ! </p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/priv2.png">
<p> We're not Authority system yet ! We're still the user Dark, but we have raised our privs to SYSTEM level privileges, we even have the "SeTakeOwnershipPrivilege" which allows us to take ownership of files </p>

<p>Getprivs output before priv escalation</p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/priv1.png">
<p>Getprivs output after priv escalation</p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/priv3.png">
