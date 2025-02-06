# Index.html-.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Pages with Sounds</title>
    <style>
        body {
            background: linear-gradient(45deg, #ff7f50, #ff1493, #ff69b4, #f0e68c); 
            background-size: 400% 400%;
            animation: gradientAnimation 6s ease infinite;
          font-family: 'Arial', sans-serif;
      }
        @keyframes gradientAnimation {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        h1 {
            font-size: 3em;
            text-align: center;
            color: white;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
            animation: bounce 2s infinite;
        }
        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        button {
            padding: 15px 30px;
            font-size: 1.5em;
            background-color: rgba(255, 255, 255, 0.8);
            border: none;
            cursor: pointer;
            margin-top: 20px;
            display: block;
            margin-left: auto;
            margin-right: auto;
            border-radius: 10px;
            transition: transform 0.2s, box-shadow 0.2s;
        }
        button:hover {
            background-color: rgba(255, 255, 255, 1);
            box-shadow: 0px 0px 15px rgba(255, 255, 255, 0.6);
            transform: scale(1.1);
        }
        .page {
            display: none;
        }
        .page.active {
            display: block;
        }
        .sparkle {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            z-index: -1;
            background: url('https://media.giphy.com/media/3o7TKoOVESv0tkxOue/giphy.gif') center center no-repeat;
            background-size: cover;
        }
    </style>
</head>
<body>
    <div class="sparkle"></div>
    <!-- الصفحة الأولى: النجمة -->
    <div id="starPage" class="page active">
        <h1>⭐ اضغط على النجمة ⭐</h1>
        <button onclick="goToCatPage()">اضغط على النجمة</button>
    </div>
    <!-- الصفحة الثانية: القطة -->
    <div id="catPage" class="page">
        <h1>🐱 اضغط على القطة 🐱</h1>
        <button onclick="goToWolfPage()">اضغط على القطة</button>
        <button onclick="goToStartPage()">⬅️ العودة</button>
        <audio id="catSound" src="https://www.soundjay.com/button/beep-07.wav"></audio>
    </div>
    <!-- الصفحة الثالثة: الذئب -->
    <div id="wolfPage" class="page">
        <h1>🐺 اضغط على الذئب 🐺</h1>
        <button onclick="goToMonkeyPage()">اضغط على الذئب</button>
        <button onclick="goToCatPage()">⬅️ العودة</button>
        <audio id="wolfSound" src="https://www.soundjay.com/animal/wolf-howling-01.mp3"></audio>
    </div>
    <!-- الصفحة الرابعة: القرد -->
    <div id="monkeyPage" class="page">
        <h1>🐒 اضغط على القرد 🐒</h1>
        <button onclick="goToFinalPage()">اضغط على القرد</button>
        <button onclick="goToWolfPage()">⬅️ العودة</button>
        <audio id="monkeySound" src="https://www.soundjay.com/animal/monkey-01.mp3"></audio>
    </div>
    <!-- الصفحة الأخيرة: النهاية -->
    <div id="finalPage" class="page">
        <h1>💦💦💦 to someone 💦💦💦</h1>
        <button onclick="goToStartPage()">⬅️ اضغط للعودة للبداية</button>
    </div>
    <script>
        function playSound(soundId) {
            const sound = document.getElementById(soundId);
            sound.currentTime = 0; // إعادة الصوت للبداية
            sound.play();
        }
        function goToCatPage() {
            changePage('starPage', 'catPage');
            playSound('catSound');
        }
        function goToWolfPage() {
            changePage('catPage', 'wolfPage');
            playSound('wolfSound');
        }
        function goToMonkeyPage() {
            changePage('wolfPage', 'monkeyPage');
            playSound('monkeySound');
        }
        function goToFinalPage() {
            changePage('monkeyPage', 'finalPage');
        }
        function goToStartPage() {
            changePage('finalPage', 'starPage');
        }
        function changePage(currentPageId, nextPageId) {
            document.getElementById(currentPageId).classList.remove('active');
            document.getElementById(nextPageId).classList.add('active');
        }
    </script>
</body>
</html>
