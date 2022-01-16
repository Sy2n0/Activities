# Baby misc

- Author : 0xrakesh
- Category : Forensic
- Description : See the file structure

Challenges file   
[Babymisc.zip](https://github.com/CYB3R-Syno/Tamil-CTF/files/7249033/Babymisc.zip)

**Please understand that there is an error that does not go up as a regular file, so please upload it as a zip file.**

<hr>

# Write up

When I checked through the binwalk command, I could see that there was a pdf.txt file.
<img width="1158" alt="Screen Shot 2021-09-29 at 2 27 03 PM" src="https://user-images.githubusercontent.com/84657474/135208444-ebf9356d-e3f8-4019-b243-d8a7ce6dccf9.png">

And I separated it using the -e (--extract) option.
<img width="1158" alt="Screen Shot 2021-09-29 at 2 28 46 PM" src="https://user-images.githubusercontent.com/84657474/135208648-22f3b2da-e29b-401b-894d-52cd660fb415.png">

In the txt file, we were able to check the following information.
```
[14:30:14] [~/Desktop/Tamil_Forensic/Baby misc/_Babymisc.extracted] ❱❱❱ cat 1.pdf.txt 
VGFtaWxDVEYK
[14:30:16] [cost 0.036s] cat 1.pdf.txt                                                                                                              

[14:30:17] [~/Desktop/Tamil_Forensic/Baby misc/_Babymisc.extracted] ❱❱❱ cat 2.pdf.txt 
Hello everyone
[14:30:20] [cost 0.038s] cat 2.pdf.txt                                                                                                              

[14:30:20] [~/Desktop/Tamil_Forensic/Baby misc/_Babymisc.extracted] ❱❱❱ cat 3.pdf.txt
Join our discord server - https://discord.gg/kJA6yHKn
[14:30:23] [cost 0.037s] cat 3.pdf.txt                                                                                                              

[14:30:23] [~/Desktop/Tamil_Forensic/Baby misc/_Babymisc.extracted] ❱❱❱ cat 4.pdf.txt 
Follow us in twitter - https://twitter.com/tamilctf
[14:30:27] [cost 0.034s] cat 4.pdf.txt                                                                                                              

[14:30:27] [~/Desktop/Tamil_Forensic/Baby misc/_Babymisc.extracted] ❱❱❱ cat 5.pdf.txt 
e1IzdjNyU0VyCg==
[14:30:29] [cost 0.035s] cat 5.pdf.txt                                                                                                              

[14:30:29] [~/Desktop/Tamil_Forensic/Baby misc/_Babymisc.extracted] ❱❱❱ cat 6.pdf.txt 
Did you enjoy our ctf challenges ? 
[14:30:31] [cost 0.045s] cat 6.pdf.txt                                                                                                              

[14:30:31] [~/Desktop/Tamil_Forensic/Baby misc/_Babymisc.extracted] ❱❱❱ cat 7.pdf.txt 
Did you finish remining misc challenges ?
[14:30:33] [cost 0.046s] cat 7.pdf.txt                                                                                                              

[14:30:33] [~/Desktop/Tamil_Forensic/Baby misc/_Babymisc.extracted] ❱❱❱ cat 8.pdf.txt 
Did you finish reverse engineering challenges ?
[14:30:36] [cost 0.047s] cat 8.pdf.txt                                                                                                              

[14:30:36] [~/Desktop/Tamil_Forensic/Baby misc/_Babymisc.extracted] ❱❱❱ cat 9.pdf.txt 
X21BazNfQQo=
[14:30:38] [cost 0.034s] cat 9.pdf.txt                                                                                                              

[14:30:38] [~/Desktop/Tamil_Forensic/Baby misc/_Babymisc.extracted] ❱❱❱ cat 10.pdf.txt 
This is polyglots technique.
[14:30:40] [cost 0.042s] cat 10.pdf.txt                                                                                                             

[14:30:43] [~/Desktop/Tamil_Forensic/Baby misc/_Babymisc.extracted] ❱❱❱ cat 11.pdf.txt 
Are you interesting in pwn ?
[14:30:46] [cost 0.040s] cat 11.pdf.txt                                                                                                             

[14:30:46] [~/Desktop/Tamil_Forensic/Baby misc/_Babymisc.extracted] ❱❱❱ cat 12.pdf.txt 
Did you know about polyglots ?
[14:30:48] [cost 0.040s] cat 12.pdf.txt                                                                                                             

[14:30:48] [~/Desktop/Tamil_Forensic/Baby misc/_Babymisc.extracted] ❱❱❱ cat 13.pdf.txt 
TTFzQ30K
[14:30:50] [cost 0.052s] cat 13.pdf.txt 
````

In this process, I checked the strange string in 1.pdf.txt / 5.pdf.txt / 9.pdf.txt / 13.pdf.txt, and I saw 5.pdf.txt and 9.pdf.txt and found that it was base 64.

```
1.pdf.txt = VGFtaWxDVEYK
5.pdf.txt = e1IzdjNyU0VyCg==
9.pdf.txt = X21BazNfQQo=
13.pdf.txt = TTFzQ30K
```
The decoding was performed in base 64 by connecting as follows.
```
1. VGFtaWxDVEYKe1IzdjNyU0VyCg==
2. TTFzQ30KX21BazNfQQo=
```
First Base64 Decode is "TamilCTF{R3v3rSEr"
<img width="1792" alt="Screen Shot 2021-09-29 at 2 36 53 PM" src="https://user-images.githubusercontent.com/84657474/135209321-2b667bdb-47ec-4954-a981-4c1bfee9114c.png">

Second Base64 Decode is "M1sC}_mAk3_A"
<img width="1792" alt="Screen Shot 2021-09-29 at 2 39 14 PM" src="https://user-images.githubusercontent.com/84657474/135209562-da9ecfa7-38cd-4917-b941-256bde62fe17.png">

I completed the flag by combining them based on what came out now.

Flag is ```TamilCTF{R3v3rSEr_mAk3_A_M1sC}```


