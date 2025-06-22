<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ديوان العراق - تجمع شعراء العراق</title>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* المتغيرات والأساسيات */
        :root {
            --background: #F8F1E5;
            --card-bg: #FFFFFF;
            --primary: #D4B996;
            --accent: #A78A7F;
            --text: #4A403A;
            --light-text: #8D7B68;
            --hover: #E6D5C4;
            --shadow: 0 4px 15px rgba(138, 121, 107, 0.12);
            --transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Cairo', sans-serif;
        }
        
        body {
            background-color: var(--background);
            color: var(--text);
            min-height: 100vh;
            padding-bottom: 80px;
            position: relative;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        /* الترويسة */
        header {
            background: linear-gradient(to right, var(--primary), rgba(212, 185, 150, 0.9));
            padding: 1rem 2rem;
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 1000;
            backdrop-filter: blur(5px);
        }
        
        .header-container {
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
        }
        
        /* نظام الطبقات */
        .app-layers {
            min-height: 70vh;
            position: relative;
            margin-top: 30px;
        }
        
        .layer {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0;
            visibility: hidden;
            transform: translateX(30px);
            transition: var(--transition);
            padding: 20px;
            background: var(--background);
            border-radius: 20px;
            box-shadow: var(--shadow);
        }
        
        .layer.active {
            opacity: 1;
            visibility: visible;
            transform: translateX(0);
            z-index: 100;
        }
        
        .layer-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 2px solid var(--primary);
        }
        
        .layer-header h2 {
            font-size: 1.8rem;
            color: var(--accent);
        }
        
        .back-btn {
            background: var(--primary);
            color: white;
            border: none;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: var(--transition);
            font-size: 1.2rem;
        }
        
        .back-btn:hover {
            background: var(--accent);
            transform: rotate(-10deg);
        }
        
        /* الطبقة الأولى: الشعراء */
        .poets-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 25px;
        }
        
        .poet-card {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 25px;
            text-align: center;
            box-shadow: var(--shadow);
            transition: var(--transition);
            cursor: pointer;
            border: 1px solid rgba(167, 138, 127, 0.1);
            animation: fadeIn 0.6s ease forwards;
            opacity: 0;
        }
        
        .poet-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 10px 25px rgba(138, 121, 107, 0.2);
            border-color: var(--primary);
        }
        
        .poet-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, var(--primary), var(--accent));
            margin: 0 auto 15px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 2rem;
        }
        
        .poet-card h3 {
            font-size: 1.4rem;
            color: var(--accent);
            margin-bottom: 5px;
        }
        
        .poet-card p {
            color: var(--light-text);
            font-size: 0.95rem;
        }
        
        /* الطبقة الثانية: الأقسام الشعرية */
        .categories-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 20px;
        }
        
        .category-card {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 25px 15px;
            text-align: center;
            box-shadow: var(--shadow);
            transition: var(--transition);
            cursor: pointer;
            border: 1px solid rgba(167, 138, 127, 0.1);
            animation: fadeIn 0.6s ease forwards;
            opacity: 0;
        }
        
        .category-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(138, 121, 107, 0.15);
            background: linear-gradient(to bottom, var(--card-bg), #fcf9f5);
        }
        
        .category-icon {
            font-size: 2.5rem;
            color: var(--accent);
            margin-bottom: 15px;
            transition: var(--transition);
        }
        
        .category-card:hover .category-icon {
            transform: scale(1.1);
            color: var(--primary);
        }
        
        .category-card h3 {
            font-size: 1.3rem;
            color: var(--accent);
        }
        
        /* الطبقة الثالثة: القصائد */
        .poems-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 25px;
        }
        
        .poem-card {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 25px;
            box-shadow: var(--shadow);
            transition: var(--transition);
            border: 1px solid rgba(167, 138, 127, 0.1);
            animation: fadeIn 0.6s ease forwards;
            opacity: 0;
            display: flex;
            flex-direction: column;
            height: 100%;
        }
        
        .poem-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(138, 121, 107, 0.18);
        }
        
        .poem-title {
            font-size: 1.4rem;
            color: var(--accent);
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px dashed var(--primary);
        }
        
        .poem-excerpt {
            color: var(--text);
            line-height: 1.9;
            font-size: 1.1rem;
            flex-grow: 1;
            margin-bottom: 20px;
            font-weight: 500;
        }
        
        .poem-actions {
            display: flex;
            gap: 10px;
            justify-content: space-between;
        }
        
        .btn {
            padding: 10px 20px;
            border-radius: 50px;
            border: none;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 1rem;
        }
        
        .read-btn {
            background: var(--primary);
            color: white;
        }
        
        .read-btn:hover {
            background: var(--accent);
            transform: translateY(-3px);
            box-shadow: 0 4px 10px rgba(167, 138, 127, 0.3);
        }
        
        .copy-btn {
            background: rgba(212, 185, 150, 0.15);
            color: var(--accent);
        }
        
        .copy-btn:hover {
            background: rgba(167, 138, 127, 0.25);
            transform: translateY(-3px);
        }
        
        /* الفوتر */
        footer {
            background: linear-gradient(to right, var(--accent), #8D6E63);
            color: white;
            padding: 1.5rem;
            text-align: center;
            position: fixed;
            bottom: 0;
            width: 100%;
            z-index: 1000;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        
        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 10px;
        }
        
        .social-links a {
            color: white;
            font-size: 1.3rem;
            transition: var(--transition);
        }
        
        .social-links a:hover {
            color: var(--hover);
            transform: translateY(-3px);
        }
        
        /* حركات وتأثيرات */
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
        
        /* تصميم متجاوب */
        @media (max-width: 768px) {
            .poets-grid, .categories-grid, .poems-container {
                grid-template-columns: repeat(auto-fill, minmax(100%, 1fr));
            }
            
            .layer-header h2 {
                font-size: 1.5rem;
            }
        }
        
        /* التأخر في الظهور للعناصر */
        .poet-card:nth-child(1) { animation-delay: 0.1s; }
        .poet-card:nth-child(2) { animation-delay: 0.2s; }
        .poet-card:nth-child(3) { animation-delay: 0.3s; }
        .poet-card:nth-child(4) { animation-delay: 0.4s; }
        .poet-card:nth-child(5) { animation-delay: 0.5s; }
        .poet-card:nth-child(6) { animation-delay: 0.6s; }
        
        .category-card:nth-child(1) { animation-delay: 0.1s; }
        .category-card:nth-child(2) { animation-delay: 0.2s; }
        .category-card:nth-child(3) { animation-delay: 0.3s; }
        .category-card:nth-child(4) { animation-delay: 0.4s; }
        .category-card:nth-child(5) { animation-delay: 0.5s; }
        
        .poem-card:nth-child(1) { animation-delay: 0.1s; }
        .poem-card:nth-child(2) { animation-delay: 0.2s; }
        .poem-card:nth-child(3) { animation-delay: 0.3s; }
        .poem-card:nth-child(4) { animation-delay: 0.4s; }
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
        </div>
    </header>

    <!-- نظام الطبقات -->
    <div class="container">
        <div class="app-layers">
            <!-- الطبقة الأولى: الشعراء -->
            <div class="layer active" id="poets-layer">
                <div class="layer-header">
                    <button class="back-btn" onclick="goHome()" style="visibility: hidden;">
                        <i class="fas fa-arrow-left"></i>
                    </button>
                    <h2>شعراء العراق</h2>
                </div>
                
                <div class="poets-grid">
                    <!-- الشعراء سيعرضون هنا -->
                </div>
            </div>
            
            <!-- الطبقة الثانية: الأقسام الشعرية -->
            <div class="layer" id="categories-layer">
                <div class="layer-header">
                    <button class="back-btn" onclick="showPoets()">
                        <i class="fas fa-arrow-left"></i>
                    </button>
                    <h2 id="categories-title">أقسام شعرية</h2>
                </div>
                
                <div class="categories-grid">
                    <!-- الأقسام ستعرض هنا -->
                </div>
            </div>
            
            <!-- الطبقة الثالثة: القصائد -->
            <div class="layer" id="poems-layer">
                <div class="layer-header">
                    <button class="back-btn" onclick="showCategories()">
                        <i class="fas fa-arrow-left"></i>
                    </button>
                    <h2 id="poems-title">قصائد</h2>
                </div>
                
                <div class="poems-container">
                    <!-- القصائد ستعرض هنا -->
                </div>
            </div>
        </div>
    </div>

    <!-- الفوتر -->
    <footer>
        <div class="footer-content">
            <p>© 2025 كرار حيدر – جميع الحقوق محفوظة</p>
            <div class="social-links">
                <a href="#" title="YouTube"><i class="fab fa-youtube"></i></a>
                <a href="#" title="TikTok"><i class="fab fa-tiktok"></i></a>
            </div>
        </div>
    </footer>

    <script>
        // بيانات الشعراء والأقسام والقصائد
        const poets = [
            { id: 1, name: "بدر شاكر السياب", description: "شاعر عراقي رائد من رواد الشعر الحر" },
            { id: 2, name: "مظفر النواب", description: "شاعر عراقي معاصر، اشتهر بقصائده السياسية" },
            { id: 3, name: "عبد الرزاق عبد الواحد", description: "شاعر عراقي كبير، صاحب القصائد الوطنية" },
            { id: 4, name: "نازك الملائكة", description: "رائدة الشعر الحر في الأدب العربي" },
            { id: 5, name: "محمد مهدي الجواهري", description: "شاعر العرب الأكبر وأحد أبرز شعراء العراق" },
            { id: 6, name: "عبد الوهاب البياتي", description: "من أهم شعراء العراق والعالم العربي" },
            { id: 7, name: "بلند الحيدري", description: "شاعر عراقي رائد من رواد الحداثة" },
            { id: 8, name: "سعدي يوسف", description: "شاعر وكاتب ومترجم عراقي" },
            { id: 9, name: "فاضل العزاوي", description: "شاعر وروائي عراقي معاصر" },
            { id: 10, name: "حسين مردان", description: "شاعر وكاتب مسرحي عراقي" }
        ];
        
        const categories = [
            { id: 1, name: "الحب", icon: "fas fa-heart" },
            { id: 2, name: "الغزل", icon: "fas fa-rose" },
            { id: 3, name: "الحكمة", icon: "fas fa-lightbulb" },
            { id: 4, name: "الفخر", icon: "fas fa-crown" },
            { id: 5, name: "الحنين", icon: "fas fa-home" },
            { id: 6, name: "الوطن", icon: "fas fa-flag" },
            { id: 7, name: "الفراق", icon: "fas fa-sad-cry" }
        ];
        
        const poems = {
            love: [
                { 
                    title: "أغنية حب", 
                    excerpt: "أحبكِ مثلما تحبُّ الورودُ الربيعا\nومثلما تحبُّ الطيورُ الغصون\nأحبكِ مثلما تحبُّ النجومُ الدجى\nومثلما تحبُّ العيون العيون" 
                },
                { 
                    title: "لقاء", 
                    excerpt: "ولما التقينا بعد طول الفراق\nتساقطت الأقنعة من عيوننا\nوكأننا لم نفترق ساعة\nولم تكن بيننا حدود ولا وطن" 
                },
                { 
                    title: "في عينيك", 
                    excerpt: "في عينيكِ بحرٌ من الأسرار\nوشمسٌ تشرقُ في كلِّ فجر\nفي عينيكِ وطنٌ من الأحلام\nوجنةٌ تغمرني بالسحر" 
                }
            ],
            wisdom: [
                { 
                    title: "الحكمة", 
                    excerpt: "الحكمةُ بحرٌ لا قرارَ له\nوالحكماءُ فيه صيادون\nمن صبرَ في الصيدِ أمسى غنياً\nومن عجلَ عاد بالخسران" 
                },
                { 
                    title: "العمر", 
                    excerpt: "العمرُ أيامٌ تمُرُّ سريعاً\nفلا تضيعْ وقتك في الندم\nاصنعْ من اللحظاتِ درراً\nومن الأيامِ عقداً يفتخر به الزمن" 
                },
                { 
                    title: "الصبر", 
                    excerpt: "الصبرُ مفتاحُ الفرجِ دوماً\nومن يصبرْ يدركْ ما يريد\nوالدهرُ يدورُ على كلِّ حال\nوما يدومُ سوى خلقِ العبيد" 
                }
            ],
            homeland: [
                { 
                    title: "دجلة الخير", 
                    excerpt: "يا دجلة الخيرِ يا نهراً يُعانقُهُ\nسحرُ الربى، وعبيرُ الوردِ والزهرِ\nيا دجلةَ الخيرِ، كم فيك منَ عبرةٍ\nتجري، وكم فيكِ من عبرٍ ومنْ دررِ" 
                },
                { 
                    title: "بلادي", 
                    excerpt: "بلادي وإن جارتْ عليَّ عزيزةٌ\nوأهلي وإن ضنوا عليَّ كرامُ\nأُحبُّ تربتها وسماءَ ربوعها\nوأُحبُّ ناسَها الكرامَ الأعلام" 
                },
                { 
                    title: "العراق", 
                    excerpt: "العراقُ أرضُ الأنبياءِ وحضرةُ\nالعلمِ والفنِّ والأدبِ الرصين\nهي أُمُّ الدنيا ومنبعُ العطاءِ\nوسراجُ الشرقِ في كلِّ حين" 
                }
            ]
        };
        
        // متغيرات حالة التطبيق
        let currentPoet = null;
        let currentCategory = null;
        
        // تهيئة التطبيق
        function initializeApp() {
            renderPoets();
        }
        
        // عرض الشعراء
        function renderPoets() {
            const poetsGrid = document.querySelector('.poets-grid');
            poetsGrid.innerHTML = '';
            
            poets.forEach(poet => {
                const poetCard = document.createElement('div');
                poetCard.className = 'poet-card';
                poetCard.innerHTML = `
                    <div class="poet-icon">
                        <i class="fas fa-user"></i>
                    </div>
                    <h3>${poet.name}</h3>
                    <p>${poet.description}</p>
                `;
                poetCard.addEventListener('click', () => showCategories(poet));
                poetsGrid.appendChild(poetCard);
            });
        }
        
        // عرض الأقسام الشعرية
        function showCategories(poet) {
            currentPoet = poet;
            document.getElementById('categories-title').textContent = `أقسام شعرية: ${poet.name}`;
            
            const categoriesGrid = document.querySelector('.categories-grid');
            categoriesGrid.innerHTML = '';
            
            categories.forEach(category => {
                const categoryCard = document.createElement('div');
                categoryCard.className = 'category-card';
                categoryCard.innerHTML = `
                    <div class="category-icon">
                        <i class="${category.icon}"></i>
                    </div>
                    <h3>${category.name}</h3>
                `;
                categoryCard.addEventListener('click', () => showPoems(category));
                categoriesGrid.appendChild(categoryCard);
            });
            
            switchLayer('categories-layer');
        }
        
        // عرض القصائد
        function showPoems(category) {
            currentCategory = category;
            document.getElementById('poems-title').textContent = `${category.name}: ${currentPoet.name}`;
            
            const poemsContainer = document.querySelector('.poems-container');
            poemsContainer.innerHTML = '';
            
            // اختيار مجموعة قصائد عشوائية بناءً على التصنيف
            let selectedPoems = [];
            if (category.name === 'الحب' || category.name === 'الغزل') {
                selectedPoems = [...poems.love];
            } else if (category.name === 'الحكمة') {
                selectedPoems = [...poems.wisdom];
            } else {
                selectedPoems = [...poems.homeland];
            }
            
            // إضافة القصائد
            selectedPoems.forEach(poem => {
                const poemCard = document.createElement('div');
                poemCard.className = 'poem-card';
                poemCard.innerHTML = `
                    <div class="poem-title">${poem.title}</div>
                    <div class="poem-excerpt">${poem.excerpt}</div>
                    <div class="poem-actions">
                        <button class="btn copy-btn" onclick="copyPoem(this)">
                            <i class="fas fa-copy"></i> نسخ القصيدة
                        </button>
                        <button class="btn read-btn">
                            <i class="fas fa-book-open"></i> قراءة كاملة
                        </button>
                    </div>
                `;
                poemsContainer.appendChild(poemCard);
            });
            
            switchLayer('poems-layer');
        }
        
        // التبديل بين الطبقات
        function switchLayer(layerId) {
            document.querySelectorAll('.layer').forEach(layer => {
                layer.classList.remove('active');
            });
            document.getElementById(layerId).classList.add('active');
        }
        
        // العودة إلى الشعراء
        function showPoets() {
            switchLayer('poets-layer');
        }
        
        // العودة إلى الأقسام
        function showCategories() {
            switchLayer('categories-layer');
        }
        
        // العودة إلى الصفحة الرئيسية
        function goHome() {
            switchLayer('poets-layer');
        }
        
        // نسخ القصيدة
        function copyPoem(btn) {
            const poemText = btn.closest('.poem-card').querySelector('.poem-excerpt').textContent;
            navigator.clipboard.writeText(poemText).then(() => {
                const originalText = btn.innerHTML;
                btn.innerHTML = '<i class="fas fa-check"></i> تم النسخ';
                setTimeout(() => {
                    btn.innerHTML = originalText;
                }, 2000);
            });
        }
        
        // تهيئة التطبيق عند تحميل الصفحة
        document.addEventListener('DOMContentLoaded', initializeApp);
    </script>
</body>
</html>
