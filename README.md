<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Team Carousel</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin: 20px;
      background: #f4f4f4;
    }
    .about-title {
      font-size: 32px;
      margin-bottom: 20px;
    }
    .carousel-container {
      position: relative;
      overflow: hidden;
      max-width: 600px;
      margin: auto;
    }
    .carousel-track {
      display: flex;
      transition: transform 0.5s ease;
    }
    .card {
      min-width: 100%;
      box-sizing: border-box;
    }
    .card img {
      width: 100%;
      border-radius: 8px;
    }
    .nav-arrow {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      font-size: 2em;
      background: rgba(0, 0, 0, 0.5);
      color: white;
      border: none;
      padding: 10px;
      cursor: pointer;
      z-index: 1;
    }
    .nav-arrow.left {
      left: 10px;
    }
    .nav-arrow.right {
      right: 10px;
    }
    .member-info {
      margin-top: 20px;
    }
    .member-name {
      font-size: 24px;
      margin: 0;
    }
    .member-role {
      color: gray;
    }
    .dots {
      display: flex;
      justify-content: center;
      margin-top: 15px;
    }
    .dot {
      width: 12px;
      height: 12px;
      border-radius: 50%;
      background: gray;
      margin: 0 5px;
      cursor: pointer;
    }
    .dot.active {
      background: black;
    }
  </style>
</head>
<body>
<h1 class="about-title">OUR TEAM</h1>
<div class="carousel-container">
  <button class="nav-arrow left">‹</button>
  <div class="carousel-track" id="carouselTrack">
    <div class="card" data-index="0">
      <img src="https://images.unsplash.com/photo-1573497019940-1c28c88b4f3e?q=80&w=3687&auto=format&fit=crop" alt="Team Member 1">
    </div>
    <div class="card" data-index="1">
      <img src="https://images.unsplash.com/photo-1568602471122-7832951cc4c5?q=80&w=3870&auto=format&fit=crop" alt="Team Member 2">
    </div>
    <div class="card" data-index="2">
      <img src="https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?w=900&auto=format&fit=crop&q=60" alt="Team Member 3">
    </div>
    <div class="card" data-index="3">
      <img src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=900&auto=format&fit=crop&q=60" alt="Team Member 4">
    </div>
    <div class="card" data-index="4">
      <img src="https://images.unsplash.com/photo-1655249481446-25d575f1c054?w=900&auto=format&fit=crop&q=60" alt="Team Member 5">
    </div>
    <div class="card" data-index="5">
      <img src="https://images.unsplash.com/photo-1519085360753-af0119f7cbe7?q=80&w=3687&auto=format&fit=crop" alt="Team Member 6">
    </div>
  </div>
  <button class="nav-arrow right">›</button>
</div>
<div class="member-info">
  <h2 class="member-name" id="memberName">David Kim</h2>
  <p class="member-role" id="memberRole">Founder</p>
</div>
<div class="dots">
  <div class="dot active" data-index="0"></div>
  <div class="dot" data-index="1"></div>
  <div class="dot" data-index="2"></div>
  <div class="dot" data-index="3"></div>
  <div class="dot" data-index="4"></div>
  <div class="dot" data-index="5"></div>
</div>
<script>
  const track = document.querySelector('.carousel-track');
  const cards = document.querySelectorAll('.card');
  const dots = document.querySelectorAll('.dot');
  const leftButton = document.querySelector('.nav-arrow.left');
  const rightButton = document.querySelector('.nav-arrow.right');
  const memberName = document.getElementById('memberName');
  const memberRole = document.getElementById('memberRole');

  const names = ['David Kim', 'Sarah Lee', 'Mike Johnson', 'Emily Stone', 'Alex Tan', 'Lisa Wu'];
  const roles = ['Founder', 'CTO', 'Designer', 'Marketing', 'Analyst', 'Developer'];

  let currentIndex = 0;

  function updateCarousel(index) {
    const offset = -index * 100;
    track.style.transform = `translateX(${offset}%)`;
    dots.forEach(dot => dot.classList.remove('active'));
    dots[index].classList.add('active');
    memberName.textContent = names[index];
    memberRole.textContent = roles[index];
  }

  leftButton.addEventListener('click', () => {
    currentIndex = (currentIndex - 1 + cards.length) % cards.length;
    updateCarousel(currentIndex);
  });

  rightButton.addEventListener('click', () => {
    currentIndex = (currentIndex + 1) % cards.length;
    updateCarousel(currentIndex);
  });

  dots.forEach(dot => {
    dot.addEventListener('click', () => {
      currentIndex = parseInt(dot.getAttribute('data-index'));
      updateCarousel(currentIndex);
    });
  });
</script>
</body>
</html>
