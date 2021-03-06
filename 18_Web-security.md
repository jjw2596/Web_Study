# 💻 웹 보안 지식

## 📖 HTTPS

> 웹 데이터를 전송하는 프로토콜인 HTTP의 보안 버전
* 웹 사이트 사용자의 신용카드 번호 등 중요한 데이터를 안전하게 전송
* SSL을 이용하여 서버와 브라우저 사이의 암호화된 연결을 지원  

<br>

## 📖 콘텐츠 보안 정책(CSP, Content-Security-Policy)

> 일반적인 웹 취약점이나 XSS에 대해 애플리케이션을 안전하게 보호하기 위해 고안된 보안 계층
* Content-Security-Policy HTTP 응답 헤더를 설정하여 사용
* 스크립트 및 이미지와 같은 외부 리소스를 안전하게 로드 하도록 지원
* 모든 리소스 요청을 HTTPS 등으로 투명하게 업그레이드

<br>

## 📖 교차 출처 리소스 공유(CORS, Cross-Origin Resource Sharing)

> 추가 HTTP헤더를 사용하여 한 출처에서 실행중인 웹페이지가 다른 출처의 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제
* 리소스가 자신의 출처와 다를때 교차 출처 HTTP 요청을 실행
* 다른 도메인의 리소스를 요청할 수 있도록 허용하는 정책

### 관련 개념

* 출처(origin)
    : 도메인, 프로토콜, 포트

* SOP(Same-Origin Policy)
    : 같은 출처에서만 리소스를 공유할 수 있는 정책

<br>

## 📖 SSL(Secure Socket Layer)

> 웹 사이트와 브라우저(or 서버) 사이에 전송된 데이터를 암호화하여 인터넷 연결 보안을 유지하는 기술 표준
* 인증되지 않은 사용자로부터 세션 중에 교환된 데이터를 보호
* TCP/IP 및 응용프로그램계층 사이에 구현된 공개키 암호를 사용한 보안기술
=> IEFT(국제 인터넷 표준화 기구)에 의해 TLS로 표준화

<br>

## 📖 TLS(Transport Layer Security)

> 모든 종류의 인터넷 트래픽을 암호화하는 기술표준

* SSL/TLS로 많이 사용
* 브라우저 주소창에 https와 사물쇠 모양이 있는 경우 TLS를 통해 연결되어 있음을 의미
* 이메일, 유즈넷 등에서 사용

<br>

## 📖 SSL/TLS

> 클라이언트 / 서버 간 통신을 암호화 하는 기법
* 전송계층 프로토콜이며 HTTP나 FTP 등의 응용계층 프로토콜과 조합하여 사용
* 인증기관(CA)가 발행하는 서버 인증서를 사용  
<br>
※ 서버인증서  
    * 서버의 신뢰성을 증명하기 위한 디지털 데이터
    * 서버의 공개 키와 사용자의 정보가 합쳐져 있는 데이터

<br>

## 📖 OWASP(The Open Wen Apllication Security Project)

> 웹에 관한 정보 노출, 악성 파일 및 스크립트, 보안 취약점 등을 연구하느 오픈소스 웹 애플리케이션 보안 프로젝트