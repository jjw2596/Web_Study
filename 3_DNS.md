# DNS(Domain Name System)란?

* 인터넷을 이용할 때 도메인 이름(www.example.com)을 웹 브라우저의 주소창에 입력하고 접속을 한다.

* 실제로는 도메인 이름을 IP 주소(숫자)로 변환하여 통신하는데 도메일 주소를 숫자인 IP 주소로 변환하는 것을 담당하는 시스템이 **DNS**이다.  

## DNS를 사용하는 이유

* 많은 사이트들의 IP 주소를 일일이 외워서 기억할 수 없고 **길고 복잡한 IP 주소를 외울수가 없기 때문에** DNS를 사용한다.  

# DNS의 구성 요소

1. **도메인 네임 스페이스(Domain Name Space)**  
: 최상위에 루트 DNS 서버가 존재하고 그 하위로 인터넷에 연결된 모든 노드가 연속해서 이어진 계층 구조로 구성  

2. **네임 서버(Name Server)**  
: 주소를 변환 시기키 위해 도메인 네임 스페이스의 트리구조에 대한 정보가 필요. 이 정보를 가진 서버 도메인 이름을 IP주소로 변환하는 서비스

3. **리졸버(Resolver)**  
: DNS 클라이언트의 요청을 네임 서버로 전달하고 네임 서버로부터 오메인 이름과 IP주소를 받아 클라이언트에게 제공하는 기능 수행

# DNS 동작원리

![DNS_process](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcgbNqc%2Fbtq1uuMDN4D%2Fcfifchk6rOn14ZyP9LB8O0%2Fimg.jpg)  

## 기본 동작 원리
```
1. 쿼리 전송  
: 브라우저가 유저로부터 입력받은 도메인 이름을 이용해 쿼리를 날린다. 쿼리는 SIP나 무선 통신업체가 운영하는 DNS Resolver 서버에 
도달하여 도메인 네임을 IP로 바꾸기 위해 어떤 DNS 서버에 요청해야 하는지를 질의하게 된다.  

2. 루트 서버  
: DNS Resolver가 상호작용하는 첫번째 DMS서버를 루트 서버라 하며, 루트 서버는 .com과 같은 최상위 도메인에 대한 DNS 정보를 알고있다.
루트 서버는 쿼리를 요청한 지점에서 멀지 않은 도메인으로 전송시켜 준다.

3. TLD 서버  
: TLD 서버는 최상위 도메인 내에 차상위 도메인에 대한 주소 정보를 저장하는 서버로 쿼리가 TLD서버에 도착하면 TLD 서버가
도메인 네임에 대한 IP주소를 답변한다.

4. DNS
: 서버를 거친 쿼리문이 도메인 네임에 대한 IP 주소를 DNS Resolver로 전송한다.

5. Web Site
: DNS Resolver는 문의한 도메인 네임에 해당하는 IP주소를 브라우저에 알려주고 브라우저는 IP주소로 접근하여 컨텐츠를 가져온다.
```

## DNS 정보 조회 Flow

1. 클라이언트(웹 브라우저)가 DNS를 조회하는 쿼리를 발생시킨다.

2. 발생한 요청은 **Local DNS 서버로 이동**. 이 대의 요청은 다음과 같은 DNS Resolver들을 거치게 된다.  
    - 클라이언트에 저장된 로컬 네임 서버 DNS 캐시
    - ISP가 제공하는 네임서버 DNS 캐시
    - 캐시에서 값이 있으면 해당 IP정보를 응답값으로 전달
    - 없으면 Local PC의 설정 조회 후 다음으로 넘어간다.
<br><br>

3. **DNS 주소에 대한 쿼리가 Root 서버**로 향한다. Root 서버는 '.com'과 같은 최상위 도메인에 대한 DNS 정보를 포함. 도메인 정보에 따라 일반 최상위 도메인(.com, .net, .org ...)이나 국가 최상위 도메인(.kr, .jp ...)으로 분륟외어 **각각에 알맞은 TLD서버의 정보를 전달**받는다.

4. TLD 서버 정보를 이용해 TLD 서버에서 해당 도메인 주소에 대한 관리 주체 서버로 연결

5. 도메인 주소를 관리하는 DNS 서버에서 해당 도메인 주소에 대한 IP를 반환

6. 반환된 IP가 응답으로 전달되면서 Local DNS 캐시에 오게된다.

7. Local DNS를 통해 클라이언트는 IP정보를 얻게되고 해당 서버로 접근하게 된다.

### 예시

![DNS_process](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcXT3gz%2FbtrnbIDMwgR%2FORrJDVES2Jd7kevBbC1tD1%2Fimg.png)  

1. 브라우저에서 "www.naver.com"을 입력. PC는 Local인 203.248.252.2에게 "www.naver.com"이라는 hostname에 대한 IP주소를 물어본다.  
    * Local DNS에 IP주소가 있다면 PC에게 바로 주소를 준다.

2. **Root DNS**에게 질의를 한다.

3. Root DNS서버는 "www.naver.com"의 주소를 모른다는 응답을 한다.

4. Local DNS가 **"com DNS"**(com 도메인을 관리하는 DNS 서버)에게 질의

5. com DNS서버는 주소를 모른다는 응답을 한다.

6. Local DNS가 "www.naver.com"도메인을 관리하는 DNS 서버로 질의를 한다.

7. naver.com 도메인을 관리하는 DNS서버에는 naver.com 호스트네임에 대한 IP주소가 있으므로 "www.naver.com"에 대한 IP 주소인 222.122.195.6을 반환한다.

8. 수신한 Local DNS는 "www.naver.com"에 대한 IP주소를 캐싱하고 해당 IP 주소를 PC에 전달

=> 이와 같이 Local DNS 서버가 여러 DNS 서버를 차례대로(Root DNS 서버 -> com DNS 서버 -> naver.com DNS 서버) 물어봐서 그 답으 찾는 과정을 **Recursive Query**라고 부른다.

# 도메인 네임

## 도메인 네임의 발생 배경

* 인터넷 상에서 다른 단말에 접근하기 위해서는 **숫자와 구분자(.)로 이뤄진 고유의 IP**를 알아야함

* 수많은 서버의 IP를 하나씩 외우는 것은 불편함을 초래함

* IP를 대신해 사용자가 *기억하기 쉬운 영문, 숫자 및 구분자(.)로 구성*된 **도메인 네임(Domain Name)**이 등장

## 도메인 네임의 정의

* 넓은 의미 : 네트워크 상에서 컴퓨터를 식별하는 **호스트 명**

* 좁은 의미 : **도메인 레지스트리에게서 등록된 이름** 
    - 도메인 레지스트리 : 최상위 도메인에 등록된 모든 도메인 네임의 데이터베이스

## 도메인 네임 구조

![domain_name_structure](https://t1.daumcdn.net/cfile/tistory/997DA9405BDFB7B71E)  

* 인터넷 상의 모든 도메인은 루트라고 불리는 도메인 아래에 역트리 구조로 계층적으로 구성

* 루트 도메인 아래의 단계를 1단계 도메인 또는 최상위 도메인(TLD)라고 부르며, 그 다음을 2단계 도메인(SLD)이라고 함

* 도메인은 일반최상위도메인(gTLD)과 국가 최상위도메인(ccTLD)로 구분할 수 있으며 gTLD는 스폰서도메인과 언스폰서도메인으로 구분된다.
