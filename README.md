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
            margin: 0;
            font-family: Arial, sans-serif;
            overflow: hidden;
            background-image: url('https://i.imgur.com/8Q8Z8gD.png'); /* Background image for Holi */
            background-size: cover;
            background-position: center;
            color: white; /* Change text color for better visibility */
        }
        h1 {
            font-size: 48px;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7); /* Add shadow for better visibility */
        }
        .quote {
            font-size: 24px;
            margin-bottom: 40px;
            text-align: center;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.5); /* Add shadow for better visibility */
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
    </style>
</head>
<body>
    <h1>Happy Holi from Vasu!</h1>
    <div class="quote" id="quote"></div>
    <div id="balloonContainer"></div>

    <script>
        const quotes = [
            "Let the colors of Holi spread the message of peace and happiness.",
            "Holi is the time to break the ice and renew relationships.",
            "May your life be filled with vibrant colors of joy and happiness.",
            "Celebrate life with colors of joy and happiness.",
            "Wishing you a Holi filled with sweet memories and moments to cherish."
        ];

        // Display a random quote
        document.getElementById('quote').innerText = quotes[Math.floor(Math.random() * quotes.length)];

        // Function to create a balloon
        function createBalloon(x, y) {
            const balloon = document.createElement('div');
            balloon.classList.add('balloon');
            balloon.style.left = x + 'px';
            balloon.style.top = y + 'px';

            balloon.classList.add('burst');
            setTimeout(() => {
                balloon.remove();
            }, 500);

            document.getElementById('balloonContainer').appendChild(balloon);
        }

        // Event listener for clicks
        document.addEventListener('click', (event) => {
            createBalloon(event.clientX - 25, event.clientY - 35); // Adjust position to center the balloon
        });
    </script>
</body>
</html>
