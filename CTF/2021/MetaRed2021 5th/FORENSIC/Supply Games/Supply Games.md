# Supply Games

#### Author : duarte; orang3

#### Category : FORENSIC

#### Description
```A class assignment was focused on developing a retro game. Our students created a Pacman, but we think they tried to trick us.```

<hr>

#### Write up
pacman.py 는 Utils.py의 기능을 사용하며, requirements.txt에 포함된 pip 패키지가 필요한 Python으로 만든 간단한 Pacman 게임이였습니다.

사실, requirements.txt에 포함된 pip 패키지가 전부 필요하지 않았으며, pip 패키지에 대부분은 필요하지 않은 패키지였습니다.

패키지들을 보는 과정에서 원래는 Python 패키지인 ```Turtle```이 ```tutle```로 오타가 나있는것을 볼 수 있었습니다.

```tutle```은 ```Turtle```이 하는 모든 작업과 다른 작업을 수행하는 pypi.org에 의도적으로 업로드 된것을 확인할 수 있었습니다.
<img width="1792" alt="Screen Shot 2021-12-22 at 9 42 36 AM" src="https://user-images.githubusercontent.com/84657474/147015776-cd810c08-85b2-4073-883e-fcd6a4762529.png">

pip를 통해 ```tutle```을 설치하고 pacman.py가 이를 사용하면 잠재적으로 우리가 모르는 사이에 악성코드가 실행되고 있었던겁니다.

```tutle``` 패키지에서 사용하는 ```tutle.py```에는 다음과 같은 코드가 포함되어있었습니다.

```
import tempfile
temp = tempfile.NamedTemporaryFile(mode='wb', buffering=0)
temp.write(bytes.fromhex('43544655417b30485f4e6f215f705950495f48696a41636b217d'))
```

하단 마지막 줄에 보이는 hex를 string으로 변환시키니 Flag를 얻을 수 있었다.
<img width="1122" alt="Screen Shot 2021-12-22 at 9 49 12 AM" src="https://user-images.githubusercontent.com/84657474/147016274-1b1b9dc7-f354-4452-902b-27cc806600fc.png">

```CTFUA{0H_No!_pYPI_HijAck!}```
