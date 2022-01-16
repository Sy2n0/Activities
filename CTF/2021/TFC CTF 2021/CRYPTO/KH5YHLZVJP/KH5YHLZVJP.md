# KH5YHLZVJP

#### Challenge author: hofill
#### Description : VSZjXqmSYy HO9r144FBh 1Gv5vy5U1l uxLV68cO0m vcT2Cdrha7 qliRgqiCZC MZxl0YVJ6u fnSepQQNYh bJjYwWg3PK 4N1PJoBUWQ 8ctNT4y2OV IPDydPtdAt ZGB5uyzMIy eSuvvq5h9X Vj9soPan2T chy1HfePMc pjMpOB0s9r NvSyG6iG7O R1zDwOq6El

<hr>

# Write up 

<img width="1024" alt="Screen Shot 2021-11-27 at 10 55 49 PM" src="https://user-images.githubusercontent.com/84657474/143684403-ec5183e7-db9d-41f8-b06a-21eb90a0bf94.png">

이 문제는 코드를 짜서 풀었다.

```python
from base64 import b64decode
from pprint import pprint
import itertools
import string

xorcipher = b64decode("YHR6cGxwSQBYBQFRTUoFbUZaUGsIA2lEUAMbUAVFXFIMX10eawJTbl4DWExqBUdJARhXAlRaB0RqUkdfVF9cR0BNYHNxcWB2TQhWBwtSQUcDaUVcU2kBBmpBXAsfUgdGWVQHWl0VaAdeal4AWE9mBEhFDBlUCFtbBUVoUkpbVFhTQk1OYHNzcWZwTwJcAgZUR0AAaUReV2gFB21AUAAbUQRAWF8NXl4daQRTbF0BXkxpBUNCBBxXCFRdAUFtX0RXVVxcQU9KZXZycm11SABfBQNQQUMBZkteVWYCBG1AXgYUVQhAX1MEWVQZbAVWZl0MX0pvBEZADR1fB19bAURnUEdXUFxUTEtOZH9zdmVxTARaDAFWR0ULZ0tXVWwCA2xNXwIfVwBEX1YBVVoeaQheaVkEWE5oA0ZJBB5fBl1ZBkBsV0JXVVxUQUFNYHFyemZwTwBfBQBTR0AFbEBcX2sIAWhFWAcbXQdEWVcMWFwfbABfaFgHWUFmAEVABh5fBllUAENpXkZZUFBXQU1EbXF2c2NzSAdfAAdaR0YHaURXX2wDAGZFXAsVUgBDX18EXVofbwRSZ14AWE1qBERCBxpXCF5bB0BoVkFXWlhWRktIYXJwd21+QwheDAVaQ0MCb0NdU2gFAGZBWAIcVgRAWFcAVFUbZwFTZlkAVkxsBEhIARg=")

banned = "'`=\\^|~<"

def recover_stream(c):
    state = []
    for i in range(10):
        result = chr(ord(str(i))^c)
        if result in string.printable and result not in banned:
            state.append(result)
    return state

# Flag length: 66

for iterator in range(66):

    l = []
    for x in range(iterator,len(xorcipher),66):
        l.append(recover_stream(xorcipher[x]))

    goal = []
    for k in l:
        for h in k:
            if all(h in e for e in l) and h not in goal:
                goal.append(h)

    print(goal)
```

다음과 같은 코드를 작성하여 실행시 암호문을 디코딩할 수 있었다.

```

['T', 'U']
['F', 'G']
['B', 'C']
['B', 'C']
['T', 'U']
['F', 'G']
['{', 'z']
['0', '1']
['n', 'o']
['5', '4']
['3', '2']
['c', 'b']
['u', 't']
['r', 's']
['3', '2']
['_']
['r', 's']
['n', 'o']
['f', 'g']
['_']
['0', '1']
['3', '2', '1', '0', '7', '6', '5', '4']
['_']
['t', 'u']
['h', 'i']
['3', '2']
['-', ',']
['d', 'e']
['1', '0']
['u', 't', 'w', 'v', 'q', 'p', 's', 'r']
['l', 'm', 'n', 'o', 'h', 'i', 'j', 'k']
['f', 'g']
['4', '5']
['m', 'l']
['m', 'l']
[',', '-']
['_']
['0', '1']
['g', 'f']
['_']
['n', 'o', 'l', 'm', 'j', 'k', 'h', 'i']
['5', '4']
['n', 'o']
['x', 'y']
['_']
['5', '4', '7', '6', '1', '0', '3', '2']
['q', 'p']
['q', 'p']
['5', '4']
['(', ')', '*', '+', ',', '-', '.', '/']
['g', 'f']
['0', '1']
['l', 'm']
['l', 'm']
['7', '6', '5', '4', '3', '2', '1', '0']
['t', 'u', 'v', 'w', 'p', 'q', 'r', 's']
['_']
['f', 'g']
['s', 'r']
['o', 'n']
['b', 'c']
['i', 'h']
['d', 'e']
['u', 't']
['x', 'y']
['}']
```

선택지가 굉장히 많은 문제였다.

이중에 한가지씩 선택하면 됬었는데 사실 나같은 경우는 운빨이 한 80%는 됬던거같다.

```
TFCCTF{1n53cur3_rng_15_th3-d0wnf4ll-_0f_m4ny_4pp5.f0ll0w_fsociety}
```




