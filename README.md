
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>BabyJoy - Little Fun World</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  text-align: center;
  font-family: Arial, sans-serif;
  background: #fff0f7;
  color: #663399;
}

header {
  background: linear-gradient(135deg, #ff83b8, #b58af5);
  color: white;
  padding: 22px 10px;
  font-size: 29px;
  font-weight: bold;
}

header small {
  font-size: 15px;
}

nav {
  background: white;
  padding: 10px 5px;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 6px;
  position: sticky;
  top: 0;
  z-index: 10;
  box-shadow: 0 2px 8px #ddd;
}

button {
  background: #8b72ee;
  color: white;
  border: none;
  padding: 13px 17px;
  margin: 5px;
  border-radius: 15px;
  font-size: 17px;
  cursor: pointer;
}

button:active {
  transform: scale(.94);
}

nav button {
  font-size: 14px;
  padding: 11px;
}

.card {
  background: white;
  margin: 15px;
  padding: 22px 12px;
  border-radius: 22px;
  box-shadow: 0 3px 10px #ead6e8;
}

h2 {
  color: #a052b5;
}

.section {
  display: none;
}

.section.active {
  display: block;
}

.big-emoji {
  font-size: 85px;
  margin: 15px;
}

.animal-btn {
  font-size: 18px;
  min-width: 115px;
}

#animalDisplay {
  font-size: 90px;
  min-height: 115px;
}

#message {
  font-size: 19px;
  color: #a052b5;
}

#bubbleArea {
  background: #e4f7ff;
  border-radius: 20px;
  height: 320px;
  position: relative;
  overflow: hidden;
  margin: 12px;
}

.bubble {
  position: absolute;
  border-radius: 50%;
  border: 3px solid white;
  background: radial-gradient(circle at 30% 25%,
    white, #91e7ff, #ba9bff);
  box-shadow: 0 3px 12px #9bcde9;
  cursor: pointer;
  animation: floatUp 4s linear forwards;
}

@keyframes floatUp {
  from { transform: translateY(340px); }
  to { transform: translateY(-100px); }
}

#score {
  font-size: 25px;
  font-weight: bold;
}

#learnDisplay {
  font-size: 65px;
  padding: 20px;
}

input[type=range] {
  width: 80%;
  accent-color: #8b72ee;
}

footer {
  padding: 25px;
  color: #a052b5;
}

.hidden {
  display: none;
}
</style>
</head>

<body>

<header>
🌈 BabyJoy 🌈
<br><small>Little Fun World</small>
</header>

<nav>
<button onclick="showSection('home')">🏠 Home</button>
<button onclick="showSection('animals')">🐾 Animals</button>
<button onclick="showSection('games')">🎮 Games</button>
<button onclick="showSection('music')">🎵 Music</button>
<button onclick="showSection('learning')">📚 Learning</button>
<button onclick="showSection('sleep')">🌙 Sleep</button>
</nav>

<!-- HOME -->
<div id="home" class="section active">

<div class="card">
<h2>⭐ Welcome, Little Star!</h2>
<div class="big-emoji">🧸🌈</div>
<p>Welcome to BabyJoy!</p>
<p>Let's play, discover, listen and learn!</p>
</div>

<div class="card">
<h2>What would you like to do?</h2>
<button onclick="showSection('animals')">🐾 Animal World</button>
<button onclick="showSection('games')">🫧 Bubble Game</button>
<button onclick="showSection('music')">🎵 Music World</button>
<button onclick="showSection('learning')">📚 Learning</button>
<button onclick="showSection('sleep')">🌙 Sweet Dreams</button>
</div>

</div>

<!-- ANIMALS -->
<div id="animals" class="section">

<div class="card">
<h2>🐾 Animal World</h2>
<p>Touch an animal to see it and hear its sound!</p>

<div id="animalDisplay">🐶</div>
<p id="message">Choose your favourite animal!</p>

<div>
<button class="animal-btn" onclick="animal('dog')">🐶 Dog</button>
<button class="animal-btn" onclick="animal('cat')">🐱 Cat</button>
<button class="animal-btn" onclick="animal('cow')">🐮 Cow</button>
<button class="animal-btn" onclick="animal('duck')">🦆 Duck</button>
<button class="animal-btn" onclick="animal('lion')">🦁 Lion</button>
<button class="animal-btn" onclick="animal('sheep')">🐑 Sheep</button>
<button class="animal-btn" onclick="animal('frog')">🐸 Frog</button>
<button class="animal-btn" onclick="animal('monkey')">🐵 Monkey</button>
<button class="animal-btn" onclick="animal('elephant')">🐘 Elephant</button>
</div>
</div>

</div>

<!-- GAMES -->
<div id="games" class="section">

<div class="card">
<h2>🫧 Bubble Pop Challenge!</h2>
<p>Pop as many bubbles as you can before time runs out!</p>

<p id="score">⭐ Score: 0</p>
<p id="timer">⏰ Time: 30</p>

<button onclick="startGame()">▶ Start Game</button>
<button onclick="stopGame()">⏹ Stop</button>

<div id="bubbleArea"></div>
<p id="gameMessage">Ready to play?</p>
</div>

</div>

<!-- MUSIC -->
<div id="music" class="section">

<div class="card">
<h2>🎵 Music World</h2>
<div class="big-emoji">🎹🎶</div>
<p>Let's make some beautiful music!</p>

<button onclick="playNote(262)">🎵 Do</button>
<button onclick="playNote(294)">🎵 Re</button>
<button onclick="playNote(330)">🎵 Mi</button>
<button onclick="playNote(349)">🎵 Fa</button>
<button onclick="playNote(392)">🎵 Sol</button>
<button onclick="playNote(440)">🎵 La</button>
<button onclick="playNote(494)">🎵 Ti</button>
<button onclick="playNote(523)">🎵 Do</button>
</div>

<div class="card">
<h2>🎼 Little Melody</h2>
<p>Listen to a cheerful original melody!</p>
<button onclick="playMelody()">▶ Play Melody</button>
<button onclick="stopMusic()">⏹ Stop Music</button>
</div>

</div>

<!-- LEARNING -->
<div id="learning" class="section">

<div class="card">
<h2>📚 Little Learners</h2>
<p>Let's discover letters, numbers and colours!</p>

<div id="learnDisplay">🌈</div>
<p id="learnMessage">Choose something to learn!</p>

<h3>🔤 Alphabet</h3>
<button onclick="learnLetters()">Show Letter</button>

<h3>🔢 Numbers</h3>
<button onclick="learnNumbers()">Show Number</button>

<h3>🎨 Colours</h3>
<button onclick="learnColors()">Show Colour</button>
</div>

</div>

<!-- SLEEP -->
<div id="sleep" class="section">

<div class="card">
<h2>🌙 Sweet Dreams</h2>
<div class="big-emoji">🌙⭐🧸</div>
<p>It's time to relax, little star.</p>
<p>Enjoy a gentle original lullaby.</p>

<button onclick="playLullaby()">🌙 Play Lullaby</button>
<button onclick="stopMusic()">⏹ Stop Lullaby</button>
<p id="sleepMessage">Sweet dreams! ❤️</p>
</div>

</div>

<!-- SOUND SETTINGS -->
<div class="card">
<h2>🔊 Sound Settings</h2>
<p>Adjust the sound volume</p>
<input type="range" min="0" max="100" value="70"
oninput="setVolume(this.value)">
<p id="volumeText">Volume: 70%</p>
<button onclick="stopMusic()">🔇 Stop Sound</button>
</div>

<footer>
🌈 BabyJoy – Little Fun World 🌈
<p>Play • Learn • Discover • Dream</p>
</footer>

<script>

// NAVIGATION

function showSection(section) {
  document.querySelectorAll('.section').forEach(s => {
    s.classList.remove('active');
  });

  document.getElementById(section).classList.add('active');

  if (section !== 'games') stopGame();
}

// SOUND ENGINE

let audioContext;
let masterGain;
let volumeLevel = 0.7;
let activeNodes = [];
let musicTimers = [];
let musicPlaying = false;

function getAudio() {
  if (!audioContext || audioContext.state === "closed") {
    audioContext = new (window.AudioContext || window.webkitAudioContext)();
    masterGain = audioContext.createGain();
    masterGain.gain.value = volumeLevel;
    masterGain.connect(audioContext.destination);
  }

  if (audioContext.state === "suspended") {
    audioContext.resume();
  }

  return audioContext;
}

function setVolume(value) {
  volumeLevel = value / 100;

  if (masterGain) {
    masterGain.gain.setTargetAtTime(
      volumeLevel, audioContext.currentTime, 0.05
    );
  }

  document.getElementById("volumeText").textContent =
    "Volume: " + value + "%";
}

function playTone(frequency, duration = 0.25, type = "sine") {
  const ctx = getAudio();
  const osc = ctx.createOscillator();
  const gain = ctx.createGain();

  osc.type = type;
  osc.frequency.value = frequency;

  gain.gain.setValueAtTime(0.001, ctx.currentTime);
  gain.gain.linearRampToValueAtTime(0.8, ctx.currentTime + 0.03);
  gain.gain.exponentialRampToValueAtTime(
    0.001, ctx.currentTime + duration
  );

  osc.connect(gain);
  gain.connect(masterGain);

  osc.start();
  osc.stop(ctx.currentTime + duration + 0.02);

  activeNodes.push(osc);

  osc.onended = () => {
    activeNodes = activeNodes.filter(n => n !== osc);
  };
}

function playNote(freq) {
  stopMusic();
  playTone(freq, 0.5);
}

// ANIMAL SOUNDS

const animalData = {
  dog: {
    emoji: "🐶",
    message: "Woof! Woof! I'm a dog!",
    notes: [300, 220, 300, 220],
    type: "triangle"
  },
  cat: {
    emoji: "🐱",
    message: "Meow! Meow! I'm a cat!",
    notes: [650, 520, 600],
    type: "sine"
  },
  cow: {
    emoji: "🐮",
    message: "Moooo! I'm a cow!",
    notes: [160, 140, 120],
    type: "sawtooth"
  },
  duck: {
    emoji: "🦆",
    message: "Quack! Quack! I'm a duck!",
    notes: [500, 350, 500, 350],
    type: "square"
  },
  lion: {
    emoji: "🦁",
    message: "Roar! I'm a lion!",
    notes: [130, 100, 150],
    type: "sawtooth"
  },
  sheep: {
    emoji: "🐑",
    message: "Baaa! Baaa! I'm a sheep!",
    notes: [350, 300, 350],
    type: "triangle"
  },
  frog: {
    emoji: "🐸",
    message: "Ribbit! Ribbit! I'm a frog!",
    notes: [250, 350, 250],
    type: "square"
  },
  monkey: {
    emoji: "🐵",
    message: "Ooh! Ooh! I'm a monkey!",
    notes: [450, 600, 450],
    type: "triangle"
  },
  elephant: {
    emoji: "🐘",
    message: "Trumpet! I'm an elephant!",
    notes: [180, 350, 180],
    type: "sawtooth"
  }
};

function animal(name) {
  stopMusic();

  const data = animalData[name];

  document.getElementById("animalDisplay").textContent = data.emoji;
  document.getElementById("message").textContent = data.message;

  const ctx = getAudio();

  data.notes.forEach((freq, i) => {
    const start = ctx.currentTime + i * 0.22;
    const osc = ctx.createOscillator();
    const gain = ctx.createGain();

    osc.type = data.type;
    osc.frequency.value = freq;

    gain.gain.setValueAtTime(0.001, start);
    gain.gain.linearRampToValueAtTime(0.65, start + 0.04);
    gain.gain.exponentialRampToValueAtTime(
      0.001, start + 0.19
    );

    osc.connect(gain);
    gain.connect(masterGain);

    osc.start(start);
    osc.stop(start + 0.21);
    activeNodes.push(osc);
  });
}

// BUBBLE GAME

let gameScore = 0;
let gameTime = 30;
let gameInterval;
let bubbleInterval;
let gameRunning = false;

function startGame() {
  stopGame();

  gameRunning = true;
  gameScore = 0;
  gameTime = 30;

  document.getElementById("score").textContent = "⭐ Score: 0";
  document.getElementById("timer").textContent = "⏰ Time: 30";
  document.getElementById("gameMessage").textContent =
    "Pop the bubbles! 🎉";

  const area = document.getElementById("bubbleArea");
  area.innerHTML = "";

  bubbleInterval = setInterval(createBubble, 650);

  gameInterval = setInterval(() => {
    gameTime--;

    document.getElementById("timer").textContent =
      "⏰ Time: " + gameTime;

    if (gameTime <= 0) {
      stopGame();
      document.getElementById("gameMessage").textContent =
        "🎉 Amazing! Your score is " + gameScore + "!";
    }
  }, 1000);
}

function createBubble() {
  if (!gameRunning) return;

  const area = document.getElementById("bubbleArea");
  const bubble = document.createElement("div");

  const size = 35 + Math.random() * 45;

  bubble.className = "bubble";
  bubble.style.width = size + "px";
  bubble.style.height = size + "px";
  bubble.style.left = Math.random() *
    Math.max(0, area.clientWidth - size) + "px";
  bubble.style.bottom = "-60px";

  bubble.onclick = function() {
    if (!gameRunning) return;

    gameScore++;
    document.getElementById("score").textContent =
      "⭐ Score: " + gameScore;

    playTone(500 + Math.random() * 400, 0.12);
    bubble.remove();
  };

  area.appendChild(bubble);

  setTimeout(() => {
    bubble.remove();
  }, 4000);
}

function stopGame() {
  gameRunning = false;
  clearInterval(gameInterval);
  clearInterval(bubbleInterval);
}

// LEARNING

let letterIndex = 0;
let numberIndex = 1;
let colorIndex = 0;

const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("");
const colors = [
  ["🔴", "Red"],
  ["🔵", "Blue"],
  ["🟡", "Yellow"],
  ["🟢", "Green"],
  ["🟣", "Purple"],
  ["🟠", "Orange"]
];

function learnLetters() {
  const letter = letters[letterIndex];

  document.getElementById("learnDisplay").textContent = letter;
  document.getElementById("learnMessage").textContent =
    "Letter " + letter;

  letterIndex = (letterIndex + 1) % letters.length;
  playTone(400, 0.2);
}

function learnNumbers() {
  document.getElementById("learnDisplay").textContent =
    numberIndex;

  document.getElementById("learnMessage").textContent =
    "Number " + numberIndex;

  numberIndex = numberIndex >= 10 ? 1 : numberIndex + 1;
  playTone(500, 0.2);
}

function learnColors() {
  const color = colors[colorIndex];

  document.getElementById("learnDisplay").textContent = color[0];
  document.getElementById("learnMessage").textContent =
    "This is " + color[1] + "!";

  colorIndex = (colorIndex + 1) % colors.length;
  playTone(600, 0.2);
}

// MUSIC

const melody = [
  262, 330, 392, 330,
  294, 349, 440, 349,
  330, 392, 523, 392,
  349, 440, 523, 440
];

function scheduleMelody(notes, duration, interval) {
  stopMusic();

  musicPlaying = true;

  let index = 0;

  function nextNote() {
    if (!musicPlaying) return;

    if (index >= notes.length) {
      stopMusic();
      return;
    }

    playTone(notes[index], duration);
    index++;

    const timer = setTimeout(nextNote, interval);
    musicTimers.push(timer);
  }

  nextNote();
}

function playMelody() {
  scheduleMelody(melody, 0.35, 400);
}

// ORIGINAL GENTLE LULLABY

const lullaby = [
  392, 349, 330, 294,
  330, 294, 262, 294,
  330, 349, 392, 330,
  294, 262, 294, 262
];

function playLullaby() {
  stopMusic();

  document.getElementById("sleepMessage").textContent =
    "🌙 Enjoy your gentle lullaby... Sweet dreams!";

  musicPlaying = true;

  let index = 0;
  const endTime = Date.now() + 180000;

  function nextLullabyNote() {
    if (!musicPlaying || Date.now() >= endTime) {
      stopMusic();
      return;
    }

    playTone(lullaby[index], 0.85);
    index = (index + 1) % lullaby.length;

    const timer = setTimeout(nextLullabyNote, 1100);
    musicTimers.push(timer);
  }

  nextLullabyNote();
}

// STOP ALL MUSIC AND SOUNDS

function stopMusic() {
  musicPlaying = false;

  musicTimers.forEach(timer => clearTimeout(timer));
  musicTimers = [];

  activeNodes.forEach(node => {
    try {
      node.stop();
    } catch(e) {}
  });

  activeNodes = [];
}

</script>

</body>
</html>
