# html_git_hub
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tienda de Ropa Deportiva</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script> <!-- Librería jsPDF -->
    <script src="https://cdn.jsdelivr.net/npm/jspdf-autotable@3.5.19/dist/jspdf.plugin.autotable.js"></script> <!-- AutoTable para jsPDF -->
    <script src="https://cdn.jsdelivr.net/npm/qrcode/build/qrcode.min.js"></script> <!-- QRCode.js -->
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css" rel="stylesheet"> <!-- Font Awesome para íconos -->
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }
        header {
            background-color: #28a745;
            color: white;
            padding: 20px;
            text-align: center;
        }
        nav {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 10px;
        }
        nav a {
            text-decoration: none;
            color: #333;
            font-weight: bold;
        }
        .container {
            padding: 20px;
        }
        .product-item {
            display: inline-block;
            width: 250px;
            margin: 10px;
            padding: 15px;
            background-color: white;
            border: 1px solid #ddd;
            border-radius: 8px;
            text-align: center;
        }
        .product-item img {
            width: 100%;
            height: auto;
            border-radius: 8px;
        }
        .product-item h3 {
            font-size: 20px;
            margin: 10px 0;
        }
        .product-item p {
            font-size: 18px;
            color: #28a745;
            margin: 10px 0;
        }
        .cart {
            margin-top: 20px;
        }
        .cart-item {
            display: flex;
            justify-content: space-between;
            padding: 5px 0;
        }
        button {
            padding: 10px;
            color: white;
            background-color: #28a745;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
        #payment-methods {
            margin-top: 20px;
        }
        .payment-form input {
            margin: 10px 0;
            padding: 10px;
            width: 100%;
        }
        footer {
            background-color: #28a745;
            color: white;
            padding: 20px;
            text-align: center;
        }
        .social-links a {
            margin: 0 10px;
            color: white;
            text-decoration: none;
            font-size: 24px;
        }
        .social-links a:hover {
            color: #fff;
            opacity: 0.7;
        }
        #qrCodeContainer {
            display: none;
            text-align: center;
            margin-top: 20px;
        }
        #qrCodeContainer img {
            width: 300px; /* Tamaño aumentado para la imagen del QR */
            height: auto;
        }
        #welcome-btn {
            display: block;
            margin: 20px auto;
            padding: 10px 20px;
            background-color: #28a745;
            color: white;
            border: none;
            cursor: pointer;
        }
        #welcome-btn:hover {
            background-color: #218838;
        }
        #welcome-message {
            text-align: center;
            padding: 20px;
            background-color: #28a745;
            color: white;
            border-radius: 8px;
            margin-top: 20px;
            display: none; /* Esto estará oculto hasta que el usuario haga clic en el botón */
        }
    </style>
</head>
<body>
                                                                                                                                                                                 
<header>
    <h1>Bienvenidos a SPORT SCZ</h1>
</header>

<button id="welcome-btn" onclick="showWelcomeMessage()">Bienvenido</button>

<nav>
    <a href="#" onclick="showSection('contacto')">Bienvenidos</a>
    <a href="#" onclick="showSection('productos')">Productos</a>
    <a href="#" onclick="showSection('carrito')">Carrito</a>
    <a href="#" onclick="showSection('contacto')">Contacto</a>
</nav>

<div id="productos" class="container">
    <h2>Productos Disponibles</h2>

    <!-- Producto 1 -->
    <div class="product-item">
        <img src="https://cicadex.com/wp-content/uploads/2020/01/350-33-Camiseta-Hom-Azul-ped-27-3-4-RH-copia.jpg" width="300" height="100" alt="Camiseta Deportiva">
        <h3>Camiseta Deportiva</h3>
        <p>Bs120</p>
        <button onclick="addToCart('Camiseta Deportiva', 30)">Añadir al Carrito</button>
    </div>
    <!-- Producto 2 -->
    <div class="product-item">
        <img src="https://www.abyss.com.ar/img_productos/25I-0142.jpg" width="300" height="100" alt="Pantalón Deportivo">
        <h3>Pantalón Deportivo</h3>
        <p>Bs150</p>
        <button onclick="addToCart('Pantalón Deportivo', 30)">Añadir al Carrito</button>
    </div>
    <!-- Producto 3 -->
    <div class="product-item">
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSPQpDLSPEwNQF535arbUuMLmIribGdNk8tAg&s" alt="Zapatillas Deportivas">
        <h3>Zapatillas Futsal</h3>
        <p>Bs450</p>
        <button onclick="addToCart('Zapatillas de Futsal', 250)">Añadir al Carrito</button>
    </div>
    <!-- Producto 4 -->
    <div class="product-item">
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQREP5pKpCEcgaXaYf99nQx7bRAzQGy7VXjZw&s" width="300" height="100" alt="Medias Antideslizante">
        <h3>Medias Antideslizante</h3>
        <p>Bs30</p>
        <button onclick="addToCart('Medias Antideslizante', 20)">Añadir al Carrito</button>
    </div>
    <!-- Producto 5 -->
    <div class="product-item">
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRVHDMsAgtvw7V-yCKZsQWWmU-9XotkQsUqhA&s" width="300" height="100" alt="Zapatillas de Futsal">
        <h3>Zapatillas de Deportivas</h3>
        <p>Bs600</p>
        <button onclick="addToCart('Zapatillas Deportivas', 800)">Añadir al Carrito</button>
    </div>
    <!-- Producto 6 -->
    <div class="product-item">
        <img src="https://www.hites.com/dw/image/v2/BDPN_PRD/on/demandware.static/-/Sites-mastercatalog_HITES/default/dw8e228a64/images/original/pim/847401001/847401001_1.jpg?sw=1000&sh=1000" alt="Short Deportivo">
        <h3>Short Deportivo</h3>
        <p>Bs80</p>
        <button onclick="addToCart('Short Deportivo', 30)">Añadir al Carrito</button>
    </div>
    <!-- Producto 7 -->
    <div class="product-item">
        <img src="https://m.media-amazon.com/images/I/51GPQolvYNL.jpg" width="300" height="100" alt="Chamarra Deportiva">
        <h3>Chamarra Deportiva</h3>
        <p>Bs180</p>
        <button onclick="addToCart('Chamarra Deportiva', 80)">Añadir al Carrito</button>
    </div>
    <!-- Producto 8 -->
    <div class="product-item">
        <img src="https://cdnx.jumpseller.com/accesorios-noit/image/67907808/resize/306/407?1758822748" width="300" height="100" alt="Rodillera Deportiva">
        <h3>Rodillera Deportiva</h3>
        <p>Bs250</p>
        <button onclick="addToCart('Rodillera Deportiva', 120)">Añadir al Carrito</button>
    </div>
    <!-- Producto 9 -->
    <div class="product-item">
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcThpREi6lb2fbj5nwXhgW4HUH0uVoZ0mR-3UA&s" alt="Canilleras">
        <h3>Canilleras</h3>
        <p>Bs150</p>
        <button onclick="addToCart('Canilleras', 60)">Añadir al Carrito</button>
    </div>
    <!-- Producto 10 -->
    <div class="product-item">
        <img src="https://static.nike.com/a/images/t_web_pw_592_v2/f_auto/d6d842fe-e77e-4d07-b30b-3f495fe303be/NK+ELMNTL+BKPK+-+HBR.png" alt="Mochila Deportiva">
        <h3>Mochila Deportiva</h3>
        <p>Bs370</p>
        <button onclick="addToCart('Mochila Deportiva', 40)">Añadir al Carrito</button>
    </div>
</div>

<div id="carrito" class="container" style="display: none;">
    <h2>Carrito de Compras</h2>
    <div id="cartItems"></div>
    <div id="cartTotal" class="cart"></div>
    <div id="payment-methods">
        <h3>Métodos de Pago</h3>
        <button onclick="payWithCard()">Pagar con Tarjeta</button>
        <button onclick="payWithQR()">Pagar con QR</button>
    </div>

    <div id="payment-form" class="payment-form" style="display: none;">
        <input type="text" id="cardNumber" placeholder="Número de tarjeta">
        <input type="text" id="cardHolder" placeholder="Titular de la tarjeta">
        <input type="date" id="expiryDate" placeholder="Fecha de expiración">
        <input type="text" id="cvv" placeholder="CVV">
        <button onclick="generateInvoice()">Generar Factura</button>
    </div>
</div>

<div id="qrCodeContainer">
    <h3>Escanea el código QR para realizar el pago</h3>
    <div id="qrCode"></div> <!-- Aquí se generará el código QR -->
</div>

<div id="contacto" class="container" style="display: none;">
    <h2>Contacto</h2>
    <p>Si tienes alguna pregunta, no dudes en contactarnos.</p>
    <p>Email: sportscztiendadeportiva@gmail.com</p>
    <p>Teléfono: +591 62020462</p>
</div>
<footer>
    <p>Gracias por visitar nuestra tienda. ¡Esperamos verte pronto!</p>
    <div class="social-links">
        <a href="https://www.facebook.com/share/19Sff2F1sh/" target="_blank"><i class="fab fa-facebook"></i></a>
        <a href="https://web.whatsapp.com/" target="_blank"><i class="fab fa-whatsapp"></i></a>
        <a href="https://www.instagram.com/tienda_sport1221?igsh=MXcyMHJydWliZmF0ZQ==" target="_blank"><i class="fab fa-instagram"></i></a>
    </div>
</footer>

<script>
    let cart = [];

    function showSection(section) {
        document.querySelectorAll('.container').forEach(container => container.style.display = 'none');
        document.getElementById(section).style.display = 'block';
    }

    function addToCart(item, price) {
        cart.push({ item, price });
        alert(item + ' añadido al carrito.');
        updateCartDisplay();
    }

    function updateCartDisplay() {
        const cartItems = document.getElementById('cartItems');
        const cartTotal = document.getElementById('cartTotal');
        cartItems.innerHTML = '';
        let total = 0;

        cart.forEach(({ item, price }) => {
            cartItems.innerHTML += `<div class="cart-item"><span>${item}</span><span>$${price}</span></div>`;
            total += price;
        });

        cartTotal.innerHTML = `<strong>Total: $${total}</strong>`;
    }

    function payWithCard() {
        document.getElementById('payment-form').style.display = 'block'; // Muestra el formulario de tarjeta
    }

    function payWithQR() {
        const qrCodeContainer = document.getElementById('qrCodeContainer');
        qrCodeContainer.style.display = 'block'; // Muestra el QR
        generateQRCode('https://example.com/pago'); // Cambia este enlace por el enlace de pago correspondiente
    }

    function generateQRCode(paymentLink) {
        QRCode.toDataURL(paymentLink, function (err, url) {
            const qrCode = document.getElementById('qrCode');
            qrCode.innerHTML = `<img src="Imagen/qr.jpg" alt="QR de pago">`; // Muestra el código QR
        });
    }

    function generateInvoice() {
        const { jsPDF } = window.jspdf;
        const doc = new jsPDF();
        let total = 0;

        doc.text('Factura de Compra', 10, 10);
        doc.text(`Fecha: ${new Date().toLocaleDateString()}`, 10, 20);

        let tableBody = cart.map(item => {
            total += item.price;
            return [item.item, `$${item.price}`];
        });

        doc.autoTable({
            head: [['Producto', 'Precio']],
            body: tableBody,
            startY: 30, // Posición inicial de la tabla
            theme: 'grid', // Estilo de la tabla
            margin: { horizontal: 10 },
        });

        doc.text(`Total: $${total}`, 10, doc.lastAutoTable.finalY + 10);
        doc.save('Factura.pdf');
    }

    function showWelcomeMessage() {
        alert("¡Bienvenido a nuestra tienda de ropa deportiva! Estamos felices de tenerte con nosotros.");
    }
</script>

</body>
</html>


