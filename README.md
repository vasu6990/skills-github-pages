<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Holi!</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0e68c;
            margin: 0;
            font-family: Arial, sans-serif;
            overflow: hidden;
        }
        h1 {
            color: #ff5722;
            font-size: 48px;
            margin-bottom: 20px;
        }
        .balloon {
            width: 50px;
            height: 70px;
            background-color: #ff4081;
            border-radius: 50% 50% 0 0;
            position: absolute;
            cursor: pointer;
            transition: transform 0.2s;
        }
        .balloon:hover {
            transform: scale(1.1);
        }
        .burst {
            background-image: url('https://i.imgur.com/1Z5Z5gD.png'); /* URL of the bursting balloon image */
            background-size: cover;
            width: 70px; /* Adjust size as needed */
            height: 70px; /* Adjust size as needed */
            animation: burst 0.5s forwards;
        }
        @keyframes burst {
            0% { transform: scale(1); }
            100% { transform: scale(0); }
        }
    </style>
</head>
<body>
    <h1>Happy Holi!</h1>
    <div id="balloonContainer"></div>

    <script>
        const balloonContainer = document.getElementById('balloonContainer');

        function createBalloon() {
            const balloon = document.createElement('div');
            balloon.classList.add('balloon');
            balloon.style.left = Math.random() * (window.innerWidth - 50) + 'px';
            balloon.style.top = Math.random() * (window.innerHeight - 100) + 'px';

            balloon.addEventListener('click', () => {
                balloon.classList.add('burst');
                setTimeout(() => {
                    balloon.remove();
                }, 500);
                displayMessage();
            });

            balloonContainer.appendChild(balloon);
        }

        function displayMessage() {
            const message = document.createElement('div');
            message.innerText = "Splash! 🎉";
            message.style.position = 'absolute';
            message.style.top = Math.random() * (window.innerHeight - 100) + 'px';
            message.style.left = Math.random() * (window.innerWidth - 100) + 'px';
            message.style.fontSize = '24px';
            message.style.color = '#ff5722';
            message.style.pointerEvents = 'none';
            document.body.appendChild(message);

            setTimeout(() => {
                message.remove();
            }, 1000);
        }

        // Create balloons at intervals
        setInterval(createBalloon, 1000);
    </script>
</body>
</html>

