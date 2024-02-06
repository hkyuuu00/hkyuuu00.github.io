---
date: 2024-01-18 21:18:01 +0900
layout: post
title: "[JS] JavaScript 기초 정리 [2]"
subtitle: "JavaScript 기초를 정리하여 자세히 알아보기"
description: JavaScript의 기본 문법들 알아보며 JavaScript의 구조를 공부
image: /assets/img/post/js.jpg
optimized_image: /assets/img/post/js-optimized.jpg
category: programing
tags:
  - programing
  - JavaScript
  - JS
---

<span style="font-size:1.9em; font-weight:bold;">목차</span>
* TOC
{:toc}


## DOM

<span style="font-size:1.4em; font-weight:bold;">DOM 이란?</span>

**DOM**은 *Document Object Model*의 약자로 *HTML*의 작은 부분까지 접근할 수 있으며, 문서 구조, 스타일, 내용등을 변경하고 HTML로 이루어진 웹 페이지를 동적으로 움직이게 만드는 모델이다.

*DOM* 위에 있는 최상위 객체 모델은 *BOM*으로 *window*라는 객체가 있으며 *DOM*은 *window*객체의 하위 객체이며, *window*는 생략이 가능하다.

![nodetree](../assets/img/post/nodetree.jpg)

*Document Node*<br>
*document* 객체를 말하며 *DOM* 트리에 접근하기 위한 최상위 노드로 모든 *DOM* 트리에 접근하기 위해 시작하는 노드이다.

*Element Node*<br>
*HTML* 구성 요소인 태그를 의미한다. 문서내 태그들은 모두 *Element Node*이며, 각각의 *Element Node*는 다시 *Attribute*와 *Text Node*를 가진다.

*Attribute Node*<br>
태그들의 속성을 객체화한 노드를 의미하며, 특정 태그의 속성에 접근할 때 사용해야 한다.

*Text Node*<br>
태그의 텍스트를 객체화한 노드이며, 자식 노드를 가질 수 없고 *DOM* 트리구조의 마지막 노드이다.


<span style="font-size:1.4em; font-weight:bold;">HTML요소에 관한 메소드</span>

**HTML요소 선택**
<table>
  <tr>
    <td>.getElementById()</td>
    <td>해당 아이디의 요소를 선택</td>
  </tr>
  <tr>
    <td>.getElementsByClassName()</td>
    <td>해당 클래스에 속한 요소를 모두 선택</td>
  </tr>
  <tr>
    <td>.getElementsByName()</td>
    <td>해당 name 속성값을 가지는 요소를 모두 선택</td>
  </tr>
  <tr>
    <td>.querySelectorAll() </td>
    <td>해당 선택자로 선택되는 요소들을 모두 선택</td>
  </tr>
  <tr>
    <td>.querySelector()</td>
    <td>해당 선택자로 선택되느 요소를 1개 선택</td>
  </tr>
  <tr>
    <td>appendChild(append할 Element)</td>
    <td>선택한 Element의 자식 Element 마지막에 추가</td>
  </tr>
  <tr>
    <td>remove()</td>
    <td>선택된 Element 삭제</td>
  </tr>
  <tr>
    <td>removeChild(삭제할 Element)</td>
    <td>선택된 Element의 자식 Element 삭제</td>
  </tr>
  <tr>
    <td>createElement(만들 Element)</td>
    <td>Element 생성, 그 후 appendChild()로 추가해줘야 함</td>
  </tr>
  <tr>
    <td>firstChild/lastChild</td>
    <td>first면 첫번째, last면 마지막 자식 Element 반환</td>
  </tr>
  <tr>
    <td>textContent</td>
    <td>요소의 텍스트 내용만을 가져오거나 설정</td>
  </tr>
  <tr>
    <td>innerText</td>
    <td>요소의 보이는 텍스트만을 가져오거나 설정</td>
  </tr>
  <tr>
    <td>innerHTML</td>
    <td>요소의 HTML 내용을 가져오나 설정</td>
  </tr>
  <tr>
    <td>window.content</td>
    <td>현재 창 또는 프레임의 내용을 참조</td>
  </tr>
  <tr>
    <td>window.onload</td>
    <td>페이지가 완전히 로드된 후에 실행할 스크립트를 설정</td>
  </tr>
  <tr>
    <td>window.dump</td>
    <td>디버깅 정보를 출력</td>
  </tr>
  <tr>
    <td>window.scrollTo</td>
    <td>주어진 좌표로 창 또는 프레임의 내용을 스크롤</td>
  </tr>
</table>


<span style="font-size:1.4em; font-weight:bold;">이벤트, 스타일 오브젝트</span>

**이벤트 오브젝트**
<table>
  <tr>
    <td>type</td>
    <td>이벤트의 종류를 참조</td>
  </tr>
  <tr>
    <td>keyCode</td>
    <td>키 코드를 참조</td>
  </tr>
  <tr>
    <td>altKey</td>
    <td>Alt키가 눌렸는지 참조</td>
  </tr>
  <tr>
    <td>button</td>
    <td>마우스 버튼의 종류를 참조</td>
  </tr>
  <tr>
    <td>screenX</td>
    <td>모니터 화면에서 마우스의 x좌표를 참조</td>
  </tr>
  <tr>
    <td>screenY</td>
    <td>모니터 화면에서 마우스의 y좌표를 참조</td>
  </tr>
  <tr>
    <td>clientX</td>
    <td>브라우저 페이지에서 마우스의 x좌표를 참조</td>
  </tr>
  <tr>
    <td>clientY</td>
    <td>브라우저 페이지에서 마우스의 y좌표를 참조</td>
  </tr>
</table>

**스타일 오브젝트**
<table>
 <tr>
    <td>color</td>
    <td>문자 색을 참조 설정</td>
  </tr>
  <tr>
    <td>fontFamily</td>
    <td>글꼴을 참조 설정</td>
  </tr>
  <tr>
    <td>fontSize</td>
    <td>글꼴 크기를 참조 설정</td>
  </tr>
  <tr>
    <td>fontWeight</td>
    <td>글꼴의 굵기를 참조 설정</td>
  </tr>
  <tr>
    <td>fontStyle</td>
    <td>글꼴의 스타일을 참조 설정</td>
  </tr>
  <tr>
    <td>textDecoration</td>
    <td>문자 장식을 참조 설정</td>
  </tr>
  <tr>
    <td>textTransform</td>
    <td>영문자의 대소문자를 참조 설정</td>
  </tr>
  <tr>
    <td>textAlign</td>
    <td>행 정렬을 참조 설정</td>
  </tr>
  <tr>
    <td>textIndent</td>
    <td>첫 번째 행의 들여쓰기를 참조 설정</td>
  </tr>
</table>

**기타 오브젝트**
<table>
  <tr>
    <td>history.back()</td>
    <td>한 페이지 뒤로 돌아가기</td>
  </tr>
  <tr>
    <td>history.Forward()</td>
    <td>한 페이지 앞으로 가기</td>
  </tr>
  <tr>
    <td>history.go()</td>
    <td>지정한 값 만큼 이동</td>
  </tr>
  <tr>
    <td>anchors.name</td>
    <td>앵커 이름을 참조 설정</td>
  </tr>
  <tr>
    <td>anchors.text</td>
    <td>앵커의 텍스트를 참조 설정</td>
  </tr>
</table>

위의 내용 말고도 각종 참조 설정하는 오브젝트들이 많다. 다양한 오브젝트들은 검색을 통해 찾아보자. 


## 이벤트

<span style="font-size:1.4em; font-weight:bold;">이벤트란?</span>

이벤트는 웹 페이지에서 특정 행동을 했을 때, 어떤 사건을 발생시키는 것이다.<br>
이벤트 처리기는 이벤트가 발생했을 때, 개발자가 구현한 기능을 수행하도록 함수를 연결하는 것을 이벤트 핸들러 또는 이벤트 리스너라고 한다.

<span style="font-size:1.4em; font-weight:bold;">이벤트 핸들러와 리스너</span>

<span style="font-size:1.1em; font-weight:bold;">이벤트 핸들러</span>

이벤트 핸들러는 하나의 요소에 하나의 이벤트를 처리할 수 있다. *HTML* 태그에 설정하거나, *DOM* 요소 객체의 이벤트 처리기 프로퍼티로 설정하는 방법이다.<br>

이벤트 핸들러는 앞에 **on**을 붙여 주고 이벤트에 대한 동작을 처리한다. 

```html
<!--html태그에 바로 사용하는 법-->
<div onclick="alert('클릭')">클릭</div>

<!--함수를 사용하는 법-->
<div onclick="view()">클릭</div>
    
<script>
  function view() {
    alert("클릭");
  }
</script>
```


<span style="font-size:1.1em; font-weight:bold;">이벤트 리스너</span>

이벤트 리스너는 하나의 요소에 여러가지 이벤트를 처리할 수 있으며, addEventListner() 메소드를 사용한다.<br>
`DOM객체. addEventListener(이벤트명, 실행할 함수명, 옵션)`

```html
<html>
  <a>클릭</a>
</html>
<script>
  const a = document.querySelector('a');
  a.addEventListener('click', showConsole);
  function showConsole() {
  	console.log("콘솔로그 실행");
  }
</script>
```

이벤트 리스너를 삭제하려면 밑의 방식을 사용하면 된다<br>

`DOM객체. removeEventListener(이벤트명, 실행했던 함수명);`


<span style="font-size:1.4em; font-weight:bold;">주요 이벤트 종류</span>

이벤트 핸들러를 사용할 경우 이벤트 앞에 **on**붙이기

**마우스 이벤트**
<table>
  <tr>
    <td>click</td>
    <td>요소에 마우스를 클릭했을 때 이벤트가 발생</td>
  </tr>
  <tr>
    <td>dbclick</td>
    <td>요소에 마우스를 더블클릭했을 때 이벤트가 발생</td>
  </tr>
  <tr>
    <td>mouseover</td>
    <td>요소에 마우스를 오버했을 때 이벤트가 발생</td>
  </tr>
  <tr>
    <td>mouseout</td>
    <td>요소에 마우스를 아웃했을 때 이벤트가 발생</td>
  </tr>
  <tr>
    <td>mousedown</td>
    <td>요소에 마우스를 눌렀을 때 이벤트가 발생</td>
  </tr>
  <tr>
    <td>mouseup</td>
    <td>요소에 마우스를 떼었을 때 이벤트가 발생</td>
  </tr>
  <tr>
    <td>mousemove</td>
    <td>요소에 마우스를 움직였을 때 이벤트가 발생</td>
  </tr>
  <tr>
    <td>contextmenu</td>
    <td>마우스 오른쪽 버튼을 눌렀을 때 메뉴가 나오기 전에 이벤트 발생</td>
  </tr>
</table>

**키 이벤트**
<table>
  <tr>
    <td>keydown</td>
    <td>키를 눌렀을 때 이벤트가 발생</td>
  </tr>
  <tr>
    <td>keyup</td>
    <td>키를 떼었을 때 이벤트가 발생</td>
  </tr>
  <tr>
    <td>keypress</td>
    <td>키를 누른 상태에서 이벤트가 발생</td>
  </tr>
</table>

**폼 이벤트**
<table>
  <tr>
    <td>focus</td>
    <td>요소에 포커스가 이동되었을 때 이벤트 발생</td>
  </tr>
  <tr>
    <td>blur</td>
    <td>요소에 포커스가 벗어났을 때 이벤트 발생</td>
  </tr>
  <tr>
    <td>change</td>
    <td>요소에 값이 변경 되었을 때 이벤트 발생</td>
  </tr>
  <tr>
    <td>submit</td>
    <td>submit 버튼을 눌렀을 때 이벤트 발생</td>
  </tr>
  <tr>
    <td>reset</td>
    <td>reset 버튼을 눌렀을 때 이벤트 발생</td>
  </tr>
  <tr>
    <td>select</td>
    <td>input이나 textarea안의 텍스트를 드래그하여 선택했을 때 이벤트 발생 </td>
  </tr>
</table>

**기타 이벤트**
<table>
  <tr>
    <td>load</td>
    <td>페이지의 로딩이 완료되었을 때 이벤트 발생</td>
  </tr>
  <tr>
    <td>abort</td>
    <td>이미지의 로딩이 중단되었을 때 이벤트 발생</td>
  </tr>
  <tr>
    <td>unload</td>
    <td>페이지가 다른 곳으로 이동될 때 이벤트 발생</td>
  </tr>
  <tr>
    <td>resize</td>
    <td>요소에 사이즈가 변경되었을 때 이벤트 발생</td>
  </tr>
  <tr>
    <td>scroll</td>
    <td>스크롤바를 움직였을 때 이벤트 발생</td>
  </tr>
</table>


지금까지 자바스크립트의 기초를 알아봤고, 나중에 자바스크립트로 프로젝트를 하면서 모듈화와 *AJAX*, 비동기처리 등에 대해 공부해봐야겠다.
