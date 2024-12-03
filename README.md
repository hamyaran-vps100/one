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
    </script>
</head>
<body>
    <iframe id="iframe-content" src="https://ipx.freehost.io/" style="width: 100%; height: 100vh; border: none;" onload="rewriteLinks()"></iframe>
</body>
</html>
