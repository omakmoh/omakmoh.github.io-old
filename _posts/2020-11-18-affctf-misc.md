---
title: Affinity CTF Lite 2020 - MISC
published: true
---
Hello, i'm *Omar* again, yesterday i've Pwned Affinity CTF Lite 2020
I'll start with the first category and it's the Miscellaneous category.
It's have one challange ( for me but the category have DiscOrder, just take the flag from discord )
Let's start with Shark has a long tail
![](/../../assets/affctf/sharkchallange.png)<br>
With the given file, [SharkHasALongTail.pcap](https://github.com/omakmoh/omakmoh.github.io/blob/main/assets/affctf/SharkHasALongTail.pcap) It's a pcap file,
Anyone will open the file in wireshark,Me too, i'll do the same.
I literally tried everything, everything was normal.
I Just noticed something very interesting, the TCP header length of all packets are under 255
![](/../../assets/affctf/packetslen.png)<br>
which means it could be decimal. After some using of google & tshark documentation i get this command `tshark -r SharkHasALongTail.pcap -T fields -e tcp.len`
i used it on the file. and the output was
![](/../../assets/affctf/output.png)<br>
Copy it and paste into cyberchef and choose Decimal recipe.
![](/../../assets/affctf/flagoutput.png)<br>
The flag is `AFFCTF{TCPDUMP_Never_Disappoints}`
