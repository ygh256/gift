# gift
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>生日快乐</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: linear-gradient(135deg, #0c0c2e 0%, #1a1a3e 50%, #2d1b69 100%);
            color: white;
            font-family: 'Arial Rounded MT Bold', 'Helvetica Rounded', Arial, sans-serif;
            overflow: hidden;
            width: 100vw;
            height: 100vh;
            position: relative;
        }
        
        /* 星空背景 */
        .stars {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
        }
        
        /* 流星容器 */
        .meteors {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }
        
        /* 主内容容器 */
        .container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 2;
            padding: 20px;
        }
        
        /* 生日快乐文字 */
        .birthday-text {
            font-size: 5rem;
            text-align: center;
            margin-bottom: 30px;
            text-shadow: 
                0 0 10px #ff0080, 
                0 0 20px #ff0080, 
                0 0 30px #ff0080, 
                0 0 40px #ff00ff, 
                0 0 70px #ff00ff, 
                0 0 80px #ff00ff;
            animation: textGlow 2s ease-in-out infinite alternate;
            letter-spacing: 5px;
            line-height: 1.2;
            padding: 0 20px;
        }
        
        /* 文字动画 */
        @keyframes textGlow {
            0% {
                text-shadow: 
                    0 0 10px #ff0080, 
                    0 0 20px #ff0080, 
                    0 0 30px #ff0080, 
                    0 0 40px #ff00ff, 
                    0 0 70px #ff00ff, 
                    0 0 80px #ff00ff;
                transform: scale(1);
            }
            100% {
                text-shadow: 
                    0 0 20px #ff0080, 
                    0 0 30px #ff0080, 
                    0 0 40px #ff0080, 
                    0 0 50px #ff00ff, 
                    0 0 80px #ff00ff, 
                    0 0 90px #ff00ff;
                transform: scale(1.05);
            }
        }
        
        /* 祝福语容器 */
        .wishes-container {
            max-width: 90%;
            text-align: center;
            margin-top: 20px;
            position: relative;
            z-index: 3;
        }
        
        /* 祝福语 */
        .wishes {
            font-size: 1.8rem;
            text-align: center;
            line-height: 1.6;
            text-shadow: 0 0 10px rgba(255, 255, 255, 0.7);
            animation: fadeInOut 4s ease-in-out infinite;
            margin-bottom: 30px;
            padding: 0 20px;
        }
        
        @keyframes fadeInOut {
            0%, 100% { opacity: 0.7; }
            50% { opacity: 1; }
        }
        
        /* 装饰性元素 */
        .decorations {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-top: 20px;
            flex-wrap: wrap;
        }
        
        .decoration-item {
            width: 40px;
            height: 40px;
            background-color: #ff00ff;
            border-radius: 50%;
            opacity: 0.7;
            animation: bounce 2s ease-in-out infinite;
            box-shadow: 0 0 15px #ff00ff;
        }
        
        .decoration-item:nth-child(1) {
            background-color: #ff0080;
            animation-delay: 0s;
        }
        
        .decoration-item:nth-child(2) {
            background-color: #00ffff;
            animation-delay: 0.5s;
        }
        
        .decoration-item:nth-child(3) {
            background-color: #ffff00;
            animation-delay: 1s;
        }
        
        .decoration-item:nth-child(4) {
            background-color: #00ff80;
            animation-delay: 1.5s;
        }
        
        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }
        
        /* 横屏提示 */
        .orientation-message {
            display: none;
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.9);
            z-index: 100;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            font-size: 1.8rem;
            text-align: center;
            padding: 20px;
        }
        
        .orientation-message p {
            margin-bottom: 20px;
        }
        
        .orientation-message .rotate-icon {
            font-size: 4rem;
            animation: rotateAnimation 2s linear infinite;
            margin-bottom: 20px;
        }
        
        @keyframes rotateAnimation {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(90deg); }
        }
        
        /* 响应式调整 */
        @media (max-width: 768px) and (orientation: portrait) {
            .orientation-message {
                display: flex;
            }
            
            .birthday-text {
                font-size: 4rem;
            }
            
            .wishes {
                font-size: 1.5rem;
            }
        }
        
        @media (max-width: 768px) and (orientation: landscape) {
            .birthday-text {
                font-size: 4.5rem;
            }
            
            .container {
                padding: 10px;
            }
            
            .wishes {
                font-size: 1.6rem;
                margin-top: 10px;
            }
            
            .decoration-item {
                width: 30px;
                height: 30px;
            }
        }
        
        @media (max-width: 480px) and (orientation: landscape) {
            .birthday-text {
                font-size: 3.5rem;
                letter-spacing: 3px;
            }
            
            .wishes {
                font-size: 1.3rem;
            }
            
            .decorations {
                gap: 20px;
            }
            
            .decoration-item {
                width: 25px;
                height: 25px;
            }
        }
    </style>
</head>
<body>
    <!-- 星空背景 -->
    <div class="stars" id="stars"></div>
    
    <!-- 流星容器 -->
    <div class="meteors" id="meteors"></div>
    
    <!-- 主内容 -->
    <div class="container">
        <h1 class="birthday-text">生日快乐</h1>
        
        <div class="wishes-container">
            <div class="wishes" id="wishes">
                愿你的每个愿望都能实现，每一天都充满欢笑与阳光！
            </div>
            
            <div class="decorations">
                <div class="decoration-item"></div>
                <div class="decoration-item"></div>
                <div class="decoration-item"></div>
                <div class="decoration-item"></div>
            </div>
        </div>
    </div>
    
    <!-- 横屏提示 -->
    <div class="orientation-message">
        <div class="rotate-icon">↻</div>
        <p>请将手机横屏以获得最佳体验</p>
        <p>Happy Birthday!</p>
    </div>

    <script>
        // 创建星空背景
        function createStars() {
            const starsContainer = document.getElementById('stars');
            const starsCount = 200;
            
            for (let i = 0; i < starsCount; i++) {
                const star = document.createElement('div');
                star.style.position = 'absolute';
                star.style.width = Math.random() * 3 + 'px';
                star.style.height = star.style.width;
                star.style.backgroundColor = 'white';
                star.style.borderRadius = '50%';
                star.style.left = Math.random() * 100 + '%';
                star.style.top = Math.random() * 100 + '%';
                star.style.opacity = Math.random() * 0.8 + 0.2;
                star.style.boxShadow = '0 0 5px white';
                
                // 添加闪烁动画
                const duration = Math.random() * 5 + 3;
                star.style.animation = `twinkle ${duration}s infinite alternate`;
                
                starsContainer.appendChild(star);
            }
            
            // 添加闪烁动画关键帧
            const style = document.createElement('style');
            style.textContent = `
                @keyframes twinkle {
                    0% { opacity: 0.2; }
                    100% { opacity: 0.9; }
                }
            `;
            document.head.appendChild(style);
        }
        
        // 创建流星效果
        function createMeteors() {
            const meteorsContainer = document.getElementById('meteors');
            const meteorsCount = 12; // 增加流星数量
            
            for (let i = 0; i < meteorsCount; i++) {
                const meteor = document.createElement('div');
                meteor.style.position = 'absolute';
                
                // 随机流星长度
                const meteorLength = Math.random() * 80 + 50;
                meteor.style.width = meteorLength + 'px';
                meteor.style.height = '2px';
                
                // 随机流星颜色
                const colors = [
                    'rgba(255,255,255,1) 0%, rgba(255,255,255,0) 100%',
                    'rgba(255,0,255,1) 0%, rgba(255,0,255,0) 100%',
                    'rgba(0,255,255,1) 0%, rgba(0,255,255,0) 100%',
                    'rgba(255,255,0,1) 0%, rgba(255,255,0,0) 100%'
                ];
                const randomColor = colors[Math.floor(Math.random() * colors.length)];
                meteor.style.background = `linear-gradient(90deg, ${randomColor})`;
                
                meteor.style.borderRadius = '50%';
                meteor.style.left = Math.random() * 100 + '%';
                meteor.style.top = Math.random() * 100 + '%';
                meteor.style.opacity = '0';
                
                // 随机流星角度
                const angle = Math.random() * 30 - 45; // -45到-15度之间
                meteor.style.transform = `rotate(${angle}deg)`;
                
                // 添加流星动画
                const delay = Math.random() * 20;
                const duration = Math.random() * 2 + 1;
                meteor.style.animation = `meteorFall ${duration}s linear ${delay}s infinite`;
                
                meteorsContainer.appendChild(meteor);
            }
            
            // 添加流星动画关键帧
            const style = document.createElement('style');
            style.textContent = `
                @keyframes meteorFall {
                    0% {
                        opacity: 0;
                        transform: translateX(0) translateY(0) rotate(var(--angle, -45deg));
                    }
                    10% {
                        opacity: 1;
                    }
                    70% {
                        opacity: 1;
                    }
                    100% {
                        opacity: 0;
                        transform: translateX(400px) translateY(400px) rotate(var(--angle, -45deg));
                    }
                }
            `;
            document.head.appendChild(style);
        }
        
        // 动态祝福语
        const birthdayMessages = [
      "愿你天天开心，事事顺遂",
      "愿我们年年有今日，岁岁有今朝",
      "愿你的每个愿望都能实现，每一天都充满欢笑与阳光！",
      "新的一岁，愿所有美好如期而至，所有幸运不期而遇！",
      "祝你生日快乐，健康平安，心想事成，万事如意！",
        ];
        
        function changeMessage() {
            const messageElement = document.getElementById('wishes');
            let currentIndex = 0;
            
            setInterval(() => {
                currentIndex = (currentIndex + 1) % birthdayMessages.length;
                messageElement.style.opacity = 0;
                
                setTimeout(() => {
                    messageElement.textContent = birthdayMessages[currentIndex];
                    messageElement.style.opacity = 1;
                }, 500);
            }, 5000);
        }
        
        // 页面加载完成后初始化
        window.addEventListener('DOMContentLoaded', () => {
            createStars();
            createMeteors();
            changeMessage();
            
            // 检查横屏状态
            function checkOrientation() {
                const orientationMessage = document.querySelector('.orientation-message');
                if (window.innerWidth < window.innerHeight && window.innerWidth <= 768) {
                    // 竖屏且是移动设备
                    orientationMessage.style.display = 'flex';
                } else {
                    orientationMessage.style.display = 'none';
                }
            }
            
            checkOrientation();
            window.addEventListener('resize', checkOrientation);
            window.addEventListener('orientationchange', checkOrientation);
            
            // 添加点击屏幕增加流星效果
            document.body.addEventListener('click', function(e) {
                createClickMeteor(e.clientX, e.clientY);
            });
            
            // 触摸事件支持移动设备
            document.body.addEventListener('touchstart', function(e) {
                const touch = e.touches[0];
                createClickMeteor(touch.clientX, touch.clientY);
            });
        });
        
        // 点击屏幕生成流星
        function createClickMeteor(x, y) {
            const meteor = document.createElement('div');
            meteor.style.position = 'absolute';
            meteor.style.width = '100px';
            meteor.style.height = '3px';
            
            // 随机颜色
            const colors = ['#ff0080', '#ff00ff', '#00ffff', '#ffff00'];
            const randomColor = colors[Math.floor(Math.random() * colors.length)];
            meteor.style.background = `linear-gradient(90deg, ${randomColor}, transparent)`;
            
            meteor.style.borderRadius = '50%';
            meteor.style.left = x + 'px';
            meteor.style.top = y + 'px';
            meteor.style.opacity = '1';
            meteor.style.transform = 'rotate(-45deg)';
            meteor.style.zIndex = '10';
            
            document.querySelector('.meteors').appendChild(meteor);
            
            // 动画
            const animation = meteor.animate([
                { transform: 'translateX(0) translateY(0) rotate(-45deg)', opacity: 1 },
                { transform: 'translateX(300px) translateY(300px) rotate(-45deg)', opacity: 0 }
            ], {
                duration: 1000,
                easing: 'linear'
            });
            
            animation.onfinish = () => {
                meteor.remove();
            };
        }
    </script>
</body>
</html>
