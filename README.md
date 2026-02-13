<<!DOCTYPE html>
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
  overflow:hidden;
  display:flex;
  justify-content:center;
  align-items:center;
  background:url("background.jpg") no-repeat center center;
  background-size:cover;   /* full background view */
  position:relative;
  color:white;
}

/* Soft dark overlay */
body::after{
  content:"";
  position:absolute;
  inset:0;
  background:linear-gradient(to top, rgba(0,0,0,0.7), rgba(0,0,0,0.3));
  z-index:0;
}

/* Moon */
.moon{
  position:absolute;
  top:60px;
  right:80px;
  width:120px;
  height:120px;
  border-radius:50%;
  background:radial-gradient(circle,#fff,#ddd 40%,transparent 70%);
  box-shadow:0 0 80px #ffffffaa;
  animation:floatMoon 8s ease-in-out infinite alternate;
  z-index:0;
}

@keyframes floatMoon{
  from{transform:translateY(0);}
  to{transform:translateY(20px);}
}

/* Stars */
.star{
  position:absolute;
  width:2px;
  height:2px;
  background:white;
  border-radius:50%;
  animation:twinkle 3s infinite alternate;
}

@keyframes twinkle{
  from{opacity:0.2;}
  to{opacity:1;}
}

/* Floating hearts */
.heart{
  position:absolute;
  bottom:-20px;
  animation:floatUp 8s linear infinite;
  opacity:0.6;
}

@keyframes floatUp{
  from{transform:translateY(0) scale(1); opacity:0.6;}
  to{transform:translateY(-110vh) scale(1.4); opacity:0;}
}

/* Glass Card */
.card{
  position:relative;
  z-index:2;
  width:90%;
  max-width:420px;
  padding:30px;
  border-radius:20px;
  background:rgba(255,255,255,0.08);
  backdrop-filter:blur(25px);
  box-shadow:0 20px 50px rgba(0,0,0,0.6);
  text-align:center;
  transition:0.6s ease;
}

h1{ margin-bottom:20px; font-weight:500; }

.question{
  margin-bottom:20px;
  min-height:60px;
  font-size:18px;
}

input{
  width:100%;
  padding:14px;
  border:none;
  border-radius:30px;
  outline:none;
  background:rgba(255,255,255,0.1);
  color:white;
  text-align:center;
}

button{
  margin-top:20px;
  width:100%;
  padding:14px;
  border:none;
  border-radius:30px;
  cursor:pointer;
  background:linear-gradient(90deg,#ff4d8d,#8a2be2);
  color:white;
  transition:0.3s;
}

button:hover{ transform:scale(1.05); }

#final{ display:none; }

.message{
  margin-top:20px;
  min-height:120px;
  line-height:1.6;
  white-space:pre-line;
}

/* Proposal Finale */
#proposal{
  position:fixed;
  inset:0;
  display:flex;
  justify-content:center;
  align-items:center;
  font-size:40px;
  font-weight:bold;
  text-align:center;
  background:radial-gradient(circle, rgba(255,0,128,0.3), transparent 70%);
  opacity:0;
  pointer-events:none;
  transition:1.2s ease;
  z-index:5;
}

#proposal.show{
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
    text-shadow:0 0 25px #ff99cc, 0 0 50px #ff4d8d;
  }
}
</style>
</head>

<body>

<div class="moon"></div>
<div id="proposal"><div class="glow">I LOVE YOU AMMU 💖</div></div>

<script>
/* Stars */
for(let i=0;i<70;i++){
  let s=document.createElement("div");
  s.className="star";
  s.style.top=Math.random()*100+"vh";
  s.style.left=Math.random()*100+"vw";
  s.style.animationDuration=(2+Math.random()*3)+"s";
  document.body.appendChild(s);
}

/* Hearts */
setInterval(()=>{
  let h=document.createElement("div");
  h.className="heart";
  h.innerHTML="💖";
  h.style.left=Math.random()*100+"vw";
  h.style.fontSize=(12+Math.random()*20)+"px";
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),8000);
},700);
</script>

<div class="card" id="card">

<h1>Ammu Princess 👑</h1>

<div id="quiz">
  <div class="question" id="question">
    Who is my princess? 👑
  </div>
  <input type="text" id="answer" placeholder="Type here...">
  <button onclick="next()">Next 💌</button>
</div>

<div id="final">
  <div class="message" id="msg"></div>
</div>

</div>

<script>
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
  setTimeout(typeMessage,600);
}

const text=`Ammu Princess… 🤍
You are my peace.
You are my forever.
You are my answered prayer. 🌙✨`;

let i=0;

function typeMessage(){
  if(i < text.length){
    document.getElementById("msg").innerHTML += text.charAt(i);
    i++;
    requestAnimationFrame(typeMessage);
  } else {
    setTimeout(showProposal,1200);
  }
}

function showProposal(){
  document.getElementById("proposal").classList.add("show");
  document.getElementById("card").style.transform="scale(0.9)";
}
</script>

</body>
</html>>>

background-size: cover;
background-position: center;
background-attachment: fixed;

![background jpg](https://github.com/user-attachments/assets/718585bb-a81f-48a7-8f8c-fa35a685baaa)


