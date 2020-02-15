# HTTP

## request와 Response
HTTP는 request와 response를 나타낸다.
JavaScript HTML 등의 컨테츠를 서버와 클라이언트가 주고받기 위해서는 공통된 약속의 메시지가 필요하다.
바로 그 메세지를 HTTP 라고 하고 HTTP는 request와 response라는 메세지로 구분되어 있다.

실제로 HTTP는 추상적이다 하지만 익숙해지자.

실제로 크롬의 network 창을 보면 현재 브라우저가 서버와 무엇을 주고받고 있는지 눈으로 확인할 수 있다. 예를 들어 이미지 파일 src tag를 보면 실제적으로는 클라이언트가 서버에 img 파일을 요청하는 의미이다.

### Request Headers
GET /index.html HTTP/1.1<br>
<strong>
  request line : 우리가 웹서버에게 요청하는 정보가 무엇인가, 
  HTTP/1.1 :
  웹 브라우저가 현재 사용할 수 있는 HTTP의 버전
</strong>  
<strong>request headers</strong>
Upgrade-Insecure-Requests: 1

User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.130 Safari/537.36
Sec-Fetch-User: ?1

<strong>User-Agent는 Web Browser의 다른 의미이다. User-Agent를 통해서 통계 같은 것을 낼 수 있따. 어떤 운영체제인가 어떤 Web Broswer인가, 또한 이 정보를 바탕으로 로봇임을 감지해서 차단할수도 있다.</strong>
Referer: http://localhost:8080/badboy.html



우리의 web browser가 web server에게 보내주는 것이다.
말 그대로 view source를 하면 볼수 있는 위와같은 예시를 web browser가 webserver한테
보내주는 것이다.

### Response Headers 예시
HTTP/1.1 200 OK<br>
-> version, status code(응답 결과), 응답 결과에 대한 사람의 언어(http responses code.이 중 200번대이면 성공했다는 뜻이다.<br>
-> 403 forbidden, 404 not found, 300번대 redirection 등이 있다.
Date: Sat, 15 Feb 2020 03:52:55 GMT
Server: Apache
X-Frame-Options: SAMEORIGIN
Last-Modified: Fri, 14 Feb 2020 12:19:09 GMT    //이 정보는 언제 마지막으로 수정됐따.
ETag: "45d-59e883666c940-gzip"
Accept-Ranges: bytes
Vary: Accept-Encoding
Content-Encoding: gzip  // 컨텐츠를 gzip이라는 타입으로 압축해서 보냈으니 이를 기반으로 압축을 풀어라.
Content-Length: 470     //길이
Content-Type: text/html // 어떤 타입인지를 확인해서 web browser는 이를 토대로 파일을 읽어온다.

Web browser는 Web server에 필요한 정보를 대신 요청해주는 기계, Web Server는 WEb browser가 요청한 정보를 적절하게 응답해주는 기계라고 할 수 있다.

<strong>
쉽게 생각하면 웹 브라우저는 사용자가 요청한 필요한 웹 서버의 데이터를 HTTP의 형식의 소스코드로 정리해서 웹 서버에게 request하게 된다. 웹 서버는 이러한 HTTP 형식의 문서를 response하게되고 reponse한 데이터를 기반으로 필요한 데이터의 헤더를 생성해서 필요한 데이터와 함께 담아서 web browser에거 response 해주게 된다. response 받은 데이터를 웹 브라우저는 읽고 결과적으로 화면에 나타나게 되는 것이다.
</strong>
