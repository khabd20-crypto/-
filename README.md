
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>بنك الأسئلة - الاختبار التفاعلي</title>
    <style>
        :root {
            --primary: #3498db;
            --secondary: #2c3e50;
            --success: #2ecc71;
            --danger: #e74c3c;
            --warning: #f39c12;
            --light: #ecf0f1;
            --dark: #34495e;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }
        
        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 30px 0;
            text-align: center;
            border-radius: 10px;
            margin-bottom: 30px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        header h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }
        
        header p {
            font-size: 1.2rem;
            opacity: 0.9;
        }
        
        .card {
            background: white;
            border-radius: 10px;
            padding: 25px;
            margin-bottom: 20px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s ease;
        }
        
        .card:hover {
            transform: translateY(-5px);
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--secondary);
        }
        
        input, select {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
            transition: border 0.3s;
        }
        
        input:focus, select:focus {
            border-color: var(--primary);
            outline: none;
            box-shadow: 0 0 0 2px rgba(52, 152, 219, 0.2);
        }
        
        .btn {
            display: inline-block;
            background: var(--primary);
            color: white;
            padding: 12px 25px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: all 0.3s ease;
            text-align: center;
        }
        
        .btn:hover {
            background: #2980b9;
            transform: translateY(-2px);
        }
        
        .btn-success {
            background: var(--success);
        }
        
        .btn-success:hover {
            background: #27ae60;
        }
        
        .btn-danger {
            background: var(--danger);
        }
        
        .btn-danger:hover {
            background: #c0392b;
        }
        
        .btn-block {
            display: block;
            width: 100%;
        }
        
        .hidden {
            display: none;
        }
        
        .question-container {
            margin-bottom: 30px;
        }
        
        .question-number {
            font-size: 1.2rem;
            font-weight: 600;
            color: var(--primary);
            margin-bottom: 10px;
        }
        
        .question-text {
            font-size: 1.1rem;
            margin-bottom: 20px;
            line-height: 1.8;
        }
        
        .options-container {
            display: grid;
            gap: 10px;
        }
        
        .option {
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .option:hover {
            background-color: #f8f9fa;
        }
        
        .option.selected {
            background-color: #e1f5fe;
            border-color: var(--primary);
        }
        
        .option.correct {
            background-color: #e8f5e9;
            border-color: var(--success);
        }
        
        .option.incorrect {
            background-color: #ffebee;
            border-color: var(--danger);
        }
        
        .navigation {
            display: flex;
            justify-content: space-between;
            margin-top: 30px;
        }
        
        .results-container {
            text-align: center;
        }
        
        .score {
            font-size: 3rem;
            font-weight: 700;
            color: var(--primary);
            margin: 20px 0;
        }
        
        .progress-bar {
            height: 10px;
            background-color: #e0e0e0;
            border-radius: 5px;
            margin-bottom: 20px;
            overflow: hidden;
        }
        
        .progress {
            height: 100%;
            background-color: var(--primary);
            width: 0%;
            transition: width 0.5s ease;
        }
        
        .timer {
            font-size: 1.2rem;
            font-weight: 600;
            color: var(--secondary);
            margin-bottom: 20px;
        }
        
        .footer {
            text-align: center;
            margin-top: 40px;
            padding-top: 20px;
            border-top: 1px solid #eee;
            color: #7f8c8d;
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 10px;
            }
            
            header h1 {
                font-size: 2rem;
            }
            
            .card {
                padding: 15px;
            }
            
            .navigation {
                flex-direction: column;
                gap: 10px;
            }
            
            .btn {
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>بنك الأسئلة - الاختبار التفاعلي</h1>
            <p>اختبار في تصنيف التفاعلات الكيميائية والتفاعلات في المحاليل المائية</p>
        </header>
        
        <!-- نموذج بيانات الطالب -->
        <div id="student-form" class="card">
            <h2>بيانات الطالب</h2>
            <div class="form-group">
                <label for="student-name">الاسم الثلاثي</label>
                <input type="text" id="student-name" placeholder="أدخل اسمك الثلاثي" required>
            </div>
            <div class="form-group">
                <label for="student-class">الشعبة</label>
                <input type="text" id="student-class" placeholder="أدخل الشعبة" required>
            </div>
            <button id="start-test" class="btn btn-block">بدء الاختبار</button>
        </div>
        
        <!-- شاشة الاختبار -->
        <div id="test-screen" class="hidden">
            <div class="card">
                <div class="timer" id="timer">الوقت المتبقي: 60:00</div>
                <div class="progress-bar">
                    <div class="progress" id="progress"></div>
                </div>
                <div class="question-number" id="question-number">السؤال 1 من 50</div>
                <div class="question-text" id="question-text"></div>
                <div class="options-container" id="options-container"></div>
                <div class="navigation">
                    <button id="prev-btn" class="btn">السابق</button>
                    <button id="next-btn" class="btn">التالي</button>
                </div>
            </div>
            <button id="submit-test" class="btn btn-danger btn-block">إنهاء الاختبار</button>
        </div>
        
        <!-- شاشة النتائج -->
        <div id="results-screen" class="card hidden">
            <div class="results-container">
                <h2>نتيجة الاختبار</h2>
                <div class="score" id="final-score">0/50</div>
                <p id="student-info"></p>
                <p id="percentage"></p>
                <p id="performance-message"></p>
                <div class="navigation">
                    <button id="review-btn" class="btn">مراجعة الإجابات</button>
                    <button id="retake-btn" class="btn btn-success">إعادة الاختبار</button>
                </div>
            </div>
        </div>
        
        <div class="footer">
            <p>بنك الأسئلة - الاختبار التفاعلي &copy; 2023</p>
        </div>
    </div>

    <script>
        // بيانات الأسئلة
        const questions = [
            {
                question: "المقصود بالتفاعل الكيميائي؟",
                options: [
                    "عملية يتغير فيها شكل المادة فقط",
                    "عملية تتكون فيها مواد جديدة بخصائص مختلفة",
                    "عملية فيزيائية لا تتغير فيها المواد"
                ],
                correct: 1
            },
            {
                question: "من أمثلة تفاعلات الاتحاد:",
                options: [
                    "H₂ + O₂ → 2H₂O⁺",
                    "KClO₃ → 2KCl + 3O₂⁻",
                    "Cu + 2AgNO₃ → Cu(NO₃)₂ + 2Ag"
                ],
                correct: 1
            },
            {
                question: "في تفاعل التحلل، ينتج:",
                options: [
                    "مركب جديد",
                    "عنصران أو أكثر من مركب واحد",
                    "محلول متجانس"
                ],
                correct: 1
            },
            {
                question: "أي مما يلي يصف تفاعل الإحلال البسيط؟",
                options: [
                    "اتحاد عنصرين لتكوين مركب",
                    "إحلال عنصر محل عنصر آخر في مركب",
                    "تحلل مركب إلى عناصره"
                ],
                correct: 1
            },
            {
                question: "التفاعل: Cu + ZnSO₄ → ZnSO₄ + Cu هو مثال على:",
                options: [
                    "اتحاد",
                    "إحلال بسيط",
                    "إحلال مزدوج"
                ],
                correct: 1
            },
            {
                question: "ما نوع التفاعل: NaCl + AgNO₃ → AgCl + NaNO₃",
                options: [
                    "إحلال بسيط",
                    "إحلال مزدوج",
                    "تحليل"
                ],
                correct: 1
            },
            {
                question: "أي من التالي يمثل تفاعل التحلل؟",
                options: [
                    "CaCO₃ → CaO + CO₂",
                    "H₂ + Cl₂ → 2HCl",
                    "Fe + CuSO₄ → FeSO₄ + Cu"
                ],
                correct: 0
            },
            {
                question: "تفاعل اتخاذ الأكسجين مع الحديد لتكوين صدا الحديد مثال على:",
                options: [
                    "اتحاد",
                    "احتراق",
                    "إحلال بسيط"
                ],
                correct: 0
            },
            {
                question: "التفاعل: Na + Cl₂ → 2NaCl⁺ يُصنف على أنه:",
                options: [
                    "اتحاد",
                    "تحليل",
                    "إحلال مزدوج"
                ],
                correct: 0
            },
            {
                question: "في تفاعلات الإحلال، يعتمد حدوث التفاعل على:",
                options: [
                    "درجة الحرارة فقط",
                    "النشاط الكيميائي للعناصر",
                    "لون العناصر"
                ],
                correct: 1
            },
            {
                question: "يقصد بسلسلة النشاط الكيميائي أنها ترتيب العناصر وفق:",
                options: [
                    "أعدادها الذرية",
                    "نشاطها الكيميائي",
                    "درجات انصهارها"
                ],
                correct: 1
            },
            {
                question: "العنصر الأعلى في سلسلة النشاط الكيميائي:",
                options: [
                    "أقل نشاطاً",
                    "أكثر نشاطاً",
                    "متعدل"
                ],
                correct: 1
            },
            {
                question: "أي من العناصر التالية يمكنه إحلال النحاس من محاليله؟",
                options: [
                    "الفضة",
                    "الحديد",
                    "الزنبق"
                ],
                correct: 1
            },
            {
                question: "عند وضع فلز نشط في محلول يحتوي على أيونات فلز أقل نشاطا، يحدث:",
                options: [
                    "لا تفاعل",
                    "تفاعل إحلال بسيط",
                    "تفاعل إحلال مزدوج"
                ],
                correct: 1
            },
            {
                question: "يستخدم الكيميائي سلسلة النشاط الكيميائي للتنبؤ ب:",
                options: [
                    "لون اللهب",
                    "قابلية الذوبان",
                    "حدوث تفاعلات الإحلال"
                ],
                correct: 2
            },
            {
                question: "يقصد بالمحلول المائي أنه:",
                options: [
                    "محلول يذوب فيه المذاب في الماء",
                    "محلول يحتوي على الكحول",
                    "محلول لا يحتوي على ماء"
                ],
                correct: 0
            },
            {
                question: "المركبات التي تتكون إلى أيونات في الماء تُسمى:",
                options: [
                    "غير إلكتروليتية",
                    "إلكتروليتية",
                    "غازية"
                ],
                correct: 1
            },
            {
                question: "عند ذوبان NaCl في الماء، ينتج:",
                options: [
                    "Cl⁻ و Na⁺",
                    "NaCl₂",
                    "H₂O₂"
                ],
                correct: 0
            },
            {
                question: "المركب الذي لا يتفكك إلى أيونات في الماء هو:",
                options: [
                    "NaCl",
                    "CH₃OH",
                    "HCl"
                ],
                correct: 1
            },
            {
                question: "التفاعل الذي ينتج عنه راسب أو ماء أو غاز يُعرف بأنه:",
                options: [
                    "تفاعل إحلال مزدوج",
                    "تفاعل احتراق",
                    "تفاعل تحليل"
                ],
                correct: 0
            },
            {
                question: "المعادلة الأيونية الكاملة تُظهر:",
                options: [
                    "فقط الأيونات المشاركة في التفاعل",
                    "جميع الأيونات الموجودة في المحلول",
                    "الأيونات المتفرجة فقط"
                ],
                correct: 1
            },
            {
                question: "المعادلة الأيونية النهائية تكتب بعد:",
                options: [
                    "حذف الأيونات المتفرجة",
                    "إضافة الماء",
                    "موازنة الكتلة فقط"
                ],
                correct: 0
            },
            {
                question: "في تفاعل: AgNO₃ + NaCl → AgCl + NaNO₃ الأيون المتفرج هو:",
                options: [
                    "Na⁺",
                    "Ag⁺",
                    "Cl⁻"
                ],
                correct: 0
            },
            {
                question: "نتيجة التفاعل بين HCl و NaOH هي:",
                options: [
                    "NaCl + H₂O",
                    "H₂ + O₂",
                    "Na₂O + Cl₂"
                ],
                correct: 0
            },
            {
                question: "الهدف من موازنة المعادلة هو:",
                options: [
                    "جعل عدد الذرات متساوياً في الطرفين",
                    "تغيير نوع العناصر",
                    "زيادة عدد النواتج"
                ],
                correct: 0
            },
            {
                question: "عدد ذرات الهيدروجين في CH₃ هو:",
                options: [
                    "1",
                    "2",
                    "3"
                ],
                correct: 2
            },
            {
                question: "أي مما يلي معادلة موزونة؟",
                options: [
                    "H₂ + O₂ → H₂O",
                    "H₂ + O₂ → 2H₂O",
                    "H₂ + 2O₂ → 2H₂O"
                ],
                correct: 1
            },
            {
                question: "في تفاعل الاحتراق الكامل للهيدروكربونات، ينتج:",
                options: [
                    "CO₂ و H₂O",
                    "CO فقط",
                    "H₂O فقط"
                ],
                correct: 0
            },
            {
                question: "المعادلة التي تمثل تفاعل التعادل هي:",
                options: [
                    "حمض + قاعدة → ملح + ماء",
                    "غاز + ماء → قاعدة + غاز",
                    "ملح + ماء → حمض + غاز"
                ],
                correct: 0
            },
            {
                question: "عند خلط محلول كبريتات الباريوم مع كلوريد الصوديوم، يتكون:",
                options: [
                    "راسب أبيض",
                    "غاز",
                    "محلول صافي"
                ],
                correct: 2
            },
            {
                question: "عند خلط NaOH مع HCl ينتج:",
                options: [
                    "ملح وماء",
                    "غاز وماء",
                    "راسب"
                ],
                correct: 0
            },
            {
                question: "أي مما يلي ينتج غازًا في التفاعل؟",
                options: [
                    "كربونات + حمض",
                    "كلوريد + قاعدة",
                    "ملح + ملح"
                ],
                correct: 0
            },
            {
                question: "في تفاعل الأحماض مع المعادن، الناتج عادة هو:",
                options: [
                    "ملح + غاز هيدروجين",
                    "ماء فقط",
                    "قاعدة فقط"
                ],
                correct: 0
            },
            {
                question: "عند تفاعل حمض الكبريتيك مع كربونات الكالسيوم، ينتج:",
                options: [
                    "ماء وغاز ثاني أكسيد الكربون",
                    "فقط ماء",
                    "فقط غاز"
                ],
                correct: 0
            },
            {
                question: "الفرق بين تفاعل الإحلال البسيط والمزدوج أن:",
                options: [
                    "في البسيط يحدث تبادل بين مركبين",
                    "في المزدوج يتبادل عنصران موضعهما",
                    "في البسيط يحل عنصر محل آخر"
                ],
                correct: 2
            },
            {
                question: "تفاعل الاحتراق يختلف عن الاتحاد بأنه:",
                options: [
                    "ينتج طاقة",
                    "يتطلب وجود أكسجين",
                    "لا يحتاج حرارة"
                ],
                correct: 1
            },
            {
                question: "عند مقارنة نشاط الصوديوم والنحاس، فإن:",
                options: [
                    "الصوديوم أنشط",
                    "النحاس أنشط",
                    "كلاهما متساوي"
                ],
                correct: 0
            },
            {
                question: "عند خلط محلولين دون تكون راسب أو غاز، يدل ذلك على:",
                options: [
                    "حدوث تفاعل",
                    "عدم حدوث تفاعل",
                    "تكون مادة جديدة"
                ],
                correct: 1
            },
            {
                question: "إذا ذابت المادة في الماء وأنتجت أيونات، فهي:",
                options: [
                    "إلكتروليتية",
                    "غير إلكتروليتية",
                    "غازية"
                ],
                correct: 0
            },
            {
                question: "عند تسخين كربونات النحاس، ينتج:",
                options: [
                    "أكسيد النحاس وثاني أكسيد الكربون",
                    "كلوريد النحاس",
                    "ماء فقط"
                ],
                correct: 0
            },
            {
                question: "تفاعل الحديد مع الكبريت لتكوين كبريتيد الحديد هو مثال على:",
                options: [
                    "اتحاد",
                    "تحليل",
                    "احتراق"
                ],
                correct: 0
            },
            {
                question: "عند احتراق الميثان في الهواء، الناتج هو:",
                options: [
                    "H₂O و CO₂",
                    "CO فقط",
                    "H₂ فقط"
                ],
                correct: 0
            },
            {
                question: "التفاعل الذي يتم فيه نقل إلكترونات هو:",
                options: [
                    "احتراق",
                    "أكسدة واختزال",
                    "اتحاد"
                ],
                correct: 1
            },
            {
                question: "المادة التي تفقد إلكترونات في تفاعل الأكسدة والاختزال تُسمى:",
                options: [
                    "عامل مؤكسد",
                    "عامل مختزل",
                    "متفرج"
                ],
                correct: 1
            },
            {
                question: "في تفاعل التعادل، أي من التالي صحيح؟",
                options: [
                    "H⁺ يتحد مع OH⁻ لتكوين H₂O",
                    "Na⁺ يتحد مع Cl⁻ لتكوين NaOH",
                    "H⁺ يتحد مع Cl⁻ لتكوين HCl"
                ],
                correct: 0
            },
            {
                question: "عند كتابة المعادلة الأيونية النهائية، يجب أن تكون:",
                options: [
                    "موزونة بالكتلة والشحنة",
                    "موزونة بالكتلة فقط",
                    "موزونة بالشحنة فقط"
                ],
                correct: 0
            },
            {
                question: "الأيونات المتفرجة لا تظهر في:",
                options: [
                    "المعادلة الأيونية الكاملة",
                    "المعادلة النهائية",
                    "المعادلة الكيميائية الرمزية"
                ],
                correct: 1
            },
            {
                question: "عند ذوبان السكر في الماء لا يتكون تيار كهربائي لأن:",
                options: [
                    "السكر لا يتفكك إلى أيونات",
                    "السكر مركب أيوني",
                    "الماء غير نقي"
                ],
                correct: 0
            },
            {
                question: "أي الأيونات التالية متفرجة في التفاعل بين NaCl و AgNO₃؟",
                options: [
                    "Ag⁺",
                    "Cl⁻",
                    "Na⁺"
                ],
                correct: 2
            }
        ];

        // العناصر DOM
        const studentForm = document.getElementById('student-form');
        const testScreen = document.getElementById('test-screen');
        const resultsScreen = document.getElementById('results-screen');
        const startTestBtn = document.getElementById('start-test');
        const submitTestBtn = document.getElementById('submit-test');
        const prevBtn = document.getElementById('prev-btn');
        const nextBtn = document.getElementById('next-btn');
        const reviewBtn = document.getElementById('review-btn');
        const retakeBtn = document.getElementById('retake-btn');
        const questionNumber = document.getElementById('question-number');
        const questionText = document.getElementById('question-text');
        const optionsContainer = document.getElementById('options-container');
        const timerElement = document.getElementById('timer');
        const progressBar = document.getElementById('progress');
        const finalScore = document.getElementById('final-score');
        const studentInfo = document.getElementById('student-info');
        const percentage = document.getElementById('percentage');
        const performanceMessage = document.getElementById('performance-message');

        // متغيرات التطبيق
        let currentQuestion = 0;
        let userAnswers = new Array(questions.length).fill(null);
        let studentName = '';
        let studentClass = '';
        let timeLeft = 60 * 60; // 60 دقيقة بالثواني
        let timerInterval;

        // بدء الاختبار
        startTestBtn.addEventListener('click', () => {
            studentName = document.getElementById('student-name').value.trim();
            studentClass = document.getElementById('student-class').value.trim();
            
            if (!studentName || !studentClass) {
                alert('يرجى إدخال الاسم الثلاثي والشعبة');
                return;
            }
            
            studentForm.classList.add('hidden');
            testScreen.classList.remove('hidden');
            
            startTimer();
            loadQuestion();
        });

        // بدء المؤقت
        function startTimer() {
            timerInterval = setInterval(() => {
                timeLeft--;
                
                const minutes = Math.floor(timeLeft / 60);
                const seconds = timeLeft % 60;
                timerElement.textContent = `الوقت المتبقي: ${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
                
                // تحديث شريط التقدم
                const progressPercentage = ((60 * 60 - timeLeft) / (60 * 60)) * 100;
                progressBar.style.width = `${progressPercentage}%`;
                
                if (timeLeft <= 0) {
                    clearInterval(timerInterval);
                    submitTest();
                }
            }, 1000);
        }

        // تحميل السؤال الحالي
        function loadQuestion() {
            const question = questions[currentQuestion];
            
            questionNumber.textContent = `السؤال ${currentQuestion + 1} من ${questions.length}`;
            questionText.textContent = question.question;
            
            optionsContainer.innerHTML = '';
            
            question.options.forEach((option, index) => {
                const optionElement = document.createElement('div');
                optionElement.classList.add('option');
                
                if (userAnswers[currentQuestion] === index) {
                    optionElement.classList.add('selected');
                }
                
                optionElement.textContent = option;
                optionElement.addEventListener('click', () => selectOption(index));
                
                optionsContainer.appendChild(optionElement);
            });
            
            // تحديث حالة أزرار التنقل
            prevBtn.disabled = currentQuestion === 0;
            nextBtn.disabled = currentQuestion === questions.length - 1;
        }

        // اختيار إجابة
        function selectOption(index) {
            userAnswers[currentQuestion] = index;
            
            // تحديث المظهر البصري للخيارات
            const options = document.querySelectorAll('.option');
            options.forEach((option, i) => {
                if (i === index) {
                    option.classList.add('selected');
                } else {
                    option.classList.remove('selected');
                }
            });
        }

        // الانتقال إلى السؤال التالي
        nextBtn.addEventListener('click', () => {
            if (currentQuestion < questions.length - 1) {
                currentQuestion++;
                loadQuestion();
            }
        });

        // العودة إلى السؤال السابق
        prevBtn.addEventListener('click', () => {
            if (currentQuestion > 0) {
                currentQuestion--;
                loadQuestion();
            }
        });

        // إنهاء الاختبار
        submitTestBtn.addEventListener('click', () => {
            if (confirm('هل أنت متأكد من إنهاء الاختبار؟')) {
                submitTest();
            }
        });

        // تقديم الاختبار وعرض النتائج
        function submitTest() {
            clearInterval(timerInterval);
            
            // حساب النتيجة
            let score = 0;
            userAnswers.forEach((answer, index) => {
                if (answer === questions[index].correct) {
                    score++;
                }
            });
            
            // عرض النتائج
            testScreen.classList.add('hidden');
            resultsScreen.classList.remove('hidden');
            
            finalScore.textContent = `${score}/${questions.length}`;
            studentInfo.textContent = `الطالب: ${studentName} - الشعبة: ${studentClass}`;
            
            const percent = ((score / questions.length) * 100).toFixed(1);
            percentage.textContent = `النسبة المئوية: ${percent}%`;
            
            // رسالة الأداء
            if (percent >= 90) {
                performanceMessage.textContent = 'ممتاز! أداء رائع';
                performanceMessage.style.color = 'var(--success)';
            } else if (percent >= 70) {
                performanceMessage.textContent = 'جيد جداً! استمر في التقدم';
                performanceMessage.style.color = 'var(--primary)';
            } else if (percent >= 50) {
                performanceMessage.textContent = 'مقبول، يمكنك التحسين';
                performanceMessage.style.color = 'var(--warning)';
            } else {
                performanceMessage.textContent = 'يحتاج إلى تحسين، حاول مرة أخرى';
                performanceMessage.style.color = 'var(--danger)';
            }
        }

        // مراجعة الإجابات
        reviewBtn.addEventListener('click', () => {
            resultsScreen.classList.add('hidden');
            testScreen.classList.remove('hidden');
            
            // إظهار الإجابات الصحيحة والخاطئة
            const question = questions[currentQuestion];
            const options = document.querySelectorAll('.option');
            
            options.forEach((option, index) => {
                if (index === question.correct) {
                    option.classList.add('correct');
                } else if (index === userAnswers[currentQuestion] && index !== question.correct) {
                    option.classList.add('incorrect');
                }
                
                // منع اختيار إجابات جديدة في وضع المراجعة
                option.style.pointerEvents = 'none';
            });
            
            // إخفاء أزرار التنقل والإرسال
            prevBtn.style.display = 'none';
            nextBtn.style.display = 'none';
            submitTestBtn.style.display = 'none';
        });

        // إعادة الاختبار
        retakeBtn.addEventListener('click', () => {
            // إعادة تعيين جميع المتغيرات
            currentQuestion = 0;
            userAnswers = new Array(questions.length).fill(null);
            timeLeft = 60 * 60;
            
            // إعادة تعيين واجهة المستخدم
            resultsScreen.classList.add('hidden');
            studentForm.classList.remove('hidden');
            
            document.getElementById('student-name').value = '';
            document.getElementById('student-class').value = '';
            
            // إعادة تعيين أزرار التنقل والإرسال
            prevBtn.style.display = 'inline-block';
            nextBtn.style.display = 'inline-block';
            submitTestBtn.style.display = 'block';
        });
    </script>
</body>
</html>
