# Rabbit

작성자 : Syno     

분야 : Web     
문제 파일 : x     

Description     
```
Visit here to solve this challenge:-

TryHackMeTHM

flag format: CyberGrabs{}

Creator: Mr.Holmes
```
# Write up
<img width="580" alt="Screen Shot 2022-02-10 at 1 20 27 AM" src="https://user-images.githubusercontent.com/84657474/153243438-2b110c0a-1822-4de0-9bf7-155bf2d52c2b.png">

해당 문제는 ```TryHackMe```라는 사이트에서 인스턴스를 실행한 후 문제를 푸는 방식이었다.

<img width="1792" alt="Screen Shot 2022-02-10 at 1 29 28 AM" src="https://user-images.githubusercontent.com/84657474/153245084-ef768add-301c-47dc-b882-04489a5924dd.png">

<hr> 

### OpenVPN 다운 및 연결     
Add 1 hour 옆 ? 버튼 -> Use a VPN (See Instruction) 클릭
<img width="1792" alt="Screen Shot 2022-02-10 at 1 30 19 AM" src="https://user-images.githubusercontent.com/84657474/153245237-8ace1725-3940-498f-8664-8d5fffef769b.png">

우측 상단 다운로드 버튼 클릭 (Download My Configuration File)


<img width="635" alt="Screen Shot 2022-02-10 at 1 31 31 AM" src="https://user-images.githubusercontent.com/84657474/153245462-c9b6dc6b-bd36-4321-9825-84e09d03a6ba.png">


<hr>

```
sudo openvpn file.ovpn
```
명령어를 통하여 서버를 실행시킵니다.
<img width="1652" alt="Screen Shot 2022-02-10 at 1 41 49 AM" src="https://user-images.githubusercontent.com/84657474/153247490-7bc5e0bc-814b-4042-85e3-97e65e12ad2d.png">

이 후 TryHackMe 사이트에서도 볼 수 있듯이 해당 IP Address를 브라우저를 통하여 접속하면 문제 사이트에 접속할 수 있습니다.     
또한 TryHackMe 사이트 문제 설명란을 보면 ```flag.txt```에 flag가 존재하는것을 알 수 있다.
<img width="489" alt="Screen Shot 2022-02-10 at 1 45 39 AM" src="https://user-images.githubusercontent.com/84657474/153248252-998cee1c-4575-48aa-aea7-69ab1eb8f5bb.png">
<img width="1652" alt="Screen Shot 2022-02-10 at 1 48 05 AM" src="https://user-images.githubusercontent.com/84657474/153248713-4b57ddb7-f83d-44ea-be5b-c67de3d22b39.png">

해당 사이트에서 url뒤에 ```/flag.txt```를 붙이면 쉽게 Flag를 받을 수 있었다.
<img width="1652" alt="Screen Shot 2022-02-10 at 1 49 28 AM" src="https://user-images.githubusercontent.com/84657474/153248971-741c0572-8ca7-46b7-8fc8-106adf845073.png">


# Flag
```CyberGrabs{rabbit_under_rabbit_under_rabbithole_adios}``` 
