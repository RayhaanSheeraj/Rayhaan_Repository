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
         #game-container {
            display: flex;
            align-items: flex-start; /* Align items at the top */
        }
        cookie-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-right: 40px; /* Add space between the cookie and the shop */
        }
        #cookie {
            width: 400px;
            height: 400px;
            background-image:url("{{site.baseurl}}/images/cookie.png");
            background-size: cover;
            border-radius: 50%;
            cursor: pointer;
        }
        #score {
            font-size: 24px;
            margin-top: 20px;
        }
        #shop {
            display: flex;
            flex-direction: column;
            align-items: flex-start; 
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
    <details>
    <summary><div id = "shop" style="font-size: 36px; font-weight: bold; color:#000000">Shop</div></summary>
    <button class="button" onclick="buyClicker()">Buy Clicker - 25 cookies</button>
    <br>
    <button class="button" onclick="buyBaker()">Baker - 100 cookies</button>
    <br>
     <button class="button" onclick="buyMine()">Cookie Mine - 10000 cookies</button>
    <br> 
    <button class="button" onclick="buyMultiplier()">Cursor Multiplier - 50000 cookies</button>
    </details>
    <style>
    details summary {
        cursor: pointer;
        font-size: 36px;
        font-weight: bold;
        color: #000000;
        position: relative;
        padding-right: 20px;
    }
    /* Adding the arrow symbol */
    details summary::after {
        content: '\25BC'; /* Downward arrow symbol */
        position: absolute;
        right: 0;
        font-size: 24px;
        transition: transform 0.3s ease;
    }
    /* Rotate the arrow when the details are opened */
    details[open] summary::after {
        transform: rotate(180deg); /* Rotate to point upwards */
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
    <audio id="clickSound" src="{{site.baseurl}}/audio/cookieclicking.mp3"></audio>
    <script> 
        let cps = 0;
        let score = 0;
        let clickers = 0; 
        let bakers = 0; 
        let mines = 0;
        let click_multi = 1;
    const clickSound = document.getElementById('clickSound');
    document.getElementById('cookie').addEventListener('click', function() {
    score += click_multi;
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
        document.getElementById('mine-count').innerText = 'Cookie Mines: ' + mines;
        cps+= 15;
            document.getElementById('cps-count').innerText = 'Cookies per second: ' + cps;
        setInterval(function() {
            score+= 15;
            document.getElementById('score').innerText = 'Cookies: ' + score;
        }, 1000);
    } else {
        alert('Not enough cookies to buy a cookie mine');
    }
}
    function buyMultiplier() {
    if (score >= 50000) {
        score -= 50000;
        click_multi *= 2;
        document.getElementById('score').innerText = 'Cookies: ' + score;
                alert('Multiplier purchased! Now you gain ' + click_multi + ' cookies per click!');
    } else {
        alert('Not enough cookies to buy a multiplier');
    }
}
    </script>
</body>
</html>