---
date: 2024-02-01 20:31:22 +0900
layout: post
title: "[JS] JavaScript를 이용한 끝말잇기 만들기"
subtitle: "JavaScript를 이용하여 끝말잇기 게임을 만들어보자."
description: JavaScript를 이용하여 끝말잇기 게임을 만들어보고 JavaScript에 대한 이해도 키우기
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

그동안 *JavaScript*의 기초를 배우면서 얻은 기술들을 이용하여 간단한 게임들을 만드려보려고 한다.<br>
간단한 게임들을 만들기위해 **Let's Get It 자바스크립트 프로그래밍** 이라는 책을 이용했다.
[![Let's Get It 자바스크립트 프로그래밍](https://shopping-phinf.pstatic.net/main_3243831/32438311618.20230927071101.jpg?type=w300)](https://search.shopping.naver.com/book/catalog/32438311618)

오늘은 책을 참고해 끝말잇기 게임을 만들어보도록 하겠다.


## HTML화면

먼저 HTML을 이용해 웹 페이지에서 보여지는 부분들을 만들어보자.

```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>끝말잇기</title>
    </head>

    <body>
        <div><span id="order">1</span>번째 참가자</div>
        <div>제시어: <span id="word"></span></div>
        <div>남은 시간: <span id="timeout">10</span></div>
        <input type="text">
        <button>입력</button>
    </body>
<html>
```
![word-relay](../assets/img/post/word-relay.jpg)

이렇게 웹 페이지의 보여지는 부분은 완성했다. 다음은 기능을 추가해보자.


## 참가자 순번 설정

다음은 참가하는 인원을 정해서 웹페이지에 순번대로 게임을 진행할 수 있도록 해보자.

```js
//프롬프트를 이용하여 참가인원 값 받기
const number = Number(prompt("몇 명이 참가합니까?"));

//$order 변수에 참가자 순번 저장
const $order = document.querySelector('#order'); 
```
먼저 웹 페이지가 시작할 때 몇 명이 참가하는지 입력받고 그 값을 `Number()`를 이용해 자료형을 변환해서 *number*변수에 넣어준다.<br>
그리고 몇번째 참가자인지 보여주는 숫자를 *$order*로 설정해준다

```js
//order변수에 $order의 텍스트를 자료형을 변환하여 저장
const order = Number($order.textContent); 
if(order + 1 > number){ 
    //참가자 순번 1번으로 바꾸기
    $order.textContent = 1; 
} else {
    //참가자 순번에서 다음 순번으로 넘어갈 때 1 더해주기
    $order.textContent = order + 1; 
}
```
밑에서 끝말잇기 기능을 만들 때 순번이 넘어갈 때 넣을 기능이다.<br>
order, 즉 참가자 순번에 해당하는 부분이 다음으로 넘어갈 때 프롬프트로 받은 number보다 클 경우 다시 1번째로 돌아가도록 설정한다.


## 끝말잇기 기능 만들기

끝말잇기의 규칙대로 끝말과 첫말이 같도록 하는 기능과 이미 말한 단어를 또 사용할 수 없도록 하는 기능을 만들어보자.

```js
//버튼의 변수 설정
const $botton = document.querySelector('button'); 

//input의 변수 설정(단어 입력 창)
const $input = document.querySelector('input'); 

//제시어 창의 변수 설정
const $word = document.querySelector('#word'); 

let words = []; //통과한 단어를 배열로 설정
let word; //제시어
let newWord; //입력단어
```
먼저 사용할 변수들을 설정해준다.

```js
//indexOf를 사용하여 통과한 단어와 입력단어를 비교
const onClickButton = () => {       
    if (words.indexOf(newWord) >= 0){ 
        alert('이미 사용한 단어입니다.');
        return;
    }
    
    //제시어가 없거나 제시어의 끝단어와 입력단어의 앞단어가 같을 경우
    if (!word || word[word.length-1] === newWord[0]) {
        //제시어에 입력값 넣기
        word = newWord; 

        //통과된 단어배열(words)에 제시어(word) 맨 뒤에 추가
        words.push(word); 

        //제시어 창($word)에 제시어 넣기(word)
        $word.textContent = word; 
    } else {
        alert('올바르지 않은 단어');  
    }
    //입력창 초기화 후 포커스
    $input.value = ''; 
    $input.focus();
}
//단어를 입력하면 실행되는 이벤트
const onInput = (event) => {
    //이벤트가 발생한 부분의 값을 입력값 변수(newWord)에 저장
    newWord = event.target.value;
}
//이벤트 리스너를 통해 이벤트가 발생하면 함수 실행
$botton.addEventListener('click', onClickButton);
$input.addEventListener('input', onInput);
```


## 추가기능 만들기

추가 기능으로 시간제한 기능과 3글자로만 가능하도록 하는 기능을 추가해보자.

```js
//입력 단어가 3글자가 아닐경우
if (newWord.length !== 3) {
    alert('3글자 단어만 가능합니다.')
    return;
}
```
먼저 3글자만 허용하는 코드로 *.length*를 이용해 3글자가 아니면 알림이 나오도록 해준다.<br>
위 코드는 `onClickButton` 함수 안에 추가를 해줘야한다.

다음은 시간제한 기능이다.
```js
//시간 초가 나오는 부분을 $timeout변수로 설정
const $timeout = document.querySelector('#timeout');
//밑에서 사용할 count와 intercalId를 변수로 설정
let count;
let intervalId;


//시간제한 함수
function timeOut() {
    //먼저 count는 10으로 설정
    count = 10;

    //intervalId가 반복되는 작업이 설정되어 있다면, 안의 코드를 실행
    if (intervalId) {
        clearInterval(intervalId); // 이전 interval 정리

    }
    //setInterval을 통해 안에있는 코드를 1초마다 실행
    intervalId = setInterval(() => {
        //시간 초가 나오는 부분을 1 감소 후 대입
        //count--가 맞지만 딜레이때문에 수정
        $timeout.textContent = --count;
        
        //만약 카운트가 0이하로 내려가면 패배자를 알려주고 새로고침
        if (count <= 0) {
            clearInterval(intervalId); // 이전 interval 정리
            alert($order.textContent + '번째 참가자 패배');
            location.reload();
        }
    }, 1000);
}
```


## 전체 정리

이렇게 추가 기능을 추가하여 끝말잇기를 완성했다. 마지막은 우리말 사전 OpenAPI를 가져와서 적용시키는 부분이지만 아직 어려운 부분이 많아 여기까지 완성을 했다.

완성 코드
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>끝말잇기</title>
    </head>

    <body>
        <div><span id="order">1</span>번째 참가자</div>
        <div>제시어: <span id="word"></span></div>
        <div>남은 시간: <span id="timeout">10</span></div>
        <input type="text">
        <button>입력</button>

        <script>
            const number = Number(prompt("몇 명이 참가합니까?"));
            const $botton = document.querySelector('button');
            const $input = document.querySelector('input');
            const $word = document.querySelector('#word');
            const $order = document.querySelector('#order');
            const $timeout = document.querySelector('#timeout');

            let words = [];
            let count;
            let intervalId;
            let word;
            let newWord;
            
            const onClickButton = () => {
                
                if (newWord.length !== 3) { 
                    alert('3글자 단어만 가능합니다.')
                    return;
                }
                if (words.indexOf(newWord) >= 0){
                    alert('이미 사용한 단어입니다.');
                    return;
                }
                
                if (!word || word[word.length-1] === newWord[0]) {
                    timeOut();
                    word = newWord;
                    words.push(word);
                    $word.textContent = word;

                    const order = Number($order.textContent);
                    if(order + 1 > number){
                        $order.textContent = 1;
                    } else {
                        $order.textContent = order + 1;
                    }
                } else {
                    alert('올바르지 않은 단어');  
                }
                $input.value = '';
                $input.focus();
            }
            const onInput = (event) => {
                newWord = event.target.value;
            }

            function timeOut() {
                count = 10;
                if (intervalId) {
                    clearInterval(intervalId);

                }
                intervalId = setInterval(() => {
                    $timeout.textContent = --count;
                    if (count <= 0) {
                        clearInterval(intervalId);
                        alert($order.textContent + '번째 참가자 패배');
                        location.reload();
                    }
                }, 1000);
            }

            $botton.addEventListener('click', onClickButton);
            $input.addEventListener('input', onInput);
        </script>   
    </body>
</html>
```