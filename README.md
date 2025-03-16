<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Wishes to Admin Ji</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0e68c; /* Light yellow background */
            font-family: Arial, sans-serif;
        }
        h1 {
            color: #ff5722;
            margin-bottom: 20px;
        }
        #message {
            display: none;
            padding: 20px;
            background-color: white;
            border: 2px solid #ff5722;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
            font-size: 24px;
            text-align: center;
            animation: pop 0.5s ease-in-out, slideIn 0.5s ease-in-out;
        }
        @keyframes pop {
            0% {
                transform: scale(0);
                opacity: 0;
            }
            50% {
                transform: scale(1.1);
                opacity: 1;
            }
            100% {
                transform: scale(1);
            }
        }
        @keyframes slideIn {
            0% {
                transform: translateY(-50px);
                opacity: 0;
            }
            100% {
                transform: translateY(0);
                opacity: 1;
            }
        }
        button {
            padding: 10px 20px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>
    <h1>🎉 जन्मदिन मुबारक हो, एडमिन जी! 🎉</h1>
    <button onclick="showMessage()">संदेश दिखाएँ</button>
    <div id="message">
        <p>आपका जन्मदिन सभी समूह के सदस्यों की ओर से बहुत-बहुत मुबारक हो!</p>
    </div>

    <script>
        function showMessage() {
            const messageDiv = document.getElementById('message');
            messageDiv.style.display = 'block'; // Show the message
            messageDiv.classList.add('show'); // Add class to trigger animation
        }
    </script>
</body>
</html>
