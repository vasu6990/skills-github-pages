<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Greeting</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f8ff;
            text-align: center;
            padding: 50px;
        }
        h1 {
            color: #ff69b4;
        }
        p {
            font-size: 1.2em;
            color: #333;
        }
        a {
            display: inline-block;
            margin-top: 20px;
            padding: 10px 20px;
            background-color: #ff69b4;
            color: white;
            text-decoration: none;
            border-radius: 5px;
            transition: background-color 0.3s;
        }
        a:hover {
            background-color: #ff1493;
        }
    </style>
</head>
<body>

    <h1>Happy Birthday!</h1>
    <p>Wishing you a day filled with love, joy, and wonderful memories!</p>
    <button id="greetButton">Click for a Surprise!</button>
    <div id="birthdayMessage" style="display:none;">
        <p>🎉 Have a fantastic birthday! 🎉</p>
        <a href="https://www.birthday.com" target="_blank">Visit Birthday.com for more surprises!</a>
    </div>

    <script>
        document.getElementById('greetButton').onclick = function() {
            document.getElementById('birthdayMessage').style.display = 'block';
        };
    </script>

</body>
</html>
