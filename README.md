<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Will you be my Valentine?</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    
    body {
      background-color: #ffcfe0;
      font-family: 'Arial', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      overflow: hidden;
    }

    .card {
      background: white;
      padding: 40px 30px;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.1);
      text-align: center;
      max-width: 400px;
      width: 90%;
      position: relative;
    }

    .cat {
      font-size: 60px;
      margin-bottom: 20px;
    }

    h1 {
      font-size: 24px;
      color: #333;
      margin-bottom: 30px;
      font-weight: 600;
    }

    .buttons {
      display: flex;
      gap: 15px;
      justify-content: center;
      margin-bottom: 20px;
    }

    button {
      padding: 12px 30px;
      font-size: 18px;
      border: none;
      border-radius: 50px;
      cursor: pointer;
      font-weight: bold;
      transition: transform 0.1s ease;
    }

    button:active {
      transform: scale(0.95);
    }

    #yesBtn {
      background-color: #ff4d6d;
      color: white;
    }

    #noBtn {
      background-color: #e9ecef;
      color: #333;
      position: relative;
    }

    .small-text {
      font-size: 12px;
      color: #888;
      margin-top: 10px;
    }

    #result {
      display: none;
      animation: popIn 0.5s ease;
    }

    #result h2 {
      font-size: 32px;
      color: #ff4d6d;
      margin: 20px 0;
    }

    #result img {
      width: 100%;
      max-width: 300px;
      border-radius: 12px;
      margin-top: 15px;
    }

    @keyframes popIn {
      0% { transform: scale(0); opacity: 0; }
      80% { transform: scale(1.1); }
      100% { transform: scale(1); opacity: 1; }
    }

    .confetti {
      position: fixed;
      width: 10px;
      height: 10px;
      background: #ff4d6d;
      animation: confetti-fall 3s linear forwards;
    }

    @keyframes confetti-fall {
      to {
        transform: translateY(100vh) rotate(720deg);
        opacity: 0;
      }
    }
  </style>
</head>
<body>
  <div class="card">
    <div class="cat">🐱💕</div>
    <h1 id="question">PUT_HER_NAME_HERE will you be my valentine?</h1>
    
    <div class="buttons" id="buttons">
      <button id="yesBtn">Yes</button>
      <button id="noBtn">No</button>
    </div>
    
    <p class="small-text">*No seems a bit shy 👀</p>

    <div id="result">
      <h2>YAY! 🎉</h2>
      <img src="https://media.giphy.com/media/3o6ZsUJ44ffpnAW7Dy/giphy.gif" alt="Willem Dafoe celebrating">
    </div>
  </div>

  <script>
    const noBtn = document.getElementById('noBtn');
    const yesBtn = document.getElementById('yesBtn');
    const result = document.getElementById('result');
    const buttons = document.getElementById('buttons');
    const question = document.getElementById('question');
    const smallText = document.querySelector('.small-text');

    noBtn.addEventListener('mouseover', () => {
      const maxX = window.innerWidth - noBtn.offsetWidth - 20;
      const maxY = window.innerHeight - noBtn.offsetHeight - 20;
      
      const x = Math.random() * maxX;
      const y = Math.random() * maxY;
      
      noBtn.style.position = 'fixed';
      noBtn.style.left = x + 'px';
      noBtn.style.top = y + 'px';
    });

    noBtn.addEventListener('click', (e) => {
      e.preventDefault();
      noBtn.dispatchEvent(new Event('mouseover'));
    });

    yesBtn.addEventListener('click', () => {
      question.style.display = 'none';
      buttons.style.display = 'none';
      smallText.style.display = 'none';
      result.style.display = 'block';
      createConfetti();
    });

    function createConfetti() {
      for (let i = 0; i < 50; i++) {
        setTimeout(() => {
          const confetti = document.createElement('div');
          confetti.classList.add('confetti');
          confetti.style.left = Math.random() * 100 + 'vw';
          confetti.style.backgroundColor = `hsl(${Math.random() * 360}, 100%, 50%)`;
          confetti.style.animationDelay = Math.random() * 0.5 + 's';
          document.body.appendChild(confetti);
          
          setTimeout(() => confetti.remove(), 3000);
        }, i * 50);
      }
    }
  </script>
</body>
</html>
