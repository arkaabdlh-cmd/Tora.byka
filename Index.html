<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Kasir & Dapur — Sistem Pesanan</title>
<style>
*{box-sizing:border-box}body{margin:0;font-family:Arial,Helvetica,sans-serif;background:#f5f6f8;color:#202124}
header{background:#111827;color:white;padding:18px 22px;display:flex;justify-content:space-between;align-items:center;gap:12px}
header h1{margin:0;font-size:22px}header small{opacity:.75}
.tabs{display:flex;gap:8px;padding:14px;background:white;border-bottom:1px solid #ddd}
button{border:0;border-radius:10px;padding:11px 15px;font-weight:700;cursor:pointer}
.tab{background:#e5e7eb}.tab.active{background:#111827;color:white}
main{max-width:1200px;margin:auto;padding:18px}.panel{display:none}.panel.active{display:block}
.card{background:white;border-radius:16px;padding:18px;box-shadow:0 3px 15px #0000000d;margin-bottom:16px}
.grid{display:grid;grid-template-columns:1fr 1.3fr;gap:16px}.row{display:flex;gap:10px;align-items:end}
label{font-size:13px;font-weight:700;display:block;margin-bottom:6px}
input,select{width:100%;padding:12px;border:1px solid #d1d5db;border-radius:10px;font-size:15px}
.btn{background:#2563eb;color:white}.btn.green{background:#16a34a}.btn.red{background:#dc2626}.btn.gray{background:#6b7280;color:white}
.menu{display:grid;grid-template-columns:repeat(2,1fr);gap:10px}.food{padding:14px;border:1px solid #ddd;border-radius:12px;background:#fff;text-align:left}.food:hover{border-color:#2563eb}
.food b{display:block}.food span{font-size:13px;color:#666}
.cart-item{display:flex;justify-content:space-between;align-items:center;padding:10px 0;border-bottom:1px solid #eee}.qty button{padding:5px 9px}
.total{font-size:20px;font-weight:800;text-align:right;margin-top:14px}
.queue{font-size:32px;font-weight:900;text-align:center;background:#111827;color:#fff;border-radius:14px;padding:15px}
.orders{display:grid;grid-template-columns:repeat(3,1fr);gap:14px}.order{background:white;border-radius:15px;padding:16px;border:2px solid #e5e7eb}.order.new{border-color:#f59e0b}.order.done{border-color:#22c55e;opacity:.8}
.badge{display:inline-block;padding:5px 9px;border-radius:20px;background:#fef3c7;color:#92400e;font-size:12px;font-weight:800}.done .badge{background:#dcfce7;color:#166534}
.order h3{margin:8px 0}.order ul{padding-left:20px}.muted{color:#6b7280;font-size:13px}
.empty{text-align:center;color:#777;padding:35px}.topline{display:flex;justify-content:space-between;align-items:center;gap:10px}
@media(max-width:800px){.grid,.orders{grid-template-columns:1fr}.menu{grid-template-columns:1fr}header{align-items:flex-start;flex-direction:column}}
</style>
</head>
<body>
<header><div><h1>🍜 Kasir & Dapur</h1><small>Sistem pesanan terhubung — gaya restoran cepat saji</small></div><div id="clock"></div></header>
<div class="tabs">
<button class="tab active" onclick="showPanel('cashier',this)">💳 Kasir</button>
<button class="tab" onclick="showPanel('kitchen',this)">👨‍🍳 Dapur</button>
</div>
<main>
<section id="cashier" class="panel active">
<div class="grid">
<div class="card">
<h2>Pesanan Baru</h2>
<label>Nama Pelanggan</label><input id="customer" placeholder="Contoh: Budi">
<h3>Pilih Makanan</h3>
<div class="menu" id="menu"></div>
</div>
<div class="card">
<div class="topline"><h2>Keranjang</h2><button class="btn gray" onclick="clearCart()">Kosongkan</button></div>
<div id="cart"><div class="empty">Belum ada makanan.</div></div>
<div class="total">Total: <span id="total">Rp0</span></div>
<button class="btn green" style="width:100%;margin-top:14px" onclick="sendOrder()">Kirim Pesanan ke Dapur</button>
</div>
</div>
<div class="card">
<div class="topline"><h2>Pesanan Hari Ini</h2><button class="btn red" onclick="resetAll()">Reset Semua</button></div>
<div id="cashierOrders" class="orders"></div>
</div>
</section>

<section id="kitchen" class="panel">
<div class="card">
<div class="topline"><div><h2>👨‍🍳 Layar Dapur</h2><p class="muted">Pesanan dari kasir akan muncul otomatis di sini.</p></div><div><div class="muted">Antrian berikutnya</div><div id="nextQueue" class="queue">#1</div></div></div>
</div>
<div id="kitchenOrders" class="orders"></div>
</section>
</main>
<script>
const menuItems=[
 ["Mie Gaco","Rp12.000"],["Mie Pedas","Rp14.000"],["Mie Keju","Rp16.000"],["Udang Rambutan","Rp10.000"],
 ["Pangsit Goreng","Rp10.000"],["Es Teh","Rp5.000"],["Lemon Tea","Rp7.000"],["Air Mineral","Rp4.000"]
];
let cart=[];
let orders=JSON.parse(localStorage.getItem("orders_v1")||"[]");
let lastQueue=Number(localStorage.getItem("lastQueue_v1")||0);

function rupiah(n){return "Rp"+n.toLocaleString("id-ID")}
function price(s){return Number(s.replace(/[^\d]/g,""))}
function save(){localStorage.setItem("orders_v1",JSON.stringify(orders));localStorage.setItem("lastQueue_v1",lastQueue)}
function renderMenu(){document.getElementById("menu").innerHTML=menuItems.map((m,i)=>`<button class="food" onclick="addItem(${i})"><b>${m[0]}</b><span>${m[1]}</span></button>`).join("")}
function addItem(i){let x=cart.find(a=>a.name===menuItems[i][0]);if(x)x.qty++;else cart.push({name:menuItems[i][0],price:price(menuItems[i][1]),qty:1});renderCart()}
function changeQty(i,d){cart[i].qty+=d;if(cart[i].qty<=0)cart.splice(i,1);renderCart()}
function renderCart(){
 let el=document.getElementById("cart");
 if(!cart.length){el.innerHTML='<div class="empty">Belum ada makanan.</div>';document.getElementById("total").textContent="Rp0";return}
 el.innerHTML=cart.map((x,i)=>`<div class="cart-item"><div><b>${x.name}</b><div class="muted">${rupiah(x.price)} × ${x.qty}</div></div><div class="qty"><button onclick="changeQty(${i},-1)">−</button> <b>${x.qty}</b> <button onclick="changeQty(${i},1)">+</button></div></div>`).join("");
 document.getElementById("total").textContent=rupiah(cart.reduce((a,x)=>a+x.price*x.qty,0))
}
function sendOrder(){
 let name=document.getElementById("customer").value.trim();
 if(!name){alert("Isi nama pelanggan terlebih dahulu.");return}
 if(!cart.length){alert("Pilih minimal satu makanan.");return}
 lastQueue++;
 orders.unshift({id:Date.now(),queue:lastQueue,customer:name,items:cart.map(x=>({...x})),status:"Baru",time:new Date().toLocaleTimeString("id-ID",{hour:"2-digit",minute:"2-digit"})});
 save();cart=[];document.getElementById("customer").value="";renderCart();renderOrders();
 alert("Pesanan berhasil dikirim ke dapur! Nomor antrian #"+lastQueue);
}
function statusOrder(id,status){let o=orders.find(x=>x.id===id);if(o){o.status=status;save();renderOrders()}}
function renderOrders(){
 let make=(kitchen=false)=>orders.length?orders.map(o=>`<div class="order ${o.status==='Selesai'?'done':'new'}">
 <div class="topline"><span class="badge">${o.status}</span><b>#${o.queue}</b></div>
 <h3>${o.customer}</h3><div class="muted">${o.time}</div>
 <ul>${o.items.map(x=>`<li>${x.name} — <b>${x.qty} pcs</b></li>`).join("")}</ul>
 ${kitchen && o.status!=="Selesai"?`<button class="btn green" style="width:100%" onclick="statusOrder(${o.id},'Selesai')">✓ Tandai Selesai</button>`:""}
 ${!kitchen && o.status==="Selesai"?`<div class="muted">Sudah selesai dibuat.</div>`:""}
 </div>`).join(""):'<div class="empty">Belum ada pesanan.</div>';
 document.getElementById("cashierOrders").innerHTML=make(false);
 document.getElementById("kitchenOrders").innerHTML=make(true);
 let pending=orders.filter(x=>x.status!=="Selesai");
 document.getElementById("nextQueue").textContent=pending.length?"#"+pending[pending.length-1].queue:"#"+(lastQueue+1);
}
function clearCart(){cart=[];renderCart()}
function resetAll(){if(confirm("Hapus semua data pesanan?")){orders=[];lastQueue=0;save();renderOrders()}}
function showPanel(id,btn){document.querySelectorAll(".panel").forEach(x=>x.classList.remove("active"));document.getElementById(id).classList.add("active");document.querySelectorAll(".tab").forEach(x=>x.classList.remove("active"));btn.classList.add("active")}
function tick(){document.getElementById("clock").textContent=new Date().toLocaleTimeString("id-ID",{hour:"2-digit",minute:"2-digit",second:"2-digit"})}
window.addEventListener("storage",()=>{orders=JSON.parse(localStorage.getItem("orders_v1")||"[]");lastQueue=Number(localStorage.getItem("lastQueue_v1")||0);renderOrders()});
renderMenu();renderCart();renderOrders();tick();setInterval(tick,1000);setInterval(renderOrders,1000);
</script>
</body>
</html>
