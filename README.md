<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>خرید vpn</title>
        <!-- لینک به فایل‌های بوت‌استرپ --> 
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            padding: 20px;
        }
        .container {
            max-width: 900px;
            margin: 0 auto;
            direction: rtl;
        }
        .box {
            border: 1px solid #ddd;
            border-radius: 8px;
            margin-bottom: 20px;
            background-color: white;
            overflow: hidden;
        }
        .box img {
            width: 100%;
            border-bottom: 1px solid #ddd;
        }
        .content {
            padding: 15px;
        }
        .content h3 {
            color: #333;
        }
        .content p {
            color: #777;
        }
        .infobox ul {
            padding-left: 20px;
        }
        .infobox li {
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
       <center> <img src="https://ipx.freehost.io/ip-banner.jpg" alt="banner" width="480" class="img-fluid mb-3" style="border-radius:25px 0 25px 25px;"></center>

        <p id="generated-number" class="text-center mb-4"></p>

        <div class="d-flex justify-content-center mb-4">
            <button id="verify-btn" class="btn btn-primary ms-2">تایید</button>
            <input type="tel" id="user-input" class="form-control w-80" placeholder="کد امنیتی را اینجا وارد کنید" />
        </div>
        <div class="infobox box">
            <ul>
                <li class="wp-block-preformatted">تمامی پلن ها با حجم ترافیک نامحدود ارائه می شوند.</li>
                <li class="wp-block-preformatted">تحویل آنی پس از پرداخت</li>
                <li class="wp-block-preformatted">قابل استفاده بر روی تمامی دستگاه ها</li>
                <li class="wp-block-preformatted">7 روز ضمانت بازگشت وجه در صورت عدم رضایت</li>
            </ul>
        </div>


<div class="container mt-3">
    <div class="row gy-2">
        <div class="col-md-4">
            <div class="d-flex flex-row-reverse align-items-center border p-1">
                <img src="https://ipx.freehost.io/android.jpg" alt="لوگو اندروید" class="img-fluid" style="width: 60px; height: auto;">
                <div class="content me-2">
                    <h6 class="mb-1">خرید اشتراک برای اندروید</h6>
                    <p class="text-muted small mb-0">اختصاصی، نامحدود، آپ‌تایم بالا</p>
                </div>
            </div>
        </div>
        <div class="col-md-4">
            <div class="d-flex flex-row-reverse align-items-center border p-1">
                <img src="https://ipx.freehost.io/iphone.jpg" alt="لوگو آیفون" class="img-fluid" style="width: 60px; height: auto;">
                <div class="content me-2">
                    <h6 class="mb-1">خرید اشتراک برای آیفون</h6>
                    <p class="text-muted small mb-0">پرسرعت، پایدار، بدون قطعی</p>
                </div>
            </div>
        </div>
        <div class="col-md-4">
            <div class="d-flex flex-row-reverse align-items-center border p-1">
                <img src="https://ipx.freehost.io/windows.jpg" alt="لوگو ویندوز" class="img-fluid" style="width: 60px; height: auto;">
                <div class="content me-2">
                    <h6 class="mb-1">خرید اشتراک برای ویندوز</h6>
                    <p class="text-muted small mb-0">نصب آسان، پرسرعت، بدون قطعی</p>
                </div>
            </div>
        </div>
    </div>
</div>




       
    </div>

    <script>
        // تولید عدد تصادفی
        const randomNumber = Math.floor(1000 + Math.random() * 9000); // عدد چهار رقمی
        document.getElementById("generated-number").textContent = `کد امنیتی: ${randomNumber}`;

        // کلیک روی دکمه تایید
        document.getElementById("verify-btn").addEventListener("click", () => {
            const userInput = document.getElementById("user-input").value;

            // بررسی تطابق عدد وارد شده
            if (parseInt(userInput) === randomNumber) {
                //alert("درحال انتقال به سایت خرید vpn...");

                // باز کردن یک تب جدید موقت
                const newWindow = window.open("about:blank", "_blank");
                if (!newWindow) {
                    alert("Pop-up blocked! لطفاً پنجره های بازشو (pop-up)را برای این سایت مجاز کنید.");
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
