# Write up
- Challenges Name : How about a magic trick, hah?
- Author : Ziyad

<hr>

해당 문제는 Network 분야에 500점짜리 문제였습니다.      
pcap파일을 주며 파일을 분석하기 위해 wireshark를 사용하였습니다.

File -> Export Object -> HTML 을 통하여 파일들을 확인했습니다.
확인했을때 multipart/form-data 형식에 php 파일을 확인할 수 있었습니다.
<img width="1680" alt="Screen Shot 2022-01-16 at 4 07 16 PM" src="https://user-images.githubusercontent.com/84657474/149650742-0bcd9ac0-dbf9-4039-a405-fdaded649cb1.png">

해당 파일을 다운 후 [hexed.it](https://hexed.it) 으로 가져가서 확인해보았습니다.
파일 상단 부분에서 JFIF라는 사진 파일 형식을 확인할 수 있었습니다.
<img width="1680" alt="Screen Shot 2022-01-16 at 4 13 14 PM" src="https://user-images.githubusercontent.com/84657474/149650886-8f3ee1ac-e1c6-49dd-bd78-1c4cf0a81adc.png">

또한 하단 부분에서는 다음 사진과 같이 password 부분을 확인할 수 있었습니다.
<img width="1680" alt="Screen Shot 2022-01-16 at 4 14 30 PM" src="https://user-images.githubusercontent.com/84657474/149650912-afe515e0-340e-434c-92dd-6a06b060c147.png">

이제 상단에 필요없는 부분과 하단에 필요없는 부분을 삭제후 jpg파일로 저장을 합니다.
저장을 하게되면 다음과 같은 qr코드를 확인할 수 있습니다.
<img width="1586" alt="Screen Shot 2022-01-16 at 4 18 38 PM" src="https://user-images.githubusercontent.com/84657474/149651018-c81e9e39-6121-4658-86ff-1969a5ea54f4.png">

이제 stegosuite를 통하여 이미지에 숨겨져 있는 Flag를 추출하면됩니다.     
아까 봤듯이 Password는 다음과 같이 ```Oh, hee-hee,aha. Ha, ooh, hee,ha-ha, ha-ha.``` 입니다.

다음과 같이 Flag를 얻을 수 있었습니다.
<img width="1586" alt="Screen Shot 2022-01-16 at 4 26 29 PM" src="https://user-images.githubusercontent.com/84657474/149651193-b7631d0e-4eb6-4ae8-8f09-835b9ee2d26f.png">

<hr>

Flag is ```CSCFlag{L4ugh_1t_UP_N0w!}```
