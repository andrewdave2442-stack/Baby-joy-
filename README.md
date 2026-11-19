
let audioContext;

function animal(name) {
  const AudioContextClass =
    window.AudioContext || window.webkitAudioContext;

  if (!AudioContextClass) {
    document.getElementById("message").textContent =
      "Audio is not supported by this browser.";
    return;
  }

  if (!audioContext) {
    audioContext = new AudioContextClass();
  }

  audioContext.resume().then(() => {
    const sounds = {
      dog: [300, 180, 300],
      cat: [650, 500, 650],
      cow: [180, 140, 180],
      duck: [500, 350, 500]
    };

    document.getElementById("message").textContent =
      "Hello from the " + name + "! ❤️";

    sounds[name].forEach((frequency, i) => {
      const oscillator = audioContext.createOscillator();
      const volume = audioContext.createGain();

      oscillator.frequency.value = frequency;
      oscillator.type = "sine";

      const start = audioContext.currentTime + i * 0.3;

      volume.gain.setValueAtTime(0.001, start);
      volume.gain.linearRampToValueAtTime(0.2, start + 0.05);
      volume.gain.linearRampToValueAtTime(0.001, start + 0.25);

      oscillator.connect(volume);
      volume.connect(audioContext.destination);

      oscillator.start(start);
      oscillator.stop(start + 0.26);
    });
  });
}
