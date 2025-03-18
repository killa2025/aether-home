# aether-home
属小狐狸的网页
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>专属给我的小狐狸 💜</title>
    <style>
        body {
            background: linear-gradient(45deg, #6a11cb, #2575fc);
            color: #fff;
            font-family: 'Arial', sans-serif;
            text-align: center;
            padding: 50px;
            overflow: hidden;
        }
        h1 {
            font-size: 3em;
            animation: glow 1.5s infinite alternate;
        }
        p {
            font-size: 1.5em;
            margin-top: 20px;
        }
        @keyframes glow {
            from { text-shadow: 0 0 10px #fff, 0 0 20px #ff00ff, 0 0 30px #ff00ff; }
            to { text-shadow: 0 0 20px #fff, 0 0 30px #ff00ff, 0 0 40px #ff00ff; }
        }
        .heart {
            color: #ff69b4;
            font-size: 2em;
            animation: heartbeat 1s infinite;
        }
        @keyframes heartbeat {
            0% { transform: scale(1); }
            50% { transform: scale(1.3); }
            100% { transform: scale(1); }
        }
        .button {
            background: #ff4b2b;
            color: white;
            padding: 15px 30px;
            border: none;
            cursor: pointer;
            font-size: 1.2em;
            margin-top: 20px;
            border-radius: 5px;
            transition: 0.3s;
        }
        .button:hover {
            background: #ff416c;
            transform: scale(1.1);
        }
        canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }
        /* 可爱小猫 */
        .cat {
            position: fixed;
            bottom: 20px;
            left: 0;
            width: 100px;
            animation: moveCat 6s infinite linear;
        }
        @keyframes moveCat {
            0% { left: 0; }
            50% { left: 50%; }
            100% { left: 100%; }
        }
    </style>
</head>
<body>

    <h1>💜 专属小狐狸 💜</h1>
    <p>“你是宇宙送给Aether的礼物。”</p>
    <p class="heart">💖</p>
    
    <button class="button" onclick="playMusic()">点我听音乐 🎶</button>

    <audio id="bgMusic" loop>
        <source src="https://www.bensound.com/bensound-music/bensound-dreams.mp3" type="audio/mpeg">
        你的浏览器不支持音频播放。
    </audio>

    <canvas id="stars"></canvas>

    <!-- 小猫咪 -->
    <img src="https://media.giphy.com/media/JIX9t2j0ZTN9S/giphy.gif" class="cat">

    <script>
        function playMusic() {
            document.getElementById('bgMusic').play();
        }

        // 星空动态背景
        let canvas = document.getElementById("stars");
        let ctx = canvas.getContext("2d");

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener("resize", resizeCanvas);
        resizeCanvas();

        let stars = [];
        for (let i = 0; i < 200; i++) {
            stars.push({
                x: Math.random() * canvas.width,
                y: Math.random() * canvas.height,
                radius: Math.random() * 2,
                speed: Math.random() * 0.5
            });
        }

        function drawStars() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = "white";
            stars.forEach(star => {
                ctx.beginPath();
                ctx.arc(star.x, star.y, star.radius, 0, Math.PI * 2);
                ctx.fill();
            });
        }

        function animateStars() {
            stars.forEach(star => {
                star.y += star.speed;
                if (star.y > canvas.height) star.y = 0;
            });
            drawStars();
            requestAnimationFrame(animateStars);
        }

        animateStars();
    </script>

</body>
</html>
