<!DOCTYPE html>
<html lang="fa">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نمایش سایت دوم</title>
    <script>
        function rewriteLinks() {
            const iframe = document.getElementById("iframe-content");
            const iframeDoc = iframe.contentDocument || iframe.contentWindow.document;

            // تغییر رفتار لینک‌ها
            const links = iframeDoc.querySelectorAll("a");
            links.forEach(link => {
                link.addEventListener("click", function (event) {
                    event.preventDefault(); // جلوگیری از رفتن به لینک اصلی
                    iframe.src = "https://ipx.freehost.io/?url=" + encodeURIComponent(link.href); // بازنویسی لینک در iframe
                });
            });
        }
            // جلوگیری از کلیک راست
        document.addEventListener('contextmenu', function (e) {
            e.preventDefault();
            alert("Right-click is disabled!");
        });

        // جلوگیری از استفاده از کلیدهای خاص برای باز کردن ابزارهای توسعه‌دهنده
        document.addEventListener('keydown', function (e) {
            // Ctrl+Shift+I (Inspect), Ctrl+Shift+J (Console), Ctrl+U (View Source), F12
            if ((e.ctrlKey && e.shiftKey && (e.key === 'I' || e.key === 'J')) || 
                e.key === 'F12' || 
                (e.ctrlKey && e.key === 'U')) {
                e.preventDefault();
                alert("Developer tools are disabled!");
            }
        });

        // شناسایی باز شدن ابزارهای توسعه‌دهنده با کاهش اندازه پنجره
        const detectDevTools = function () {
            const threshold = 160; // آستانه برای عرض/ارتفاع ابزارهای توسعه
            if (window.outerWidth - window.innerWidth > threshold || window.outerHeight - window.innerHeight > threshold) {
                alert("Developer tools detected!");
                document.body.innerHTML = ""; // حذف محتوا در صورت شناسایی
            }
        };
        setInterval(detectDevTools, 1000); // بررسی هر ثانیه
    </script>

  <script>
        // آدرس سرور PHP
        const proxyUrl = 'https://ipx.freehost.io';
        const targetUrl = 'https://ipx.freehost.io'; // آدرس سایت مقصد

        // درخواست به سرور PHP و بارگذاری پاسخ در iframe
        fetch(proxyUrl + '?url=' + encodeURIComponent(targetUrl))
            .then(response => response.text())
            .then(data => {
                const iframe = document.getElementById('iframe');
                const blob = new Blob([data], { type: 'text/html' });
                iframe.src = URL.createObjectURL(blob);
            })
            .catch(error => console.error('Error:', error));
    </script>
    
</head>
<body>
    <iframe id="iframe-content" src="https://ipx.freehost.io/" style="width: 100%; height: 100vh; border: none;" onload="rewriteLinks()"></iframe>
</body>
</html>
