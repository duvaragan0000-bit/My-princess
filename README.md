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
  overflow:hidden;
  display:flex;
  justify-content:center;
  align-items:center;
  background:url('https://images.unsplash.com/photo-1503264116251-35a269479413?auto=format&fit=crop&w=1500&q=80') no-repeat center/cover;
  position:relative;
  color:white;
}

/* Dark overlay */
body::after{
  content:"";
  position:absolute;
  inset:0;
  background:linear-gradient(to top, rgba(0,0,0,0.7), rgba(0,0,0,0.3));
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
  box-shadow:0 0 60px #ffffff88;
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

/* Hearts */
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
  box-shadow:0 20px 50px rgba(0,0,0,0.5);
  text-align:center;
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

#photo{
  width:100%;
  border-radius:15px;
  margin-top:15px;
  opacity:0;
  transform:translateY(20px);
  transition:1s ease;
}

#photo.show{
  opacity:1;
  transform:translateY(0);
}

.message{
  margin-top:15px;
  min-height:120px;
  line-height:1.6;
  white-space:pre-line;
}

/* Music Button */
.music-btn{
  position:absolute;
  bottom:20px;
  right:20px;
  background:rgba(255,255,255,0.2);
  border:none;
  padding:10px 15px;
  border-radius:30px;
  color:white;
  cursor:pointer;
  backdrop-filter:blur(10px);
}
</style>
</head>

<body>

<div class="moon"></div>

<button class="music-btn" onclick="toggleMusic()">🎵 Music</button>

<audio id="bgMusic" loop>
  <source src="music.mp3" type="audio/mpeg">
</audio>

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
},800);
</script>

<div class="card">

<h1>Ammu Princess 👑</h1>

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
let music=document.getElementById("bgMusic");
let playing=false;

function toggleMusic(){
  if(!playing){
    music.volume=0;
    music.play();
    let fade=setInterval(()=>{
      if(music.volume<0.9){
        music.volume+=0.05;
      }else{
        clearInterval(fade);
      }
    },200);
    playing=true;
  }else{
    music.pause();
    playing=false;
  }
}

let questions=[
"Who is my princess? 👑",
"Who is my forever? 💍",
"Who owns my heart? ❤️"
];

let index=0;

function next(){
  let val=document.getElementById("answer").value.toLowerCase();
  if(val==="ammu"){
    toggleMusic(); // start music on interaction
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
  setTimeout(()=>{
    document.getElementById("photo").classList.add("show");
  },300);
  setTimeout(typeMessage,800);
}

const text=`Ammu Princess… 🤍
You are the answer to every question in my life.
Like the moon in the night sky,
you light up my darkest days. 🌙✨
May Allah protect our love forever.
I love you endlessly 💖`;

let i=0;

function typeMessage(){
  if(i < text.length){
    document.getElementById("msg").innerHTML += text.charAt(i);
    i++;
    requestAnimationFrame(typeMessage);
  }
</script>

</body>
</html>![background jpg](https://github.com/user-attachments/assets/8e17afde-02dc-45e2-9a7c-281e938442be)
<style>
body{
  height:100vh;
  overflow:hidden;
  display:flex;
  justify-content:center;
  align-items:center;

  /* Your custom image */![background jpg](https://github.com/user-attachments/assets/fbbf56c7-2a9f-4466-9f01-8f3c5b30ed25)

  background: url("background.jpg") no-repeat center center/cover;

  position:relative;
  color:white;
}

/* Dark cinematic overlay */
body::after{
  content:"";
  position:absolute;
  inset:0;
  background:linear-gradient(
    to top,
    rgba(0,0,0,0.8),
    rgba(0,0,0,0.4)
  );
  z-index:0;
}
</style>
![background jpg](https://github.com/user-attachments/assets/193c6af1-d394-4b5b-8373-101e0c4135ff)

