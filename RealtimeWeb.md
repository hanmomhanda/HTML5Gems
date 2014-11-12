# 웹에서의 실시간 커뮤니케이션

## 실시간 커뮤니케이션

언제부터인가 '실시간(real time)'이라는 용어가 기술 용어가 아니라 생활 용어인 것처럼 아주 친숙해졌다. 실시간 검색어 순위, 실시간 VOD, 실시간 버스 운행 현황, 실시간 예매, 실시간 견적 등 '실시간'이라는 용어를 앞에 붙이지 않으면 왠지 시대에 좀 뒤쳐진 듯한 느낌이 들 정도다.

'실시간'이라는 용어는 컴퓨터 분야에서 가장 먼저 사용되었다. 구체적인 기술 분야에 따라 실시간이 실제 의미하는 시간의 차이는 굉장히 크지만, 일반적으로는 다음과 같이 이해하면 큰 무리가 없다.

> 사용자가 거의 지연 시간이 없는 것처럼 느낄 수 있는 처리 속도의 수준

그렇다면 사용자가 거의 지연 시간이 없는 것처럼 느끼는 수준은 대략 어느 정도의 시간을 말하는걸까? 이에 대해서는 사용성 분야의 대가라고 알려진 야콥 닐센(Yakob Nielsen)의 3가지의 한계 시간을 기준으로 삼는 경우가 많다. 야콥 닐센은 1993년에 출간한 '사용성 엔지니어링(Usability Engineering)'에서 다음과 같은 세 가지의 한계 시간을 주장했다.

- 0.1초 : 어떤 시스템이 즉각 반응한다고 느끼는 시간 한계
- 1초 : 사용자가 지연 시간을 인지는 하지만 원래 하려고 했던 행동에 대한 생각의 흐름이 끊기지 않는 시간 한계
- 10초 : 사용자가 다른 일로 주의를 돌려버리게 되는 시간 한계

따라서 야콥 닐센의 주장에 따르면 커뮤니케이션의 어느 일방이 이벤트를 발생시키고 0.1초 이내에 회신을 받을 수 있으면, 실시간 커뮤니케이션이라고 봐도 크게 틀리지 않으며, 1초 이내라면 거의 실시간 커뮤니케이션이라고 대부분의 사용자가 인정해 줄 수 있는 수준이라고 볼 수 있다.


## 실시간 웹

야콥 닐센은 웹 애플리케이션에 대해서도 앞에서 기술한 세 가지의 시간 한계를 동일하게 적용한다(http://www.nngroup.com/articles/response-times-3-important-limits/). 시간의 한계로 보면 그렇게 볼 수 있지만, 일반적으로 실시간 웹 또는 실시간 웹 기술이라고 하면 시간 단위 보다는 사용자에게 정보를 전달하는 방식을 의미하는 경우가 많다. 

다시 말해, 사용자가 어떤 정적인 웹 페이지에 대한 링크를 클릭했을 때, 0.1초 이내에 그 페이지를 사용자에게 보여줄 수 있다고 해서 그 시스템을 실시간 웹 시스템이라고 하지는 않는다. 그보다는 어떤 이벤트가 발생했을 때 사용자가 직접 체크하지 않아도 해당 이벤트에 대한 정보를 사용자에게 바로 알려줄 수 있는 시스템을 실시간 웹 시스템이라고 한다.  

예를 들어 누군가 나에게 메일을 보냈을 때, 내가 굳이 받은 메일함을 새로 고침하거나 클릭하지 않아도 이미 열려있는 받은 메일함 페이지에 새로 받은 메일이 표시가 된다면, 그 웹 메일 시스템은 실시간 웹 시스템이라고 할 수 있다.

웹은 사실 이런 의미에서의 실시간이라는 개념이 없이 출발했다. 더 정확히 말하자면, 웹에서 정보를 교환할 수 있게 해주는 근본 체계인 HTTP는 이런 의미에서의 실시간이라는 개념이 없었다. 1991년 팀 버너스 리가 최초로 제안한 HTTP는 그 이름처럼 텍스트로 이루어진 정보를 링크를 통해 전송할 수 있게 해주는 프로토콜이었다.

하지만 머지않아 HTML 명세가 나오고, 브라우저라는 프로그램이 나오면서 웹은 폭발적으로 성장했고, CGI(Common Gateway Interface) 같은 기술이 나오면서 정적인 정보만을 제공하던 한계를 넘어서고, AJAX(Asynchronous JavaScript and XML) 기술이 나오면서 '실시간 웹 기술'의 기반을 갖출 수 있게 되었다.

이제는 HTML5 명세가 공식적으로 발표(2014년 10월)되면서 WebSocket이나 Server Sent Events 같은 진정한 실시간 웹 기술이 표준으로 자리잡게 되었지만, 아직까지 웹을 구성하고 있는 브라우저나 네트워크 장비, 서버 들이 모두 HTML5를 지원하고 있는 것이 아니기 때문에, 진정한 실시간 웹 시스템을 만들려면 HTML5가 지원되지 않는 상황에서도 AJAX를 통해 구현한 방식으로 처리할 수 있어야 한다. 따라서 HTML5가 표준이 된 지금도 여전히 AJAX를 이용한 기존의 실시간 웹 기술을 알아야 할 필요가 있다.

## AJAX Polling

AJAX Polling은 가장 직관적이고 이해하기 쉬운 형태의 기법이다. 폴링이라는 이름에서 알 수 있는 것처럼 일정 시간 간격을 두고 주기적으로 서버에 요청을 날려서 응답을 받는 방식으로 실시간성을 확보한다.

<<폴링 그림>>

30초를 주기로 폴링한다고 가정할 때의 코드는 대략 다음과 같다.

``` javascript
var url = '/get/newInfo';
var polling = function(url) {
    var xhr = new XMLHttpRequest();
    xhr.open('GET', url);
    xhr.onreadystatechange = function () { ... };
    xhr.send(url);
};

var intervalId = setInterval( function() { polling(url); }, 30000 ); 
```

폴링은 주기적으로 서버에 요청을 날리므로, 서버가 클라이언트에게 알려야 할 이벤트가 주기적으로 발생할 때에는 비용 대비 효과가 가장 좋다. 또한, 요청/응답이 주기적으로 일정하기 때문에 네트워크 부하를 예측할 수 있는 일정 수준으로 정적으로 유지할 수 있다. 하지만, 서버로의 요청 전송 주기가 언제나 정확히 30초라는 것을 보장할 수 없고, 또 요청이 서버로 전송되는 데 소요되는 시간도 불규칙할 수 있기 때문에, 클라이언트의 주기와 서버의 주기가 엇갈리는 때도 많으며, 이 경우에는 실시간 웹 관점에서 가장 좋지 않은 결과가 나올 수 있다.

<< 주기가 맞는 경우와 맞지 않는 경우 비교 그림 >>

또한 서버 측에서 클라이언트에게 알려야 할 이벤트가 불규칙적으로 발생할 때에는, 이벤트가 발생하지 않아 서버가 사실 상 응답해야할 메시지가 없을 때에도 클라이언트는 주기만 돌아오면 계속 서버에 요청을 날리므로 불필요한 요청/응답에 의한 자원 낭비가 발생한다. 이런 단점을 보완할 수 있는 방식이 AJAX Long Polling이다.

## AJAX Long Polling

AJAX Long Polling은 클라이언트가 주기적으로 서버에 요청을 날리는 대신에, 서버로부터 응답을 받을 때만 다시 서버에 요청을 날린다.

<< Long Polling  그림 >>

Long Polling 방식의 코드는 대략 다음과 같다.

``` javascript
var url = '/get/newInfo';
var longPolling = function(url) {
    var xhr = new XMLHttpRequest();
    xhr.open('GET', url);
    xhr.onreadystate = function() { 
        ... 
        longPolling(url);
    };
    xhr.send();
};

longPolling(url);
```

Long Polling은 실질적으로 커뮤니케이션을 할 필요가 있을 때만 요청과 응답이 오가기 때문에 Polling에 비해 더 효율적이라고 할 수 있다. 하지만 사용자에게 알려야 할 이벤트 발생 빈도가 매우 높을 때에는, Polling보다 더 큰 네트워크 부하가 발생할 수 있다.

<< 빈도가 높을 때 폴링은 복수 메시지를 하나의 응답에 모아 회신할 수 있지만, 롱 폴링은 이벤트 하나마다 개별 메시지 응답을 보내는 그림 >>

따라서 이벤트 발생 빈도가 높은 상황에서 Long Polling을 적용할 때에는, 우선 순위가 높은 메시지는 즉각 회신하도록 하고, 우선 순위가 낮은 메시지는 개수 또는 크기 기준으로 일정량을 넘을 때만 서버가 응답을 보내는 네이글 알고리듬(Nagle's Algorithm)의 도입을 검토해서 과도한 부하 발생을 방지하는 보완 조치가 필요하다.



# Websocket

웹소켓은 하나의 TCP 연결 위에서 전이중(full-duplex) 통신 채널을 제공하는 프로토콜로서 2011년에 IETF에 의해 표준으로 제정되었다. 웹소켓을 진정한 실시간 웹 기술이라고 할 수 있는 이유는 '하나의 TCP 연결'과 '전이중'이라는 단어에 담겨있다. 

앞에서 살펴봤던 AJAX Polling/Long Polling은 그 정도에 차이가 있을 뿐, 연결 지속성이 없는 HTTP로 실시간성을 확보하기 위해 클라이언트가 서버에 계속 새로운 HTTP 연결을 생성하는데, 이는 꽤 많은 오버헤드를 유발한다.

<< Note : Browser Networking - Message Overhead 자료 >> 

또한 기존의 HTTP는 기본적으로 요청-응답 패러다임으로, 양방향 통신이 가능하기는 하지만 클라이언트와 서버가 동시에 상대방에게 데이터를 전송할 수 없는 반이중 통신을 지원한다.

웹소켓은 하나의 TCP 연결로 불필요한 연결 오버헤드를 줄일 수 있고, 전이중 통신을 지원해서 연결 지연을 줄일 수 있으므로, Polling 기반의 전통적인 실시간 웹 기술에 비해 성능 면에서 훨씬 뛰어나다.

흔히 말하는 HTML5 웹소켓이라는 것은 정확하게는 IETF에서 제정한 웹소켓 프로토콜이 아니라 웹소켓 프로토콜을 활용할 수 있도록 W3C에서 제정한 웹소켓 API 표준을 말하는 것이지만, 사실 상 혼용되어 사용되고 있으며 문맥에 따라 어떨 때는 프로토콜로, 어떨 때는 API로 이해하는 것이 좋다.

먼저 웹소켓 프로토콜에 대해 알아보고, 웹소켓 API를 이용하여 대화방 예제 프로그램을 만들어 볼 것이다. 그리고 웹소켓을 지원하지 않는 경우에도 실시간 웹 프로그램을 만들 수 있는 fallback 방안과 폴리필 및 웹소켓의 보안과 같은 실무적인 문제도 함께 다뤄볼 것이다.

## 동작원리 <4페이지>

웹소켓은 HTTP를 이용한 실시간 웹 기술의 한계를 기존의 HTTP 인프라에서 극복하기 위해 탄생했다. 그래서 HTTP 용 80포트나 HTTPS 용 443포트에서도 작동하도록 설계되어 있다. 하지만, 웹소켓이 80포트나 443포트에 의존적인 것은 아니다. 웹소켓은 TCP 위에서 작동하는 독립적인 프로토콜로서 브라우저를 통하지 않고도, 또 80포트나 443포트 외의 다른 포트로도 통신이 가능하지만, 브라우저를 통해 웹소켓을 이용하는 경우가 대부분을 차지하므로 이 책에서도 브라우저에서 웹소켓을 사용하는 것을 중심으로 다룬다.

웹소켓 프로토콜은 크게 핸드셰이크와 데이터 전송 두 가지로 구성되어 있다.

### HTTP 핸드셰이크와 업그레이드

브라우저를 통한 웹소켓의 연결은 클라이언트가 서버로 보내는 HTTP 요청으로 시작된다. 

<< https://tools.ietf.org/html/rfc6455#section-1.2 의 요청 헤더 >>

일반적인 HTTP 요청 헤더와 다른 부분이 몇 가지 있지만, 가장 먼저 눈여겨 봐야할 것은 `Upgrade : websocket`과 `Connection : Upgrade` 부분이다. 클라이언트는 웹소켓 연결을 위해 이와 같이 서버에게 업그레이드 요청을 날린다.

서버는 클라이언트의 요청을 받고 업그레이드를 허용할 경우 아래와 같은 응답 헤더를 클라이언트에 회신한다.

<< https://tools.ietf.org/html/rfc6455#section-1.2 의 응답 헤더 >>

서버의 응답 헤더에는 `Upgrade : websocket`과 `Connection : Upgrade` 와 함께 `Switching Protocols`라는 정보를 회신한다.

이렇게 HTTP 핸드셰이크와 업그레이드가 완료되면 클라이언트와 서버는 웹소켓으로 연결되며, 이 때부터 클라이언트와 서버는 기존의 요청/응답 방식이 아닌 양방향 전이중 통신 방식으로 상대방에게 언제든지 데이터를 전송할 수 있게 된다.

### 상태, 이벤트, 메서드, 전송 가능 데이터타입
### AJAX Polling, AJAX Long-Polling, HTTP Streaming과의 비교
## 웹소켓 활용 서비스 사례 <1페이지>
## 웹소켓의 한계 <1페이지>
## 실전 Websocket <15페이지>
### Echo 예제(vertx, node.js - Browser)
### fallback 방안
### 폴리필 소개
### 보안
### 80포트 공유?(잘 모름, 알아봐야함)
### Scale Out?(잘 모름, 알아봐야함)


## 참고 자료

- Realtime의 정의
    - http://whatis.techtarget.com/definition/real-time
    - http://en.wikipedia.org/wiki/Real-time
- Response Times: The 3 Important Limits
    - http://www.nngroup.com/articles/response-times-3-important-limits/
- Real Time Web
    - http://en.wikipedia.org/wiki/Real-time_web
- AJAX의 역사
    - http://en.wikipedia.org/wiki/Ajax_(programming)
- 네이글 알고리듬
    - http://en.wikipedia.org/wiki/Nagle's_algorithm
- Websocket Protocol
    - https://tools.ietf.org/html/rfc6455
- Websocket API
    - http://www.w3.org/TR/websockets/
- Websocket Attributes
    - http://www.tutorialspoint.com/html5/html5_websocket.htm
- Realtime Web App 사례
    - http://www.leggetter.co.uk/real-time-web-technologies-guide 
- Websocket Q&A
    - http://stackoverflow.com/questions/13967051/does-websocket-only-broadcasts-the-data-to-all-clients-connected-instead-of-send
    - http://stackoverflow.com/questions/11077857/what-are-long-polling-websockets-server-sent-events-sse-and-comet/12855533#12855533
- HTTP 관련 각종 통계
    - http://httparchive.org/
- Websocket 정리 자료
    - http://refcardz.dzone.com/refcardz/html5-websocket
