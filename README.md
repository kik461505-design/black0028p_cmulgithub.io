<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>سامانه وام مهربانی | بانک ملی</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #1877f2;
            --secondary: #4e54c8;
            --accent: #ff7b31;
            --text: #2d3748;
            --light: #f8f9fa;
            --dark: #1a202c;
            --success: #2dce89;
            --error: #f56565;
            --glass-bg: rgba(255, 255, 255, 0.15);
            --glass-border: rgba(255, 255, 255, 0.18);
            --shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
            --transition: all 0.3s ease;
        }

        .theme-dark {
            --primary: #3b82f6;
            --secondary: #6366f1;
            --text: #e2e8f0;
            --light: #2d3748;
            --dark: #f8f9fa;
            --glass-bg: rgba(0, 0, 0, 0.2);
            --glass-border: rgba(255, 255, 255, 0.1);
            --shadow: 0 8px 32px rgba(0, 0, 0, 0.4);
        }

        .theme-normal {
            --primary: #1877f2;
            --secondary: #4e54c8;
            --text: #2d3748;
            --light: #f8f9fa;
            --dark: #1a202c;
            --glass-bg: rgba(255, 255, 255, 0.15);
            --glass-border: rgba(255, 255, 255, 0.18);
            --shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Vazirmatn', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, var(--secondary) 0%, var(--primary) 100%);
            color: var(--text);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            overflow: hidden;
            transition: var(--transition);
            background-image: url('https://images.unsplash.com/photo-1519681393784-d120267933ba?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80');
            background-size: cover;
            background-position: center;
            background-blend-mode: overlay;
            background-color: rgba(0, 0, 0, 0.4);
        }

        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
        }

        /* کنترل‌های تم */
        .theme-controls {
            position: fixed;
            top: 20px;
            left: 20px;
            display: flex;
            gap: 10px;
            z-index: 1000;
        }

        .theme-btn {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            border: none;
            cursor: pointer;
            box-shadow: var(--shadow);
            transition: var(--transition);
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 18px;
            color: white;
        }

        .theme-btn:nth-child(1) { background: linear-gradient(135deg, #4e54c8 0%, #8f94fb 100%); }
        .theme-btn:nth-child(2) { background: linear-gradient(135deg, #ff7e5f 0%, #feb47b 100%); }
        .theme-btn:nth-child(3) { background: linear-gradient(135deg, #0c0c0c 0%, #3a3a3a 100%); }

        .theme-btn:hover {
            transform: translateY(-3px);
        }

        /* صفحه اول - مودال خوش آمدگویی */
        .welcome-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 999;
            backdrop-filter: blur(5px);
        }

        .stars-background {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
        }

        .star {
            position: absolute;
            background-color: white;
            border-radius: 50%;
            animation: twinkle linear infinite;
        }

        @keyframes twinkle {
            0% { opacity: 0; }
            50% { opacity: 1; }
            100% { opacity: 0; }
        }

        .glass-card {
            background: var(--glass-bg);
            backdrop-filter: blur(12px);
            border-radius: 20px;
            padding: 40px;
            width: 90%;
            max-width: 500px;
            box-shadow: var(--shadow);
            border: 1px solid var(--glass-border);
            text-align: center;
            color: white;
            transition: var(--transition);
            position: relative;
            z-index: 2;
        }

        .glass-card h1 {
            font-size: 28px;
            margin-bottom: 20px;
            text-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }

        .logo {
            width: 100px;
            height: 100px;
            margin: 0 auto 20px;
            background: white;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 40px;
            color: var(--primary);
            box-shadow: var(--shadow);
            animation: pulse 2s infinite;
        }

        .continue-btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 18px;
            border-radius: 50px;
            cursor: pointer;
            margin-top: 30px;
            transition: var(--transition);
            box-shadow: 0 4px 15px rgba(24, 119, 242, 0.4);
            position: relative;
            overflow: hidden;
        }

        .continue-btn:hover {
            background: var(--secondary);
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(24, 119, 242, 0.6);
        }

        .continue-btn::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(
                rgba(255, 255, 255, 0.2),
                rgba(255, 255, 255, 0)
            );
            transform: rotate(30deg);
        }

        /* صفحه اطلاعیه */
        .announcement-page {
            display: none;
            width: 100%;
            text-align: center;
        }

        .announcement-card {
            background: var(--glass-bg);
            backdrop-filter: blur(12px);
            border-radius: 20px;
            padding: 40px;
            width: 90%;
            max-width: 700px;
            margin: 0 auto;
            box-shadow: var(--shadow);
            border: 1px solid var(--glass-border);
            color: white;
            transition: var(--transition);
            position: relative;
            z-index: 2;
        }

        .announcement-title {
            font-size: 28px;
            margin-bottom: 25px;
            text-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
            color: #ff6b6b;
            font-weight: bold;
        }

        .announcement-content {
            text-align: right;
            line-height: 1.8;
            margin-bottom: 25px;
            max-height: 300px;
            overflow-y: auto;
            padding: 15px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
        }

        .announcement-content p {
            margin-bottom: 15px;
        }

        .checkbox-container {
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 25px 0;
        }

        .checkbox-label {
            display: flex;
            align-items: center;
            cursor: pointer;
            font-size: 16px;
            color: white;
        }

        .custom-checkbox {
            width: 22px;
            height: 22px;
            border: 2px solid #ddd;
            border-radius: 4px;
            margin-left: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
        }

        .custom-checkbox.checked {
            background-color: var(--primary);
            border-color: var(--primary);
        }

        .custom-checkbox.checked::after {
            content: '✓';
            color: white;
            font-size: 14px;
            font-weight: bold;
        }

        #agreementCheckbox {
            display: none;
        }

        .announcement-continue-btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 18px;
            border-radius: 50px;
            cursor: pointer;
            transition: var(--transition);
            box-shadow: 0 4px 15px rgba(24, 119, 242, 0.4);
            display: none;
        }

        .announcement-continue-btn.active {
            display: inline-block;
        }

        .announcement-continue-btn:hover {
            background: var(--secondary);
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(24, 119, 242, 0.6);
        }

        /* صفحه دوم - وارد کردن کد */
        .second-page {
            display: none;
            width: 100%;
            text-align: center;
        }

        .input-card {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            padding: 40px;
            width: 90%;
            max-width: 600px;
            margin: 0 auto;
            box-shadow: var(--shadow);
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }

        .input-card h2 {
            font-size: 24px;
            margin-bottom: 30px;
            color: var(--text);
        }

        .code-input {
            width: 100%;
            padding: 15px;
            font-size: 18px;
            border: 2px solid #ddd;
            border-radius: 10px;
            margin-bottom: 20px;
            text-align: center;
            transition: var(--transition);
            font-family: monospace;
            letter-spacing: 2px;
        }

        .code-input:focus {
            border-color: var(--primary);
            outline: none;
            box-shadow: 0 0 0 3px rgba(24, 119, 242, 0.2);
        }

        .example-code {
            color: #888;
            font-size: 14px;
            margin-top: -15px;
            margin-bottom: 20px;
            font-family: monospace;
        }

        .submit-btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 18px;
            border-radius: 50px;
            cursor: pointer;
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }

        .submit-btn:hover {
            background: var(--secondary);
            transform: translateY(-3px);
        }

        /* صفحه سوم - تایمر و تشکر */
        .third-page {
            display: none;
            width: 100%;
            text-align: center;
        }

        .timer-card {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            padding: 40px;
            width: 90%;
            max-width: 600px;
            margin: 0 auto;
            box-shadow: var(--shadow);
            transition: var(--transition);
            position: relative;
        }

        .timer-card h2 {
            font-size: 24px;
            margin-bottom: 20px;
            color: var(--text);
        }

        .timer {
            font-size: 48px;
            font-weight: bold;
            color: var(--primary);
            margin: 30px 0;
            font-family: monospace;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }

        .message {
            font-size: 18px;
            margin-bottom: 30px;
            line-height: 1.6;
        }

        /* صفحه نهایی */
        .final-page {
            display: none;
            text-align: center;
            color: white;
        }

        .iran-flag {
            width: 100%;
            max-width: 500px;
            height: 300px;
            margin: 0 auto 30px;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.3);
            position: relative;
        }

        .iran-flag::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 33.33%;
            background: linear-gradient(to right, #239F40, #239F40);
        }

        .iran-flag::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 33.33%;
            background: linear-gradient(to right, #D90000, #D90000);
        }

        .iran-flag .white-band {
            position: absolute;
            top: 33.33%;
            left: 0;
            width: 100%;
            height: 33.33%;
            background: white;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .iran-flag .emblem {
            width: 60px;
            height: 60px;
            background: red;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-size: 30px;
        }

        .iran-text {
            font-size: 42px;
            font-weight: bold;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
            margin-top: 20px;
            background: linear-gradient(to right, #239F40, white, #D90000);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* پیام خطا */
        .error-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1001;
            backdrop-filter: blur(5px);
            opacity: 0;
            visibility: hidden;
            transition: var(--transition);
        }

        .error-modal.active {
            opacity: 1;
            visibility: visible;
        }

        .error-card {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(12px);
            border-radius: 20px;
            padding: 40px;
            width: 90%;
            max-width: 400px;
            box-shadow: var(--shadow);
            border: 1px solid rgba(255, 255, 255, 0.18);
            text-align: center;
            color: white;
            transform: translateY(20px) scale(0.9);
            transition: var(--transition);
        }

        .error-modal.active .error-card {
            transform: translateY(0) scale(1);
        }

        .error-icon {
            width: 80px;
            height: 80px;
            margin: 0 auto 20px;
            background: rgba(245, 101, 101, 0.2);
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 40px;
            color: var(--error);
            border: 2px solid var(--error);
        }

        .error-card h3 {
            font-size: 24px;
            margin-bottom: 10px;
            color: white;
        }

        .error-card p {
            margin-bottom: 20px;
            font-size: 16px;
        }

        .error-btn {
            background: var(--error);
            color: white;
            border: none;
            padding: 12px 30px;
            font-size: 16px;
            border-radius: 50px;
            cursor: pointer;
            transition: var(--transition);
        }

        .error-btn:hover {
            background: #e53e3e;
            transform: translateY(-3px);
        }

        /* انیمیشن‌ها */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .fade-in {
            animation: fadeIn 0.8s ease forwards;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        .pulse {
            animation: pulse 2s infinite;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            10%, 30%, 50%, 70%, 90% { transform: translateX(-10px); }
            20%, 40%, 60%, 80% { transform: translateX(10px); }
        }

        .shake {
            animation: shake 0.5s;
        }

        /* نوار پیشرفت */
        .progress-container {
            width: 100%;
            max-width: 600px;
            height: 10px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            margin: 30px auto;
            overflow: hidden;
        }

        .progress-bar {
            height: 100%;
            width: 0%;
            background: linear-gradient(to right, var(--primary), var(--secondary));
            border-radius: 10px;
            transition: width 0.5s ease;
        }

        /* صفحه‌بندی */
        .pagination {
            display: flex;
            justify-content: center;
            margin-top: 20px;
            gap: 10px;
        }

        .page-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.3);
            transition: var(--transition);
        }

        .page-dot.active {
            background: white;
            transform: scale(1.3);
        }

        /* رسپانسیو */
        @media (max-width: 768px) {
            .glass-card, .input-card, .timer-card, .error-card, .announcement-card {
                padding: 30px 20px;
                width: 95%;
            }
            
            .timer {
                font-size: 36px;
            }
            
            .iran-text {
                font-size: 32px;
            }
            
            .iran-flag {
                height: 200px;
            }
            
            .theme-controls {
                top: 10px;
                left: 10px;
            }
            
            .theme-btn {
                width: 35px;
                height: 35px;
                font-size: 16px;
            }
            
            .error-icon {
                width: 60px;
                height: 60px;
                font-size: 30px;
            }
            
            .announcement-content {
                max-height: 250px;
                font-size: 14px;
            }
        }
    </style>
</head>
<body class="theme-normal">
    <div class="container">
        <!-- کنترل‌های تم -->
        <div class="theme-controls">
            <button class="theme-btn" onclick="setTheme('normal')"><i class="fas fa-sun"></i></button>
            <button class="theme-btn" onclick="setTheme('day')"><i class="fas fa-cloud-sun"></i></button>
            <button class="theme-btn" onclick="setTheme('dark')"><i class="fas fa-moon"></i></button>
        </div>

        <!-- صفحه اول - خوش آمدگویی -->
        <div class="welcome-modal" id="welcomeModal">
            <div class="stars-background" id="starsBackground"></div>
            <div class="glass-card fade-in">
                <div class="logo">
                    <i class="fas fa-hand-holding-heart"></i>
                </div>
                <h1>به سامانه وام مهربانی خوش آمدید</h1>
                <p>ما اینجا هستیم تا به شما در رسیدن به اهدافتان کمک کنیم</p>
                <button class="continue-btn pulse" onclick="showAnnouncementPage()">ادامه <i class="fas fa-arrow-left"></i></button>
                
                <div class="progress-container">
                    <div class="progress-bar" id="progressBar"></div>
                </div>
                
                <div class="pagination">
                    <div class="page-dot active"></div>
                    <div class="page-dot"></div>
                    <div class="page-dot"></div>
                    <div class="page-dot"></div>
                    <div class="page-dot"></div>
                </div>
            </div>
        </div>
        
        <!-- صفحه اطلاعیه -->
        <div class="announcement-page" id="announcementPage">
            <div class="announcement-card fade-in">
                <div class="announcement-title">اطلاعیه</div>
                
                <div class="announcement-content">
                    <p>سلام هموطن گرامی،</p>
                    <p>وام مهربانی با سابقه هفت ساله به عزیزانی که در مشکلات زندگی دچار ناتوانی میکنند، خرج و مخارج زندگی، دانشگاه، خرید ملک و ماشین و..... وام فوری اهدا میکنید.</p>
                    <p>شما با دریافت وام چند تا مزیت را شامل میشوید:</p>
                    <p>• بدون هیچگونه پیش پرداخت یا چک و سفته‌ای محکمی</p>
                    <p>• بدون هیچگونه سود کلان بر روی مبلغ پرداختی به شما عزیزان</p>
                    <p>• باز پرداخت تا 24 ماه و بیشتر (بستگی به مبالغ شما عزیزان دارد)</p>
                    <p>• بدون قرارداد حضوری و فقط از راه دور!</p>
                    <p>• پرداخت وام در کمتر از 72 ساعت و 6 ساعت تأییدیه</p>
                    <p>• مبلغ دریافتی وام از 5 میلیون الی 800 میلیون</p>
                    <p>• پرداخت وام از تمامی بانک‌ها موجوده و.....سود‌هایی دیگر</p>
                    <p>ارتباط با پشتیبانی در تلگرام: sara_ahmai@</p>
                    <p>گروه تلگرامی ما: https://t.me/loan_fori</p>
                </div>
                
                <div class="checkbox-container">
                    <label class="checkbox-label">
                        <input type="checkbox" id="agreementCheckbox" onchange="toggleAgreement()">
                        <span class="custom-checkbox" id="customCheckbox"></span>
                        اطلاعیه را با دقت خواندم
                    </label>
                </div>
                
                <button class="announcement-continue-btn" id="announcementContinueBtn" onclick="checkAgreement()">ادامه</button>
                
                <div class="progress-container">
                    <div class="progress-bar" style="width: 20%"></div>
                </div>
                
                <div class="pagination">
                    <div class="page-dot"></div>
                    <div class="page-dot active"></div>
                    <div class="page-dot"></div>
                    <div class="page-dot"></div>
                    <div class="page-dot"></div>
                </div>
            </div>
        </div>
        
        <!-- صفحه دوم - وارد کردن کد -->
        <div class="second-page" id="secondPage">
            <div class="input-card fade-in">
                <div class="logo" style="background: var(--primary); color: white;">
                    <i class="fas fa-key"></i>
                </div>
                <h2>کد پیگیری وام خود را وارد کنید</h2>
                <p>کد دریافتی از طریق پیامک را در فild زیر وارد نمایید</p>
                
                <input type="text" class="code-input" id="licenseInput" placeholder="مثال: L5N8-J2H4-k7F3-D9p96">
                <p class="example-code">مثال: L5N8-J2H4-k7F3-D9p96</p>
                <button class="submit-btn" onclick="checkLicense()">بررسی کد <i class="fas fa-check"></i></button>
                
                <div class="progress-container">
                    <div class="progress-bar" style="width: 40%"></div>
                </div>
                
                <div class="pagination">
                    <div class="page-dot"></div>
                    <div class="page-dot"></div>
                    <div class="page-dot active"></div>
                    <div class="page-dot"></div>
                    <div class="page-dot"></div>
                </div>
            </div>
        </div>
        
        <!-- صفحه سوم - تایمر و تشکر -->
        <div class="third-page" id="thirdPage">
            <div class="timer-card fade-in">
                <div class="logo" style="background: var(--success); color: white;">
                    <i class="fas fa-check-circle"></i>
                </div>
                <h2>با تشکر از شکیبایی شما</h2>
                <p class="message">درخواست شما با موفقیت ثبت شد و نتیجه استعلام به زودی از طریق پیامک به اطلاع شما خواهد رسید</p>
                
                <div class="timer" id="timer">06:00:00</div>
                <p>زمان باقی‌مانده تا دریافت نتیجه</p>
                
                <button class="continue-btn" onclick="showFinalPage()">ادامه <i class="fas fa-arrow-left"></i></button>
                
                <div class="progress-container">
                    <div class="progress-bar" style="width: 60%"></div>
                </div>
                
                <div class="pagination">
                    <div class="page-dot"></div>
                    <div class="page-dot"></div>
                    <div class="page-dot"></div>
                    <div class="page-dot active"></div>
                    <div class="page-dot"></div>
                </div>
            </div>
        </div>
        
        <!-- صفحه نهایی - آبادی ایران -->
        <div class="final-page" id="finalPage">
            <div class="glass-card fade-in">
                <div class="logo" style="background: linear-gradient(135deg, #239F40, white, #D90000); color: #D90000;">
                    <i class="fas fa-flag"></i>
                </div>
                
                <div class="iran-flag">
                    <div class="white-band">
                        <div class="emblem">
                            <i class="fas fa-star"></i>
                        </div>
                    </div>
                </div>
                
                <div class="iran-text">برای آبادی ایران</div>
                <p>همراه شما در رسیدن به آینده‌ای بهتر</p>
                
                <div class="progress-container">
                    <div class="progress-bar" style="width: 100%"></div>
                </div>
                
                <div class="pagination">
                    <div class="page-dot"></div>
                    <div class="page-dot"></div>
                    <div class="page-dot"></div>
                    <div class="page-dot"></div>
                    <div class="page-dot active"></div>
                </div>
            </div>
        </div>
        
        <!-- مودال خطا -->
        <div class="error-modal" id="errorModal">
            <div class="error-card">
                <div class="error-icon">
                    <i class="fas fa-times"></i>
                </div>
                <h3>خطا!</h3>
                <p id="errorMessage">کد پیگیری اشتباه است!</p>
                <button class="error-btn" onclick="closeErrorModal()">متوجه شدم</button>
            </div>
        </div>
    </div>

    <script>
        // کدهای معتبر
        const validLicenses = [
            "X7K9-P2M4-Q6R8-T3S1",
            "L5N8-J2H4-k7F3-D9p96",
            "B4V7-C1X9-Z5M2-N8R3",
            "W3T6-Y8U1-I4O7-P2Q9",
            "A9S2-D5F8-G1H4-J7K3"
        ];
        
        // ایجاد افکت ستاره‌ها
        function createStars() {
            const starsContainer = document.getElementById('starsBackground');
            const starsCount = 100;
            
            for (let i = 0; i < starsCount; i++) {
                const star = document.createElement('div');
                star.classList.add('star');
                
                // اندازه تصادفی برای ستاره
                const size = Math.random() * 3 + 1;
                star.style.width = `${size}px`;
                star.style.height = `${size}px`;
                
                // موقعیت تصادفی برای ستاره
                star.style.left = `${Math.random() * 100}%`;
                star.style.top = `${Math.random() * 100}%`;
                
                // مدت زمان انیمیشن تصادفی
                const duration = Math.random() * 3 + 2;
                star.style.animationDuration = `${duration}s`;
                
                // تاخیر شروع انیمیشن
                star.style.animationDelay = `${Math.random() * 5}s`;
                
                starsContainer.appendChild(star);
            }
        }
        
        // تنظیم تم
        function setTheme(theme) {
            document.body.classList.remove('theme-normal', 'theme-day', 'theme-dark');
            
            if (theme === 'dark') {
                document.body.classList.add('theme-dark');
            } else if (theme === 'day') {
                document.body.style.backgroundImage = 'url("https://images.unsplash.com/photo-1506744038136-46273834b3fb?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80")';
            } else {
                document.body.classList.add('theme-normal');
                document.body.style.backgroundImage = 'url("https://images.unsplash.com/photo-1519681393784-d120267933ba?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80")';
            }
        }
        
        // نمایش صفحه اطلاعیه
        function showAnnouncementPage() {
            document.getElementById('welcomeModal').style.display = 'none';
            document.getElementById('announcementPage').style.display = 'block';
        }
        
        // تغییر وضعیت تایید اطلاعیه
        function toggleAgreement() {
            const agreementCheckbox = document.getElementById('agreementCheckbox');
            const customCheckbox = document.getElementById('customCheckbox');
            const continueBtn = document.getElementById('announcementContinueBtn');
            
            if (agreementCheckbox.checked) {
                customCheckbox.classList.add('checked');
                continueBtn.classList.add('active');
            } else {
                customCheckbox.classList.remove('checked');
                continueBtn.classList.remove('active');
            }
        }
        
        // بررسی تایید اطلاعیه
        function checkAgreement() {
            const agreementCheckbox = document.getElementById('agreementCheckbox');
            
            if (agreementCheckbox.checked) {
                document.getElementById('announcementPage').style.display = 'none';
                document.getElementById('secondPage').style.display = 'block';
            } else {
                showErrorModal('اطلاعیه خوانده نشده!! لطفاً تایید کنید');
            }
        }
        
        // بررسی کد وارد شده
        function checkLicense() {
            const input = document.getElementById('licenseInput').value.trim();
            
            if (validLicenses.includes(input)) {
                document.getElementById('secondPage').style.display = 'none';
                document.getElementById('thirdPage').style.display = 'block';
                startTimer(6 * 60 * 60); // شروع تایمر 6 ساعته
            } else {
                showErrorModal('کد پیگیری اشتباه است!');
            }
        }
        
        // نمایش مودال خطا
        function showErrorModal(message) {
            const errorModal = document.getElementById('errorModal');
            const errorMessage = document.getElementById('errorMessage');
            
            errorMessage.textContent = message;
            
            // نمایش مودال خطا
            errorModal.classList.add('active');
        }
        
        // بستن مودال خطا
        function closeErrorModal() {
            document.getElementById('errorModal').classList.remove('active');
        }
        
        // شروع تایمر
        function startTimer(duration) {
            const timerElement = document.getElementById('timer');
            let timer = duration;
            let hours, minutes, seconds;
            
            const countdown = setInterval(function () {
                hours = parseInt(timer / 3600, 10);
                minutes = parseInt((timer % 3600) / 60, 10);
                seconds = parseInt(timer % 60, 10);
                
                hours = hours < 10 ? "0" + hours : hours;
                minutes = minutes < 10 ? "0" + minutes : minutes;
                seconds = seconds < 10 ? "0" + seconds : seconds;
                
                timerElement.textContent = hours + ":" + minutes + ":" + seconds;
                
                if (--timer < 0) {
                    clearInterval(countdown);
                }
            }, 1000);
        }
        
        // نمایش صفحه نهایی
        function showFinalPage() {
            document.getElementById('thirdPage').style.display = 'none';
            document.getElementById('finalPage').style.display = 'block';
        }
        
        // ایجاد افکت‌ها پس از لود صفحه
        window.addEventListener('load', function() {
            createStars();
        });
    </script>

    <!-- فونت Vazirmatn برای پشتیبانی از فارسی -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/rastikerdar/vazirmatn@v33.003/Vazirmatn-font-face.css">
</body>
</html>
