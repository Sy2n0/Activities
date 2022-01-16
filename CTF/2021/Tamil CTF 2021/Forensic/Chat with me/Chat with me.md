# Chat with me

- Author : Jo Praveen
- Category : Forensic
- Description : Help JoPraveen to check his GF phone, in which she hides a message secretly

Challenges file   
[chatwithme.zip](https://github.com/CYB3R-Syno/Tamil-CTF/files/7250586/chatwithme.zip)

<hr>

# Write up
The zip file was decompressed first.   
I was able to obtain the cpt file through unzip.

The configuration was confirmed through the tree command.
<img width="1158" alt="Screen Shot 2021-09-29 at 7 01 25 PM" src="https://user-images.githubusercontent.com/84657474/135247631-b739ca43-1e0b-4652-8bac-6c50df804e31.png">


The file seems important in a total of three things. 
- hiddddddeeennnnn_properlyyy.obb
- WhatsApp Chat with SECRET_DISCUSSIONS.txt
- whatsapp.zip.cpt

I checked the file on the obb first.
```
[19:04:48] [~/Desktop/Tamil_Forensic/Chat with me/Android/obb] ❱❱❱ file hiddddddeeennnnn_properlyyy.obb 
hiddddddeeennnnn_properlyyy.obb: Zip archive data, at least v2.0 to extract, compression method=deflate
[19:04:50] [cost 0.039s] file hiddddddeeennnnn_properlyyy.obb      
```

I thought it was an obb file, but I can see that it is a zip file and a password is hung.   

Second, we checked SECRET_DISCUSSIONS.txt.
<img width="1158" alt="Screen Shot 2021-09-29 at 7 27 41 PM" src="https://user-images.githubusercontent.com/84657474/135251591-67e55bc6-c3db-4e42-a59d-e77cf07f4e6c.png">

The password is not here. 
So I used **fcrackzip**.    
I was able to get a password through fcrackzip. ```samantha.```
<img width="1158" alt="Screen Shot 2021-09-30 at 8 53 27 AM" src="https://user-images.githubusercontent.com/84657474/135363953-aca42ada-a127-41a4-8c7b-8a8aebad276c.png">

After that, the unzip was conducted.
```

┌──(root💀705875b5fe6e)-[~/Downloads]
└─# unzip hiddddddeeennnnn_properlyyy.obb 
Archive:  hiddddddeeennnnn_properlyyy.obb
[hiddddddeeennnnn_properlyyy.obb] get_password.py password: 
  inflating: get_password.py   
  ```    

We were able to obtain the get_password.py file and confirmed that a format similar to Flag appeared when running.
<img width="1158" alt="Screen Shot 2021-09-30 at 8 57 27 AM" src="https://user-images.githubusercontent.com/84657474/135364215-d4d05c84-6866-4316-b352-aae131d8e635.png">

But later, we found out that this was the password for the cpt file, not the flag.
After that, we looked at cpt encryption.

Search Keyword ```cpt file encryption```
<img width="1792" alt="Screen Shot 2021-09-30 at 12 23 52 PM" src="https://user-images.githubusercontent.com/84657474/135381686-ee2491ea-2de9-417a-9a44-1763454c71ce.png">

I was able to know about crypto and continued to solve the problem using ```ccrypt```.   
I decompressed it and I was able to get a normal zip file.
<img width="1158" alt="Screen Shot 2021-09-30 at 2 23 43 PM" src="https://user-images.githubusercontent.com/84657474/135392203-587edf80-9605-4de0-8bbf-bbc1a7edcd88.png">

Also, when I decompressed the zip file, there were files similar to the first files I saw.

<img width="1158" alt="Screen Shot 2021-09-30 at 2 25 02 PM" src="https://user-images.githubusercontent.com/84657474/135392344-4fba7c9f-7ed5-4d1d-8df5-feddf766a16d.png">

I was able to see the WhatsApp\ Chat\ with\ GIMME\ FLAG\ VROO.txt file and read it myself.
<img width="1788" alt="Screen Shot 2021-09-30 at 2 27 12 PM" src="https://user-images.githubusercontent.com/84657474/135392599-f46f4c44-b18c-4f5d-ada4-f39715c365cc.png">
<img width="1788" alt="Screen Shot 2021-09-30 at 2 28 11 PM" src="https://user-images.githubusercontent.com/84657474/135392702-6f21f6f8-59b0-48ac-91f4-bd7bec431598.png">
(Please understand that the first part that was cut off was created and checked by creating a new text file.)

I was able to check again that the sticker folder had a file and moved on to the sticker folder.
Strings were checked through the strings command in the STK-20210804-WA0136.webp file.
<img width="1039" alt="Screen Shot 2021-09-30 at 2 32 02 PM" src="https://user-images.githubusercontent.com/84657474/135393049-eede2b79-80e8-4d11-8691-d98df3c386ae.png">

```
{"sticker-pack-id":"com.snowcorp.stickerly.android.stickercontentprovider 5661e2d0-bfcd-40e6-8fed-7f91e43735c5","sticker-pack-link":"https://sticker.ly/s/<sticker-pack-code>","sticker-pack-code":"3HCM91","sticker-pack-publisher":"Sticker.ly * jopraveen","android-app-store-link":"https:\/\/play.google.com\/store\/apps\/details?id=com.snowcorp.stickerly.android","ios-app-store-link":"https:\/\/itunes.apple.com\/app\/id1458740001?mt=8"}
```
This part was very eye-catching and looked special.
```
"sticker-pack-link":"https://sticker.ly/s/<sticker-pack-code>"
```
That's why I connected it and they said they need a sticker pack code after url.
Also, the sticker pack code was written on the right back row.
```
"sticker-pack-code":"3HCM91"
```
Now, let's enter url and sticker pack code to access.
If you check the site title after connecting, you were able to obtain a flag.
<img width="1792" alt="Screen Shot 2021-09-30 at 2 36 49 PM" src="https://user-images.githubusercontent.com/84657474/135393476-1df6f9c6-36f6-465e-80d6-43c4fa01e3c9.png">

Flag is ```TamilCTF{7h4ts_4_n1c3_st1ck3r}```
