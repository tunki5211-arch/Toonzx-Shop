<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ADMIN PANEL</title>

<style>
body{
  background:#020216;
  color:#00ffff;
  font-family:Consolas, monospace;
}
header{
  padding:15px;
  text-align:center;
  box-shadow:0 0 15px #00ffff;
}
.order{
  margin:20px;
  padding:15px;
  border:1px solid #00ffff;
}
.order img{
  width:100%;
  max-width:300px;
}
button{
  margin-top:10px;
  padding:8px 15px;
  background:#ff00ff;
  border:none;
  font-weight:bold;
}
</style>
</head>

<body>

<header>
  <h2>🔐 ADMIN PANEL</h2>
</header>

<div id="orders"></div>

<script>
let orders = JSON.parse(localStorage.getItem("orders") || "[]");
const box = document.getElementById("orders");

if(orders.length === 0){
  box.innerHTML = "<p style='padding:20px'>ยังไม่มีออเดอร์</p>";
}

orders.forEach((o,i)=>{
  box.innerHTML += `
    <div class="order">
      <p>📦 ${o.item}</p>
      <p>🕒 ${o.time}</p>
      <img src="${o.slip}">
      <br>
      <button onclick="deleteOrder(${i})">ลบ</button>
    </div>
  `;
});

function deleteOrder(i){
  orders.splice(i,1);
  localStorage.setItem("orders", JSON.stringify(orders));
  location.reload();
}
</script>

</body>
</html>
