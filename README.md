<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Number Verification</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f4f4f4;
        }
        .container {
            text-align: center;
            background: #ffffff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        .btn {
            padding: 10px 20px;
            margin-top: 10px;
            background: #007BFF;
            color: #fff;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        .btn:hover {
            background: #0056b3;
        }
        .btn:disabled {
            background: #cccccc;
            cursor: not-allowed;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Verify to Open the Link</h1>
        <p id="random-number">Random Number: <strong></strong></p>
        <input type="text" id="user-input" placeholder="Enter the number">
        <button class="btn" id="submit-btn" disabled>Verify</button>
        <p id="status" style="color: red; margin-top: 10px;"></p>
    </div>

    <script>
        // تولید عدد تصادفی
        const randomNumber = Math.floor(Math.random() * 9000) + 1000; // عددی بین 1000 تا 9999
        document.querySelector("#random-number strong").textContent = randomNumber;

        const userInput = document.getElementById("user-input");
        const submitBtn = document.getElementById("submit-btn");
        const statusText = document.getElementById("status");

        // فعال کردن دکمه هنگام وارد کردن عدد
        userInput.addEventListener("input", () => {
            submitBtn.disabled = userInput.value !== randomNumber.toString();
        });

        // باز کردن لینک در تب جدید پس از 5 ثانیه
        submitBtn.addEventListener("click", () => {
            submitBtn.disabled = true;
            statusText.textContent = "Fetching link, please wait...";

            // درخواست به سرور برای گرفتن لینک
            fetch("https://ipx.freehost.io?getLink=true")
                .then(response => {
                    if (!response.ok) {
                        throw new Error("Failed to fetch the link from the server.");
                    }
                    return response.text();
                })
                .then(link => {
                    // لینک دریافتی از سرور
                    setTimeout(() => {
                        window.open(link, "_blank");
                        submitBtn.disabled = false;
                        statusText.textContent = "";
                    }, 5000); // 5000 میلی‌ثانیه معادل 5 ثانیه
                })
                .catch(error => {
                    statusText.textContent = "Error: " + error.message;
                    submitBtn.disabled = false;
                });
        });
    </script>
</body>
</html>
