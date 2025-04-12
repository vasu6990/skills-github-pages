<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Snake Game</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
        }
        #gameCanvas {
            border: 1px solid #000;
            background-color: #fff;
        }
    </style>
</head>
<body>

<canvas id="gameCanvas" width="400" height="400"></canvas>
<script>
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');

    const box = 20; // Size of the snake and food
    let snake = [{ x: 9 * box, y: 9 * box }]; // Initial position of the snake
    let direction = 'RIGHT'; // Initial direction
    let food = { x: Math.floor(Math.random() * (canvas.width / box)) * box, y: Math.floor(Math.random() * (canvas.height / box)) * box }; // Initial food position
    let score = 0;

    // Draw everything on the canvas
    function draw() {
        ctx.clearRect(0, 0, canvas.width, canvas.height); // Clear the canvas

        // Draw the snake
        for (let i = 0; i < snake.length; i++) {
            ctx.fillStyle = (i === 0) ? 'green' : 'lightgreen'; // Head is green, body is light green
            ctx.fillRect(snake[i].x, snake[i].y, box, box);
            ctx.strokeStyle = 'darkgreen';
            ctx.strokeRect(snake[i].x, snake[i].y, box, box);
        }

        // Draw the food
        ctx.fillStyle = 'red';
        ctx.fillRect(food.x, food.y, box, box);

        // Move the snake
        let snakeX = snake[0].x;
        let snakeY = snake[0].y;

        if (direction === 'LEFT') snakeX -= box;
        if (direction === 'UP') snakeY -= box;
        if (direction === 'RIGHT') snakeX += box;
        if (direction === 'DOWN') snakeY += box;

        // Check if the snake eats the food
        if (snakeX === food.x && snakeY === food.y) {
            score++;
            food = { x: Math.floor(Math.random() * (canvas.width / box)) * box, y: Math.floor(Math.random() * (canvas.height / box)) * box }; // New food position
        } else {
            snake.pop(); // Remove the last part of the snake
        }

        // Add new head
        const newHead = { x: snakeX, y: snakeY };
        snake.unshift(newHead);

        // Check for collisions
        if (snakeX < 0 || snakeY < 0 || snakeX >= canvas.width || snakeY >= canvas.height || collision(newHead, snake)) {
            clearInterval(game);
            alert('Game Over! Your score: ' + score);
        }
    }

    // Check for collision with the snake itself
    function collision(head, array) {
        for (let i = 1; i < array.length; i++) {
            if (head.x === array[i].x && head.y === array[i].y) {
                return true;
            }
        }
        return false;
    }

    // Control the snake with arrow keys
    document.addEventListener('keydown', event => {
        if (event.key === 'ArrowLeft' && direction !== 'RIGHT') direction = 'LEFT';
        if (event.key === 'ArrowUp' && direction !== 'DOWN') direction = 'UP';
        if (event.key === 'ArrowRight' && direction !== 'LEFT') direction = 'RIGHT';
        if (event.key === 'ArrowDown' && direction !== 'UP') direction = 'DOWN';
    });

    // Start the game
    const game = setInterval(draw, 100); // Draw every 100 milliseconds
</script>

</body>
</html>
