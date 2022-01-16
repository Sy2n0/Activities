# MACDONALDS

#### Challenge author: hofill
#### Description : I'm a huge Ronald fan. My fan page doubles down as my cloud storage page! You'll never find my secrets!

<hr>

# Write up

<img width="1021" alt="Screen Shot 2021-11-28 at 10 57 57 AM" src="https://user-images.githubusercontent.com/84657474/143726015-e44ac1fb-3d84-4c43-89c1-68309fad020d.png">

해당 문제는 /.DS_Store를 통하여 풀 수 있었다.
물론 CTF가 끝나자마자 롸업 쓸 시간도 안주는 줄은 몰랐다,, (서버 닫힘)

<img width="1792" alt="Screen Shot 2021-11-28 at 10 58 52 AM" src="https://user-images.githubusercontent.com/84657474/143726028-7aa0be0e-27b2-495e-a5bc-b625baef1783.png">
억울 그 자체

첫번째 /.DS_Store 에서는 Secrets 항목들이 7갠가 8개가 있었다.

이 부분에서 Secrets 안에는 뭐가 더 있구나를 팀원이 확인시켜줬으며, url/secrets/.DS_Store 로 들어가면 또 다른 .DS_Store를 다운 받을 수 있었다.

해당 파일 안에는 ```5973b4cc1d61c110188ee413cddb8652.php``` 해당 PHP가 적혀있었으며, url/secrets/5973b4cc1d61c110188ee413cddb8652.php로 접속 시 Flag를 받을 수 있었다.
<img width="1792" alt="web" src="https://user-images.githubusercontent.com/84657474/143726066-e6ebb755-aa58-4233-a154-e52c84ec9551.png">

```TFCCTF{.D5_S70r3_1s_s0_4nn0ying_wh3n_c0mp1l1ng_j4rs_y0urs3lf}```


