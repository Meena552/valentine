<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For My Valentine ❤️</title>

<style>
body {
  margin: 0;
  font-family: 'Segoe UI', sans-serif;
  background: linear-gradient(to right, #ffb6c1, #ffd1dc);
  text-align: center;
  overflow: hidden;
}

h1 {
  color: #b30059;
  margin-top: 40px;
}

button {
  padding: 12px 30px;
  font-size: 20px;
  border-radius: 30px;
  border: none;
  cursor: pointer;
  margin: 15px;
}

#yesBtn { background: #ff4d6d; color: white; }
#noBtn  { background: gray; color: white; position: absolute; }

.hidden { display: none; }

.gift {
  background: white;
  padding: 20px;
  border-radius: 20px;
  margin: 15px;
  cursor: pointer;
  font-size: 22px;
}

/* Floating stars & butterflies */
.star, .butterfly {
  position: absolute;
  animation: float 6s infinite linear;
}

.star {
  color: white;
  font-size: 14px;
}

.butterfly {
  font-size: 24px;
}

@keyframes float {
  0% { transform: translateY(100vh); opacity: 1; }
  100% { transform: translateY(-10vh); opacity: 0; }
}
</style>
</head>

<body>

<div id="question">
  <div style="font-size:80px;">🧸💖</div>
  <h1>Will you be my Valentine?</h1>
  <button id="yesBtn" onclick="showGifts()">Yes 💘</button>
  <button id="noBtn" onclick="noClicked()">No 😏</button>
  <p id="noMsg"></p>
</div>

<div id="gifts" class="hidden">
  <h1>🎁 Your Gifts 🎁</h1>

  <div class="gift" onclick="playSong()">🎵 Gift 1 – Our Song</div>
  <div class="gift" onclick="showMessage()">💌 Gift 2 – My Heart</div>
  <div class="gift" onclick="showPhotos()">📸 Gift 3 – Our Memories</div>

  <div id="content"></div>
</div>

<audio id="song" src="song.mp3"></audio>

<script>
let noCount = 0;
const msgs = [
  "Vena 😤",
  "Vena Aludhuruva 😢",
  "Mandaiya Odachuruva Paathuko 😡"
];

function noClicked() {
  if (noCount < msgs.length) {
    document.getElementById("noMsg").innerText = msgs[noCount];
    noCount++;
  } else {
    moveNo();
  }
}

function moveNo() {
  const btn = document.getElementById("noBtn");
  btn.style.left = Math.random()*80 + "%";
  btn.style.top  = Math.random()*80 + "%";
}

function showGifts() {
  document.getElementById("question").style.display = "none";
  document.getElementById("gifts").classList.remove("hidden");
}

function playSong() {
  document.getElementById("song").play();
  document.getElementById("content").innerHTML =
    "<h2>🎶 Close your eyes & feel us 💖</h2>";
}

function showMessage() {
  document.getElementById("content").innerHTML = `
  <p style="font-size:20px; color:#800040; padding:20px;">
  Na una romba love panra 💕<br><br>
  Ne enakaga epavum irukanum.<br>
  Enaku edhavadhu problem varumbothu,
  ne first person ah irundhu adha solve pananum.<br><br>
  Na sogama irundhalu, sad ah feel panalu,
  ne en kaiya pudichu
  "na iruka, rendu peru paathukla"
  nu sonna… enaku romba pudikum ❤️<br><br>
  Happy Valentine’s Day 💖
  </p>`;
}

function showPhotos() {
  document.getElementById("content").innerHTML = `
  <img src="photo1/pic1.jpg" width="200">
  <img src="photo2/pic2.jpg" width="200">
  <img src="photo3/pic3.jpg" width="200">
  <img src="photo4/pic4.jpg" width="200">`;
}

/* Stars & butterflies generator */
setInterval(() => {
  const el = document.createElement("div");
  el.className = Math.random() > 0.5 ? "star" : "butterfly";
  el.innerHTML = el.className === "star" ? "⭐" : "🦋";
  el.style.left = Math.random()*100 + "vw";
  document.body.appendChild(el);
  setTimeout(()=>el.remove(),6000);
}, 300);
</script>

</body>
</html>
