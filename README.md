<!DOCTYPE html>
<html lang="ta">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Chlooooo 🎉</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 50%, #a1c4fd 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            text-align: center;
            overflow: hidden;
        }

        .music-btn {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.8);
            border: 2px solid #ff3366;
            color: #ff3366;
            padding: 10px 18px;
            border-radius: 30px;
            font-weight: bold;
            cursor: pointer;
            z-index: 100;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
        }
        .music-btn:hover {
            background: #ff3366;
            color: white;
        }

        .card-container {
            position: relative;
            width: 90%;
            max-width: 450px;
            min-height: 480px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .card {
            position: absolute;
            width: 100%;
            background: rgba(255, 255, 255, 0.92);
            padding: 30px 20px;
            border-radius: 25px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.15);
            backdrop-filter: blur(8px);
            opacity: 0;
            visibility: hidden;
            transform: scale(0.8) translateY(20px);
            transition: all 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
        }

        .card.active {
            opacity: 1;
            visibility: visible;
            transform: scale(1) translateY(0);
        }

        h1 {
            color: #ff3366;
            font-size: 2.2rem;
            margin-bottom: 15px;
        }

        .name {
            color: #6c5ce7;
            font-size: 1.8rem;
            font-weight: bold;
            margin-bottom: 20px;
        }

        p {
            color: #444;
            font-size: 1.15rem;
            line-height: 1.6;
            margin-bottom: 25px;
        }

        /* 📸 PHOTO GALLERY STYLES */
        .gallery-box {
            position: relative;
            width: 100%;
            height: 220px;
            border-radius: 15px;
            overflow: hidden;
            margin-bottom: 15px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.15);
            background: #f0f0f0;
        }

        .gallery-box img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 15px;
            display: none;
        }

        .gallery-box img.active-img {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        .gallery-controls {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }

        .gallery-btn {
            background: #6c5ce7;
            color: white;
            border: none;
            padding: 6px 15px;
            border-radius: 15px;
            cursor: pointer;
            font-weight: bold;
        }

        .gift-box {
            font-size: 4rem;
            cursor: pointer;
            animation: pulse 1.5s infinite;
            margin: 15px 0;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.15); }
            100% { transform: scale(1); }
        }

        .hidden-message {
            display: none;
            color: #d63031;
            font-weight: bold;
            font-size: 1.2rem;
            margin-top: 15px;
            animation: fadeIn 1s ease forwards;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .btn-group {
            display: flex;
            justify-content: space-between;
            gap: 10px;
            margin-top: 15px;
        }

        .btn {
            background: #ff3366;
            color: white;
            border: none;
            padding: 12px 22px;
            font-size: 1rem;
            border-radius: 25px;
            cursor: pointer;
            flex: 1;
            transition: all 0.2s;
            box-shadow: 0 5px 15px rgba(255, 51, 102, 0.3);
        }

        .btn:hover {
            background: #e02e5b;
            transform: translateY(-2px);
        }

        .btn-secondary {
            background: #6c5ce7;
            box-shadow: 0 5px 15px rgba(108, 92, 231, 0.3);
        }

        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            top: -10px;
            animation: fall 4s linear infinite;
            z-index: 1;
        }

        @keyframes fall {
            to { transform: translateY(100vh) rotate(360deg); }
        }
    </style>
</head>
<body>

    <audio id="bgMusic" loop>
        <source src="Kannana-Kanne.mp3" type="audio/mpeg">
    </audio>

    <button class="music-btn" onclick="toggleMusic()" id="musicBtn">🎵 Play Music</button>

    <div class="card-container">
        
        <!-- Page 1: Welcome -->
        <div class="card active" id="page1">
            <h1>🎉 Birthday Special! ✨</h1>
            <div class="name">Happy Birthday Chlooooo 🎂</div>
            <p>Unakkaga oru chinna surprise ready panni irukken! Keela irukkira button-a click pannu!</p>
            <button class="btn" onclick="nextPage(2)">Next Page ➔</button>
        </div>

        <!-- Page 2: Special Wish -->
        <div class="card" id="page2">
            <h1>🌟 Special Wish</h1>
            <p>Intha naal unakku romba santhoshathaiyum, unoda ellaa kanavugalum niraveruradhuku ennode manamaarndha vaazhthukkal! ❤️</p>
            <div class="btn-group">
                <button class="btn btn-secondary" onclick="nextPage(1)">⬅ Back</button>
                <button class="btn" onclick="nextPage(3)">See Memories 📸 ➔</button>
            </div>
        </div>

        <!-- Page 3: 📸 NEW PHOTO GALLERY -->
        <div class="card" id="page3">
            <h1>📸 Sweet Memories</h1>
            
            <div class="gallery-box">
                <!-- Inga unga photos link-a maathikonga -->
                <img src="hanuman-chromebook-wallpaper.jpg" class="gallery-img active-img" alt="Photo 1">
                <img src="thumb-1920-79608.jpg" class="gallery-img" alt="Photo 2">
                <img src="wp2604452.jpg" class="gallery-img" alt="Photo 3">
            </div>

            <div class="gallery-controls">
                <button class="gallery-btn" onclick="changePhoto(-1)">◀ Prev</button>
                <span id="photoCount" style="color: #666; font-weight: bold;">1 / 3</span>
                <button class="gallery-btn" onclick="changePhoto(1)">Next ▶</button>
            </div>

            <div class="btn-group">
                <button class="btn btn-secondary" onclick="nextPage(2)">⬅ Back</button>
                <button class="btn" onclick="nextPage(4)">Surprise Gift 🎁 ➔</button>
            </div>
        </div>

        <!-- Page 4: Gift Surprise -->
        <div class="card" id="page4">
            <h1>🎁 Tap the Gift Box!</h1>
            <p>Unakkana Secret Wish keela irukkura gift box ullae irukku, click panni paar!</p>
            <div class="gift-box" onclick="openGift()">🎁</div>
            <div class="hidden-message" id="secretWish">
                 Keep smiling always! Un sirippu dhaan unakku azhage! Unakku oru semma grand party wait pannudhu! 🥳🎂
            </div>
            <div class="btn-group" style="margin-top: 25px;">
                <button class="btn btn-secondary" onclick="nextPage(3)">⬅ Back</button>
                <button class="btn" onclick="nextPage(5)">Final Surprise 🎉</button>
            </div>
        </div>

        <!-- Page 5: Celebration Page -->
        <div class="card" id="page5">
            <h1>🥳 Grand Blast! 🎆</h1>
            <div class="name">Annapoorani Chlooooo</div>
            <p>Have an incredible year ahead full of love, success, and happiness! Enjoy your day to the fullest! 🎈✨</p>
            <button class="btn btn-secondary" onclick="nextPage(1)">🔄 Start Again</button>
        </div>

    </div>

    <script>
        // Page Navigation
        function nextPage(pageNumber) {
            const cards = document.querySelectorAll('.card');
            cards.forEach(card => card.classList.remove('active'));
            
            const targetCard = document.getElementById('page' + pageNumber);
            targetCard.classList.add('active');

            if(pageNumber === 5) {
                createConfetti();
            }
        }

        // 📸 GALLERY SCRIPT
        let currentPhotoIndex = 0;
        const photos = document.querySelectorAll('.gallery-img');
        const photoCount = document.getElementById('photoCount');

        function changePhoto(direction) {
            photos[currentPhotoIndex].classList.remove('active-img');
            
            currentPhotoIndex += direction;
            if (currentPhotoIndex < 0) {
                currentPhotoIndex = photos.length - 1;
            } else if (currentPhotoIndex >= photos.length) {
                currentPhotoIndex = 0;
            }
            
            photos[currentPhotoIndex].classList.add('active-img');
            photoCount.innerText = (currentPhotoIndex + 1) + " / " + photos.length;
        }

        // Surprise Gift Reveal
        function openGift() {
            const gift = document.querySelector('.gift-box');
            const secret = document.getElementById('secretWish');
            gift.style.transform = 'scale(1.3) rotate(15deg)';
            setTimeout(() => {
                gift.innerText = '🔓✨';
                secret.style.display = 'block';
            }, 300);
        }

        // Music Play / Pause Toggle
        const music = document.getElementById('bgMusic');
        const musicBtn = document.getElementById('musicBtn');
        let isPlaying = false;

        function toggleMusic() {
            if (isPlaying) {
                music.pause();
                musicBtn.innerText = '🎵 Play Music';
            } else {
                music.play();
                musicBtn.innerText = '⏸️ Pause Music';
            }
            isPlaying = !isPlaying;
        }

        // Confetti generator
        function createConfetti() {
            const colors = ['#ff3366', '#6c5ce7', '#00b894', '#fdcb6e', '#e17055'];
            for (let i = 0; i < 60; i++) {
                let confetti = document.createElement('div');
                confetti.classList.add('confetti');
                confetti.style.left = Math.random() * 100 + 'vw';
                confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                confetti.style.animationDuration = (Math.random() * 3 + 2) + 's';
                confetti.style.opacity = Math.random();
                document.body.appendChild(confetti);
            }
        }
    </script>
</body>
</html>
