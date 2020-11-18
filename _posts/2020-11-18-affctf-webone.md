---
title: Affinity CTF Lite 2020 - Web Part One
published: true
---
Continuing the Affinity CTF Lite 2020 Writeups.
First Challange:
![](/../../assets/affctf/soodefaultchallange.png)<br>
If we Open the given [Link](http://web2.affinityctf.com) it's give us a Apache2 Ubuntu
Default Page, Bruteforce & Fuzzing are not allowed,
After some manual enumeration in the HTML soruce You'll notice some unusual HTML Entites
![](/../../assets/affctf/unusualhe.png)<br>
I wrote a fast script to collect & decode the entites
[Click me to get the script](https://pastebin.com/x0P7513Q)
And run it we got the flag
![](/../../assets/affctf/script.png)
The flag is `AFFCTF{htmlentity}`

* * *
Second Challange: 
![](/../../assets/affctf/poddchallange.png)<br>
If we Open the given [Link](http://web3.affinityctf.com) it's give us a Challenge name & Challenge description
![](/../../assets/affctf/poddchallanged.png)<br>
The author gave us a directory in the description,first thing came to my mand it's [URL DOUBLE ENCODING](https://owasp.org/www-community/Double_Encoding)
I'll encode this given directory using this [Website](https://www.url-encode-decode.com)
![](/../../assets/affctf/twiceencoding.png)<br>
Then put the encoded directory in the [URL](http://web3.affinityctf.com/here%252Fis%252Fthe_flag) you'll get the flag.
The flag is `AFFCTF{1s7r1pl3D1p83tt3r?}`
