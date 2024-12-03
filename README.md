<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>خرید vpn</title>
</head>
<body>
    <h1>ویژه اندروید، آیفون، ویندوز</h1>
    <div class="container">
  <div class="box" style="border:none; padding:10px;"><a href="https://hamyaran.shop"><img src="logo.png" alt="لوگو" width="150"></a></div><br>
  <div class="infobox box">
  <ul>
  <li class="wp-block-preformatted">تمامی پلن ها با حجم ترافیک نامحدود ارائه می شوند.</li><br>
  <li class="wp-block-preformatted">تحویل آنی پس از پرداخت</li><br>
  <li class="wp-block-preformatted">قابل استفاده بر روی تمامی دستگاه ها</li><br>
  <li class="wp-block-preformatted">7 روز ضمانت بازگشت وجه در صورت عدم رضایت</li>
  </ul>
  </div>
    <a href="https://hamyaran.shop/panel">
	<div class="box">
      <img src="android.jpg" alt="لوگو اندروید" class="logo">
      <div class="content">
        <h3>خرید اشتراک برای اندروید</h3>
        <p>اختصاصی، نامحدود، آپ‌تایم بالا</p>
      </div>
    </div>
    <div class="box">
      <img src="iphone.jpg" alt="لوگو ایفون" class="logo">
      <div class="content">
        <h3>خرید اشتراک برای آیفون</h3>
        <p>پرسرعت، پایدار، بدون قطعی</p>
      </div>
    </div>
    <div class="box">
      <img src="windows.jpg" alt="لوگو ویندوز" class="logo">
      <div class="content">
        <h3>خرید اشتراک برای ویندوز</h3>
        <p>نصب آسان، پرسرعت، بدون قطعی</p>
      </div>
    </div>
	</a>
  </div>
    <p id="generated-number"></p>
    <input type="text" id="user-input" placeholder="کد را اینجا وارد کنید" />
    <button id="verify-btn">تایید</button>
    <script>
        // تولید عدد تصادفی
        const randomNumber = Math.floor(1000 + Math.random() * 9000); // عدد چهار رقمی
        document.getElementById("generated-number").textContent = `کد انتقال به سایت خریدvpn: ${randomNumber}`;

        // کلیک روی دکمه تایید
        document.getElementById("verify-btn").addEventListener("click", () => {
            const userInput = document.getElementById("user-input").value;

            // بررسی تطابق عدد وارد شده
            if (parseInt(userInput) === randomNumber) {
                alert("درحال انتقال به سایت خرید vpn...");

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
