<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Relationship Finder</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f8ff;
            font-family: Arial, sans-serif;
        }
        h1 {
            color: #4CAF50;
        }
        input {
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            padding: 10px 15px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        .result {
            margin-top: 20px;
            font-size: 20px;
            color: #333;
        }
    </style>
</head>
<body>
    <h1>Find Your Relationship</h1>
    <input type="text" id="nameInput" placeholder="Enter your name" />
    <button onclick="findRelationship()">Submit</button>
    <div class="result" id="result"></div>

    <script>
        function findRelationship() {
            const name = document.getElementById('nameInput').value.trim();
            const resultDiv = document.getElementById('result');

            // Define relationships
            const relationships = {
                "Jyoti": "Sister",
                "Pooja": "Sister",
                "S P Verma": "Father",
                "Munni Verma": "Mother",
                "Divyansh": "Niece",
                "Kriyansh": "Niece",
                "Aaru": "Bestie"
            };

            // Check if the name exists in the relationships object
            if (relationships[name]) {
                resultDiv.innerHTML = `Your relationship is: ${relationships[name]}`;
            } else {
                resultDiv.innerHTML = `There is no relation between ${name} and you.`;
            }
        }
    </script>
</body>
</html>

