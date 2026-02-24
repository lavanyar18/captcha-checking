<!DOCTYPE html>
<html>
<head>
    <title>CAPTCHA Validation</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }

        .container {
            width: 300px;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 8px;
        }

        .captcha-box {
            font-size: 24px;
            font-weight: bold;
            letter-spacing: 4px;
            background: #f2f2f2;
            padding: 10px;
            text-align: center;
            margin-bottom: 10px;
            user-select: none;
        }

        input {
            width: 100%;
            padding: 8px;
            margin-bottom: 10px;
        }

        button {
            width: 100%;
            padding: 8px;
            background-color: #28a745;
            color: white;
            border: none;
            cursor: pointer;
        }

        button:hover {
            background-color: #218838;
        }

        .error {
            color: red;
        }

        .success {
            color: green;
        }
    </style>
</head>
<body>

<div class="container">
    <div class="captcha-box" id="captcha"></div>

    <input type="text" id="userInput" placeholder="Enter CAPTCHA">
    <button onclick="checkCaptcha()">Submit</button>

    <p id="message"></p>
</div>

<script>
    let captchaCode = "";

    function generateCaptcha() {
        const chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
        captchaCode = "";
        for (let i = 0; i < 6; i++) {
            captchaCode += chars.charAt(Math.floor(Math.random() * chars.length));
        }
        document.getElementById("captcha").innerText = captchaCode;
    }

    function checkCaptcha() {
        const input = document.getElementById("userInput").value;
        const message = document.getElementById("message");

        if (input === captchaCode) {
            message.innerHTML = "CAPTCHA Verified Successfully!";
            message.className = "success";
        } else {
            message.innerHTML = "Incorrect CAPTCHA. Try Again.";
            message.className = "error";
            generateCaptcha(); // new captcha if wrong
        }
    }

    // Generate when page loads
    generateCaptcha();
</script>

</body>
</html>
