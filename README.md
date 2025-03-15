<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Car Game</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
        }
        #gameArea {
            position: relative;
            width: 300px;
            height: 500px;
            border: 2px solid #333;
            overflow: hidden;
            background-color: #e0e0e0;
        }
        .car {
            position: absolute;
            bottom: 10px;
            left: 50%;
            transform: translateX(-50%);
            width: 50px;
            height: 100px;
            background-color: blue;
        }
        .obstacle {
            position: absolute;
            width: 50px;
            height: 100px;
            background-color: red;
        }
        .button {
            margin: 10px;
            padding: 10px 20px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .button:hover {
            background-color: #218838;
        }
        #gameOver {
            display: none;
            font-size: 24px;
            color: red;
        }
    </style>
</head>
<body>
    <h1>Car Game</h1>
    <button class="button" onclick="startGame('easy')">Easy</button>
    <button class="button" onclick="startGame('medium')">Medium</button>
    <button class="button" onclick="startGame('hard')">Hard</button>
    <div id="gameArea">
        <div class="car" id="car"></div>
        <div id="gameOver">Game Over!</div>
    </div>

    <script>
        let gameInterval;
        let obstacleInterval;
        let car;
        let gameArea;
        let gameOverText;
        let speed = 2; // Base speed for obstacles
        let isGameOver = false;

        function startGame(difficulty) {
            isGameOver = false;
            speed = difficulty === 'easy' ? 2 : difficulty === 'medium' ? 4 : 6;
            car = document.getElementById('car');
            gameArea = document.getElementById('gameArea');
            gameOverText = document.getElementById('gameOver');
            gameOverText.style.display = 'none';
            car.style.left = '125px'; // Reset car position

            clearInterval(gameInterval);
            clearInterval(obstacleInterval);
            gameInterval = setInterval(moveObstacles, 20);
            obstacleInterval = setInterval(createObstacle, 2000);
        }

        function moveObstacles() {
            const obstacles = document.querySelectorAll('.obstacle');
            obstacles.forEach(obstacle => {
                let obstacleTop = parseInt(window.getComputedStyle(obstacle).getPropertyValue('top'));
                obstacle.style.top = (obstacleTop + speed) + 'px';

                // Check for collision
                if (obstacleTop > 500) {
                    obstacle.remove(); // Remove obstacle if it goes out of view
                }

                // Collision detection
                if (isCollision(car, obstacle)) {
                    endGame();
                }
            });
        }

        function createObstacle() {
            const obstacle = document.createElement('div');
            obstacle.classList.add('obstacle');
            obstacle.style.left = Math.random() * (gameArea.clientWidth - 50) + 'px'; // Random position
            obstacle.style.top = '0px'; // Start from the top
            gameArea.appendChild(obstacle);
        }

        function isCollision(car, obstacle) {
            const carRect = car.getBoundingClientRect();
            const obstacleRect = obstacle.getBoundingClientRect();

            return !(
                carRect.top > obstacleRect.bottom ||
                carRect.bottom < obstacleRect.top ||
                carRect.right < obstacleRect.left ||
                carRect.left > obstacleRect.right
            );
        }

        function endGame() {
            isGameOver = true;
            clearInterval(gameInterval);
            clearInterval(obstacleInterval);
            gameOverText.style.display = 'block';
        }

        // Move car left and right
        document.addEventListener('keydown', (event) => {
            if (!isGameOver) {
                const carLeft = parseInt(window.getComputedStyle(car).getPropertyValue('left'));
                if (event.key === 'ArrowLeft' && carLeft > 0) {
                    car.style.left = (carLeft - 15) + 'px'; // Move left
                } else if (event.key === 'ArrowRight' && carLeft < (gameArea.clientWidth - 50)) {
                    car.style.left = (carLeft + 15) + 'px'; // Move right
                }
            }
        });
    </script>
</body>
</html>
