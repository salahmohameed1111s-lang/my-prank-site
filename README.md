<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>بوابة تسجيل الدخول الآمنة</title>
    <style>
        /* ألوان احترافية وتأثيرات بصرية للموقع */
        body {
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #1f1c2c, #928dab);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            transition: background 0.5s ease;
        }

        /* حاوية نموذج تسجيل الدخول */
        .login-container {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            padding: 40px;
            border-radius: 15px;
            box-shadow: 0 15px 25px rgba(0,0,0,0.3);
            width: 350px;
            text-align: center;
            transition: all 0.5s ease;
        }

        .login-container h2 {
            color: #fff;
            margin-bottom: 30px;
            font-size: 24px;
        }

        .input-group {
            margin-bottom: 20px;
            position: relative;
        }

        .input-group input {
            width: 100%;
            padding: 10px 0;
            font-size: 16px;
            color: #fff;
            background: transparent;
            border: none;
            border-bottom: 2px solid #fff;
            outline: none;
            transition: 0.3s;
        }

        .input-group input:focus {
            border-bottom-color: #00d2ff;
        }

        .btn {
            background: linear-gradient(90deg, #00d2ff, #3a7bd5);
            border: none;
            padding: 12px 20px;
            color: white;
            font-size: 16px;
            border-radius: 25px;
            cursor: pointer;
            width: 100%;
            font-weight: bold;
            box-shadow: 0 5px 15px rgba(0,210,255,0.3);
            transition: 0.3s;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(0,210,255,0.5);
        }

        /* شاشة الاختراق المزيفة (مخفية في البداية) */
        .hack-screen {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: #ff0000;
            color: black;
            z-index: 9999;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            font-family: 'Courier New', Courier, monospace;
            text-align: center;
            animation: flash 0.2s infinite alternate;
        }

        @keyframes flash {
            from { background-color: #990000; }
            to { background-color: #ff0000; }
        }

        .hack-box {
            background: rgba(0, 0, 0, 0.9);
            color: #00ff00;
            padding: 30px;
            border-radius: 10px;
            border: 3px solid #fff;
            box-shadow: 0 0 50px rgba(0,0,0,1);
            max-width: 80%;
        }

        .hack-box h1 {
            color: #ff0000;
            font-size: 35px;
            margin-bottom: 20px;
            text-shadow: 0 0 10px #ff0000;
        }

        .hack-box p {
            font-size: 20px;
            font-weight: bold;
        }

        /* حقوق البرمجة في أسفل الصفحة */
        .footer {
            position: absolute;
            bottom: 15px;
            color: rgba(255, 255, 255, 0.7);
            font-size: 14px;
            pointer-events: none;
            z-index: 10000; /* لتبقى ظاهرة حتى فوق الشاشة الحمراء */
            background: rgba(0,0,0,0.5);
            padding: 5px 15px;
            border-radius: 15px;
        }
    </style>
</head>
<body>

    <!-- واجهة تسجيل الدخول -->
    <div class="login-container" id="loginCard">
        <h2>تسجيل الدخول للنظام</h2>
        <form id="loginForm" onsubmit="triggerPrank(event)">
            <div class="input-group">
                <input type="text" placeholder="اسم المستخدم" required>
            </div>
            <div class="input-group">
                <input type="password" placeholder="كلمة المرور" required>
            </div>
            <button type="submit" class="btn">دخول</button>
        </form>
    </div>

    <!-- شاشة المزحة (الاختراق) -->
    <div class="hack-screen" id="hackScreen">
        <div class="hack-box">
            <h1>⚠️ تم اختراق نظام هاتفك بنجاح! ⚠️</h1>
            <p>جاري سحب الصور، الملفات، الحسابات والرسائل الشخصية...</p>
            <p style="color: white; font-size: 16px; margin-top: 20px;">( هههههه لا تقلق، هذه مجرد مزحة! 😜 )</p>
        </div>
    </div>

    <!-- الحقوق أسفل الموقع -->
    <div class="footer">
        تمت البرمجة بواسطة صلاح ابراميل
    </div>

    <script>
        function triggerPrank(event) {
            // منع الصفحة من إعادة التحميل عند إرسال النموذج
            event.preventDefault(); 
            
            // إخفاء واجهة تسجيل الدخول وإظهار شاشة الاختراق
            document.getElementById('loginCard').style.display = 'none';
            document.getElementById('hackScreen').style.display = 'flex';
            
            // إضافة صوت تنبيه اختياري إذا أردت (تأثير مرعب إضافي للمزحة)
            try {
                let audioCtx = new (window.AudioContext || window.webkitAudioContext)();
                let oscillator = audioCtx.createOscillator();
                oscillator.type = 'sawtooth';
                oscillator.frequency.setValueAtTime(150, audioCtx.currentTime); // صوت غليظ ومزعج
                oscillator.connect(audioCtx.destination);
                oscillator.start();
                setTimeout(() => oscillator.stop(), 2000); // يتوقف الصوت بعد ثانيتين
            } catch(e) {
                console.log("Audio not supported or blocked by browser");
            }
        }
    </script>
</body>
</html>
