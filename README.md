
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>BabyJoy - Little Fun World</title>

<style>
body {
  margin: 0;
  text-align: center;
  font-family: Arial, sans-serif;
  background: #fff0f7;
  color: #663399;
}

header {
  background: #ff83b8;
  color: white;
  padding: 25px 10px;
  border-radius: 0 0 25px 25px;
}

header h1 {
  font-size: 30px;
  margin: 5px;
}

header p {
  font-size: 15px;
}

nav {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 8px;
  padding: 12px;
}

nav button {
  background: #ffb6d5;
  border: none;
  padding: 12px;
  border-radius: 15px;
  font-size: 14px;
  color: #663399;
}

section {
  display: none;
  padding: 20px;
}

section.active {
  display: block;
}

.card {
  background: white;
  margin: 12px auto;
  padding: 20px;
  border-radius: 20px;
  max-width: 350px;
  box-shadow: 0 3px 8px #e6b4d0;
}

.big {
  font-size: 55px;
}

button {
  cursor: pointer;
}

.action {
  background: #ff83b8;
  border: none;
  border-radius: 15px;
  padding: 12px 20px;
  color: white;
  font-size: 16px;
}

footer {
  background: #ff83b8;
  color: white;
  padding: 20px;
  margin-top: 30px;
}
</style>
</head>

<body>

<header>
<h1>🌈 BabyJoy 🌈</h1>
<p>Little Fun World</p>
<p>Play • Learn • Discover • Dream</p>
</header>

<nav>
<button onclick="showPage('home')">🏠 Home</button>
<button onclick="showPage('games')">🎮 Games</button>
<button onclick="showPage('learning')">📚 Learning</button>
<button onclick="showPage('music')">🎵 Music</button>
<button onclick="showPage('animals')">🐻 Animals</button>
</nav>

<section id="home" class="active">
<h2>Welcome to BabyJoy! 💖</h2>
<div class="card">
<div class="big">🧸🌈🎈</div>
<h2>Hello Little Explorer!</h2>
<p>A magical world full of fun, music and learning.</p>
</div>
</section>

<section id="games">
<h2>🎮 Game World</h2>
<div class="card">
<div class="big">🎈</div>
<h3>Balloon Fun</h3>
<p>Get ready for exciting games!</p>
</div>
</section>

<section id="learning">
<h2>📚 Learning World</h2>
<div class="card">
<div class="big">🔤</div>
<h3>Learn and Discover</h3>
<p>Letters, numbers, colours and shapes!</p>
</div>
</section>

<section id="music">
<h2>🎵 Music World</h2>
<div class="card">
<div class="big">🎶</div>
<h3>Little Music Corner</h3>
<p>Enjoy fun sounds and melodies!</p>
</div>
</section>

<section id="animals">
<h2>🐻 Animal World</h2>
<div class="card">
<div class="big">🐶🐱🐮</div>
<h3>Meet the Animals!</h3>
<p>Discover wonderful animals and their sounds.</p>
</div>
</section>

<!-- PART 2: BABYJOY ACTIVITIES -->

<div class="card">
<h2>🎈 Balloon Pop Game</h2>
<p id="balloonScore">Score: 0</p>
<div class="big" id="balloon">🎈</div>
<button class="action" onclick="popBalloon()">POP!</button>
</div>

<div class="card">
<h2>🔤 Alphabet Fun</h2>
<div class="big" id="letter">A</div>
<button class="action" onclick="nextLetter()">Next Letter</button>
</div>

<div class="card">
<h2>🔢 Count with BabyJoy</h2>
<div class="big" id="number">1</div>
<button class="action" onclick="nextNumber()">Next Number</button>
</div>

<div class="card">
<h2>🎨 Colour Fun</h2>
<div class="big" id="colour">❤️</div>
<button class="action" onclick="nextColour()">Next Colour</button>
</div>

<div class="card">
<h2>🐾 Animal Sounds</h2>
<div class="big" id="animalPicture">🐶</div>
<h3 id="animalName">Dog</h3>
<button class="action" onclick="nextAnimal()">Next Animal</button>
<button class="action" onclick="animalSound()">🔊 Hear Sound</button>
</div>

<script>
let score = 0;

function popBalloon() {
  score++;
  document.getElementById("balloonScore").innerText =
    "Score: " + score;

  document.getElementById("balloon").innerText =
    ["🎈","🎉","💖","🌟"][Math.floor(Math.random()*4)];
}

let letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
let letterIndex = 0;

function nextLetter() {
  letterIndex = (letterIndex + 1) % letters.length;
  document.getElementById("letter").innerText =
    letters[letterIndex];
}

let numberIndex = 1;

function nextNumber() {
  numberIndex++;
  if(numberIndex > 20) numberIndex = 1;
  document.getElementById("number").innerText =
    numberIndex;
}

let colours = ["❤️","💙","💚","💛","💜","🧡","🤍"];
let colourIndex = 0;

function nextColour() {
  colourIndex = (colourIndex + 1) % colours.length;
  document.getElementById("colour").innerText =
    colours[colourIndex];
}

let animals = [
  ["🐶","Dog","Woof woof!"],
  ["🐱","Cat","Meow meow!"],
  ["🐮","Cow","Moo moo!"],
  ["🐸","Frog","Ribbit ribbit!"],
  ["🦁","Lion","Roar!"],
  ["🐑","Sheep","Baa baa!"],
  ["🐤","Bird","Tweet tweet!"],
  ["🐘","Elephant","Trumpet!"],
  ["🐵","Monkey","Ooh ooh!"]
];

let animalIndex = 0;

function nextAnimal() {
  animalIndex = (animalIndex + 1) % animals.length;
  showAnimal();
}

function showAnimal() {
  document.getElementById("animalPicture").innerText =
    animals[animalIndex][0];

  document.getElementById("animalName").innerText =
    animals[animalIndex][1];
}

function animalSound() {
  if ("speechSynthesis" in window) {
    speechSynthesis.cancel();
    let speech = new SpeechSynthesisUtterance(
      animals[animalIndex][2]
    );
    speech.rate = 0.8;
    speechSynthesis.speak(speech);
  }
}
</script>

<!-- PART 3: MUSIC, SLEEP AND FINAL SETTINGS -->

<section id="music">
<h2>🎵 BabyJoy Music Corner</h2>

<div class="card">
<div class="big">🎶🎹🎼</div>
<h3>Happy Music</h3>
<p>Enjoy your happy music corner!</p>
<button class="action" onclick="playHappyMusic()">
▶ Play Music
</button>
<button class="action" onclick="stopMusic()">
⏹ Stop Music
</button>
</div>

<div class="card">
<h2>🌙 Sleep Time</h2>
<div class="big">🌙⭐💤</div>
<p>Time to relax, little explorer.</p>
<button class="action" onclick="playLullaby()">
🌙 Play Lullaby
</button>
<button class="action" onclick="stopMusic()">
⏹ Stop
</button>
</div>

<div class="card">
<h3>🔊 Volume Control</h3>
<input
type="range"
id="volume"
min="0"
max="1"
step="0.1"
value="0.7"
oninput="changeVolume(this.value)"
>
<p id="volumeText">Volume: 70%</p>
</div>
</section>

<footer>
🌈 BabyJoy – Little Fun World 🌈
<p>Play • Learn • Discover • Dream</p>
<p>Made with 💖 for little explorers</p>
</footer>

<script>
let musicContext = null;
let musicOscillators = [];
let musicTimer = null;
let currentVolume = 0.7;

function stopMusic() {
  if (musicTimer) {
    clearInterval(musicTimer);
    musicTimer = null;
  }

  musicOscillators.forEach(function(osc) {
    try { osc.stop(); } catch(e) {}
  });

  musicOscillators = [];
}

function playTone(frequency, duration) {
  try {
    if (!musicContext) {
      musicContext = new (
        window.AudioContext ||
        window.webkitAudioContext
      )();
    }

    musicContext.resume();

    let osc = musicContext.createOscillator();
    let gain = musicContext.createGain();

    osc.type = "sine";
    osc.frequency.value = frequency;
    gain.gain.value = currentVolume * 0.08;

    osc.connect(gain);
    gain.connect(musicContext.destination);

    osc.start();
    osc.stop(musicContext.currentTime + duration);

    musicOscillators.push(osc);
  } catch(e) {}
}

function playHappyMusic() {
  stopMusic();

  let notes = [262,294,330,349,392,349,330,294];
  let i = 0;

  musicTimer = setInterval(function() {
    playTone(notes[i], 0.35);
    i = (i + 1) % notes.length;
  }, 450);
}

function playLullaby() {
  stopMusic();

  let notes = [392,349,330,294,262,294,330,262];
  let i = 0;

  musicTimer = setInterval(function() {
    playTone(notes[i], 1.1);
    i = (i + 1) % notes.length;
  }, 1300);
}

function changeVolume(value) {
  currentVolume = Number(value);

  document.getElementById("volumeText").innerText =
    "Volume: " + Math.round(currentVolume * 100) + "%";
}

function showPage(page) {
  document.querySelectorAll("section").forEach(function(section) {
    section.classList.remove("active");
  });

  let selected = document.getElementById(page);

  if (selected) {
    selected.classList.add("active");
  }

  stopMusic();
  window.scrollTo(0,0);
}
</script>

</body>
</html>
