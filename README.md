<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Valentine’s Day 💖 My princess</title>

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
  background:url("background.jpg") no-repeat center center;
  background-size:cover;
  background-attachment:fixed;
  position:relative;
  overflow:hidden;
  color:white;
  text-align:center;
}

/* Romantic dark overlay */
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
  max-width:500px;
  padding:50px 35px;
  border-radius:30px;
  background:rgba(255,255,255,0.08);
  backdrop-filter:blur(30px);
  box-shadow:0 30px 70px rgba(0,0,0,0.7);
  display:flex;
  flex-direction:column;
  align-items:center;
  gap:25px;
}

/* Title */
.title{
  font-size:28px;
  font-weight:600;
  letter-spacing:1px;
}

/* Question */
.question{
  font-size:18px;
  line-height:1.6;
}

/* Buttons */
.btn-group{
  display:flex;
  gap:15px;
}

button{
  padding:12px 28px;
  border:none;
  border-radius:30px;
  font-size:16px;
  cursor:pointer;
  transition:0.3s ease;
}

.yes{
  background:linear-gradient(90deg,#ff4d8d,#ff1a75);
  color:white;
}

.yes:hover{
  transform:scale(1.1);
  box-shadow:0 0 25px #ff4d8d;
}

.no{
  background:white;
  color:#ff1a75;
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
  to{transform:translateY(-110vh) scale(1.6); opacity:0;}
}

/* Final Screen */
#final{
  position:fixed;
  inset:0;
  display:flex;
  justify-content:center;
  align-items:center;
  text-align:center;
  background:radial-gradient(circle, rgba(255,0,128,0.3), transparent 70%);
  font-size:40px;
  font-weight:bold;
  opacity:0;
  pointer-events:none;
  transition:1.5s ease;
  z-index:5;
  padding:20px;
}

#final.show{
  opacity:1;
}

.glow{
  animation:glowText 2s ease-in-out infinite alternate;
}

@keyframes glowText{
  from{
    text-shadow:0 0 15px #ff4d8d, 0 0 30px #ff4d8d;
  }
  to{
    text-shadow:0 0 35px #ff99cc, 0 0 70px #ff4d8d;
  }
}
</style>
</head>

<body>

<div class="card">
  <div class="title">Happy Valentine’s Day 💘 Ammu</div>

  <div class="question">
    Ammu 💞<br><br>
    Will you be my forever love?
  </div>

  <div class="btn-group">
    <button class="yes" onclick="acceptLove()">YES 💖</button>
    <button class="no" onclick="moveNo(this)">NO 😢</button>
  </div>
</div>

<div id="final">
  <div class="glow">
    I LOVE YOU AMMU 💖<br><br>
    Happy Valentine’s Day ❤️
  </div>
</div>

<script>
/* Floating hearts */
setInterval(()=>{
  let h=document.createElement("div");
  h.className="heart";
  h.innerHTML="💖";
  h.style.left=Math.random()*100+"vw";
  h.style.fontSize=(14+Math.random()*20)+"px";
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),8000);
},700);

/* YES button */
function acceptLove(){
  document.getElementById("final").classList.add("show");
}

/* NO button runs away */
function moveNo(btn){
  btn.style.position="absolute";
  btn.style.top=Math.random()*80+"vh";
  btn.style.left=Math.random()*80+"vw";
}
</script>

</body>
</html>

background-size: cover;
background-position: center;
background-attachment: fixed;

![background jpg](https://github.com/user-attachments/assets/718585bb-a81f-48a7-8f8c-fa35a685baaa)


