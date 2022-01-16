# DISCORD SHENANIGANS

#### Challenge author: hofill
#### Description : We considered giving you a free flag. However, we decided against it. In general, we would never do that! Or would we? That's the beginning of a good CTF! Discord is the new Twitter. To be able to solve this challenge, you'll need to join our discord. Link in the Rules page.

<hr>

# Write up
<img width="1027" alt="Screen Shot 2021-11-27 at 9 54 05 PM" src="https://user-images.githubusercontent.com/84657474/143682126-561118a5-30b3-455f-8b55-82fa586ea271.png">

사실 해당 문제는 굉장히 당황을 한 문제였다.

이미 전 문제에서 Discord 관련해서 나온 상태였고 또 다시 Discord 와 관련지어서 나올꺼라고는 생각을 못했기 때문이다.

먼저 대회 디스코드에서 운영진이 보기에는 문장은 맞는거같은데 조금 이상한 글을 보낸것을 확인할 수 있었다.

<img width="1090" alt="Screen Shot 2021-11-27 at 9 57 20 PM" src="https://user-images.githubusercontent.com/84657474/143682244-3e4b800f-e37d-4339-8080-4442ae013b30.png">

이걸 어떻게 해야하나.. 고민을 한 5~6시간한거 같은데.. 도무지 감이 안잡혀서 다른 문제를 풀다가 갑작스럽게 붙잡고 푼 문제이다.


제일 중요했던 부분은 문제에 설명 부분이었다.

Discord is the new Twitter 다음과 같이 Discord는 새로운 Twitter입니다. 라는 문장이 굉장히 눈에 들어왔다.

해당 대회 관련 트위터도 찾아보고.. 이것저것 다 해봤는데 사실상 아무것도 못하다가 운영진이 답답했는지 힌트를 올린것을 확인했다.

<img width="524" alt="Screen Shot 2021-11-27 at 10 03 38 PM" src="https://user-images.githubusercontent.com/84657474/143682457-622d1d1b-c475-4217-bb90-1e4dcfbd7327.png">

힌트에는 트윗에는 메세지를 숨길 수 있는 방법이 있다. 숨긴 메세지를 볼 수 있나 ? 라는 형식에 문장이 있었다.

구글을 통하여 찾아보던 과정에서 [Twitter Secret Messages](https://holloway.nz/steg/) 라는 사이트를 찾을 수 있었다.

해당 사이트에서 처음 봤던 문장을 디코딩하니 Flag를 얻을 수 있었다.

<img width="1792" alt="Screen Shot 2021-11-27 at 10 06 30 PM" src="https://user-images.githubusercontent.com/84657474/143682557-58778362-bdf3-4067-99d8-552786696fdc.png">

```
TFCCTF{th1s_5t3g0_fl4g_w45_n0t_h1dden_w3ll}
```




