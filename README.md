<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Flowers For You?</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Comic Sans MS', 'Chalkboard SE', 'Poppins', cursive, sans-serif;
    }

    body {
      background-color: #ffdae9;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      transition: background-color 1s ease;
    }

    /* Initial Prompt Card */
    .card {
      background: #ffffff;
      padding: 30px 25px;
      border-radius: 25px;
      box-shadow: 0 10px 25px rgba(255, 105, 180, 0.3);
      text-align: center;
      width: 320px;
      position: relative;
      transition: transform 0.5s ease, opacity 0.5s ease;
    }

    .card img {
      width: 140px;
      height: 140px;
      object-fit: contain;
      border-radius: 15px;
      margin-bottom: 15px;
    }

    .card h1 {
      color: #ff4b8b;
      font-size: 24px;
      margin-bottom: 25px;
    }

    .btn-group {
      display: flex;
      justify-content: center;
      gap: 15px;
      position: relative;
      min-height: 50px;
    }

    button {
      padding: 10px 25px;
      font-size: 16px;
      font-weight: bold;
      border: none;
      border-radius: 20px;
      cursor: pointer;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
      transition: transform 0.2s ease;
    }

    #yesBtn {
      background-color: #4CAF50;
      color: white;
    }

    #yesBtn:hover {
      transform: scale(1.1);
    }

    #noBtn {
      background-color: #ff3b30;
      color: white;
      position: absolute;
      right: 40px;
    }

    /* Tulip Container */
    .flower-container {
      display: none;
      opacity: 0;
      flex-direction: column;
      align-items: center;
      transition: opacity 1s ease;
    }

    .flower-container.visible {
      display: flex;
      opacity: 1;
    }

    .glass-dome {
      width: 220px;
      height: 320px;
      border: 4px solid rgba(255, 255, 255, 0.7);
      border-bottom: 12px solid #5a3d28;
      border-radius: 110px 110px 15px 15px;
      background: linear-gradient(135deg, rgba(255,255,255,0.4) 0%, rgba(255,255,255,0.05) 100%);
      box-shadow: inset 0 0 15px rgba(255,255,255,0.5), 0 15px 25px rgba(0,0,0,0.3);
      position: relative;
      display: flex;
      justify-content: center;
      align-items: flex-end;
      padding-bottom: 10px;
      backdrop-filter: blur(2px);
    }

    /* SVG Tulip Styling */
    .tulip-svg {
      width: 140px;
      height: 230px;
      filter: drop-shadow(0 5px 10px rgba(0,0,0,0.2));
      animation: float 3s ease-in-out infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-8px); }
    }

    /* Floating Heart Animation */
    .heart {
      position: absolute;
      font-size: 20px;
      color: #4a90e2;
      animation: flyUp 4s linear infinite;
      opacity: 0;
      bottom: 0;
    }

    @keyframes flyUp {
      0% {
        transform: translateY(0) scale(0.8);
        opacity: 1;
      }
      100% {
        transform: translateY(-100vh) scale(1.3);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <!-- Initial Card -->
  <div class="card" id="card">
    <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExM3Y1b241Z2dudXBhZ2sycHNydWtrYW80dHFyZzRxMWkxcjI0cmY4YiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/MDJ9IbxxvDUQM/giphy.gif" alt="Cute Cat">
    <h1>Flowers For You?</h1>
    <div class="btn-group">
      <button id="yesBtn">Yes</button>
      <button id="noBtn">No</button>
    </div>
  </div>

  <!-- Blue Tulip Reveal Container -->
  <div class="flower-container" id="flowerContainer">
    <div class="glass-dome">
      <svg class="tulip-svg" viewBox="0 0 100 150">
        <!-- Stem & Leaves -->
        <path d="M50 80 Q 48 110 50 145" stroke="#4a7c59" stroke-width="4" fill="none" stroke-linecap="round"/>
        <path d="M50 115 Q 25 105 20 90 Q 35 95 50 110" fill="#6b9b76"/>
        <path d="M50 125 Q 75 115 80 100 Q 65 105 50 120" fill="#6b9b76"/>
        
        <!-- Tulips Group -->
        <!-- Center Main Tulip -->
        <g transform="translate(0, -5)">
          <path d="M35 55 C 32 80, 68 80, 65 55 C 65 35, 35 35, 35 55 Z" fill="#4a90e2"/>
          <path d="M35 55 C 40 40, 50 30, 50 55 C 40 65, 35 60, 35 55 Z" fill="#357abd"/>
          <path d="M65 55 C 60 40, 50 30, 50 55 C 60 65, 65 60, 65 55 Z" fill="#70a6ff"/>
          <path d="M42 48 C 45 35, 55 35, 58 48 C 50 58, 45 55, 42 48 Z" fill="#90c0ff"/>
        </g>

        <!-- Left Tulip Bud -->
        <g transform="translate(-18, 15) rotate(-20 35 55) scale(0.65)">
          <path d="M50 80 Q 40 95 50 110" stroke="#4a7c59" stroke-width="4" fill="none"/>
          <path d="M35 55 C 32 80, 68 80, 65 55 C 65 35, 35 35, 35 55 Z" fill="#357abd"/>
          <path d="M35 55 C 40 40, 50 30, 50 55 C 40 65, 35 60, 35 55 Z" fill="#4a90e2"/>
          <path d="M65 55 C 60 40, 50 30, 50 55 C 60 65, 65 60, 65 55 Z" fill="#70a6ff"/>
        </g>

        <!-- Right Tulip Bud -->
        <g transform="translate(18, 20) rotate(20 65 55) scale(0.6)">
          <path d="M50 80 Q 60 95 50 110" stroke="#4a7c59" stroke-width="4" fill="none"/>
          <path d="M35 55 C 32 80, 68 80, 65 55 C 65 35, 35 35, 35 55 Z" fill="#70a6ff"/>
          <path d="M35 55 C 40 40, 50 30, 50 55 C 40 65, 35 60, 35 55 Z" fill="#4a90e2"/>
          <path d="M65 55 C 60 40, 50 30, 50 55 C 60 65, 65 60, 65 55 Z" fill="#357abd"/>
        </g>
      </svg>
    </div>
  </div>

  <script>
    const noBtn = document.getElementById('noBtn');
    const yesBtn = document.getElementById('yesBtn');
    const card = document.getElementById('card');
    const flowerContainer = document.getElementById('flowerContainer');

    // Runaway "No" Button interaction
    function moveNoBtn() {
      const x = Math.random() * 200 - 100;
      const y = Math.random() * 200 - 100;
      noBtn.style.transform = `translate(${x}px, ${y}px)`;
    }

    noBtn.addEventListener('mouseenter', moveNoBtn);
    noBtn.addEventListener('click', (e) => {
      e.preventDefault();
      moveNoBtn();
    });

    // Reveal Tulip Bouquet on "Yes"
    yesBtn.addEventListener('click', () => {
      card.style.opacity = '0';
      card.style.transform = 'scale(0.8)';
      
      setTimeout(() => {
        card.style.display = 'none';
        document.body.style.backgroundColor = '#1a2639';
        flowerContainer.classList.add('visible');
        startHearts();
      }, 500);
    });

    // Spawn floating blue hearts
    function startHearts() {
      setInterval(() => {
        const heart = document.createElement('div');
        heart.classList.add('heart');
        heart.innerHTML = '💙';
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.animationDuration = (Math.random() * 2 + 3) + 's';
        document.body.appendChild(heart);

        setTimeout(() => heart.remove(), 5000);
      }, 300);
    }
  </script>
</body>
</html>
