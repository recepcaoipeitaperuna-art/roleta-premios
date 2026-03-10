<!DOCTYPE html><html lang="pt-br">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Roleta de Prêmios</title><link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet"><style>
body{
margin:0;
font-family:'Poppins',sans-serif;
background:linear-gradient(135deg,#6a11cb,#2575fc);
min-height:100vh;
display:flex;
align-items:center;
justify-content:center;
color:white;
}

.container{
text-align:center;
max-width:420px;
padding:30px;
}

h1{
margin-bottom:10px;
font-size:28px;
}

p{
margin-bottom:25px;
opacity:0.9;
}

#wheelBox{
position:relative;
width:340px;
margin:auto;
}

#pointer{
width:0;
height:0;
border-left:18px solid transparent;
border-right:18px solid transparent;
border-bottom:35px solid #ffffff;
position:absolute;
left:50%;
transform:translateX(-50%);
top:-10px;
z-index:10;
}

canvas{
background:white;
border-radius:50%;
box-shadow:0 10px 30px rgba(0,0,0,0.35);
}

button{
margin-top:30px;
padding:16px 45px;
font-size:18px;
border:none;
border-radius:40px;
background:#ffcc00;
color:#333;
font-weight:600;
cursor:pointer;
box-shadow:0 5px 15px rgba(0,0,0,0.2);
transition:0.2s;
}

button:hover{
transform:scale(1.05);
}

#resultado{
margin-top:25px;
font-size:22px;
font-weight:600;
}

footer{
margin-top:25px;
font-size:12px;
opacity:0.7;
}

</style></head><body><div class="container"><h1>🎁 Gire a Roleta de Prêmios</h1>
<p>Tente a sorte e veja qual benefício você ganhou!</p><div id="wheelBox">
<div id="pointer"></div>
<canvas id="wheel" width="340" height="340"></canvas>
</div><button onclick="spin()">Girar agora</button>

<div id="resultado"></div><footer>Você tem apenas 1 chance</footer></div><script>

const prizes=[
"10% de desconto na primeira mensalidade",
"50% de desconto no uniforme",
"Mais uma chance! Gire novamente",
"10% de desconto em todas as mensalidades de uma especialização",
"50% de desconto no curso de injetáveis",
"Não foi dessa vez",
"Uma apostila de qualquer disciplina",
"Curso de injetáveis gratuito"
];

const canvas=document.getElementById("wheel");
const ctx=canvas.getContext("2d");

const slices=prizes.length;
const sliceAngle=2*Math.PI/slices;

function drawWheel(){

for(let i=0;i<slices;i++){

const angle=i*sliceAngle;

ctx.beginPath();
ctx.moveTo(170,170);
ctx.arc(170,170,170,angle,angle+sliceAngle);

ctx.fillStyle=i%2?"#ffcc00":"#ff8c00";
ctx.fill();

ctx.save();
ctx.translate(170,170);
ctx.rotate(angle+sliceAngle/2);
ctx.fillStyle="#333";
ctx.font="bold 14px Poppins";
ctx.textAlign="right";
ctx.fillText(prizes[i],150,5);
ctx.restore();

}

}

let spinning=false;

function spin(){

if(localStorage.getItem("roleta_usada") && !spinning){
alert("Você já girou a roleta.");
return;
}

if(spinning) return;

spinning=true;

const wheel=document.getElementById("wheel");

let extraSpins=Math.floor(Math.random()*5)+6;
let selected=Math.floor(Math.random()*slices);

let finalDeg=(extraSpins*360)+(selected*(360/slices));

wheel.style.transition="transform 5s cubic-bezier(.17,.67,.24,.99)";
wheel.style.transform=`rotate(${finalDeg}deg)`;

setTimeout(()=>{

const prize=prizes[selected];

document.getElementById("resultado").innerHTML="🎉 Você ganhou: <br><b>"+prize+"</b>";

if(prize!=="Mais uma chance! Gire novamente"){
localStorage.setItem("roleta_usada",true);
}

spinning=false;

},5000);

}


drawWheel();

</script></body>
</html>
