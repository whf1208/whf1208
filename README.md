<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday!</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            height: 100vh;
            background: linear-gradient(to right, #ff9a9e, #fad0c4);
            font-family: 'Arial', sans-serif;
            overflow: hidden;
        }
        .container {
            text-align: center;
            animation: fadeIn 2s ease-in-out;
        }
        @keyframes fadeIn {
            0% { opacity: 0; transform: scale(0.8); }
            100% { opacity: 1; transform: scale(1); }
        }
        h1 {
            font-size: 3rem;
            color: white;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
            margin: 20px 0;
        }
        canvas {
            display: block;
            margin: 0 auto;
        }
        .balloons {
            position: absolute;
            bottom: -150px;
            width: 100%;
            animation: floatUp 5s infinite;
        }
        .balloon {
            width: 50px;
            height: 70px;
            background-color: #FFD700;
            border-radius: 50% 50% 45% 45%;
            position: absolute;
            animation: moveBalloon 6s infinite;
        }
        .balloon:nth-child(2) { background-color: #FF69B4; animation-delay: 1s; }
        .balloon:nth-child(3) { background-color: #87CEEB; animation-delay: 2s; }
        .balloon:nth-child(4) { background-color: #32CD32; animation-delay: 3s; }
        .balloon:nth-child(5) { background-color: #FF4500; animation-delay: 4s; }

        @keyframes floatUp {
            0% { transform: translateY(100%); }
            100% { transform: translateY(-100%); }
        }

        @keyframes moveBalloon {
            0%, 100% { transform: translateX(0); }
            50% { transform: translateX(50px); }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🎉 Happy Birthday, Alice! 🎉</h1>
        <canvas id="cakeCanvas" width="400" height="300"></canvas>
        <div class="balloons">
            <div class="balloon" style="left: 10%;"></div>
            <div class="balloon" style="left: 30%;"></div>
            <div class="balloon" style="left: 50%;"></div>
            <div class="balloon" style="left: 70%;"></div>
            <div class="balloon" style="left: 90%;"></div>
        </div>
    </div>

    <script>
        // 蛋糕绘制逻辑
        function drawCake() {
            const canvas = document.getElementById('cakeCanvas');
            const ctx = canvas.getContext('2d');

            // 蛋糕底座
            ctx.fillStyle = '#D2691E'; // 巧克力色
            ctx.fillRect(100, 200, 200, 50); // 底部矩形

            // 蛋糕主体
            ctx.fillStyle = '#FFDAB9'; // 桃色
            ctx.fillRect(120, 100, 160, 100); // 上部矩形

            // 糖霜层
            ctx.fillStyle = '#FFF0F5'; // 淡粉色
            ctx.beginPath();
            ctx.moveTo(120, 100);
            ctx.lineTo(280, 100);
            ctx.bezierCurveTo(260, 130, 240, 130, 220, 100);
            ctx.bezierCurveTo(200, 130, 180, 130, 160, 100);
            ctx.bezierCurveTo(140, 130, 120, 130, 120, 100);
            ctx.closePath();
            ctx.fill();

            // 蜡烛
            for (let i = 0; i < 3; i++) {
                ctx.fillStyle = '#FFD700'; // 黄色
                ctx.fillRect(150 + i * 40, 60, 10, 40); // 蜡烛
                ctx.fillStyle = '#FF4500'; // 橙色火焰
                ctx.beginPath();
                ctx.arc(155 + i * 40, 60, 5, 0, Math.PI * 2); // 圆形火焰
                ctx.fill();
            }
        }

        // 调用画蛋糕的函数
        drawCake();
    </script>
</body>
</html>
