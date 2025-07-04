<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>عروض حصرية - مطعم فلوفرز سلط</title>
    <style>
        :root {
            --primary: #2e7d32;
            --primary-light: #4caf50;
            --secondary: #ff9800;
            --light: #f5f5f5;
            --dark: #333;
            --error: #d32f2f;
        }
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        body {
            background: linear-gradient(135deg, #f5f7fa 0%, #e4edf5 100%);
            color: var(--dark);
            line-height: 1.6;
            padding: 20px;
            min-height: 100vh;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }
        header {
            background: linear-gradient(to right, var(--primary), var(--primary-light));
            color: white;
            padding: 30px 20px;
            text-align: center;
            position: relative;
        }
        .logo { 
            font-size: 2.5rem; 
            margin-bottom: 10px; 
            display: inline-block;
            animation: pulse 2s infinite;
        }
        h1 { font-size: 1.8rem; margin-bottom: 10px; }
        .tagline { font-size: 1.1rem; opacity: 0.9; }
        .offer-badge {
            position: absolute;
            top: 20px;
            left: 20px;
            background-color: var(--secondary);
            color: white;
            padding: 8px 15px;
            border-radius: 20px;
            font-weight: bold;
            transform: rotate(-5deg);
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }
        .content { padding: 30px; }
        .form-section, .offers-section { margin-bottom: 30px; }
        .section-title {
            color: var(--primary);
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid var(--primary-light);
            position: relative;
        }
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            width: 50px;
            height: 2px;
            background: var(--secondary);
        }
        
        /* Form Styles */
        .form-group { margin-bottom: 20px; position: relative; }
        label { display: block; margin-bottom: 8px; font-weight: 600; }
        input, select, button {
            width: 100%;
            padding: 14px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            transition: all 0.3s;
        }
        input:focus, select:focus {
            border-color: var(--primary);
            outline: none;
            box-shadow: 0 0 0 3px rgba(46, 125, 50, 0.2);
        }
        button {
            background: linear-gradient(to right, var(--primary), var(--primary-light));
            color: white;
            border: none;
            cursor: pointer;
            font-weight: bold;
            box-shadow: 0 4px 10px rgba(46, 125, 50, 0.3);
            position: relative;
            overflow: hidden;
        }
        button:hover { 
            transform: translateY(-2px); 
            box-shadow: 0 6px 15px rgba(46, 125, 50, 0.4); 
        }
        button:active {
            transform: translateY(1px);
        }
        
        /* Error Styles */
        .input-error {
            border-color: var(--error) !important;
        }
        .error-text {
            color: var(--error);
            font-size: 0.8rem;
            margin-top: 5px;
            display: none;
        }
        
        /* Offer Card Styles */
        .offers-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        .offer-card {
            background-color: var(--light);
            border-radius: 10px;
            padding: 20px;
            border-left: 4px solid var(--secondary);
            transition: all 0.3s ease;
            box-shadow: 0 4px 8px rgba(0,0,0,0.05);
            position: relative;
            overflow: hidden;
        }
        .offer-card:hover { 
            transform: translateY(-5px); 
            box-shadow: 0 8px 16px rgba(0,0,0,0.1);
        }
        .offer-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: var(--secondary);
            transform: scaleX(0);
            transform-origin: left;
            transition: transform 0.3s ease;
        }
        .offer-card:hover::before {
            transform: scaleX(1);
        }
        .offer-title { 
            color: var(--primary); 
            margin-bottom: 10px; 
            font-weight: 600; 
            font-size: 1.2rem;
        }
        .offer-desc { 
            color: var(--dark); 
            margin-bottom: 15px; 
            font-size: 0.95rem; 
            line-height: 1.5;
        }
        .offer-price { 
            font-weight: bold; 
            color: var(--secondary); 
            font-size: 1.2rem; 
            text-align: left;
        }
        
        /* Utility Styles */
        .success-message {
            background-color: #d4edda; 
            color: #155724; 
            padding: 15px;
            border-radius: 8px; 
            margin-top: 20px; 
            text-align: center; 
            display: none;
            animation: fadeIn 0.5s ease;
        }
        .error-message {
            background-color: #f8d7da; 
            color: #721c24; 
            padding: 15px;
            border-radius: 8px; 
            margin-top: 20px; 
            text-align: center; 
            display: none;
            animation: fadeIn 0.5s ease;
        }
        .loading-spinner {
            border: 5px solid #f3f3f3;
            border-top: 5px solid var(--primary);
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
            margin: 20px auto;
            display: none;
        }
        .empty-offers {
            text-align: center;
            padding: 20px;
            color: #666;
            grid-column: 1 / -1;
        }
        
        /* Animations */
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        footer {
            text-align: center; 
            padding: 20px; 
            background-color: #f5f5f5;
            color: #666; 
            font-size: 0.9rem;
            border-top: 1px solid #eee;
        }
        
        /* Responsive Design */
        @media (max-width: 768px) {
            .container {
                border-radius: 10px;
            }
            header {
                padding: 20px 15px;
            }
            .logo {
                font-size: 2rem;
            }
            h1 {
                font-size: 1.5rem;
            }
            .tagline {
                font-size: 1rem;
            }
            .content {
                padding: 20px 15px;
            }
            .offers-grid {
                grid-template-columns: 1fr;
            }
            .offer-card {
                padding: 15px;
            }
            input, select, button {
                padding: 12px;
                font-size: 0.95rem;
            }
            footer p {
                font-size: 0.8rem;
            }
        }
        
        @media (max-width: 480px) {
            body {
                padding: 10px;
            }
            header {
                padding: 15px 10px;
            }
            .logo {
                font-size: 1.8rem;
            }
            h1 {
                font-size: 1.3rem;
            }
            .section-title {
                font-size: 1.2rem;
            }
            .offer-title {
                font-size: 1.1rem;
            }
            .offer-price {
                font-size: 1.1rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="offer-badge">خصم ٢٠٪</div>
            <div class="logo">🥗</div>
            <h1>مطعم فلوفرز سلط</h1>
            <p class="tagline">اشترك الآن واحصل على عروض حصرية وتخفيضات على السلطات الطازجة!</p>
        </header>
        
        <div class="content">
            <div class="form-section">
                <h2 class="section-title">سجل بياناتك واحصل على العروض</h2>
                <form id="offerForm">
                    <div class="form-group">
                        <label for="name">الاسم الكامل</label>
                        <input type="text" id="name" required placeholder="أدخل اسمك هنا">
                        <div id="nameError" class="error-text">يجب إدخال الاسم الكامل</div>
                    </div>
                    
                    <div class="form-group">
                        <label for="phone">رقم الجوال (واتساب)</label>
                        <input type="tel" id="phone" required placeholder="مثال: 05XXXXXXXX" pattern="^05\d{8}$">
                        <div id="phoneError" class="error-text">يجب أن يبدأ الرقم بـ 05 ويحتوي على 10 أرقام</div>
                    </div>
                    
                    <div class="form-group">
                        <label for="favorite">ما هي سلطتك المفضلة؟</label>
                        <select id="favorite" required>
                            <option value="" disabled selected>اختر من القائمة</option>
                            <option value="سلطة فلوفرز">سلطة فلوفرز</option>
                            <option value="سلطة كراب">سلطة كراب</option>
                            <option value="سلطة سيزر">سلطة سيزر</option>
                            <option value="سلطة ريتش">سلطة ريتش</option>
                            <option value="سلطة كينوا">سلطة كينوا</option>
                        </select>
                    </div>
                    
                    <button type="submit">اشترك واحصل على العروض الحصرية</button>
                </form>
                
                <div id="successMessage" class="success-message">
                    شكراً لتسجيلك! سيصلك أول عرض خلال دقائق على واتساب.
                </div>
                <div id="errorMessage" class="error-message">
                    حدث خطأ أثناء الإرسال. يرجى المحاولة مرة أخرى.
                </div>
            </div>
            
            <div class="offers-section">
                <h2 class="section-title">عروضنا الحصرية هذا الأسبوع</h2>
                <div id="offersGrid" class="offers-grid">
                    <div class="loading-spinner" id="loadingSpinner"></div>
                    <!-- سيتم ملء العروض ديناميكياً من Firebase -->
                </div>
            </div>
        </div>
        
        <footer>
            <p>مطعم فلوفرز سلط - توصيل سريع وطازج 24/7</p>
            <p>هاتف: 0551234567 | العنوان: شارع التحلية، الرياض</p>
            <p style="margin-top: 15px;">جميع الحقوق محفوظة © 2025</p>
        </footer>
    </div>
    
    <!-- Firebase SDK -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getFirestore, collection, getDocs } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // Firebase configuration - استبدل هذه القيم بقيم مشروعك
        const firebaseConfig = {
            apiKey: "AIzaSyABCD1234...",
            authDomain: "your-project.firebaseapp.com",
            projectId: "your-project-id",
            storageBucket: "your-project.appspot.com",
            messagingSenderId: "123456789",
            appId: "1:123456789:web:abcd1234"
        };

        // Initialize Firebase
        const app = initializeApp(firebaseConfig);
        const db = getFirestore(app);

        // DOM Elements
        const offersGrid = document.getElementById('offersGrid');
        const loadingSpinner = document.getElementById('loadingSpinner');
        const form = document.getElementById('offerForm');
        const successMessage = document.getElementById('successMessage');
        const errorMessage = document.getElementById('errorMessage');
        const nameInput = document.getElementById('name');
        const phoneInput = document.getElementById('phone');
        const favoriteSelect = document.getElementById('favorite');
        const nameError = document.getElementById('nameError');
        const phoneError = document.getElementById('phoneError');

        // Function to show loading state
        function showLoading() {
            loadingSpinner.style.display = 'block';
        }

        // Function to hide loading state
        function hideLoading() {
            loadingSpinner.style.display = 'none';
        }

        // Function to validate phone number
        function validatePhone(phone) {
            const phonePattern = /^05\d{8}$/;
            return phonePattern.test(phone);
        }

        // Load offers from Firebase
        async function loadOffers() {
            showLoading();
            try {
                const offersSnapshot = await getDocs(collection(db, "offers"));
                offersGrid.innerHTML = '';
                
                if (offersSnapshot.empty) {
                    offersGrid.innerHTML = `
                        <div class="empty-offers">
                            <p>لا توجد عروض متاحة حالياً. ترقبوا جديدنا!</p>
                        </div>
                    `;
                } else {
                    offersSnapshot.forEach((doc) => {
                        const offer = doc.data();
                        const offerCard = document.createElement('div');
                        offerCard.className = 'offer-card';
                        offerCard.innerHTML = `
                            <h3 class="offer-title">${offer.title || 'عرض مميز'}</h3>
                            <p class="offer-desc">${offer.description || 'تفاصيل العرض غير متوفرة حالياً'}</p>
                            <p class="offer-price">${offer.price || 'السعر غير متوفر'}</p>
                        `;
                        offersGrid.appendChild(offerCard);
                    });
                }
            } catch (error) {
                console.error("Error loading offers:", error);
                offersGrid.innerHTML = `
                    <div class="error-message" style="display: block; grid-column: 1/-1;">
                        <p>حدث خطأ في تحميل العروض. الرجاء المحاولة مرة أخرى.</p>
                    </div>
                `;
            } finally {
                hideLoading();
            }
        }

        // Handle form submission
        form.addEventListener('submit', async function(e) {
            e.preventDefault();
            
            // Reset messages and errors
            successMessage.style.display = 'none';
            errorMessage.style.display = 'none';
            nameError.style.display = 'none';
            phoneError.style.display = 'none';
            nameInput.classList.remove('input-error');
            phoneInput.classList.remove('input-error');
            
            // Validate inputs
            const name = nameInput.value.trim();
            const phone = phoneInput.value.trim();
            const favorite = favoriteSelect.value;
            let isValid = true;
            
            if (!name) {
                nameInput.classList.add('input-error');
                nameError.style.display = 'block';
                isValid = false;
            }
            
            if (!validatePhone(phone)) {
                phoneInput.classList.add('input-error');
                phoneError.style.display = 'block';
                isValid = false;
            }
            
            if (!favorite) {
                favoriteSelect.classList.add('input-error');
                isValid = false;
            }
            
            if (!isValid) {
                return;
            }
            
            try {
                // Save customer data to Firebase (optional)
                // يمكنك إضافة كود لحفظ بيانات العميل في Firebase إذا كنت بحاجة لذلك
                
                // Send WhatsApp message
                const restaurantWhatsappNumber = '966551234567'; // استبدل برقم الواتساب الفعلي
                const whatsappMessage = `مرحباً، أنا ${name} أرغب في الاشتراك في عروض مطعم فلوفرز سلط. سلطتي المفضلة: ${favorite}. رقمي: ${phone}`;
                const whatsappUrl = `https://wa.me/${restaurantWhatsappNumber}?text=${encodeURIComponent(whatsappMessage)}`;
                
                // Show success message
                successMessage.style.display = 'block';
                
                // Open WhatsApp after a small delay
                setTimeout(() => {
                    window.open(whatsappUrl, '_blank');
                }, 1000);
                
                // Reset form
                form.reset();
                
            } catch (error) {
                console.error("Error submitting form:", error);
                errorMessage.style.display = 'block';
            }
        });

        // Initialize the page
        document.addEventListener('DOMContentLoaded', () => {
            loadOffers();
        });

        // Add input validation on blur
        nameInput.addEventListener('blur', function() {
            if (!this.value.trim()) {
                this.classList.add('input-error');
                nameError.style.display = 'block';
            } else {
                this.classList.remove('input-error');
                nameError.style.display = 'none';
            }
        });

        phoneInput.addEventListener('blur', function() {
            if (!validatePhone(this.value.trim())) {
                this.classList.add('input-error');
                phoneError.style.display = 'block';
            } else {
                this.classList.remove('input-error');
                phoneError.style.display = 'none';
            }
        });
    </script>
</body>
</html>
