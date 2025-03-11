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
            background-image: url('https://i.imgur.com/8Q8Z8gD.png'); /* Balloon image */
            background-size: cover;
            position: absolute;
            cursor: pointer;
            transition: transform 0.2s;
        }
        .balloon:hover {
            transform: scale(1.1);
        }
        .burst {
            background-image: url('https://i.imgur.com/1Z5Z5gD.png'); /* Bursting balloon image */
            background-size: cover;
            width: 70px; /* Adjust size as needed */
            height: 70px; /* Adjust size as needed */
            animation: burst 0.5s forwards;
        }
        @keyframes burst {
            0% { transform: scale(1); }
            100% { transform: scale(0); }
        }
        .water-drop {
            position: absolute;
            width: 10px;
            height: 10px;
            background-color: rgba(0, 162, 232, 0.7); /* Water drop color */
            border-radius: 50%;
            animation: splash 0.5s forwards;
        }
        @keyframes splash {
            0% { transform: scale(1); opacity: 1; }
            100% { transform: scale(0); opacity: 0; }
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
                createWaterDrops(balloon.style.left, balloon.style.top);
                setTimeout(() => {
                    balloon.remove();
                }, 500);
            });

            balloonContainer.appendChild(balloon);
        }

        function createWaterDrops(left, top) {
            for (let i = 0; i < 10; i++) {
                const drop = document.createElement('div');
                drop.classList.add('water-drop');
                drop.style.left = parseInt(left) + Math.random() * 50 + 'px';
                drop.style.top = parseInt(top) + Math.random() * 50 + 'px';
                document.body.appendChild(drop);

                setTimeout(() => {
                    drop.remove();
                }, 500);
            }
        }

        // Create balloons at intervals
        setInterval(createBalloon, 1000);
    </script>
</body>
</html>

