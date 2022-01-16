# Happy Meal

#### Author : thiefCatcher

#### Category : FORENSIC

#### Description
```The students did a lunch meeting at MacDonald's, but before they went to lunch, they push the new code to the repository.```
<hr>

#### Write up
bots.zip에는 python 스크립트가 있는 git 리포지토리가 포함되어 있습니다. 

이 저장소에는 2개의 분기가 있으며 더 많은 커밋과 파일을 보려면 분기 간에 전환해야 합니다. 

두 번째 분기에는 플래그가 포함된 .DS_Store 파일이 있습니다.

<img width="959" alt="Screen Shot 2021-12-22 at 9 59 26 AM" src="https://user-images.githubusercontent.com/84657474/147017012-a600359e-5913-4931-9c17-86454e9e5500.png">
다음과 같이 xxd 명령어를 통하여 찾을 수 있었습니다.

```CTFUA{M4c0S_1s_n0t_4_me4l}``` 
