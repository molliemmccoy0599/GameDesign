# GameDesign
Game design for "My Pal" interactive pet game

## Code: 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Virtual Pet</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }

        .game-container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            width: 300px;
        }

        .header {
            text-align: center;
            margin-bottom: 20px;
        }

        .cat-container {
            width: 200px;
            height: 200px;
            position: relative;
            margin: 0 auto;
        }

        .cat-body {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            width: 120px;
            height: 100px;
            background: #000000;
            border: 2px solid #333333;
            border-radius: 30px;
        }

        .cat-head {
            position: absolute;
            bottom: 80px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 90px;
            background: #000000;
            border: 2px solid #333333;
            border-radius: 50%;
        }

        .ear {
            position: absolute;
            width: 30px;
            height: 30px;
            background: #000000;
            border: 2px solid #333333;
            transform: rotate(45deg);
        }

        .ear-left {
            top: -15px;
            left: 10px;
        }

        .ear-right {
            top: -15px;
            right: 10px;
        }

        .inner-ear {
            position: absolute;
            inset: 5px;
            background: #666666;
            border-radius: 2px;
        }

        .eye {
            position: absolute;
            width: 15px;
            height: 15px;
            background: #333333;
            border-radius: 50%;
            top: 35px;
        }

        .eye-left {
            left: 25px;
        }

        .eye-right {
            right: 25px;
        }

        .eye-shine {
            position: absolute;
            width: 5px;
            height: 5px;
            background: white;
            border-radius: 50%;
            top: 2px;
            left: 2px;
        }

        .nose {
            position: absolute;
            width: 8px;
            height: 8px;
            background: #666666;
            border-radius: 50%;
            top: 55px;
            left: 50%;
            transform: translateX(-50%);
        }

        .mouth {
            position: absolute;
            width: 20px;
            height: 10px;
            border-bottom: 2px solid #333333;
            border-radius: 50%;
            top: 65px;
            left: 50%;
            transform: translateX(-50%);
        }

        .paw {
            position: absolute;
            width: 25px;
            height: 25px;
            background: #000000;
            border: 2px solid #333333;
            border-radius: 50%;
            bottom: 0;
        }

        .paw-left {
            left: 20px;
        }

        .paw-right {
            right: 20px;
        }

        .tail {
            position: absolute;
            width: 10px;
            height: 50px;
            background: #000000;
            border: 2px solid #333333;
            border-radius: 20px;
            bottom: 40px;
            right: 0;
            transform: rotate(30deg);
        }

        .stat-container {
            display: flex;
            align-items: center;
            gap: 10px;
            margin: 10px 0;
        }

        .stat-label {
            font-size: 20px;
            min-width: 30px;
        }

        .stat-bar {
            width: 100%;
            height: 20px;
            background: #eee;
            border-radius: 10px;
            overflow: hidden;
        }

        .stat-fill {
            height: 100%;
            width: 50%;
            transition: width 0.5s, background-color 0.5s;
        }

        .happiness-fill {
            background: #ff69b4;
        }

        .health-fill {
            background: #4169e1;
        }

        .flash {
            background: #4CAF50 !important;
            filter: brightness(1.2);
        }

        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }

        .action-btn {
            width: 50px;
            height: 50px;
            border: none;
            border-radius: 50%;
            background: #f0f0f0;
            cursor: pointer;
            transition: background 0.3s;
            font-size: 20px;
        }

        .action-btn:hover {
            background: #e0e0e0;
        }

        .message {
            text-align: center;
            margin: 10px 0;
            min-height: 20px;
        }

        .start-screen {
            text-align: center;
            max-width: 200px;
            margin: 0 auto;
        }

        .start-screen input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
            text-align: center;
        }

        .start-screen button {
            padding: 10px 20px;
            border: none;
            border-radius: 20px;
            background: #f0f0f0;
            cursor: pointer;
            margin-top: 10px;
        }

        .blush {
            position: absolute;
            width: 15px;
            height: 8px;
            background: #444444;
            border-radius: 50%;
            opacity: 0.6;
            top: 45px;
        }

        .blush-left {
            left: 15px;
        }

        .blush-right {
            right: 15px;
        }

        .hidden {
            display: none;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
    </style>
</head>
<body>
    <div class="game-container">
        <div id="startScreen" class="start-screen">
            <div class="cat-container">
                <div class="cat-body">
                    <div class="cat-head">
                        <div class="ear ear-left"><div class="inner-ear"></div></div>
                        <div class="ear ear-right"><div class="inner-ear"></div></div>
                        <div class="eye eye-left"><div class="eye-shine"></div></div>
                        <div class="eye eye-right"><div class="eye-shine"></div></div>
                        <div class="nose"></div>
                        <div class="mouth"></div>
                        <div class="blush blush-left hidden"></div>
                        <div class="blush blush-right hidden"></div>
                    </div>
                    <div class="paw paw-left"></div>
                    <div class="paw paw-right"></div>
                </div>
                <div class="tail"></div>
            </div>
            <input type="text" id="petName" placeholder="Name your pet">
            <button onclick="startGame()">Start</button>
        </div>

        <div id="gameScreen" class="hidden">
            <div class="header">
                <h1>My Pal</h1>
                <div id="name"></div>
            </div>

            <div class="cat-container">
                <div class="cat-body">
                    <div class="cat-head">
                        <div class="ear ear-left"><div class="inner-ear"></div></div>
                        <div class="ear ear-right"><div class="inner-ear"></div></div>
                        <div class="eye eye-left"><div class="eye-shine"></div></div>
                        <div class="eye eye-right"><div class="eye-shine"></div></div>
                        <div class="nose"></div>
                        <div class="mouth"></div>
                        <div class="blush blush-left hidden"></div>
                        <div class="blush blush-right hidden"></div>
                    </div>
                    <div class="paw paw-left"></div>
                    <div class="paw paw-right"></div>
                </div>
                <div class="tail"></div>
            </div>

            <div class="message" id="message"></div>

            <div class="stat-container">
                <div class="stat-label">❤️</div>
                <div class="stat-bar">
                    <div id="happinessBar" class="stat-fill happiness-fill"></div>
                </div>
            </div>
            <div class="stat-container">
                <div class="stat-label">💗</div>
                <div class="stat-bar">
                    <div id="healthBar" class="stat-fill health-fill"></div>
                </div>
            </div>

            <div class="buttons">
                <button class="action-btn" onclick="feed()">🐟</button>
                <button class="action-btn" onclick="water()">💧</button>
                <button class="action-btn" onclick="brush()">✨</button>
            </div>
        </div>
    </div>

    <script>
        let stats = {
            happiness: 50,
            health: 50,
            lastFed: Date.now(),
            lastWatered: Date.now()
        };

        function startGame() {
            const name = document.getElementById('petName').value || 'My Pet';
            document.getElementById('startScreen').classList.add('hidden');
            document.getElementById('gameScreen').classList.remove('hidden');
            document.getElementById('name').textContent = name;
            updateStats();
            startStatDecay();
        }

        function updateStats() {
            document.getElementById('happinessBar').style.width = `${stats.happiness}%`;
            document.getElementById('healthBar').style.width = `${stats.health}%`;
            updateMood();
        }

        function updateMood() {
            const blushLeft = document.querySelector('#gameScreen .blush-left');
            const blushRight = document.querySelector('#gameScreen .blush-right');
            const mouth = document.querySelector('#gameScreen .mouth');
            
            if (stats.happiness > 80 && stats.health > 80) {
                blushLeft.classList.remove('hidden');
                blushRight.classList.remove('hidden');
                mouth.style.borderBottom = '2px solid #333333';
                mouth.style.borderTop = 'none';
            } else if (stats.happiness < 20 || stats.health < 20) {
                blushLeft.classList.add('hidden');
                blushRight.classList.add('hidden');
                mouth.style.borderBottom = 'none';
                mouth.style.borderTop = '2px solid #333333';
            } else {
                blushLeft.classList.add('hidden');
                blushRight.classList.add('hidden');
                mouth.style.borderBottom = '2px solid #333333';
                mouth.style.borderTop = 'none';
            }
        }

        function flashBar(barId) {
            const bar = document.getElementById(barId);
            bar.classList.add('flash');
            setTimeout(() => bar.classList.remove('flash'), 1000);
        }

        function showMessage(text) {
            const messageEl = document.getElementById('message');
            messageEl.textContent = text;
            setTimeout(() => messageEl.textContent = '', 3000);
        }

        function feed() {
            if (Date.now() - stats.lastFed < 5000) {
                showMessage('Mrrp! Still eating! 🐱');
                return;
            }
            
            stats.happiness = Math.min(100, stats.happiness + 30);
            stats.health = Math.min(100, stats.health + 20);
            stats.lastFed = Date.now();
            
            flashBar('happinessBar');
            flashBar('healthBar');
            showMessage('Purrrr! Thank you! 😺');
            updateStats();
        }

        function water() {
            if (Date.now() - stats.lastWatered < 5000) {
                showMessage('*tiny meow* Not thirsty! 💖');
                return;
            }
            
            stats.health = Math.min(100, stats.health + 25);
            stats.happiness = Math.min(100, stats.happiness + 15);
            stats.lastWatered = Date.now();
            
            flashBar('healthBar');
            flashBar('happinessBar');
            showMessage('*happy sips* Meow! 💦');
            updateStats();
        }

        function brush() {
            stats.happiness = Math.min(100, stats.happiness + 25);
            stats.health = Math.min(100, stats.health + 10);
            
            flashBar('happinessBar');
            flashBar('healthBar');
            showMessage('Purrrrrrr! 💝');
            updateStats();
        }

        function startStatDecay() {
            setInterval(() => {
                stats.happiness = Math.max(0, stats.happiness - 0.2);
                stats.health = Math.max(0, stats.health - 0.1);
                updateStats();
            }, 3000);
        }
    </script>
</body>
</html>

Here is my code in Safari:

https://github.com/user-attachments/assets/55d451b5-7397-4db5-81c2-218f7e3f5f3a



## Overview
For my project I wanted to think about games I tend to like. I am not a huge gamer by any means and I often choose more "comfy" or "cozy" games either that or word search so I wanted to make almost like a little Tamagotchi so I made this little cat. It looks more like a mouse but you can feed it, give it a name, give it water, and brush it to boost the animals health and happiness. I based the model off of a cat I used to live with and found this to be really fun. I am still struggling to put full code in to Github and have it show up in the way I think it is supposed to but I am working on it.


## Users
People that do not have a pet or cannot have one do to a living situation. A virtual pet is a great offering and can be a great companion. 

## Learnings 
I upgraded my Claude.ai so it was able to run a stronger line of code on this assignment. I also just decided to have fun with this and I found that made the process a little easier. When I took out the mental component of being a base coder as well I was able to see my self as a mini problem solver and director rather than just blatant base code and I really enjoyed that. I also learned that like humans Claude.ai can make mistakes and so correctly them and noticing when it drops a certain line is crucial to keeping the code and Claude.ai running smoothly. 
