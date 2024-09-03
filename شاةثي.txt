<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>الصواوي لتجارة الأجهزة الإلكترونية</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            direction: rtl;
            text-align: center;
        }

        header {
            background-color: #333;
            color: white;
            padding: 20px;
        }

        nav {
            background-color: #444;
            padding: 15px;
        }

        nav a {
            color: white;
            margin: 0 15px;
            text-decoration: none;
            cursor: pointer;
        }

        .banner {
            width: 100%;
            max-width: 100%;
            height: 400px;
            background-image: url('https://via.placeholder.com/1200x400');
            background-size: cover;
            background-position: center;
            margin-bottom: 20px;
        }

        .category {
            margin: 20px;
            padding: 20px;
            background-color: #fff;
            border: 1px solid #ccc;
            border-radius: 5px;
            width: 300px;
            display: inline-block;
            cursor: pointer;
        }

        .category:hover {
            background-color: #ddd;
        }

        .products {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            margin: 20px;
        }

        .product {
            background-color: white;
            margin: 10px;
            padding: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
            width: 250px;
            text-align: center;
        }

        .product img {
            max-width: 100%;
            border-radius: 5px;
        }

        .product h3 {
            margin: 10px 0;
        }

        .product p {
            margin: 10px 0;
            color: #555;
        }

        .product button {
            background-color: #28a745;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
        }

        .product button:hover {
            background-color: #218838;
        }

        footer {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 15px 0;
            margin-top: 20px;
        }

        .order-form {
            display: none;
            padding: 20px;
            background-color: #fff;
            border-radius: 5px;
            margin: 20px auto;
            width: 300px;
        }

        .order-form label {
            display: block;
            margin-bottom: 10px;
        }

        .order-form input {
            width: 100%;
            padding: 8px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        .order-form button {
            background-color: #007bff;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .order-form button:hover {
            background-color: #0056b3;
        }

        .contact {
            display: none;
            padding: 20px;
            background-color: #fff;
            border-radius: 5px;
            margin: 20px auto;
            width: 300px;
        }

        .contact p {
            font-size: 18px;
            margin: 10px 0;
        }

        #cart {
            display: none;
            margin: 20px;
        }

        #cart h3 {
            margin-bottom: 20px;
        }

        #cart ul {
            list-style-type: none;
            padding: 0;
        }

        #cart ul li {
            background-color: #fff;
            margin: 10px 0;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        #cart button {
            background-color: #28a745;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
        }

        #cart button:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>

    <header>
        <h1>الصواوي لتجارة الأجهزة الإلكترونية</h1>
    </header>

    <nav>
        <a href="javascript:void(0)" onclick="showCategory('new')">أجهزة جديدة</a>
        <a href="javascript:void(0)" onclick="showCategory('used')">أجهزة مستعملة</a>
        <a href="javascript:void(0)" onclick="showCategory('laptop')">لابتوب استيراد</a>
        <a href="javascript:void(0)" onclick="showContact()">اتصل بنا</a>
        <a href="javascript:void(0)" onclick="showCart()">سلة المشتريات</a>
    </nav>

    <div class="banner"></div>

    <!-- الأقسام الرئيسية -->
    <section id="categories">
        <div class="category" onclick="showCategory('new')">
            <h2>أجهزة جديدة</h2>
        </div>
        <div class="category" onclick="showCategory('used')">
            <h2>أجهزة مستعملة</h2>
        </div>
        <div class="category" onclick="showCategory('laptop')">
            <h2>لابتوب استيراد</h2>
        </div>
    </section>

    <!-- المنتجات -->
    <section id="products" class="products"></section>

    <!-- سلة المشتريات -->
    <div id="cart">
        <h3>سلة المشتريات</h3>
        <ul id="cartItems"></ul>
        <button onclick="showOrderForm()">تأكيد الطلب</button>
    </div>

    <!-- نموذج الطلب -->
    <div id="orderForm" class="order-form">
        <h3>تأكيد الطلب</h3>
        <label for="name">الاسم الكامل</label>
        <input type="text" id="name" required>
        <label for="phone">رقم الهاتف</label>
        <input type="text" id="phone" required>
        <label for="address">العنوان</label>
        <input type="text" id="address" required>
        <button onclick="confirmOrder()">تأكيد الطلب</button>
    </div>

    <!-- قسم الاتصال بنا -->
    <div id="contactSection" class="contact">
        <h3>اتصل بنا</h3>
        <p>رقم خدمة العملاء: 01067250858</p>
    </div>

    <footer>
        <p>&copy; 2024 الصواوي لتجارة الأجهزة الإلكترونية. جميع الحقوق محفوظة.</p>
    </footer>

    <script>
        const products = {
            'new': [
                { name: 'iPhone 12 جديد', price: '12000 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 6.1 بوصة، ذاكرة 128 جيجابايت، كاميرا 12 ميجابكسل' },
                { name: 'Samsung S21 جديد', price: '10000 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 6.2 بوصة، ذاكرة 128 جيجابايت، كاميرا 64 ميجابكسل' },
                { name: 'Huawei Mate 40 جديد', price: '9000 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 6.5 بوصة، ذاكرة 256 جيجابايت، كاميرا 50 ميجابكسل' },
                { name: 'Xiaomi Mi 11 جديد', price: '8000 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 6.8 بوصة، ذاكرة 256 جيجابايت، كاميرا 108 ميجابكسل' },
                { name: 'OnePlus 9 جديد', price: '7000 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 6.55 بوصة، ذاكرة 128 جيجابايت، كاميرا 48 ميجابكسل' }
            ],
            'used': [
                { name: 'iPhone X مستعمل', price: '3000 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 5.8 بوصة، ذاكرة 64 جيجابايت، كاميرا 12 ميجابكسل' },
                { name: 'Samsung S9 مستعمل', price: '2500 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 5.8 بوصة، ذاكرة 64 جيجابايت، كاميرا 12 ميجابكسل' },
                { name: 'Huawei P30 مستعمل', price: '4000 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 6.1 بوصة، ذاكرة 128 جيجابايت، كاميرا 40 ميجابكسل' },
                { name: 'Xiaomi Mi 9 مستعمل', price: '3500 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 6.39 بوصة، ذاكرة 128 جيجابايت، كاميرا 48 ميجابكسل' },
                { name: 'OnePlus 7 مستعمل', price: '3000 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 6.41 بوصة، ذاكرة 128 جيجابايت، كاميرا 48 ميجابكسل' }
            ],
            'laptop': [
                { name: 'Dell Latitude 5490', price: '6000 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 14 بوصة، ذاكرة 256 جيجابايت، معالج Intel i5' },
                { name: 'HP EliteBook 840 G5', price: '7000 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 14 بوصة، ذاكرة 512 جيجابايت، معالج Intel i7' },
                { name: 'Lenovo ThinkPad T480', price: '6500 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 14 بوصة، ذاكرة 256 جيجابايت، معالج Intel i5' },
                { name: 'Dell XPS 13', price: '9000 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 13.3 بوصة، ذاكرة 512 جيجابايت، معالج Intel i7' },
                { name: 'Apple MacBook Pro', price: '12000 جنيه', img: 'https://via.placeholder.com/150', specs: 'مواصفات: شاشة 13 بوصة، ذاكرة 256 جيجابايت، معالج Apple M1' }
            ]
        };

        function showCategory(category) {
            const productSection = document.getElementById('products');
            productSection.innerHTML = '';
            products[category].forEach(product => {
                const productDiv = document.createElement('div');
                productDiv.className = 'product';
                productDiv.innerHTML = `
                    <img src="${product.img}" alt="${product.name}">
                    <h3>${product.name}</h3>
                    <p>${product.specs}</p>
                    <p>السعر: ${product.price}</p>
                    <button onclick="addToCart('${product.name}', '${product.price}')">أضف إلى السلة</button>
                `;
                productSection.appendChild(productDiv);
            });
        }

        let cart = [];

        function addToCart(name, price) {
            cart.push({ name, price });
            alert('تمت إضافة المنتج إلى السلة!');
        }

        function showCart() {
            const cartSection = document.getElementById('cart');
            const cartItems = document.getElementById('cartItems');
            cartItems.innerHTML = '';
            cart.forEach(item => {
                const li = document.createElement('li');
                li.textContent = `${item.name} - ${item.price}`;
                cartItems.appendChild(li);
            });
            cartSection.style.display = 'block';
            document.getElementById('products').style.display = 'none';
            document.getElementById('categories').style.display = 'none';
            document.getElementById('orderForm').style.display = 'none';
            document.getElementById('contactSection').style.display = 'none';
        }

        function showOrderForm() {
            document.getElementById('orderForm').style.display = 'block';
            document.getElementById('cart').style.display = 'none';
        }

        function confirmOrder() {
            alert('تم تأكيد الطلب. شكراً لتسوقك معنا!');
            document.getElementById('orderForm').style.display = 'none';
            document.getElementById('categories').style.display = 'block';
        }

        function showContact() {
            document.getElementById('contactSection').style.display = 'block';
            document.getElementById('products').style.display = 'none';
            document.getElementById('categories').style.display = 'none';
            document.getElementById('cart').style.display = 'none';
            document.getElementById('orderForm').style.display = 'none';
        }
    </script>
</body>
</html>
