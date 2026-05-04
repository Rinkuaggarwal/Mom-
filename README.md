<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Happy Birthday Mom ❤️</title>

<style>
body {
  margin: 0;
  background: #fce4ec;
  font-family: 'Arial', sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  overflow: hidden;
}

/* Envelope */
.envelope {
  position: relative;
  width: 300px;
  height: 200px;
  background: #ff8fa3;
  cursor: pointer;
}

.flap {
  position: absolute;
  width: 100%;
  height: 100%;
  background: #ff6f91;
  clip-path: polygon(0 0, 100% 0, 50% 50%);
  transform-origin: top;
  transition: 1s;
}

.card {
  position: absolute;
  width: 280px;
  height: 180px;
  background: white;
  top: 10px;
  left: 10px;
  padding: 15px;
  box-sizing: border-box;
  transform: translateY(0);
  transition: 1s;
  overflow: hidden;
}

.open .flap {
  transform: rotateX(180deg);
}

.open .card {
  transform: translateY(-200px);
}

/* Pages */
.page {
  display: none;
}

.page.active {
  display: block;
}

/* Buttons */
button {
  margin-top: 10px;
  padding: 5px 10px;
  border: none;
  background: #ff6f91;
  color: white;
  cursor: pointer;
}

/* Image */
img {
  width: 100%;
  border-radius: 10px;
}

/* Confetti */
.confetti {
  position: fixed;
  width: 10px;
  height: 10px;
  background: red;
  top: 0;
  animation: fall linear infinite;
}

@keyframes fall {
  to {
    transform: translateY(100vh);
  }
}
</style>
</head>

<body>

<div class="envelope" onclick="openCard()">
  <div class="flap"></div>

  <div class="card">
    
    <!-- Page 1 -->
    <div class="page active" id="page1">
      <h2>🎉 Happy Birthday Mom 🎉</h2>
      <p>You are my queen 👑 and my biggest blessing ❤️</p>
      <button onclick="nextPage()">Next ➡</button>
    </div>

    <!-- Page 2 -->
    <div class="page" id="page2">
      <img src="IMG_20260119_232113.jpg"alt="Mom">
      <p>Thank you for your love, care, and everything you do 💖</p>
      <button onclick="nextPage()">Next ➡</button>
    </div>

    <!-- Page 3 -->
    <div class="page" id="page3">
      <h3>I Love You Mom ❤️</h3>
      <p>Wishing you endless happiness and joy 🎂</p>
    </div>

  </div>
</div>

<!-- Birthday Song -->
<audio id="song" src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3"></audio>

<script>
let currentPage = 1;

function openCard() {
  document.querySelector(".envelope").classList.add("open");
  document.getElementById("song").play();
  createConfetti();
}

function nextPage() {
  document.getElementById("page" + currentPage).classList.remove("active");
  currentPage++;
  document.getElementById("page" + currentPage).classList.add("active");
}

function createConfetti() {
  for (let i = 0; i < 50; i++) {
    let confetti = document.createElement("div");
    confetti.classList.add("confetti");
    confetti.style.left = Math.random() * 100 + "vw";
    confetti.style.backgroundColor = randomColor();
    confetti.style.animationDuration = (Math.random() * 3 + 2) + "s";
    document.body.appendChild(confetti);
  }
}

function randomColor() {
  const colors = ["#ff0", "#f00", "#0f0", "#00f", "#ff69b4"];
  return colors[Math.floor(Math.random() * colors.length)];
}
</script>

</body>
</html>
