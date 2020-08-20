<p>A Rick and Morty CTF. Help turn Rick back into a human!</p>
<p>Being a huge Rick and Morty fan, i couldn't help but challenge myself to solve this CTF ! let's see how fun it's gonna be ! </p>
<p>First things first, we start with the Nmap scan, i use the options -sV to determine the versions of services running, -sC to scan with the default Nmap scripts, and -A for O detection ! It's wise to use -p- to scna for all ports, but it takes plenty of time, especially if you're running ona VM </p>
<p><b>Scan results : </b></p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/picklerick1.png">
<p> Port 80 is open, There is a web app hosted in Apache, and port 22 is also present, that's for SSH, my guess is that we will get some credentials from the web page and ssh with them into the system ! maybe </p>
<p> First step is to explore the Web pages and run <b>Dirbuster</b></p>
<p>The web app<p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/picklerick3.png">
<p>Based on the description, i'm once again guessing that we'll need to find some credentials, ssh into the machine and find the hidden ingredients !</p>
<b>Inspecting the web page source code </b>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/picklerick4.png">
<p>Niice, we already have a username !</p>
<p>For Dirbuster, i used the medium word list which can be found here <b>/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt</b></p>
<p>For the extenstions, it's hosted on an Apache server, so we definitely add <b>php</b>, for more findings we can add <b>txt, jpeg, jpg, tar, zip..etc</b></p>
<p>I also checked <b>Be recursive</b> which means that it it finds a directory /dir1, it will keep looking for directory within it, /dir1/..</p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/picklerick2.png">
<b>Results</b>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/picklerick5.png">
<p>Let's check the Robits.txt file</p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/picklerick6.png">
<p>It seems like a password ! we can try to login with in on the Login.php page we found earlier </p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/picklerick7.png">
<p>Great, the website is vulnerable to Command injection ! let's list the current directory </p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/picklerick8.png">
<p>First flag found ! in the file <b>Sup3rS3cretPickl3Ingred.txt</b><p>
<p>For further inspect, we go back to the root folder and start from there ! <b>home and root</b> directories are interesting </p>
<img src="https://github.com/She9Bang/TryHackMe/blob/master/images/picklerick9.png">
<p>Finding the second flag is quite easy, i'll leave that to you ! Hint : it's in /home/rick</p>
<p>We have the root folder left to explore ! For that we need sudo powers, fortunately, after executing <b>sudo -l</b> we can see that we can use sudo on any command without any password ! so, now we have the sudo powers simply by adding sudo to our commands ! </p>

<p>After all we haven't used ssh, it was quite an easy CTF but fun ! </p>




