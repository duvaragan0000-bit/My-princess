<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Valentine’s Day 💖</title>

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
  position:relative;
  overflow:hidden;
  color:white;
  text-align:center;
}

/* Dark romantic overlay */
body::after{
  content:"";
  position:absolute;
  inset:0;
  background:linear-gradient(to top, rgba(0,0,0,0.75), rgba(0,0,0,0.4));
  z-index:0;
}

/* Center Card */
.card{
  position:relative;
  z-index:2;
  width:90%;
  max-width:480px;
  padding:40px 30px;
  border-radius:25px;
  background:rgba(255,255,255,0.08);
  backdrop-filter:blur(25px);
  box-shadow:0 25px 60px rgba(0,0,0,0.6);
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  gap:20px;
}

/* Title */
.title{
  font-size:26px;
  font-weight:600;
  letter-spacing:1px;
}

/* Subtitle */
.subtitle{
  font-size:16px;
  opacity:0.9;
  line-height:1.6;
  min-height:80px;
}

/* Button */
button{
  padding:14px 30px;
  border:none;
  border-radius:30px;
  background:linear-gradient(90deg,#ff4d8d,#ff1a75);
  color:white;
  font-size:16px;
  cursor:pointer;
  transition:0.3s ease;
}

button:hover{
  transform:scale(1.08);
  box-shadow:0 0 20px #ff4d8d;
}

/* Floating hearts */
.heart{
  position:absolute;
  bottom:-20px;
  animation:floatUp 8s linear infinite;
  opacity:0.7;
}

@keyframes floatUp{
  from{transform:translateY(0) scale(1); opacity:0.7;}
  to{transform:translateY(-110vh) scale(1.5); opacity:0;}
}

/* Final Glow Screen */
#finalScreen{
  position:fixed;
  inset:0;
  display:flex;
  justify-content:center;
  align-items:center;
  background:radial-gradient(circle, rgba(255,0,128,0.3), transparent 70%);
  font-size:40px;
  font-weight:bold;
  opacity:0;
  pointer-events:none;
  transition:1.5s ease;
  z-index:5;
  text-align:center;
  padding:20px;
}

#finalScreen.show{
  opacity:1;
}

.glow{
  animation:glowText 2s ease-in-out infinite alternate;
}

@keyframes glowText{
  from{
    text-shadow:0 0 10px #ff4d8d, 0 0 20px #ff4d8d;
  }
  to{
    text-shadow:0 0 30px #ff99cc, 0 0 60px #ff4d8d;
  }
}
</style>
</head>

<body>

<div class="card">
  <div class="title">Happy Valentine’s Day 💘 Ammu</div>

  <div class="subtitle" id="message">
    Click below to reveal something special…
  </div>

  <button onclick="startLove()">Open My Heart 💖</button>
</div>

<div id="finalScreen">
  <div class="glow">
    I LOVE YOU AMMU 💖<br><br>
    Happy Valentine’s Day ❤️
  </div>
</div>

<script>
/* Floating hearts background */
setInterval(()=>{
  let h=document.createElement("div");
  h.className="heart";
  h.innerHTML="💖";
  h.style.left=Math.random()*100+"vw";
  h.style.fontSize=(14+Math.random()*20)+"px";
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),8000);
},700);

/* Typing effect */
const text=`Ammu 🤍
On this beautiful Valentine’s Day,
I just want you to know…
You are my peace,
my happiness,
and my forever love. 💞`;

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
    setTimeout(()=>{
      document.getElementById("finalScreen").classList.add("show");
    },1500);
  }
}
</script>

</body>
</html>>

background-size: cover;
background-position: center;
background-attachment: fixed;

![background jpg](https://github.com/user-attachments/assets/718585bb-a81f-48a7-8f8c-fa35a685baaa)


