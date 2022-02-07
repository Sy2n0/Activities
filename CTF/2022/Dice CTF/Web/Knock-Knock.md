# Lost Phone 2

작성자 : Syno    
     
분야 : osint     
문제 파일 : x     
     
Description      
```My phone just came online, it must have been an open wifi, this is the BSSID: 24:0b:88:6a:e4:c9 could you tell the location ? flag{x,y} up to 2 decimal places".``` 

<hr>

## Write up
![Screen Shot 2022-02-07 at 3 52 04 PM](https://user-images.githubusercontent.com/84657474/152739034-c3408c08-a3d6-4d74-9c8e-8eba3f58a5d9.png)
해당 문제는 OSINT분야에 문제로 Lost Phone을 해결해야지 나오는 문제였다.

문제에 설명을 보면 휴대폰이 온라인이되었고 와이파이가 열려있다고 한다.

또한 BSSID 값을 준다.

해당 BSSID 값을 통해서 x와 y에 위치를 찾는거였다.

그럼 가장 먼저 BSSID를 통하여 정보를 검색할 수 있는 [wigle](https://www.wigle.net/) 을 통하여 문제를 풀려했다.

사실 어떻게 사용하는지 몰라서 1시간 가량을 쩔쩔맸다,,

해당 사진과 같이 View -> Advanced Search에서 검색이 가능하다고한다. (그냥되는줄 알았는데 회원가입하고 로그인을 해야지 이용가능,,)
![Screen Shot 2022-02-07 at 3 45 07 PM](https://user-images.githubusercontent.com/84657474/152738169-b47296ea-6ef0-4fee-9002-f88924271151.png)

가입을 하고 로그인을 하면 다음과 같은 Advanced Search 창으로 넘어올 수 있다.

다음과 같은 부분에서 ```BSSID/MAC:``` 칸에 문제 설명에서 준 BSSID를 넣으면 된다.
![Screen Shot 2022-02-07 at 3 46 30 PM](https://user-images.githubusercontent.com/84657474/152738334-a4981d25-bb87-41c9-bda9-17c8f39376d8.png)

BSSID 값을 넣고 Query를 누르면 다음과 같은 정보가 뜬다.

사진을 잘보면 ```Est. Lat``` 과 ```Est. Long``` 값을 확인할 수 있다.

문제 설명에서 말한것처럼 Flag는 소수점 2자리까지라고 한다.
![Screen Shot 2022-02-07 at 3 47 42 PM](https://user-images.githubusercontent.com/84657474/152738491-14567e19-1d2e-4e24-a58c-178bedc1bc78.png)


## Flag
```flag{28.49, 77.41}```  

