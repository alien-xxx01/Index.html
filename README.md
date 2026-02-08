<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Invitation for My Love</title>
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Playfair+Display:wght@400;700&family=Cormorant+Garamond:wght@300;400;600&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      min-height: 100vh;
      background: linear-gradient(135deg, #1a0a1a 0%, #2d1b2d 50%, #1a0a1a 100%);
      font-family: 'Cormorant Garamond', serif;
      overflow-x: hidden;
      position: relative;
    }

    /* Animated background particles */
    .bg-animation {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 0;
      overflow: hidden;
    }

    .floating-heart {
      position: absolute;
      font-size: 20px;
      opacity: 0.4;
      animation: float-up 12s infinite ease-in-out;
    }

    @keyframes float-up {
      0%, 100% { 
        transform: translateY(100vh) rotate(0deg) scale(0.5); 
        opacity: 0; 
      }
      10% { opacity: 0.4; }
      90% { opacity: 0.4; }
      100% { 
        transform: translateY(-100vh) rotate(360deg) scale(1.2); 
        opacity: 0; 
      }
    }

    /* Main container */
    .invitation-container {
      position: relative;
      z-index: 10;
      max-width: 800px;
      margin: 0 auto;
      padding: 40px 20px;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }

    /* Header with names */
    .header-section {
      text-align: center;
      margin-bottom: 40px;
      animation: fade-in-down 1.5s ease-out;
    }

    .names {
      font-family: 'Great Vibes', cursive;
      font-size: 4rem;
      color: #ffd700;
      text-shadow: 0 0 30px rgba(255, 215, 0, 0.5);
      margin-bottom: 10px;
      letter-spacing: 3px;
    }

    .ampersand {
      font-size: 3rem;
      color: #ff69b4;
      display: block;
      margin: 10px 0;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); opacity: 0.8; }
      50% { transform: scale(1.2); opacity: 1; }
    }

    /* Main card */
    .invitation-card {
      background: rgba(255, 255, 255, 0.05);
      backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 215, 0, 0.3);
      border-radius: 30px;
      padding: 50px 40px;
      text-align: center;
      box-shadow: 
        0 20px 60px rgba(0, 0, 0, 0.5),
        inset 0 1px 0 rgba(255, 255, 255, 0.1);
      animation: fade-in-up 1.5s ease-out 0.5s both;
      position: relative;
      overflow: hidden;
    }

    .invitation-card::before {
      content: '';
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: radial-gradient(circle, rgba(255, 215, 0, 0.1) 0%, transparent 70%);
      animation: rotate 20s linear infinite;
    }

    @keyframes rotate {
      from { transform: rotate(0deg); }
      to { transform: rotate(360deg); }
    }

    .card-content {
      position: relative;
      z-index: 2;
    }

    .invitation-title {
      font-family: 'Playfair Display', serif;
      font-size: 2.5rem;
      color: #fff;
      margin-bottom: 30px;
      text-transform: uppercase;
      letter-spacing: 5px;
      font-weight: 300;
    }

    .invitation-text {
      font-size: 1.3rem;
      color: #e0e0e0;
      line-height: 2;
      margin-bottom: 40px;
      font-weight: 300;
    }

    .highlight {
      color: #ffd700;
      font-weight: 600;
      font-size: 1.5rem;
      display: block;
      margin: 20px 0;
      text-shadow: 0 0 20px rgba(255, 215, 0, 0.4);
    }

    /* Date section */
    .date-section {
      margin: 40px 0;
      padding: 30px;
      background: rgba(255, 105, 180, 0.1);
      border-radius: 20px;
      border: 1px solid rgba(255, 105, 180, 0.3);
      animation: fade-in 2s ease-out 1s both;
    }

    .date-label {
      font-size: 1rem;
      color: #ff69b4;
      text-transform: uppercase;
      letter-spacing: 3px;
      margin-bottom: 15px;
    }

    .date-value {
      font-family: 'Playfair Display', serif;
      font-size: 2rem;
      color: #fff;
      margin-bottom: 10px;
    }

    .time-value {
      font-size: 1.5rem;
      color: #ffd700;
      font-family: 'Great Vibes', cursive;
    }

    /* Location */
    .location {
      margin: 30px 0;
      font-size: 1.2rem;
      color: #ccc;
      animation: fade-in 2s ease-out 1.5s both;
    }

    .location-icon {
      font-size: 2rem;
      margin-bottom: 10px;
      display: block;
    }

    /* RSVP Buttons */
    .rsvp-section {
      margin-top: 50px;
      animation: fade-in-up 2s ease-out 2s both;
    }

    .rsvp-text {
      font-size: 1.2rem;
      color: #ff69b4;
      margin-bottom: 30px;
      font-style: italic;
    }

    .button-group {
      display: flex;
      gap: 20px;
      justify-content: center;
      flex-wrap: wrap;
    }

    .rsvp-btn {
      padding: 18px 50px;
      font-size: 1.2rem;
      border: none;
      border-radius: 50px;
      cursor: pointer;
      font-family: 'Cormorant Garamond', serif;
      font-weight: 600;
      letter-spacing: 2px;
      transition: all 0.4s ease;
      text-transform: uppercase;
      position: relative;
      overflow: hidden;
    }

    .btn-accept {
      background: linear-gradient(45deg, #ff1493, #ff69b4);
      color: white;
      box-shadow: 0 10px 30px rgba(255, 20, 147, 0.4);
    }

    .btn-accept:hover {
      transform: translateY(-5px) scale(1.05);
      box-shadow: 0 15px 40px rgba(255, 20, 147, 0.6);
    }

    .btn-decline {
      background: transparent;
      color: #999;
      border: 2px solid #666;
    }

    .btn-decline:hover {
      border-color: #ff1493;
      color: #ff1493;
      transform: translateY(-3px);
    }

    /* Footer quote */
    .footer-quote {
      margin-top: 50px;
      font-family: 'Great Vibes', cursive;
      font-size: 1.8rem;
      color: #ffd700;
      opacity: 0.8;
      animation: fade-in 2s ease-out 2.5s both;
      text-align: center;
    }

    /* Animations */
    @keyframes fade-in-down {
      from { opacity: 0; transform: translateY(-50px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @keyframes fade-in-up {
      from { opacity: 0; transform: translateY(50px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @keyframes fade-in {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    /* Response Modal */
    .modal-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.95);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      opacity: 0;
      transition: opacity 0.5s ease;
    }

    .modal-overlay.active {
      display: flex;
      opacity: 1;
    }

    .modal-content {
      background: linear-gradient(135deg, #2d1b2d, #1a0a1a);
      padding: 60px;
      border-radius: 30px;
      border: 2px solid #ffd700;
      text-align: center;
      max-width: 500px;
      transform: scale(0.8);
      opacity: 0;
      transition: all 0.5s ease;
      box-shadow: 0 0 100px rgba(255, 215, 0, 0.3);
    }

    .modal-overlay.active .modal-content {
      transform: scale(1);
      opacity: 1;
    }

    .modal-title {
      font-family: 'Great Vibes', cursive;
      font-size: 3rem;
      color: #ffd700;
      margin-bottom: 20px;
    }

    .modal-text {
      font-size: 1.3rem;
      color: #fff;
      line-height: 1.8;
      margin-bottom: 30px;
    }

    .modal-hearts {
      font-size: 3rem;
      animation: bounce 1s infinite;
    }

    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-20px); }
    }

    /* Running away button effect */
    .btn-decline.running {
      position: fixed;
      transition: all 0.3s ease;
    }

    /* Responsive */
    @media (max-width: 600px) {
      .names { font-size: 2.5rem; }
      .invitation-title { font-size: 1.8rem; }
      .invitation-card { padding: 30px 20px; }
      .rsvp-btn { padding: 15px 35px; font-size: 1rem; }
    }
  </style>
</head>
<body>

  <!-- Background Animation -->
  <div class="bg-animation" id="bgAnimation"></div>

  <!-- Main Container -->
  <div class="invitation-container">
    
    <!-- Header -->
    <div class="header-section">
      <div class="names">
        <span id="name1">Your Name</span>
        <span class="ampersand">&</span>
        <span id="name2">Her Name</span>
      </div>
    </div>

    <!-- Invitation Card -->
    <div class="invitation-card">
      <div class="card-content">
        <h1 class="invitation-title">You're Invited</h1>
        
        <p class="invitation-text">
          To a special evening with<br>
          <span class="highlight">Dinner & Walk</span>
          <br><br>
          I would be honored if you would join me<br>
          for a romantic night under the stars
        </p>

        <!-- Date Section -->
        <div class="date-section">
          <div class="date-label">Save the Date</div>
          <div class="date-value" id="dateDisplay">Saturday, February 14</div>
          <div class="time-value" id="timeDisplay">8:00 PM</div>
        </div>

        <!-- Location -->
        <div class="location">
          <span class="location-icon">📍</span>
          <div id="locationText">Our Special Place</div>
        </div>
      </div>
    </div>

    <!-- RSVP Section -->
    <div class="rsvp-section">
      <p class="rsvp-text">Will you make this evening unforgettable?</p>
      <div class="button-group">
        <button class="rsvp-btn btn-accept" onclick="handleAccept()">
          Yes, I'd Love To
        </button>
        <button class="rsvp-btn btn-decline" id="declineBtn" onclick="handleDecline()">
          Maybe Later
        </button>
      </div>
    </div>

    <!-- Footer Quote -->
    <div class="footer-quote">
      "Every moment with you is a moment I treasure"
    </div>

  </div>

  <!-- Success Modal -->
  <div class="modal-overlay" id="successModal">
    <div class="modal-content">
      <div class="modal-title">Wonderful!</div>
      <div class="modal-text">
        I can't wait to see you tonight.<br>
        Prepare yourself for an evening<br>
        filled with love and surprises.<br><br>
        <span style="color: #ff69b4;">See you at 8:00 PM</span>
      </div>
      <div class="modal-hearts">💖 ✨ 💖</div>
    </div>
  </div>

  <!-- Decline Modal -->
  <div class="modal-overlay" id="declineModal">
    <div class="modal-content" style="border-color: #ff1493;">
      <div class="modal-title" style="color: #ff1493; font-size: 2.5rem;">Think Again...</div>
      <div class="modal-text">
        Are you sure you want to<br>
        miss this magical evening?<br><br>
        <span style="color: #ffd700;">My heart is waiting for you</span>
      </div>
      <div class="button-group" style="margin-top: 30px;">
        <button class="rsvp-btn btn-accept" onclick="changeToAccept()">
          Actually, Yes!
        </button>
      </div>
    </div>
  </div>

  <script>
    // Create floating hearts background
    function createFloatingHearts() {
      const container = document.getElementById('bgAnimation');
      const hearts = ['💖', '💕', '💗', '💝', '💘', '✨', '🌟', '💫'];
      
      for (let i = 0; i < 25; i++) {
        const heart = document.createElement('div');
        heart.className = 'floating-heart';
        heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
        heart.style.left = Math.random() * 100 + '%';
        heart.style.animationDelay = Math.random() * 12 + 's';
        heart.style.animationDuration = (10 + Math.random() * 8) + 's';
        heart.style.fontSize = (15 + Math.random() * 25) + 'px';
        container.appendChild(heart);
      }
    }

    // Set current date (next Saturday)
    function setDate() {
      const today = new Date();
      const nextSaturday = new Date();
      nextSaturday.setDate(today.getDate() + (6 - today.getDay() + 7) % 7);
      
      const options = { weekday: 'long', month: 'long', day: 'numeric' };
      document.getElementById('dateDisplay').textContent = 
        nextSaturday.toLocaleDateString('en-US', options);
    }

    // Handle Accept
    function handleAccept() {
      const modal = document.getElementById('successModal');
      modal.classList.add('active');
      createHeartExplosion();
    }

    // Handle Decline
    let declineCount = 0;
    function handleDecline() {
      declineCount++;
      const btn = document.getElementById('declineBtn');
      
      if (declineCount === 1) {
        // First click - show warning
        const modal = document.getElementById('declineModal');
        modal.classList.add('active');
      } else {
        // Button runs away
        btn.classList.add('running');
        const x = 50 + Math.random() * (window.innerWidth - 200);
        const y = 50 + Math.random() * (window.innerHeight - 100);
        btn.style.left = x + 'px';
        btn.style.top = y + 'px';
        btn.textContent = "Catch me if you can!";
      }
    }

    // Change to accept from decline modal
    function changeToAccept() {
      document.getElementById('declineModal').classList.remove('active');
      setTimeout(() => handleAccept(), 300);
    }

    // Close modal on background click
    document.querySelectorAll('.modal-overlay').forEach(overlay => {
      overlay.addEventListener('click', function(e) {
        if (e.target === this && this.id === 'declineModal') {
          this.classList.remove('active');
        }
      });
    });

    // Heart explosion effect
    function createHeartExplosion() {
      const hearts = ['💖', '💕', '💗', '💝', '💘', '✨', '🌟'];
      for (let i = 0; i < 50; i++) {
        setTimeout(() => {
          const heart = document.createElement('div');
          heart.style.position = 'fixed';
          heart.style.left = (window.innerWidth / 2) + 'px';
          heart.style.top = (window.innerHeight / 2) + 'px';
          heart.style.fontSize = (20 + Math.random() * 30) + 'px';
          heart.style.pointerEvents = 'none';
          heart.style.zIndex = '9999';
          heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
          
          const angle = Math.random() * Math.PI * 2;
          const velocity = 100 + Math.random() * 300;
          const tx = Math.cos(angle) * velocity;
          const ty = Math.sin(angle) * velocity;
          
          heart.style.transition = 'all 1.5s cubic-bezier(0.68, -0.55, 0.265, 1.55)';
          document.body.appendChild(heart);
          
          setTimeout(() => {
            heart.style.transform = `translate(${tx}px, ${ty}px) scale(0)`;
            heart.style.opacity = '0';
          }, 50);
          
          setTimeout(() => heart.remove(), 1500);
        }, i * 30);
      }
    }

    // Initialize
    createFloatingHearts();
    setDate();

    // Make decline button run away on hover after first click
    document.getElementById('declineBtn').addEventListener('mouseenter', function() {
      if (declineCount >= 1 && !this.classList.contains('running')) {
        this.classList.add('running');
        const x = 50 + Math.random() * (window.innerWidth - 200);
        const y = 50 + Math.random() * (window.innerHeight - 100);
        this.style.left = x + 'px';
        this.style.top = y + 'px';
      }
    });
  </script>

</body>
</html>
