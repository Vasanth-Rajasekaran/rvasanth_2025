---
layout: post
title: Snake Game 
description: A simple Snake game using HTML, CSS, and JavaScript.
search_exclude: true
permalink: /snake
---
Use your WASD keys to play the game

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Snake Game</title>
    <style>
        body {
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
        }

        canvas {
            display: block;
            background-color: #000;
            margin: 50px auto;
            border: 10px solid darkblue; /* Dark blue border */
            border-radius: 10px;
        }
    </style>
</head>
<body>

    <canvas id="snakeGame" width="400" height="400"></canvas>

    <script>
        const canvas = document.getElementById('snakeGame');
        const ctx = canvas.getContext('2d');

        const box = 20;
        let snake = [{ x: 9 * box, y: 10 * box }];
        let food = {
            x: Math.floor(Math.random() * 19) * box,
            y: Math.floor(Math.random() * 19) * box
        };
        let score = 0;
        let direction = null;
        let directionChanged = false;  // Flag to prevent multiple direction changes per tick

        // Modify the event listener to use 'WASD' keys
        document.addEventListener('keydown', changeDirection);

        function changeDirection(event) {
            const key = event.keyCode;
            if (!directionChanged) {  // Allow direction change only if it hasn't changed in this tick
                if (key === 65 && direction !== 'RIGHT') { // 'A' for left
                    direction = 'LEFT';
                } else if (key === 87 && direction !== 'DOWN') { // 'W' for up
                    direction = 'UP';
                } else if (key === 68 && direction !== 'LEFT') { // 'D' for right
                    direction = 'RIGHT';
                } else if (key === 83 && direction !== 'UP') { // 'S' for down
                    direction = 'DOWN';
                }
                directionChanged = true;  // Prevent further changes until next tick
            }
        }

        function collision(newHead, snakeArray) {
            for (let i = 0; i < snakeArray.length; i++) {
                if (newHead.x === snakeArray[i].x && newHead.y === snakeArray[i].y) {
                    return true;
                }
            }
            return false;
        }

        function drawGame() {
            // Draw background
            ctx.fillStyle = '#000';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            // Draw snake
            for (let i = 0; i < snake.length; i++) {
                ctx.fillStyle = i === 0 ? 'green' : 'white';
                ctx.fillRect(snake[i].x, snake[i].y, box, box);
                ctx.strokeStyle = '#000';
                ctx.strokeRect(snake[i].x, snake[i].y, box, box);
            }

            // Draw food
            ctx.fillStyle = 'red';
            ctx.fillRect(food.x, food.y, box, box);

            // Get snake's head position
            let snakeX = snake[0].x;
            let snakeY = snake[0].y;

            // Move snake's head
            if (direction === 'LEFT') snakeX -= box;
            if (direction === 'RIGHT') snakeX += box;
            if (direction === 'UP') snakeY -= box;
            if (direction === 'DOWN') snakeY += box;

            // Check if the snake ate the food
            if (snakeX === food.x && snakeY === food.y) {
                score++;
                food = {
                    x: Math.floor(Math.random() * 19) * box,
                    y: Math.floor(Math.random() * 19) * box
                };
            } else {
                snake.pop(); // Remove the tail of the snake
            }

            // Create new head for the snake
            let newHead = { x: snakeX, y: snakeY };

            // Check for collisions with the walls or itself
            if (
                snakeX < 0 || snakeX >= canvas.width ||
                snakeY < 0 || snakeY >= canvas.height ||
                collision(newHead, snake)
            ) {
                clearInterval(game);
                alert('Game Over! Your score was: ' + score);
                location.reload();  // Reloads the page to restart the game
            }

            snake.unshift(newHead);  // Adds the new head to the beginning of the snake array

            directionChanged = false;  // Reset flag to allow direction change in the next tick
        }

        let game = setInterval(drawGame, 100);
    </script>

</body>
</html>
