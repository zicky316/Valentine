<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Loading...</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #333;
      text-align: center;
      overflow: hidden;
    }

    .card {
      background: white;
      padding: 40px 30px;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.15);
      max-width: 400px;
      width: 90%;
      animation: fadeIn 1.5s ease forwards;
      position: relative;
      z-index: 2;
    }

    h1 {
      margin-bottom: 10px;
      font-size: 28px;
    }

    p {
      font-size: 18px;
      margin: 15px 0 25px;
    }

    button {
      border: none;
      padding: 12px 22px;
      margin: 8px;
      font-size: 16px;
      border-radius: 10px;
      cursor: pointer;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }

    .yes {
      background-color: #ff4d6d;
      color: white;
    }

    .yes:hover {
      transform: scale(1.05);
      box-shadow: 0 6px 15px rgba(255, 77, 109, 0.4);
    }

    .no {
      background-color: #ddd;
    }

    .hidden {
      display: none;
    }

    /* Floating hearts */
    .heart {
      position: absolute;
      bottom: -20px;
      width: 20px;
      height: 20px;
      background: #ff4d6d;
      transform: rotate(45deg);
      animation: floatUp 6s linear infinite;
      opacity: 0.7;
      z-index: 1;
    }

    .heart::before,
    .heart::after {
      content: "";
      position: absolute;
      width: 20px;
      height: 20px;
      background: #ff4d6d;
      border-radius: 50%;
    }

    .heart::before { top: -10px; left: 0; }
    .heart::after { left: -10px; top: 0; }

    @keyframes floatUp {
      0% { transform: translateY(0) rotate(45deg); opacity: 0.7; }
      100% { transform: translateY(-110vh) rotate(45deg); opacity: 0; }
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>

  <div class="card" id="loading">
    <h1>Loading feelings for Shaquila...</h1>
    <p id="progress">0%</p>
  </div>

  <div class="card hidden" id="question">
    <h1>Hi my love Shaquila ❤️</h1>
    <p>Every day with you feels like the best part of my life.</p>
    <p><strong>Will you be my Valentine?</strong></p>

    <button class="yes" onclick="sayYes()">YES 💖</button>
    <button class="no" onclick="moveNo(this)">No</button>
  </div>

  <div class="card hidden" id="yesMessage">
    <h1>Yaaay Shaquila!!! 💕</h1>
    <p>You just made me the happiest person alive.</p>
    <p>I love you so much. Happy Valentine's Day ❤️</p>
  </div>

  <script>
    let percent = 0;
    const progressText = document.getElementById('progress');
    const loading = document.getElementById('loading');
    const question = document.getElementById('question');

    const interval = setInterval(() => {
      percent += 5;
      progressText.textContent = percent + '%';

      if (percent >= 100) {
        clearInterval(interval);
        loading.classList.add('hidden');
        question.classList.remove('hidden');
        document.title = 'A question for Shaquila ❤️';
        startHearts();
      }
    }, 120);

    function sayYes() {
      question.classList.add('hidden');
      document.getElementById('yesMessage').classList.remove('hidden');
      document.title = 'She said YES! 💖';
    }

    function moveNo(button) {
      const x = Math.random() * (window.innerWidth - button.clientWidth);
      const y = Math.random() * (window.innerHeight - button.clientHeight);
      button.style.position = 'absolute';
      button.style.left = x + 'px';
      button.style.top = y + 'px';
    }

    function startHearts() {
      setInterval(() => {
        const heart = document.createElement('div');
        heart.className = 'heart';
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.animationDuration = (4 + Math.random() * 3) + 's';
        document.body.appendChild(heart);

        setTimeout(() => heart.remove(), 7000);
      }, 300);
    }
  </script>
</body>
</html>
