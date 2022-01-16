# Path to Blog

#### Author : randN

#### Category : WEB

#### Description
```A professor deployed his blog with a popular web server. But he forgot the path to the rest of the blog, help him find the path to the blog /.``` 

<hr>

#### Write up

해당 문제에서는 단순한 웹 페이지가 끝이었습니다.

소스 코드에는 크게 특별한 부분이 없었으며, 링크나 다른 페이지 또한 존재하지 않았습니다.

그러나 응답 헤더에서 서버 및 해당 버전에 대한 일부 정보를 확인할 수 있었습니다.

<img width="1792" alt="Screen Shot 2021-12-18 at 4 26 46 PM" src="https://user-images.githubusercontent.com/84657474/146633225-ecff1d06-c5d0-4fd3-8ccd-38d2c9119f64.png">

Apache의 취약점에 대하여 검색하던 도중 [Apache 2.4.50 RCE Vuln](https://httpd.apache.org/security/vulnerabilities_24.html)에 따라서 2.4.50 버전은 경로 탐색 및 원격 코드 실행(RCE)에 취약하다는 것을 할 수 있었다.

이 취약점을 탐색하는데 사용할 수 있는 PoC가 있으며 [Exploit DB](https://exploit-db.com/exploits/50406)에 제공된 PoC를 사용하였습니다.

먼저 테스트를 진행했습니다.
<img width="1122" alt="Screen Shot 2021-12-18 at 4 39 33 PM" src="https://user-images.githubusercontent.com/84657474/146633545-2bf1c786-cf32-4484-afc2-6a8447c2cc70.png">

이제 우리는 Daemon 사용자로 명령을 실행 할 수 있다는 것을 알았습니다.

현재 디렉토리의 내용들을 나열했으며, 아마도 더 좋은 정보를 찾을 수 있다고 생각했습니다.
<img width="1370" alt="Screen Shot 2021-12-18 at 4 43 14 PM" src="https://user-images.githubusercontent.com/84657474/146633640-dbce769b-acab-4ea0-9f20-f8e5bfa8a522.png">

read_flag의 실행 파일의 소유자(그룹)의 동일한 파일 권한으로 실행 파일을 실행할 수 잇도록 바이너리는 setuid (및 setgid) 비트 세트가 있습니다.

또한 Binary 소스 코드도 있었습니다.
<img width="1370" alt="Screen Shot 2021-12-18 at 4 49 33 PM" src="https://user-images.githubusercontent.com/84657474/146633793-371e2049-e96f-4fc1-b834-4532a5b79aac.png">

코드를 살펴보면 현재 사용자 ID를 가져오며 0인지를 확인합니다.

이 조건이 충족된다면 Flag를 읽을 수 있으며 이를 위해 문자열을 읽을 때 BOF로 취약성을 탐색할 수 있습니다. (gets(input)) 

이 문제와 비슷한 문제를 볼 수 있었습니다. [BOF binary Exploit](https://0xrick.github,io/binary-exploitation/bof2/) 
<img width="1370" alt="Screen Shot 2021-12-18 at 4 56 08 PM" src="https://user-images.githubusercontent.com/84657474/146633971-1ef65fa3-1566-487e-844c-437560c0c1a5.png">

```CTFUA{P4th_n0rm4lize_g0n3_wRonG}``` 
