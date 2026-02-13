<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title> Princess ♕</title>

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:-apple-system, BlinkMacSystemFont, sans-serif;
}

body{
  min-height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  background:url("background.jpg") no-repeat center center;
  background-size:cover;
  background-position:center;
  background-attachment:scroll;
  position:relative;
  color:white;
  overflow:hidden;
}

/* Overlay */
body::after{
  content:"";
  position:absolute;
  inset:0;
  background:linear-gradient(to top, rgba(0,0,0,0.75), rgba(0,0,0,0.35));
  z-index:0;
}

/* Moon */
.moon{
  position:absolute;
  top:60px;
  right:50px;
  width:110px;
  height:110px;
  border-radius:50%;
  background:radial-gradient(circle,#fff,#ddd 40%,transparent 70%);
  box-shadow:0 0 60px #ffffffaa;
  animation:floatMoon 6s ease-in-out infinite alternate;
  z-index:0;
}

@keyframes floatMoon{
  from{transform:translateY(0);}
  to{transform:translateY(15px);}
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
  width:92%;
  max-width:420px;
  padding:30px;
  border-radius:25px;
  background:rgba(255,255,255,0.08);
  backdrop-filter:blur(25px);
  box-shadow:0 20px 50px rgba(0,0,0,0.6);
  text-align:center;
  transition:0.6s ease;
}

h1{
  margin-bottom:20px;
  font-weight:500;
}

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
  font-size:16px;
}

input::placeholder{
  color:#ddd;
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
  font-size:16px;
  transition:0.3s;
}

button:hover{
  transform:scale(1.05);
}

#final{
  display:none;
}

.message{
  margin-top:20px;
  min-height:120px;
  line-height:1.6;
  white-space:pre-line;
  font-size:17px;
}

/* Proposal Screen */
#proposal{
  position:fixed;
  inset:0;
  display:flex;
  justify-content:center;
  align-items:center;
  font-size:34px;
  font-weight:bold;
  text-align:center;
  background:radial-gradient(circle, rgba(255,0,128,0.3), transparent 70%);
  opacity:0;
  pointer-events:none;
  transition:1.2s ease;
  z-index:5;
  padding:20px;
}

#proposal.show{
  opacity:1;
}

.glow{
  animation:glowText 2s infinite alternate;
}

@keyframes glowText{
  from{
    text-shadow:0 0 15px #ff4d8d;
  }
  to{
    text-shadow:0 0 40px #ff99cc;
  }
}
</style>
</head>

<body>

<div class="moon"></div>
<div id="proposal"><div class="glow">I LOVE YOU AMMU 💖</div></div>

<div class="card" id="card">

<h1> Princess 👑</h1>

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

/* Stars */
for(let i=0;i<60;i++){
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
  h.style.fontSize=(12+Math.random()*18)+"px";
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),8000);
},700);

/* Questions */
let questions=[
"Who is my princess? 👑",
"Who is my forever? 💍",
"Who owns my heart? ❤️"
];

let index=0;

function next(){
  let input=document.getElementById("answer");
  let val=input.value.trim().toLowerCase();

  if(val==="ammu"){
    index++;
    input.value="";

    if(index<questions.length){
      document.getElementById("question").innerText=questions[index];
    }else{
      showFinal();
    }
  } else {
    input.value="";
    input.placeholder="Only one correct answer 😉";
  }
}

function showFinal(){
  document.getElementById("quiz").style.display="none";
  document.getElementById("final").style.display="block";
  typeMessage();
}

const text=` Princess… 🤍 nee na ennaku romba pudikum naa edthu varikum unna hurt panirutha romba sorry princess enima appdi panna mattan love you princess 🌙✨`;

let i=0;

function typeMessage(){
  if(i < text.length){
    document.getElementById("msg").innerHTML += text.charAt(i);
    i++;
    setTimeout(typeMessage,30);
  } else {
    setTimeout(showProposal,1000);
  }
}

function showProposal(){
  document.getElementById("proposal").classList.add("show");
  document.getElementById("card").style.transform="scale(0.95)";
}
body{
  min-height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;

  background-image: url("background.jpg");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;       /* fills entire screen */
  background-attachment: scroll; /* important for mobile */

  position:relative;
  overflow:hidden;
  color:white;
}



</body>
</html>

</script>
![background jpg](https://github.com/user-attachments/assets/05e8430d-f392-4707-b51a-3cc724f3dc5c)

body{
  min-height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;

  background-image: url("background.jpg");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;       /* fills entire screen */
  background-attachment: scroll; /* important for mobile */

  position:relative;
  overflow:hidden;
  color:white;
}



</body>
</html>
