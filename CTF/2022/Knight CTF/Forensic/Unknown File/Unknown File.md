# Unknown File

## Description
```
My friend sent me a file & told me there is a flag in it. He dare me to find the flag. But I have no idea what the file is about. Can you help me get the flag?
```

<hr>

## Write up
file that contains “file” as an extension. So the first thing we can do is to check the file into HEX Editor.

<img width="1139" alt="Screen Shot 2022-01-24 at 8 08 50 PM" src="https://user-images.githubusercontent.com/84657474/150772141-b74e6527-e89e-47ba-8bba-dedffd33ab1b.png">
So by looking at headers we can see headers are tempered so let’s replace the first few HEX numbers and make the “PNG” headers.

<img width="1139" alt="Screen Shot 2022-01-24 at 8 14 53 PM" src="https://user-images.githubusercontent.com/84657474/150772992-256031a6-4bf0-42e9-8c2c-8ece3db51fdf.png">
<img width="1312" alt="Screen Shot 2022-01-24 at 8 18 39 PM" src="https://user-images.githubusercontent.com/84657474/150773520-ffc60e0d-77f7-4a12-a4bd-00aa60b9c731.png">


# Flag
```
KCTF{Imag3_H3ad3r_M4nipul4t10N}
```
