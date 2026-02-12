<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Happy Valentine’s Day ❤️</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: black;
      color: white;
      text-align: center;
      font-family: 'Segoe UI', sans-serif;
      overflow-x: hidden;
    }

    .teddy {
      font-size: 80px;
      animation: float 2s infinite;
    }

    @keyframes float {
      0% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
      100% { transform: translateY(0); }
    }

    button {
      padding: 12px 25px;
      font-size: 18px;
      margin: 10px;
      border-radius: 25px;
      border: none;
      cursor: pointer;
    }

    .yes { background: pink; }
    .no { background: lightgray; position: absolute; }

    #gifts img {
      margin: 10px;
      border-radius: 10px;
    }

    /* Stars */
    .star {
      position: fixed;
      width: 2px;
      height: 2px;
      background: white;
      animation: fall linear infinite;
    }

    @keyframes fall {
      from { transform: translateY(-100px); }
      to { transform: translateY(100vh); }
    }
  </style>
</head>

<body>

  <!-- Question Section -->
  <div id="question">
    <div class="teddy">🧸💖</div>
    <h1>Will you be my Valentine?</h1>
    <button class="yes" onclick="sayYes()">Yes 💕</button>
    <button class="no" onclick="sayNo()">No 😜</button>
  </div>

  <!-- Gifts Section -->
  <div id="gifts" style="display:none;">
    <h1>I love you ❤️ Happy Valentine’s Day 💕</h1>
    <h2>🎁 Your Gifts 🎁</h2>

    <button onclick="openGift(1)">Gift 1 🎵</button>
    <button onclick="openGift(2)">Gift 2 💌</button>
    <button onclick="openGift(3)">Gift 3 📸</button>

    <div id="giftContent"></div>
  </div>

<script>
let noCount = 0;

function sayYes() {
  document.getElementById("question").style.display = "none";
  document.getElementById("gifts").style.display = "block";
}

function sayNo() {
  noCount++;

  const noBtn = document.querySelector(".no");

  if (noCount === 1) alert("Vena 😏");
  if (noCount === 2) alert("Vena Aludhuruva 😢");
  if (noCount === 3) alert("Mandaiya Odachuruva Paathuko 😡");

  noBtn.style.left = Math.random() * window.innerWidth + "px";
  noBtn.style.top = Math.random() * window.innerHeight + "px";
}

function openGift(num) {
  const content = document.getElementById("giftContent");

  if (num === 1) {
    content.innerHTML = `
     <h3>🎵 Our Favourite Songs</h3>
  <button onclick="playSong('song1.mp3')">Song 1 💖</button>
  <button onclick="playSong('song2.mp3')">Song 2 💕</button>

  <audio id="player" controls></audio>
`;
  }

  if (num === 2) {
    content.innerHTML = `
      <p style="font-size:18px;">
      Na una romba love panra ❤️<br><br>
      Ne enakaga epavum irukanum.<br>
      Enaku edhavadhu problem varumbothu  
      ne first person ah irundhu adha solve pananum.<br><br>
      Na sogama irundhalum sad ah feel panalum  
      ne en kaiya pudichu  
      "na iruka rendu peru paathukalam"  
      nu sonna romba pudikum 💕<br><br>
      Happy Valentine’s Day ❤️
      </p>
    `;
  }

  if (num === 3) {
    content.innerHTML = `
      <h3>📸 Our Memories</h3>
      <img src="photos/pics1.png" width="200">
      <img src="photos/pics2.png" width="200">
      <img src="photos/pics3.png" width="200">
      <img src="photos/pics3.png" width="200">
      <img src="photos/pics5.png" width="200">
    `;
  }
}

/* Stars animation */
for (let i = 0; i < 50; i++) {
  let star = document.createElement("div");
  star.className = "star";
  star.style.left = Math.random() * 100 + "vw";
  star.style.animationDuration = (Math.random() * 3 + 2) + "s";
  document.body.appendChild(star);
}
</script>

</body>
</html>

