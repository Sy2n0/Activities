# Betacap

- Author : 0xcyberpj
- Category : Forensic
- Description : Nothing to say just play with shark or something

Challenges file   
[beta_cap.zip](https://github.com/CYB3R-Syno/Tamil-CTF/files/7249184/beta_cap.zip)

<hr>

# Write up

Since it came out as a zip file, I decompressed it first.   
Then the pcapng file came out.

I opened the pcappng file through wireshark.
<img width="1792" alt="Screen Shot 2021-09-29 at 2 57 53 PM" src="https://user-images.githubusercontent.com/84657474/135211380-c2cfea7c-15ee-4b44-986a-d24606ef767f.png">

Files could be found and downloaded in File -> Export Objects -> HTTP
<img width="1317" alt="Screen Shot 2021-09-29 at 3 01 06 PM" src="https://user-images.githubusercontent.com/84657474/135211695-e17d8cc6-5dba-47ea-b46e-701a8337ed65.png">

The following is a summary of the files.
```
1. got.zip = wall.png

[15:04:35] [~/Desktop/Tamil_Forensic/Betacap/file] ❱❱❱ exiftool wall.png|grep Comment
Comment                         : if_you_going_to_play_this_ctf_then_please_put_it_as_a_wallpaper_#godblessyou
[15:04:46] [cost 0.144s] exiftool wall.png|grep Comment   
```
```
2. secret.zip = secret_kea_bulp.png

[15:05:50] [~/Desktop/Tamil_Forensic/Betacap/file] ❱❱❱ exiftool secret_kea_bulp.png|grep Comment 
Comment                         : cyberpj_is_really_a_stupid_please_check_another_zip_please
[15:05:58] [cost 0.134s] exiftool secret_kea_bulp.png|grep Comment  
```
```
3. waste = zip file

[15:06:55] [~/Desktop/Tamil_Forensic/Betacap/file] ❱❱❱ file waste
waste: Zip archive data, at least v2.0 to extract, compression method=deflate
[15:06:58] [cost 0.036s] file waste 
```

Through the file command, it was found that the waste file was a zip file.

After that, I decompressed the file and found waste.png.
<img width="1158" alt="Screen Shot 2021-09-29 at 3 08 25 PM" src="https://user-images.githubusercontent.com/84657474/135212457-221a8b3d-2835-4361-855c-c6cd35ac9470.png">

After reading the waste.png file using the cat command, I was able to check what appeared to be hex code in the file.
```{54616d696c4354467b6c69746572616c6c795f695f686174655f796f755f61745f616c6c7d0a}```
<img width="1263" alt="Screen Shot 2021-09-29 at 3 09 50 PM" src="https://user-images.githubusercontent.com/84657474/135212584-37d9849c-d481-484a-9754-20d2b6a24a43.png">

I was able to obtain a flag by decoding as follows.
<img width="1263" alt="Screen Shot 2021-09-29 at 3 12 17 PM" src="https://user-images.githubusercontent.com/84657474/135212793-66bfa63d-3d62-4cfe-87bd-fdb34298bedb.png">

Flag is ```TamilCTF{literally_i_hate_you_at_all}```
