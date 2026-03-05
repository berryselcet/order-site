<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<title>訂單查詢</title>
<style>
body{
font-family: Arial;
background:#f5f5f5;
text-align:center;
padding:40px;
}

.box{
background:white;
padding:30px;
border-radius:10px;
max-width:500px;
margin:auto;
box-shadow:0 0 10px rgba(0,0,0,0.1);
}

button{
padding:10px 20px;
margin:10px;
font-size:16px;
cursor:pointer;
}

input{
padding:10px;
margin:10px;
width:80%;
}
</style>
</head>

<body>

<div class="box" id="step1">

<h2>請輸入訂購人姓名</h2>
<p>如在LINE群，請輸入群名</p>

<input id="nameInput" placeholder="例如：阿妹">

<br>

<button onclick="checkName()">確認</button>

</div>


<div class="box" id="step2" style="display:none">

<h2>訂單資訊</h2>

<div id="orderInfo"></div>

<button onclick="confirmOrder()">確認無誤</button>

<button onclick="reportError()">有錯誤，回報給團主</button>

</div>


<div class="box" id="step3" style="display:none">

<h2>匯款資訊</h2>

<p>銀行：822 中國信託</p>
<p>帳號：123456789012</p>

<p>請輸入匯款後五碼</p>
<input id="last5">

<p>請輸入匯款時間</p>
<input id="time">

<br>

<button onclick="finishPayment()">確認</button>

</div>


<div class="box" id="step4" style="display:none">

<h2>已完成匯款</h2>

<p>稍等團主更新資訊</p>

</div>


<script>

const orders = {

"阿妹":{
items:[
"排球少年立牌 x1",
"徽章 x2"
],
total:450
}

}

function checkName(){

let name = document.getElementById("nameInput").value

if(orders[name]){

document.getElementById("step1").style.display="none"
document.getElementById("step2").style.display="block"

let order = orders[name]

let html = "<h3>"+name+"</h3>"

html+="<p>購買商品：</p>"

order.items.forEach(i=>{
html+="<p>"+i+"</p>"
})

html+="<h3>未匯款金額："+order.total+" 元</h3>"

document.getElementById("orderInfo").innerHTML = html

}else{

alert("查無訂單")

}

}

function confirmOrder(){

document.getElementById("step2").style.display="none"
document.getElementById("step3").style.display="block"

}

function reportError(){

alert("請聯絡團主")

}

function finishPayment(){

document.getElementById("step3").style.display="none"
document.getElementById("step4").style.display="block"

}

</script>

</body>
</html>
