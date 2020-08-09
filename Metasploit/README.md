<p> Explanation of some parts of the metasploit room </p>

<h3> Modules : </h3>
<p><b>Exploit :</b> Takes advantage of a system's vulnerability, and install a payload on the system. The payload can either be a reverse shell or a meterpreter 
<p><b>Payload :</b> The malicious code that the exploit executes on the system, which will give you access
<p><b>Auxiliary :</b> In metasploit any module that is not an exploit is an auxiliary module. Exploit modules always have a payload. Auxiliary modules are a fascinating feature of the framework allowing it to extend for a variety of purposes other than exploitation. You can create your own quick vulnerability scanners, port scanners, make MSF work as an FTP, HTTP or SMTP client and do a whole lot of other cool stuff. You have a ready to use code library at your disposal enabling quick development of such tools.<p>
<p><b>Encoder :</b> Obfuscation to baypass signature detection </p>
<p><b>Post :</b> can be run on compromised targets to gather evidence, pivot into a target network, and much more.</p>
<p><b>NOP :</b> used with buffer overflow and ROP attacks </p>

<h3> Commands : </h3>
<p><b> Connect :</b> By issuing the connect command with an IP address and port number, you can connect to a remote host from within msfconsole the same as you would with Netcat or Telnet.</p>
<p><b> db_nmap -sV BOX-IP : </b>  built in way to run Nmap </p>
<p><b> Post exploitatation : </b></p>
<p><b> migrate :</b> migrate a Meterpreter session from one process to another. A given process PID to migrate to or the module can spawn one and migrate to that newly spawned process.</p>
<p><b> load kiwi:</b> To load Mimikatz on metasploit (extract plaintexts passwords, hash, PIN code and kerberos tickets from memory. mimikatz can also perform pass-the-hash, pass-the-ticket or build Golden tickets.) </p>
<p><b> run post/multi/recon/local_exploit_suggester:</b> heck for various exploits which we can run within our session to elevate our privileges </p>
<p><b>shell :</b> Spawn a normal system shell (Instead of meterpreter) </p>
