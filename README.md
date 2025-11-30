# e-commerce-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>E-Commerce Website</title>
  <style>
    * { margin:0; padding:0; box-sizing:border-box; font-family:Arial; }
    body { background:#f5f5f5; }
    header { background:#222; color:#fff; padding:15px 30px; display:flex; justify-content:space-between; align-items:center; position:sticky; top:0; z-index:1000; }
    header h1 { font-size:24px; }
    header .cart-btn { cursor:pointer; font-size:18px; }

    .home-banner { background:#333 url('banner.jpg') center/cover no-repeat; height:280px; display:flex; justify-content:center; align-items:center; color:white; font-size:32px; font-weight:bold; }

    .products { padding:30px; display:grid; grid-template-columns:repeat(auto-fit, minmax(250px,1fr)); gap:20px; }
    .product-card { background:#fff; padding:15px; border-radius:10px; box-shadow:0 2px 8px rgba(0,0,0,0.1); text-align:center; }
    .product-card img { width:100%; height:200px; object-fit:cover; border-radius:8px; cursor:pointer; }
    .product-card h3 { margin:10px 0; }
    .product-card button { margin-top:10px; background:#222; color:white; border:none; padding:10px 15px; cursor:pointer; border-radius:6px; }

    /* Cart Slide */
    #cartPanel { position:fixed; right:-350px; top:0; width:350px; height:100%; background:white; box-shadow:-3px 0 10px rgba(0,0,0,0.3); padding:20px; transition:0.4s; overflow-y:auto; }
    #cartPanel h2 { margin-bottom:15px; }

    .cart-item { padding:10px; background:#eee; border-radius:6px; margin-bottom:10px; }

    /* Product Popup */
    #popup { position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.7); display:none; justify-content:center; align-items:center; }
    #popup .box { background:white; padding:20px; border-radius:10px; width:350px; }
    #popup img { width:100%; border-radius:10px; }
    #popup button { margin-top:10px; padding:10px; background:#222; color:#fff; border:none; cursor:pointer; width:100%; border-radius:6px; }
  </style>
</head>
<body>

<header>
  <h1>My Shop</h1>
  <div class="cart-btn" onclick="toggleCart()">🛒 Cart (<span id="cartCount">0</span>)</div>
</header>

<div class="home-banner">WELCOME TO OUR STORE</div>

<section class="products" id="productList">
  <div class="product-card">
    <img src="product1.jpg" onclick="openPopup('product1.jpg', 'Smart Watch')">
    <h3>Smart Watch</h3>
    <p>₹1999</p>
    <button onclick="addToCart('Smart Watch')">Add to Cart</button>
  </div>

  <div class="product-card">
    <img src="product2.jpg" onclick="openPopup('product2.jpg', 'Headphones')">
    <h3>Headphones</h3>
    <p>₹1499</p>
    <button onclick="addToCart('Headphones')">Add to Cart</button>
  </div>

  <div class="product-card">
    <img src="product3.jpg" onclick="openPopup('product3.jpg', 'Shoes')">
    <h3>Running Shoes</h3>
    <p>₹2499</p>
    <button onclick="addToCart('Shoes')">Add to Cart</button>
  </div>
</section>

<!-- Cart Panel -->
<div id="cartPanel">
  <h2>Your Cart</h2>
  <div id="cartItems"></div>
</div>

<!-- Product Popup -->
<div id="popup">
  <div class="box">
    <img id="popupImg">
    <h3 id="popupName"></h3>
    <button onclick="closePopup()">Close</button>
  </div>
</div>

<script>
  let cart = [];

  function toggleCart(){
    const panel = document.getElementById("cartPanel");
    panel.style.right = panel.style.right === "0px" ? "-350px" : "0px";
  }

  function addToCart(item){
    cart.push(item);
    document.getElementById("cartCount").innerText = cart.length;
    renderCart();
  }

  function renderCart(){
    const c = document.getElementById("cartItems");
    c.innerHTML = "";
    cart.forEach(i => {
      c.innerHTML += `<div class='cart-item'>${i}</div>`;
    });
  }

  function openPopup(img, name){
    document.getElementById("popupImg").src = img;
    document.getElementById("popupName").innerText = name;
    document.getElementById("popup").style.display = "flex";
  }

  function closePopup(){
    document.getElementById("popup").style.display = "none";
  }
</script>

</body>
</html>
