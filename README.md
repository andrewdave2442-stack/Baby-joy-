
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
  padding: 25px;
  font-size: 28px;
}
.card {
  background: white;
  margin: 15px;
  padding: 20px;
  border-radius: 20px;
}
button {
  background: #8b72ee;
  color: white;
  border: none;
  padding: 16px;
  margin: 7px;
  border-radius: 15px;
  font-size: 20px;
}
</style>
</head>
<body>
<header>
🌈 BabyJoy 🌈
<br><small>Little Fun World</small>
</header>

<div class="card">
<h2>⭐ Welcome, Little Star!</h2>
<p>Let's play and learn!</p>
</div>

<div class="card">
<h2>🐾 Animal Sounds</h2>
<button onclick="animal('dog')">🐶 Dog</button>
<button onclick="animal('cat')">🐱 Cat</button>
<button onclick="animal('cow')">🐮 Cow</button>
<button onclick="animal('duck')">🦆 Duck</button>
<p id="message">Tap an animal to hear a sound!</p>
</div>

<div class="card">
<h2>🫧 Bubble Fun</h2>
<button onclick="alert('Pop! Pop! Pop!')">Pop bubbles!</button>
</div>

<div class="card">
<h2>🌙 Sweet Dreams</h2>
<p>Rest and relax, little star!</p>
</div>

<script>
function animal(name) {
  const audio = new (window.AudioContext || window.webkitAudioContext)();
  const sounds = {
    dog: [300, 180, 300],
    cat: [650, 500, 650],
    cow: [180, 140, 180],
    duck: [500, 350, 500]
  };
  document.getElementById("message").textContent =
    "Hello from the " + name + "! ❤️";
  sounds[name].forEach((frequency, i) => {
    const oscillator = audio.createOscillator();
    const volume = audio.createGain();
    oscillator.frequency.value = frequency;
    oscillator.type = "sine";
    volume.gain.setValueAtTime(0.0001, audio.currentTime + i * 0.25);
    volume.gain.linearRampToValueAtTime(
      0.12, audio.currentTime + i * 0.25 + 0.03
    );
    volume.gain.exponentialRampToValueAtTime(
      0.0001, audio.currentTime + i * 0.25 + 0.18
    );
    oscillator.connect(volume);
    volume.connect(audio.destination);
    oscillator.start(audio.currentTime + i * 0.25);
    oscillator.stop(audio.currentTime + i * 0.25 + 0.2);
  });
}
</script>
</body>
</html>
