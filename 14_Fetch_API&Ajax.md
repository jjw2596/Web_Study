# Fetch API / Ajax(XHR) 배우기

## Ajax(Asynchronouse Javascript XML)  

* XMLHttpRequest 객체를 이용해서 웹 서버와 비동기로 통신하고, DOM을 이용해서 웹 페이지를 동적으로 바꿔주는 프로그래밍 기법
* 현재 XML을 사용하는건 드물고 JSON을 사용
* 페이지 새로 고침 없이 특정 데이터만 리로드
* 서버로부터 데이터를 받고 작업을 수행
<br><br>

## Ajax 구현하기

Ajax를 구현하는 기술에는 여러 기술이 존재한다.  
대표적으로 3가지가 있다.  
1. XMLHttpRequest
2. Fetch API
3. JQuery
<br><br>

## Fetch API  

* Fetch API는 기본적으로 XMLHttpRequest보다 더 강력하고 유연하다
* 이벤트 기반인 XMLHttpRequest와는 달리 Fetch API는 Promise 기반으로 구성되어 있어 비동기 처리 프로그래밍 방식에 잘 맞는 형태이다
* then이나 catch와 같은 체이닝으로 작성할 수 있다  
    ```
    체이닝: 랜덤 파일의 어드레스 기법이다. 어떤 내용을 찾을 경우, 최초의 어드레스에는 원하는 데이터가 없으므로, 다음의 어드레스가 지정된다. 이렇게 하여 차례로 다른 어드레스를 더듬어 원하는 데이터에 도달한다. 체이닝의 기법은 파일의 복잡한 구조를 가지고 있는 경우에 사용된다.
    ```
* 가독성이 좋으며 Async / Await으로 비동기 콜백을 쉽게 벗어날 수 있다
* Fetch API는 JS 기본 라이브러리이기 때문에 JQuery와 같이 CDN과 같은 다른 작업을 하지 않아도 바로 사용할 수 있다.
<br><br>

## fetch 사용법

* `fetch()` 함수는 첫번째 인자로 URL, 두번째 인자로 옵션 객체를 받고 Promise 타입의 객체를 반환
* 반환된 객체는 API 호출이 성공했을 경우에는 응답(response) 객체를 resolve하고, 실패했을 경우에는 예외(error) 객체를 rejcet한다
```javascript
fetch("https://jsonplaceholder.typicode.com/posts", option)
    .then(res => res.text())
    .then(text => console.log(text));
```
1. fetch에는 기본적으로 첫 번째 인자에 요청할 <b>url</b>이 들어간다.
2. 기본적으로 http 메서드 중 GET으로 등장
3. fetch를 통해 ajax를 호출 시 해당 주소에 요청을 보낸 다음, 응답 객체(Promise object Response)를 받는다.
4. 첫 번째 <b>then</b>에서 그 응답을 받게되고, <b>res.text()</b>메서드로 파싱한 text 값을 리턴한다
5. 그 다음 then에서 리턴받은 text 값을 받고, 원하는 처리를 할 수 있게 된다.

* 옵션(options) 객체에는 HTTP 방식(method), HTTP 요형 헤더(header), HTTP 요청 전문(body) 등을 설정할 수 있다.
* 응답 객체로 부터는 HTTP 응답 상태(status), HTTP 응답 헤더(headers), HTTP 응답 전문(body) 등을 읽어올 수 있다.
* fetch() 함수는 엄밀히 말해 브라우저의 window 객체에 소속되어 있기 때문에 window.fetch()로 사용되기도 한다.
<br><br>

## Fetch API 기본 형태

Fetch API는 Promise 기반이기 때문에 체이닝 형태로 사용될 수 있다.
```javascript
fetch("http://server-ip.com")
    .then((response) => {
        return response.json();
    })
    .then((myJson) => {
        console.log(JSON.stringify(myJson);)
    })
    .catch((error) => {
        console.err(error);
    });
```
<br><br>

## response 프로퍼티와 메서드

* fetch를 통해 요청을 하고 서버로부터 값을 응답 받으면 .then을 통해 함수의 인자에 담기게 되는데 이 값은 <b>Resonse객체로서 여러가지 정보</b>를 담고 있다.
* 필요한 변수값이나 메서드를 뽑아내서 값을 얻으면 된다.
    * response.status : HTTP 상태 코드(ex) 200, 300, ...)
    * response.ok : HTTP 상태 코다가 200과 299 사이일 경우 true
    * response.body : 내용
    * response.text() : 응답을 읽고 텍스트를 반환
    * response.json() : 응답을 JSON 형태로 파싱
    * response.formData() : 응답을 FormData 객체 형태로 반환
    * response.blob() : 응답을 Blob(타입이 있는 바이너리 데이터) 형태로 반환
    * response.arrayBuffer : 응답을 ArrayBuffer(바이너리 데이터를 로우 레벨 형식으로 표현한 것) 형태로 반환
* 응답 자료 형태 반환 메서드는 한 번만 사용할 수 있다.
* 만일 response.text()를 사용해 응답을 얻었다면 본문의 콘텐츠는 모두 처리된 상태이기 때문에 다른 반환 메서드를 사용해도 동작하지 않는다.
<br><br>

## header 조작하기

* 서버와 통신 할 때, HTTP 헤더를 조작하는 일은 필수적으로 진행되어야 한다.
* Fetch API에서도 header를 조작할 수 있는데, 다음과 같이 option 객체에 ehaders에 들어갈 내용들을 지정하는 방법을 사용할 수 있다.
```javascript
const option = {
    headers : {
        "Content-Type" : "application/json",
    },
};

fetch("http://server-ip.com", option)
    .then((response) => {
        //생략
    })
    .then((myJson) => {
        //생략
    })
    .catch((error) => {
        //생략
    });
```
<br><br>

## Fetch API GET Method

**GET:존재하는 자원을 요청**
* fetch 함수는 디폴트로 GET방식으로 작동되고 GET방식은 요청 전문을 받지 않기 때문에 옵션 인자가 필요 없다.  
* 단순히 원격 API에 있는 데이터를 가져올 때 쓰임
* 응답(response) 객체는 json()메서드를 제공하고, 이 메서드를 호출하면 응답 객체로 부터 JSON 형태의 데이터를 자바스크립트 객체로 변환하여 얻을 수 있음

```javascript
fetch("https://jsonplaceholder.typicode.com/posts/1") // posts의 id 1인 엘리먼트를 가져옴
    .then((response) => response.json())
    .then((data) => console.log(data))

//응답 결과
{
"userId": 1,
"id": 1,
"title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
"body": "quia et suscipit↵suscipit recusandae consequuntur …strum rerum est autem sunt rem eveniet architecto"
}
```
<br><br>

## Fetch API POST Method

**POST:새로운 자원 생성 요청**
* 폼 등을 사용해서 데이터를 만들어 낼 때, 보내는 데이터의 양이 많거나 비밀번호 등 개인정보를 보낼 때 사용
* 새로운 포스트 생성 위해서는 <b>method 옵션을 POST로 지정</b>해주고, <b>header 옵션으로 JSON포맷 사용한다고 알려줘야 함. body옵션에는 요청 데이터를 JSON포맷</b>으로 넣어줌
    * method : HTTP 메서드
    * header : 요청 헤드가 담긴 객체(제약 사항 있음)
    * body : 보내려는 데이터(요청 본문)로 string이나 FormData, BufferSource, Bolb, UrlSearchParams 객체 형태
```javascript
fetch("https://jsonplaceholder.typicode.com/posts", {
    method: "POST", // POST
    headers: { // 헤더 조작
        "Content-Type": "application/json",
    },
    body: JSON.stringify({ // 자바스크립트 객체를 json화 한다.
        title: "Test",
        body: "I am testing!",
        userId: 1,
    }),
})
    .then((response) => response.json())
    .then((data) => console.log(data))
```
<br><br>

## Fetch API PUT Method(전체수정)

**PUT:존재하는 자원 변경 요청**
* API에서 관리하는 데이터의 <b>수정</b>을 위해 사용
* method 옵션만 PUT으로 설정한다는 점 빼고는 POST방식과 비슷
* <b>전체를 body의 데이터로 교체</b>
```javascript
fetch("https://jsonplaceholder.typicode.com/posts", {
    method: "PUT",
    headers: {
        "Content-Type": "application/json",
    },
    body: JSON.stringify({
        title: "Test" // 아예 title 엘리먼트로 전체 데이터를 바꿈. 마치 innerHTML같이.
    }),
})
    .then((response) => response.json())
    .then((data) => console.log(data))
```
<br><br>

## Fetch API PATCH Method(부분수정)

**PATCH:존재하는 자원 일부 변경 요청**
* body의 데이터와 알맞는 <b>일부</b>만 교체함
```javascript
fetch("https://jsonplaceholder.typicode.com/posts/1", { // posts의 id 1인 엘리먼트를 수정
    method: "PATCH",
    headers: {
        "Content-Type": "application/json",
    },
    body: JSON.stringify({
        title: "Test" // title만 바꿈. 나머지 요소는 건들지 않음.
    }),
})
    .then((response) => response.json())
    .then((data) => console.log(data))
```
<br><br>

## Fetch API DELETE Method

**DELETE:존재하는 자원 삭제 요청**
* 보낼 데이터가 없기 때문에 headers, body 옵션이 필요없음
```javascript
fetch("https://jsonplaceholder.typicode.com/posts/1", {
    method: "DELETE",
    })
    .then((response) => response.json())
    .then((data) => console.log(data))
```
<br><br>