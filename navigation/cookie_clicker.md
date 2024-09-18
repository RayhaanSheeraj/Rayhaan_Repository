---
layout: page
title: Cookie Clicker
search_exclude: true
permalink: /cookieclicker/
---


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cookie Clicker</title>
    <div id="cps-count">Cookies per second: 0</div>
    <style>
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background-color: #f0f0f0;
            margin: 0;
            font-family: Arial, sans-serif;
        }
        #cookie {
            width: 200px;
            height: 200px;
            background-image:url("{{site.baseurl}}/images/cookie.png");
            background-size: cover;
            border-radius: 50%;
            cursor: pointer;
        }
        #score {
            font-size: 24px;
            margin-top: 20px;
        }
        .button {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            background-color: #6699ff;
            color: white;
        }
        .button:hover {
            background-color: #5577cc;
        }
    </style>
</head>
<body>
    <div id="cookie"></div>
    <div id="score">Cookies: 0</div>
    <div id="clicker-count">Clickers: 0</div>
    <div id="baker-count">Bakers: 0</div>
    <div id="mine-count">Cookie Mine: 0</div>
    <br>
    <br>
    <div style="font-size: 36px; font-weight: bold; color:#000000">Shop</div>
    <button class="button" onclick="buyClicker()">Buy Clicker - 25 cookies</button>
    <br>
    <button class="button" onclick="buyBaker()">Baker - 100 cookies</button>
    <br>
     <button class="button" onclick="buyMine()">Mine - 10000 cookies</button>
    <br>
    <audio id="clickSound" src="{{site.baseurl}}/audio/cookieclicking.mp3"></audio>
    <script> 
        let cps = 0;
        let score = 0;
        let clickers = 0; 
        let bakers = 0; 
        let mines = 0;
    const clickSound = document.getElementById('clickSound');
    document.getElementById('cookie').addEventListener('click', function() {
    score++;
    document.getElementById('score').innerText = 'Cookies: ' + score;
    clickSound.play();
    console.log("sound played");
});
    function buyClicker() {
    if (score >= 25) {
        score -= 25;
        clickers++; 
        document.getElementById('score').innerText = 'Cookies: ' + score;
        document.getElementById('clicker-count').innerText = 'Clickers: ' + clickers;
        cps+=1;
            document.getElementById('cps-count').innerText = 'Cookies per second: ' + cps;
        setInterval(function() {
            score++;
            document.getElementById('score').innerText = 'Cookies: ' + score;
        }, 1000);
    } else {
        alert('Not enough cookies to buy a clicker!');
    }
}
    function buyBaker() {
    if (score >= 100) {
        score -= 100;
        bakers++; 
        document.getElementById('score').innerText = 'Cookies: ' + score;
        document.getElementById('baker-count').innerText = 'Bakers: ' + bakers;
        cps+= 5;
            document.getElementById('cps-count').innerText = 'Cookies per second: ' + cps;
        setInterval(function() {
            score+= 5;
            document.getElementById('score').innerText = 'Cookies: ' + score;
        }, 1000);
    } else {
        alert('Not enough cookies to buy a baker');
    }
}
    function buyMine() {
    if (score >= 10000) {
        score -= 10000;
        mines++; 
        document.getElementById('score').innerText = 'Cookies: ' + score;
        document.getElementById('baker-count').innerText = 'Cookie Mines: ' + mines;
        cps+= 15;
            document.getElementById('cps-count').innerText = 'Cookies per second: ' + cps;
        setInterval(function() {
            score+= 15;
            document.getElementById('score').innerText = 'Cookies: ' + score;
        }, 1000);
    } else {
        alert('Not enough cookies to buy a baker');
    }
}
    
    </script>
</body>
</html>