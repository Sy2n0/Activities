# Vim bar

- Author : 0xcyberpj
- Category : Forensic
- Description : its a simple straight forward challenge, use tools wisely, hope you know the power of vim dish wash bar!..... :/

Challenges file   
[vim-bar.pcap.zip](https://github.com/CYB3R-Syno/Tamil-CTF/files/7267534/vim-bar.pcap.zip)

<hr>

# Write up
First, I checked the file format.
```
[22:33:56] [~/Downloads] ❱❱❱ file vim-bar.pcap 
vim-bar.pcap: pcapng capture file - version 1.0
[22:34:00] [cost 0.038s] file vim-bar.pcap  
```

After that, we checked using the strings command.
<img width="1158" alt="Screen Shot 2021-10-01 at 10 34 56 PM" src="https://user-images.githubusercontent.com/84657474/135628858-9e91f735-bc0d-4a33-9169-3787fe17407f.png">

```vim_crypto?``` I thought it was related to vim in the part.

Next, I checked it through **wireshark**.   
This part was seen, and copy was performed after checking the hex dump.
<img width="1232" alt="Screen Shot 2021-10-01 at 10 37 58 PM" src="https://user-images.githubusercontent.com/84657474/135629403-31a34fea-031f-480a-b8aa-66756f455cdb.png">

When I proceeded as follows, I found out that it was ```Vim encrypted file data```.
<img width="1158" alt="Screen Shot 2021-10-01 at 10 42 12 PM" src="https://user-images.githubusercontent.com/84657474/135630061-36cd98ae-4b1e-40ef-9b4e-ca5ab6982076.png">

After that, I searched Google for the ```vim encryption brute force``` and saw the following on github.   
[vim encryption brute force](https://github.com/nlitsme/vimdecrypt)

I was able to get a flag as follows.
<img width="1158" alt="Screen Shot 2021-10-01 at 10 49 02 PM" src="https://user-images.githubusercontent.com/84657474/135631151-80266c05-2aa0-4715-9004-9d4597a24d05.png">
