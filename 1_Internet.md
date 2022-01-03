# 인터넷이란?

+ **인터넷**은 표준 인터넷 프로토콜 집합(TCP/IP)을 사용해 전 세계 수십억 명의 사용자들에게 제공되는 **지구 전체의 컴퓨터 네트워크 시스템**이다.
+ 개인, 학교, 기업, 정부 네트워크 등을 한정적 지역에서 전체 영역으로 유선, 무선, 광케이블 기술 등을 통해 연결한 *네트워크들의 네트워크*로 볼 수 있다.  
+ 인터넷은 하이퍼텍스트 마크업 언어(HTML)나 전자 우편을 지원하는 기반 기술 등을 통해 광대한 범위의 정보 자원과 서비스들을 운반한다.  
<br><br>

## 인터넷의 시작

인터넷이란 이름은 1973년 TCP/IP를 정립한 빈튼 서프와 밥 간이 '네트워크의 네트워크'를 구현하여 모든 컴퓨터를 하나의 통신망 안에 연결(International Network)하고자 하는 의도에서 이를 줄여 인터넷(Internet)이라고 처음 명명하였던 데 어원을 두고 있다.

미국 국방성의 *ARPANET*은 이러한 인터네트워크를 본격적으로 구축한 최초의 사례로 아파넷은 초기에는 연구목적으로 쓰였으나 참여 기관이 늘어나면서 다양한 목적으로 아파넷을 쓰고자 하는 요구가 많아졌다.  

또한, 컴퓨터의 종류가 다양해지면서 프로토콜을 재정비할 필요성이 부각되었다. 1983년, 미국 국방성은 군사용 네트워크 기능을 <u>밀넷(MILNET, Military Network)</u>으로 분리시키고, 아파넷은 민간용 네트워크가 되었다. 또한, 초창기에 사용하던 NCP(Network Control Program)보다 속도 및 안정성이 향상된 <u>TCP/IP를 공식 프로토콜로 도입</u>했다. 이로 인해 인터넷 컴퓨터 네트워크의 기본 구조가 갖춰졌으며, 이 때를 즈음하여 '인터넷'은 단순히 일반명사 '인터네트워크'의 약어가 아닌 고유명사 취급을 받기 시작했다.
![ARPANET](https://media.vlpt.us/images/jgone2/post/6f70ba70-ac17-484a-86a9-5ec2f4116dca/%EC%9D%B8%ED%84%B0%EB%84%B7%20%EC%8B%9C%EC%B4%88%EC%9D%B8%20%EC%95%84%ED%8C%8C%EB%84%B7%EC%9D%98%20%EC%97%B0%EA%B2%B0%20%EB%B3%80%ED%99%94.png)  ARPANET의 변화 양상

# 인터넷 작동 원리

## 인터넷 통신의 변화 양상

**① 컴퓨터 ↔ 컴퓨터(1:1 / N:N)**  
두 대 이상의 컴퓨터가 통신이 필요할 때, 다른 컴퓨터와 유선 혹은 무선으로 연결되어야 한다. 그러나 연결하는 컴퓨터의 개수가 많아질수록 아래의 그림처럼 복잡성이 증가하게 된다.  
![complexed_network](https://media.vlpt.us/images/doomchit_3/post/347572a8-3b5b-4b72-89fb-40091d17df10/2.png)

**② 컴퓨터 ↔ 라우터 ↔ 컴퓨터**  
위의 문제를 해결하기 위해 <mark>라우터</mark>라고 하는 특수한 소형 컴퓨터에 네트워크의 각 컴퓨터를 연결한다. <u>라우터는 주어진 컴퓨터에서 보낸 메시지가 올바른 대상 컴퓨터에 도착하는지 확인하는 역할을 수행</u>한다. 아래의 그림이 라우터에 연결된 컴퓨터를 그린 것이다.  
![Router](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbbSCAD%2FbtqECNHyxWm%2FywzrUKBdGbi4gK53zd13ik%2Fimg.png)  

**③ 컴퓨터 ↔ 라우터 ↔ 라우터 ↔ 컴퓨터**  
라우터도 소형 특수 컴퓨터이기 때문에 라우터끼리의 연결도 당연히 가능하며 이러한 라우터 간의 연결은 **무한**대로 할 수 있다.  

**④ 컴퓨터 ↔ 라우터 ↔ 모뎀 ↔ 전화 시설**  
라우터 간의 연결은 케이블 간의 연결이라는 물리적 한계가 있기 때문에 아주 먼 거리까지의 연결은 사실상 힘들다. 그래서 <u>네트워크와 전화 시설을 연결하기 위한 특수 장비</u>인 <mark>모뎀</mark>을 이용해 전화선을 사용한 장거리 네트워크에 연결할 수 있도록 했다.  

**⑤ 컴퓨터 ↔ 라우터 ↔ 모뎀 ↔ 전화 시설 ↔ ISP (↔ ISP) ↔ 전화 시설 ↔ 모뎀 ↔ 라우터 ↔ 컴퓨터**  
모뎀을 통해 전화 시설에 연결한 후 <mark>인터넷 서비스 제공업체(ISP;Internet Service Privider)</mark>에 연결해야 한다. 여기서 <u>ISP란 모두 함계 연결되는 특수한 라우터를 관리하고 다른 ISP의 라우터에도 Access 할 수 있는 회사</u>로 한국에서는 KT, SKT, LG U+가 있다.
![ISP](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FAbY57%2FbtqS295edCG%2FfRH8KbSSKkZF9IkDnLPwJ1%2Fimg.png)  
현재의 인터넷은 이러한 방식으로 연결되어 서로 통신하는 원리를 가지고 있다.  
<br>

# HTTP는 무엇인가?

+ **HTTP** : <strong>Hyper Text Transfer Protocol</strong>의 약자로 인터넷에서 데이터를 주고받을 수 있는 프로토콜. 즉, 일종의 **통신 규약**  
+ 웹 상에서 네트워크로 서버끼리 통신을 할 때 어떠한 형식으로 할 지 규정한 것. 프론트앤드 서버와 클라이언트 간 통신 / 백앤드와 프론트앤드 서버 간 통신에 사용
+ TCP/IP 기반  
<br><br>

## HTTP의 기본 구조, 통신방식

+ **요청/응답(Request/Response) 구조**
+ <b>요청 : Client -> Server / 응답 : Server -> Client</b>
+ HTTP는 <b>Stateless</b>이다. State(상태)를 저장하지 않는다. 즉, 각각의 요청/응답은 독립적이다.  
<br><br>

## HTTP Request 구조

**① Start Line**  
HTTP Request의 첫 라인으로 3부분으로 구성되어 있다. 
+ HTP Method : 해당 Request가 의도한 Action을 정의하는 부분
  - <b>GET</b> : 자료를 요청할 때 사용
  - <b>POST</b> : 자료의 생성을 요청할 때 사용
  - <b>PUT</b> : 자료의 수정을 요청할 때 사용
  - <b>DELETE</b> : 자료의 삭제를 요청할 때 사용
+ Request Target : 해당 Request가 전송되는 목표 URL
+ HTTP Version 

**② Header**
+ 해당 Request에 대한 추가 정보를 담고있는 부분
+ Key:Value 값으로 되어있다.(: 사용)<br>
자주 사용 되는 Header 정보
  - Host : 요청이 전송되는 Target의 host url
  - User-Agent : 요청을 보내는 클라이언트의 정보
  - Accept : 해당 요청이 받을 수 있는 Response 타입
  - Connection : 해당 요청이 끝난 후 클라이언트와 서버가 계속해서 네트워크 연결을 유지할지 안할지 지시
  - Content-Type : 해당 요청이 보내는 메시지 Body의 타입
  - Content-Length : 메시지 Body의 길이

**③ Body**  
해당 Request의 실제 메시지/내용. Body가 없는 Request도 많다. GET Request들은 대부분 Body가 없는 경우가 많다.  
Request 코드 예시  
```
GET https://www.google.com HTTP/1.1 //시작줄
User-Agent: Mozilla/5.0 (Window NT 10.0; Win64; x64) ... //헤더 : 요청에 대한 정보
Upgrade-Insecure-Requests: 1 // Body
```

## HTTP Response 구조

Response도 Request처럼 3부분으로 구성되어 있다.  
**① Status Line**  
Response의 상태를 간략하게 나타내주는 부분.
+ HTTP 버전
+ Status Code : 응답 상태를 나타내는 코드
  - <b>1XX(조건부 응답)</b> : 요청을 받았으며 작업을 계속한다.
  - <b>2XX(성공)</b> : 클라이언트가 요청한 동작을 수신하여 이해했고 승낙했으며 성공적으로 처리했음
  - <b>3XX(리다이렉션 완료)</b> : 클라이언트는 요청을 마치기 위해 추가 동작을 취해야 한다.
  - <b>4XX(요청 오류)</b> : 클라이언트에 오류가 있음을 나타낸다.
  - <b>5XX(서버 오류)</b> : 서버가 유효한 요청을 명백하게 수행하지 못했음
+ Status Text : 응답 상태를 간략하게 설명해주는 부분

**② Headers**  
+ Response의 Headers와 동일
+ 다만 Response에서만 사용되는 Header 값들이 존재

**③ Body**  
+ Response의 Body와 일반적으로 동일하다.
+ Request와 마찬가지로 모든 Response가 Body가 있지는 않다. 데이터를 전송할 필요가 없을경우 Body가 비어있게 된다.  
