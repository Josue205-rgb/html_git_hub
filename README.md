# html_git_hub
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tienda de Ropa Deportiva - SPORT SCZ</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/jspdf-autotable@3.5.19/dist/jspdf.plugin.autotable.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/qrcode/build/qrcode.min.js"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }

        header {
            background: linear-gradient(135deg, #28a745 0%, #20c997 100%);
            color: white;
            padding: 30px 20px;
            text-align: center;
            box-shadow: 0 4px 20px rgba(0,0,0,0.2);
        }

        header h1 {
            font-size: 2.5em;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
            margin-bottom: 10px;
        }

        #welcome-btn {
            margin-top: 15px;
            padding: 12px 30px;
            background: white;
            color: #28a745;
            border: none;
            border-radius: 25px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        #welcome-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0,0,0,0.3);
        }

        nav {
            background: white;
            display: flex;
            justify-content: center;
            gap: 30px;
            padding: 20px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            flex-wrap: wrap;
        }

        nav a {
            text-decoration: none;
            color: #333;
            font-weight: bold;
            padding: 10px 20px;
            border-radius: 20px;
            transition: all 0.3s;
        }

        nav a:hover {
            background: linear-gradient(135deg, #28a745 0%, #20c997 100%);
            color: white;
            transform: translateY(-2px);
        }

        .container {
            padding: 30px 20px;
            max-width: 1400px;
            margin: 0 auto;
        }

        .container h2 {
            color: white;
            text-align: center;
            margin-bottom: 30px;
            font-size: 2em;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        .product-item {
            display: inline-block;
            width: 280px;
            margin: 15px;
            padding: 20px;
            background: white;
            border-radius: 15px;
            text-align: center;
            transition: all 0.3s;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            vertical-align: top;
        }

        .product-item:hover {
            transform: translateY(-10px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .product-item img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 10px;
            margin-bottom: 15px;
        }

        .product-item h3 {
            font-size: 1.3em;
            margin: 10px 0;
            color: #333;
        }

        .product-item p {
            font-size: 1.5em;
            color: #28a745;
            font-weight: bold;
            margin: 10px 0;
        }

        button {
            padding: 12px 25px;
            color: white;
            background: linear-gradient(135deg, #28a745 0%, #20c997 100%);
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s;
            box-shadow: 0 4px 15px rgba(40, 167, 69, 0.3);
        }

        button:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(40, 167, 69, 0.4);
        }

        .btn-danger {
            background: linear-gradient(135deg, #dc3545 0%, #c82333 100%);
            padding: 8px 15px;
            font-size: 0.9em;
            box-shadow: 0 4px 15px rgba(220, 53, 69, 0.3);
        }

        .btn-danger:hover {
            box-shadow: 0 6px 20px rgba(220, 53, 69, 0.4);
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            margin: 10px 0;
            background: white;
            border-radius: 10px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .cart-item-info {
            flex-grow: 1;
            text-align: left;
        }

        .cart-item-name {
            font-weight: bold;
            font-size: 1.1em;
            color: #333;
        }

        .cart-item-price {
            color: #28a745;
            font-weight: bold;
        }

        #cartTotal {
            background: white;
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
            text-align: right;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        #cartTotal strong {
            font-size: 1.5em;
            color: #28a745;
        }

        #payment-methods {
            margin-top: 30px;
            text-align: center;
        }

        #payment-methods h3 {
            color: white;
            margin-bottom: 20px;
        }

        #payment-methods button {
            margin: 0 10px;
        }

        .payment-form {
            background: white;
            padding: 30px;
            border-radius: 15px;
            margin-top: 20px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .payment-form input {
            width: 100%;
            margin: 10px 0;
            padding: 15px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            transition: border-color 0.3s;
        }

        .payment-form input:focus {
            outline: none;
            border-color: #28a745;
        }

        #qrCodeContainer {
            display: none;
            background: white;
            padding: 30px;
            border-radius: 15px;
            margin-top: 20px;
            text-align: center;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        #qrCodeContainer h3 {
            color: #333;
            margin-bottom: 20px;
        }

        #qrCode canvas {
            margin: 20px auto;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        .contact-card {
            background: white;
            padding: 40px;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            max-width: 600px;
            margin: 0 auto;
        }

        .contact-card h2 {
            color: #333;
            margin-bottom: 20px;
        }

        .contact-card p {
            color: #666;
            font-size: 1.1em;
            margin: 15px 0;
        }

        .contact-card i {
            color: #28a745;
            margin-right: 10px;
        }

        footer {
            background: linear-gradient(135deg, #28a745 0%, #20c997 100%);
            color: white;
            padding: 30px 20px;
            text-align: center;
            margin-top: 50px;
        }

        .social-links {
            margin-top: 20px;
        }

        .social-links a {
            margin: 0 15px;
            color: white;
            text-decoration: none;
            font-size: 28px;
            transition: all 0.3s;
        }

        .social-links a:hover {
            transform: scale(1.2);
            opacity: 0.8;
        }

        .empty-cart {
            text-align: center;
            padding: 60px 20px;
            color: white;
        }

        .empty-cart i {
            font-size: 4em;
            margin-bottom: 20px;
            opacity: 0.7;
        }

        .empty-cart h3 {
            font-size: 1.8em;
            margin-bottom: 10px;
        }

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

        .cart-item {
            animation: fadeIn 0.5s;
        }
    </style>
</head>
<body>

<header>
    <h1><i class="fas fa-running"></i> SPORT SCZ</h1>
    <p style="font-size: 1.2em; margin-top: 10px;">Tu tienda deportiva de confianza</p>
    <button id="welcome-btn" onclick="showWelcomeMessage()">
        <i class="fas fa-hand-sparkles"></i> Bienvenido
    </button>
</header>

<nav>
    <a href="#" onclick="showSection('productos')"><i class="fas fa-tshirt"></i> Productos</a>
    <a href="#" onclick="showSection('carrito')"><i class="fas fa-shopping-cart"></i> Carrito (<span id="cartCount">0</span>)</a>
    <a href="#" onclick="showSection('contacto')"><i class="fas fa-phone"></i> Contacto</a>
</nav>

<div id="productos" class="container">
    <h2>Productos Disponibles</h2>

    <div class="product-item">
        <img src="https://cicadex.com/wp-content/uploads/2020/01/350-33-Camiseta-Hom-Azul-ped-27-3-4-RH-copia.jpg" alt="Camiseta Deportiva">
        <h3>Camiseta Deportiva</h3>
        <p>Bs 120</p>
        <button onclick="addToCart('Camiseta Deportiva', 120)"><i class="fas fa-cart-plus"></i> Añadir</button>
    </div>

    <div class="product-item">
        <img src="https://www.abyss.com.ar/img_productos/25I-0142.jpg" alt="Pantalón Deportivo">
        <h3>Pantalón Deportivo</h3>
        <p>Bs 150</p>
        <button onclick="addToCart('Pantalón Deportivo', 150)"><i class="fas fa-cart-plus"></i> Añadir</button>
    </div>

    <div class="product-item">
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSPQpDLSPEwNQF535arbUuMLmIribGdNk8tAg&s" alt="Zapatillas Futsal">
        <h3>Zapatillas Futsal</h3>
        <p>Bs 450</p>
        <button onclick="addToCart('Zapatillas Futsal', 450)"><i class="fas fa-cart-plus"></i> Añadir</button>
    </div>

    <div class="product-item">
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQREP5pKpCEcgaXaYf99nQx7bRAzQGy7VXjZw&s" alt="Medias Antideslizante">
        <h3>Medias Antideslizante</h3>
        <p>Bs 30</p>
        <button onclick="addToCart('Medias Antideslizante', 30)"><i class="fas fa-cart-plus"></i> Añadir</button>
    </div>

    <div class="product-item">
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRVHDMsAgtvw7V-yCKZsQWWmU-9XotkQsUqhA&s" alt="Zapatillas Deportivas">
        <h3>Zapatillas Deportivas</h3>
        <p>Bs 600</p>
        <button onclick="addToCart('Zapatillas Deportivas', 600)"><i class="fas fa-cart-plus"></i> Añadir</button>
    </div>

    <div class="product-item">
        <img src="https://www.hites.com/dw/image/v2/BDPN_PRD/on/demandware.static/-/Sites-mastercatalog_HITES/default/dw8e228a64/images/original/pim/847401001/847401001_1.jpg?sw=1000&sh=1000" alt="Short Deportivo">
        <h3>Short Deportivo</h3>
        <p>Bs 80</p>
        <button onclick="addToCart('Short Deportivo', 80)"><i class="fas fa-cart-plus"></i> Añadir</button>
    </div>

    <div class="product-item">
        <img src="https://m.media-amazon.com/images/I/51GPQolvYNL.jpg" alt="Chamarra Deportiva">
        <h3>Chamarra Deportiva</h3>
        <p>Bs 180</p>
        <button onclick="addToCart('Chamarra Deportiva', 180)"><i class="fas fa-cart-plus"></i> Añadir</button>
    </div>

    <div class="product-item">
        <img src="https://cdnx.jumpseller.com/accesorios-noit/image/67907808/resize/306/407?1758822748" alt="Rodillera Deportiva">
        <h3>Rodillera Deportiva</h3>
        <p>Bs 250</p>
        <button onclick="addToCart('Rodillera Deportiva', 250)"><i class="fas fa-cart-plus"></i> Añadir</button>
    </div>

    <div class="product-item">
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcThpREi6lb2fbj5nwXhgW4HUH0uVoZ0mR-3UA&s" alt="Canilleras">
        <h3>Canilleras</h3>
        <p>Bs 150</p>
        <button onclick="addToCart('Canilleras', 150)"><i class="fas fa-cart-plus"></i> Añadir</button>
    </div>

    <div class="product-item">
        <img src="https://static.nike.com/a/images/t_web_pw_592_v2/f_auto/d6d842fe-e77e-4d07-b30b-3f495fe303be/NK+ELMNTL+BKPK+-+HBR.png" alt="Mochila Deportiva">
        <h3>Mochila Deportiva</h3>
        <p>Bs 370</p>
        <button onclick="addToCart('Mochila Deportiva', 370)"><i class="fas fa-cart-plus"></i> Añadir</button>
    </div>
</div>

<div id="carrito" class="container" style="display: none;">
    <h2><i class="fas fa-shopping-cart"></i> Carrito de Compras</h2>
    <div id="cartItems"></div>
    <div id="cartTotal"></div>
    
    <div id="payment-methods">
        <h3>Métodos de Pago</h3>
        <button onclick="payWithCard()"><i class="fas fa-credit-card"></i> Pagar con Tarjeta</button>
        <button onclick="payWithQR()"><i class="fas fa-qrcode"></i> Pagar con QR</button>
    </div>

    <div id="payment-form" class="payment-form" style="display: none;">
        <h3 style="color: #333; margin-bottom: 20px;">Datos de la Tarjeta</h3>
        <input type="text" id="cardNumber" placeholder="Número de tarjeta">
        <input type="text" id="cardHolder" placeholder="Titular de la tarjeta">
        <input type="date" id="expiryDate" placeholder="Fecha de expiración">
        <input type="text" id="cvv" placeholder="CVV">
        <button onclick="generateInvoice()"><i class="fas fa-file-invoice"></i> Generar Factura</button>
    </div>

    <div id="qrCodeContainer">
        <h3>Escanea el código QR para realizar el pago</h3>
        <div id="qrCode"></div>
        <p style="margin-top: 20px; color: #666;">Total a pagar: Bs <span id="qrTotal">0</span></p>
    </div>
</div>

<div id="contacto" class="container" style="display: none;">
    <div class="contact-card">
        <h2><i class="fas fa-address-card"></i> Contacto</h2>
        <p>Si tienes alguna pregunta, no dudes en contactarnos.</p>
        <p><i class="fas fa-envelope"></i> Email: sportscztiendadeportiva@gmail.com</p>
        <p><i class="fas fa-phone-alt"></i> Teléfono: +591 62020462</p>
        <p><i class="fas fa-map-marker-alt"></i> Santa Cruz, Bolivia</p>
    </div>
</div>

<footer>
    <p style="font-size: 1.2em; margin-bottom: 10px;">Gracias por visitar nuestra tienda. ¡Esperamos verte pronto!</p>
    <p>SPORT SCZ - Tu mejor opción deportiva</p>
    <div class="social-links">
        <a href="https://www.facebook.com/share/19Sff2F1sh/" target="_blank" title="Facebook">
            <i class="fab fa-facebook"></i>
        </a>
        <a href="https://web.whatsapp.com/" target="_blank" title="WhatsApp">
            <i class="fab fa-whatsapp"></i>
        </a>
        <a href="https://www.instagram.com/tienda_sport1221?igsh=MXcyMHJydWliZmF0ZQ==" target="_blank" title="Instagram">
            <i class="fab fa-instagram"></i>
        </a>
    </div>
</footer>

<script>
    let cart = [];

    function showSection(section) {
        document.querySelectorAll('.container').forEach(container => container.style.display = 'none');
        document.getElementById(section).style.display = 'block';
        
        if (section === 'carrito') {
            updateCartDisplay();
        }
    }

    function addToCart(item, price) {
        cart.push({ 
            id: Date.now(),
            item, 
            price 
        });
        updateCartCount();
        
        // Notificación mejorada
        const notification = document.createElement('div');
        notification.style.cssText = `
            position: fixed;
            top: 100px;
            right: 20px;
            background: linear-gradient(135deg, #28a745 0%, #20c997 100%);
            color: white;
            padding: 20px 30px;
            border-radius: 10px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.3);
            z-index: 1000;
            animation: slideIn 0.5s;
        `;
        notification.innerHTML = `<i class="fas fa-check-circle"></i> ${item} añadido al carrito`;
        document.body.appendChild(notification);
        
        setTimeout(() => {
            notification.remove();
        }, 3000);
    }

    function removeFromCart(id) {
        cart = cart.filter(item => item.id !== id);
        updateCartDisplay();
        updateCartCount();
    }

    function updateCartCount() {
        document.getElementById('cartCount').textContent = cart.length;
    }

    function updateCartDisplay() {
        const cartItems = document.getElementById('cartItems');
        const cartTotal = document.getElementById('cartTotal');
        
        if (cart.length === 0) {
            cartItems.innerHTML = `
                <div class="empty-cart">
                    <i class="fas fa-shopping-cart"></i>
                    <h3>Tu carrito está vacío</h3>
                    <p>Agrega productos para comenzar tu compra</p>
                </div>
            `;
            cartTotal.innerHTML = '';
            return;
        }
        
        cartItems.innerHTML = '';
        let total = 0;

        cart.forEach(({ id, item, price }) => {
            const cartItem = document.createElement('div');
            cartItem.className = 'cart-item';
            cartItem.innerHTML = `
                <div class="cart-item-info">
                    <div class="cart-item-name">${item}</div>
                    <div class="cart-item-price">Bs ${price}</div>
                </div>
                <button class="btn-danger" onclick="removeFromCart(${id})">
                    <i class="fas fa-trash"></i> Eliminar
                </button>
            `;
            cartItems.appendChild(cartItem);
            total += price;
        });

        cartTotal.innerHTML = `<strong>Total: Bs ${total}</strong>`;
    }

    function payWithCard() {
        document.getElementById('payment-form').style.display = 'block';
        document.getElementById('qrCodeContainer').style.display = 'none';
    }

    function payWithQR() {
        const total = cart.reduce((sum, item) => sum + item.price, 0);
        document.getElementById('qrTotal').textContent = total;
        document.getElementById('qrCodeContainer').style.display = 'block';
        document.getElementById('payment-form').style.display = 'none';
        
        const paymentData = `SPORT SCZ - Total: Bs ${total}`;
        QRCode.toCanvas(document.createElement('canvas'), paymentData, {
            width: 300,
            margin: 2,
            color: {
                dark: '#28a745',
                light: '#ffffff'
            }
        }, function (err, canvas) {
            const qrCode = document.getElementById('qrCode');
            qrCode.innerHTML = '';
            qrCode.appendChild(canvas);
        });
    }

    function generateInvoice() {
        if (cart.length === 0) {
            alert('El carrito está vacío');
            return;
        }

        const { jsPDF } = window.jspdf;
        const doc = new jsPDF();
        let total = 0;

        doc.setFontSize(20);
        doc.text('SPORT SCZ', 105, 20, { align: 'center' });
        doc.setFontSize(16);
        doc.text('Factura de Compra', 105, 30, { align: 'center' });
        doc.setFontSize(12);
        doc.text(`Fecha: ${new Date().toLocaleDateString()}`, 20, 45);
        doc.text(`Hora: ${new Date().toLocaleTimeString()}`, 20, 52);

        let tableBody = cart.map(item => {
            total += item.price;
            return [item.item, `Bs ${item.price}`];
        });

        doc.autoTable({
            head: [['Producto', 'Precio']],
            body: tableBody,
            startY: 60,
            theme: 'striped',
            headStyles: { fillColor: [40, 167, 69] },
            margin: { horizontal: 20 },
        });

        doc.setFontSize(14);
        doc.text(`Total: Bs ${total}`, 20, doc.lastAutoTable.finalY + 15);
        doc.text('¡Gracias por su compra!', 105, doc.lastAutoTable.finalY + 30, { align: 'center' });
        
        doc.save('Factura_SPORT_SCZ.pdf');
        
        alert('Factura generada exitosamente');
    }

    function showWelcomeMessage() {
        alert("¡Bienvenido a SPORT SCZ! 🏃‍♂️\n\nTu tienda deportiva de confianza en Santa Cruz.\nEncuentra los mejores productos para tu entrenamiento.");
    }

    // Mostrar productos por defecto
    showSection('productos');
</script>

</body>
</html>
