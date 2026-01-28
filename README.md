<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Jhoana ❤️</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&family=Great+Vibes&display=swap');

:root {
  --bg: #ffdde1;
  --accent: #d63384;
  --card: #fff;
}

body {
  margin: 0;
  height: 100vh;
  background: var(--bg);
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: 'Poppins', sans-serif;
  overflow: hidden;
  text-align: center;
}

/* THEMES */
body.dark {
  --bg: #1a1a1a;
  --accent: #ff758f;
  --card: #2a2a2a;
  color: #fff;
}
body.cozy {
  --bg: #fce1c9;
  --accent: #a63d40;
  --card: #fff7ec;
}

.container {
  background: var(--card);
  padding: 30px;
  border-radius: 25px;
  z-index: 10;
  max-width: 350px;
}

/* FLOATING HEARTS */
.heart {
  position: fixed;
  bottom: -20px;
  font-size: 20px;
  animation: floatUp linear infinite;
  opacity: 0.7;
  pointer-events: none;
}
@keyframes floatUp {
  to { transform: translateY(-110vh) rotate(360deg); opacity: 0; }
}

/* ENVELOPE */
.envelope {
  width: 250px;
  height: 160px;
  background: #fff;
  margin: 20px auto;
  position: relative;
  border-radius: 10px;
  cursor: pointer;
}
.flap {
  position: absolute;
  top: 0;
  width: 100%;
  height: 80px;
  background: #f8c8dc;
  clip-path: polygon(0 0, 50% 100%, 100% 0);
  transition: 0.8s;
}
.letter {
  position: absolute;
  top: 40px;
  left: 10px;
  right: 10px;
  background: #fff0f6;
  padding: 15px;
  border-radius: 10px;
  font-family: 'Great Vibes', cursive;
  font-size: 1.5rem;
  opacity: 0;
  transition: 0.8s;
}
.envelope.open .flap { transform: rotateX(180deg); }
.envelope.open .letter { opacity: 1; transform: translateY(-30px); }

/* BUTTONS */
button {
  padding: 12px 25px;
  border: none;
  border-radius: 50px;
  font-size: 1rem;
  cursor: pointer;
  font-weight: 600;
}
#yesBtn { background: #28a745; color: white; }
#noBtn {
  background: #dc3545;
  color: white;
  position: absolute;
}

/* TOOLS */
.top-bar {
  position: fixed;
  top: 15px;
  right: 15px;
  display: flex;
  gap: 10px;
  z-index: 20;
}

/* COUNTDOWN */
#countdown {
  font-size: 1.1rem;
  margin-top: 10px;
  color: var(--accent);
}
</style>
</head>

<body>

<div class="top-bar">
  <button onclick="toggleMusic()">🎵</button>
  <button onclick="setTheme('')">💗</button>
  <button onclick="setTheme('dark')">🌙</button>
  <button onclick="setTheme('cozy')">☕</button>
</div>

<audio id="music" loop>
  <source src="https://cdn.pixabay.com/audio/2022/10/25/audio_7d6c3a5c8c.mp3">
</audio>

<div class="container" id="questionScreen">
  <h1>Jhoana 💖</h1>
  <p>Will you be my Valentine?</p>
  <p id="countdown"></p>

  <div style="margin-top:20px; position:relative; height:60px;">
    <button id="yesBtn">YES!</button>
    <button id="noBtn">No</button>
  </div>
</div>

<div class="container" id="successScreen" style="display:none;">
  <div class="envelope open">
    <div class="flap"></div>
    <div class="letter">
      Jhoana,<br>
      February 17, 2026 💕<br>
      It’s a date.
    </div>
  </div>
</div>

<script>
/* HEARTS */
setInterval(() => {
  const h = document.createElement('div');
  h.className = 'heart';
  h.innerText = '❤️';
  h.style.left = Math.random()*100+'vw';
  h.style.animationDuration = 3 + Math.random()*3 + 's';
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),6000);
},400);

/* NO BUTTON */
const noBtn = document.getElementById('noBtn');
noBtn.addEventListener('mouseenter', move);
noBtn.addEventListener('touchstart', move);
function move(){
  noBtn.style.position='fixed';
  noBtn.style.left=Math.random()*(window.innerWidth-100)+'px';
  noBtn.style.top=Math.random()*(window.innerHeight-60)+'px';
}

/* YES */
document.getElementById('yesBtn').onclick=()=>{
  document.getElementById('questionScreen').style.display='none';
  document.getElementById('successScreen').style.display='block';
};

/* COUNTDOWN */
const target = new Date("Feb 17, 2026 00:00:00");
setInterval(()=>{
  const now=new Date();
  const d=target-now;
  const days=Math.floor(d/(1000*60*60*24));
  document.getElementById('countdown').innerText =
    days>0 ? `${days} days until our date 💕` : `It's today ❤️`;
},1000);

/* MUSIC */
let playing=false;
function toggleMusic(){
  const m=document.getElementById('music');
  playing?m.pause():m.play();
  playing=!playing;
}

/* THEME */
function setTheme(t){
  document.body.className=t;
}
</script>

</body>
</html>
