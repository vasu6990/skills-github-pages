<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flappy Bird Clone</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #70c5ce; /* Sky color */
        }
        #gameCanvas {
            display: block;
            background-color: #70c5ce; /* Sky color */
            margin: 0 auto;
            position: relative;
        }
        .bird {
            position: absolute;
            width: 40px;
            height: 40px;
            background-color: yellow; /* Bird color */
            border-radius: 50%; /* Make it round */
        }
        .pipe {
            position: absolute;
            background-color: green; /* Pipe color */
        }
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
    <div id="gameOver">Game Over!<br><button onclick="restartGame()">Restart</button></div>
    <canvas id="gameCanvas" width="400" height="600"></canvas>

    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');

        let birdY = canvas.height / 2;
        let birdVelocity = 0;
        const gravity = 0.5;
        const jump = -10;
        const birdWidth = 40;
        const birdHeight = 40;
        let pipes = [];
        let pipeWidth = 50;
        let pipeGap = 150;
        let frame = 0;
        let score = 0;
        let isGameOver = false;

        function drawBird() {
            ctx.fillStyle = 'yellow';
            ctx.fillRect(50, birdY, birdWidth, birdHeight);
        }

        function drawPipes() {
            ctx.fillStyle = 'green';
            pipes.forEach(pipe => {
                ctx.fillRect(pipe.x, 0, pipeWidth, pipe.top);
                ctx.fillRect(pipe.x, canvas.height - pipe.bottom, pipeWidth, pipe.bottom);
            });
        }

        function updatePipes() {
            if (frame % 90 === 0) { // Create a new pipe every 90 frames
                const top = Math.random() * (canvas.height - pipeGap - 20) + 20;
                const bottom = canvas.height - top - pipeGap;
                pipes.push({ x: canvas.width, top: top, bottom: bottom });
            }

            pipes.forEach(pipe => {
                pipe.x -= 2; // Move pipes to the left
            });

            // Remove off-screen pipes
            if (pipes.length && pipes[0].x < -pipeWidth) {
                pipes.shift();
                score++;
            }
        }

        function checkCollision() {
            if (birdY + birdHeight > canvas.height || birdY < 0) {
                endGame();
            }

            pipes.forEach(pipe => {
                if (
                    50 < pipe.x + pipeWidth &&
                    50 + birdWidth > pipe.x &&
                    (birdY < pipe.top || birdY + birdHeight > canvas.height - pipe.bottom)
                ) {
                    endGame();
                }
            });
        }

        function endGame() {
            isGameOver = true;
            document.getElementById('gameOver').style.display = 'block';
        }

        function restartGame() {
            birdY = canvas.height / 2;
            birdVelocity = 0;
            pipes = [];
            frame = 0;
            score = 0;
            isGameOver = false;
            document.getElementById('gameOver').style.display = 'none';
            gameLoop();
        }

        function gameLoop() {
            if (isGameOver) return;

            ctx.clearRect(0, 0, canvas.width, canvas.height);
            birdVelocity += gravity;
            birdY += birdVelocity;

            drawBird();
            updatePipes();
            drawPipes();
            checkCollision();

            frame++;
            requestAnimationFrame(gameLoop);
        }

        // Jump when clicking or tapping anywhere on the canvas
        canvas.addEventListener('click', () => {
            if (!isGameOver) {
                birdVelocity = jump; // Make the bird jump
            } else {
                restartGame(); // Restart the game if it's over
            }
        });

        // Start the game
        gameLoop();
    </script>
</body>
</html>
