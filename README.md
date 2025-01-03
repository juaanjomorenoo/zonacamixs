<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tienda Online</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f9f9f9;
            color: #333;
        }
        header {
            background-color: #4CAF50;
            color: white;
            padding: 1rem 0;
            text-align: center;
        }
        nav {
            background-color: #333;
            color: white;
            padding: 1rem;
            text-align: center;
        }
        nav a {
            color: white;
            margin: 0 1rem;
            text-decoration: none;
        }
        main {
            padding: 2rem;
        }
        .catalog {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 1rem;
        }
        .product {
            border: 1px solid #ddd;
            border-radius: 5px;
            padding: 1rem;
            text-align: center;
            background-color: white;
        }
        .product img {
            max-width: 100%;
            height: auto;
        }
        .product h3 {
            margin: 0.5rem 0;
        }
        .product p {
            margin: 0.5rem 0;
        }
        .product button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 5px;
            cursor: pointer;
        }
        .product button:hover {
            background-color: #45a049;
        }
        .cart {
            margin-top: 2rem;
            border: 1px solid #ddd;
            padding: 1rem;
            background-color: white;
            border-radius: 5px;
        }
        .cart h3 {
            margin: 0;
        }
        .cart-items {
            list-style: none;
            padding: 0;
            margin: 1rem 0;
        }
        .cart-items li {
            display: flex;
            justify-content: space-between;
            margin: 0.5rem 0;
        }
        .cart-total {
            font-weight: bold;
            margin-top: 1rem;
        }
        .checkout-buttons {
            margin-top: 1rem;
            display: flex;
            gap: 1rem;
        }
        .checkout-buttons button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 5px;
            cursor: pointer;
        }
        .checkout-buttons button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>
    <header>
        <h1>Tienda Online</h1>
    </header>
    <nav>
        <a href="#catalogo">Catálogo</a>
        <a href="#carrito">Carrito</a>
    </nav>
    <main>
        <section id="catalogo">
            <h2>Catálogo de Productos</h2>
            <div class="catalog">
                <div class="product" data-id="1" data-name="Producto 1" data-price="10">
                    <img src="https://via.placeholder.com/200" alt="Producto 1">
                    <h3>Producto 1</h3>
                    <p>$10.00</p>
                    <button class="add-to-cart">Añadir al Carrito</button>
                </div>
                <div class="product" data-id="2" data-name="Producto 2" data-price="20">
                    <img src="https://via.placeholder.com/200" alt="Producto 2">
                    <h3>Producto 2</h3>
                    <p>$20.00</p>
                    <button class="add-to-cart">Añadir al Carrito</button>
                </div>
                <div class="product" data-id="3" data-name="Producto 3" data-price="30">
                    <img src="https://via.placeholder.com/200" alt="Producto 3">
                    <h3>Producto 3</h3>
                    <p>$30.00</p>
                    <button class="add-to-cart">Añadir al Carrito</button>
                </div>
            </div>
        </section>
        <section id="carrito">
            <h2>Carrito</h2>
            <div class="cart">
                <h3>Productos en el carrito</h3>
                <ul class="cart-items"></ul>
                <p class="cart-total">Total: $0.00</p>
                <div class="checkout-buttons">
                    <button id="pay-paypal">Pagar con PayPal</button>
                    <button id="pay-cod">Pagar Contra Reembolso</button>
                </div>
            </div>
        </section>
    </main>
    <script>
        // Variables
        const cartItems = [];
        const cartItemsList = document.querySelector('.cart-items');
        const cartTotal = document.querySelector('.cart-total');

        // Función para actualizar el carrito
        function updateCart() {
            cartItemsList.innerHTML = '';
            let total = 0;
            cartItems.forEach(item => {
                const li = document.createElement('li');
                li.textContent = `${item.name} - $${item.price}`;
                cartItemsList.appendChild(li);
                total += item.price;
            });
            cartTotal.textContent = `Total: $${total.toFixed(2)}`;
        }

        // Función para añadir al carrito
        function addToCart(e) {
            const product = e.target.closest('.product');
            const id = product.dataset.id;
            const name = product.dataset.name;
            const price = parseFloat(product.dataset.price);
            cartItems.push({ id, name, price });
            updateCart();
        }

        // Añadir eventos a los botones de añadir al carrito
        document.querySelectorAll('.add-to-cart').forEach(button => {
            button.addEventListener('click', addToCart);
        });

        // Placeholder para procesar pagos
        document.getElementById('pay-paypal').addEventListener('click', () => {
            alert('Redirigiendo a PayPal...');
        });

        document.getElementById('pay-cod').addEventListener('click', () => {
            alert('Pedido realizado con opción de contra reembolso.');
        });
    </script>
</body>
</html>
