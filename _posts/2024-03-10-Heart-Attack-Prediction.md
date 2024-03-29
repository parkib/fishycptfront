---
toc: true
layout: base
search_exclude: false
permalink: heart
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Heart Attack Prediction</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
            background-color: #F5F5F5;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h1 {
            text-align: center;
            color: #3F51B5;
            font-size: 36px;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
        }
        form {
            max-width: 600px;
            margin: 0 auto;
        }
        p {
            color: #555;
            font-size: 16px;
            line-height: 1.5;
        }
        label {
            font-weight: bold;
            display: block;
            margin-bottom: 5px;
            color: #333;
        }
        input,
        select {
            width: calc(100% - 22px);
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
            box-sizing: border-box;
            font-size: 16px;
        }
        button {
            background-color: #3F51B5;
            color: #fff;
            border: none;
            border-radius: 5px;
            padding: 12px 24px;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #303F9F;
        }
        #result {
            margin-top: 20px;
        }
        #result p {
            color: #333;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Heart Attack Prediction</h1>
        <form id="heartForm">
            <p><strong>Important Note: </strong> Some aspects of these predictions may not be accurate due to limitations in the dataset.</p>
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required><br><br>
            <label for="sex">Gender:</label>
            <select id="sex" name="sex" required>
                <option value="Male">Male</option>
                <option value="Female">Female</option>
                <option value="Other">Other</option>
            </select><br><br>
            <label for="age">Age:</label>
            <input type="number" id="age" name="age" required><br><br>
            <label for="cp">Chest Pain Level:</label>
            <input type="number" id="cp" name="cp" required><br><br>
            <label for="trtpbs">Resting Blood Pressure (Max value 200 mm/Hg)</label>
            <input type="number" id="trtpbs" name="trtpbs" required><br><br>
            <label for="chol"> Cholesterol:</label>
            <input type="number" id="chol" name="chol" required><br><br>
            <label for="exng">Exercise Induced Angina:</label>
            <select id="exng" name="exng">
                <option value="0">No Exercise Induced Angina</option>
                <option value="1">Yes Exercise Induced Angina</option>
            </select><br><br>
            <button type="button" onclick="predictHeart()">Predict Probability of Heart Attack</button>
        </form>
        <div id="result"></div>
    </div>
    <script>
        function predictHeart() {
            var form = document.getElementById('heartForm');
            var name = document.getElementById('name');
            var resultDiv = document.getElementById('result');
            // Check if any required fields are empty
            var requiredFields = form.querySelectorAll('input[required], select[required]');
            var isEmpty = Array.from(requiredFields).some(field => !field.value.trim());
            if (isEmpty) {
                resultDiv.innerHTML = '<p>Please fill out all required fields.</p>';
                return;
            }
            var formData = {
                sex: form['sex'].value,
                age: form['age'].value,
                cp: form['cp'].value,
                trtpbs: form['trtpbs'].value,
                chol: form['chol'].value,
                exng: form['exng'].value
            };
            fetch('http://localhost:8086/api/heart/predict', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
                'Accept': 'application/json'
            },
            body: JSON.stringify(formData)
        })
        .then(response => response.json())
        .then(data => {
            resultDiv.innerHTML = '<h2>Prediction Result for ' + name.value + '</h2>';
                for (var key in data) {
                    resultDiv.innerHTML += '<p>' + key + ': ' + data[key] + '</p>';
                }
                var heartProbability = parseFloat(data['heart_prob']);
                if (data[key] < 30) {
                    resultDiv.innerHTML += '<p>:partying_face::partying_face::partying_face::partying_face: You are healthy! :partying_face::partying_face::partying_face::partying_face::partying_face: </p>';
                } else {
                    resultDiv.innerHTML += '<p> :skull: You are in danger! :skull: </p>';
                }
            })
            .catch(error => {
                console.error('Error:', error);
            });
        }
    </script>