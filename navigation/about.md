---
layout: page
title: About Rayhaan Sheeraj
permalink: /about/
---

Hello, my name is Rayhaan Sheeraj and I'm in 10th grade. 

Some of my favorite hobbies are playing video games and hanging out with friends. 

My favorite video game is Spiderman PS4 and Minecraft. I enjoy watching Marvel movies, playing the electrical guitar, and swimming. 

The reason I joined this class was to improve my coding skills and I hope to become a much better coder by the end of this year. 😀

<center>
<div class="border">
    <img alt="AboutRayhaanSheeraj" src="{{site.baseurl}}/images/RayhaanHobbies.png" width="700" height="520">
</div>
</center>

<button class="button" onclick="toggleDarkMode()">Toggle Dark/Light Mode</button>

<style>
    .border {
        border: 20px solid #000; 
        display: inline-block;
        box-sizing: border-box; 
    }
    .border img {
        display: block; 
    }


    body.dark-mode {
        background-color: #121212;
        color: #fff; 
    }

    body.dark-mode .border {
        border: 20px solid #fff; 
    }
</style>

<script>

    function toggleDarkMode() {
        document.body.classList.toggle('dark-mode');
        document.body.classList.toggle('light-mode');
        const isDarkMode = document.body.classList.contains('dark-mode');
        localStorage.setItem('darkMode', isDarkMode);
    }


    const savedDarkMode = localStorage.getItem('darkMode');
    if (savedDarkMode === 'true') {
        document.body.classList.add('dark-mode');
    } else {
        document.body.classList.add('light-mode');
    }
</script>
