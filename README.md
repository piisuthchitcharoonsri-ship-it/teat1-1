<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ร้านขายของออนไลน์</title>
  <style>
    body {
      font-family: 'Prompt', sans-serif;
      background-color: #fdf6f9;
      margin: 0;
      padding: 0;
      color: #333;
    }
    header {
      background: #ffd6e8;
      padding: 20px;
      text-align: center;
      border-bottom: 3px solid #ffb3c6;
    }
    header h1 {
      margin: 0;
      color: #d63384;
    }
    nav a {
      text-decoration: none;
      color: #d63384;
      font-weight: bold;
      margin: 0 10px;
      cursor: pointer;
    }
    .products {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin: 30px;
      flex-wrap: wrap;
    }
    .product {
      background: #fff0f6;
      border: 2px solid #ffb3c6;
      border-radius: 12px;
      padding: 20px;
      width: 200px;
      text-align: center;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      margin-bottom: 20px;
    }
    .product img {
      max-width: 100%;
      border-radius: 8px;
    }
    button {
      background: #ff85a1;
      color: white;
      border: none;
      padding: 10px;
      border-radius: 8px;
      cursor: pointer;
      transition: 0.3s;
      margin-top: 10px;
    }
    button:hover {
      background: #d63384;
    }
    .cart {
      padding: 20px;
      max-width: 500px;
      margin: 30px auto;
      background: #fff0f6;
      border: 2px solid #ffb3c6;
      border-radius: 12px;
    }
    .cart ul {
      padding-left: 20px;
      margin: 0 0 10px 0;
    }
    .cart li {
      margin-bottom: 8px;
    }
    .remove-btn {
      background: #d63384;
      color: #fff;
      border: none;
      border-radius: 6px;
      padding: 4px 8px;
      margin-left: 10px;
      cursor: pointer;
      font-size: 12px;
    }
    .remove-btn:hover {
      background: #ff85a1;
    }
    .hidden {
      display: none;
    }
    .active-link {
      text-decoration: underline;
    }
  </style>
</head>
<body>
  <header>
    <h1>ร้านขายของออนไลน์</h1>
    <nav>
      <a id="shop-link" class="active-link" onclick="showSection('shop')">หน้าร้าน</a>
      <a id="cart-link" onclick="showSection('cart')">ตะกร้าสินค้า 🛒</a>
    </nav>
  </header>
  <main>
    <Product List Section >
    <section id="shop-section">
      <div class="products">
        <div class="product">
          <img src="https://via.placeholder.com/200" alt="สินค้า 1">
          <h2>สินค้า 1</h2>
          <p>ราคา: 100 บาท</p>
          <button onclick="addToCart('สินค้า 1', 100)">หยิบใส่ตะกร้า</button>
        </div>
        <div class="product">
          <img src="https://via.placeholder.com/200" alt="สินค้า 2">
          <h2>สินค้า 2</h2>
          <p>ราคา: 200 บาท</p>
          <button onclick="addToCart('สินค้า 2', 200)">หยิบใส่ตะกร้า</button>
        </div>
        <div class="product">
          <img src="https://via.placeholder.com/200" alt="สินค้า 3">
          <h2>สินค้า 3</h2>
          <p>ราคา: 300 บาท</p>
          <button onclick="addToCart('สินค้า 3', 300)">หยิบใส่ตะกร้า</button>
        </div>
      </div>
   
   </section>
   
   <-- Cart Section -->
   
   <section id="cart-section" class="hidden">
      <div class="cart">
        <h2>ตะกร้าสินค้า</h2>
        <ul id="cart-items"></ul>
        <p id="cart-total">รวมทั้งหมด: 0 บาท</p>
        <button onclick="clearCart()" style="margin-top:10px;">ล้างตะกร้าสินค้า</button>
      </div>
    </section>
  </main>
  <script>/Show/Hide sections
    function showSection(section) {
      document.getElementById('shop-section').classList.add('hidden');
      document.getElementById('cart-section').classList.add('hidden');
      document.getElementById('shop-link').classList.remove('active-link');
      document.getElementById('cart-link').classList.remove('active-link');
      if (section === 'shop') {
        document.getElementById('shop-section').classList.remove('hidden');
        document.getElementById('shop-link').classList.add('active-link');
      } else {
        document.getElementById('cart-section').classList.remove('hidden');
        document.getElementById('cart-link').classList.add('active-link');
        loadCart();
      }
    }
    / Add to cart
    function addToCart(name, price) {
      let cart = JSON.parse(localStorage.getItem("cart")) || [];
      cart.push({ name, price });
      localStorage.setItem("cart", JSON.stringify(cart));
      alert(name + " ถูกเพิ่มเข้าตะกร้าแล้ว!");
    }
  / Remove from cart
    function removeFromCart(index) {
      let cart = JSON.parse(localStorage.getItem("cart")) || [];
      cart.splice(index, 1);
      localStorage.setItem("cart", JSON.stringify(cart));
      loadCart();
    }
  / Clear cart
    function clearCart() {
      localStorage.removeItem("cart");
      loadCart();
    }
/ Load cart
    function loadCart() {
      let cart = JSON.parse(localStorage.getItem("cart")) || [];
      let cartItems = document.getElementById("cart-items");
      let cartTotal = document.getElementById("cart-total");
      let total = 0;
   cartItems.innerHTML = "";
      if (cart.length === 0) {
        let li = document.createElement("li");
        li.textContent = "ไม่มีสินค้าในตะกร้า";
        cartItems.appendChild(li);
      } else {
        cart.forEach((item, index) => {
          let li = document.createElement("li");
          li.textContent = `${item.name} - ${item.price} บาท`;
          let removeBtn = document.createElement("button");
          removeBtn.textContent = "ลบ";
          removeBtn.className = "remove-btn";
          removeBtn.onclick = function() { removeFromCart(index); };
          li.appendChild(removeBtn);
          cartItems.appendChild(li);
          total += item.price;
        });
      }
      cartTotal.textContent = "รวมทั้งหมด: " + total + " บาท";
    }
   / Initial view
    showSection('shop');
  </script>
</body>
</html>
