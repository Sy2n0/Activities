# Can you be Admin?

### Description
```Be Admin & get the Flag.```  

<hr>

## Write up

다음 사진과 같이 오직 ```KnightSquad``` agent 로만 접속이 가능하다고 합니다.     
![Screen Shot 2022-01-26 at 9 29 38 PM](https://user-images.githubusercontent.com/84657474/151163169-e3097f33-fc22-409e-a0c0-cafda925a565.png)

Agent를 변경하고 넘어가면 또 다른 페이지가 뜬다.     
사실 이 부분에서 엄청 당황했다.     
지금까지 경험해본 CTF에서는 Agent만 바꾸면 바꿨지.. 특정 network에서만 접속할 수 있는 문제를 처음 봤었다.     

다음 사진을 해석해보면 "이 페이지는 knight squad network를 참조하고 오직 home network에서만 접근이 가능하다" 라고 명시되어있다.     
![Screen Shot 2022-01-26 at 9 30 24 PM](https://user-images.githubusercontent.com/84657474/151163261-e021b015-5257-4870-a42f-a493b4c0ba99.png)

구글에서 조금 검색을 해본 결과 refers을 local로 바꿀 수 있다라는 Reddit에 올라와있는 댓글을 봤다.     
![Screen Shot 2022-01-26 at 9 43 04 PM](https://user-images.githubusercontent.com/84657474/151164965-84a87648-76ce-465f-ae8a-7ca7bdb1c23c.png)

그러자 해당 사진 처럼 로그인 화면으로 넘어와졌다.     
![Screen Shot 2022-01-26 at 9 37 45 PM](https://user-images.githubusercontent.com/84657474/151164226-12c5aebc-fc31-41f7-ad31-d7697a20b0ca.png)

소스코드를 보면 ```JSFuck``` 으로 인코딩 되어있는 부분을 찾을 수 있었다.     
![Screen Shot 2022-01-26 at 9 38 35 PM](https://user-images.githubusercontent.com/84657474/151164340-cfec3f41-beae-4da1-9051-a56abb360eff.png)

해당 ```JSFuck``` 을 디코딩하면 다음과 같이 뜬다.     
![Screen Shot 2022-01-26 at 9 43 46 PM](https://user-images.githubusercontent.com/84657474/151165049-7162f992-6f8a-4566-9007-f09b55a7665c.png)

뭔가 이상하다싶은 느낌이 있지만 30분 정도 삽질해본 결과 Base85로 인코딩이 되어있다는 것을 알 수 있었다.     
-> 유독 Knight CTF에서는 Base85가 많이 나온 느낌이다,,     
base85로 디코딩을 하면 username과 password를 알 수 있다.     
이제 해당 username과 password로 로그인을 해보면 된다.     
![Screen Shot 2022-01-26 at 9 45 24 PM](https://user-images.githubusercontent.com/84657474/151165297-13657a21-5d96-40ac-9432-846e4e25bee4.png)

로그인이 되었다.      
근데 Flag는 없네?? 나느 당연히 이 정도 왔으면 그냥 로그인하면 Flag를 주는 줄 알았다,,     
![Screen Shot 2022-01-26 at 9 47 24 PM](https://user-images.githubusercontent.com/84657474/151165551-c914a980-8451-4b48-bf5f-50180fb4d83b.png)

Cookie값이 추가된것을 확인할 수 있었으며, base64로 디코딩해보면 뭔지 알 수 있었다.     
```Tm9ybWFsX1VzZXI%3D``` -> ```Normal_User7.```
![Screen Shot 2022-01-26 at 9 50 08 PM](https://user-images.githubusercontent.com/84657474/151165914-c2b46735-62d2-41b3-9f54-fa620cfb9387.png)

이제 진짜 마지막이다.
해당 Normal_user7. 을 admin으로 바꾸고 암호화를 해서 넣어주면 된다.
![Screen Shot 2022-01-26 at 9 59 41 PM](https://user-images.githubusercontent.com/84657474/151167211-86ada8df-d349-4bee-a3bc-661bf12034c6.png)


## Flag
```KCTF{FiN4LIY_y0u_ar3_4dm1N}```  
