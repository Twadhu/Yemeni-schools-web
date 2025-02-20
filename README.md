<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منصة مدارس الجمهورية اليمنية</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f8ff;
            color: #333;
            text-align: center;
            margin: 0;
            padding: 0;
        }
        header, footer {
            background-color: #218c74;
            color: white;
            padding: 10px;
        }
        main {
            margin: 20px;
        }
        form {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        label {
            margin: 10px 0 5px;
        }
        input, select, button {
            margin: 5px 0;
            padding: 10px;
            width: 80%;
            max-width: 300px;
        }
        button {
            background-color: #218c74;
            color: white;
            border: none;
            cursor: pointer;
        }
        .error {
            color: red;
        }
    </style>
</head>
<body>
    <header>
        <h1>مرحبًا بكم في منصة مدارس الجمهورية اليمنية</h1>
    </header>

    <main>
        <section id="login">
            <h2>تسجيل الدخول</h2>
            <form id="login-form">
                <label for="email">البريد الإلكتروني:</label>
                <input type="email" id="email" name="email" required>
                
                <label for="password">كلمة المرور:</label>
                <input type="password" id="password" name="password" required>
                
                <button type="submit">تسجيل الدخول</button>
            </form>
            <p id="login-error" class="error"></p>
        </section>

        <section id="register" style="display: none;">
            <h2>إنشاء حساب</h2>
            <form id="register-form">
                <label for="full-name">الاسم الرباعي:</label>
                <input type="text" id="full-name" name="full-name" required>

                <label for="surname">اللقب:</label>
                <input type="text" id="surname" name="surname" required>

                <label for="gender">الجنس:</label>
                <select id="gender" name="gender">
                    <option value="male">ذكر</option>
                    <option value="female">أنثى</option>
                </select>

                <label for="role">الدور:</label>
                <select id="role" name="role">
                    <option value="student">طالب</option>
                    <option value="teacher">مدرس</option>
                    <option value="admin">إدارة مدرسة</option>
                </select>

                <label for="reg-email">البريد الإلكتروني:</label>
                <input type="email" id="reg-email" name="reg-email" required>

                <label for="reg-password">كلمة المرور:</label>
                <input type="password" id="reg-password" name="reg-password" required>

                <label for="confirm-password">تأكيد كلمة المرور:</label>
                <input type="password" id="confirm-password" name="confirm-password" required>

                <label for="school">اختيار المدرسة:</label>
                <select id="school" name="school">
                    <option value="مدرسة النور بالثوباني">مدرسة النور بالثوباني</option>
                </select>

                <label for="grade">الصف الدراسي:</label>
                <select id="grade" name="grade">
                    <option value="1">الأول</option>
                    <option value="2">الثاني</option>
                    <option value="3">الثالث</option>
                    <option value="4">الرابع</option>
                    <option value="5">الخامس</option>
                    <option value="6">السادس</option>
                    <option value="7">السابع</option>
                    <option value="8">الثامن</option>
                    <option value="9">التاسع</option>
                    <option value="10">الأول الثانوي</option>
                    <option value="11">الثاني الثانوي</option>
                    <option value="12">الثالث الثانوي</option>
                </select>

                <label for="phone">رقم الهاتف:</label>
                <input type="text" id="phone" name="phone" required>

                <button type="submit">حفظ</button>
            </form>
            <p id="register-error" class="error"></p>
        </section>

        <button id="toggle-button" onclick="toggleForms()">إنشاء حساب جديد</button>
    </main>

    <footer>
        <p>تم إنشاء الصفحة بواسطة عبدالله عباس، جميع الحقوق محفوظة.</p>
        <p>للتواصل عبر الواتساب: +967771004061</p>
    </footer>

    <script>
        function toggleForms() {
            const loginSection = document.getElementById('login');
            const registerSection = document.getElementById('register');
            const toggleButton = document.getElementById('toggle-button');

            if (loginSection.style.display === 'none') {
                loginSection.style.display = 'block';
                registerSection.style.display = 'none';
                toggleButton.textContent = 'إنشاء حساب جديد';
            } else {
                loginSection.style.display = 'none';
                registerSection.style.display = 'block';
                toggleButton.textContent = 'تسجيل الدخول';
            }
        }

        document.getElementById('login-form').addEventListener('submit', async (e) => {
            e.preventDefault();
            const email = document.getElementById('email').value;
            const password = document.getElementById('password').value;

            if (email === "test@example.com" && password === "123456") {
                alert("تم تسجيل الدخول بنجاح!");
                window.location.href = "dashboard.html";
            } else {
                document.getElementById('login-error').textContent = "البريد الإلكتروني أو كلمة المرور غير صحيحة.";
            }
        });

        document.getElementById('register-form').addEventListener('submit', async (e) => {
            e.preventDefault();
            const password = document.getElementById('reg-password').value;
            const confirmPassword = document.getElementById('confirm-password').value;

            if (password !== confirmPassword) {
                document.getElementById('register-error').textContent = "كلمة المرور غير متطابقة.";
                return;
            }

            alert("تم إنشاء الحساب بنجاح! سيتم إرسال رابط التفعيل إلى بريدك الإلكتروني.");
            toggleForms();
        }); 
        // إعداد EmailJS لإرسال بريد عند قبول الطالب
(function() {
    document.addEventListener("DOMContentLoaded", function() {
        document.getElementById("acceptStudentBtn").addEventListener("click", function() {
            const studentName = document.getElementById("studentName").value;
            const schoolName = document.getElementById("schoolName").value;
            const studentEmail = document.getElementById("studentEmail").value;

            if (!studentName || !schoolName || !studentEmail) {
                alert("يرجى إدخال جميع البيانات المطلوبة");
                return;
            }

            emailjs.init("QM4EgDHKawTHU-5dp"); // المفتاح العام EmailJS
            
            const templateParams = {
                to_name: studentName,
                Yemeni: schoolName,
                message: `تهانينا! تم قبولك في ${schoolName}. يمكنك الآن تسجيل الدخول إلى المنصة للوصول إلى جميع الميزات المتاحة لك.`,
                to_email: studentEmail
            };

            emailjs.send("service_stduown", "template_27rvt66", templateParams)
                .then(function(response) {
                    alert("تم إرسال البريد بنجاح إلى " + studentEmail);
                    console.log("Email sent successfully:", response);
                }, function(error) {
                    alert("حدث خطأ أثناء إرسال البريد. يرجى المحاولة مرة أخرى.");
                    console.error("Email error:", error);
                });
        });
    });
})();

    </script>
</body>
</html>
