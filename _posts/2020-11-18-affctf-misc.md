---
title: Affinity CTF Lite 2020 - MISC
published: true
---
Hello, i'm *Omar* again, yesterday i've Pwned Affinity CTF Lite 2020
I'll first with the first category and it's the Miscellaneous category.
It's have one challange ( for me but the category have DiscOrder, just take the flag from discord )
- Shark has a long tail
![](/../../assets/affctf/sharkchallange.png)<br>
With the given file, [SharkHasALongTail.pcap](https://github.com/omakmoh/omakmoh.github.io/blob/main/assets/affctf/SharkHasALongTail.pcap) It's a pcap file,
Anyone will open the file in wireshark,Me too, i'll do the same.
I literally tried everything, everything was normal.
I Just noticed something very interesting, the TCP header length of all packets are under 255
![](/../../assets/affctf/packetslen.png)<br>
which means it could be decimal.
