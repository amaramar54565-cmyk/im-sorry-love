# im-sorry-love
im sorry love
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>For Momo</title>
  <style>
    * { box-sizing: border-box; }

    body {
      margin: 0;
      height: 100vh;
      background: radial-gradient(circle at top, #fdeff2, #cfd9ff);
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: "Segoe UI", sans-serif;
      overflow: hidden;
    }

    /* 💗 Floating Hearts Background */
    .hearts {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      overflow: hidden;
      z-index: 0;
    }

    .heart {
      position: absolute;
      bottom: -50px;
      font-size: 18px;
      color: rgba(217, 76, 125, 0.35);
      animation: floatUp linear infinite;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(0) scale(1);
        opacity: 0;
      }
      20% { opacity: 0.6; }
      80% { opacity: 0.4; }
      100% {
        transform: translateY(-110vh) scale(1.4);
        opacity: 0;
      }
    }

    /* 💎 Card */
    .card {
      position: relative;
      z-index: 2;
      background: rgba(255, 255, 255, 0.97);
      backdrop-filter: blur(12px);
      padding: 55px 42px;
      border-radius: 28px;
      width: 92%;
      max-width: 480px;
      box-shadow: 0 35px 70px rgba(0, 0, 0, 0.28);
      text-align: center;
      animation: rise 1.4s ease;
    }

    @keyframes rise {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }

    h1 {
      color: #d94c7d;
      font-weight: 600;
      margin-bottom: 20px;
    }

    .message {
      font-size: 17px;
      color: #333;
      line-height: 1.7;
      min-height: 130px;
      white-space: pre-line;
      transition: opacity 0.5s ease;
    }

    .buttons {
      margin-top: 38px;
      display: flex;
      flex-direction: column;
      gap: 15px;
    }

    button {
      padding: 14px;
      border-radius: 32px;
      border: none;
      font-size: 15px;
      cursor: pointer;
      transition: transform 0.25s, box-shadow 0.25s;
    }

    .continue {
      background: #d94c7d;
      color: white;
      box-shadow: 0 12px 28px rgba(217, 76, 125, 0.45);
    }

    .continue:hover { transform: scale(1.05); }

    .forgive {
      background: transparent;
      color: #d94c7d;
      border: 2px solid #d94c7d;
    }

    .forgive:hover {
      transform: scale(1.04);
      box-shadow: 0 0 22px rgba(217, 76, 125, 0.3);
    }

    .footer {
      margin-top: 30px;
      font-size: 13px;
      color: #777;
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

  <!-- 💗 Hearts -->
  <div class="hearts" id="hearts"></div>

  <!-- 🎹 Music -->
  <audio id="music" loop>
    <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_0b6c89c8f2.mp3" type="audio/mpeg">
  </audio>

  <div class="card">
    <h1>Momo</h1>

    <div class="message" id="text"></div>

    <div class="buttons">
      <button class="continue" id="continueBtn" onclick="nextMessage()">
        Continue
      </button>

      <button class="forgive hidden" id="forgiveBtn" onclick="forgiven()">
        I forgive you 🤍
      </button>
    </div>

    <div class="footer">
      from someone who truly cares about you
    </div>
  </div>

  <script>
    /* 💗 Generate hearts */
    const heartsContainer = document.getElementById("hearts");

    for (let i = 0; i < 25; i++) {
      const heart = document.createElement("div");
      heart.classList.add("heart");
      heart.innerText = "❤";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.animationDuration = 8 + Math.random() * 8 + "s";
      heart.style.fontSize = 14 + Math.random() * 14 + "px";
      heart.style.animationDelay = Math.random() * 5 + "s";
      heartsContainer.appendChild(heart);
    }

    const messages = [
      "I didn’t want to send a rushed message or a careless apology.",
      "I needed you to know that I’ve reflected on my actions.",
      "I understand how I hurt you, and I take full responsibility.",
      "You matter to me more than my pride, more than being right.",
      "I am genuinely sorry, Momo.",
      "I don’t expect forgiveness or immediate answers.",
      "I just hope, in time, we can talk and heal this."
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
        "Thank you for giving me this chance.\n\nYou don’t have to reply right now.\nTake all the time you need.\n\nI’ll be here — whenever you’re ready.";

      forgiveBtn.classList.add("hidden");
    }

    nextMessage();
  </script>

</body>
</html>
