‏<!DOCTYPE ‏<!DOCTYPE html>
‏<html lang="ar" dir="rtl">
‏<head>
‏    <meta charset="UTF-8">
‏    <meta name="viewport" content="width=device-width, initial-scale=1.0">
‏    <title>كرار حيدر - موقع شخصي</title>
    <!-- تحميل Tailwind CSS من CDN لتطبيق الأنماط بسهولة وفعالية -->
‏    <script src="https://cdn.tailwindcss.com"></script>
    <!-- تحميل خط Poppins من Google Fonts، وهو خط عصري ونظيف ومناسب لجميع الأجهزة -->
‏    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <!-- تحميل Font Awesome لإضافة أيقونات جميلة وواضحة لقسم التواصل -->
‏    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
‏    <style>
        /* تعريف الخط الأساسي للصفحة */
‏        body {
‏            font-family: 'Poppins', sans-serif;
            /* لون خلفية رصاصي فاتح أكثر وضوحاً */
‏            background-color: #E0E0E0; /* لون رصاصي فاتح أكثر وضوحًا */
‏            color: #1A202C; /* لون نص داكن لضمان تباين جيد وقابلية قراءة ممتازة */
        }
        /* تعريف لون ذهبي ناعم مخصص لاستخدامه في العناوين والأيقونات والفواصل */
‏        .text-soft-gold {
‏            color: #B8A375; /* كود سداسي عشري للون ذهبي ناعم */
        }
        /* تعريف لون ذهبي ناعم مخصص للحدود (الفواصل بين الأقسام) */
‏        .border-soft-gold {
‏            border-color: #B8A375;
        }
        /* تعريف لون ذهبي ناعم مخصص للخلفيات، على الرغم من عدم استخدامه هنا بشكل مكثف */
‏        .bg-soft-gold {
‏            background-color: #B8A375;
        }
        /* نمط مخصص لزر الأيقونة ليتناسب مع تصميم الأيقونات الأخرى */
‏        .icon-button {
‏            display: flex;
‏            align-items: center;
‏            gap: 0.75rem; /* 12px */
‏            transition: color 0.3s ease;
        }
‏        .icon-button:hover {
‏            color: #B8A375; /* لون ذهبي ناعم عند التحويم */
        }
‏    </style>
‏</head>
<!-- جسم الصفحة، يتم توسيطه في المنتصف لتوفير مظهر جذاب على الشاشات الكبيرة -->
‏<body class="flex justify-center items-center min-h-screen p-4">
    <!-- الحاوية الرئيسية للمحتوى، تحدد أقصى عرض وتوسيطها في المنتصف، مع ظلال مستديرة لإضافة لمسة جمالية -->
‏    <div class="max-w-3xl w-full bg-white rounded-xl shadow-lg p-8 sm:p-12 space-y-4 md:space-y-6">
        <!-- قسم العنوان الرئيسي للموقع (اسم كرار حيدر) مع إطار بارز -->
‏        <header class="text-center p-6 border-2 border-soft-gold rounded-lg shadow-sm">
‏            <h1 class="text-4xl sm:text-5xl font-extrabold text-gray-900 leading-tight">كرار حيدر</h1>
‏        </header>

        <!-- قسم مولد الشعر بأسلوب جبار رشيد (ميزة تستخدم Gemini API) -->
        <!-- تم إزالة border-t هنا -->
‏        <section class="space-y-4 pt-4 pb-8 text-center">
‏            <h2 class="text-2xl sm:text-3xl font-semibold text-soft-gold mb-4">شعر بأسلوب جبار رشيد 📜</h2>
‏            <div class="flex flex-col items-center gap-4">
‏                <textarea id="poemTopicInput"
‏                          class="w-full p-4 rounded-lg border border-gray-300 focus:ring-2 focus:ring-soft-gold focus:border-transparent text-lg text-gray-800 text-right"
‏                          rows="3"
‏                          placeholder="اكتب موضوع الشعر الذي تريده (مثال: الحب، الفراق، الأمل)..."></textarea>
‏                <button id="generatePoemBtn"
‏                        class="bg-soft-gold text-white font-bold py-3 px-6 rounded-lg shadow-md hover:bg-opacity-90 transition-all duration-300 transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-soft-gold focus:ring-opacity-50">
                    اكتب لي شعرًا ✍️
‏                </button>
                <!-- مؤشر التحميل الذي يظهر أثناء انتظار رد LLM -->
‏                <div id="loadingPoemIndicator" class="mt-4 text-gray-600 hidden">
                    جاري كتابة القصيدة...
‏                </div>
                <!-- المكان الذي ستعرض فيه القصيدة التي تم توليدها -->
‏                <div id="generatedPoem" class="mt-6 p-4 bg-gray-50 rounded-lg shadow-inner w-full text-lg leading-relaxed text-gray-800 whitespace-pre-wrap text-center">
                    <!-- القصيدة ستظهر هنا -->
‏                </div>
                <!-- رسالة الخطأ -->
‏                <div id="poemError" class="mt-4 text-red-600 hidden"></div>
‏            </div>
‏        </section>

        <!-- قسم معلومات التواصل المعدل -->
        <!-- تم إضافة border-t هنا ليكون خط فاصل جديد فوق هذا القسم -->
‏        <section class="space-y-4 pt-4 border-t border-soft-gold">
‏            <h2 class="text-2xl sm:text-3xl font-semibold text-soft-gold mb-4 text-center">تواصل معي</h2>
            <!-- استخدام فليكس بوكس لعرض العناصر أفقياً وتوسيطها -->
‏            <div class="flex flex-wrap justify-center gap-x-8 gap-y-4 text-lg leading-relaxed text-gray-700">
                <!-- حساب إنستغرام مع أيقونة ورابط مباشر -->
‏                <a href="https://www.instagram.com/k9x9i" target="_blank" class="icon-button text-gray-900 hover:text-soft-gold transition-colors">
‏                    <i class="fab fa-instagram text-soft-gold text-xl"></i>
‏                    <span>Instagram: k9x9i</span>
‏                </a>
                <!-- حساب تيليجرام مع أيقونة ورابط مباشر -->
‏                <a href="https://t.me/K1_ar1" target="_blank" class="icon-button text-gray-900 hover:text-soft-gold transition-colors">
‏                    <i class="fab fa-telegram-plane text-soft-gold text-xl"></i>
‏                    <span>Telegram: @K1_ar1</span>
‏                </a>
‏            </div>
‏        </section>

        <!-- قسم حقوق النشر في التذييل -->
‏        <footer class="text-center pt-8 text-sm text-gray-600">
‏            <p>جميع الحقوق محفوظة كرار حيدر 2024 ©️</p>
‏        </footer>
‏    </div>

‏    <script>
        // دالة للتعامل مع توليد الشعر بأسلوب جبار رشيد
‏        document.getElementById('generatePoemBtn').addEventListener('click', async () => {
‏            const poemTopicInput = document.getElementById('poemTopicInput');
‏            const generatedPoem = document.getElementById('generatedPoem');
‏            const loadingIndicator = document.getElementById('loadingPoemIndicator');
‏            const generateButton = document.getElementById('generatePoemBtn');
‏            const poemError = document.getElementById('poemError');

‏            const topic = poemTopicInput.value.trim();

‏            if (!topic) {
‏                poemError.textContent = "الرجاء إدخال موضوع للشعر.";
‏                poemError.classList.remove('hidden');
‏                generatedPoem.textContent = '';
‏                return;
‏            } else {
‏                poemError.classList.add('hidden');
            }

            // عرض مؤشر التحميل وإخفاء النص السابق
‏            loadingIndicator.classList.remove('hidden');
‏            generatedPoem.textContent = '';
‏            generateButton.disabled = true; // تعطيل الزر أثناء التحميل

‏            try {
‏                let chatHistory = [];
                // الأمر للنموذج لتوليد شعر بأسلوب جبار رشيد
‏                const prompt = `اكتب قصيدة رومانسية أو تأملية موجزة بأسلوب الشاعر العراقي جبار رشيد عن موضوع: ${topic}. استخدم مفردات وأساليب قريبة من أسلوبه المعروف في الشعر الحر والعاطفي. لا تتجاوز القصيدة 6 أسطر.`;
‏                chatHistory.push({ role: "user", parts: [{ text: prompt }] });

‏                const payload = { contents: chatHistory };
‏                const apiKey = "";
‏                const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

‏                const response = await fetch(apiUrl, {
‏                    method: 'POST',
‏                    headers: { 'Content-Type': 'application/json' },
‏                    body: JSON.stringify(payload)
                });

‏                const result = await response.json();

‏                if (result.candidates && result.candidates.length > 0 &&
‏                    result.candidates[0].content && result.candidates[0].content.parts &&
‏                    result.candidates[0].content.parts.length > 0) {
‏                    const text = result.candidates[0].content.parts[0].text;
‏                    generatedPoem.textContent = text; // عرض القصيدة التي تم توليدها
‏                } else {
‏                    generatedPoem.textContent = "حدث خطأ في توليد الشعر. يرجى المحاولة مرة أخرى.";
‏                    console.error("Gemini API returned an unexpected structure for poem generation:", result);
                }
‏            } catch (error) {
‏                generatedPoem.textContent = "عذراً، حدث خطأ أثناء الاتصال بالخادم. يرجى المحاولة مرة أخرى.";
‏                console.error("Error calling Gemini API for poem generation:", error);
‏            } finally {
‏                loadingIndicator.classList.add('hidden');
‏                generateButton.disabled = false;
            }
        });
‏    </script>
‏</body>
‏</html>
