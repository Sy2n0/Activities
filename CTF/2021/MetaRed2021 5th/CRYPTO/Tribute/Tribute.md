# Tribute

#### Author : Botto

#### Category : Crypto

#### Description
```After watching a TV Show you went to have lunch at "100 Montaditos" and you found this menu, what will you do ?``` 

<hr>

#### Write up

이것은 [Mr.Robot](https://www.youtube.com/watch?v=i9CBKGLVCME) 드라마에 나왔던 암호학입니다. 

처음에는 A1Z26 decoder를 통하여 디코딩을 진행했습니다.

다음과 같은 결과물을 얻을 수 있었습니다.
<img width="1092" alt="Screen Shot 2021-12-18 at 4 07 45 PM" src="https://user-images.githubusercontent.com/84657474/146632757-c699582c-693f-4897-8397-aa35159a9d41.png">

```GURAHZOREFJVYYURYCLBHSVAQLBHEPNYYVATOHGQBAGORQHCRQPHGQBJAGURJBBQFGURLORREQBF```

다음으로는 ROT13을 통하여 알파벳을 13글자씩 밀어내는 방식에 치환암호를 적용시켰습니다.

<img width="1792" alt="Screen Shot 2021-12-18 at 4 11 03 PM" src="https://user-images.githubusercontent.com/84657474/146632827-61baa6be-2488-474f-a14b-4f6da624fe56.png">

```THENUMBERSWILLHELPYOUFINDYOURCALLINGBUTDONTBEDUPEDCUTDOWNTHEWOODSTHEYBEERDOS```

```THE NUMBER SWILL HELP YOU FIND YOUR CALLING BUT DONT BE DUPED CUT DOWN THE WOODS THEY BEER DOS```

이제 메뉴(flag.jpeg) [Erdos-Woods number sequence](https://oeis.org/A059756) 에서 메뉴 항복을 제거해야 했습니다.

해당 숫자들을 제거한 후 빨간색으로 된 숫자들을 모으면 다음과 같은 hex값 결과가 나옵니다.

``` 43 54 46 55 41 7b 39 33 30 31 39 32 37 7d ```

이제 마지막으로 hex to string을 통하여 변환 시켜준 후 Flag를 얻을 수 있었습니다.
<img width="1792" alt="Screen Shot 2021-12-18 at 4 17 13 PM" src="https://user-images.githubusercontent.com/84657474/146632989-eb9beee3-59d8-4efb-b09d-a6426638e306.png">

```
CTFUA{9301927}
```

