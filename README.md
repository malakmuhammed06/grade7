# grade7
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مؤقت الاختبار</title>
    <style>
        .timer-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f8f9fa;
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            width: 220px;
            margin: 20px auto;
        }
        .timer-label {
            font-size: 16px;
            color: #495057;
            margin-bottom: 8px;
            font-weight: bold;
        }
        #timer {
            font-size: 36px;
            font-weight: bold;
            color: #2b2b2b;
            background: #ffffff;
            padding: 10px 20px;
            border-radius: 8px;
            border: 2px solid #dee2e6;
            letter-spacing: 2px;
        }
        .timer-warning {
            color: #dc3545 !important;
            border-color: #dc3545 !important;
            animation: pulse 1s infinite;
        }
        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
        }
    </style>
</head>
<body>

    <div class="timer-container">
        <div class="timer-label">الوقت المتبقي</div>
        <div id="timer">01:00</div>
    </div>

    <script>
        let timeLeft = 60; // 60 ثانية (دقيقة واحدة)
        const timerDisplay = document.getElementById('timer');

        const countdown = setInterval(() => {
            let minutes = Math.floor(timeLeft / 60);
            let seconds = timeLeft % 60;

            // تنسيق الأرقام لتظهر دائماً بصيغة 00:00
            let formattedTime = 
                String(minutes).padStart(2, '0') + ':' + 
                String(seconds).padStart(2, '0');

            timerDisplay.textContent = formattedTime;

            // تنبيه مرئي عندما يتبقى 10 ثوانٍ أو أقل
            if (timeLeft <= 10) {
                timerDisplay.classList.add('timer-warning');
            }

            if (timeLeft <= 0) {
                clearInterval(countdown);
                timerDisplay.textContent = "انتهى الوقت!";
                timerDisplay.style.fontSize = "22px";
                // يمكنك هنا إضافة وظيفة تلقائية لإرسال الاختبار عند انتهاء الوقت
            }
            
            timeLeft--;
        }, 1000);
    </script>

</body>
</html>
