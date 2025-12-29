# please-forgive-me-baby
Im-sorry-Mamma
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>For Momo 🤍</title>

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

    /* 💕 Cute floating hearts */
    .hearts {
      position: absolute;
      inset: 0;
      z-index: 0;
      pointer-events: none;
    }

    .heart {
      position: absolute;
      bottom: -40px;
      animation: floatUp linear infinite;
      opacity: 0;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(0) scale(0.8);
        opacity: 0;
      }
      20% { opacity: 0.7; }
      80% { opacity: 0.6; }
      100% {
        transform: translateY(-110vh) scale(1.4);
        opacity: 0;
      }
    }

    /* 💎 Card */
    .card {
      position: relative;
      z-index: 2;
      background: rgba(255, 255, 255, 0.98);
      backdrop-filter: blur(14px);
      padding: 55px 45px;
      border-radius: 32px;
      width: 92%;
      max-width: 480px;
      box-shadow: 0 40px 80px rgba(0,0,0,0.25);
      text-align: center;
      animation: popIn 1.3s ease;
    }

    @keyframes popIn {
      from {
        opacity: 0;
        transform: scale(0.9) translateY(30px);
      }
      to {
        opacity: 1;
        transform: scale(1) translateY(0);
      }
    }

    h1 {
      color: #ff6f91;
      font-weight: 600;
      margin-bottom: 18px;
      letter-spacing: 0.3px;
    }

    .message {
      font-size: 17px;
      color: #333;
      line-height: 1.7;
      min-height: 140px;
      white-space: pre-line;
      transition: opacity 0.5s ease;
    }

    .buttons {
      margin-top: 40px;
      display: flex;
      flex-direction: column;
      gap: 16px;
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
      box-shadow: 0 12px 28px rgba(255,111,145,0.45);
    }

    .continue:hover {
      transform: scale(1.06);
    }

    .forgive {
      background: white;
      color: #ff6f91;
      border: 2px solid #ff6f91;
      box-shadow: 0 0 0 rgba(0,0,0,0);
    }

    .forgive:hover {
      transform: scale(1.05);
      box-shadow: 0 0 22px rgba(255,111,145,0.35);
    }

    .footer {
      margin-top: 32px;
      font-size: 13px;
      color: #888;
    }

    .hidden { display: none; }

    .fade {
      animation: fadeSoft 1.2s ease forwards;
    }

    @keyframes fadeSoft {
      from { opacity: 0; }
      to { opacity: 1; }
    }
  </style>
</head>
<body>

  <!-- 💕 Background hearts -->
  <div class="hearts" id="hearts"></div>

  <!-- 🎹 Soft sad piano -->
  <audio id="music" loop>
    <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_0b6c89c8f2.mp3" type="audio/mpeg">
  </audio>

  <div class="card">
    <h1>Momo 🤍</h1>

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
      made with effort, feelings, and honesty
    </div>
  </div>

  <script>
    /* 💕 Generate cute hearts */
    const heartsContainer = document.getElementById("hearts");
    const heartEmojis = ["💗","💖","💞","💕","🤍"];

    for (let i = 0; i < 30; i++) {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.innerText = heartEmojis[Math.floor(Math.random() * heartEmojis.length)];
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.fontSize = 14 + Math.random() * 16 + "px";
      heart.style.animationDuration = 8 + Math.random() * 10 + "s";
      heart.style.animationDelay = Math.random() * 6 + "s";
      heartsContainer.appendChild(heart);
    }

    const messages = [
      "Hey Momo…",
      "I didn’t want to say sorry in a careless way.",
      "So I made this, hoping you’d feel how much I care.",
      "I know I hurt you, and I take full responsibility for that.",
      "You genuinely matter to me — more than my pride.",
      "I’m really, truly sorry.",
      "No pressure, no rush… I just hope we can talk when you’re ready."
    ];

    let index = 0;
    const text = document.getElementById("text");
    const forgiveBtn = document.getElementById("forgiveBtn");
    const continueBtn = document.getElementById("continueBtn");
    const music = document.getElementById("music");

    function nextMessage() {
      text.style.opacity = 0;

      setTimeout(() => {
        if (index < messages.length) {
          text.innerText = messages[index];
          text.style.opacity = 1;
          index++;
        }

        if (index === messages.length) {
          continueBtn.classList.add("hidden");
          forgiveBtn.classList.remove("hidden");
        }
      }, 300);
    }

    function forgiven() {
      music.volume = 0.35;
      music.play();

      text.classList.add("fade");
      text.innerText =
        "Thank you for reading all of this.\n\nYou don’t have to say anything right now.\nJust know that I’m here,\nand I’m not going anywhere. 🤍";

      forgiveBtn.classList.add("hidden");
    }

    nextMessage();
  </script>

</body>
</html>
