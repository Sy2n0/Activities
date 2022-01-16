# Dark night

- Author : 0xcyberpj
- Category : Forensic
- Description : Batman hunts in dark

Challenges file   
[dark_night.zip](https://github.com/CYB3R-Syno/Tamil-CTF/files/7248957/dark_night.zip)

<hr>

# Write up
When you decompress the zip file, **dark_night.pdf** appears.

As shown in the following picture, all of the pdf files were black and nothing was visible.
This part reminded me of pdftotech.   
So I changed the file through pdftotech.
<img width="1618" alt="Screen Shot 2021-09-29 at 2 04 21 PM" src="https://user-images.githubusercontent.com/84657474/135206430-928b5ce2-1c98-499e-9f42-82002028a1d5.png">

After changing the file, I was able to download the txt file, and I thought there would be an answer here.
<img width="1792" alt="Screen Shot 2021-09-29 at 2 06 51 PM" src="https://user-images.githubusercontent.com/84657474/135206650-c197897e-4581-48ce-bd9f-e5d59cbece1c.png">

I was able to see what I saw and ASCII code, and I converted it into string.
<img width="1792" alt="Screen Shot 2021-09-29 at 2 07 43 PM" src="https://user-images.githubusercontent.com/84657474/135206716-32896fdb-7e9c-4dfb-b29b-21c4306a23b9.png">

After that, I was able to obtain a flag as follows.   
<img width="1792" alt="Screen Shot 2021-09-29 at 2 14 30 PM" src="https://user-images.githubusercontent.com/84657474/135207319-f0c85789-3c4a-4744-bdcd-e7f74bbf7da4.png">

Flag is ```TamilCTF{1_l0v3_bb44tt_man}```
