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
