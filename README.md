
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>BabyJoy - Little Fun World</title>

<style>
* { box-sizing: border-box; }

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
  font-size: 30px;
  font-weight: bold;
}

header small { font-size: 17px; }

.card {
  background: white;
  margin: 15px;
  padding: 22px 12px;
  border-radius: 22px;
  box-shadow: 0 3px 10px #eac5db;
}

h2 { color: #9b59b6; }

button {
  background: #8b72ee;
  color: white;
  border: none;
  padding: 14px;
  margin: 6px;
  border-radius: 15px;
  font-size: 18px;
  cursor: pointer;
}

button:active {
  transform: scale(.95);
  background: #ff83b8;
}

.animal-button {
  min-width: 105px;
}

.number-button {
  min-width: 55px;
  font-size: 23px;
}

.letter-button {
  min-width: 43px;
  font-size: 20px;
}

.color-button {
  min-width: 90px;
  min-height: 65px;
}

.fruit {
  font-size: 55px;
  display: inline-block;
  margin: 8px;
}

#message, #learningMessage {
  font-weight: bold;
  color: #ff69a6;
  font-size: 18px;
  min-height: 25px;
}

.bubble {
  font-size: 38px;
  animation: float 2s infinite alternate;
}

@keyframes float {
  from { transform: translateY(0); }
  to { transform: translateY(-12px); }
}

footer {
  padding: 20px;
}
</style>
</head>

<body>

<header>
 🌹 BabyJoy 🌹
<br>
<small>Little Fun World</small>
</header>

<div class="card">
<h2>⭐ Welcome, Little Star!</h2>
<p>Let's play, explore and learn!</p>
🐻 🐰 🐼 🦋
</div>

<!-- ANIMAL SOUNDS -->

<div class="card">
<h2>🐾 Animal Sounds</h2>
<p>Touch an animal to hear its sound!</p>
<div id="animals"></div>
<p id="message">Tap an animal! ❤️</p>
<button onclick="stopSound()">🔇 Stop Sound</button>
</div>

<!-- NUMBERS -->

<div class="card">
<h2>🔢 Learn Numbers</h2>
<p>Tap a number to hear its name!</p>
<div id="numbers"></div>
<p id="numberMessage">Let's count together! ⭐</p>
</div>

<!-- ALPHABET -->

<div class="card">
<h2>🔤 Learn the Alphabet</h2>
<p>Tap a letter to hear it!</p>
<div id="letters"></div>
<p id="letterMessage">A B C, come learn with me!</p>
</div>

<!-- COLOURS -->

<div class="card">
<h2>🎨 Colour World</h2>
<p>Tap a colour to learn its name!</p>
<div id="colors"></div>
<p id="colorMessage">Colours are beautiful! 🌈</p>
</div>

<!-- FRUITS -->

<div class="card">
<h2>🍎 Fruit Garden</h2>
<p>Tap a fruit to learn its name!</p>
<div id="fruits"></div>
<p id="fruitMessage">Yummy fruits! ❤️</p>
</div>

<!-- MUSIC -->

<div class="card">
<h2>🎵 Music Corner</h2>
<p>Enjoy a happy little tune!</p>
<button onclick="playMusic()">🎶 Play Happy Tune</button>
<button onclick="stopMusic()">⏹ Stop Music</button>
</div>

<!-- BUBBLES -->

<div class="card">
<h2>🫧 Bubble Fun</h2>
<div class="bubble">🫧 🫧 🫧</div>
<p>Pop and play, little star!</p>
<button onclick="popBubbles()">Pop bubbles!</button>
<p id="bubbleMessage"></p>
</div>

<!-- DREAMS -->

<div class="card">
<h2>🌙 Sweet Dreams</h2>
<p>Time to relax, little star!</p>
🌙 ⭐ 💤
<br>
<button onclick="dreamTime()">Sweet Dreams</button>
</div>

<footer>
⭐ BabyJoy - Little Fun World ⭐
<p>Made with love for little learners ❤️</p>
</footer>

<script>

// SPEECH SUPPORT

function speak(words) {
  if (!("speechSynthesis" in window)) {
    alert("Speech is not supported on this browser.");
    return;
  }

  speechSynthesis.cancel();

  const message = new SpeechSynthesisUtterance(words);
  message.lang = "en-GB";
  message.rate = 0.8;
  message.pitch = 1.2;

  speechSynthesis.speak(message);
}

// ANIMAL SOUNDS

const animalSounds = {
  dog: ["🐶", "Dog", "https://sfxmint.com/dl/animal-dog-bark-25.mp3"],
  cat: ["🐱", "Cat", "https://sfxmint.com/dl/animal-cat-meow-34.mp3"],
  cow: ["🐮", "Cow", "https://sfxmint.com/dl/cow-moo-02.mp3"],
  duck: ["🦆", "Duck", "https://sfxmint.com/dl/duck-quack-02.mp3"],
  frog: ["🐸", "Frog", "https://sfxmint.com/dl/animal-frog-14.mp3"],
  monkey: ["🐵", "Monkey", "https://sfxmint.com/dl/monkey-chatter-01.mp3"],
  lion: ["🦁", "Lion", "https://sfxmint.com/dl/lion-roar-01.mp3"],
  elephant: ["🐘", "Elephant", "https://sfxmint.com/dl/elephant-trumpet-01.mp3"],
  chicken: ["🐔", "Chicken", "https://sfxmint.com/dl/hen-cluck-02.mp3"],
  sheep: ["🐑", "Sheep", "https://sfxmint.com/dl/sheep-bleat-02.mp3"]
};

let currentAudio = null;

Object.keys(animalSounds).forEach(key => {
  const a = animalSounds[key];
  const button = document.createElement("button");

  button.className = "animal-button";
  button.textContent = a[0] + " " + a[1];
  button.onclick = () => playAnimal(key);

  document.getElementById("animals").appendChild(button);
});

function playAnimal(name) {
  stopSound();

  const a = animalSounds[name];
  currentAudio = new Audio(a[2]);
  currentAudio.volume = 0.8;

  document.getElementById("message").textContent =
    "Hello from the " + a[1] + "! ❤️";

  currentAudio.play().catch(() => {
    document.getElementById("message").textContent =
      "Sound unavailable. Please try again.";
  });
}

function stopSound() {
  if (currentAudio) {
    currentAudio.pause();
    currentAudio.currentTime = 0;
    currentAudio = null;
  }
}

// NUMBERS

const numbers = [
  "One", "Two", "Three", "Four", "Five",
  "Six", "Seven", "Eight", "Nine", "Ten"
];

numbers.forEach((word, i) => {
  const button = document.createElement("button");
  button.className = "number-button";
  button.textContent = i + 1;

  button.onclick = () => {
    document.getElementById("numberMessage").textContent =
      i + 1 + " - " + word + "! ⭐";
    speak(word);
  };

  document.getElementById("numbers").appendChild(button);
});

// ALPHABET

"ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("").forEach(letter => {
  const button = document.createElement("button");
  button.className = "letter-button";
  button.textContent = letter;

  button.onclick = () => {
    document.getElementById("letterMessage").textContent =
      "Letter " + letter + "! ❤️";
    speak(letter);
  };

  document.getElementById("letters").appendChild(button);
});

// COLOURS

const colors = [
  ["Red", "#ff3333"],
  ["Blue", "#3388ff"],
  ["Yellow", "#ffd633"],
  ["Green", "#36bb65"],
  ["Pink", "#ff83b8"],
  ["Purple", "#9864dd"],
  ["Orange", "#ff9933"],
  ["Brown", "#996633"],
  ["Black", "#333333"],
  ["White", "#eeeeee"]
];

colors.forEach(c => {
  const button = document.createElement("button");
  button.className = "color-button";
  button.textContent = c[0];
  button.style.background = c[1];

  if (c[0] === "Yellow" || c[0] === "White") {
    button.style.color = "#663399";
  }

  button.onclick = () => {
    document.getElementById("colorMessage").textContent =
      "This colour is " + c[0] + "! 🎨";
    speak(c[0]);
  };

  document.getElementById("colors").appendChild(button);
});

// FRUITS

const fruits = [
  ["🍎", "Apple"],
  ["🍌", "Banana"],
  ["🍊", "Orange"],
  ["🍇", "Grapes"],
  ["🍓", "Strawberry"],
  ["🍍", "Pineapple"],
  ["🥭", "Mango"],
  ["🍉", "Watermelon"],
  ["🍐", "Pear"],
  ["🍒", "Cherries"]
];

fruits.forEach(f => {
  const button = document.createElement("button");
  button.innerHTML =
    '<span class="fruit">' + f[0] + '</span><br>' + f[1];

  button.onclick = () => {
    document.getElementById("fruitMessage").textContent =
      f[1] + "! Yummy! 🍓";
    speak(f[1]);
  };

  document.getElementById("fruits").appendChild(button);
});

// HAPPY ORIGINAL TUNE

let musicTimer = null;
let musicAudio = null;

function playMusic() {
  stopMusic();

  const AudioContextClass =
    window.AudioContext || window.webkitAudioContext;

  if (!AudioContextClass) {
    alert("Music is not supported on this browser.");
    return;
  }

  const ctx = new AudioContextClass();

  const melody = [
    523.25, 587.33, 659.25, 783.99,
    659.25, 587.33, 523.25, 392
  ];

  let index = 0;

  function note() {
    if (index >= melody.length) {
      ctx.close();
      musicTimer = null;
      return;
    }

    const osc = ctx.createOscillator();
    const gain = ctx.createGain();

    osc.type = "sine";
    osc.frequency.value = melody[index];

    gain.gain.setValueAtTime(0.0001, ctx.currentTime);
    gain.gain.linearRampToValueAtTime(
      0.12, ctx.currentTime + 0.04
    );
    gain.gain.exponentialRampToValueAtTime(
      0.0001, ctx.currentTime + 0.3
    );

    osc.connect(gain);
    gain.connect(ctx.destination);

    osc.start();
    osc.stop(ctx.currentTime + 0.32);

    index++;
    musicTimer = setTimeout(note, 380);
  }

  ctx.resume().then(note);
}

function stopMusic() {
  if (musicTimer) {
    clearTimeout(musicTimer);
    musicTimer = null;
  }
}

// BUBBLE FUN

function popBubbles() {
  document.getElementById("bubbleMessage").textContent =
    "POP! POP! POP! 🫧✨";
}

// SWEET DREAMS

function dreamTime() {
  stopSound();
  stopMusic();
  speechSynthesis.cancel();
  alert("Good night, little star! 🌙");
}

</script>

</body>
</html>
