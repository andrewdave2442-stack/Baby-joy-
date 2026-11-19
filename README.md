
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>BabyJoy - Little Fun World</title>
<style>
*{box-sizing:border-box}
body{margin:0;text-align:center;font-family:Arial,sans-serif;background:#fff0f7;color:#663399}
header{background:#ff83b8;color:white;padding:20px 10px}
h1{margin:5px}
.page{display:none;padding:15px}
#home{display:block}
.menu,.items{display:grid;grid-template-columns:repeat(2,1fr);gap:12px;max-width:650px;margin:15px auto}
button{border:0;border-radius:18px;padding:15px 10px;font-size:18px;background:#ffb6d5;color:#663399;cursor:pointer;box-shadow:0 3px 6px #0002}
button:active{transform:scale(.96)}
.menu button{min-height:95px;font-size:21px;font-weight:bold}
.home-btn{background:#8bdcff;margin:12px;padding:12px 25px}
.animal-card{background:white;padding:10px;border-radius:18px;box-shadow:0 3px 7px #0002}
.animal-card img{width:100%;height:125px;object-fit:cover;border-radius:14px}
.animal-card p{font-size:20px;margin:8px}
#animalDisplay{display:none;background:white;border-radius:20px;padding:15px;margin:15px auto;max-width:400px}
#animalPicture{width:100%;max-height:250px;object-fit:cover;border-radius:15px}
.big-emoji{font-size:65px;margin:10px}
#gameArea{height:350px;background:#e4f7ff;border-radius:18px;position:relative;overflow:hidden;margin:15px auto;max-width:500px}
.balloon{position:absolute;font-size:45px;cursor:pointer;user-select:none}
#bubbleArea{min-height:250px;background:#dff7ff;border-radius:20px;padding:15px}
.bubble{display:inline-block;font-size:45px;padding:8px;cursor:pointer}
input{padding:12px;font-size:20px;border-radius:10px;border:2px solid #ff83b8;width:100px}
.volumeBox{background:white;padding:12px;border-radius:16px;margin:12px auto;max-width:400px}
#volumeSlider{width:85%;accent-color:#ff69a8}
footer{padding:20px;color:#996699}
</style>
</head>
<body>

<header>
<h1>🌹BabyJoy🌹</h1>
<p>Little Fun World 🎈</p>
</header>

<div class="volumeBox">
<strong>🔊 BabyJoy Volume</strong>
<p id="volumeLabel">100%</p>
<input id="volumeSlider" type="range" min="0" max="100" value="100">
</div>

<section id="home" class="page">
<h2>Welcome to BabyJoy! 💖</h2>
<p>Choose what you want to explore.</p>
<div class="menu">
<button onclick="showPage('animals')">🐶 Animals</button>
<button onclick="showPage('learning')">📚 Learning</button>
<button onclick="showPage('games')">🎮 Games</button>
<button onclick="showPage('music')">🎵 Music</button>
<button onclick="showPage('bubbles')">🫧 Bubble Fun</button>
<button onclick="showPage('dreams')">🌙 Sweet Dreams</button>
</div>
</section>

<section id="animals" class="page">
<h2>🐾 Animal World</h2>
<p>Tap an animal to see its picture and hear its sound!</p>
<div class="items" id="animalList"></div>
<div id="animalDisplay">
<h2 id="animalName"></h2>
<img id="animalPicture" src="" alt="Animal picture">
<p id="animalMessage"></p>
<button onclick="repeatAnimal()">🔊 Play Sound Again</button>
</div>
<button class="home-btn" onclick="showPage('home')">🏠 Home</button>
</section>

<section id="learning" class="page">
<h2>📚 Learning Corner</h2>
<h3>🔢 Numbers</h3>
<div class="items">
<button onclick="speak('One')">1️⃣ One</button>
<button onclick="speak('Two')">2️⃣ Two</button>
<button onclick="speak('Three')">3️⃣ Three</button>
<button onclick="speak('Four')">4️⃣ Four</button>
<button onclick="speak('Five')">5️⃣ Five</button>
<button onclick="speak('Six')">6️⃣ Six</button>
<button onclick="speak('Seven')">7️⃣ Seven</button>
<button onclick="speak('Eight')">8️⃣ Eight</button>
<button onclick="speak('Nine')">9️⃣ Nine</button>
<button onclick="speak('Ten')">🔟 Ten</button>
</div>
<h3>🔤 Alphabet</h3>
<div class="items" id="alphabet"></div>
<h3>🎨 Colours</h3>
<div class="items">
<button style="background:red;color:white" onclick="speak('Red')">Red</button>
<button style="background:blue;color:white" onclick="speak('Blue')">Blue</button>
<button style="background:yellow" onclick="speak('Yellow')">Yellow</button>
<button style="background:green;color:white" onclick="speak('Green')">Green</button>
<button style="background:orange" onclick="speak('Orange')">Orange</button>
<button style="background:purple;color:white" onclick="speak('Purple')">Purple</button>
</div>
<h3>🍎 Fruits</h3>
<div class="items">
<button onclick="speak('Apple')">🍎 Apple</button>
<button onclick="speak('Banana')">🍌 Banana</button>
<button onclick="speak('Orange')">🍊 Orange</button>
<button onclick="speak('Grapes')">🍇 Grapes</button>
<button onclick="speak('Watermelon')">🍉 Watermelon</button>
<button onclick="speak('Pineapple')">🍍 Pineapple</button>
</div>
<button class="home-btn" onclick="showPage('home')">🏠 Home</button>
</section>

<section id="games" class="page">
<h2>🎮 Mini Games</h2>
<h3>🎈 Balloon Pop</h3>
<p>Collect 15 points in 30 seconds!</p>
<p>Score: <span id="score">0</span> | Time: <span id="time">30</span></p>
<button onclick="startBalloonGame()">▶ Start Game</button>
<button onclick="stopBalloonGame()">⏹ Stop</button>
<div id="gameArea"></div>
<h3>🎨 Colour Matching</h3>
<p id="colourQuestion"></p>
<div class="items">
<button style="background:red" onclick="checkColour('Red')">Red</button>
<button style="background:blue" onclick="checkColour('Blue')">Blue</button>
<button style="background:green" onclick="checkColour('Green')">Green</button>
<button style="background:yellow" onclick="checkColour('Yellow')">Yellow</button>
</div>
<p id="colourResult"></p>
<h3>🔢 Find the Number</h3>
<p id="numberQuestion"></p>
<div class="items">
<button onclick="checkNumber(3)">3</button>
<button onclick="checkNumber(5)">5</button>
<button onclick="checkNumber(7)">7</button>
<button onclick="checkNumber(9)">9</button>
</div>
<p id="numberResult"></p>
<button class="home-btn" onclick="showPage('home')">🏠 Home</button>
</section>

<section id="music" class="page">
<h2>🎵 Music Corner</h2>
<p>Enjoy a happy little melody!</p>
<button onclick="playMusic()">▶ Play Music</button>
<button onclick="stopMusic()">⏹ Stop Music</button>
<p>Music plays for up to 3 minutes.</p>
<button class="home-btn" onclick="showPage('home')">🏠 Home</button>
</section>

<section id="bubbles" class="page">
<h2>🫧 Bubble Fun</h2>
<p>Tap the bubbles to pop them!</p>
<div id="bubbleArea"></div>
<button onclick="makeBubbles()">✨ More Bubbles</button>
<button class="home-btn" onclick="showPage('home')">🏠 Home</button>
</section>

<section id="dreams" class="page">
<h2>🌙 Sweet Dreams</h2>
<p>Relax with a gentle lullaby.</p>
<div class="big-emoji">🌟🌙⭐</div>
<button onclick="playLullaby()">▶ Play Lullaby</button>
<button onclick="stopLullaby()">⏹ Stop Lullaby</button>
<p id="dreamMessage">Sweet dreams, little one! 💖</p>
<button class="home-btn" onclick="showPage('home')">🏠 Home</button>
</section>

<footer>Made with 💖 for little explorers | BabyJoy</footer>

<script>
/* MASTER VOLUME */
let masterVolume=1;
const volumeSlider=document.getElementById('volumeSlider');

volumeSlider.addEventListener('input',function(){
  masterVolume=Number(this.value)/100;
  document.getElementById('volumeLabel').textContent=this.value+'%';
  if(animalAudio) animalAudio.volume=masterVolume;
  if(musicGain) musicGain.gain.value=0.16*masterVolume;
  if(lullabyGain) lullabyGain.gain.value=0.045*masterVolume;
});

function showPage(id){
  document.querySelectorAll('.page').forEach(p=>p.style.display='none');
  document.getElementById(id).style.display='block';
  stopBalloonGame();
}

const animals=[
{name:'Dog',emoji:'🐶',image:'https://loremflickr.com/320/240/dog',sound:'https://sfxmint.com/dl/animal-dog-bark-25.mp3'},
{name:'Cat',emoji:'🐱',image:'https://loremflickr.com/320/240/cat',sound:'https://sfxmint.com/dl/animal-cat-meow-34.mp3'},
{name:'Cow',emoji:'🐮',image:'https://loremflickr.com/320/240/cow',sound:'https://sfxmint.com/dl/cow-moo-02.mp3'},
{name:'Duck',emoji:'🦆',image:'https://loremflickr.com/320/240/duck',sound:'https://sfxmint.com/dl/duck-quack-02.mp3'},
{name:'Frog',emoji:'🐸',image:'https://loremflickr.com/320/240/frog',sound:'https://sfxmint.com/dl/animal-frog-14.mp3'},
{name:'Monkey',emoji:'🐵',image:'https://loremflickr.com/320/240/monkey',sound:'https://sfxmint.com/dl/monkey-chatter-01.mp3'},
{name:'Lion',emoji:'🦁',image:'https://loremflickr.com/320/240/lion',sound:'https://sfxmint.com/dl/lion-roar-01.mp3'},
{name:'Elephant',emoji:'🐘',image:'https://loremflickr.com/320/240/elephant',sound:'https://sfxmint.com/dl/elephant-trumpet-01.mp3'},
{name:'Chicken',emoji:'🐔',image:'https://loremflickr.com/320/240/chicken',sound:'https://sfxmint.com/dl/hen-cluck-02.mp3'},
{name:'Sheep',emoji:'🐑',image:'https://loremflickr.com/320/240/sheep',sound:'https://sfxmint.com/dl/sheep-bleat-02.mp3'}
];

let currentAnimal=null,animalAudio=null;

function buildAnimals(){
 const list=document.getElementById('animalList');
 animals.forEach(a=>{
  const card=document.createElement('div');
  card.className='animal-card';
  card.innerHTML='<div class="big-emoji">'+a.emoji+'</div><p>'+a.name+'</p>';
  card.onclick=()=>selectAnimal(a);
  list.appendChild(card);
 });
}

function selectAnimal(a){
 currentAnimal=a;
 document.getElementById('animalDisplay').style.display='block';
 document.getElementById('animalName').textContent=a.emoji+' '+a.name;
 document.getElementById('animalPicture').src=a.image;
 document.getElementById('animalMessage').textContent='This is a '+a.name+'!';
 repeatAnimal();
 document.getElementById('animalDisplay').scrollIntoView({behavior:'smooth'});
}

function repeatAnimal(){
 if(!currentAnimal)return;
 if(animalAudio){animalAudio.pause();animalAudio.currentTime=0;}
 animalAudio=new Audio(currentAnimal.sound);
 animalAudio.volume=masterVolume;
 animalAudio.play().catch(()=>{
  document.getElementById('animalMessage').textContent='Sound could not load. Please try again!';
 });
}

function speak(word){
 if(!('speechSynthesis' in window))return;
 speechSynthesis.cancel();
 const msg=new SpeechSynthesisUtterance(word);
 msg.rate=0.8;
 msg.volume=masterVolume;
 speechSynthesis.speak(msg);
}

'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(letter=>{
 const b=document.createElement('button');
 b.textContent=letter;
 b.onclick=()=>speak(letter);
 document.getElementById('alphabet').appendChild(b);
});

/* BALLOON GAME */
let balloonTimer=null,balloonClock=null,gameScore=0,gameTime=30;

function startBalloonGame(){
 stopBalloonGame();
 gameScore=0;gameTime=30;
 updateGameText();
 const area=document.getElementById('gameArea');
 area.innerHTML='';
 balloonTimer=setInterval(()=>{
  const b=document.createElement('span');
  b.className='balloon';
  b.textContent=Math.random()<0.2?'⭐':'🎈';
  b.style.left=Math.random()*85+'%';
  b.style.bottom='-50px';
  area.appendChild(b);
  let h=-50;
  const move=setInterval(()=>{
   h+=4;b.style.bottom=h+'px';
   if(h>350||!b.isConnected){clearInterval(move);b.remove();}
  },60);
  b.onclick=()=>{
   gameScore+=b.textContent==='⭐'?3:1;
   updateGameText();b.remove();clearInterval(move);
   if(gameScore>=15)finishBalloonGame('🎉 You won!');
  };
 },700);
 balloonClock=setInterval(()=>{
  gameTime--;updateGameText();
  if(gameTime<=0)finishBalloonGame('⏰ Time is up!');
 },1000);
}
function updateGameText(){
 document.getElementById('score').textContent=gameScore;
 document.getElementById('time').textContent=gameTime;
}
function finishBalloonGame(message){
 stopBalloonGame();
 document.getElementById('gameArea').innerHTML='<h2>'+message+'</h2>';
}
function stopBalloonGame(){
 clearInterval(balloonTimer);clearInterval(balloonClock);
 balloonTimer=null;balloonClock=null;
}

/* COLOUR GAME */
const colours=['Red','Blue','Green','Yellow'];
let correctColour='Red';
function newColourQuestion(){
 correctColour=colours[Math.floor(Math.random()*colours.length)];
 document.getElementById('colourQuestion').textContent='Find the colour: '+correctColour;
}
function checkColour(answer){
 document.getElementById('colourResult').textContent=answer===correctColour?'🎉 Correct!':'Try again!';
 if(answer===correctColour)newColourQuestion();
}

/* NUMBER GAME */
let correctNumber=5;
function newNumberQuestion(){
 correctNumber=Math.floor(Math.random()*10)+1;
 document.getElementById('numberQuestion').textContent='Find number '+correctNumber;
}
function checkNumber(answer){
 document.getElementById('numberResult').textContent=answer===correctNumber?'🎉 Well done!':'Try again!';
 if(answer===correctNumber)newNumberQuestion();
}

/* BUBBLES */
function makeBubbles(){
 const area=document.getElementById('bubbleArea');
 area.innerHTML='';
 for(let i=0;i<18;i++){
  const b=document.createElement('span');
  b.className='bubble';b.textContent='🫧';
  b.onclick=()=>{b.textContent='✨';setTimeout(()=>b.remove(),300);};
  area.appendChild(b);
 }
}

/* MUSIC */
let musicContext=null,musicGain=null,musicTimer=null,musicEnd=null;
function playMusic(){
 stopMusic();
 const AC=window.AudioContext||window.webkitAudioContext;
 if(!AC)return;
 musicContext=new AC();
 musicGain=musicContext.createGain();
 musicGain.gain.value=0.16*masterVolume;
 musicGain.connect(musicContext.destination);
 const notes=[261.6,293.7,329.6,392,329.6,293.7,261.6,392,440,392,329.6,293.7,261.6,329.6,392,261.6];
 let index=0;
 function note(){
  if(!musicContext)return;
  const osc=musicContext.createOscillator();
  const gain=musicContext.createGain();
  osc.type='sine';
  osc.frequency.value=notes[index++%notes.length];
  gain.gain.setValueAtTime(0.8,musicContext.currentTime);
  gain.gain.exponentialRampToValueAtTime(0.001,musicContext.currentTime+0.35);
  osc.connect(gain);gain.connect(musicGain);
  osc.start();osc.stop(musicContext.currentTime+0.36);
 }
 note();musicTimer=setInterval(note,400);
 musicEnd=setTimeout(stopMusic,180000);
}
function stopMusic(){
 clearInterval(musicTimer);clearTimeout(musicEnd);
 musicTimer=null;musicEnd=null;
 if(musicContext){musicContext.close();musicContext=null;}
 musicGain=null;
}

/* LULLABY */
let lullabyContext=null,lullabyGain=null,lullabyTimer=null,lullabyEnd=null;
function playLullaby(){
 stopLullaby();
 const AC=window.AudioContext||window.webkitAudioContext;
 if(!AC)return;
 lullabyContext=new AC();
 lullabyGain=lullabyContext.createGain();
 lullabyGain.gain.value=0.045*masterVolume;
 lullabyGain.connect(lullabyContext.destination);
 const notes=[261.6,329.6,392,329.6,293.7,349.2,392,261.6];
 let index=0;
 function note(){
  if(!lullabyContext)return;
  const osc=lullabyContext.createOscillator();
  const gain=lullabyContext.createGain();
  osc.type='sine';osc.frequency.value=notes[index++%notes.length];
  gain.gain.setValueAtTime(0.7,lullabyContext.currentTime);
  gain.gain.exponentialRampToValueAtTime(0.001,lullabyContext.currentTime+0.9);
  osc.connect(gain);gain.connect(lullabyGain);
  osc.start();osc.stop(lullabyContext.currentTime+0.9);
 }
 note();lullabyTimer=setInterval(note,1000);
 lullabyEnd=setTimeout(stopLullaby,180000);
 document.getElementById('dreamMessage').textContent='Playing a gentle lullaby... 💖';
}
function stopLullaby(){
 clearInterval(lullabyTimer);clearTimeout(lullabyEnd);
 lullabyTimer=null;lullabyEnd=null;
 if(lullabyContext){lullabyContext.close();lullabyContext=null;}
 lullabyGain=null;
 const msg=document.getElementById('dreamMessage');
 if(msg)msg.textContent='Lullaby stopped. Sweet dreams! 🌙';
}

/* START */
buildAnimals();
makeBubbles();
newColourQuestion();
newNumberQuestion();
</script>
</body>
</html>
