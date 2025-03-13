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
            background-color: #f0e68c; /* Light yellow background */
            text-align: center;
        }
        h1 {
            color: #ff5722;
            margin-bottom: 20px;
        }
        input {
            padding: 10px;
            width: 200px;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            padding: 10px 20px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>
    <h1>Welcome to Holi Celebration!</h1>
    <input type="text" id="username" placeholder="Enter your name" />
    <button onclick="wishHoli()">Submit</button>

    <script>
        const quotes = [
            "Let the colors of Holi spread the message of peace and happiness.",
            "Holi is the time to break the ice and renew relationships.",
            "May your life be filled with vibrant colors of joy and happiness.",
            "Celebrate life with colors of joy and happiness.",
            "Wishing you a Holi filled with sweet memories and moments to cherish."
        ];

        function wishHoli() {
            const username = document.getElementById('username').value;
            if (username) {
                const randomQuote = quotes[Math.floor(Math.random() * quotes.length)];
                alert(`Happy Holi from Vasu, ${username}!\n\nQuote: ${randomQuote}`);
            } else {
                alert("Please enter your name.");
            }
        }
    </script>
</body>
</html>
