# PRETTY GOOD PHISHER

#### Challenge author: hofill
#### Description : This phisher thinks he's the game! We got his PGP Key ID from his phishing e-mail, and we know for sure that he has another PGP key publicized under his real name! Can you find out more about him?
#### PGP Key : A2DCB36111E3656B

<hr>

# Write up
<img width="1020" alt="Screen Shot 2021-11-27 at 10 19 45 PM" src="https://user-images.githubusercontent.com/84657474/143683115-98c07d98-c35c-44c3-ab61-5d4081f90ec2.png">

제일 MISC 분야 문제 중 제일 어렵다고 느낀 문제입니다,,

사실 PGP라는 것을 처음 들어보기도 했고..  처음 들어본 문제다보니 감도 안잡혀서 삽질을 굉장히 많이 했습니다..

일단 해당 문제는 PGP Key를 통하여 유저에 이메일을 알아내는 것이 먼저였습니다.

pgp key search engine 사이트를 통하여 알아낼 수 있었습니다.

<img width="1792" alt="Screen Shot 2021-11-27 at 10 24 53 PM" src="https://user-images.githubusercontent.com/84657474/143683256-fc39c5f0-0b72-476d-98f5-f41d0afaf9b7.png">

다음과 같이 PGP Key에 등록된 이메일을 찾을 수 있었습니다.

```
tdgd11fd8@gmail.com
```

두번째로 해결해야 할 부분은 해당 메일에 실제 유저 이름을 알아내는 것이였습니다.

이 부분에서는 [GHunt](https://github.com/mxrch/GHunt)라는 OSINT 툴을 사용했습니다. (LSID 값을 못찾아서 등록하는데만 2시간 걸렸슴니다..)

<img width="1242" alt="Screen Shot 2021-11-27 at 10 31 44 PM" src="https://user-images.githubusercontent.com/84657474/143683497-5562cd7a-d1a6-4dae-9c66-be1fdeccd69a.png">

다음과 같이 해당 gmail에 등록된 이름을 찾을 수 있었습니다.

```
Theobald Dannie Gyles
```

마지막 세번째로 해결해야하는 부분은 해당 이름을 가지고 새로운 GPG Key를 찾는것이다. (사실 이 부분은 이해가 안감.. 해당 이름에 GPG키를 찾는건지 아니면 해당 이름으로 등록된 다른걸 찾는건지)

<img width="1792" alt="Screen Shot 2021-11-27 at 10 34 47 PM" src="https://user-images.githubusercontent.com/84657474/143683636-76ec53bf-ef50-422e-a1d3-a6dad0cb7335.png">

해당 사진에서 볼 수 있듯이 Gyles 부분만 통하여 Flag를 찾을 수 있었다.

```
TFCCTF{Pee,G...Pee!_w4s_wh4t_th4t_h3_t0ld_m3....!}
```



