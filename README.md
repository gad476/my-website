<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>عرض شراكة استثمارية</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;800&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Cairo', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
            color: #333;
            line-height: 1.6;
            overflow-x: hidden;
        }
        
        /* أزرار التصدير */
        .export-controls {
            position: fixed;
            top: 20px;
            right: 20px;
            z-index: 1000;
            display: flex;
            gap: 15px;
            flex-direction: column;
        }
        
        .export-btn {
            background: linear-gradient(145deg, #ff6b6b, #ee5a24);
            color: white;
            border: none;
            padding: 15px 25px;
            border-radius: 50px;
            cursor: pointer;
            font-weight: 700;
            font-size: 14px;
            box-shadow: 0 8px 25px rgba(238, 90, 36, 0.4);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
        }
        
        .export-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s;
        }
        
        .export-btn:hover::before {
            left: 100%;
        }
        
        .export-btn:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 15px 35px rgba(238, 90, 36, 0.6);
        }
        
        .export-btn.pdf {
            background: linear-gradient(145deg, #6c5ce7, #a29bfe);
            box-shadow: 0 8px 25px rgba(108, 92, 231, 0.4);
        }
        
        .export-btn.pdf:hover {
            box-shadow: 0 15px 35px rgba(108, 92, 231, 0.6);
        }
        
        .presentation-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 40px 20px;
        }
        
        .slide {
            background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
            border-radius: 25px;
            box-shadow: 
                0 20px 60px rgba(0,0,0,0.1),
                0 8px 25px rgba(0,0,0,0.08),
                inset 0 1px 0 rgba(255,255,255,0.9);
            margin: 40px 0;
            padding: 50px;
            animation: slideIn 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
        }
        
        .slide::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 6px;
            background: linear-gradient(90deg, #ff6b6b, #4ecdc4, #45b7d1, #96ceb4);
            border-radius: 25px 25px 0 0;
        }
        
        @keyframes slideIn {
            from { 
                opacity: 0; 
                transform: translateY(30px) scale(0.98); 
            }
            to { 
                opacity: 1; 
                transform: translateY(0) scale(1); 
            }
        }
        
        .slide h1 {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            font-size: 3em;
            font-weight: 800;
            margin-bottom: 30px;
            text-align: center;
            position: relative;
        }
        
        .slide h1::after {
            content: '';
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 4px;
            background: linear-gradient(90deg, #ff6b6b, #4ecdc4);
            border-radius: 2px;
        }
        
        .slide h2 {
            color: #2d3436;
            font-size: 2.2em;
            font-weight: 700;
            margin: 30px 0 20px 0;
            position: relative;
            padding-right: 25px;
        }
        
        .slide h2::before {
            content: '';
            position: absolute;
            right: 0;
            top: 50%;
            transform: translateY(-50%);
            width: 8px;
            height: 40px;
            background: linear-gradient(135deg, #ff6b6b, #4ecdc4);
            border-radius: 4px;
        }
        
        .slide h3 {
            color: #636e72;
            font-size: 1.4em;
            font-weight: 600;
            margin: 20px 0 15px 0;
        }
        
        .highlight-box {
            background: linear-gradient(135deg, #74b9ff 0%, #0984e3 100%);
            color: white;
            border-radius: 20px;
            padding: 30px;
            margin: 30px 0;
            box-shadow: 0 15px 40px rgba(116, 185, 255, 0.3);
            position: relative;
            overflow: hidden;
        }
        
        .highlight-box::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%);
            animation: shine 3s infinite;
        }
        
        @keyframes shine {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        .success-badge {
            background: linear-gradient(145deg, #00b894, #00a085);
            color: white;
            padding: 8px 15px;
            border-radius: 25px;
            font-size: 0.9em;
            font-weight: 600;
            margin-left: 15px;
            box-shadow: 0 4px 15px rgba(0, 184, 148, 0.3);
            display: inline-block;
        }
        
        .cost-table, .revenue-table {
            width: 100%;
            border-collapse: collapse;
            margin: 30px 0;
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }
        
        .cost-table th, .revenue-table th {
            background: linear-gradient(135deg, #6c5ce7, #a29bfe);
            color: white;
            padding: 20px;
            text-align: center;
            font-weight: 700;
            font-size: 1.1em;
            text-shadow: 0 1px 2px rgba(0,0,0,0.2);
        }
        
        .cost-table td, .revenue-table td {
            padding: 18px 20px;
            border-bottom: 1px solid #f1f3f4;
            text-align: center;
            font-weight: 500;
            transition: all 0.3s ease;
        }
        
        .cost-table tr:hover, .revenue-table tr:hover {
            background: linear-gradient(135deg, #f8f9ff, #e8f4f8);
            transform: scale(1.01);
        }
        
        .one-time {
            background: linear-gradient(145deg, #55a3ff, #003d82);
            color: white;
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: 600;
            font-size: 0.9em;
            box-shadow: 0 4px 12px rgba(85, 163, 255, 0.3);
        }
        
        .recurring {
            background: linear-gradient(145deg, #26de81, #20bf6b);
            color: white;
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: 600;
            font-size: 0.9em;
            box-shadow: 0 4px 12px rgba(38, 222, 129, 0.3);
        }
        
        .total-row {
            background: linear-gradient(135deg, #2d3436, #636e72) !important;
            color: white !important;
            font-weight: 700 !important;
            font-size: 1.1em !important;
        }
        
        .revenue-source {
            background: linear-gradient(135deg, #ffeaa7, #fdcb6e);
            border: none;
            border-radius: 15px;
            padding: 25px;
            margin: 20px 0;
            box-shadow: 0 8px 25px rgba(253, 203, 110, 0.3);
            position: relative;
        }
        
        .revenue-source::before {
            content: '💰';
            position: absolute;
            top: -10px;
            right: 20px;
            font-size: 2em;
            background: white;
            padding: 10px;
            border-radius: 50%;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }
        
        .revenue-source h4 {
            color: #2d3436;
            margin-bottom: 15px;
            font-weight: 700;
            font-size: 1.2em;
        }
        
        .strength-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin: 30px 0;
        }
        
        .strength-item {
            background: linear-gradient(145deg, #ff7675, #e17055);
            color: white;
            padding: 30px;
            border-radius: 20px;
            text-align: center;
            box-shadow: 0 15px 35px rgba(225, 112, 85, 0.4);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
        }
        
        .strength-item:nth-child(2n) {
            background: linear-gradient(145deg, #00b894, #00a085);
            box-shadow: 0 15px 35px rgba(0, 184, 148, 0.4);
        }
        
        .strength-item:nth-child(3n) {
            background: linear-gradient(145deg, #6c5ce7, #a29bfe);
            box-shadow: 0 15px 35px rgba(108, 92, 231, 0.4);
        }
        
        .strength-item:hover {
            transform: translateY(-10px) scale(1.05);
            box-shadow: 0 25px 50px rgba(0,0,0,0.2);
        }
        
        .strength-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.6s;
        }
        
        .strength-item:hover::before {
            left: 100%;
        }
        
        .strength-item h3 {
            color: white;
            font-size: 1.3em;
            margin-bottom: 15px;
            font-weight: 700;
        }
        
        .cta-section {
            text-align: center;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
            color: white;
            padding: 50px;
            border-radius: 25px;
            margin: 40px 0;
            box-shadow: 0 20px 60px rgba(102, 126, 234, 0.4);
            position: relative;
            overflow: hidden;
        }
        
        .cta-section::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%);
            animation: pulse 4s infinite;
        }
        
        @keyframes pulse {
            0%, 100% { opacity: 0.5; }
            50% { opacity: 1; }
        }
        
        .cta-section h2 {
            color: white;
            border: none;
            padding: 0;
            font-size: 2.5em;
            margin-bottom: 25px;
            text-shadow: 0 2px 4px rgba(0,0,0,0.3);
        }
        
        .cta-section h2::before {
            display: none;
        }
        
        .progress-indicator {
            display: flex;
            justify-content: center;
            margin: 30px 0;
            gap: 20px;
        }
        
        .progress-step {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: linear-gradient(145deg, #ddd, #bbb);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 1.2em;
            position: relative;
            transition: all 0.4s ease;
        }
        
        .progress-step.completed {
            background: linear-gradient(145deg, #00b894, #00a085);
            color: white;
            box-shadow: 0 8px 25px rgba(0, 184, 148, 0.4);
            animation: bounce 0.6s ease;
        }
        
        .progress-step.current {
            background: linear-gradient(145deg, #fdcb6e, #e17055);
            color: white;
            box-shadow: 0 8px 25px rgba(253, 203, 110, 0.4);
            animation: pulse-current 2s infinite;
        }
        
        @keyframes bounce {
            0%, 20%, 53%, 80%, 100% { transform: translate3d(0,0,0); }
            40%, 43% { transform: translate3d(0,-10px,0); }
            70% { transform: translate3d(0,-5px,0); }
            90% { transform: translate3d(0,-2px,0); }
        }
        
        @keyframes pulse-current {
            0%, 100% { box-shadow: 0 8px 25px rgba(253, 203, 110, 0.4); }
            50% { box-shadow: 0 8px 35px rgba(253, 203, 110, 0.8); }
        }
        
        .example-box {
            background: linear-gradient(135deg, #a8e6cf, #88d8a3);
            border-radius: 15px;
            padding: 25px;
            margin: 20px 0;
            box-shadow: 0 10px 30px rgba(136, 216, 163, 0.3);
            border: 2px solid rgba(255,255,255,0.3);
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 25px 0;
        }
        
        .stat-item {
            text-align: center;
            padding: 20px;
            background: rgba(255,255,255,0.9);
            border-radius: 15px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            transition: transform 0.3s ease;
        }
        
        .stat-item:hover {
            transform: translateY(-5px);
        }
        
        .stat-number {
            font-size: 2em;
            font-weight: 800;
            background: linear-gradient(135deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        @media print {
            .export-controls {
                display: none;
            }
            
            body {
                background: white;
            }
            
            .slide {
                page-break-inside: avoid;
                margin: 10px 0;
                box-shadow: none;
                border: 1px solid #ddd;
            }
            
            .slide::before {
                display: none;
            }
        }
        
        @media (max-width: 768px) {
            .export-controls {
                position: relative;
                top: auto;
                right: auto;
                flex-direction: row;
                justify-content: center;
                margin: 20px 0;
            }
            
            .slide {
                padding: 30px 20px;
                margin: 20px 0;
            }
            
            .slide h1 {
                font-size: 2em;
            }
            
            .slide h2 {
                font-size: 1.6em;
            }
            
            .strength-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- أزرار التصدير -->
    <div class="export-controls">
        <button class="export-btn pdf" onclick="exportToPDF()">📄 تصدير PDF</button>
        <button class="export-btn" onclick="printPresentation()">🖨️ طباعة</button>
    </div>
    
    <div class="presentation-container">
        
        <!-- العنوان الرئيسي -->
        <div class="slide">
            <h1>🚀 فرصة استثمارية لا تُفوَّت</h1>
            <div class="highlight-box" style="text-align: center;">
                <h2 style="border: none; padding: 0; margin: 10px 0; color: white;">شركتان متكاملتان • مقر واحد • أرباح مضاعفة</h2>
                <div class="stats-grid" style="margin: 30px 0;">
                    <div class="stat-item">
                        <div class="stat-number">🏠</div>
                        <h3 style="color: #2d3436;">التسويق العقاري</h3>
                        <p style="color: #636e72;">منصة رقمية متطورة</p>
                    </div>
                    <div class="stat-item">
                        <div class="stat-number">🚚</div>
                        <h3 style="color: #2d3436;">توصيل الطلبات</h3>
                        <p style="color: #636e72;">خدمة سريعة وموثوقة</p>
                    </div>
                    <div class="stat-item">
                        <div class="stat-number">💎</div>
                        <h3 style="color: #2d3436;">عوائد مضمونة</h3>
                        <p style="color: #636e72;">استثمار ذكي ومدروس</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- ما تم إنجازه -->
        <div class="slide">
            <h2>✨ إنجازات حقيقية • ليس مجرد أفكار</h2>
            <div class="progress-indicator">
                <div class="progress-step completed">✓</div>
                <div class="progress-step completed">✓</div>
                <div class="progress-step current">3</div>
            </div>
            <div class="stats-grid">
                <div class="strength-item" style="background: linear-gradient(145deg, #00b894, #00a085);">
                    <span class="success-badge" style="background: rgba(255,255,255,0.2);">مكتمل 100%</span>
                    <h3>تأسيس الشركة</h3>
                    <div class="stat-number" style="color: white;">20,000 ج</div>
                    <p>تم الصرف بالفعل</p>
                </div>
                <div class="strength-item" style="background: linear-gradient(145deg, #00b894, #00a085);">
                    <span class="success-badge" style="background: rgba(255,255,255,0.2);">جاهز للعمل</span>
                    <h3>موقع التسويق العقاري</h3>
                    <div class="stat-number" style="color: white;">100%</div>
                    <p>مبرمج بالكامل</p>
                </div>
                <div class="strength-item" style="background: linear-gradient(145deg, #fdcb6e, #e17055);">
                    <span class="success-badge" style="background: rgba(255,255,255,0.2);">المراحل الأخيرة</span>
                    <h3>تطبيق التوصيل</h3>
                    <div class="stat-number" style="color: white;">85%</div>
                    <p>قريباً جداً</p>
                </div>
            </div>
        </div>

        <!-- المصروفات -->
        <div class="slide">
            <h2>💰 هيكل الاستثمار الشفاف</h2>
            
            <div class="example-box">
                <h3>🟦 الاستثمار الأولي (مرة واحدة فقط)</h3>
                <table class="cost-table">
                    <thead>
                        <tr>
                            <th>البند</th>
                            <th>المبلغ</th>
                            <th>النوع</th>
                            <th>العائد</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><strong>ترخيص التسويق العقاري</strong></td>
                            <td><span class="stat-number" style="font-size: 1.2em;">25,000 ج</span></td>
                            <td><span class="one-time">مرة واحدة</span></td>
                            <td>✅ دخول السوق فوراً</td>
                        </tr>
                        <tr>
                            <td><strong>ترخيص شركة التوصيل</strong></td>
                            <td><span class="stat-number" style="font-size: 1.2em;">75,000 ج</span></td>
                            <td><span class="one-time">مرة واحدة</span></td>
                            <td>✅ احتكار منطقة جغرافية</td>
                        </tr>
                        <tr>
                            <td><strong>استضافة مواقع متقدمة</strong></td>
                            <td><span class="stat-number" style="font-size: 1.2em;">7,000 ج</span></td>
                            <td><span class="one-time">5 سنوات</span></td>
                            <td>✅ أداء فائق</td>
                        </tr>
                        <tr>
                            <td><strong>أثاث وتجهيز احترافي</strong></td>
                            <td><span class="stat-number" style="font-size: 1.2em;">25,000 ج</span></td>
                            <td><span class="one-time">مرة واحدة</span></td>
                            <td>✅ مظهر مهني</td>
                        </tr>
                        <tr class="total-row">
                            <td><strong>📊 إجمالي الاستثمار الأولي</strong></td>
                            <td><strong>132,000 ج</strong></td>
                            <td colspan="2"><strong>استثمار لمرة واحدة فقط!</strong></td>
                        </tr>
                    </tbody>
                </table>
            </div>

            <div class="revenue-source">
                <h3>🔄 التكاليف التشغيلية السنوية</h3>
                <table class="cost-table">
                    <thead>
                        <tr>
                            <th>البند</th>
                            <th>المبلغ السنوي</th>
                            <th>المبلغ الشهري</th>
                            <th>الفائدة</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><strong>إيجار مقر استراتيجي</strong></td>
                            <td><span class="stat-number" style="font-size: 1.2em;">120,000 ج</span></td>
                            <td><span class="recurring">10,000 ج</span></td>
                            <td>📍 موقع مميز</td>
                        </tr>
                        <tr>
                            <td><strong>موظف خدمة عملاء محترف</strong></td>
                            <td><span class="stat-number" style="font-size: 1.2em;">36,000 ج</span></td>
                            <td><span class="recurring">3,000 ج</span></td>
                            <td>🎯 خدمة عملاء ممتازة</td>
                        </tr>
                        <tr>
                            <td><strong>حملات تسويق ذكية</strong></td>
                            <td><span class="stat-number" style="font-size: 1.2em;">12,000 ج</span></td>
                            <td><span class="recurring">1,000 ج</span></td>
                            <td>📈 نمو العلامة التجارية</td>
                        </tr>
                        <tr class="total-row">
                            <td><strong>📊 إجمالي التكاليف السنوية</strong></td>
                            <td><strong>168,000 ج</strong></td>
                            <td><strong>14,000 ج</strong></td>
                            <td><strong>تكاليف ثابتة ومحسوبة</strong></td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

        <!-- مصادر الإيرادات - العقارات -->
        <div class="slide">
            <h2>🏆 مصادر الإيرادات الذهبية - العقارات</h2>
            
            <div class="revenue-source" style="background: linear-gradient(135deg, #a8e6cf, #88d8a3);">
                <h4>💎 إيرادات دورية مضمونة</h4>
                <div class="stats-grid">
                    <div class="stat-item">
                        <div class="stat-number">📢</div>
                        <h4>إعلانات المطورين</h4>
                        <span class="recurring">شهرية/سنوية</span>
                        <p>عقود طويلة المدى</p>
                    </div>
                    <div class="stat-item">
                        <div class="stat-number">⭐</div>
                        <h4>باقات الإبراز</h4>
                        <span class="recurring">اشتراكات</span>
                        <p>خدمات مميزة للعملاء</p>
                    </div>
                </div>
            </div>

            <div class="revenue-source" style="background: linear-gradient(135deg, #ffeaa7, #fdcb6e);">
                <h4>🚀 إيرادات لكل صفقة</h4>
                <div class="stats-grid">
                    <div class="stat-item">
                        <div class="stat-number">1-3%</div>
                        <h4>عمولة البيع/الإيجار</h4>
                        <span class="one-time">لكل عملية</span>
                        <p>من قيمة العقار</p>
                    </div>
                    <div class="stat-item">
                        <div class="stat-number">📸</div>
                        <h4>خدمات إضافية</h4>
                        <span class="one-time">حسب الطلب</span>
                        <p>تصوير - جولات افتراضية</p>
                    </div>
                </div>
            </div>

            <div class="example-box">
                <h3>💡 مثال توضيحي</h3>
                <p style="font-size: 1.1em; text-align: center; color: #2d3436;">
                    <strong>بيع عقار بقيمة مليون جنيه = 10,000 – 30,000 جنيه دخل من العمولة فقط!</strong>
                </p>
            </div>
        </div>

        <!-- مصادر الإيرادات - التوصيل -->
        <div class="slide">
            <h2>🚚 مصادر الإيرادات الذهبية - التوصيل</h2>
            
            <div class="revenue-source" style="background: linear-gradient(135deg, #81ecec, #74b9ff);">
                <h4>⚡ إيرادات فورية ومتنوعة</h4>
                <div class="stats-grid">
                    <div class="stat-item">
                        <div class="stat-number">10-15%</div>
                        <h4>عمولة على كل طلب</h4>
                        <span class="recurring">لكل عملية</span>
                        <p>من قيمة الطلب</p>
                    </div>
                    <div class="stat-item">
                        <div class="stat-number">🚛</div>
                        <h4>رسوم التوصيل</h4>
                        <span class="recurring">لكل طلب</span>
                        <p>مبلغ ثابت للعملية</p>
                    </div>
                    <div class="stat-item">
                        <div class="stat-number">🏪</div>
                        <h4>اشتراكات شهرية</h4>
                        <span class="recurring">شهرية</span>
                        <p>للمتاجر والمطاعم</p>
                    </div>
                    <div class="stat-item">
                        <div class="stat-number">📱</div>
                        <h4>إعلانات التطبيق</h4>
                        <span class="recurring">شهرية/سنوية</span>
                        <p>داخل المنصة</p>
                    </div>
                </div>
            </div>

            <div class="highlight-box">
                <h3>📊 معادلة النجاح المحسوبة</h3>
                <div class="stats-grid" style="margin: 20px 0;">
                    <div class="stat-item">
                        <div class="stat-number">100</div>
                        <h4>طلب يومياً</h4>
                        <p>متوسط 50 ج للطلب</p>
                    </div>
                    <div class="stat-item">
                        <div class="stat-number">15%</div>
                        <h4>عمولة + رسوم</h4>
                        <p>حوالي 7.5 ج للطلب</p>
                    </div>
                    <div class="stat-item" style="background: linear-gradient(145deg, #fdcb6e, #e17055);">
                        <div class="stat-number" style="color: white;">22,500</div>
                        <h4 style="color: white;">جنيه شهرياً</h4>
                        <p style="color: rgba(255,255,255,0.8);">إيراد محتمل</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- نقاط القوة -->
        <div class="slide">
            <h2>🎯 نقاط القوة التنافسية</h2>
            <div class="strength-grid">
                <div class="strength-item">
                    <h3>💰 توفير التكاليف</h3>
                    <p>مقر واحد لشركتين = مصاريف أقل وعوائد أكبر</p>
                </div>
                <div class="strength-item">
                    <h3>🔄 تنويع الدخل</h3>
                    <p>عقارات + توصيل = استقرار مالي وحماية من المخاطر</p>
                </div>
                <div class="strength-item">
                    <h3>📈 أسواق نامية</h3>
                    <p>قطاع العقارات مستقر وخدمات التوصيل تنمو بسرعة</p>
                </div>
                <div class="strength-item">
                    <h3>⚡ بنية تقنية جاهزة</h3>
                    <p>الموقع العقاري جاهز والتطبيق في المراحل الأخيرة</p>
                </div>
                <div class="strength-item">
                    <h3>🚀 قابلية التوسع</h3>
                    <p>إمكانية التوسع لمدن أخرى بعد إثبات النجاح</p>
                </div>
                <div class="strength-item">
                    <h3>📊 نموذج دخل متنوع</h3>
                    <p>إيرادات دورية + إيرادات لكل عملية</p>
                </div>
            </div>
        </div>

        <!-- توقعات الإيرادات -->
        <div class="slide">
            <h2>📈 توقعات الإيرادات والعوائد</h2>
            
            <div class="highlight-box">
                <h3 style="color: white; margin-bottom: 20px;">🎯 السيناريو المتحفظ - السنة الأولى</h3>
                <div class="stats-grid">
                    <div class="stat-item">
                        <div class="stat-number">🏠</div>
                        <h4>العقارات</h4>
                        <p><strong>180,000 ج</strong> سنوياً</p>
                        <small>إعلانات + عمولات محدودة</small>
                    </div>
                    <div class="stat-item">
                        <div class="stat-number">🚚</div>
                        <h4>التوصيل</h4>
                        <p><strong>120,000 ج</strong> سنوياً</p>
                        <small>نمو تدريجي</small>
                    </div>
                    <div class="stat-item" style="background: linear-gradient(145deg, #00b894, #00a085); color: white;">
                        <div class="stat-number" style="color: white;">300,000</div>
                        <h4 style="color: white;">إجمالي الإيرادات</h4>
                        <p style="color: rgba(255,255,255,0.9)">السنة الأولى</p>
                    </div>
                </div>
            </div>

            <div class="revenue-source">
                <h3>📊 تحليل الربحية</h3>
                <table class="revenue-table">
                    <thead>
                        <tr>
                            <th>البند</th>
                            <th>السنة الأولى</th>
                            <th>السنة الثانية</th>
                            <th>النمو المتوقع</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><strong>إجمالي الإيرادات</strong></td>
                            <td><span class="stat-number" style="font-size: 1.1em;">300,000 ج</span></td>
                            <td><span class="stat-number" style="font-size: 1.1em;">450,000 ج</span></td>
                            <td><span class="success-badge">+50%</span></td>
                        </tr>
                        <tr>
                            <td><strong>التكاليف التشغيلية</strong></td>
                            <td>168,000 ج</td>
                            <td>185,000 ج</td>
                            <td>+10%</td>
                        </tr>
                        <tr class="total-row">
                            <td><strong>صافي الربح</strong></td>
                            <td><strong>132,000 ج</strong></td>
                            <td><strong>265,000 ج</strong></td>
                            <td><strong>عائد 100%</strong></td>
                        </tr>
                    </tbody>
                </table>
            </div>

            <div class="example-box">
                <h3>🎉 نقطة التعادل</h3>
                <p style="text-align: center; font-size: 1.1em; color: #2d3436;">
                    <strong>استرداد كامل الاستثمار في السنة الأولى!</strong><br>
                    <small>كل ما يأتي بعد ذلك = أرباح صافية</small>
                </p>
            </div>
        </div>

        <!-- الخاتمة والدعوة للعمل -->
        <div class="slide">
            <div class="cta-section">
                <h2>🎯 الفرصة الاستثمارية الذهبية</h2>
                <div class="stats-grid" style="margin: 30px 0;">
                    <div style="background: rgba(255,255,255,0.1); padding: 25px; border-radius: 15px;">
                        <h3 style="color: white;">✨ استثمار محدود</h3>
                        <p style="color: rgba(255,255,255,0.9);">مقابل دخول سوقين ضخمين بأصول تقنية جاهزة</p>
                    </div>
                    <div style="background: rgba(255,255,255,0.1); padding: 25px; border-radius: 15px;">
                        <h3 style="color: white;">📈 رؤية واضحة</h3>
                        <p style="color: rgba(255,255,255,0.9);">للإيرادات مع نموذج عمل مجرب ومربح</p>
                    </div>
                    <div style="background: rgba(255,255,255,0.1); padding: 25px; border-radius: 15px;">
                        <h3 style="color: white;">🚀 نمو متسارع</h3>
                        <p style="color: rgba(255,255,255,0.9);">مشروع واحد = مصدران للإيرادات + قابلية توسع بلا حدود</p>
                    </div>
                </div>
                
                <div style="background: rgba(255,255,255,0.95); color: #2d3436; padding: 30px; border-radius: 20px; margin: 30px 0;">
                    <h3 style="margin-bottom: 20px; color: #2d3436;">💡 لماذا الآن هو الوقت المثالي؟</h3>
                    <div class="stats-grid">
                        <div class="stat-item">
                            <div class="stat-number">✅</div>
                            <h4>البنية التقنية جاهزة</h4>
                            <p>لا وقت ضائع في التطوير</p>
                        </div>
                        <div class="stat-item">
                            <div class="stat-number">📊</div>
                            <h4>السوق في نمو متسارع</h4>
                            <p>فرصة لا تعوض</p>
                        </div>
                        <div class="stat-item">
                            <div class="stat-number">💰</div>
                            <h4>عوائد متوقعة واضحة</h4>
                            <p>استثمار مدروس ومحسوب</p>
                        </div>
                        <div class="stat-item">
                            <div class="stat-number">👥</div>
                            <h4>فريق عمل ملتزم</h4>
                            <p>رؤية واضحة للمستقبل</p>
                        </div>
                    </div>
                </div>
                
                <div class="highlight-box" style="background: linear-gradient(135deg, #ff6b6b, #ee5a24); margin: 30px 0;">
                    <h2 style="font-size: 2.2em; margin: 15px 0; color: white;">🤝 معاً نحو النجاح!</h2>
                    <p style="font-size: 1.3em; color: white; margin: 0;">هذه ليست مجرد فكرة... بل خطة عملية جاهزة للتنفيذ!</p>
                </div>
                
                <div style="background: rgba(255,255,255,0.1); padding: 25px; border-radius: 15px; margin: 20px 0;">
                    <h3 style="color: white; margin-bottom: 15px;">📞 الخطوة التالية</h3>
                    <p style="color: rgba(255,255,255,0.9); font-size: 1.1em;">
                        دعنا نلتقي لمناقشة التفاصيل وبدء رحلة النجاح المشتركة
                    </p>
                </div>
            </div>
        </div>

    </div>

    <script>
        // وظيفة تصدير إلى PDF
        function exportToPDF() {
            // إخفاء أزرار التصدير مؤقتاً
            const controls = document.querySelector('.export-controls');
            const originalDisplay = controls.style.display;
            controls.style.display = 'none';
            
            // تحسين التنسيق للطباعة
            const originalBodyStyle = document.body.style.background;
            document.body.style.background = 'white';
            
            const slides = document.querySelectorAll('.slide');
            slides.forEach(slide => {
                slide.style.pageBreakInside = 'avoid';
                slide.style.marginBottom = '15px';
            });
            
            // طباعة الصفحة (المستخدم يختار "حفظ كـ PDF")
            window.print();
            
            // إعادة التنسيق الأصلي
            setTimeout(() => {
                controls.style.display = originalDisplay;
                document.body.style.background = originalBodyStyle;
            }, 1000);
        }
        
        // وظيفة الطباعة العادية
        function printPresentation() {
            const controls = document.querySelector('.export-controls');
            const originalDisplay = controls.style.display;
            controls.style.display = 'none';
            
            window.print();
            
            setTimeout(() => {
                controls.style.display = originalDisplay;
            }, 1000);
        }
        
        // إضافة تأثيرات تفاعلية عند التحميل
        document.addEventListener('DOMContentLoaded', function() {
            // تأثير الظهور التدريجي للشرائح
            const slides = document.querySelectorAll('.slide');
            
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.opacity = '1';
                        entry.target.style.transform = 'translateY(0) scale(1)';
                    }
                });
            }, { threshold: 0.1 });
            
            slides.forEach((slide, index) => {
                slide.style.opacity = '0';
                slide.style.transform = 'translateY(30px) scale(0.98)';
                slide.style.transition = `all 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275) ${index * 0.1}s`;
                observer.observe(slide);
            });
            
            // تأثيرات تفاعلية للجداول
            const tableRows = document.querySelectorAll('.cost-table tr, .revenue-table tr');
            tableRows.forEach(row => {
                if (!row.classList.contains('total-row')) {
                    row.addEventListener('mouseenter', function() {
                        this.style.transform = 'scale(1.02)';
                        this.style.zIndex = '10';
                    });
                    
                    row.addEventListener('mouseleave', function() {
                        this.style.transform = 'scale(1)';
                        this.style.zIndex = '1';
                    });
                }
            });
            
            // تأثير النبض للعناصر المهمة
            const pulseElements = document.querySelectorAll('.stat-number');
            pulseElements.forEach(element => {
                element.addEventListener('mouseenter', function() {
                    this.style.animation = 'pulse-current 1s ease';
                });
                
                element.addEventListener('animationend', function() {
                    this.style.animation = '';
                });
            });
        });
        
        // تأثيرات الماوس للأزرار
        const exportButtons = document.querySelectorAll('.export-btn');
        exportButtons.forEach(button => {
            button.addEventListener('click', function() {
                this.style.transform = 'scale(0.95)';
                setTimeout(() => {
                    this.style.transform = '';
                }, 150);
            });
        });
        
        // وظيفة إضافية لحفظ كـ HTML
        function downloadHTML() {
            const htmlContent = `<!DOCTYPE html>${document.documentElement.outerHTML}`;
            const blob = new Blob([htmlContent], { type: 'text/html;charset=utf-8' });
            const url = URL.createObjectURL(blob);
            const link = document.createElement('a');
            link.href = url;
            link.download = 'عرض_الشراكة_الاستثمارية_المتكامل.html';
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            URL.revokeObjectURL(url);
        }
    </script>
</body>
</html>
