# <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For You ❤️</title>

<style>
body {
  margin: 0;
  padding: 0;
  font-family: 'Segoe UI', sans-serif;
  background: black;
  color: white;
  text-align: center;
  overflow: hidden;
}

#startScreen {
  position: fixed;
  width: 100%;
  height: 100%;
  background: linear-gradient(#ff4e7a, #ff758c);
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

button {
  padding: 15px 30px;
  font-size: 20px;
  border: none;
  border-radius: 30px;
  background: white;
  color: #ff4e7a;
  cursor: pointer;
}

#mainContent {
  display: none;
  padding-top: 50px;
}

h1 {
  font-size: 40px;
  animation: glow 2s infinite alternate;
}

@keyframes glow {
  from { text-shadow: 0 0 10px pink; }
  to { text-shadow: 0 0 25px red; }
}

.heart {
  position: absolute;
  color: red;
  animation: float 5s linear infinite;
}

@keyframes float {
  0% { transform: translateY(100vh); opacity: 1; }
  100% { transform: translateY(-10vh); opacity: 0; }
}
</style>
</head>

<body>

<div id="startScreen">
  <h2>Hey ❤️</h2>
  <button onclick="start()">Open Your Surprise 🎁</button>
</div>

<div id="mainContent">
  <h1>Happy Birthday 💖</h1>
  <h2 id="name">My Queen 👑</h2>

  <p id="typing"></p>

  <img src="photo.jpg" width="220" style="border-radius:20px; margin-top:20px;">
</div>

<audio id="music" loop>
  <source src="music.mp3" type="audio/mpeg">
</audio>

<script>
function start() {
  document.getElementById("startScreen").style.display = "none";
  document.getElementById("mainContent").style.display = "block";
  document.getElementById("music").play();
  typeText();
  createHearts();
}

let text = "You are the most beautiful part of my life 💖 I am so lucky to have you. I love you forever ❤️";
let i = 0;

function typeText() {
  if (i < text.length) {
    document.getElementById("typing").innerHTML += text.charAt(i);
    i++;
    setTimeout(typeText, 50);
  }
}

function createHearts() {
  setInterval(() => {
    let heart = document.createElement("div");
    heart.innerHTML = "❤️";
    heart.className = "heart";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = Math.random() * 20 + 20 + "px";
    document.body.appendChild(heart);

    setTimeout(() => heart.remove(), 5000);
  }, 300);
}
</script>

</body>
</html>
