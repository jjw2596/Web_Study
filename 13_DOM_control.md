# DOM 조작 방법 배우기

## DOM(Document Object Model)

* DOM은 동일한 문서를 표현, 저장, 조작하는 방법을 제공
* DOM은 웹 페이지의 객채 지향 표현이며, 자바스크립트와 같은 스크립팅 언어를 이용해 DOM을 수정할 수 있다.
* document.getElementById(id)  
  document.getElementByClassName(class)  
  document.getElementByTagName(name)  
  위와 같은 명령어로 해당 노드를 선택할 수 있고,  
  document.querySelector(".className" or "#id" or "TagName")  
  document.querySelectorAll()  
  과 같은 명령어로도 선택 가능
* createElement - CREATE  
  querySelector, querySelectorAll - READ  
  textContent, id, classList, setAttribute - UPDATE  
  remove, removeChild, innerHTML = "" , textContent = "" - DELETE  
  appendChild - APPEND