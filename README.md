
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
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
}

header h1 {
  margin: 0;
  font-size: 30px;
}

section {
  background: white;
  margin: 18px 12px;
  padding: 20px 12px;
  border-radius: 20px;
  box-shadow: 0 4px 10px #e8c5d8;
}

h2 {
  color: #e7549b;
}

button {
  border: none;
  border-radius: 15px;
  padding: 13px 17px;
  margin: 6px;
  font-size: 17px;
  background: #ff83b8;
  color: white;
  cursor: pointer;
}

button:active {
  transform: scale(0.95);
}

.animal {
  background: #a879e8;
}

.learning {
  background: #55b9d6;
}

.stop {
  background: #777;
}

#bubbleArea {
  position: relative;
  height: 180px;
  overflow: hidden;
  background: #e6f7ff;
  border-radius: 15px;
  margin-top: 12px;
}

.bubble {
  position: absolute;
  bottom: -50px;
  border-radius: 50%;
  background: #ff9ed0;
  opacity: 0.75;
  animation: floatUp 4s linear forwards;
}

@keyframes floatUp {
  from {
    transform: translateY(0);
  }
  to {
    transform: translateY(-250px);
  }
}

footer {
  padding: 20px;
  background: #ff83b8;
  color: white;
  margin-top: 20px;
}
</style>
</head>

<body>

<header>
  <h1>🌹 BabyJoy 🌹</h1>
  <h2 style="color:white;">Little Fun World</h2>
  <p>Play, learn and have fun!</p>
</header>

<section>
  <h2>⭐ Welcome, Little Star!</h2>
  <p>Let's play and learn!</p>
</section>

<section>
  <h2>🐾 Animal Sounds</h2>
  <p>Tap an animal to hear its sound!</p>

  <button class="animal" onclick="playAnimal('dog')">🐶 Dog</button>
  <button class="animal" onclick="playAnimal('cat')">🐱 Cat</button>
  <button class="animal" onclick="playAnimal('cow')">🐮 Cow</button>
  <button class="animal" onclick="playAnimal('duck')">🦆 Duck</button>
  <button class="animal" onclick="playAnimal('frog')">🐸 Frog</button>
  <button class="animal" onclick="playAnimal('monkey')">🐵 Monkey</button>
  <button class="animal" onclick="playAnimal('lion')">🦁 Lion</button>
  <button class="animal" onclick="playAnimal('elephant')">🐘 Elephant</button>
  <button class="animal" onclick="playAnimal('chicken')">🐔 Chicken</button>
  <button class="animal" onclick="playAnimal('sheep')">🐑 Sheep</button>
</section>

<section>
  <h2>🔢 Learn Numbers</h2>
  <p>Tap a number and listen!</p>
  <div id="numbers"></div>
</section>

<section>
  <h2>🔤 Learn the Alphabet</h2>
  <p>Tap a letter and listen!</p>
  <div id="alphabet"></div>
</section>

<section>
  <h2>🎨 Learn Colours</h2>
  <p>Discover beautiful colours!</p>
  <div id="colours"></div>
</section>

<section>
  <h2>🍎 Learn Fruits</h2>
  <p>Discover yummy fruits!</p>
  <div id="fruits"></div>
</section>

<section>
  <h2>🎵 Music Corner</h2>
  <p>Enjoy a happy BabyJoy tune!</p>
  <button onclick="playMusic()">▶️ Play Music</button>
  <button class="stop" onclick="stopMusic()">⏹ Stop Music</button>
  <p id="musicMessage">Music plays for up to 3 minutes.</p>
</section>

<section>
  <h2>🫧 Bubble Fun</h2>
  <p>Pop and play with the bubbles!</p>
  <button onclick="makeBubbles()">🫧 Make Bubbles</button>
  <div id="bubbleArea" onclick="makeBubbles()"></div>
</section>

<section>
  <h2>🌙 Sweet Dreams</h2>
  <p>Time to relax, little star!</p>
  <button onclick="dreamTime()">🌙 Sleep Time</button>
</section>

<footer>
  ⭐ Have fun with BabyJoy! ⭐
  <p>Little Fun World 🌈</p>
</footer>

<script>

// ANIMAL SOUNDS

const animalSounds = {
  dog: "https://sfxmint.com/dl/animal-dog-bark-25.mp3",
  cat: "https://sfxmint.com/dl/animal-cat-meow-34.mp3",
  cow: "https://sfxmint.com/dl/cow-moo-02.mp3",
  duck: "https://sfxmint.com/dl/duck-quack-02.mp3",
  frog: "https://sfxmint.com/dl/animal-frog-14.mp3",
  monkey: "https://sfxmint.com/dl/monkey-chatter-01.mp3",
  lion: "https://sfxmint.com/dl/lion-roar-01.mp3",
  elephant: "https://sfxmint.com/dl/elephant-trumpet-01.mp3",
  chicken: "https://sfxmint.com/dl/hen-cluck-02.mp3",
  sheep: "https://sfxmint.com/dl/sheep-bleat-02.mp3"
};

let currentAnimal = null;

function playAnimal(animal) {
  if (currentAnimal) {
    currentAnimal.pause();
    currentAnimal.currentTime = 0;
  }

  currentAnimal = new Audio(animalSounds[animal]);

  currentAnimal.play().catch(() => {
    alert("Sound could not play. Please check your internet connection.");
  });
}

// SPEAKING FUNCTION

function speak(words) {
  if (!("speechSynthesis" in window)) {
    alert("Speech is not supported by this browser.");
    return;
  }

  speechSynthesis.cancel();

  const message = new SpeechSynthesisUtterance(words);
  message.rate = 0.85;
  message.pitch = 1.2;

  speechSynthesis.speak(message);
}

// NUMBERS

const numbers = document.getElementById("numbers");

for (let i = 1; i <= 10; i++) {
  const button = document.createElement("button");
  button.className = "learning";
  button.textContent = i;

  button.onclick = () => speak(String(i));

  numbers.appendChild(button);
}

// ALPHABET

const alphabet = document.getElementById("alphabet");

"ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("").forEach(letter => {
  const button = document.createElement("button");
  button.className = "learning";
  button.textContent = letter;

  button.onclick = () => speak(letter);

  alphabet.appendChild(button);
});

// COLOURS

const colourList = [
  ["🔴 Red", "Red"],
  ["🔵 Blue", "Blue"],
  ["🟡 Yellow", "Yellow"],
  ["🟢 Green", "Green"],
  ["🟠 Orange", "Orange"],
  ["🟣 Purple", "Purple"],
  ["⚫ Black", "Black"],
  ["⚪ White", "White"],
  ["🩷 Pink", "Pink"],
  ["🤎 Brown", "Brown"]
];

const colours = document.getElementById("colours");

colourList.forEach(item => {
  const button = document.createElement("button");
  button.className = "learning";
  button.textContent = item[0];

  button.onclick = () => speak(item[1]);

  colours.appendChild(button);
});

// FRUITS

const fruitList = [
  ["🍎 Apple", "Apple"],
  ["🍌 Banana", "Banana"],
  ["🍊 Orange", "Orange"],
  ["🍇 Grapes", "Grapes"],
  ["🍉 Watermelon", "Watermelon"],
  ["🍍 Pineapple", "Pineapple"],
  ["🥭 Mango", "Mango"],
  ["🍓 Strawberry", "Strawberry"],
  ["🍐 Pear", "Pear"],
  ["🍒 Cherry", "Cherry"]
];

const fruits = document.getElementById("fruits");

fruitList.forEach(item => {
  const button = document.createElement("button");
  button.className = "learning";
  button.textContent = item[0];

  button.onclick = () => speak(item[1]);

  fruits.appendChild(button);
});

// BABYJOY 3-MINUTE MUSIC CORNER

let musicContext = null;
let musicTimer = null;
let musicStopTimer = null;

function playMusic() {
  stopMusic();

  const AudioContextClass =
    window.AudioContext || window.webkitAudioContext;

  if (!AudioContextClass) {
    alert("Music is not supported on this browser.");
    return;
  }

  const ctx = new AudioContextClass();
  musicContext = ctx;

  const melody = [
    523.25, 587.33, 659.25, 783.99,
    659.25, 587.33, 523.25, 392,
    440, 523.25, 659.25, 587.33,
    523.25, 440, 392, 523.25
  ];

  let index = 0;

  function note() {
    if (musicContext !== ctx) return;

    const osc = ctx.createOscillator();
    const gain = ctx.createGain();

    osc.type = "sine";
    osc.frequency.value = melody[index];

    gain.gain.setValueAtTime(0.0001, ctx.currentTime);
    gain.gain.linearRampToValueAtTime(
      0.10, ctx.currentTime + 0.04
    );
    gain.gain.exponentialRampToValueAtTime(
      0.0001, ctx.currentTime + 0.32
    );

    osc.connect(gain);
    gain.connect(ctx.destination);

    osc.start();
    osc.stop(ctx.currentTime + 0.34);

    index = (index + 1) % melody.length;

    musicTimer = setTimeout(note, 380);
  }

  ctx.resume().then(() => {
    if (musicContext !== ctx) return;

    note();

    musicStopTimer = setTimeout(() => {
      stopMusic();
      document.getElementById("musicMessage").textContent =
        "Music time is finished! 🎵";
    }, 180000);

    document.getElementById("musicMessage").textContent =
      "Enjoy your BabyJoy music! 🎶";
  }).catch(() => {
    stopMusic();
    alert("Please tap Play Music again.");
  });
}

function stopMusic() {
  clearTimeout(musicTimer);
  clearTimeout(musicStopTimer);

  musicTimer = null;
  musicStopTimer = null;

  if (musicContext) {
    const oldContext = musicContext;
    musicContext = null;
    oldContext.close();
  }

  const message = document.getElementById("musicMessage");

  if (message) {
    message.textContent = "Music stopped. 🎵";
  }
}

// BUBBLE FUN

function makeBubbles() {
  const area = document.getElementById("bubbleArea");

  for (let i = 0; i < 12; i++) {
    const bubble = document.createElement("div");
    bubble.className = "bubble";

    const size = Math.random() * 30 + 15;

    bubble.style.width = size + "px";
    bubble.style.height = size + "px";
    bubble.style.left = Math.random() * 90 + "%";
    bubble.style.animationDuration =
      (Math.random() * 3 + 2) + "s";

    area.appendChild(bubble);

    setTimeout(() => bubble.remove(), 5000);
  }
}

// SWEET DREAMS

function dreamTime() {
  stopMusic();

  if (currentAnimal) {
    currentAnimal.pause();
    currentAnimal.currentTime = 0;
  }

  if ("speechSynthesis" in window) {
    speechSynthesis.cancel();
  }

  speak("Good night, little star. Sweet dreams!");
}

</script>

</body>
</html>
