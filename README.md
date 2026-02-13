<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Valentine’s Day 💖 my princess</title>

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:-apple-system, BlinkMacSystemFont, sans-serif;
}

body{
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  background:url("background.jpg") no-repeat center center/cover;
  overflow:hidden;
  position:relative;
  color:white;
  text-align:center;
}

/* Dark overlay */
body::after{
  content:"";
  position:absolute;
  inset:0;
  background:linear-gradient(to top, rgba(0,0,0,0.75), rgba(0,0,0,0.45));
  z-index:0;
}

/* Center Card */
.card{
  position:relative;
  z-index:2;
  width:92%;
  max-width:500px;
  padding:50px 35px;
  border-radius:30px;
  background:rgba(255,255,255,0.08);
  backdrop-filter:blur(30px);
  box-shadow:0 30px 80px rgba(0,0,0,0.6);
  display:flex;
  flex-direction:column;
  align-items:center;
  gap:25px;
}

.title{
  font-size:28px;
  font-weight:600;
  letter-spacing:1px;
}

.message{
  font-size:17px;
  line-height:1.7;
  min-height:120px;
  opacity:0.95;
}

button{
  padding:15px 35px;
  border:none;
  border-radius:35px;
  background:linear-gradient(90deg,#ff4d8d,#ff0066);
  color:white;
  font-size:16px;
  cursor:pointer;
  transition:0.3s;
}

button:hover{
  transform:scale(1.08);
  box-shadow:0 0 25px #ff4d8d;
}

/* Rose petals */
.petal{
  position:absolute;
  top:-20px;
  font-size:20px;
  animation:fall linear forwards;
}

@keyframes fall{
  to{
    transform:translateY(110vh) rotate(360deg);
    opacity:0;
  }
}

/* Sparkles */
.sparkle{
  position:absolute;
  width:3px;
  height:3px;
  background:white;
  border-radius:50%;
  animation:twinkle 2s infinite alternate;
}

@keyframes twinkle{
  from{opacity:0.2;}
  to{opacity:1;}
}

/* Firework */
.firework{
  position:absolute;
  width:6px;
  height:6px;
  border-radius:50%;
  animation:explode 1s ease-out forwards;
}

@keyframes explode{
  to{
    transform:translate(var(--x), var(--y));
    opacity:0;
  }
}

/* Final Glow Screen */
#finalScreen{
  position:fixed;
  inset:0;
  display:flex;
  justify-content:center;
  align-items:center;
  background:radial-gradient(circle, rgba(255,0,128,0.4), transparent 70%);
  font-size:42px;
  font-weight:bold;
  opacity:0;
  pointer-events:none;
  transition:1.5s ease;
  z-index:5;
  padding:20px;
}

#finalScreen.show{
  opacity:1;
}

.glow{
  animation:glowText 2s infinite alternate;
}

@keyframes glowText{
  from{
    text-shadow:0 0 10px #ff4d8d, 0 0 20px #ff4d8d;
  }
  to{
    text-shadow:0 0 40px #ff99cc, 0 0 80px #ff0066;
  }
}
</style>
</head>

<body>

<div class="card">
  <div class="title">Happy Valentine’s Day 💘 Ammu</div>
  <div class="message" id="message">
    Tap below to open my heart…
  </div>
  <button onclick="startLove()">Open My Heart 💖</button>
</div>

<div id="finalScreen">
  <div class="glow">
    I LOVE YOU AMMU 💖<br><br>
    Forever & Always ❤️
  </div>
</div>

<script>
/* Sparkles background */
for(let i=0;i<60;i++){
  let s=document.createElement("div");
  s.className="sparkle";
  s.style.top=Math.random()*100+"vh";
  s.style.left=Math.random()*100+"vw";
  s.style.animationDuration=(1+Math.random()*2)+"s";
  document.body.appendChild(s);
}

/* Rose petals */
setInterval(()=>{
  let p=document.createElement("div");
  p.className="petal";
  p.innerHTML="🌹";
  p.style.left=Math.random()*100+"vw";
  p.style.animationDuration=(5+Math.random()*5)+"s";
  document.body.appendChild(p);
  setTimeout(()=>p.remove(),10000);
},500);

/* Typing */
const text=`Ammu 🤍
On this beautiful Valentine’s Day,
you are my greatest blessing.
My peace.
My happiness.
My forever love. 💞`;

let i=0;

function startLove(){
  document.querySelector("button").style.display="none";
  typeText();
}

function typeText(){
  if(i < text.length){
    document.getElementById("message").innerHTML += text.charAt(i);
    i++;
    requestAnimationFrame(typeText);
  } else {
    setTimeout(showFinal,1500);
  }
}

function showFinal(){
  document.getElementById("finalScreen").classList.add("show");

  if(navigator.vibrate){
    navigator.vibrate([200,100,200]);
  }

  createFireworks();
}

function createFireworks(){
  for(let i=0;i<80;i++){
    let f=document.createElement("div");
    f.className="firework";
    f.style.background=`hsl(${Math.random()*360},100%,60%)`;
    f.style.left="50%";
    f.style.top="50%";
    f.style.setProperty("--x",(Math.random()*300-150)+"px");
    f.style.setProperty("--y",(Math.random()*300-150)+"px");
    document.body.appendChild(f);
    setTimeout(()=>f.remove(),1000);
  }
}
</script>

</body>
</html>
</script>

</body>
</html>
ammu-final.html
background.jpg)

![background jpg](https://github.com/user-attachments/assets/718585bb-a81f-48a7-8f8c-fa35a685baaa)


