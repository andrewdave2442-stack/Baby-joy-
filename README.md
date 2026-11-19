

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
  background: #ff83b8;
  color: white;
  padding: 25px 10px;
  font-size: 30px;
  font-weight: bold;
}

header small {
  font-size: 17px;
}

.card {
  background: white;
  margin: 15px;
  padding: 22px 12px;
  border-radius: 22px;
  box-shadow: 0 3px 10px #eac5db;
}

h2 {
  color: #9b59b6;
}

button {
  background: #8b72ee;
  color: white;
  border: none;
  padding: 15px;
  margin: 7px;
  border-radius: 16px;
  font-size: 19px;
  cursor: pointer;
}

button:active {
  background: #ff83b8;
  transform: scale(0.95);
}

.animal-button {
  min-width: 115px;
}

#message {
  font-size: 18px;
  color: #ff69a6;
  font-weight: bold;
}

.bubble {
  display: inline-block;
  font-size: 35px;
  animation: float 2s infinite alternate;
}

@keyframes float {
  from { transform: translateY(0); }
  to { transform: translateY(-15px); }
}

footer {
  padding: 20px;
  color: #9b59b6;
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

<div class="card">
<h2>🐾 Animal Sounds</h2>
<p>Touch an animal to hear its sound!</p>

<button class="animal-button" onclick="playAnimal('dog')">
🐶 Dog
</button>

<button class="animal-button" onclick="playAnimal('cat')">
🐱 Cat
</button>

<button class="animal-button" onclick="playAnimal('cow')">
🐮 Cow
</button>

<button class="animal-button" onclick="playAnimal('duck')">
🦆 Duck
</button>

<button class="animal-button" onclick="playAnimal('frog')">
🐸 Frog
</button>

<p id="message">Tap an animal! ❤️</p>
<button onclick="stopSound()">🔇 Stop Sound</button>
</div>

<div class="card">
<h2>🫧 Bubble Fun</h2>
<div class="bubble">🫧 🫧 🫧</div>
<p>Pop and play, little star!</p>
<button onclick="popBubbles()">Pop bubbles!</button>
<p id="bubbleMessage"></p>
</div>

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

// REAL ANIMAL AUDIO FILES

const animalSounds = {
  dog: {
    name: "Dog",
    sound: "https://sfxmint.com/dl/animal-dog-bark-25.mp3"
  },

  cat: {
    name: "Cat",
    sound: "https://sfxmint.com/dl/animal-cat-meow-34.mp3"
  },

  cow: {
    name: "Cow",
    sound: "https://sfxmint.com/dl/cow-moo-02.mp3"
  },

  duck: {
    name: "Duck",
    sound: "https://sfxmint.com/dl/duck-quack-02.mp3"
  },

  frog: {
    name: "Frog",
    sound: "https://sfxmint.com/dl/animal-frog-14.mp3"
  }
};

let currentAudio = null;

function playAnimal(name) {

  if (!animalSounds[name]) return;

  if (currentAudio) {
    currentAudio.pause();
    currentAudio.currentTime = 0;
  }

  currentAudio = new Audio(animalSounds[name].sound);
  currentAudio.volume = 1;

  document.getElementById("message").textContent =
    "Hello from the " + animalSounds[name].name + "! ❤️";

  currentAudio.play().catch(() => {
    document.getElementById("message").textContent =
      "Sound unavailable. Please check your internet connection.";
  });
}

function stopSound() {
  if (currentAudio) {
    currentAudio.pause();
    currentAudio.currentTime = 0;
  }

  document.getElementById("message").textContent =
    "Sound stopped! ❤️";
}

function popBubbles() {
  document.getElementById("bubbleMessage").textContent =
    "POP! POP! POP! 🫧✨";
}

function dreamTime() {
  stopSound();

  document.getElementById("message").textContent =
    "Sweet dreams, little star! 🌙";

  alert("Good night, little star! ⭐");
}

</script>

</body>
</html>
