---
layout: page
title: Student Home 
description: Home Page
image: /images/mario_animation.png
hide: true
comments: true
---
<table>
<tbody>
    <td> 
    <a href="{{site.baseurl}}/cookieclicker">Cookie Clicker</a>
     </td>
     <td> 
    <a href="{{site.baseurl}}/my_calculator">Calculator</a>
     </td>
     <td> 
    <a href="{{site.baseurl}}/tic-tac-toe">Tic Tac Toe</a>
     </td>
     </tbody>
</table>
     
Hello, my name is Rayhaan Sheeraj, I am 15 and in 10th grade. I am taking the course AP CSP. Here you can see my journey, my projects, and my progress throughout this class.


{% assign sprite_file = site.baseurl | append: page.image %}

{% assign hash = site.data.mario_metadata %}  

{% assign pixels = 256 %}



<p id="mario" class="sprite"></p>
  

<style>
    body.light-mode {
        background-color: #f0f0f0;
        color: #000;
    }
    body.dark-mode {
        background-color: #121212;
        color: #fff;
    }
    .button {
        margin-top: 20px;
        padding: 5px 10px;
        font-size: 14px;
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

<div style="border: 1px solid white; padding: 10px;"> 
  <p>Click the button below to login:</p> 
  <button style="background-color: #6699ff !important; border-radius: 10px; color: white;">Login</button>
  <br><br>
</div> 

<div style="border: 1px solid white; padding: 10px;"> 
  <p>Click the button to learn about me:</p>
  <a href="about/" style="text-decoration: none;">
    <button style="background-color: #6699ff !important; border-radius: 10px; color: white;">About</button>
  </a>
  <br>
  <p>Click the button below to learn about the different coding languages:</p>
  <a href="https://cyberlord09.github.io/grouprepo_2025/" style="text-decoration: none;"> 
    <button style="background-color: #6699ff !important; border-radius: 10px; color: white;">Coding Languages</button> 
  </a> 
</div>

<button class="button" onclick="toggleDarkMode()">Toggle Dark/Light Mode</button>

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
