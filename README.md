
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Happy Birthday Mom</title>
<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #ffe6f0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

/* Envelope */
.envelope {
  width: 250px;
  height: 150px;
  background: #ff6699;
  position: relative;
  cursor: pointer;
  border-radius: 5px;
}

.flap {
  position: absolute;
  width: 100%;
  height: 100%;
  background: #ff3366;
  clip-path: polygon(0 0, 100% 0, 50% 60%);
  transition: 0.5s;
}

.open .flap {
  transform: rotateX(180deg);
  transform-origin: top;
}

/* Card */
.card {
  position: absolute;
  top: 10px;
  left: 10px;
  width: 230px;
  height: 130px;
  background: white;
  text-align: center;
  padding-top: 20px;
  box-sizing: border-box;
  display: none;
}

.open .card {
  display: block;
}

/* Confetti */
.confetti {
  position: fixed;
  width: 10px;
  height: 10px;
  background: red;
  animation: fall 3s linear infinite;
}

@keyframes fall {
  0% { transform: translateY(-100px); }
  100% { transform: translateY(100vh); }
}
</style>
</head>

<body>

<div class="envelope" onclick="openCard(this)">
  <div class="flap"></div>
  <div class="card">
    <h3>Happy Birthday Mom ❤️</h3>
    <p>You are my world.<br>Wishing you love & happiness!</p>
  </div>
</div>

<audio id="music">
  <source src="https://www.fesliyanstudios.com/play-mp3/387" type="audio/mpeg">
</audio>

<script>
function openCard(el) {
  el.classList.add("open");
  document.getElementById("music").play();
  startConfetti();
}

function startConfetti() {
  for (let i = 0; i < 30; i++) {
    let conf = document.createElement("div");
    conf.className = "confetti";
    conf.style.left = Math.random() * 100 + "vw";
    conf.style.backgroundColor = 
      ['#ff3366','#ffcc00','#66ffcc','#3399ff'][Math.floor(Math.random()*4)];
    conf.style.animationDuration = (Math.random()*3+2)+"s";
    document.body.appendChild(conf);
  }
}
</script>

</body>
</html>
