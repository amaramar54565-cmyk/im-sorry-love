# please-forgive-me-baby
Im-sorry-Mamma
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>For Momo 🤍</title>

  <!-- Handwritten font for her name -->
  <link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet">

  <style>
    * { box-sizing: border-box; }

    body {
      margin: 0;
      height: 100vh;
      background: linear-gradient(135deg, #ffe6f0, #e6ecff);
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: "Segoe UI", sans-serif;
      overflow: hidden;
    }

    /* 💕 Hearts (hidden at first) */
    .hearts {
      position: absolute;
      inset: 0;
      pointer-events: none;
      z-index: 0;
      display: none;
    }

    .heart {
      position: absolute;
      bottom: -40px;
      animation: floatUp linear infinite;
      opacity: 0;
    }

    @keyframes floatUp {
      0% { transform: translateY(0) scale(0.8); opacity: 0; }
      20% { opacity: 0.8; }
      80% { opacity: 0.6; }
      100% { transform: translateY(-110vh) scale(1.4); opacity: 0; }
    }

    /* 💎 Card */
    .card {
      position: relative;
      z-index: 2;
      background: rgba(255,255,255,0.98);
      backdrop-filter: blur(14px);
      padding: 58px 46px;
      border-radius: 36px;
      width: 92%;
      max-width: 480px;
      box-shadow: 0 45px 90px rgba(0,0,0,0.25);
      text-align: center;
      animation: popIn 1.3s ease;
    }

    @keyframes popIn {
      from { opacity: 0; transform: scale(0.9) translateY(30px); }
      to { opacity: 1; transform: scale(1) translateY(0); }
    }

    h1 {
      font-family: 'Pacifico', cursive;
      color: #ff6f91;
      font-size: 36px;
      margin-bottom: 22px;
    }

    .message {
      font-size: 17px;
      color: #333;
      line-height: 1.75;
      min-height: 145px;
      white-space: pre-line;
      transition: opacity 0.5s ease;
    }

    .buttons {
      margin-top: 42px;
      display: flex;
      flex-direction: column;
      gap: 18px;
    }

    button {
      padding: 15px;
      border-radius: 40px;
      border: none;
      font-size: 15px;
      cursor: pointer;
      transition: all 0.25s ease;
    }

    .continue {
      background: linear-gradient(135deg, #ff6f91, #ff9a9e);
      color: white;
      box-shadow: 0 14px 30px rgba(255,111,145,0.45);
    }

    .continue:hover { transform: scale(1.06); }

    /* ✨ Forgive button sparkle */
    .forgive {
      background: white;
      color: #ff6f91;
      border: 2px solid #ff6f91;
      position: relative;
      overflow: hidden;
    }

    .forgive::after {
      content: "";
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: radial-gradient(circle, rgba(255,182,193,0.35), transparent 60%);
      animation: sparkle 2.5s infinite;
    }

    @keyframes sparkle {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    .forgive:hover {
      transform: scale(1.07);
      box-shadow: 0 0 26px rgba(255,111,145,0.4);
    }

    .footer {
      margin-top: 34px;
      font-size: 13px;
      color: #888;
    }

    .hidden { display: none; }

    /* 💓 Heartbeat after forgiveness */
    .heartbeat {
      animation: beat 1.6s infinite;
    }

    @keyframes beat {
      0%,100% { transform: scale(1); }
      50% { transform: scale(1.04); }
    }
  </style>
</head>
<body>

  <!-- 💕 Hearts -->
  <div class="hearts" id="hearts"></div>

  <!-- 🎹 Music -->
  <audio id="music" loop>
    <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_0b6c89c8f2.mp3" type="audio/mpeg">
  </audio>

  <div class="card" id="card">
    <h1>Momo</h1>

    <div class="message" id="text"></div>

    <div class="buttons">
      <button class="continue" id="continueBtn" onclick="nextMessage()">
        Continue
      </button>

      <button class="forgive hidden" id="forgiveBtn" onclick="forgiven()">
        I forgive you 🫶
      </button>
    </div>

    <div class="footer">
      made with effort, patience, and feelings
    </div>
  </div>

  <script>
    const messages = [
      "Hey…",
      "I didn’t want to say sorry in a lazy way.",
      "So I made this, hoping you’d feel how much you matter to me.",
      "I know I hurt you, and I take full responsibility for that.",
      "You mean more to me than my pride or my mistakes.",
      "I’m truly sorry, Momo.",
      "No pressure at all — I just hope we can talk when you’re ready."
    ];

    let index = 0;
    const text = document.getElementById("text");
    const continueBtn = document.getElementById("continueBtn");
    const forgiveBtn = document.getElementById("forgiveBtn");
    const music = document.getElementById("music");
    const hearts = document.getElementById("hearts");
    const card = document.getElementById("card");

    function nextMessage() {
      text.style.opacity = 0;
      setTimeout(() => {
        text.innerText = messages[index];
        text.style.opacity = 1;
        index++;

        if (index === messages.length) {
          continueBtn.classList.add("hidden");
          forgiveBtn.classList.remove("hidden");
        }
      }, 300);
    }

    function forgiven() {
      // music
      music.volume = 0.35;
      music.play();

      // hearts appear
      hearts.style.display = "block";
      const heartEmojis = ["💗","💖","💞","💕","🤍"];

      for (let i = 0; i < 35; i++) {
        const h = document.createElement("div");
        h.className = "heart";
        h.innerText = heartEmojis[Math.floor(Math.random()*heartEmojis.length)];
        h.style.left = Math.random()*100 + "vw";
        h.style.fontSize = 14 + Math.random()*16 + "px";
        h.style.animationDuration = 8 + Math.random()*10 + "s";
        h.style.animationDelay = Math.random()*5 + "s";
        hearts.appendChild(h);
      }

      // heartbeat effect
      card.classList.add("heartbeat");

      text.innerText =
        "Thank you for reading all of this.\n\nYou don’t have to say anything right now.\nTake your time.\n\nI’m here — whenever you’re ready. 🤍";

      forgiveBtn.classList.add("hidden");
    }

    nextMessage();
  </script>

</body>
</html>
