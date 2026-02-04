# Hr-market<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>
    </head>
    <body>
        
    </body>
</html><!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>A&S Cosmetics</title>

<style>
body{
  margin:0;
  font-family:Arial, sans-serif;
  background:linear-gradient(#bfe9e5,#f6f6f6);
}

.hero{
  display:flex;
  flex-wrap:wrap;
  padding:30px;
  align-items:center;
  gap:20px;
}

.hero img{
  width:100%;
  border-radius:20px;
}

h1{font-size:32px}

button{
  padding:12px 25px;
  border:none;
  border-radius:25px;
  cursor:pointer;
  margin:5px;
  font-weight:bold;
}

#buyNow{
  background:orange;
  color:white;
}

.ghost{
  background:#e0e0e0;
}

.hidden{display:none}

#categories{
  text-align:center;
  padding:30px;
}

.category-container{
  display:flex;
  flex-wrap:wrap;
  gap:15px;
  justify-content:center;
}

.category-card{
  width:260px;
  background:white; /* neutral background */
  border-radius:20px;
  padding:15px;
  transition:0.4s;
  cursor:pointer;
  box-shadow:0 2px 6px rgba(0,0,0,0.1);
}

.category-card:hover{
  transform:scale(1.05);
}

.category-card img{
  width:100%;
  border-radius:15px;
}

#products{
  display:grid;
  grid-template-columns:repeat(2,1fr);
  gap:15px;
  padding:20px;
}

.product{
  background:white;
  padding:10px;
  border-radius:15px;
  animation:split 0.5s ease;
}

.product img{
  width:100%;
  border-radius:10px;
}

@keyframes split{
  from{opacity:0; transform:scale(0.2) rotate(-10deg);}
  to{opacity:1; transform:scale(1) rotate(0);}
}

.selection{
  background:#fff;
  margin:20px;
  padding:15px;
  border-radius:15px;
  border:1px solid #ccc;
}

.contact-card{
  background:white;
  padding:25px;
  width:90%;
  margin:30px auto;
  border-radius:20px;
  animation:fade 0.6s ease;
}

@keyframes fade{
  from{opacity:0;transform:translateY(30px)}
  to{opacity:1;transform:translateY(0)}
}
</style>
</head>

<body>

<!-- HERO -->
<section class="hero">
  <div>
    <h1>YOUR BEAUTY IS OUR MISSION</h1>
    <button id="buyNow">Buy Now</button>
    <button class="ghost">Shop All</button>
  </div>
  <img src="https://via.placeholder.com/600x400?text=Cosmetics">
</section>

<!-- CATEGORIES -->
<section id="categories" class="hidden">
  <h2>Shop by category</h2>

  <div class="category-container">

    <div class="category-card" data-category="Skin Care">
      <img src="https://via.placeholder.com/300x200?text=Skin+Care">
      <h3>SKIN CARE</h3>
      <p>Products used to care for the skin</p>
    </div>

    <div class="category-card" data-category="Fragrances">
      <img src="https://via.placeholder.com/300x200?text=Fragrance">
      <h3>FRAGRANCES / PERFUMES</h3>
      <p>Products used to add scent or fragrance</p>
    </div>

    <div class="category-card" data-category="Hair Care">
      <img src="https://via.placeholder.com/300x200?text=Hair+Care">
      <h3>HAIR CARE</h3>
      <p>Products for hair care needs</p>
    </div>

  </div>

  <button id="shopAll">Buy All</button>
</section>

<!-- PRODUCTS -->
<section id="products"></section>

<!-- SELECTIONER -->
<div class="selection hidden" id="selection">
  <h3>Your Selection</h3>
  <ul id="selectionList"></ul>
</div>

<!-- CONTACT -->
<section id="contact" class="hidden">
  <div class="contact-card">
    <h2>Contact Us</h2>
    <p>Email: your@email.com</p>
    <p>Phone: +213 xx xx xx xx</p>
  </div>
</section>

<script>
const buyNow = document.getElementById("buyNow");
const categories = document.getElementById("categories");
const products = document.getElementById("products");
const shopAll = document.getElementById("shopAll");
const contact = document.getElementById("contact");
const selection = document.getElementById("selection");
const selectionList = document.getElementById("selectionList");
let cart = [];

buyNow.onclick = () => {
  categories.classList.remove("hidden");
  categories.scrollIntoView({behavior:"smooth"});
};

document.querySelectorAll(".category-card").forEach(card=>{
  card.onclick = ()=>{
    products.innerHTML="";
    products.classList.remove("hidden");
    const category = card.dataset.category;
    for(let i=1;i<=6;i++){
      let product = document.createElement("div");
      product.className = "product";
      product.innerHTML = `
        <img src="https://via.placeholder.com/300x200?text=${category}+Product+${i}">
        <h4>${category} Product ${i}</h4>
        <p>Price: $${i*10}</p>
        <button>Add to Selection</button>
      `;
      product.querySelector("button").addEventListener("click", () => {
        cart.push(`${category} Product ${i} - $${i*10}`);
        selection.classList.remove("hidden");
        selectionList.innerHTML = cart.map(item=>`<li>${item}</li>`).join("");
      });
      products.appendChild(product);
    }
    products.scrollIntoView({behavior:"smooth"});
  };
});

shopAll.onclick = ()=>{
  contact.classList.remove("hidden");
  contact.scrollIntoView({behavior:"smooth"});
};
</script>

</body>
</html>
