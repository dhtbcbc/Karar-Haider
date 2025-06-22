<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ديوان العراق - تجمع شعراء العراق</title>
    
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* CSS متوافق مع متطلبات التصميم */
        :root {
            --primary-color: #FFF2E0;
            --accent-orange: #FFA857;
            --accent-yellow: #E0B700;
            --accent-brown: #8D6E63;
            --text-color: #333;
            --soft-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
            --transition: all 0.3s ease;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Cairo', sans-serif;
        }
        
        body {
            background-color: var(--primary-color);
            color: var(--text-color);
            line-height: 1.8;
            min-height: 100vh;
            position: relative;
            padding-bottom: 80px;
        }
        
        /* الترويسة */
        header {
            background: linear-gradient(to right, #FFA857, #E0B700);
            padding: 1rem 2rem;
            box-shadow: var(--soft-shadow);
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        
        .header-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .logo i {
            font-size: 2.5rem;
            color: white;
        }
        
        .logo h1 {
            font-size: 1.8rem;
            color: white;
            font-weight: 700;
            letter-spacing: 0;
        }
        
        nav ul {
            display: flex;
            list-style: none;
            gap: 25px;
        }
        
        nav a {
            text-decoration: none;
            color: white;
            font-weight: 600;
            font-size: 1.1rem;
            padding: 8px 15px;
            border-radius: 6px;
            transition: var(--transition);
            position: relative;
        }
        
        nav a:hover {
            background: rgba(255, 255, 255, 0.2);
        }
        
        nav a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 3px;
            background: white;
            transition: var(--transition);
        }
        
        nav a:hover::after {
            width: 100%;
        }
        
        /* الصفحة الرئيسية */
        .hero {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 2rem;
            text-align: center;
        }
        
        .hero h2 {
            font-size: 2.5rem;
            margin-bottom: 1.5rem;
            color: var(--accent-brown);
            animation: fadeIn 1s ease;
        }
        
        .hero p {
            font-size: 1.2rem;
            max-width: 800px;
            margin: 0 auto 2rem;
            color: #555;
            animation: fadeIn 1.2s ease;
        }
        
        .search-box {
            max-width: 700px;
            margin: 2rem auto;
            background: white;
            border-radius: 50px;
            padding: 8px;
            display: flex;
            box-shadow: var(--soft-shadow);
            animation: slideUp 0.8s ease;
        }
        
        .search-box input {
            flex: 1;
            border: none;
            outline: none;
            padding: 12px 20px;
            font-size: 1.1rem;
            background: transparent;
        }
        
        .search-box button {
            background: var(--accent-orange);
            border: none;
            color: white;
            padding: 12px 30px;
            border-radius: 50px;
            font-weight: 600;
            font-size: 1.1rem;
            cursor: pointer;
            transition: var(--transition);
        }
        
        .search-box button:hover {
            background: var(--accent-yellow);
            transform: scale(1.05);
        }
        
        /* أقسام الشعر */
        .sections {
            max-width: 1200px;
            margin: 4rem auto;
            padding: 0 2rem;
        }
        
        .sections h3 {
            font-size: 2rem;
            text-align: center;
            margin-bottom: 2rem;
            color: var(--accent-brown);
            position: relative;
            padding-bottom: 15px;
        }
        
        .sections h3::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 4px;
            background: var(--accent-orange);
            border-radius: 2px;
        }
        
        .poetry-types {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px;
            margin-bottom: 3rem;
        }
        
        .type-card {
            background: white;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: var(--soft-shadow);
            transition: var(--transition);
            cursor: pointer;
            animation: fadeIn 1s ease;
        }
        
        .type-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.12);
        }
        
        .type-card .icon {
            height: 180px;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(to bottom right, var(--accent-orange), var(--accent-yellow));
        }
        
        .type-card .icon i {
            font-size: 5rem;
            color: white;
        }
        
        .type-card .content {
            padding: 20px;
            text-align: center;
        }
        
        .type-card h4 {
            font-size: 1.5rem;
            margin-bottom: 10px;
            color: var(--accent-brown);
        }
        
        /* معرض الشعراء */
        .featured-poets {
            max-width: 1200px;
            margin: 4rem auto;
            padding: 0 2rem;
        }
        
        .poets-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
        }
        
        .poet-card {
            background: white;
            border-radius: 16px;
            overflow: hidden;
            box-shadow: var(--soft-shadow);
            transition: var(--transition);
            text-align: center;
            animation: fadeIn 1s ease;
        }
        
        .poet-card:hover {
            transform: translateY(-8px);
        }
        
        .poet-img {
            height: 200px;
            width: 200px;
            margin: 20px auto 10px;
            border-radius: 50%;
            overflow: hidden;
            border: 5px solid var(--primary-color);
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            position: relative;
        }
        
        .poet-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
        }
        
        .poet-card:hover .poet-img img {
            transform: scale(1.1);
        }
        
        .poet-info {
            padding: 20px;
        }
        
        .poet-info h4 {
            font-size: 1.4rem;
            margin-bottom: 5px;
            color: var(--accent-brown);
        }
        
        .poet-info p {
            color: #666;
            margin-bottom: 15px;
        }
        
        .follow-btn {
            background: var(--accent-orange);
            color: white;
            border: none;
            padding: 8px 20px;
            border-radius: 50px;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            font-size: 1rem;
        }
        
        .follow-btn:hover {
            background: var(--accent-yellow);
            transform: scale(1.05);
            box-shadow: 0 4px 8px rgba(141, 110, 99, 0.2);
        }
        
        /* قصيدة اليوم */
        .poem-of-day {
            max-width: 1200px;
            margin: 4rem auto;
            padding: 3rem;
            background: var(--accent-brown);
            border-radius: 20px;
            color: white;
            box-shadow: var(--soft-shadow);
            animation: fadeIn 1.2s ease;
        }
        
        .poem-header {
            text-align: center;
            margin-bottom: 2rem;
        }
        
        .poem-header h3 {
            font-size: 2rem;
            margin-bottom: 10px;
        }
        
        .poem-header p {
            font-size: 1.1rem;
            opacity: 0.9;
        }
        
        .poem-content {
            background: rgba(255, 255, 255, 0.1);
            padding: 2rem;
            border-radius: 15px;
            line-height: 2.2;
            font-size: 1.2rem;
            text-align: center;
            font-weight: 500;
        }
        
        .read-btn {
            display: block;
            margin: 2rem auto 0;
            background: var(--accent-orange);
            color: white;
            border: none;
            padding: 12px 35px;
            border-radius: 50px;
            font-weight: 600;
            font-size: 1.1rem;
            cursor: pointer;
            transition: var(--transition);
        }
        
        .read-btn:hover {
            background: var(--accent-yellow);
            transform: scale(1.05);
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        }
        
        /* الفوتر */
        footer {
            background: linear-gradient(to right, #8D6E63, #6d554d);
            color: white;
            padding: 2rem;
            text-align: center;
            position: fixed;
            bottom: 0;
            width: 100%;
            z-index: 1000;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .footer-content p {
            margin: 10px 0;
        }
        
        .social-icons {
            margin-top: 15px;
            display: flex;
            justify-content: center;
            gap: 20px;
        }
        
        .social-icons a {
            color: white;
            font-size: 1.5rem;
            transition: var(--transition);
        }
        
        .social-icons a:hover {
            color: var(--accent-orange);
            transform: translateY(-5px);
        }
        
        /* حركات */
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(40px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        /* تصميم متجاوب */
        @media (max-width: 768px) {
            .header-container {
                flex-direction: column;
                gap: 15px;
            }
            
            nav ul {
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .poem-of-day {
                padding: 1.5rem;
            }
            
            .hero h2 {
                font-size: 2rem;
            }
        }
        
        @media (max-width: 480px) {
            .poetry-types {
                grid-template-columns: 1fr;
            }
            
            .search-box {
                flex-direction: column;
                border-radius: 12px;
                gap: 10px;
            }
            
            .search-box input, 
            .search-box button {
                width: 100%;
                border-radius: 8px;
            }
        }
    </style>
</head>
<body>
    <!-- الترويسة -->
    <header>
        <div class="header-container">
            <div class="logo">
                <i class="fas fa-book-open"></i>
                <h1>ديوان العراق</h1>
            </div>
            
            <nav>
                <ul>
                    <li><a href="#home">الرئيسية</a></li>
                    <li><a href="#poetry-types">أنواع الشعر</a></li>
                    <li><a href="#poets">الشعراء</a></li>
                    <li><a href="#poems">القصائد</a></li>
                    <li><a href="#about">عن الديوان</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- الصفحة الرئيسية -->
    <section id="home" class="hero">
        <h2>مرحباً بكم في ديوان العراق</h2>
        <p>منصة تجمع إبداعات شعراء العراق عبر العصور، نقدم لكم كنوز الشعر العراقي بمختلف أنواعه وأشكاله</p>
        
        <div class="search-box">
            <input type="text" placeholder="ابحث عن قصيدة، شاعر، أو كلمة...">
            <button><i class="fas fa-search"></i> بحث</button>
        </div>
    </section>

    <!-- أقسام الشعر -->
    <section id="poetry-types" class="sections">
        <h3>أنواع الشعر</h3>
        
        <div class="poetry-types">
            <!-- الشعر العمودي -->
            <div class="type-card">
                <div class="icon">
                    <i class="fas fa-book"></i>
                </div>
                <div class="content">
                    <h4>الشعر العمودي</h4>
                    <p>الشعر الذي يلتزم بالوزن والقافية</p>
                </div>
            </div>
            
            <!-- الشعر الحر -->
            <div class="type-card">
                <div class="icon">
                    <i class="fas fa-feather-alt"></i>
                </div>
                <div class="content">
                    <h4>الشعر الحر</h4>
                    <p>شعر التفعيلة المتحرر من القافية الموحدة</p>
                </div>
            </div>
            
            <!-- الشعر النبطي -->
            <div class="type-card">
                <div class="icon">
                    <i class="fas fa-mountain"></i>
                </div>
                <div class="content">
                    <h4>الشعر النبطي</h4>
                    <p>الشعر البدوي بأسلوبه المميز ومفرداته</p>
                </div>
            </div>
            
            <!-- الشعر الشعبي -->
            <div class="type-card">
                <div class="icon">
                    <i class="fas fa-users"></i>
                </div>
                <div class="content">
                    <h4>الشعر الشعبي</h4>
                    <p>الشعر الموزون بلغة الناس اليومية</p>
                </div>
            </div>
        </div>
    </section>

    <!-- الشعراء المميزين -->
    <section id="poets" class="featured-poets">
        <h3>شعراء مميزون</h3>
        
        <div class="poets-grid">
            <!-- الشاعر 1 -->
            <div class="poet-card">
                <div class="poet-img">
                    <img src="https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=200&q=80" alt="محمد مهدي الجواهري">
                </div>
                <div class="poet-info">
                    <h4>محمد مهدي الجواهري</h4>
                    <p>شاعر العراق الكبير</p>
                    <button class="follow-btn">متابعة</button>
                </div>
            </div>
            
            <!-- الشاعر 2 -->
            <div class="poet-card">
                <div class="poet-img">
                    <img src="https://images.unsplash.com/photo-1560250097-0b93528c311a?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=200&q=80" alt="بدر شاكر السياب">
                </div>
                <div class="poet-info">
                    <h4>بدر شاكر السياب</h4>
                    <p>رائد الشعر الحر</p>
                    <button class="follow-btn">متابعة</button>
                </div>
            </div>
            
            <!-- الشاعر 3 -->
            <div class="poet-card">
                <div class="poet-img">
                    <img src="https://images.unsplash.com/photo-1590086782792-42dd2350140d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=200&q=80" alt="نازك الملائكة">
                </div>
                <div class="poet-info">
                    <h4>نازك الملائكة</h4>
                    <p>رائدة الشعر الحر</p>
                    <button class="follow-btn">متابعة</button>
                </div>
            </div>
            
            <!-- الشاعر 4 -->
            <div class="poet-card">
                <div class="poet-img">
                    <img src="https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=200&q=80" alt="عبد الوهاب البياتي">
                </div>
                <div class="poet-info">
                    <h4>عبد الوهاب البياتي</h4>
                    <p>شاعر الحداثة العراقي</p>
                    <button class="follow-btn">متابعة</button>
                </div>
            </div>
        </div>
    </section>

    <!-- قصيدة اليوم -->
    <section id="poems" class="poem-of-day">
        <div class="poem-header">
            <h3>قصيدة اليوم</h3>
            <p>لشاعر العراق الكبير: محمد مهدي الجواهري</p>
        </div>
        
        <div class="poem-content">
            "يا دجلة الخيرِ، يا نهراً يُعانقُهُ<br>
            سحرُ الربى، وعبيرُ الوردِ والزهرِ<br>
            يا دجلةَ الخيرِ، كمْ فيكِ منَ عبرةٍ<br>
            تجري، وكم فيكِ من عبرٍ ومنْ دررِ"
        </div>
        
        <button class="read-btn">اقرأ القصيدة كاملة</button>
    </section>

    <!-- الفوتر -->
    <footer>
        <div class="footer-content">
            <p>ديوان العراق © 2023 - جميع الحقوق محفوظة</p>
            <p>منصة تجمع إبداعات شعراء العراق عبر العصور</p>
            
            <div class="social-icons">
                <a href="#"><i class="fab fa-facebook"></i></a>
                <a href="#"><i class="fab fa-twitter"></i></a>
                <a href="#"><i class="fab fa-instagram"></i></a>
                <a href="#"><i class="fab fa-youtube"></i></a>
            </div>
        </div>
    </footer>

    <script>
        // تفاعلية بسيطة مع الصفحة
        document.addEventListener('DOMContentLoaded', function() {
            // تأثيرات عند التمرير
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.animation = 'fadeIn 1s ease forwards';
                    }
                });
            }, { threshold: 0.1 });
            
            document.querySelectorAll('.type-card, .poet-card, .poem-of-day').forEach(card => {
                card.style.opacity = '0';
                observer.observe(card);
            });
            
            // تأثير عند تمرير الماوس على الأزرار
            document.querySelectorAll('button').forEach(button => {
                button.addEventListener('mouseenter', function() {
                    this.style.transform = 'scale(1.05)';
                });
                
                button.addEventListener('mouseleave', function() {
                    this.style.transform = 'scale(1)';
                });
            });
            
            // تأثير عند تمرير الماوس على روابط التنقل
            document.querySelectorAll('nav a').forEach(link => {
                link.addEventListener('mouseenter', function() {
                    this.style.backgroundColor = 'rgba(255, 255, 255, 0.2)';
                });
                
                link.addEventListener('mouseleave', function() {
                    this.style.backgroundColor = 'transparent';
                });
            });
        });
    </script>
</body>
</html>
