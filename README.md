<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Valentine for Yas</title>

  <style>
    body {
      background: linear-gradient(#ffe6f0, #ffd6e8);
      font-family: Arial, sans-serif;
      margin: 0;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      overflow: hidden;
    }

    .container {
      text-align: center;
      width: 100%;
      max-width: 420px;
      padding: 20px;
      position: relative;
      z-index: 2;
    }

    h1 {
      color: #ff4d88;
      font-size: 2.3em;
      margin-bottom: 8px;
    }

    p {
      color: #ff6fa5;
      font-size: 1.15em;
      margin-bottom: 20px;
    }

    #sadText {
      min-height: 40px;
      color: #ff4d88;
      font-size: 1em;
      margin-bottom: 15px;
    }

    .buttons {
      position: relative;
      height: 180px;
    }

    button {
      padding: 14px 22px;
      font-size: 18px;
      border: none;
      border-radius: 18px;
      cursor: pointer;
      transition: transform 0.2s ease;
    }

    #yes {
      background-color: #ff4d88;
      color: white;
    }

    #no {
      background-color: #aaa;
      color: white;
      position: absolute;
      right: 10px;
      bottom: 10px;
    }

    .hidden {
      display: none;
    }

    /* 🎆 Fireworks */
    .firework {
      position: fixed;
      width: 6px;
      height: 6px;
      border-radius: 50%;
      animation: explode 1s ease-out forwards;
      pointer-events: none;
    }

    @keyframes explode {
      0% {
        transform: scale(1);
        opacity: 1;
      }
      100% {
        transform: translate(var(--x), var(--y)) scale(0);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <div class="container" id="question">
    <h1>Yasyyy 💖</h1>
    <p>Will you be my Valentine?</p>

    <div id="sadText"></div>

    <div class="buttons">
      <button id="yes">YES 💕</button>
      <button id="no">NO 🙄</button>
    </div>
  </div>

  <div class="container hidden" id="success">
    <h1>YIIPPYYYY 💘🥰</h1>
    <p>You probablly made my year Ms.Claire 💕</p>
    <p style="color:#ff4d88;">Happy Valentines day 💖</p>
  </div>

  <audio id="music">
    <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_3a4b6b0b93.mp3?filename=cute-happy-114254.mp3" type="audio/mpeg">
  </audio>

  <script>
    const noBtn = document.getElementById("no");
    const yesBtn = document.getElementById("yes");
    const sadText = document.getElementById("sadText");

    const messages = [
      "I’ll be a little sad if you say no 🥺",
      "That would break my heart 💔",
      "Please don’t do this to me 😭",
      "I’ve thinking about it for months 😢",
      "Okay now you’re just being like Mr.X 😔"
    ];

    let scale = 1;
    let msgIndex = 0;

    yesBtn.addEventListener("click", () => {
      document.getElementById("music").play();
      document.getElementById("question").classList.add("hidden");
      document.getElementById("success").classList.remove("hidden");
      launchFireworks();
    });

    noBtn.addEventListener("mouseover", moveNo);
    noBtn.addEventListener("click", () => {
      scale -= 0.15;
      if (scale < 0.35) noBtn.textContent = "👀";

      noBtn.style.transform = `scale(${scale})`;
      sadText.textContent = messages[msgIndex % messages.length];
      msgIndex++;
      moveNo();
    });

    function moveNo() {
      const x = Math.random() * 180;
      const y = Math.random() * 120;
      noBtn.style.left = x + "px";
      noBtn.style.top = y + "px";
  
