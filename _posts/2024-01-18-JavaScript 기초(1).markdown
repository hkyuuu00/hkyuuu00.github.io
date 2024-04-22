---
date: 2024-01-18 19:18:01 +0900
layout: post
title: "[JS] JavaScript 기초 정리 [1]"
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


## JavaScript란?

<span style="font-size:1.4em; font-weight:bold;">JavaScript란?</span>

*JavaScript*는 웹 페이지에 동적인 기능을 추가하기 위해 주로 사용하며, 웹 페이지를 프로그래밍적으로 제어하기 위한 객체기반의 스크립트 언어이다.


<span style="font-size:1.4em; font-weight:bold;">JavaScript의 위치</span>

HTML 내부에 포함시키는 방법
 - 문서 어디든 사용할 수 있으나 *HTML*문서를 전부 로드되고나서 실행하도록 `<body>`태그의 끝 부분에 사용한다.

 ```html
<!DOCTYPE html>
<html>
	<head>
 		<title>JavaScript</title>
	</head>
	<body>
  	<script>
   		자바 스크립트 코드
   	</script>
	</body>
</html>
 ```

HTML 외부에 분리하여 사용하는 방법
 - 확장자는 *.js*로 지정하여 `<script src = "index.js">` 방법으로 불러와 사용할 수 있다.
 - 자바스크립트 소스가 너무 길거나 여러 페이지에 동일한 스크립트를 사용할 때 편리하다.

```html
<!DOCTYPE html>
<html>
	<head>
 		<title>JavaScript</title>
	</head>
	<body>
  	<script src="./index.js"></script>
	</body>
</html>
```

<span style="font-size:1.4em; font-weight:bold;">주석</span>

 - // 한 줄 주석
 - /* 여러 줄 주석 */


## JavaScript의 기본 구조

<span style="font-size:1.4em; font-weight:bold;">변수와 상수</span>

**변수**는 데이터를 저장하는 컨테이너이며 저장된 값을 바꿀 수 있다.<br>
**상수**는 저장된 데이터 값이 변화할 수 없는 변수이다.  
*JavaScript*에서는 데이터 뿐만 아니라 오브젝트와 함수도 담을 수 있다.

*JavaScript*에는 3가지의 변수가 있다.
 - *var*
 - *let*
 - *const*


<span style="font-size:1.1em; font-weight:bold;">var</span>

*var*는 함수 단위 스코프이며, *var*로 선언된 변수는 선언된 함수 내에서 어디서든지 접근할 수 있다.<br>
또한 *var*로 선언된 변수는 선언 전에 사용해도 에러가 발생하지 않는다.


<span style="font-size:1.1em; font-weight:bold;">let</span>

*let*은 블록 단위 스코프로 *let*으로 선언된 변수는 선언된 블록`{}` 내에서만 접근할 수 있다.<br>
*let*으로 선언된 변수는 선언 전에 사용하면 에러가 발생한다.

<span style="font-size:1.1em; font-weight:bold;">const</span>

*const*도 블록 단위 스코프이다. 하지만, *let*과는 다르게 *const*로 선언된 변수는 한 번 할당하면 변경할 수 없다.<br>
*const*로 선언된 변수는 반드시 선언과 동시에 초기화해야 한다.


<span style="font-size:1.4em; font-weight:bold;">데이터 타입</span>

데이터 타입으로는 변경 불가능한 값인 기본 타입과 참조 타입이 있다.

기본 타입
 - *Number* - 숫자
 - *String* - 문자열
 - *Boolean* - 불린값 (true와 false를 나타내는 타입)
 - *null* - 비어있는 값
 - *undefined* - 비어있는 값
 - *symbol* - 충돌 위험이 없는 고유한 프로퍼티를 만들기 위한 타입

참조 타입
 - *Object* 객체

객체는 하나의 값만 저장되는 기본 타입과 다르게 여러 개의 프로퍼티를 저장할 수 있다.


<span style="font-size:1.4em; font-weight:bold;">연산자</span>

*JavaScript*에는 여러 연산자가 있지만 자주 사용하는 연산자들을 알아보자.

<span style="font-size:1.1em; font-weight:bold;">산술연산자</span>

<table>
  <tr>
    <td>+</td>
    <td>덧셈</td>
  </tr>
  <tr>
    <td>-</td>
    <td>뺄셈</td>
  </tr>
  <tr>
    <td>*</td>
    <td>곱셈</td>
  </tr>
  <tr>
    <td>/</td>
    <td>나눗셈</td>
  </tr>
  <tr>
    <td>%</td>
    <td>나머지</td>
  </tr>
</table>


<span style="font-size:1.1em; font-weight:bold;">대입연산자</span>

<table>
  <tr>
    <td>+=</td>
    <td>a += 1</td>
    <td>a + 1 결과값을 a에 대입</td>
  </tr>
  <tr>
    <td>-=</td>
    <td>a -= 1</td>
    <td>a - 1 결과값을 a에 대입</td>
  </tr>
  <tr>
    <td>*=</td>
    <td>a *= 1</td>
    <td>a * 1 결과값을 a에 대입</td>
  </tr>
  <tr>
    <td>/=</td>
    <td>a /= 1</td>
    <td>a / 1 결과값을 a에 대입</td>
  </tr>
  <tr>
    <td>%=</td>
    <td>a %= 1</td>
    <td>a % 1 결과값을 a에 대입</td>
  </tr>
</table>


<span style="font-size:1.1em; font-weight:bold;">증감연산자</span>

<table>
  <tr>
    <td>++a</td>
    <td>a를 1증가시킨 후, a를 반환</td>
  </tr>
  <tr>
    <td>a++</td>
    <td>a를 반환한 후, a를 1증가</td>
  </tr>
  <tr>
    <td>--a</td>
    <td>a를 1감소시킨 후, a를 반환</td>
  </tr>
  <tr>
    <td>a--</td>
    <td>a를 반환한 후, a를 1 감소</td>
  </tr>
</table>


<span style="font-size:1.1em; font-weight:bold;">비교연산자</span>

<table>
  <tr>
    <td>a == b</td>
    <td>a와 b가 같으면 true</td>
  </tr>
  <tr>
    <td>a === b</td>
    <td>a와 b의 내용과 자료형이 같으면 true</td>
  </tr>
  <tr>
    <td>a != b<br>
        a !== b</td>
    <td>a와 b가 다르면 true</td>
  </tr>
  <tr>
    <td>a > b</td>
    <td>a가 b보다 크면 true</td>
  </tr>
  <tr>
    <td>a < b </td>
    <td>a가 b보다 작으면 true</td>
  </tr>
  <tr>
    <td>a >= b</td>
    <td>a가 b보다 크거나 같으면 true</td>
  </tr>
  <tr>
    <td>a <= b </td>
    <td>a가 b보다 작거나 같으면 true</td>
  </tr>
</table>


<span style="font-size:1.1em; font-weight:bold;">논리연산자</span>

<table>
  <tr>
    <td>&&</td>
    <td>AND (논리곱)</td>
    <td>a && b</td>
    <td>a와 b가 모두 true면 true</td>
  </tr>
  <tr>
    <td>||</td>
    <td>OR (논리합)</td>
    <td>a || b</td>
    <td>a와 b 둘 중 하나라도 true이면 true</td>
  </tr>
  <tr>
    <td>!</td>
    <td>NOT (논리 부정)	</td>
    <td>!a = true</td>
    <td>a의 논리 값을 반전하여 a = false</td>
  </tr>
</table>


## 조건문과 반복문

<span style="font-size:1.4em; font-weight:bold;">조건문</span>

<span style="font-size:1.1em; font-weight:bold;">if문</span>

**if문**은 *if*로 시작하며 *if*와 *else* 그리고 다른 조건이 있을 경우 *else if*를 사용한다.

```js
if (a = 1) { 
  cosole.log('1 입니다.'); //a가 1이면 출력
} else if (a = 2) {
  console.log('2 입니다.'); //a가 2이면 출력
} else {
  console.log('1과 2가 아닙니다.') //a가 1과 2가 아닐 경우 출력
}
```


<span style="font-size:1.1em; font-weight:bold;">switch문</span>

**switch문**은 *switch*로 시작하며 *case*로 조건을 표현한다. 그리고 *break*를 이용하여 *case*를 명확하게 구분해준다.<br>
*default*는 모든 case 조건들이 일치하지 않을 때 실행되는 부분이며 *default*가 없을 경우 아무것도 실행하지 않는다.

```js
switch (result) {
  case (조건)1:
    // case1의 내용
    break;
  case (조건)2:
    // case2의 내용
    break;
  case (조건)3:
    // case3의 내용
    break;
  default:
    // default의 내용
    break;
}
```


<span style="font-size:1.4em; font-weight:bold;">반복문</span>

<span style="font-size:1.1em; font-weight:bold;">for문</span>

**for문***은 초기화, 조건, 증감식이 한 문장에 모두 포함되어 있으며, 조건이 *true*인 동안 반복해서 실행한다.

```js
for (let i = 0; i < 5; i++) {
    console.log(i); //0부터 4까지 출력
}
```


<span style="font-size:1.1em; font-weight:bold;">while문</span>

**while문**은 특정 조건이 *true*인 동안 계속해서 반복하며, 조건은 반복문 내부에서 변경되어야 하고, 그렇지 않으면 무한 루프가 발생할 수 있다.

```js
let i = 0;
while (i < 5) {
    console.log(i); //0부터 4까지 출력
    i++;
}
```

<span style="font-size:1.4em; font-weight:bold;">실행 흐름 제어</span>

조건문과 반복문에서 실행 흐름을 제어하는 사용되는 키워드이다.<br>
*break*는 완전히 종료시키고 밖으로 탈출한다.<br>
*continue*는 현재 반복을 끝내고 다음 반복으로 넘어가는 역할을 한다.


## 함수

**함수**란 어떤 기능을 수행 하거나 계산을 수행할 수 있도록 하는 도구이며, 함수를 통해 원하는 기능을 만들어 필요한 곳에서 사용 할 수 있다.

<span style="font-size:1.4em; font-weight:bold;">함수 선언과 호출</span>

함수를 사용하기 위해서는 먼저 함수를 선언해야한다.<br>
함수를 선언할 때에는 `function`을 사용하여 선언한다.

```js
function message(){
  console.log('Hello World');
}
```
함수를 선언했으면 이 함수를 사용하기 위해 호출해야한다.<br>
호출하는 방식은 `함수이름()`으로 호출한다.

```html
<input type = "button" value = "click" onclick = "message()">
<!--onclick이벤트에서 message함수를 호출-->
```


<span style="font-size:1.4em; font-weight:bold;">함수의 매개변수와 반환값</span>

매개변수는 함수를 선언할 때 작성하여 함수를 호출할 때 임의의 값을 함수 내부로 전달할 수 있다.<br>
함수 이름 뒤에 소괄호를 사용하여 매개변수를 작성하고 함수 호출 시 이 값을 전달하는 방식이다.<br>
매개변수를 여러 개 작성할 수 있으며 쉼표를 사용해서 작성하면 된다.

```js
function message(name){
  console.log('Hello ${name}');
}

message('Lee') // Hello Lee
```

반환값은 함수를 호출한 지점에 함수를 호출한 결과로 어떤 특정한 값이 대체되게 할 수 있으며 *return*을 사용한다.
**return문**은 반환 값을 전달하는 기능과 더불어 함수 자체를 종료하는 기능도 있다.

```js
function message() {
    return 'Hello World'; //Hello World를 반환하고 함수 종료
}

console.log(message()); // Hello World
```


<span style="font-size:1.4em; font-weight:bold;">화살표 함수 (Arrow function)</span>

기존의 함수 표현식에서 *function*을 삭제하고 인자를 받는 매개변수의 괄호`()`와 코드블록`{}` 사이에 화살표`=>` 를 넣어주면 화살표 함수(Arrow Function)다.<br>
함수 내부의 내용이 반환값만 있다면 코드블록과 *return*을 생략할 수 있다.
매개변수가 하나만 받는다면 매개변수의 괄호도 생략 가능하지만 매개변수가 없으면 생략할 수 없다.

```js
let a = function() {
    return b + c;
};

//화살표 함수를 이용
let a = () => {
    return b + c;
};
```
  

## 객체와 배열

<span style="font-size:1.4em; font-weight:bold;">객체의 선언과 사용</span>

*JavaScript*에서 객체를 선언해서 사용하는 방법은 3가지가 있다.
 -  객체 리터럴(Object Literal) 방식
 -  객체 생성자(Object Constructor) 방식
 -  함수 생성자(Function Constructor) 방식


<span style="font-size:1.1em; font-weight:bold;">객체 리터럴(Object Literal) 방식</span>

리터럴 방식은 중괄호를 사용하여 선언한다. 중괄호 안에는 속성을 추가하여 객체를 선언할 수 있다.

```js
const Animal = {
  name: "호랑이",
  age: 10,
};
console.log(Animal);
//{ name: "호랑이" , age: 10 }
```


<span style="font-size:1.1em; font-weight:bold;">객체 생성자(Object Constructor) 방식</span>

객체 생성자 방식은 `new Object()`를 먼저 선언하고 그 후에 속성을 정의한다.<br>
속성은 점을 찍어 `객체명.속성` 정의할 수 있으며, 또는 대괄호를 이용하여 `객채명["속성"]` 정의할 수 있다.

```js
const Animal = new Object();
Animal.name = "호랑이";
Animal["age"] = 10;

console.log(Animal);
//{ name: "호랑이" , age: 10 }
```


<span style="font-size:1.1em; font-weight:bold;">함수 생성자(Function Constructor) 방식</span>

함수 생성자는 **this** 키워드를 이용하여 속성을 정의한다. *this* 키워드는 자기 자신을 나타낼 때 사용하며, *Animal* 함수에서 *this*는 *Animal*을 나타낸다.

```js
function Animal(name, age) {
  this.name = name;
  this.age = age;
}

const Animal = new Animal("호랑이", 10);

console.log(Animal);
//{ name: "호랑이" , age: 10 }
```


<span style="font-size:1.1em; font-weight:bold;">속성 조회, 추가, 수정, 삭제</span>

속성 조회<br>
`console.log(Animal.name);`

추가<br>
`Animal.location = "애버랜드";`

수정<br>
`Animal.location = "어린이대공원";`

삭제<br>
`delete Animal.location;`


<span style="font-size:1.4em; font-weight:bold;">배열의 선언과 사용</span>

배열을 선언하는 방법으로 2가지가 있다.
 - `let arr1 = [];`
 - `let arr2 = new Array();`

배열 내부의 값을 요소라 하며 이 요소들은 쉼표로 구분된다.<br>
요소들에겐 각각 번호가 있고 이 번호를 인덱스라 하며 맨 앞부터 0으로 시작한다.<br>
```js
let arr1 = [[1, 2, 3], [4, 5]]
//배열 안에 배열을 넣을 수 있으며 이차원배열 이라고 한다.
```

배열 개수 구하기
```js
//먼저 계속 사용할 배열을 하나 만들어준다.
let Animal = ['사자','토끼','고양이','호랑이','코끼리'];

console.log(Animal.length);
//5

console.log(Animal.length - 1);
//4
//배열의 개수에서 1을 빼주면 마지막 요소의 인덱스가 나온다.
``` 


요소 추가
```js
let Animal = ['사자','토끼','고양이','호랑이','코끼리'];
Animal[5] = '강아지'; //인덱스로 추가

console.log(Animal);
//['사자','토끼','고양이','호랑이','코끼리','강아지']

//마지막에 요소 추가
target[target.length] = '강아지'; //마지막 요소의 인덱스가 배열 개수에서 1을 뺀 값
target.push('강아지');

//맨 앞에 요소 추가
target.unshift('강아지');
```


요소 수정
```js
let Animal = ['사자','토끼','고양이','호랑이','코끼리'];
Animal[3] = '강아지'; //인덱스로 원래 있던 값을 변경

console.log(Animal);
//['사자','토끼','고양이','강아지','코끼리']
```


요소 제거
```js
let Animal = ['사자','토끼','고양이','호랑이','코끼리'];
target.splice(2, 2); // 첫번째는 제거할 시작 인덱스, 두번째는 제거할 요소의 개수

console.log(Animal);
//['사자','토끼','코끼리']

target.pop(); //마지막 요소 제거
target.shift(); //첫번째 요소 제거

//제거 후 다른 요소 넣기
target.splice(2, 2, '코뿔소', '기린');
//['사자','토끼','코뿔소','기린','코끼리']
```


배열에서 요소 찾기
```js
let Animal = ['사자','토끼','고양이','호랑이','코끼리'];
const result = target.includes('여우');

console.log(result);
//false
//값이 있으면 true, 없으면 false

const result = target.indexOf('고양이'); //앞에서부터 주어진 인덱스 번호
//2

const result = target.lastIndexOf('호랑이'); //뒤에서부터 찾는 인덱스 번호
//1
```

기타 배열 사용
```js
let NewArray = [...Array1, ...Array2] 
//배열 합치기
NewArray = Array1.concat(Array2);
//배열 합치기

const a = [1,2,3,4,5]
a.map((item, 인덱스) => item +1);
//배열 반복(for문과 같음)    
//[2,3,4,5,6]

console.log(exArray6.filter((item) => item > 3));
//exArray6의 배열들을 item으로 하고 3보다 뒤의 배열들 호출
```

*forEach*사용
```js
const arr = [1, 2, 3, 4, 5];

arr.forEach(function(element, index) {
  console.log(`Index ${index}: ${element}`);
});

//Index 0: 1
//Index 1: 2
//Index 2: 3
//Index 3: 4
//Index 4: 5
```
*forEach* 함수는 자바스크립트 배열에 존재하는 각 요소에 대해 함수를 실행하는 메서드로, 배열을 순회하면서 특정 작업을 수행한다.<br>
*forEach*는 배열의 모든 요소에 대해 인수로 주어진 콜백 함수를 실행한다.


<span style="font-size:1.4em; font-weight:bold;">JSON</span>

<span style="font-size:1.1em; font-weight:bold;">JSON이란?</span>

*JSON*은 *JavaScript Object Notation*의 약자이다.<br>
데이터를 쉽게 교환하고 저장하기 위한 텍스트 기반의 데이터 교환 표준이다.<br>
*JSON*은 텍스트 기반이므로 다양한 프로그래밍 언어에서 데이터를 읽고 사용할 수 있다.

JSON의 형태는 `{ key : value }` 이다.<br>
여러 데이터를 나열할 때는 쉼표로 구분한다.<br>
 `{ key1 : value1, key2 : value2 }`
```js
let Animal = '{ "name":"호랑이", "age":10 }';
```

*JSON*에 데이터를 넣을때 객체는 중괄호`{}`, 배열은 대괄호 `[]`, 문자열은 따옴표`""`를 사용하고 나머지는 그냥 넣는다.
 - 객체: `{ k : { inKey : "value" } }`
 - 배열: `{ k : [1, 2, 3, 4] }`
 - 숫자: `{ k : 1 }`
 - 문자열: `{ k : "str" }`
 - 불린(boolean): `{ k : true }`
 - NULL: `{ k : null }`


<span style="font-size:1.1em; font-weight:bold;">JSON 변환하기</span>

객체를 *JSON*형식의 텍스트로 변환
```js
//JSON 문자열
let Animal = '{ "name":"호랑이", "age":10 }';

//JSON 형식의 텍스트를 객체로 변환 (파싱)
let parsingData = JSON.parse(Animal);
console.log(parsingData.name); //"호랑이"

//객체를 JSON 형식의 텍스트로 변환
let jsonStringAgain = JSON.stringify(parsingData);
console.log(jsonStringAgain); //'{ "name":"호랑이", "age":10 }'
```

