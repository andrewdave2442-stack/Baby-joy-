
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
  padding: 15px;
  margin: 7px;
  border-radius: 16px;
  font-size: 19px;
}

.animal-button {
  min-width: 110px;
}

button:active {
  background: #ff83b8;
}

#message {
  font-size: 18px;
  color: #ff69a6;
  font-weight: bold;
}

.bubble {
  font-size: 35px;
  animation: float 2s infinite alternate;
}

@keyframes float {
  from { transform: translateY(0); }
  to { transform: translateY(-15px); }
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

<div class="card">
<h2>🐾 Animal Sounds</h2>
<p>Touch an animal to hear its sound!</p>

<div id="animals"></div>

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

const animalSounds = {
  dog: {
    emoji: "🐶",
    name: "Dog",
    sound: "https://sfxmint.com/dl/animal-dog-bark-25.mp3"
  },
  cat: {
    emoji: "🐱",
    name: "Cat",
    sound: "https://sfxmint.com/dl/animal-cat-meow-34.mp3"
  },
  cow: {
    emoji: "🐮",
    name: "Cow",
    sound: "https://sfxmint.com/dl/cow-moo-02.mp3"
  },
  duck: {
    emoji: "🦆",
    name: "Duck",
    sound: "https://sfxmint.com/dl/duck-quack-02.mp3"
  },
  frog: {
    emoji: "🐸",
    name: "Frog",
    sound: "https://sfxmint.com/dl/animal-frog-14.mp3"
  },
  monkey: {
    emoji: "🐵",
    name: "Monkey",
    sound: "https://sfxmint.com/dl/monkey-chatter-01.mp3"
  },
  lion: {
    emoji: "🦁",
    name: "Lion",
    sound: "https://sfxmint.com/dl/lion-roar-01.mp3"
  },
  elephant: {
    emoji: "🐘",
    name: "Elephant",
    sound: "https://sfxmint.com/dl/elephant-trumpet-01.mp3"
  },
  chicken: {
    emoji: "🐔",
    name: "Chicken",
    sound: "https://sfxmint.com/dl/hen-cluck-02.mp3"
  },
  sheep: {
    emoji: "🐑",
    name: "Sheep",
    sound: "https://sfxmint.com/dl/sheep-bleat-02.mp3"
  }
};

const animalsContainer = document.getElementById("animals");

Object.keys(animalSounds).forEach(key => {
  const animal = animalSounds[key];

  const button = document.createElement("button");
  button.className = "animal-button";
  button.textContent = animal.emoji + " " + animal.name;

  button.onclick = () => playAnimal(key);

  animalsContainer.appendChild(button);
});

let currentAudio = null;

function playAnimal(name) {
  const animal = animalSounds[name];

  if (currentAudio) {
    currentAudio.pause();
    currentAudio.currentTime = 0;
  }

  currentAudio = new Audio(animal.sound);
  currentAudio.volume = 0.8;

  document.getElementById("message").textContent =
    "Hello from the " + animal.name + "! ❤️";

  currentAudio.play().catch(() => {
    document.getElementById("message").textContent =
      "Sound unavailable. Please try again.";
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

  alert("Good night, little star! 🌙");
}

</script>

</body>
</html>
