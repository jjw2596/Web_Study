# 웹 브라우저와 웹 서버

![web_browser_and_web_sever](https://media.vlpt.us/images/devegg/post/3e59600f-47be-4385-b6f7-23089a690ba6/image.png)  
* 웹 브라우저가 웹 서버에 웹 페이지 요청을 하면 웹 서버는 웹 페이지 응답을 한다.
* 서버가 브라우저에게 전달한 응답인 HTML 문서를 브라우저는 읽어들이고 해석한 후 Client에게 보여준다.

# 브라우저란?

![web_browser](https://i.pcmag.com/imagery/roundups/03gXNuxiiy22Rd9583sPojG-1.fit_lim.size_850x490.v1614012534.jpg)    
* **웹 브라우저**는 동기(Synchronous)적으로 HTML + CSS, Javascript 언어를 해석하여 내용을 화면에 보여주는 응용 소프트웨어  
* <i>Chrome, Safari, Edge, Opera, Firefox</i> 등이 있다.  
* 세계 최초의 웹 브라우저는 팀 버너스 리가 NeXTSTEP(Unix 계열의 객체지향형 운영체제)용으로 개발한 <strong>'WorldWideWeb'</strong>이다.  

# 브라우저 구조

![browser_structure](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FRYadO%2Fbtrb82lgpwU%2F9nSSKSKfgpnwI2KKkxf4w1%2Fimg.png)    

1. 사용자 인터페이스
* 사용자가 접근할 수 있는 영역

* URL을 입력할 수 있는 주소 표시줄, 이전/다음 버튼, 북마크 메뉴, 새로 고침 버튼과 현재 문서의 로드를 중단 할 수 있는 정지 버튼, 홈 버튼 등 요청한 페이지를 보여주는 창을 제외한 나머지 모든 부분
  
2. 브라우저 엔진
* 사용자 인터페이스와 렌더링 엔진 사이의 동작을 제어합니다. Data Storage를 참조하며 로컬에 데이터를 쓰고 읽으면서 다양한 작업 수행  
  
3. **렌더링 엔진**

* 웹 서버로부터 HTML, XML, 이미지 등 응답 받은 자원을 웹 브라우저 상에 나타내는 표시하는 엔진  

* 브라우저는 서버로부터 HTML 문서를 응답받으면 렌더링 엔진의 HTML 파서와 CSS 파서에 의해 **Parsing**되어 DOM(Document Object Model, 마크업 형태의 HTML 문서를 오브젝트 모델의 형태로 바꿔놓은 것), CSSOM 트리로 변환되고 렌더 트리로 결합한다. 이러한 렌더 트리를 기반으로 브라우저는 웹 페이지를 나타낸다.  

* Parsing : 어떤 페이지(문서, html 등)에서 내가 원하는 데이터를 특정 패턴이나 순서로 추출해 가공하는 것

* 렌더링 엔진의 종류
  - Blink - 크롬, 오페라
  - Webkit - 사파리
  - Trident - 익스플로어
  - EdgeHTML - 마이크로소프트 엣지  

* 렌더링 엔진은 좀 더 나은 사용자 경험을 위해 가능하면 빠르게 내용을 표시. 따라서 일련의 과정들이 동기적으로 진행되지 않는다.

* 렌더링 엔진 동작 과정  
    ![rendering_engine_process](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FWbcmc%2Fbtrb2ccbSyK%2F2TYYpp5TvLFkdVbSYFIq3K%2Fimg.png)    
    1. **렌더링 엔진은 네트워크 레이어를 통해 전달받은 HTML 문서를 파싱하여 DOM 트리를 구축. DOM은 마크업과 1:1 관계를 성립(하나의 마크업에 대한 객체 생성)**  
        ```html
        <html>
            <body>
                <p>
                    Hello World
                </p>
                <div> <img src="example.png"/></div>
            </body>
        </html>
        ```  
        위의 코드를 DOM Tree로 전환 하면 아래와 같이 구성됨  
        ![Dom_Tree](https://www.html5rocks.com/en/tutorials/internals/howbrowserswork/image015.png)  
    
    2. **외부 CSS 파일과 함께 포함된 스타일 요소를 파싱**  
        ![css_parsing](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbKJnUb%2Fbtrb8f6gRKU%2FDn4wpPKW6FVseOKdgGdZQK%2Fimg.png)  
    
    3. **DOM 트리와 위의 2번 결과물을 합쳐 렌더 트리를 구축**
        - DOM 트리가 구축되는 동안 브라우저는 DOM 트리를 기반으로 렌더 트리를 생성
        - 렌더 트리는 문서를 시각적인 구성 요소로 만들어주는 역할
        - 웹킷은 이 구성 요소를 *렌더러* 또는 *렌더 객체*라는 용어 사용. 렌더러는 자신과 자식 요소를 어떻게 배치하고 그려내야 하는지 알고 있다.  
        ![render_tree](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fw1mw9%2Fbtrb22G73FB%2FGONnhHT7sUdPL7TuCK2WG0%2Fimg.png)    
        (좌) DOM 트리, (우) 렌더 트리  
    
    4. **렌더 트리 각 노드에 대해 화면 상에서 배치할 곳을 결정(레이아웃)**
        - 렌더 트리는 위치와 크기를 가지고 있지 않기 때문에 어느 공간에 위치해야 할지 각 객체들에게 위치와 크기를 결정해준다.
    
    5. **UI 백엔드에서 렌더 트리의 각 노드를 그린다.**
        - 렌더 트리가 만들어져 레이아웃이 구성되었으면 UI 백엔드가 동작하여 렌더 트리의 각 객체를 화면의 픽셀 값으로 나타낸다.  

4. 통신
 
* HTTP요청과 같은 서버와 통신이 가능하게 하는 네트워크 호출에 사용됨

5. UI 백엔드
* select, input 등 기본적인 위젯을 그리는 인터페이스

6. 자바스크립트 해석기(엔진)
* 자바스크립트 코드를 해석하고 실행
* HTML 파서는 script 태그를 만너면 DOM 생성 프로세스를 중지하고 자바스크립트 엔진으로 권한을 넘김
* 자바스크립트 엔진은 자바스크립트 코드 또는 src 속성에 정의된 자바스크립드 파일을 로드하고 파싱하여 실행
* 실행이 완료되면 다시 HTML 파서로 제어 권한을 넘김
* 브라우저는 동기적으로 HTML, CSS, Javascript를 처리한다. 때문에 script 태그의 위치에 따라 블로킹이 발생하여 DOM의 생성이 지연될 수 있기 때문에 body 밑에 script 태그를 위치시킨다.

7. 자료 저장소
* Cookie, Local Storage, Indexed DB 등 브라우저 메모리를 활용하여 저장하는 영역

## 브라우저 동작 원리 정리
![browser_process](https://img1.daumcdn.net/thumb/R1920x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FAx7cR%2Fbtrb1qH7RCh%2F5P6KFuOtPDeS41cLbalPLk%2Fimg.png)  
