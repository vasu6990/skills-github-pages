<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Apology Message</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: Arial, sans-serif;
            background-color: #f0f0f0; /* Light gray background */
            text-align: center;
        }
        h1 {
            color: #333;
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
            background-color: #ff5722; /* Orange background */
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #e64a19; /* Darker orange on hover */
        }
    </style>
</head>
<body>
    <h1>Apology Message</h1>
    <input type="text" id="username" placeholder="Enter your name" />
    <button onclick="showApology()">Submit</button>

    <script>
        function showApology() {
            const username = document.getElementById('username').value;
            if (username) {
                alert(`Sorry, please forgive me, ${username}!`);
            } else {
                alert("Please enter your name.");
            }
        }
    </script>
</body>
</html>
