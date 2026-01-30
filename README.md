<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>USA Virtual Number Store Pro</title>
<style>
body{font-family:Arial;margin:0;background:#f2f4f7}
header{background:#0088cc;color:#fff;padding:15px;text-align:center;font-size:22px}
nav{display:flex}
nav button{flex:1;padding:12px;border:none;background:#0077aa;color:white;cursor:pointer}
nav button.active{background:#005f88}
main{padding:20px}
.card{background:#fff;padding:15px;border-radius:8px;margin-bottom:12px}
button.action{background:#0088cc;color:white;border:none;padding:10px 16px;border-radius:6px;cursor:pointer}
input,select{width:100%;padding:10px;margin:10px 0;border-radius:6px;border:1px solid #ccc;font-size:16px}
#output{margin-top:20px;font-size:16px}
</style>
</head>
<body>

<header>🇺🇸 USA Virtual Number Store Pro</header>

<nav>
<button class="tab active" data-page="home">Home</button>
<button class="tab" data-page="products">Products</button>
<button class="tab" data-page="order">Order</button>
<button class="tab" data-page="payments">Payments</button>
<button class="tab" data-page="support">Support</button>
</nav>

<main>

<!-- HOME -->
<div id="home" class="page">
<h3>Welcome 👋</h3>
<p>We provide USA virtual numbers & services for business & communication.</p>
<button class="action" onclick="showUser()">Check My Telegram Info</button>
<div id="user"></div>
</div>

<!-- PRODUCTS -->
<div id="products" class="page" style="display:none">
<div class="card">🇺🇸 Google Voice – Business use</div>
<div class="card">🇺🇸 TextNow – App verification</div>
<div class="card">🇺🇸 TextPlus – OTP support</div>
<div class="card">🇺🇸 Sideline – Business line</div>
<div class="card">🇺🇸 OpenPhone – Team use</div>
<div class="card">🇺🇸 Burner – Temporary number</div>
</div>

<!-- ORDER -->
<div id="order" class="page" style="display:none">
<h3>Place Order</h3>
<select id="product">
<option value="">Select Product</option>
<option value="Google Voice">Google Voice</option>
<option value="TextNow">TextNow</option>
<option value="TextPlus">TextPlus</option>
<option value="Sideline">Sideline</option>
<option value="OpenPhone">OpenPhone</option>
<option value="Burner">Burner</option>
</select>
<input id="qty" placeholder="Quantity">
<button class="action" onclick="sendOrder()">Send Order</button>
<div id="output"></div>
</div>

<!-- PAYMENTS -->
<div id="payments" class="page" style="display:none">
<h3>Payment Instructions 💳</h3>
<p>1️⃣ Send payment to PayPal / Wise / Crypto (Contact admin for details)</p>
<p>2️⃣ After payment, submit your transaction ID in the order form.</p>
</div>

<!-- SUPPORT -->
<div id="support" class="page" style="display:none">
<p>📩 Telegram Support</p>
<p>⏱ 24/7 Response</p>
</div>

</main>

<script>
const tg = window.Telegram.WebApp;
tg.expand();

// Tab navigation
document.querySelectorAll('.tab').forEach(btn=>{
btn.onclick=()=>{
document.querySelectorAll('.tab').forEach(b=>b.classList.remove('active'));
btn.classList.add('active');
document.querySelectorAll('.page').forEach(p=>p.style.display='none');
document.getElementById(btn.dataset.page).style.display='block';
};
});

// Show Telegram User Info
function showUser(){
const u=tg.initDataUnsafe.user;
document.getElementById("user").innerHTML=
`<p><b>${u.first_name}</b> (@${u.username || '-'})</p><p>ID: ${u.id}</p>`;
}

// Send Order to Bot/Admin
function sendOrder(){
const p=document.getElementById("product").value;
const q=document.getElementById("qty").value;
if(!p||!q){alert("Fill all fields");return;}
const msg=`ORDER\nProduct: ${p}\nQty: ${q}\nUser: ${tg.initDataUnsafe.user.first_name} (@${tg.initDataUnsafe.user.username || '-'})\nID: ${tg.initDataUnsafe.user.id}`;
tg.sendData(msg);
document.getElementById("output").innerText=" Order sent successfully!";
document.getElementById("qty").value="";
document.getElementById("product").value="";
}
</script>

</body>
</html>
