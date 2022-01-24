# Compromised FTP 

## Description 
```
We detected some malicious activity on our FTP server. Someone has performed bruteforce attack to gain access to our FTP server. Find out the Compromised FTP account username & the attacker IP from the following.
``` 
<hr>

So, it was basically a log file. Since, an OK status is sent on successful login in FTP, we search for string "OK".
![ftp](https://user-images.githubusercontent.com/84657474/150641128-ccbff8b4-2efc-45e2-9392-402e79115826.PNG)

Hence, the username is **ftpuser** and the IP of the attacker is **192.168.1.7**.


## Flag

```KCTF{ftpuser_192.168.1.7}```
