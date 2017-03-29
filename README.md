# flaskstudy# Chapter A : Python 설치

## A.1 윈도우에서의 설치

- 파이썬 홈페이지 접속 : https://www.python.org/
- 'Downloads' 메뉴 클릭 -> Download Python 3.6.0 클릭 -> 실행 클릭
  - ![스크린샷 2017-02-06 오전 5.17.01](/Users/seulgi/Desktop/스크린샷 2017-02-06 오전 5.17.01.png)
- 파이썬을 처음 설치하면 지금 바로 설치할 것인지, 사용자 모드로 설치할 것인지 지정한다.
- 창 하단에는 두개의 체크박스가 있는데 
  - ![스크린샷 2017-02-06 오전 5.19.35](/Users/seulgi/Desktop/스크린샷 2017-02-06 오전 5.19.35.png)
- 위는 모든 윈도우 사용자가 파이썬을 실행 가능하도록 런처를 설치하겠는지에 대한 선택을 나타낸다. 아래는 반드시 체크할것을 권장하는데, 이 체크박스를 선택해야만 cmd 창을 열고 어떤 폴더에서든 파이썬을 실행할 수 있기 때문이다.
- 나머지는 기본값으로 설치한다.
- 시작메뉴에서 idle을 입력하고 IDLE (Python 3.6 - 32 bit)가 표시되는지 확인한다. 이것이 보이면 파이썬 설치는 완료된 것이다.

## A.2 맥 OS X에서의 설치

- 윈도우에서와 같은 방식으로 패키지 파일을 다운로드 및 실행한다.
- 패키지 안내대로 "계속" 을 클릭한다.

## A.3 리눅스에서의 설치

- RPM 기반 배포본에서의 파이썬 설치

  ```shell
  # yum install python3
  # rpm -Uvh python3-3.6.0-10.fc26.x86_64.rpm
  ```

- DEB 기반 배포본(데비안, 우분투, 민트 등)에서의 파이썬 설치

  ```shell
  # apt-get install python3
  ```

- 파이썬 소스를 내려받아 직접 설치

  ```shell
  # cd /usr/local/src
  # wget https://www.python.org/ftp/python/3.6.0/Python-3.6.0.tgz --no-check-certificate
  # tar xzf Python-3.6.0.tgz
  # cd Python-3.6.0
  # ./configure --prefix=/usr/local/python3.6
  # make
  # make intall
  ```

- 파이썬 3.6 설치 확인

  ```shell
  # /usr/local/python3.6/bin/python3
  Python 3.6.0 (v3.6.0:41df79263a11, Dec 22 2016, 17:23:13)
  [GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
  Type "help", "copyright", "credits" or "license" for more information.
  ```






# Chapter B : 파이썬 통합 개발 환경 구성

JetBrains의 PyCharm - Community

 : https://www.jetbrains.com/pycharm/download/

![스크린샷 2017-02-10 오후 6.16.44](/Users/seulgi/Desktop/스크린샷 2017-02-10 오후 6.16.44.png)



# Chapter C : 가상 환경 구성

어떤 언어로든 프로그래밍을 하다보면 개발 라이브러리의 참조가 잘모쇠어 프로그램이 잘못된 동작을 하거나 라이브러리 버전 업데이틑로 프로그램 동작이 안될 때가 있다. 파이썬은 가상 환경 구성을 통해 이 문제를 우회할 수 있으며, 파이썬3 부터 가상 환경 생성 프로그램이 포함되어 있다. 

```shell
$ pyvenv 가상환경이름
$ source 가상환경/bin/activate

$deactivate
```



# Chapter D : Flask 설치

- Flask의 설치 (**반드시 관리자 권한으로 설치**)

```shell
$ sudo pip install flask
$ sudo pip3 install flask
```

- 특정 버전의 Flask 패키지 설치

```shell
$ sudo pip install flask==1.0
```

- 번외 : 인터넷에서 찾은 방법 (추천x)

```shell
#PyCharm 으로 생성한 프로젝트 폴더에서 실행바람

$ sudo easy_install virtualenv
#sudo pip install virtualenv
#sudo apt-get install python-virtualenv

$ mkdir myproject
$ cd myproject
$ virtualenv venv
New python executable in venv/bin/python
Installing distribute............done.

#mac
$ . venv/bin/activate 

#window
$ venv\scripts\activate


$ sudo pip install Flask

#가상환경 벗어나기
$deactivate
```



## python script에 한글 사용하기

```python
print '한글'
```

python 스크립트 파일에 위의 내용을 적고 실행해보자. 아래와 같은 에러가 나온다.

```
SyntaxError: Non-ASCII character '\xc7' in file euckr-error.py on line 1, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details
```

파이썬의 기본 인코딩은 `ascii`이다. 스크립트 파일이 ascii 인코딩일거라고 가정하고 읽어서 파싱할라고 하는데 ascii로 해석이 불가능한 **한글**이라는 단어가 존재하기 떄문에 SyntaxError(문법에러)가 발생한 것이다. 이를 해결하기 위해서는 아래와 같이 스크립트 파일 첫줄에 파일의 인코딩을 명시해주면 된다.

```python
#-*- coding: utf-8 -*-
print '한글'
```

```python
#-*- coding: euc-kr -*-
print '한글'
```

이밖에 인코딩에 관련된 자세한 사항을 알고싶다면 아래 링크를 참조바란다

https://libsora.so/posts/python-hangul/



# Chapter 1 : 웹 프로그램이란 무엇인가?

웹 프로그램은 웹 브라우저로 접속해 사용하거나 HTTP메세지를 보내 원격에서 사용하는 프로그램을 말한다. 

웹은 2000년 이후 닷컴 버블*( 인터넷 관련 분야가 성장하면서 산업 국까의 주식 시장의 지분 가격이 급격한 성장을 보인 1995년부터 2000년까지의 거품 경제 현상 )*이 급격하게 꺼지면서 닷컴 버블 이전의 웹사이트나 웹 프로그램이 주로 서비스 제공자가 선택적으로 정보를 제공해왔다면, 이후는 사용자가 콘텐츠를 만드는 형태로 변해왔다.

웹 프로그래밍 기술도 기업용 웹 프로그램에서는 HTML만을 사용한 화면 설계보다 RIA(Rich Internet Application)에 적합한 ActiveX 등을 사용하는 쪽으로 변해왔고, 2010년을 전후로 자바 스크립트가 웹 프로그램 개발의 한 축을 담당하게 되었다.

웹 프로그램은 종종 웹 애플리케이션, 웹사이트, 웹 서버와 혼용하여 사용되기에 글의 문맥을 살펴 모두 웹 프로그램으로 이해하면 된다. 참고로, 이 책에서 사용된 프로그램이나 라이브러리는 파이썬 3.4 버전을 기준으로 하고 있다.



## 1.1 웹 프로그램의 통신 구조

웹 서버의 요청/처리 구조는 아래와 같다.

![스크린샷 2017-02-05 오후 2.46.48](/Users/seulgi/Desktop/스크린샷 2017-02-05 오후 2.46.48.png)

웹 서버가 웹 프로그램에 데이터 처리를 요청하지 않는 경우가 있는데, 정적 자원(단순 HTML, 파일, 이미지 파일 등)을 요청할 경우가 그렇다.

- **웹 브라우저 <-> 웹 서버 간 콘텐츠 협상** (HTTP 1.1 기준) : 웹 브라우저가 무엇을 처리할 수 있는지 웹 서버와 협상하는 단계 

  - **서버기반 협상** ( 웹 서버가 웹 브라우저에 반환할 데이터의 형태를 직접 결정 ) : 웹 브라우저가 어떤 데이터 형태를 처리할 수 있는 지 알 수없는 채로 자원의 형태를 결정해 응답

  - **에이전트 기반 협상** : 웹 서버가 응답할 데이터 처리 형태를 결정하기 위해 첫 수신을 처리한 에이전트(대개는 캐시 서버일 수 있다)에 의해 웹 서버의 데이터 처리 형태를 결정하는 협상 방법. 최적의 데이터 형태를 결정하기 위해 두 번째 요청이 필요한 경우도 있음

  - **투명한 협상** ( 서버, 에이전트 기반 협상의 장점만을 채택 ) : HTTP 콘텐츠 협상은 웹 프로그래밍에서 잘 언급되지 않는 개념이지만, REST API 서버는 웹 브라우저가 보낸 HTTP 메세지의 헤더( Accept, Accept-Language, Accept-Encoding )를 보고 웹 프로그램은 이에 적절한 데이터 형태를 결정해 응답할 의무가 존재

    ![스크린샷 2017-02-05 오후 11.34.51](/Users/seulgi/Desktop/스크린샷 2017-02-05 오후 11.34.51.png)

콘텐츠 협상이 명확하게 이루어지지 않으면 웹 브라우저는 사용자가 이해할 수 없는 형태의 데이터를 보여주거나 데이터 처리 에러로 웹 브라우저가 비정상적으로 종료할 수도 있다. 

HTTP1.1 에서는 웹 서버의 데이터 형태 결정 기능을 향상시키기 위해 웹 브라우저가 처리할 수 있는 형태를 지정한 문자열을 HTTP 메세지의 헤더에 추가로 지정해서 전달해야 한다. **문자열은 콤마로 구분되어 있으며, 좌측에 가까울수록 브라우저가 웹 프로그램으로부터 응답받기를 선호하는 처리 형태**이다.  

웹 프로그램은 웹 서버가 정적 자원 처리를 전담하게 하는 것이 효율적이지만, 자바나 파이썬 등으로 작성된 웹 프로그램은 정적 자원을 처리하기 위해 웹 서버 기능 (정적 파일을 서비스하는 기능)을 포함한 경우가 많아 실제로 웹 브라우저와 웹 프로그램 간에 웹서버는 경유지(프록시)역할로만 사용되는 경우도 적지 않다. 

- HTTP

  - TCP/IP 기반의 프로토콜
  - 웹 프로그램과 웹 브라우저가 반드시 준수
  - 메세지가 헤더와 바디로 구성

  ![그림1](/Users/seulgi/Desktop/그림2.png)

  ![그림3](/Users/seulgi/Desktop/그림3.png)




## 1.2 파이썬을 위한 웹 프로그램 통신 규약

웹 서버와 웹 프로그램 간에 메세지를 주고받을 약속이 CGI(Common Gateway Interface) 규약이다. 2000년대 초까지는 일반적으로 펄(Perl) 언어를 사용했다. 보안성을 위해 c, c++, 델파이를 사용하기도 하나 특화되어 있지 않아 작성과 유지보수가 쉽진 않다. 그렇다고 CGI가 구세대 규약으로 분류되는 것은 옳지 않다. 웹 서버와 웹 프로그램 표준 통신 규약은 1993년에 처음 정의되었고, 2004년에 RFC 3875로 재개정되었다.

파이썬에서는 웹 프로그램을 웹 서버와 독립적으로 구현할 필요가 있었는데, 파이썬 Web-SIG에서 논의된 결과를 바탕으로 2003년 WSGI(Python Web Server Gateway Interface)가 처음 제정된다. 이후 여러차례 개정을 통해 2010년 PEP 3333으로 최종 개정되었다. WSGI 기반으로 작성된 웹 프로그램의 좋은 점은 WEGI 표준을 지키는 미들웨어라면 미들웨어 종류를 가리지 않고 동작이 가능하다는 것이다. WSGI 미들웨어는 또다른 WSGI 미들웨어에 포함해 사용할 수 있으며 Flask는 Werkzeug 미들웨어 기반으로 작성되어 있다.

```python
# wsgiref.simple_server 모듈로부터 make_server 함수를 가져온다
from wsgiref.simple_server import make_server

# wsgi 함수 헤더를 작성. wsgi 함수는 CGI 환경 변수를 담고 있는 environ 인자와 웹 브라우저에 응답을 반환하는 start_response 함수를 인자로 받는다
def application(environ, start_response)
	# '키:값' 문자열 형태로 CGI 환경 변수의 키와 값을 반복하여 파이썬 리스트로 만들어 response_body에 저장
	response_body = ['%s: %s' % (key, value)
                    for key, value in sorted(environ.item())]
    # 만들어진 파이썬 리스트를 개행 문자(\n)로 이어준다
    response_body = '\n'.join(response_body)
    
    # 웹 브라우저에 응답할 상태 문자열을 저장
    status = '200 OK'
    # 웹 브라우저에 응답할 HTTP 메세지 헤더를 구성. 메세지 헤더는 파이썬 리스트 타입으로 지정하며, (헤더 키, 값) 형태의 튜플을 요솟값으로 가진다.
    response_headers = [('Content-Type', 'text/plain'),
    	('Content-Length', str(len(response_body)))]
    # start_response 함수에 상태 문자열과 윗줄에서 구성한 헤더값을 인자로 전달
    start_response(status, response_headers)
    
    # application 함수를 호출한 WSGI 서버에게 웹 브라우저에게 응답할 문자열을 요솟값으로 가지는 파이썬 리스트 타입을 반환
    return [response_body.encode("utf8")]

# make_server 함수에 WSGI 서버가 응답할 호스트, 포트번호, WSGI 함수명을전달해 WSGI 서버 객체를 만든다
httpd = make_server(
    'localhost',
    8051,
    application
)
# WSGI 서버를 기동
httpd.handle_request()
```

WSGI 프로그램은 호출 가능한 객체로 파이썬 함수나 파이썬 클래스의 __iter__ 메서드를 재정의한 객체를 사용할 수 있다. 이때 호출 가능한 객체는 환경 변수 객체(파이썬 사전)와 응답을 시작하는 함수인  start_response 객체(함수 객체)를 인자로 전달받는다.



## 1.3 파이썬 웹 프로그래밍 맛보기

파이썬의 장점은 웹 서버 구축이나 데이터베이스 설치 등에 신경쓰지 않고 웹 프로그래밍 자체에만 집중할 수 있다는 것이다. ( 파이썬은 내장 모듈로 웹 서버 모듈을 가지고 있다 )

- 셸1-1. 웹 서버 실행

```shell
$ cd ~/Desktop
$ python -m http.server 8080
Serving HTTP on 0.0.0.0 port 8080 ...
```

![스크린샷 2017-02-06 오전 1.48.06](/Users/seulgi/Desktop/스크린샷 2017-02-06 오전 1.48.06.png)

셸 1-1의 명령으로 실행된 웹 서버는 정적 자원만을 서비스 할 수 있으며 HTTP 콘텐츠 협상 기능이 포함된 상태이다. 요즘은 자바스크립트를 사용한 개발이 활성화되어 있는데, Ajax 기술을 사용할 때 반드시 웹 서버가 필요한 경우가 있다. 이 때 파이썬을 사용하면 웹서버 기능을 사용할 수 있을 뿐만 아니라 웹 서버 기능을 사용하다 필요없어지면 파이썬 실행 창을 그냥 닫으면 된다.

- 코드1-2

  ```python
  import http.server
  import socketserver

  PORT = 8080

  # PORT로 들어오는 요청을 http.server 모듈의 SimpleHTTPRequestHandler 가 처리
  Handler = http.server.SimpleHTTPRequestHandler

  # socketserver 모듈의 TCPServer 클래스를 인스터스화
  httpd = socketserver.TCPServer(("", PORT), Handler)

  print("serving at port", PORT)
  # 소켓서버 실행, 소켓서버가 PORT로 들어오는 연결을 계속 감시
  httpd.serve_forever()
  ```

파이썬 내장 웹 서버는 정적 파일만을 서비스하는 웹 서버만 있지 않고 CGI 스크립트를 지원하도록 하는 내장 웹 서버 (이하 CGI 서버)를 실행할 수도 있다. CGI 서버의 실행은 정적인 웹서버와 달리 CGI 스크립트가 있는 디렉터리를 생성해야 한다.

- 셸1-2 CGI 서버 실행

  ```shell
  $ mkdir -p $HOME/cgi-server/{cgi-bin,htbin}
  $ cd $HOME/cgi-server
  $ python -m http.server --cgi 8080
  ```

![스크린샷 2017-02-06 오전 2.00.32](/Users/seulgi/Desktop/스크린샷 2017-02-06 오전 2.00.32.png)

CGI 서버는 보안상의 이유로 CGI 스크립트를 cgi-bin이나 htbin 디렉터리에 모아두는 것이 관례이며, 이 관례는 NCSA HTTPD Server로부터 시작했다고 보는 것이 일반적이다.



> 과거에 사용되었던 방식의 프로그래밍도 가능하다는 것을 설명하기 위해 CGI 서버를 예제로 설명하지만 현대의 웹 프로그래밍에서 CGI 스크립트 직접 실행은 보안 문제로 권장되지 않으며, 아파치 웹 서버 등의 배포본에서도 기본 설정에서 CGI 직접 실행은 막혀 있다.



- CGI 스크립트 예제

  - 코드1-3 $HOME/cgi-server/cgi-bin/helloworld.py

    ```python
    #!/usr/bin/env python
    print("Content-Type: text/xml;\n\n")
    print("Hello World")
    ```

    - CGI 스크립트는 CGI 서버가 웹 브라우저의 요청을 받아 CGI 스크립트 파일을 셸로 실행한 결과를 웹 브라우저의 반환하는 방식이기에 작성이나 저장시에 주의해야한다.
    - CGI 스크립트를 작성할 때는 첫 줄에 프로그래밍 언어의 실행 파일 경로를 적어주고 웹 브라우저에 보낼 HTTP 응답 메세지를 직접 기록
    - !/usr/bin/env python 이 문장은 셸의 PATH에서 실행 가능한 파이썬 경로를 찾아 실행하라는 의미

  - 셸1-3

    ```shell
    $ chmod +x $HOME/cgi-server/cgi-bin/helloworld.py
    ```

![스크린샷 2017-02-06 오전 2.07.20](/Users/seulgi/Desktop/스크린샷 2017-02-06 오전 2.07.20.png)

- 코드1-4 파이썬 스크립트로 CGI 서버 실행

  ```shell
  import http.server
  import socketserver

  PORT = 8080

  Handler = http.server.CGIHTTPRequestHandler

  httpd = socketserver.TCPServer(("", PORT), Handler)
  httpd.server_name = "localhost"
  httpd.serve_port = PORT
  ```

  - 코드1-2 와 유사

- 코드 1-5 클래스로 작성한 WSGI 애플리케이션(코드 1-1)

```python
from wsgiref.simple_server import make_server

class Application(object):
    def __init__(self, environ, start_response):
        self.environ = environ
        self.start_response = start_response
        
    def __iter__(self)
		response_body = ['%s: %s' % (key, value)
        	for key, value in sorted(self.environ.item())]
    	response_body = '\n'.join(response_body)
    
    	status = '200 OK'
    	response_headers = [('Content-Type', 'text/plain'),
        	('Content-Length', str(len(response_body)))]
    	self.start_response(status, response_headers)
        yield response_body.encode("utf8")

httpd = make_server(
    'localhost',
    8051,
    application
)
httpd.serve_forever()
```

클래스 형태로 작성한  WSGI 애플리케이션도 함수형과 크게 다르지 않다.





# Chapter 2 : Flask 시작하기

파이썬에서 웹 프로그래밍 용도의 프레임워크는 Flask 뿐만 아니라 Django(장고), Web2py(웹투파이), Turbogears(터보기어)같은 Full Stack(이하 풀스택) 프레임워크 같은 것들도 있다. Flask는 앞서 언급한 프레임워크와 달리 마이크로(micro) 프레임워크이다.

풀스택 프레임워크는 보통 웹 프로그래밍을 할 때 필요로 하는 모든 것들이 종합적으로 갖춰진 프레임워크를 의미하는데 파이썬의 배터리 포함 전략과 비슷한 모양새를 가지고 있으며 프로그래밍 할때는 프레임워크에서 제공하는 모듈이나 사용방법만 익히면 된다.

반면, 마이크로 프레임워크는 파이썬 웹 프로그래밍에서 가장 핵심적인 요소만 포함하고 있다. Flask의 경우는 WSGI 코어와 URL 라우팅을 지원하기 위해 werkzeug(벡자이그)와 템플릿 출력을 위해 Jinja2 라이브러리를 함께 배포한다. 이와같은 특징 덕에 데이터베이스 통합, 폼 유효성 검사, 업로드 처리, 다양한 개방형 인증 기술을 프로그래머와 환경에 맞게 추가하거나 직접 개발해서 사용할 수 있다.

Flask는 웹 프로그램의 개발 과정에서 설정해야 하는 환경 설정 값( 템플릿 경로, 정적인 파일이 있는 경로의 설정 등 )을 갖고 있고 프로그램 소스 트리 내에 static, templetes 디렉터리를 기본적으로 갖춰야 한다.



## 2.1 Flask와 함께 떠나는 웹 여행

- 프로그램 소스 트리

  ![스크린샷 2017-02-06 오전 2.57.47](/Users/seulgi/Desktop/스크린샷 2017-02-06 오전 2.57.47.png)

- 코드 2-1 __init__.py

  ```python
  from flask import Flask
  app = Flask(__name__) # 실행중인 모듈의 이름을 가리키는 __name__변수의 값을 전달하지만 임의 문자열도 전달할 수 있다

  # GET 요청에 대해 뷰 함수 등록
  @app.route('/') # route 데코레이터는 첫번째 인자를 반드시 필요로 함
  def hello_world():
      return 'Hello World!' # 뷰 함수는 처리가 끝나면 반드시 클라이언트에 응답을 반환하기 위해 return 문을 사용해야 함
  ```

- 코드 2-2 기동 스크립트 app_start.py

  ```python
  # helloworld 모듈로부터 app 이름을 가져온다. 실행중인 파이썬 프로그램의 모든 네임스페이스에서 이름을 찾지 못한 경우 NameError 예외가 발생
  from helloworld import app

  # app_start.py 이 실행되는 네임스페이스 이름이 __main__인 경우 테스트 서버를 실행
  if __name__ == '__main__':
      app.run()
  ```

- 셸 2-1 helloworld 프로그램 실행

  ```shell
  $ python app_start.py
  * Running on http://0.0.0.0:5000/
  ```

  ![스크린샷 2017-02-06 오전 3.08.02](/Users/seulgi/Desktop/스크린샷 2017-02-06 오전 3.08.02.png)



Flask 클래스는 웹 프로그램은 모든 기본 토대가 되므로 조금 더 자세히 살펴볼 필요가 있다.

![스크린샷 2017-02-06 오전 3.35.47](/Users/seulgi/Desktop/스크린샷 2017-02-06 오전 3.35.47.png)

Flask 클래스로부터 객체 생성이 완료되면, app 변수는 Flask 인스턴스를 담고 있는 객체 변수(인스턴스)로 취급된다. 

- Flask는 객체 변수로부터 가능한 작업
  - 글로벌 객체

    - 파이썬 언어 특정상 전역 영역은 어플리케이션 전체가 아닌 모듈 단위의 영역

    - 때문에 전역적으로 데이터를 보관하고 사용할 수 있도록 글로벌 객체 제공

      ```python
      from flask import g

      # 데이터베이스 연결을 시도하고 생성된 DB 연결 객체를 반환하는 함수
      def connect_db():
          # 데이터베이스 연결에 시도하는 설정값은 config 객체에 DATABASE 키 값으로 저장되어 있다
          return sqlite3.connect(app.config['DATABASE'])

      # before_request 데코레이터를 사용해 선언, HTTP 요청이 올때마다 실행된다
      @app.before_request
      def before_request():
          g.db = connect_db()

      # teardown_request 데코레이터 사용, HTTP 응답이 이뤄질 때 호출되어 처리된다
      @app.teardown_request
      def teardown_request(exception):
          db = getattr(g, 'db', None)
          if db is not None:
              db.close()
      ```

  - 사용자 응답 객체 생성

    - HTTP 응답 헤더를 추가/변경할 경우, make_response 함수를 이용

      ![그림6](/Users/seulgi/Desktop/그림6.png)

      - 코드 2-5 response_class 응답 객체 생성

        ```python
        # Response 클래스는 6개의 인자를 초기화 인자로 받는다
        from flask import Response, make_response

        @app.route('/')
        def response_test():
            # 이 코드는 웹 브라우저에 Custom Response라는 문자열을 돌려주고 HTTP 응답 메세지 헤더의 Program 키와 키 값을 설정한다. 상태 코드 값은 200으로 설정해서 브라우저의 요청이 성공적으로 처리되었음을 알린다
            custom_response = Response("Custom Response", 200, {
              "Program": "Flask Web Application"
            })

            return make_response(custom_response)
        ```

      - 코드 2-6 str 문자열 사용

        ```python
        from flask import make_response

        @app.route('/')
        def response_test():
            return make_response("Custom Response")
        ```

        - 문자열 응답 객체를 사용하는 경우는 HTTP 응답 헤더 조정이나 HTTP 응답 상태 코드 수정 등의 일을 수행할 수 없다.

      - 코드 2-7 unicode 문자열 사용

        ```python
        from flask import make_response

        @app.route('/')
        def response_test():
            return make_response(u"Custom Response")
        ```

        - 파이썬 3 이상에서는 모든 문자열을 유니코드로 취급하므로 일반 문자열을 사용해도 괜찮지만 **파이썬 2.x 버전을 사용하는 경우는 반드시 유니코드임을 표시**해줘야한다.

      - 코드 2-8 WSGI function 사용

        ```python
        from flask import make_response

        @app.route('/')
        def response_test():
            # WSGI 함수 정의 시작
            def application(environ, start_response):
                # REQUEST_METHOD는 웹 브라우저가 URL을 어떤 메서드로 호출했는지가 저장된다. 코드 2-8의 경우 'The request method was GET' 문자열을 응답한다
            	response_body = 'The request method was %s' % environ['REQUEST_METHOD']
                
            	status = '200 OK'
              	response_headers = [
                    ('Content-Type', 'text/plain'),
              		('Content-Length', 			
                     str(len(response_body)))]

                # 웹 브라우저에 응답을 시작
              	start_response(status, response_headers)

                # WSGI 함수의 일이 모두 끝남
              	return [response_body]

          	return make_response(application)
        ```

        - WSGI는 함수로 선언하여 사용하는 것이 일반적이지만 클래스로 정의하여 사용하는 경우도 있다.
        - WSGI 함수를 사용하여 응답하면, 프로그래머가 보다 정교하게 HTTP 응답을 제어할 수 있어서 고급 응용 프로그램에서는 자주 이용되는 기법 중 하나이다. 하지만 대부분의 경우 앞서 설명된 방법을 이용한다.

      - 코드 2-9 튜플 사용

        ```python
        from flask import make_response

        @app.route('/')
        def response_test():
            return make_response(('Tuple Custom Response', 
                                  'OK', {
              'response_method': 'Tuple Response'
            }))
        ```

        - 튜플로 구성된 객체는 응답 객체를 첫번째 인자로 주고, 두번째 인자는 HTTP 상태 코드 값(예:200) 또는 상태 코드 문자열(예: OK)을, 마지막으로 응답 헤더를 사전({}) 타입으로 해서 세 번째 인자로 제공한다.
        - 튜플로 전달하는 것은 응답 상태 코드나 헤더의 내용을 조정하기 편리하나 제어하는 것이 매우 까다롭다.

  - HTTP 요청 전후에 대한 핸들러 관리

    - 웹 프로그램은 HTTP 요청을 받아 응답 결과를 반환하는 것이 주 임무이다. 종종 HTTP 요청을 실행하기 이전에 어떤 추가 작업을 실행하고자 한다면, 뷰 함수 안에 추가적으로 실행해야 할 로직을 기술하는 것이 일반적일 것이다. 그러나 이와 같은 처리가 한 개의 뷰 함수에 해당하지 않고 여러 개에서 수십, 수백 개에 이른다면 사용하기 어렵다. 자바는 이런 상황을 AOP를 사용해 해결하지만 Flask는 HTTP 요청 전후에 사용할 수 있는 데코레이터를 제공한다.

    - 코드 2-10 HTTP 요청 전후에 호출되는 데코레이터

      ```python
      from flask import Flask
      app = Flask(__name__) 

      @app.route("/") 
      def http_prepost_request():
          return "/"

      @app.before_first_request
      def before_first_request():
          print("앱이 기동되고 나서 첫 번째 HTTP 요청에만 응답")

      @app.before_request
      def before_request():
          print("매 HTTP 요청이 처리되기 전에 실행")

      @app.after_request
      def after_request():
          print("매 HTTP 요청이 처리되고 나서 브라우저에 응답하기 전 실행")

      @app.teardown_request
      def teardown_request():
          print("HTTP 요청의 결과가 브라우저에 응답한 다음 실행")

      @app.teardown_appcontext
      def teardown_appcontext():
          print("HTTP 요청의 애플리케이션 컨텍스트가 종료될 때 실행")

      if __name__ == "__main__":
          app.run(host="0.0.0.0")
      ```

    - before_first_request, before_request 데코레이터를 사용한 함수는 Flask 인스턴스 객체 내에서 before_first_request_funcs, before_request_funcs 리스트 타입 변수에 요소로 추가되어 저장된다.

    - teardown_request 데코레이터를 사용한 함수는 개별 HTTP 요청이 끝난 다음 반드시 실행되어야 하는 로직을 포함해야 한다.

    - teardown_appcontext 데코레이터를 사용한 함수는 Flask 인스턴스 객체 내에서 teardown_appcontext_funcs 리스트 타입 변수에 요소로 추가된다.

  - 사용자 정의 URL 처리 함수 관리

    - 코드 2-11 URL의 일부로 다뤄지는 인자 값을 객체로 변환하기

      ```python
      # 컨버터 클래스 선언을 위한 모듈 가져오기
      from werkzeug.routing import BaseConverter
      from models import Board
      from database import db_session
      from flask import Flask, url_for

      # 컨버터 클래스 선언 시작
      class BoardView(BaseConverter):
          #URL의 일부로 넘어온 인자값은 to_python의 value로 전달
          def to_python(self, value):
              # 전달된 인자를 DB에 질의해서 첫 번째로 검색된 레코드를 가져와 뷰 함수에 인자로 전될한다.
              record = db_session.query(Board).
              			filter(Board.id == value).first()
              return record
          # to_url 함수를 호출할 경우, 파라미터의 값을 웹 브라우저가 표현할 수 있는 형태로 재구성해서 재구성된 파라미터 값을 반환
          def to_url(self, record):
              return record.id
          
      app = Flask(__name__)
      # 생성한 URL 컨버터를 board 이름으로 참조할 수 있도록 클래스를 저장
      app.url_map.converters['board'] = BoardView

      # 웹 브라우저가 접근하는 URL 매핑을 route 데코레이터를 이용해 선언
      # : 앞은 URL 컨버터명, 뒤는 뷰 함수에 전달할 변수명을 정의한다
      @app.route("/board/<board:record>", endpoint="view")
      # 뷰 함수를 선언한다. URL이 호출되면 실행되는데, BoardView 의 to_url 메서드에 의해 임의의 파이썬 객체를 반환하면 해당 객체를 뷰 함수에 인자로 전달한다. 이때 뷰 함수에 전달되는 인자의 이름은 윗줄에서 정의한 이름(콜론으로 나뉜 뒷부분)이 사용되어야 한다.
      def board_view_route(record):
          # url_for 함수의 첫번째 인자로 접근할 뷰 함수의 endpoint 이름을 지정하고, 두 번째 인자부터 접근할 뷰 함수에 가변 인자를 키워드 인자로 전달한다.
          return url_for("view", record=record)

      if __name__ == "__main__":
          app.run(host="0.0.0.0")
      ```

      - 게시판에서 35번째 게시물을 가져와서 보여달라는 명령을 수행하는 코드

  - 미들웨어 등록을 위한 순수 WSGI 객체 접근

    - 웹 버서와 웹 프로그램 간의 통신 과정은, 웹 브라우저가 웹 서버에 요청하면 웹 서버가 요청에 따른 적절한 응답을 생성해 웹 브라우저에 응답을 반환하고 통신을 끊는다. 이런 HTTP 통신 과정에서의 요청과 응답으로 구성된 하나의 처리는 하나의 독립된 응용 애플리케이션으로 볼 수 있다. 파이썬의 웹 서버 인터페이스 규격인 WSGI에서는 이런 일들을 수행하는 계층을 미들웨어라고 부른다.

    - 미들웨어는 여러개를 추가할 수 있다. 그리고 추가한 순서에 따라 순차적으로 적용되며, 미들웨어는 미들웨어 스택으로 관리된다.

    - 미들웨어는 HTTP 통신 과정에서 다양한 일을 처리할 수 있다.

      - 타킷 URL에 따른 애플리케이션 기동에 필요한 HTTP 환경 재설정과 Request Path 재설정
      - 다수의 애플리케이션 또는 다른 프레임워크의 프로그램을 같은 프로세스에서 동작시키기
      - 네트워크의 대역폭 분산 처리를 위해 로드 밸런싱과 원격 처리
      - 콘텐츠의 전처리

    - 뒤에서 다룰 5.4절 'HTTP 메서드 덮어쓰기'는 미들웨어를 등록하여 사용한 예제 중하나이다.

    - 환경 변수의 일부 값을 참조하여 로그 기록을 남기는 예제

      ```python
      # 미들웨어 클래스 선언 시작, 관례적으로 이름에 Middleware를 붙임
      # 파이썬의 모든 클래스는 상속 클래스를 명시적으로 지정하지 않는 경우는 object클래스를 상속받게 된다. 이곳에선 object 클래스를 상속받음을 명시했다.
      class LogMiddleware(object):
          """WSGI middleware for collecting site usage"""
          
          # 생성자
          def __init__(self, app):
              self.app = app
          
          # 미들웨어 클래스에 호출 메서드의 선언을 시작. 호출메서드는 인스턴스화된 객체를 함수처럼 사용하기 위해 정의하는 클래스 특별 메서드이다. 호출 메서드 이름은 반드시 __call__을 사용해야 하며 이 메서드는 두개의 인자를 받는다. 인자이름은 관례적으로 아래와 같다.
          def __call__(self, environ, start_response):
              # PATH_INFO는 웹브라우저가 접근중인 URL 정보(스키마+호스트+포트+자원주소)를 모두 포함하고 있다.
              url = environ.get("PATH_INFO", "")
              
              #QUERY_STRING을 가져온다. QUERY_STRING은 URL 뒤에 ?로 시작하는 문자열들을 의미하며, 이 문자열은 키=값의 형태로 연관지어 &문자로 연결되어 있다.
              query = unqute_plus(environ.get("QUERY_STRING", ""))
              
              #LogRecord는 프로그래머가 전달한 로그 내용을 수정하는 데 사용
              item = logging.LogRecord(
                  name="Logging",
                  level=logging.INFO,
                  pathname=url,
                  lineno="",
                  msg=query,
                  args=None,
                  exc_info=None
              )
              
              #handle 메서드는 LogHandler가 하나의 로그 레코드를 어떻게 구성할지에 대한 정보이다.
              metrics_logger.handle(item)
              
              #실행될 미들웨어를 위해 wsgi 객체를 반환해야 한다. 반환할때는 반드시 environ 인자와 start_response를 인자로 전달한 값을 반환해야 한다
              return self.app(environ, start_response)
      ```

    - 코드 2-13 미들웨어 등록

      ```python
      app = Flask(__name__)
      app.wsgi_app = LogMiddleware(app.wsgi_app)
      ```

    - 미들웨어가 하는 일은 사실 앞에서 설명했던 before_request, after_request 데코레이터 역활과 같다. 다만, 미들웨어는 웹 서버와 엡 애플리케이션 사이에서 동작하는 것이 가장 큰 차이점이라고 볼 수 있다.

  - 디버그 모드 설정

    ```python
    app = Flask(__name__)
    app.debug = True

    app.config.update(
        DEBUG=True
    )
    ```

    - Flask 객체의 debug 속성값을 True로 넘겨주면 디버깅 기능이 활성화된다.

  - 뷰 함수 등록(2.2)

  - 로거 사용(2.5)

  - 데스트 서버 실행(2.6)

  - 템플릿 필터 등록(3.7)

  - HTTP 에러 핸들러 관리(4.4)

  - Blueprint 사용(5.1)

  - 테스트 클라이언트 생성(6.1)




## 2.2 라우팅

Flask에서 URL을 처리하는 방법을 다른말로 URL 디스패치라고 한다. URL 디스패치를 Flask가 담당하고 있으므로 우리도 웹 프로그램이 수행해야 할 내용을 Flask 애플리케이션에 등록해야한다. 

- 코드 2-15 Hello World! 출력 프로그램

  ```python
  from flask import Flask
  app = Flask(__name__)

  # 웹브라우저에서 웹사이트의 /를 호출하면 hello 함수가 실행되어야 한다고 알림
  @app.route('/')
  def hello_world():
      return 'Hello World!'

  if __name__ == '__main__':
      app.run()
  ```

- 코드 2-16 /board URL 에 대한 뷰 함수 정의

  ```python
  # route 데코레이터는 route 함수가 처리할 HTTP메서드 타입을 한 개 이상 지정할 수 있다. 우리는 이후 route 데코레이터가 추가된 함수를 뷰 함수로 부르기로 한다.
  @app.route('/')
  def board_list():
      board_list = models.board.query.all()
  ```

- HTTP 메서드 타입중 GET과 POST

- |      | GET                                      | POST                                     |
  | ---- | ---------------------------------------- | ---------------------------------------- |
  | 설명   | 자원의 위치(url)과 함께 쿼리 스트링을 함께 전달. 웹 브라우저의 주소 줄에 노출됨. | HTTP 메세지의 바디에 데이터를 포함해 전달하기 때문에 많은 양의 데이터를 전달할 수 있으며, 웹서버가 HTTPS를 운영 중이면 웹 브라우저가 보내는 모든 요청이 암호화됨. |
  | 차이점  | 중요한 정보의 전달과 함께 웹 프로그램의 데이터를 변경하는 목적으로는 사용하지 않음 | 중요한 정보의 전달과 함께 웹 프로그램의 데이터를 변경하는 목적으로 사용 |

- 코드 2-17 HTTP 메서드 타입에 따른 뷰 함수 분리

  ```python
  @app.route('/board', methods=['GET'])
  def board_list_get():
      pass

  @app.route('/board', methods=['POST'])
  def board_list_post():
      pass
  ```

  - URL에 다수의 HTTP 메서드를 동시에 처리할 수 있도록 route 데코레이터에 methods 인자 값을 조정하는 방법도 있다. 그러나 HTTP 규약에서는 **하나의 URL은 하나의 HTTP 메서드 타입을 처리해야 한다**고 설명되어 있다.

- 코드 2-18 하나의 뷰 함수가 여러 HTTP 메서드 타입을 처리하도록 작성한 코드

  ```python
  @app.route('/board', methods=['GET', 'POST'])
  def board_list():
      pass
  ```

  - 특정 함수가 뷰 함수로 기능하게 하기 위해서는 Flask 애플리케이션 객체의 route 데코레이터를 함수 위에 선언해줘야 하는데, route 데코레이터는 첫번째 인자로 처리할 URL 주소를 받는다. 데코레이터를 선언해줄 때 methods 인자가 없으면 뷰 함수는 GET 요청만을 처리하게 된다.

- 코드 19 뷰 함수에 별칭 지정하기

  - 뷰 함수의 별칭은 특별히 지정하지 않으면 뷰 함수의 이름이 암시적으로 사용되며, url_for 함수에서 뷰 함수를 식별하기 위한 이름으로 사용한다.

  - 종종 뷰 함수의 이름이 길거나 적절하지 않은 이름을 사용하고 있다면 별칭을 지정하는 편이 좋다. 별칭의 지정은 route 데코레이터 또는 add_url_rule 함수에 endpoint 인자로 전달하면 된다.

    ```python
    @app.route('/board', endpoint="board")
    def board():
        pass
    ```

Flask 애플리케이션에서 슬래시에 대한 URL 뷰 함수만 구현되어 있는 상황에서 /guestbook URL을 호출하게 되면, 웹 어플리케이션은 웹 브라우저에 404 상태 코드로 응답하게 된다.

/board URL을 POST 메서드로 호출하면 웹 애플리케이션은 이에 대한 뷰 함수를 찾는다. 뷰 함수를 찾게 되면 뷰 함수가 웹 브라우저에 바로 응답하게 되지만, 만약 GET 메서드만을 처리하는 뷰 함수만을 반결했을 때 Flask 는 405 Method Not Allowed 라는 메세지와 상태 코드를 브라우저에 응답하게 된다.

route 데코레이터를 이용해 처리 가능한 URL 에는 쿼리 스트링만 변하는 고정URL, 쿼리 스트링과 URL의 일부분이 바뀌는 동적URL이 있다. 게시판을 예로 들어 설명하면 다음과 같다.

1. /board
2. /board/1
3. /board/2

- 코드 2-20 동적으로 변경되는 URL의 뷰 함수 선언하기

  ```python
  @app.route('/board')
  def board():
      pass

  @app.route('/board/<article_idx>')
  def board_view(article_idx):
      pass
  ```

  - 사용자가 요청하는 URL에서 동적으로 바뀌는 부분은 URL에 포함된 변수로 취급할 수 있다.
  - 함수의 인자명은 route 데코레이터에 전달한 URL에서 변동되는 부분의 이름이 같아야 한다. URL의 일부분을 동적으로 받는 경우가 많으면 그 수만큼 URL 뷰 함수가 받게되는 인자가 늘어나게 된다.

- 코드 2-21 URL변수에 기본값 할당

  ```python
  @app.route('/board', defaults={'page':'index'})
  @app.route('/board/<page>')
  ```

  - defaults 인자로 page 변수에 index를 넣도록 지시한다. 그 결과, 웹 애플리케이션은 최종적으로 /board/index 형태의 주소를 호출하는 것과 같은 효과를 지니게 된다

- 코드 2-22 route 데코레이터를 사용해서 뷰 함수 등록하기

  ```python
  @app.route("/flask")
  def index():
      pass
  ```

  - route 데코레이터에 두번째 인자를 전달할 때 인자 이름을 포함해 전달하지 않으면, route 데코레이터는 자연적으로 두번째 인자를 endpoint 인자로 인식하게 된다.

- 코드 2-23 add_url_rule 메서드를 사용해 라우팅 지정

  ```python
  def index():
      pass

  app.add_url_rule("/", "index", index) 
  # 지정하지 않으면 순서대로 URL, 별칭, 뷰 함수 객체로 인식
  ```

  - route 데코레이터와 add_url_rule 메서드는 기능의 차이라기보다는 관리의 차이
  - add_url_rule 메서드는 뷰 함수를 미리 만들어놓고 라우팅 지정을 하려 할 때 사용

![스크린샷 2017-02-06 오후 8.57.29](/Users/seulgi/Desktop/스크린샷 2017-02-06 오후 8.57.29.png)

Flask는 애플리케이션 하나만 실행해놓고 여러 가상 호스트와 서브 도메인 등에 응답할 수 있는 구조를 가지고 있다. 따라서 뷰 함수의 기능을 적절하게 분배하면 유지보수하기 쉬운 구조로 만들 수 있다. 

- 코드 2-24 라우팅 옵션에 defaults 인자 지정하기

  ```python
  from flask import Flask

  app = Flask(__name__)

  @app.route("/board/<article_id>")
  @app.route('/board', defaults={'article_id':10})
  def board(article_id):
      return "{}번 게시물을 보고 계십니다.".format(article_id)

  if __name__ == "__main__":
      app.run()
  ```

  - 호출예시 url
    - http://localhost:5000/board
    - http://localhost:5000/board/20

- 코드 2-26 라우팅이 처리할 도메인을 하나만 지정한 코드

  ```python
  @app.route('/board', host="example.com")
  def board():
      return "/board URL을 호출하셨습니다"
  ```

- 코드 2-27 host 옵션을 두 줄에 나누어 쓰기

  ```python
  @app.route('/board', host="example.com")
  @app.route('/board', host="example2.com")
  def board():
      return "/board URL을 호출하셨습니다"
  ```

  - 만약 가상 호스트 5개가 하나의 Flask 애플리케이션을 가리키고 host 옵션이 지정되지 않으면, 뷰 함수는 모든 가상 호스트에 응답한다.

- 코드 2-28 subdomain 옵션을 지정하여 서브 도메인별로 라우팅 지정

  ```python
  app.config['SERVER_NAME'] = "example.com:5000"

  @app.route("/board", subdomain="test")
  def board_domain_test():
      return "test 도메인의 /board URL을 호출하셨습니다"

  @app.route("/board", subdomain="answer")
  def board_domain_answer():
      return "answer 도메인의 /board URL을 호출하셨습니다"
  ```

  - subdomain 옵션은 기본 도메인이 같으면서 서브 도메인이 있으면 어떤 서브 도메인에 응답할지 지정하는 데 사용된다.

- 코드 2-29 특정 뷰 함수가 다수의 서브 도메인에 응답하도록 하기

  ```python
  app.config['SERVER_NAME'] = "example.com:5000"

  @app.route("/board", subdomain="test")
  @app.route("/board", subdomain="answer")
  def board_domain_testandanswer():
      return "test, answer 도메인의 /board URL을 호출하셨습니다."
  ```

- 코드 2-30 모든 서브 도메인에 응답하는 뷰 함수 정의

  ```python
  app.config['SERVER_NAME'] = "example.com:5000"

  @app.route("/board", subdomain="<user_domain>")
  def board_domain_testandanswer(user_domain):
      return "{} 도메인의 /board URL을 호출하셨습니다.".format(user_domain)
  ```

- 코드 2-31 redirect_to 옵션을 라우팅에 사용하여 원래의 뷰 함수에게 처리를 맡기지 않고  다른 URL로 처리 넘기기

  ```python
  @app.route("/board", redirect_to="/new_board")
  def board():
      return "/board URL을 호출하였지만 실행이 안 될겁니다"

  @app.route("/new_board")
  def new_board():
      return "/new_board URL이 호출되었습니다"
  ```

- 코드 2-32 redirect_to 옵션에 함수를 전달하여 사용하기

  ```python
  # 함수 전달을 위해 미리 선언되어 있어야 한다. adapter는 필수 인자
  def redirect_new_board(adapter, id, id2):
      return "/new_board/{0}/{1}".format(id,id2)

  @app.route("/board/<id>/<id2>", redirect_to=redirect_new_board)
  def board(id, id2):
      return "호출이 안 될겁니다"

  @app.route("/new_board/<id>/<id2>")
  def new_board(id, id2):
      return "{0}, {1} 변수와 함께 new_board URL이 호출되었습니다.".format(id, id2)
  ```

  - redirect_to 옵션을 사용하여 라우팅을 지정할 때의 좋은 점은 웹사이트가 개편되었을 때 이전 방문자의 링크를 안정적으로 유지할 수 있으며, 또 다른 뷰 함수와 before_request 데코레이터 등을 사용하지 않아도 구현할 수 있다는 것이다.
  - alias 옵션은 endpoint 옵션의 다른 옵션명으로 동작하는데, 일반적으로 alias 옵션을 따로 지정하지 않고 endpoint 속성으로 사용한다.




## 2.3 요청과 응답 다루기

HTTP 메세지는 요청과 응답으로 나누어진다. 요청과 응답은 웹 브라우저와 웹 서버간에 이뤄지는 것이 일반적이지만 종종 웹 서버들끼리 이뤄지기도 한다.

Flask 에서는 이를 처리하기 위해 Request 객체와 Response 객체를 제공한다. HTTP 요청은 flask 모듈에서 proxy화된 request 클래스를 가져와서 사용하는 것이 일반적이다.

- 코드 2-33 GET 방식에서 넘어온 쿼리 스트링에서 question 변숫값 가져오기

  ```python
  from flask import Flask, request

  @app.route("/board")
  def board_list():
      return "쿼리 스트링 question 변숫의 값 {}입니다.".format(request.args.get('question'))
  ```

  - 호출예시 url
    - http://localhost:5000/board?question=answer

- 코드 2-34 GET 방식의 쿼리 스트링에 접근하기

  ```python
  from flask import request

  @app.route("/board")
  def board():
      # 가져올 쿼리 변수명, 두번째 세번째 인자는 생략가능
      # 세번째 옵션으로 type 인자를 제공 (데이터타입 변환을 위하여)
      article_id = request.args.get("article", "1", int)
      return str(article_id)
  ```

- 코드 2-35 from 속성을 통해 데이터 읽어오기

  ```python
  from flask import request

  # 라우팅 옵션 추가
  @app.route("/board", methods=["POST"])
  def board():
      article_id = request.args.get("article", "1", int)
      return str(article_id)
  ```

- 코드 2-36 values 속성에서 데이터 읽어오기

  ```python
  from flask import request

  @app.route("/board", methods=["GET","POST"])
  def board():
      # value 속성은 GET의 쿼리 스트링 데이터를 우선시하게 된다.
      # 웹 브라우저로부터 특정 변수가 넘어오지 않았을 때 반환할 기본값을 정한다.
      return request.value.get("question", "질문을 입력하세요")
  ```

- 코드 2-38 get 메서드에 type 인자를 사용해서 미리 특정 객체로 변환해서 반환받기

  ```python
  from flask import request

  @app.route("/board", methods=["GET","POST"])
  def board():
      # answer라는 변숫값을 얻어올 때 int 객체로 반환하라는 의미
      return request.value.get("answer", 1, type=int)
  ```

- 코드 2-39 Y-m-d 타입으로 넘어온 데이터를 datetime 형태로 반환하는 사용자 데이터 타입(함수형)

  ```python
  from flask import Flask, request
  from datetime import datetime

  def dateKoreanType(date_format):
      def translate(date_str):
          return datetime.strptime(date_str, date_format)
      return translate

  @app.route("/board", methods=["GET","POST"])
  def board():
      print(request.value.get("date", "2015-02-09", type=dateKoreanType("%Y-%m-%d")))
      return "날짜는 콘솔을 확인해보세요"
  ```

- 코드 2-40 Y-m-d 타입으로 넘어온 데이터를 datetime 형태로 반환하는 사용자 데이터 타입(클래스형)

  ```python
  from flask import Flask, request
  from datetime import datetime

  class dateKoreanType:
      def __init__(self, format):
          self.format = format
      
      # self 인자 외에 가변 인자, 키워드 가변 인자를 인자로 선언해야 한다. Flask가 변환하라고 전달하는 날짜는 가변 인자의 첫 번째 값으로 전달받는다.
      def __call__(self, *args, **kwargs):
          return datetime.strptime(args[0], self.format)

  @app.route("/board", methods=["GET","POST"])
  def board():
      print(request.value.get("date", "2015-02-09", type=dateKoreanType("%Y-%m-%d")))
      return "날짜는 콘솔을 확인해보세요"
  ```

- 코드 2-41 getlist 메서드를 사용해서 같은 이름을 가진 데이터를 리스트 타입으로 가져오기

  ```python
  	print(request.value.getlist("date", "2015-02-09", type=dateKoreanType("%Y-%m-%d")))
  ```

  - 코드 2-40 에서 get 메서드 대신 getlist 메서드를 사용해 같은 이름을 가진  변숫값들을 리스트로 돌려받는 예제이다.
  - get 메서드와 달리 getlist 메서드는 defaults 인자를 받지 않는데, 그 이유는 변숫값이 넘어오지 않는 경우 기본값으로 빈 리스트를 반환하기 때문이다.



- 코드 2-42 MultiDict 데이터 타입 다루기

  ```python
  from werkzeug.datastructures import MultiDict

  post = MultiDict()
  # add 메서드는 MultiDict에 키와 값을 추가하는 메서드이다. 일반적으로 사용되는 메서드는 아니지만, 웹 브라우저가 보내온 데이터를 기준으로 MultiDict에 키와 값을 추가할 수 있다.
  post.add("question", "answer")
  # 설정하고자 하는 변수값이 없을때만 default 값으로 데이터를 추가한다
  post.setdefault("question", "answer2")
  post.setdefault("lorem", "ham")

  post2 = MultiDict()
  post2.setlist("question", ["answer1","answer2"])
  # 같은 이름으로 여러 변수를 설정하고자 하는 경우 사용한다
  post2.setlistdefault("question", ["ham","ham2"])
  #모든 변수 제거
  post2.clear()

  post_copy = post.copy() #post_copy 변경시 post 변경
  post_deepcopy = post.deepcopy() #post_deepcopy 변경시 영향없음

  question_value = post.pop("question")
  if 'question' not in post:
    print('post 변수에 더 이상 question 변수 키가 없습니다')

  question_values = post2.poplist("question")
  if 'question' not in post2:
    print('post 변수에 더 이상 question 변수 키가 없습니다')

  #데이터 병합. get에 있는 내용이 지워지진 않는다.
  get = MultiDict()
  get.add("lorem", "issue")
  post.update(get)

  ```


 

- 코드 2-51 쿠키에 들어 있는 값 보기 (2.4절에서 자세히 다룸)

```python
from flask import Flask, request, redirect, make_response

app = Flask(__name__) 

@app.route("/example/cookie") 
def example_cookie():
    print(request.cookies)
    return ""

@app.route("/example/cookie_set") 
def example_cookie_set():
    redirect_to_cookie = redirect("/example/cookie")
    response = make_response(redirect_to_cookie)
    response.set_cookie('Cookie Register', value='Example Cookie')
    return response

app.run()
```



![그림8](/Users/seulgi/Desktop/그림8.png)



## 2.4 쿠키와 세션 다루기

쿠키와 세션 모두 웹사이트 사용자인 브라우저를 식별하기 위한 방법이지만, 동작에 있어서는 약간 다른 방법을 취한다. 쿠키는 웹 프로그램이 클라이언트를 식별할 때 브라우저의 데이터를 읽는 방법이고, 세션은 브라우저를 식별할 때 서버에서 데이터를 읽어들인다.

저장할 수 있는 데이터 용량에도 차이가 있는데, 쿠키는 RFC 2109 기준으로 4096 bytes 를 담을 수 있고, 세션은 서버 측에 데이터를 저장할 수 있으므로 저장할 수 있는 데이터의 길이 제한이 존재하지 않는다.

- 코드 2-67 쿠키 설정하기

  ```python
  #-*- coding: utf-8 -*-
  from flask import Flask, Response

  app = Flask(__name__)

  @app.route("/cookie_set")
  def cookie_set():
      custom_resp = Response("Cookie를 설정합니다")
      custom_resp.set_cookie("ID", "JPUB Flask programming")
      
      return custom_resp

  app.run()
  ```

  - http://localhost:5000/cookie_set
  - ![스크린샷 2017-02-12 오후 4.33.32](/Users/seulgi/Desktop/스크린샷 2017-02-12 오후 4.33.32.png)

![스크린샷 2017-02-12 오후 4.31.27](/Users/seulgi/Desktop/스크린샷 2017-02-12 오후 4.31.27.png)

쿠키는 종종쿠키 유지 시간을 설정하거나 특정 경로 아래에서만 유효하도록 하는 등의 설정이 필요하기도 한다. 이런 설정은 set_cookie 메서드를 호출할 때 표 2-10 에 있는 인자를 제공하여 설정할 수 있다. set_cookie 메서드는 프로그래머가 쉽게 사용할 수 있도록 key 인자를 제외하고 모든 인자를 선택적으로 제공한다.

![스크린샷 2017-02-12 오후 4.36.48](/Users/seulgi/Desktop/스크린샷 2017-02-12 오후 4.36.48.png)

- 코드 2-68 쿠키 설정/확인/종료

  ```python
  # -*- coding: utf-8 -*-
  from flask import Flask, request, Response

  app = Flask(__name__)

  @app.route("/cookie_set")
  def cookie_set():
      custom_resp = Response("Cookie를 설정합니다")
      custom_resp.set_cookie("ID", "JPUB Flask programming")

      return custom_resp

  @app.route("/cookie_out")
  def cookie_out():
      custom_resp = Response("Cookie를 종료합니다")
      custom_resp.set_cookie("ID", expires=0)

      return custom_resp

  @app.route("/cookie_status")
  def cookie_status():
      return "ID 쿠키는 %s 값을 가지고 있습니다" % request.cookies.get('ID', '빈 문자열')

  app.run()
  ```

- 코드 2-69 flask에서 session 사용하기

  ```python
  # -*- coding: utf-8 -*-
  from flask import Flask, request, session

  app = Flask(__name__)
  app.secret_key = 'F12Zr47j\3yX R~X@H!jmM]Lwf/,?KT'

  @app.route("/session_set")
  def session_set():
      session['ID'] = "JPUB Flask Session Setting"
      return "세션이 설정되었습니다"


  @app.route("/session_out")
  def session_out():
      del session['ID']
      return "세션이 제거되었습니다"

  app.run()
  ```

![스크린샷 2017-02-12 오후 5.05.43](/Users/seulgi/Desktop/스크린샷 2017-02-12 오후 5.05.43.png)

- 코드 2-70 Flask 애플리케이션 기동 시 세션과 관련한 환경 변수 설정

  ```python
  from flask import Flask
  from datetime import timedelta

  app = Flask(__name__)

  app.config.update(
      SECRET_KEY= 'F12Zr47j\3yX R~X@H!jmM]Lwf/,?KT',
      SESSION_COOKIE_NAME = 'jpub_flask_session',
      PERMANENT_SESSION_LIFETIME = timedelta(31)
  )
  ```

Flask 에서 HTTP 세션 데이터는 상요자 정의 세션 인터페이스를 이용해서 파일 시스템, 데이터베이스 등에 저장하고 읽을 수 있다. Flask에서 모든 세션 인터페이스는 SessionInterface 클래스를 상속받는다.

우리는 HTTP 세션 데이터를 DB(SQLAlchemy, SQLite, pymongo) 와 Redis, Beaker 라이브러리로 관리하는 사용자 정의 세션 인터페이스의 구현 중 SQLite에 대해서만 사용 방법을 알아본다.



### 2.4.2 SQLite에 기반한 사용자 정의 세션 인터페이스

```python
from flask import Flask, session
# os 모듈은 세션 ID 별 SQLite 파일을 만들고 세션 ID별 SQLite 파일을 삭제하기 위해서 사용한다. errno 모듈은 세션 디렉터리 삭제 과정해서 발생하는 오류를 처리하는 데 사용된다. sqlite3 모듈은 SQLite 데이터베이스에 접속할 때 사용된다.
import os, errno, sqlite3
from uuid import uuid4
from pickle import dumps, loads
# MutableMapping 클래스를 상속받은 클래스는 몇 개의 특별한 메서드를 재정의해야한다. 이 클래스는 세션 데이터 객체 클래스를 선언할 때 사용한다.
from collections import MutableMapping
from flask.sessions import SessionInterface, SessionMixin


class SqliteSession(MutableMapping, SessionMixin):
    # SQLite에 접근하는 SQL 문을 언제든지 불러쓸 수 있도록 객체 속성으로 저장해둔다.
    _create_sql = (
        'CREATE TABLE IF NOT EXISTS session'
        '('
        ' key TEXT PRIMARY KEY,'
        ' val  BLOB'
        ')'
    )
    _get_sql = 'SELECT val FROM session WHERE key = ?'
    _set_sql = 'REPLACE INTO session (key, val) VALUES (?,?)'
    _del_sql = 'DELETE FROM session WHERE key = ?'
    _ite_sql = 'SELECT key FROM session'
    _len_sql = 'SELECT COUNT(*) FROM session'

    # 세션 디렉터리 경로와 세션 ID를 받아 세션별 SQLite 디렉터리를 만듭니다. 세션별 SQLite 디렉터리가 있는 경우 객체 속성만 수정합니다.
    def __init__(self, directory, sid, *args, **kwargs):
        self.path = os.path.join(directory, sid)
        self.directory = directory
        self.sid = sid
        self.modified = False
        self.conn = None
        if not os.path.exists(self.path):
            with self._get_conn() as conn:
                conn.execute(self._create_sql)
                self.new = True

    # 이 메서드는 시퀀스 타입의 변수에 슬라이싱([]) 방법으로 접근할 때 호출되며,          SQLite 데이터베이스에 키 이름으로 질의해 데이터를 가지고 오면 이를 파이썬 객체로 반환한다.
    def __getitem__(self, key):
        key = dumps(key, 0)
        rv = None
        with self._get_conn() as conn:
            for row in conn.execute(self._get_sql, (key,)):
                rv = loads(row[0])
                break
        if rv is None:
            raise KeyError('Key not in this session')
        return rv

    # 세션에 데이터를 저장할 때 호출되며, 키 이름과 저장할 데이터를 보내어 저장한다.
    def __setitem__(self, key, value):
        key = dumps(key, 0)
        value = dumps(value, 2)
        with self._get_conn() as conn:
            conn.execute(self._set_sql, (key, value))
        self.modified = True

    # 세션에 저장된 키를 제거할 때 호출된다
    def __delitem__(self, key):
        key = dumps(key, 0)
        with self._get_conn() as conn:
            conn.execute(self._del_sql, (key,))
        self.modified = True

    # 세션에 저장된 키 목록을 반환할 때 호출된다
    def __iter__(self):
        with self._get_conn() as conn:
            for row in conn.execute(self._ite_sql):
                yield loads(row[0])

    # 세션에 저장한 키 개수를 알려고 할 때 호출된다            
    def __len__(self):
        with self._get_conn() as conn:
            for row in conn.execute(self._len_sql):
                return row[0]

    # 세션별 SQLite 연결 객체를 반환한다. 연결 객체가 없을 때 먼저 연결 객체를 생성 후 반환 한다.        
    def _get_conn(self):
        if not self.conn:
            self.conn = sqlite3.Connection(self.path)
        return self.conn

    # 세션 데이터를 메서드 체인징 방식으로 이용하고자 할 때 사용하게 되는 프록시 클래스를 정의한 것이다. 웹 애플리케이션에서 SqliteSession의 setdefault 메서드를 사용하지 않으면 정의하지 않아도 됩니다.
    class CallableAttributeProxy(object):
        def __init__(self, session, key, obj, attr):
            self.session = session
            self.key = key
            self.obj = obj
            self.attr = attr

        def __call__(self, *args, **kwargs):
            rv = self.attr(*args, **kwargs)
            self.session[self.key] = self.obj
            return rv

    class PersistedObjectProxy(object):
        def __init__(self, session, key, obj):
            self.session = session
            self.key = key
            self.obj = obj

        def __getattr__(self, name):
            attr = getattr(self.obj, name)
            if callable(attr):
                return SqliteSession.CallableAttributeProxy(
                    self.session, self.key, self.obj, attr
                )
            return attr

    def setdefault(self, key, value):
        if key not in self:
            self[key] = value
            self.modified = True
        return SqliteSession.PersistedObjectProxy(
            self, key, self[key]
        )


class SqliteSessionInterface(SessionInterface):
    # 세션별 SQLite 데이터가 저장될 디렉터리를 객체 속성으로 저장한다. 인자로 받은 디렉터리가 없으면 디렉터리부터 생성한다.
    def __init__(self, directory):
        directory = os.path.abspath(directory)
        if not os.path.exists(directory):
            os.mkdir(directory)
        self.directory = directory

    # 세션 ID를 쿠키로부터 가져와서 세션ID를 세션 데이터 객체 초기화 인자로 전달하고 세션 데이터 객체를 반환한다. 쿠키로부터 가져온 세션 ID가 없으면 세션ID를 먼저 생성한다. 세션ID는 uuid4를 이용한다.
    def open_session(self, app, request):
        sid = request.cookies.get(app.session_cookie_name)
        if not sid:
            sid = str(uuid4())
        rv = SqliteSession(self.directory, sid)
        return rv

    # 세션 데이터 객체에 저장된 데이터가 없으면 세션 SQLite 파일을 삭제합니다. 그 이후 세션 데이터 수정 플래그에 따라 세션 쿠키를 삭제하고 브라우저에 세션 쿠키를 설정합니다.
    def save_session(self, app, session, response):
        domain = self.get_cookie_domain(app)
        if not session:
            try:
                os.unlink(session.path)
            except OSError as e:
                if e.errno != errno.ENOENT:
                    raise
            if session.modified:
                response.delete_cookie(app.session_cookie_name, domain=domain)
            return

        httponly = self.get_cookie_httponly(app)
        secure = self.get_cookie_secure(app)
        expires = self.get_expiration_time(app, session)

        response.set_cookie(app.session_cookie_name, session.sid,
                            expires=expires, httponly=httponly,
                            domain=domain, secure=secure)


app = Flask(__name__)
# 세션별 SQLite 파일이 저장될 디렉터리 이름을 세션 인터페이스 생성자에 전달합니다.
path = '/tmp/app_session'
if not os.path.exists(path):
    os.mkdir(path)
    # 시스템 권한 설정
    os.chmod(path, int('700', 8))
app.session_interface = SqliteSessionInterface(path)
app.config.update(
    SECRET_KEY='F12Zr47j\3yX R~X@H!jmM]Lwf/,?KT',
    SESSION_COOKIE_NAME='jpub_flask_session'
)


@app.route("/session_in")
def session_signin():
    session['test'] = "abc"

    return "Session Signin"


@app.route("/session_out")
def session_signout():
    session.clear()
    return "Session Signout"


@app.route("/session_stat")
def session_stat():
    print(session.get("test", "Empty Data"))
    return "Session Stat Print to Console"


app.run()
```



## 2.5 에러와 로깅

- 프로그램에 발생할 수 있는 상황
  - 데이터를 보내던 클라이언트의 연결이 끊어져도 웹 프로그램이 클라이언트의 데이터 전송을 기다리면서 아무 일도 하지 않는 상황
  - 데이터베이스 서버에 부하가 걸려서 추가 질의를 수행하지 못하는 상황
  - 파일 시스템에 남은 디스크 용량이 없어서 발생하는 상황
  - 하드디스크 드라이브 깨짐 현상
  - 백엔드 서버에 부하가 걸려 클라이언트의 요청을 처리하지 못하는 상황
  - 프로그래밍 에러 또는 라이브러리에서 발생하는 오류
  - 네트워크 연결이 실패해서 프로그램이 응답하지 못하는 상황

파이썬은 로깅을 위해 logging 모듈을 기본으로 제공한다.

핸들러는 로거(로그를 기록하는 객체)가 특정 저장소(파일,DB, 메일 등)에 로그를 기록하도록 도와주는 객체인데 파이썬 로깅 모듈에서 기본으로 지원되지 않는 저장소에 로그를 기록할 때는 프로그래머가 핸들러를 따로 개발해서 사용할 수 있다.

- 코드 2-82 Flask에서 로깅하는 예제

  ```python
  app.logger.debug('A value for debugging')
  app.logger.warning('A warnig occurred (%d apples)', 42)
  app.logger.error('An error occurred')
  ```

![스크린샷 2017-02-13 오후 7.47.45](/Users/seulgi/Desktop/스크린샷 2017-02-13 오후 7.47.45.png)

![스크린샷 2017-02-13 오후 7.49.05](/Users/seulgi/Desktop/스크린샷 2017-02-13 오후 7.49.05.png)

- 코드 2-84 Flask 에서 완전히 동작하는 로깅 코드

  ```python
  # -*- coding: utf-8 -*-
  from flask import Flask
  import logging

  app = Flask(__name__)
  app.config.update(DEBUG=True)
  #출력할 로그의 기본 형태 변경
  #app.debug_log_format = "%(levelname)s in %(module)s [%(lineno)d]: %(message)s"

  @app.route("/log")
  def logger():
      app.logger.debug('debug 메세지를 출력합니다')
      return "콘솔을 확인하여 주시기 바랍니다"

  app.run()
  ```

  - 기본 로그 메세지 형태

![스크린샷 2017-02-13 오후 7.53.40](/Users/seulgi/Desktop/스크린샷 2017-02-13 오후 7.53.40.png)

- 코드 2-86 flask 인스턴스의 로거에 파일 핸들러 추가하기

  ```python
  # -*- coding: utf-8 -*-
  from flask import Flask
  import logging

  app = Flask(__name__)
  app.config.update(DEBUG=True)

  # 로그 메세지 출력 형태를 담당하는 객체 생성
  file_log_format = logging.Formatter('%(levelname)-8s %(message)s')

  # 로그 핸들러 객체 생성
  file_logger = logging.FileHandler("flask_instance.log")
  # 로그 핸들러가 사용할 로그 메세지 출력 포맷 객체 지정
  file_logger.setFormatter(file_log_format)

  # 로그에 생성한 로그 핸들러 객체 추가
  app.logger.addHandler(file_logger)

  @app.route("/log")
  def logger():
      app.logger.debug('debug 메세지를 출력합니다')
      return "콘솔을 확인하여 주시기 바랍니다"

  app.run()
  ```



- 코드 2-88 SMTP 로그 핸들러 (유형만)

```python
ADMINS = ['selvia2442@naver.com']

if app.debug:
    from logging.handlers import SMTPHandler
    mail_handler = SMTPHandler('127.0.0.1',
                               'lsk2442@hanmail.net',
                               ADMINS, 'your app failed')
    app.logger.addHandler(mail_handler)
```

- 코드 2-89 SMTP 핸들러에 사용자 인증 추가하기 (유형만)

```python
handler = logging.handlers.SMTPHandler(
        ('lsk2442@hanmail.net', 587),
        'selvia2442@naver.com', ['receipt@host'], 'Mail Host',
        ('your_account_name', 'your_account_password'), [])
```



- 코드 2-90 파일 핸들러 작성하기 (유형만)

  ```python
  import logging
  handler = logging.FileHandler('flask_instance.log', mode='a', encoding='utf-8', delay=False)
  ```

- 코드 2-91 순환되는 로그 핸들러 작성 (유형만)

  ```python
  import logging.handler
  handler = logging.handler.RotatingFileHandler(filename, mode='a', maxBytes=10485760, backupCount=5, encoding='utf-8', delay=False)
  ```

   

## 2.6 로컬 서버 실행하기

- 모듈 단위로 구성된 웹 프로그램에서 로컬 서버 실행

  ```python
  from jpub import app

  if __name__ == "__main__":
      app.run()
  ```



![스크린샷 2017-02-13 오후 8.51.09](/Users/seulgi/Desktop/스크린샷 2017-02-13 오후 8.51.09.png)

![스크린샷 2017-02-13 오후 8.51.26](/Users/seulgi/Desktop/스크린샷 2017-02-13 오후 8.51.26.png)

