<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ammu Princess 👑</title>

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:-apple-system, BlinkMacSystemFont, sans-serif;
}

body{
  height:100vh;
  background:url("bg.jpg") center/cover no-repeat;
  display:flex;
  justify-content:center;
  align-items:center;
  overflow:hidden;
  color:white;
  position:relative;
}

/* Dark overlay */
body::after{
  content:"";
  position:absolute;
  width:100%;
  height:100%;
  background:rgba(0,0,0,0.55);
  z-index:0;
}

canvas{
  position:absolute;
  top:0;
  left:0;
  z-index:1;
}

.card{
  position:relative;
  width:90%;
  max-width:420px;
  background:rgba(255,255,255,0.08);
  backdrop-filter:blur(15px);
  border-radius:20px;
  padding:30px;
  text-align:center;
  z-index:2;
  box-shadow:0 20px 60px rgba(0,0,0,0.5);
}

h1{
  margin-bottom:20px;
}

.progress{
  height:4px;
  background:rgba(255,255,255,0.2);
  border-radius:10px;
  margin-bottom:20px;
  overflow:hidden;
}

.bar{
  height:100%;
  width:0%;
  background:linear-gradient(90deg,#ff4d8d,#ffd700);
  transition:0.4s ease;
}

.question{
  font-size:18px;
  min-height:60px;
}

input{
  margin-top:20px;
  width:100%;
  padding:14px;
  border-radius:30px;
  border:none;
  outline:none;
  background:rgba(255,255,255,0.15);
  color:white;
  text-align:center;
}

button{
  margin-top:20px;
  width:100%;
  padding:14px;
  border-radius:30px;
  border:none;
  cursor:pointer;
  background:linear-gradient(90deg,#ff4d8d,#ffd700);
  color:white;
}

#final{
  display:none;
}

#photo{
  width:100%;
  border-radius:15px;
  margin-top:15px;
  opacity:0;
  transform:translateY(15px);
  transition:1s ease;
}

#photo.show{
  opacity:1;
  transform:translateY(0);
}

.message{
  margin-top:15px;
  font-size:16px;
  line-height:1.6;
  min-height:120px;
  white-space:pre-line;
}
</style>
</head>

<body>

<canvas id="canvas"></canvas>

<div class="card">

<h1>Ammu Princess 👑💖</h1>

<div class="progress">
  <div class="bar" id="bar"></div>
</div>

<div id="quiz">
  <div class="question" id="question">
    Who is my princess? 👑
  </div>

  <input type="text" id="answer" placeholder="Type here...">
  <button onclick="next()">Next 💌</button>
</div>

<div id="final">
  <img src="couple.png" id="photo">
  <div class="message" id="msg"></div>
</div>

</div>

<script>
const canvas=document.getElementById("canvas");
const ctx=canvas.getContext("2d");
canvas.width=window.innerWidth;
canvas.height=window.innerHeight;

/* Moon */
let moon = {
  x: canvas.width - 120,
  y: 120,
  radius: 50
};

/* Stars */
let stars=[];
for(let i=0;i<80;i++){
  stars.push({
    x:Math.random()*canvas.width,
    y:Math.random()*canvas.height,
    size:Math.random()*2,
    alpha:Math.random()
  });
}

/* Hearts */
let hearts=[];
for(let i=0;i<25;i++){
  hearts.push({
    x:Math.random()*canvas.width,
    y:Math.random()*canvas.height,
    size:Math.random()*18+10,
    speed:Math.random()*0.5+0.2
  });
}

function animate(){
  ctx.clearRect(0,0,canvas.width,canvas.height);

  /* Draw moon */
  ctx.beginPath();
  ctx.arc(moon.x,moon.y,moon.radius,0,Math.PI*2);
  ctx.fillStyle="rgba(255,255,200,0.8)";
  ctx.shadowBlur=30;
  ctx.shadowColor="rgba(255,255,200,0.8)";
  ctx.fill();
  ctx.shadowBlur=0;

  /* Draw stars */
  stars.forEach(s=>{
    s.alpha += (Math.random()-0.5)*0.05;
    if(s.alpha<0) s.alpha=0;
    if(s.alpha>1) s.alpha=1;
    ctx.fillStyle="rgba(255,255,255,"+s.alpha+")";
    ctx.fillRect(s.x,s.y,s.size,s.size);
  });

  /* Draw floating hearts */
  hearts.forEach(h=>{
    ctx.font=h.size+"px Arial";
    ctx.fillStyle="rgba(255,105,180,0.7)";
    ctx.fillText("❤",h.x,h.y);
    h.y-=h.speed;
    if(h.y<0){
      h.y=canvas.height;
      h.x=Math.random()*canvas.width;
    }
  });

  requestAnimationFrame(animate);
}
animate();

/* Quiz + typing */
let questions=[
"Who is my princess? 👑",
"Who is my forever? 💍",
"Who owns my heart? ❤️"
];

let index=0;

function next(){
  let val=document.getElementById("answer").value.toLowerCase();

  if(val==="ammu"){
    index++;
    document.getElementById("answer").value="";
    document.getElementById("bar").style.width=(index/3*100)+"%";

    if(index<questions.length){
      document.getElementById("question").innerText=questions[index];
    }else{
      showFinal();
    }
  }
}

function showFinal(){
  document.getElementById("quiz").style.display="none";
  document.getElementById("final").style.display="block";
  setTimeout(()=>{
    document.getElementById("photo").classList.add("show");
  },300);
  setTimeout(typeMessage,800);
}

const text=`Ammu Princess… 🤍
You are the only answer to every question in my life.
You are my peace, my forever, my dua written in the stars. ✨
May Allah protect our love always.
I love you endlessly 💖`;

let i=0;

function typeMessage(){
  if(i<text.length){
    document.getElementById("msg").innerHTML += text.charAt(i);
    i++;
    requestAnimationFrame(typeMessage);
  }
}
</script>

</body>
</html>
