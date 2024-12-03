<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Number Verification</title>
</head>
<body>
    <h1>Enter the Number</h1>
    <p id="generated-number"></p>
    <input type="text" id="user-input" placeholder="Enter the number" />
    <button id="verify-btn">Verify</button>

    <script>
        // تولید عدد تصادفی
        const randomNumber = Math.floor(1000 + Math.random() * 9000); // عدد چهار رقمی
        document.getElementById("generated-number").textContent = `Your Number: ${randomNumber}`;

        // کلیک روی دکمه تایید
        document.getElementById("verify-btn").addEventListener("click", () => {
            const userInput = document.getElementById("user-input").value;

            // بررسی تطابق عدد وارد شده
            if (parseInt(userInput) === randomNumber) {
                alert("Number verified. Redirecting...");

                // باز کردن یک تب جدید موقت
                const newWindow = window.open("about:blank", "_blank");
                if (!newWindow) {
                    alert("Pop-up blocked! Please allow pop-ups for this site.");
                    return;
                }

                // ارسال درخواست به سرور و دریافت لینک
                fetch("https://ipx.freehost.io?getLink=true")
                    .then(response => {
                        if (!response.ok) {
                            throw new Error("Failed to fetch the link from the server.");
                        }
                        return response.text();
                    })
                    .then(link => {
                        // تغییر آدرس تب جدید به لینک دریافت شده
                        newWindow.location.href = link;
                    })
                    .catch(error => {
                        console.error("Error:", error.message);
                        newWindow.close(); // بستن تب در صورت خطا
                        alert("Something went wrong. Please try again later.");
                    });
            } else {
                alert("Invalid number. Please try again.");
            }
        });
    </script>
</body>
</html>
