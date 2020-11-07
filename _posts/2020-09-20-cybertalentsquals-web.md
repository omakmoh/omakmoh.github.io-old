---
title: Web Security - CyberTalents Quals 2020
published: true
---

Hello Hackers.
This is my writeup for Cybertalents Qualifications. <br>
I'll start with the First Category and which is Web Security <br>

> Challange Name: Pr0mo <br>
> Category: Web Security <br>
> Points: 100  
> Difficulty: Medium

Firstly, i run dirsearch looking for anything using the following command <br> ``python3 dirsearch.py -u http://ec2-18-156-199-115.eu-central-1.compute.amazonaws.com/promo/ -e *
``
![](/../../assets/img/pr0mo-dirsearch.PNG)<br>
i didn't find something useful <br>
Wait... what? <br>
![](/../../assets/img/waitwhat.png)<br>
Look at the Challange name again? The First thing that came to my mind is Promotion challenge in ASCWG <br>
i remembered the JWT TOKEN! <br>
![](/../../assets/img/HEHEJWT.PNG)<br>
I quickly went to my desktop and fired up burp suite then i started to intercept the request <br>
![](/../../assets/img/burpsuitejwt.PNG)<br>
Yeah! it's JWT! as I expected <br>
in my way to [JWT Website](https://jwt.io/) to decode the token <br>
![](/../../assets/img/jwtio.PNG)<br>
ohh there a role named "user" and his value "guest" <br> 
i tried to change the alg to none to bypass the secert key <br>
![](/../../assets/img/tii.PNG)<br>
but i failed :( <br>
it's time to crack the secert :D <br>
![](/../../assets/img/crackeverywhere.PNG)<br>
i went to my linux vmware machine and opened the terminal Well? <br>
Well, I'll use john the ripper tool and rockyou wordlist for crack the secert key , i put the original token in token.txt well i'll use the following command to crack the password <br>
`john token.txt --wordlist=/usr/share/wordliste/rockyou.txt --format=HMAC-SHA256` <br>
in seconds, i got the result <br>
![](/../../assets/img/jtp.PNG)<br>
Nice progress, now we have the secert, lets go back to jwt site and put it and change the user role to admin <br>
![](/../../assets/img/jwtpowertwo.PNG)<br>
Let's replace the cookie with the new cookie we crafted! <br>
WTF? Can I help you?. Text disappeard? Hmm? <br>
![](/../../assets/img/hmmmeme.PNG)<br>
Okay! no problem i'll check the page source.<br>
Okay? i found this encryption<br>
![](/../../assets/img/brainfuck.PNG)<br>
it seems like jsFuck or BrainFuck let's go to this [Website](https://www.dcode.fr/brainfuck-language) and decrypt the encryption you found in the source of the page <br>
OfF! we got the flag 
![](/../../assets/img/flag.PNG)<br>
FLAG{JWT_I_Lik3_iT}
* * *
