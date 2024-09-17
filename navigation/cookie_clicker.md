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
    <button class="button" onclick="resetGame()">Reset</button>
    <audio id="clickSound" src="{{site.baseurl}}/_audio/cookieclicking.mp3"></audio>
    <script> 
        let score = 0;
        const clickSound = document.getElementById('clickSound');
        document.getElementById('cookie').addEventListener('click', function() {
            score++;
            document.getElementById('score').innerText = 'Cookies: ' + score;
            clickSound.play();
        });
        function resetGame() {
            score = 0;
            document.getElementById('score').innerText = 'Cookies: ' + score;
        }
    </script>
</body>
</html>