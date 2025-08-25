<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ร้านขายของ</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>ร้านขายของออนไลน์</h1>
    <nav>
      <a href="cart.html">ไปที่ตะกร้า 🛒</a>
    </nav>
  </header>
  <main>
    <section class="products">
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
    </section>
  </main>
  <script src="script.js"></script>
</body>
</html>
