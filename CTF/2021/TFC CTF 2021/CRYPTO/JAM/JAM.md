# JAM

#### Challenge author: hofill
#### Description : Found this amazing new game! It's called Jam! It's very hard, though, can you help me advance faster?

<hr>

# Write up

<img width="1043" alt="Screen Shot 2021-11-28 at 10 13 24 AM" src="https://user-images.githubusercontent.com/84657474/143725136-74ac7aa7-53d8-4175-908b-d2206be53a87.png">


해당 문제는 푸는데 시간이 좀 걸렸던 문제다.

원래는 서버로 연결을 해서 푸는 문제였는데 해당 서버가 포너블 서버들과 동일하게 5분 간격으로 다운이 됬었다.

다음과 같은 python 코드를 통하여 문제를 해결할 수 있었다.

```python
from pwn import *
local = True
secretlen = 32

if local:
    p = process("python main.py", shell=True)
else:
    p = remote('34.65.54.58', 1343)

p.sendlineafter(b'> ', b'1') # Work once.
p.recvuntil(b'token: ')
token = p.recvline().decode().strip()
log.info('got token: %s' % token)

cmdline = "hash_extender -s %s -f md5 -d ' 1' -a '0' -l %d" % (token, secretlen)
log.info('doing hash length extension with hash_extender: %s' % cmdline)
hp = process(cmdline, shell=True)

hp.recvuntil(b'New signature: ')
exhash = hp.recvline().strip().decode()
log.info('new token: %s' % exhash)

hp.recvuntil(b'New string: ')
exhashdata = unhex(hp.recvline().strip())
log.info('hashdata: %s' % exhashdata)
hp.close()

p.sendlineafter(b'> ', b'3') # Recover last session
p.sendlineafter(b'1. How many coins did you have?\n', exhashdata[1:])
p.sendlineafter(b'2. What was your recovery token?\n> ', exhash.encode())
p.recvline()
result = p.recvline()

if b'Recovered successfully!'  in result:
    log.success("Attack success, getting flag...")
    p.sendlineafter(b'> ', b'2') # Trade
    p.sendlineafter(b'> ', b'1') # Flag
    flag = p.recvline().decode()
    log.success('Flag: %s' % flag)
else:
    log.failure('attack failed :(')

p.close()
```


```
TFCCTF{PUmP_up_th3_j4m,PUMP_17_up!h4shpump_it!}
```
