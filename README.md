<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mobile Car Game</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
        }
        #gameCanvas {
            display: block;
            background-color: #e0e0e0;
        }
        .button {
            position: absolute;
            bottom: 20px;
            width: 100px;
            height: 50px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        .button:hover {
            background-color: #218838;
        }
        #easy { left: 20px; }
        #medium { left: 130px; }
        #hard { left: 240px; }
        #gameOver {
            display: none;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 24px;
            color: red;
            text-align: center;
        }
    </style>
</head>
<body>
    <canvas id="gameCanvas"></canvas>
    <div id="gameOver">Game Over!<br><button onclick="restartGame()">Restart</button></div>
    <button class="button" id="easy" onclick="startGame('easy')">Easy</button>
    <button class="button" id="medium" onclick="startGame('medium')">Medium</button>
    <button class="button" id="hard" onclick="startGame('hard')">Hard</button>

    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        let carX, carY;
        const carWidth = 50;
        const carHeight = 100;
        let obstacles = [];
        let speed = 2;
        let isGameOver = false;
        let gameInterval;

        function startGame(difficulty) {
            isGameOver = false;
            obstacles = [];
            carX = canvas.width / 2 - carWidth / 2;
            carY = canvas.height - carHeight - 10;

            speed = difficulty === 'easy' ? 2 : difficulty === 'medium' ? 4 : 6;

            document.getElementById('gameOver').style.display = 'none';
            clearInterval(gameInterval);
            gameInterval = setInterval(gameLoop, 20);
            createObstacle();
        }

        function gameLoop() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            drawCar();
            moveObstacles();
            checkCollision();
        }

        function drawCar() {
            ctx.fillStyle = 'blue';
            ctx.fillRect(carX, carY, carWidth, carHeight);
        }

        function createObstacle() {
            const obstacleX = Math.random() * (canvas.width - 50);
            obstacles.push({ x: obstacleX, y: 0, width: 50, height: 100 });
            setTimeout(createObstacle, 2000); // Create a new obstacle every 2 seconds
        }

        function moveObstacles() {
            obstacles.forEach(obstacle => {
                obstacle.y += speed;
                ctx.fillStyle = 'red';
                ctx.fillRect(obstacle.x, obstacle.y, obstacle.width, obstacle.height);
            });
            obstacles = obstacles.filter(obstacle => obstacle.y < canvas.height); // Remove off-screen obstacles
        }

        function checkCollision() {
            for (let obstacle of obstacles) {
                if (carX < obstacle.x + obstacle.width &&
                    carX + carWidth > obstacle.x &&
                    carY < obstacle.y + obstacle.height &&
                    carY + carHeight > obstacle.y) {
                    endGame();
                }
            }
        }

        function endGame() {
            isGameOver = true;
            clearInterval(gameInterval);
            document.getElementById('gameOver').style.display = 'block';
        }

        function restartGame() {
            startGame('easy'); // Restart in easy mode; you can change this as needed
        }

        // Move car left and right by tapping
        canvas.addEventListener('touchstart', function(event) {
            const touchX = event.touches[0].clientX; // Get touch position
            if (touchX < canvas.width / 2 && carX > 0) {
                carX -= 15; // Move left
            } else if (touchX > canvas.width / 2 && carX < (canvas.width - carWidth)) {
                carX += 15; // Move right
            }
        });

        // Resize canvas on window resize
        window.addEventListener('resize', function() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            carX = canvas.width / 2 - carWidth / 2; // Reset car position
        });
    </script>
</body>
</html>
