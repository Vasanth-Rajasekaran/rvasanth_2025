---
layout: post
title: Cookie Clicker
description: Play Cookie Clicker
search_exclude: true
permalink: /cookie
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cookie Clicker Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
        }
        #cookie {
            width: 200px;
            height: 200px;
            background-color: #d3a35c;
            border-radius: 50%;
            margin: 20px auto;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2em;
            cursor: pointer;
        }
        #upgrades {
            margin-top: 20px;
        }
        .upgrade {
            margin: 10px;
        }
    </style>
</head>
<body>
    <h1>Cookie Clicker Game</h1>
    <div id="cookie">🍪</div>
    <h2>Cookies: <span id="cookieCount">0</span></h2>
    <h2>Cookies per Click: <span id="cookiesPerClick">1</span></h2>
    <h2>Cookies per Second: <span id="cookiesPerSecond">0</span></h2>
    <h2>Total Cookies: <span id="totalCookies">0</span></h2>
    
    <div id="upgrades">
        <button class="upgrade" onclick="buyUpgrade(50, 'Double Clicks')">Double Clicks (Cost: 50)</button>
        <button class="upgrade" onclick="buyUpgrade(500, 'Cookie Farm')">Cookie Farm (Cost: 500)</button>
    </div>

    <script>
        let cookies = 0;
        let cookiesPerClick = 1;
        let totalCookies = 0;
        let cookiesPerSecond = 0;

        const cookieCountElem = document.getElementById("cookieCount");
        const cookiesPerClickElem = document.getElementById("cookiesPerClick");
        const totalCookiesElem = document.getElementById("totalCookies");
        const cookiesPerSecondElem = document.getElementById("cookiesPerSecond");

        document.getElementById("cookie").addEventListener("click", function() {
            cookies += cookiesPerClick;
            totalCookies += cookiesPerClick;
            updateDisplay();
        });

        function buyUpgrade(cost, type) {
            if (cookies >= cost) {
                cookies -= cost;
                if (type === 'Double Clicks') {
                    cookiesPerClick *= 2;
                } else if (type === 'Cookie Farm') {
                    cookiesPerSecond += 5;
                }
                updateDisplay();
            } else {
                alert("Not enough cookies!");
            }
        }

        function updateDisplay() {
            cookieCountElem.innerText = cookies;
            cookiesPerClickElem.innerText = cookiesPerClick;
            totalCookiesElem.innerText = totalCookies;
            cookiesPerSecondElem.innerText = cookiesPerSecond;
        }

        setInterval(function() {
            cookies += cookiesPerSecond;
            totalCookies += cookiesPerSecond;
            updateDisplay();
        }, 1000);
    </script>
</body>
</html>


