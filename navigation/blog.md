---
layout: blogs
title: Blogs
search_exclude: true
permalink: /blogs/
---

<h1>Welcome to My Blogs</h1>
<p>Here you can find all my latest blogs and posts!</p>

<button class="button" onclick="toggleDarkMode()">Toggle Dark/Light Mode</button>

<style>

    body.dark-mode {
        background-color: #121212;
        color: #fff; 
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
