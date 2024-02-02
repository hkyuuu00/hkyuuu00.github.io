---
date: 2024-02-02 23:30:12 +0900
layout: post
title: "[JS] JavaScript를 이용한 계산기 만들기"
subtitle: "JavaScript를 이용하여 계산기를 만들어보자."
description: JavaScript를 이용하여 계산기를 만들어보고 JavaScript에 대한 이해도 키우기
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


## 개요

오늘은 어제와 같이 *JavaScript*를 이용하여 간단한 프로그램을 만들어봤다.<br>
계산기를 만들기위해 **Let's Get It 자바스크립트 프로그래밍** 이라는 책을 이용했다.
[![Let's Get It 자바스크립트 프로그래밍](https://shopping-phinf.pstatic.net/main_3243831/32438311618.20230927071101.jpg?type=w300)](https://search.shopping.naver.com/book/catalog/32438311618)

오늘은 책을 참고해 계산기를 만들어보도록 하겠다.<br>
먼저 계산기의 기능으로 한번의 계산 뿐 아니라 여러 연산을 한번에 하도록하고, 계산 값을 가지고 계속해서 계산을 할 수 있도록했다.

## HTML화면

계산기를 만들기위해 먼저 *HTML*을 이용해서 계산기 화면을 만들어보자.

```html
<!DOCTYPE html>
<head>
    <meta charset="utf-8">
    <title>계산기</title>
    <style>
        * { box-sizing: border-box}
        #result { width: 180px; height: 50px; margin: 5px; text-align: right }
        #operator { width: 50px; height: 50px; margin: 5px; text-align: center; font-size: 18px; }
        button { width: 50px; height: 50px; margin: 5px }
    </style>
</head>

<!--계산기버튼구현-->
<body>
    <input readonly id="operator"> <!--readonly는 읽기 전용-->
    <input readonly type="number" id="result">
    <div class="row">
        <button id="num-1">1</button>
        <button id="num-2">2</button>
        <button id="num-3">3</button>
        <button id="plus">+</button>
    </div>
    <div class="row">
        <button id="num-4">4</button>
        <button id="num-5">5</button>
        <button id="num-6">6</button>
        <button id="minus"><b>-</b></button>
    </div>
    <div class="row">
        <button id="num-7">7</button>
        <button id="num-8">8</button>
        <button id="num-9">9</button>
        <button id="divide"><b>÷</b></button>
    </div>
    <div class="row">
        <button id="clear">C</button>
        <button id="num-0">0</button>
        <button id="calculate">=</button>
        <button id="multiply">x</button>
    </div>

    <script src="./calculator.js"></script>
</body>
```
![word-relay](../assets/img/post/calculator.jpg)

위의 코드처럼 *HTML*파일과 *JS*파일을 따로 만들어 사용했다.


## 숫자버튼 클릭

숫자버튼을 클릭했을 때 숫자가 *$result*창에 나오도록 하자.

```js
let numOne = '';    //첫번째 입력 숫자
let operator = '';  //연산자
let numTwo = '';    //두번째 입력 숫자

//연산자 창
const $operator = document.querySelector('#operator');

//숫자 창
const $result = document.querySelector('#result');
```
먼저 필요한 변수들을 생성해줬다.<br>
다음은 이벤트 리스너를 사용하여 숫자가 출력하도록 하자.

```js
//id가 num-0인 부분을 선택해주고 이벤트를 설정
document.querySelector('#num-0').addEventListener('click',() => {
    //연산자가 있을 경우
    if (operator) {
        //두번째 입력 숫자에 붙히기
        numTwo += '0';
    } else {
        //첫번째 입력 숫자에 붙히기
        numOne += '0';
    }
    //숫자 창($result)에 0을 붙혀서 넣기
    $result.value += '0';
});
document.querySelector('#num-1').addEventListener('click',() => {
    if (operator) {
        numTwo += '1';
    } else {
        numOne += '1';
    }
    $result.value += '1';
});
...
```
위의 코드가 0부터 9까지 총 10개의 코드가 나열된다. 하지만 이것을 반복문을 사용하고 함수를 사용하여 짧게 만들어보자.

먼저 함수를 만들어 반복되는 *if*문을 줄이자.
```js
const onClickNumber = (event) => {
    if (!operator) { 
        //event.target.textContent를 사용해 버튼이 눌린 부분의 텍스트를 가져오기
        numOne += event.target.textContent;
    } else {
        numTwo += event.target.textContent;
    }
    $result.value += event.target.textContent;
};
```

다음은 *for*문을 사용하여 이벤트 리스너를 줄이자.
```js
for(let i=0; i<=9; i++){
    //템플릿 리터럴을 사용하여 i를 반복
    document.querySelector(`#num-${i}`).addEventListener('click', onClickNumber); 
};
```

이제 숫자를 입력해보면 숫자가 입력된다. 하지만 계산기이기에 여러 기능을 추가해야한다.<br>
 1. 계산이 끝나고 다음 계산을 할 때 숫자를 입력하면 전의 결과 지우기
 2. 첫번째 숫자 입력 후 연산자를 누르고 두번째 숫자를 입력할 때 첫번째 숫자를 창에서 지우기
```js
const onClickNumber = (event) => {
    if (!operator) {
        //1. 첫번째 숫자를 입력할 때 result값 지우기
        if(!numOne) { 
            $result.value = '';
        }
        numOne += event.target.textContent;
        $result.value += event.target.textContent;
        //if문을 줄이기 위해 else를 쓰지않고 return으로 종료 후 탈출
        return;
    }
    
    //2. numTwo가 비어있다면 true, 두번째 숫자를 처음입력할 때 창 비우기
    if(!numTwo) { 
            $result.value = '';
    }
    numTwo += event.target.textContent;
    $result.value += event.target.textContent;
};
```


## 연산자 버튼 클릭

다음은 연산자 버튼을 클릭했을 때 작동하는 기능을 넣어보자.<br>
먼저 연산자를 계산하는 함수를 만들어보겠다.
```js
//함수를 선언하고 함수에 매개변수 numOne, operator, numTwo를 받기
const evaluation = (numOne, operator, numTwo) => {
    //결과 변수 생성
    let result;
    //operator 값은 연산자 버튼 클릭 이벤트에서 설정
    switch (operator){
        case '+':
            //parseInt는 안에있는 값을 정수로 변환
            //(+)연산자는 문자열을 이어붙힐때도 사용하기에 parseInt를 사용
            result = parseInt(numOne) + parseInt(numTwo); 
            break;
        case '-':
            result = numOne - numTwo;
            break;
        case 'x':
            result = numOne * numTwo;
            break;
        case '÷':
            result = numOne / numTwo;
            break;
        default:
            break;
    }
    return result;
}
```
계산하는 함수를 만들어주고 계산할 때 이 함수를 사용해주자

다음은 연산자 버튼을 클릭했을 때 작동하는 함수를 만들어주자.
```js
const onClickOperator = (event) => {
    //첫번째 입력 숫자도 없고 결과창도 없을 때
    if (!numOne && !$result.value) { 
        alert('숫자를 먼저 입력하세요.');
        return;
    }
    //operator변수에 클릭이벤트가 발생한 부분의 텍스트 넣어주기
    operator = event.target.textContent;
    //연산자 창($operator)에 클릭이벤트가 발생한 부분의 텍스트 넣어주기
    $operator.value = event.target.textContent;
};
```

연산을 여러 번 할 때, 연속 연산을 할 때의 기능도 넣어주자.
```js
//두번째 입력 숫자가 있을 때(연산을 여러 번 할 때)
if (numTwo) {
    //eval을 사용할 수 있지만 위험하기에 계산하는 함수인 evaluation 사용
    //연산 값을 numOne에 저장하기 
    numOne = evaluation(numOne,operator,numTwo); 
    //numOne을 결과창에 띄우기
    $result.value = numOne;
    //다음 연산을 위해 numTwo와 operator 비워주기 
    operator = '';
    numTwo = '';
}

//numOne의 입력 값이 없을경우(연속 연산을 할 때)
if(!numOne){
    numOne = $result.value;
}
```

다음은 이벤트 리스너를 사용해 함수를 작동시키도록 하겠다.<br>
이번에도 4번의 이벤트 리스너를 줄여보도록 하자.
```js
//forEach 메소드를 사용하여 배열의 각 요소에 대해 괄호 안의 함수를 실행
['plus','minus','divide','multiply'].forEach((item) => { 
    document.querySelector(`#${item}`).addEventListener('click', onClickOperator);
});
```


## 이퀄 버튼과 클리어 버튼 클릭

이퀄 버튼은 입력 숫자들을 계산하여 숫자 창에 결과 값을 나타내주는 버튼이다.
```js
//이퀄 클릭 이벤트 설정
document.querySelector('#calculate').addEventListener('click', () =>{
    //numOne이 있을 경우
    if (numOne) {
        //evaluation 함수로 numOne, operator, numTwo를 계산하여 결과창에 내보내기
        $result.value = evaluation(numOne, operator, numTwo);

        //계산 후 result값 빼고 다 지우기
        numOne = ''; 
        operator = '';
        numTwo = '';
        $operator.value = '';
    } else {
        alert('숫자를 먼저 입력하세요.');
    }
});
```

클리어 버튼은 저장된 모든 변수의 값을 다 지워버리는 버튼이다.
```js
//클리어 버튼 클릭 이벤트 설정
document.querySelector('#clear').addEventListener('click', () => {
    numOne = '';
    operator = '';
    numTwo = '';
    $operator.value = '';
    $result.value = '';
});
```


## 전체 정리

계산기를 작동해보면 문제없이 잘 돌아가며 연산을 여러 번 하거나 연속으로 연산을 하는 기능도 잘 돌아간다.

*calculator.js* 전체코드
```js
let numOne = '';
let operator = '';
let numTwo = '';
const $operator = document.querySelector('#operator');
const $result = document.querySelector('#result');

//숫자 클릭 이벤트 함수
const onClickNumber = (event) => {
    if (!operator) { 
        if(!numOne) {
            $result.value = '';
        }
        numOne += event.target.textContent;
        $result.value += event.target.textContent;
        return;
    }
    
    if(!numTwo) { 
            $result.value = '';
    }
    numTwo += event.target.textContent;
    $result.value += event.target.textContent;
};

//숫자 클릭 이벤트 설정
for(let i=0; i<=9; i++){
    document.querySelector(`#num-${i}`).addEventListener('click', onClickNumber);
};

//연산자 계산 함수 생성
const evaluation = (numOne, operator, numTwo) => {
    let result;
    switch (operator){
        case '+':
            result = parseInt(numOne) + parseInt(numTwo);
            break;
        case '-':
            result = numOne - numTwo;
            break;
        case 'x':
            result = numOne * numTwo;
            break;
        case '÷':
            result = numOne / numTwo;
            break;
        default:
            break;
    }
    return result;
}

//연산자 클릭 이벤트 함수
const onClickOperator = (event) => {
    if (!numOne && !$result.value) {
        alert('숫자를 먼저 입력하세요.');
        return;
    }
    if (numTwo) {
        numOne = evaluation(numOne,operator,numTwo);
        $result.value = numOne;
        operator = '';
        numTwo = '';
    }
    operator = event.target.textContent;
    $operator.value = event.target.textContent;
    if(!numOne){
        numOne = $result.value;
    }
};

//연산자 클릭 이벤트 설정
['plus','minus','divide','multiply'].forEach((item) => { 
    document.querySelector(`#${item}`).addEventListener('click', onClickOperator);
});

//이퀄 클릭 이벤트 설정
document.querySelector('#calculate').addEventListener('click', () =>{
    if (numOne) {
        $result.value = evaluation(numOne, operator, numTwo);
        numOne = ''; 
        operator = '';
        numTwo = '';
        $operator.value = '';
    } else {
        alert('숫자를 먼저 입력하세요.');
    }
});

//클리어 버튼 클릭 이벤트 설정
document.querySelector('#clear').addEventListener('click', () => {
    numOne = '';
    operator = '';
    numTwo = '';
    $operator.value = '';
    $result.value = '';
});
```