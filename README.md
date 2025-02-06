<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نموذج إدخال البيانات</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 400px;
        }
        h1 {
            text-align: center;
            color: #333;
        }
        label {
            display: block;
            margin-bottom: 5px;
            color: #555;
        }
        input[type="text"], input[type="number"] {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 4px;
            font-size: 16px;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
        .message {
            margin-top: 15px;
            text-align: center;
            color: #28a745;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>إدخال البيانات</h1>
        <label for="name">الاسم:</label>
        <input type="text" id="name" placeholder="أدخل الاسم">
        
        <label for="age">العمر:</label>
        <input type="number" id="age" placeholder="أدخل العمر">
        
        <label for="address">العنوان:</label>
        <input type="text" id="address" placeholder="أدخل العنوان">
        
        <label for="phone">رقم الهاتف:</label>
        <input type="text" id="phone" placeholder="أدخل رقم الهاتف">
        
        <button onclick="submitData()">إرسال البيانات</button>
        <div class="message" id="message"></div>
    </div>

    <script>
        function submitData() {
            const scriptUrl = 'https://script.google.com/macros/s/xxxxxxxxxxxxxxxxxxxxx/exec'; // استبدل بهذا الرابط

            const name = document.getElementById('name').value;
            const age = document.getElementById('age').value;
            const address = document.getElementById('address').value;
            const phone = document.getElementById('phone').value;

            if (!name || !age || !address || !phone) {
                alert('يرجى تعبئة جميع الحقول');
                return;
            }

            const data = {
                name: name,
                age: age,
                address: address,
                phone: phone
            };

            fetch(scriptUrl, {
                method: 'POST',
                mode: 'no-cors',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(data)
            })
            .then(() => {
                document.getElementById('message').textContent = 'تم إرسال البيانات بنجاح!';
                document.getElementById('name').value = '';
                document.getElementById('age').value = '';
                document.getElementById('address').value = '';
                document.getElementById('phone').value = '';
            })
            .catch((error) => {
                console.error('حدث خطأ:', error);
                document.getElementById('message').textContent = 'حدث خطأ أثناء إرسال البيانات.';
            });
        }
    </script>
</body>
</html>
