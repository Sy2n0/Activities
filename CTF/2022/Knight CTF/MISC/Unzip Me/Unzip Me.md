# Unzip Me

## Description
```
Can you unzip the file ?
``` 

<hr>

## Write up
A file was given called ```unzipme.zip``` but it isn't actually a zip file.

Printing out the file contents with cat gives

<img width="1106" alt="Screen Shot 2022-01-24 at 7 47 58 PM" src="https://user-images.githubusercontent.com/84657474/150769273-8705445d-7054-47cd-8db5-bcbddf543a17.png">

It seems that some of the flag characters are mixed up with each other     
KCTF --> CKFT

Each ith character has been swapped with the (i+1)th character so I just did a python script to reshuffle it

```py
text = "lfgat.txCKFTs{_OOy_uWsPa3P_DHt_e1f3L}"
newText = ""
for i in range(0,len(text), 2):
    newText += text[i+1]
    newText += text[i]
print(newText)
```

## Flag
```
KCTF{sO_yOu_sWaPP3D_tHe_f1L3}
```  
