---
layout: page
menu: false
date: "2020-02-27 01:53:59"
title: About
description: Some description.
permalink: /about/
---
<style>
    @font-face {
        font-family: 'Cafe24Ssurround';
        src: url('https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_2105_2@1.0/Cafe24Ssurround.woff') format('woff');
        font-weight: normal;
        font-style: normal;
    }
    .text {
        font-family: 'Cafe24Ssurround'!important;
    }
    p, span {
        font-size: 18px!important;
    }
    h2, h3{
        color: #4CB7FF;
    }
    .menu {
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .tablink {
        width: 140px;
        height: 45px;
        font-family: 'Roboto', sans-serif;
        font-size: 11px;
        text-transform: uppercase;
        letter-spacing: 2.5px;
        font-weight: 500;
        color: #000;
        background-color: #fff;
        border: none;
        border-radius: 45px;
        box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.1);
        transition: all 0.3s ease 0s;
        cursor: pointer;
        outline: none;
        margin: 10px;
    }

    .tablink:hover {
        background-color: #4CB7FF;
        box-shadow: 0px 15px 20px rgba(76, 183, 255, 0.4);
        color: #fff;
        transform: translateY(-5px);
    }

    .tabcontent {
        display: none;
        padding: 20px;
        border-top: none;
    }
    .intro {
        width: 1300px;
        height: 500px;
        padding: 20px;
        background-color: #fff;
        box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.1);
        outline: none;
        margin: 0 auto;
        display: flex;
        flex-wrap: wrap;
    }
    .intro .item {
        flex-basis: 45%;
        margin: 0px;
        box-sizing: border-box;
        width: 150px;
    }
    .intro .item2 {
        flex-basis: 45%;
        margin: 0px;
        box-sizing: border-box;
        width: 300px;
    }
    .intro .item3 {
        flex-basis: 30%;
        margin: 0px;
        box-sizing: border-box;
        width: 150px;
    }
    #img {
        width: 430px;
        height: 430px;
        border-radius: 10px;
        box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.7);
        transform: rotate(-3deg);
        outline: none;
        padding: 0px;
    }
    .git:hover{
        filter: grayscale(100%) brightness(50%);
    }
    #skill {
        width: 150px;
        height: 150px;
        margin: 0;
        vertical-align: middle;
    }

    .image-container {
        position: relative;
        display: inline-block;
        width: 180px;
        height: 180px;
        overflow: hidden;
        margin: 30px;
        border-radius: 25px;
    }

    .image-container .overlay {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        height: 100%;
        width: 100%;
        opacity: 0;
        transition: .5s ease;
        background-color: black;
    }

    .image-container:hover .overlay {
        opacity: 0.8;
    }

    #skill2 {
        width: 300px;
        height: 200px;
        margin: 0;
        vertical-align: middle;
    }
    .image-container2 {
        position: relative;
        display: inline-block;
        width: 300px;
        height: 200px;
        overflow: hidden;
        margin: 30px;
        border-radius: 25px;
    }

    .image-container2 .overlay {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        height: 100%;
        width: 100%;
        opacity: 0;
        transition: .5s ease;
        background-color: black;
    }

    .image-container2:hover .overlay {
        opacity: 0.8;
    }

    .overlay .text {
        color: white;
        font-size: 20px;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        text-align: center;
    }
    #git {
        color: black!important;
    }
</style>

<div class="menu">
    <button class="tablink" onclick="openPage('Menu1', this)">PROFILE</button>
    <button class="tablink" onclick="openPage('Menu2', this)">INFO</button>
    <button class="tablink" onclick="openPage('Menu3', this)">SKILL</button>
    <button class="tablink" onclick="openPage('Menu4', this)">PROJECT</button>
</div>

<div id="Menu1" class="tabcontent">
    <div class="intro">
        <div class="item2">
            <img src="../assets/img/post/skyscraper.jpg" alt="Your Image" id ="img">
        </div>
        <div class="item" style="position: relative; bottom: 30px;">
            <h3 class="text">MY INTRODUCTION</h3><br>
            <span class="text">안녕하세요! 저는 이현규입니다.</span><br><br>
            <span class="text">웹 개발 분야에서 끊임없이 새로운 기술을 배우고, 이를 통해 자신을 계속해서 성장시켜 좋은 웹 개발자가 되고싶습니다.</span>
            <h3 class="text">MBTI : INFJ</h3><br>
            <span class="text">철저한 계획성과 높은 헌신도를 통한 업무 효율성 증가</span><br><br>
            <span class="text">뛰어난 창의력과 직관력을 이용한 뛰어난 문제해결 능력</span><br><br>
            <span class="text">타인을 이해하고 파악하는 능력을 통해 어디든 어울리는 사람</span>
        </div>
    </div>
</div>
<center>
<div id="Menu2" class="tabcontent">
    <div class="intro" style="justify-content: center;">
        <div class="item3">
            <h3 class="text">Birth</h3>
            <p class="text">2000.09</p>
        </div>
        <div class="item3">
            <h3 class="text">Phone</h3>
            <p class="text">010-9101-8806</p>
        </div>
        <div class="item3">
            <h3 class="text">Adress</h3>
            <p class="text">경기도 수원시</p>
        </div>
        <div class="item3">
            <h3 class="text">Email</h3>
            <p class="text">dlgusrb1596@naver.com</p>
        </div>
        <div class="item3">
            <h3 class="text">Major</h3>
            <p class="text">백석대학교 정보보호학 전공</p>
        </div>
        <div class="item3">
            <h3 class="text">Github</h3>
            <p class="text"><a href ="https://github.com/hkyuuu00" id = "git">hkyuuu00</a></p>
        </div>
    </div>
</div>
</center>

<div id="Menu3" class="tabcontent">
    <div class="intro">
        <center>
        <div class="image-container">
            <img src="../assets/img/profile/html.png" id="skill">
            <div class="overlay">
                <div class="text">HTML<br><br>★★★★☆</div>
            </div>
        </div>
        <div class="image-container">
            <img src="../assets/img/profile/css.png" id="skill">
            <div class="overlay">
                <div class="text">CSS<br><br>★★★★☆</div>
            </div>
        </div>
        <div class="image-container">
            <img src="../assets/img/profile/javascript.png" id="skill">
            <div class="overlay">
                <div class="text">JavaScript<br><br>★★★☆☆</div>
            </div>
        </div>
        <div class="image-container">
            <img src="../assets/img/profile/php.png" id="skill">
            <div class="overlay">
                <div class="text">PHP<br><br>★★★★☆</div>
            </div>
        </div>
        <div class="image-container">
            <img src="../assets/img/profile/mysql.png" id="skill">
            <div class="overlay">
                <div class="text">MySql<br><br>★★★★☆</div>
            </div>
        </div>
        <div class="image-container">
            <img src="../assets/img/profile/react.png" id="skill">
            <div class="overlay">
                <div class="text">React<br><br>★★☆☆☆</div>
            </div>
        </div>
        <div class="image-container">
            <img src="../assets/img/profile/node-js.png" id="skill">
            <div class="overlay">
                <div class="text">Node.js<br><br>★★☆☆☆</div>
            </div>
        </div>
        <div class="image-container">
            <img src="../assets/img/profile/jquery.png" id="skill">
            <div class="overlay">
                <div class="text">Jquery<br><br>★★☆☆☆</div>
            </div>
        </div>
        <div class="image-container">
            <img src="../assets/img/profile/python.png" id="skill">
            <div class="overlay">
                <div class="text">Python<br><br>★★★☆☆</div>
            </div>
        </div>
        <div class="image-container">
            <img src="../assets/img/profile/github.png" id="skill">
            <div class="overlay">
                <div class="text">Github<br><br>★★★☆☆</div>
            </div>
        </div>
        </center>
    </div>
</div>

<div id="Menu4" class="tabcontent">
    <center>
    <div class="intro" style="justify-content: center;">
        <div class="image-container2">
            <a href = "https://github.com/hkyuuu00/create_community"><img src="../assets/img/profile/community.png" id="skill2"></a>
            <div class="overlay">
                <div class="text">커뮤니티 게시판</div>
            </div>
        </div>
        <div class="image-container2">
            <a href = "http://lhkyuuuu00.dothome.co.kr/kt/"><img src="../assets/img/profile/kiosk.png" id="skill2"></a>
            <div class="overlay">
                <div class="text">키오스크</div>
            </div>
        </div>
        <div class="image-container2">
            <a href = "https://github.com/hkyuuu00/"><img src="../assets/img/uploads/profile.png" id="skill2"></a>
            <div class="overlay">
                <div class="text">진행중...</div>
            </div>
        </div>
    </div>
    </center>
</div>


<script>
    function openPage(pageName, elmnt) {
        var i, tabcontent, tablinks;
        tabcontent = document.getElementsByClassName("tabcontent");
        for (i = 0; i < tabcontent.length; i++) {
            tabcontent[i].style.display = "none";
        }
        tablinks = document.getElementsByClassName("tablink");
        for (i = 0; i < tablinks.length; i++) {
            tablinks[i].style.backgroundColor = "";
        }
        document.getElementById(pageName).style.display = "block";
        elmnt.style.backgroundColor = "#ccc";
    }

    document.getElementsByClassName("tablink")[0].click();
</script>