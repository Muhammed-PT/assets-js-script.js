# assets-js-script.js


let products = [
    { id: 1, name: "Black T-Shirt", price: 499, img: "assets/images/p1.jpg" },
    { id: 2, name: "Blue Jeans", price: 1299, img: "assets/images/p2.jpg" },
    { id: 3, name: "Summer Hoodie", price: 899, img: "assets/images/p3.jpg" }
];

// Display Home Products
let homeBox = document.getElementById("homeProducts");
if (homeBox) {
    products.forEach(p => {
        homeBox.innerHTML += `
        <div class="product-card">
            <img src="${p.img}" width="100%">
            <h3>${p.name}</h3>
            <p>₹${p.price}</p>
            <button onclick="addToCart(${p.id})">Add to Cart</button>
        </div>`;
    });
}

// Display Shop Items
let shopBox = document.getElementById("shopProducts");
if (shopBox) {
    products.forEach(p => {
        shopBox.innerHTML += `
        <div class="product-card">
            <img src="${p.img}" width="100%">
            <h3>${p.name}</h3>
            <p>₹${p.price}</p>
            <button onclick="addToCart(${p.id})">Add to Cart</button>
        </div>`;
    });
}

// Cart System
function addToCart(id) {
    let cart = JSON.parse(localStorage.getItem("cart")) || [];
    cart.push(products.find(p => p.id === id));
    localStorage.setItem("cart", JSON.stringify(cart));
    alert("Added to cart!");
}

let cartBox = document.getElementById("cartItems");
if (cartBox) {
    let cart = JSON.parse(localStorage.getItem("cart")) || [];
    cart.forEach(p => {
        cartBox.innerHTML += `
        <div class="product-card">
            <img src="${p.img}" width="100%">
            <h3>${p.name}</h3>
            <p>₹${p.price}</p>
        </div>`;
    });
}
