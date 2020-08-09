<h3>Ice room walkthrough and explanation ! </h3>
<p> I won't be putting much screenshots and step by step commands, as you can find that in many other writeups ! i will focus more on explaning the logic and details behind each step </p>

<h3>I.Recon and exploitation : </h3>
<p>Let's run Nmap ! </p>
<src img="https://github.com/She9Bang/TryHackMe/blob/master/images/icenmap1.png">
<p>We notice that on port 8000 there is the "icecast streaming media server" service running, let's check if there is any vulnerabilities that fit with out system description (Windows7)</p>
<p> Just from googling "icecast streaming media server windows 7 exploit" i found a Rapid7 link, i often explore Rapid 7 first, because it means there is a metasploit module for it !
After getting the CVE code from Rapid7, i searched it on cvedetails.com, it turned out to be an Execute code overflow attack ! </p>
<src img="https://github.com/She9Bang/TryHackMe/blob/master/images/rapid7.png">
<src img="https://github.com/She9Bang/TryHackMe/blob/master/images/cve.png">

<p>Now that we know the exploit that might work, let's fireup Metasploit, search for the exploit, set the options, and launch it ! we got a Meterpreter Shell !! </p> 
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/shell.png">
