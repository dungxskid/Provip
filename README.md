<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>dungxnogay's bio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            height: 100vh;
            width: 100vw;
            touch-action: none;
            position: relative;
        }
        
        .parallax-bg {
            position: absolute;
            width: 200%;
            height: 200%;
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            will-change: transform;
        }
        
        .bio-container {
            position: absolute;
            width: 90%;
            max-width: 500px;
            padding: 30px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
            backdrop-filter: blur(10px);
            text-align: center;
            transition: transform 0.1s ease-out;
            z-index: 10;
            will-change: transform;
        }
        
        .avatar {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            object-fit: cover;
            border: 5px solid rgba(255, 255, 255, 0.5);
            margin-bottom: 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        h1 {
            color: #333;
            margin-bottom: 10px;
            font-size: 24px;
        }
        
        p {
            color: #666;
            margin-bottom: 20px;
            line-height: 1.6;
        }
        
        .social-links {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 25px;
        }
        
        .social-links a {
            display: inline-block;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: #fff;
            display: flex;
            align-items: center;
            justify-content: center;
            text-decoration: none;
            color: white;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
        }
        
        .social-links a:hover {
            transform: translateY(-5px);
        }
        
        .bg-element {
            position: absolute;
            border-radius: 50%;
            opacity: 0.6;
            z-index: 1;
            will-change: transform;
        }
        
        .music-control {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 50px;
            height: 50px;
            background: rgba(255, 255, 255, 0.8);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 100;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            cursor: pointer;
        }
        
        .music-control i {
            font-size: 24px;
            color: #333;
        }
    </style>
    <!-- Thêm Font Awesome cho icon nhạc -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
</head>
<body>
    <div class="parallax-bg" id="parallaxBg"></div>
    
    <div class="bio-container" id="bio">
        <img src=https://cdn.discordapp.com/attachments/1335849309090091028/1369327049713520702/IMG_1468.jpg?ex=681d6ef1&is=681c1d71&hm=01011ff3003c12cc28aa402fb2cc42cf7387b1eaf0af8c85f3b4430ae439e1b3&" 
        alt="Avatar" class="avatar">
        <h1>hi,iam dungxnogay</h1>
        <p>not saygex as you as </p>
        <p>name,alias:Bui Tien Dung,[Kuri]</p>
        <p>age:12</p>
        <p>best skill in life:lazy :D</p>
<p>skill(code):Lua,python,Html</p>
<p>note:i learn code to desgin web,cheat roblox :D</p>
<p>note2:learn code is to easy</p>
        <div class="social-links">
            <a href="Dũng Bùi" style="background: #3b5998;"><i class="fab fa-facebook-f"></i></a>
            <a href="Iamkuri" style="background: #1da1f2;"><i class="fab fa-twitter"></i></a>
            <a href="dungxskid" style="background: #333;"><i class="fab fa-github"></i></a>
        </div>
    </div>

    <!-- Nút điều khiển nhạc -->
    <div class="music-control" id="musicControl">
        <i class="fas fa-music"></i>
    </div>

    <!-- Phần tử audio cho nhạc nền -->
    <audio id="bgMusic" loop>
        <source src="https://m.soundcloud.com/hyan3official/th-p-drill-t-do-mck-prod-gaz-2" type="audio/mpeg">
        Trình duyệt của bạn không hỗ trợ audio ;D.
    </audio>

    <script>
        const bio = document.getElementById('bio');
        const parallaxBg = document.getElementById('parallaxBg');
        const musicControl = document.getElementById('musicControl');
        const bgMusic = document.getElementById('bgMusic');
        let posX = window.innerWidth / 2 - bio.offsetWidth / 2;
        let posY = window.innerHeight / 2 - bio.offsetHeight / 2;
        let startX, startY;
        let bgX = 0, bgY = 0;
        let isMusicPlaying = false;
        
        // Vị trí ban đầu
        bio.style.left = posX + 'px';
        bio.style.top = posY + 'px';
        
        // Xử lý sự kiện cảm ứng
        bio.addEventListener('touchstart', function(e) {
            e.preventDefault();
            startX = e.touches[0].clientX - posX;
            startY = e.touches[0].clientY - posY;
        });
        
        bio.addEventListener('touchmove', function(e) {
            e.preventDefault();
            posX = e.touches[0].clientX - startX;
            posY = e.touches[0].clientY - startY;
            
            // Giới hạn di chuyển trong màn hình
            posX = Math.max(0, Math.min(posX, window.innerWidth - bio.offsetWidth));
            posY = Math.max(0, Math.min(posY, window.innerHeight - bio.offsetHeight));
            
            bio.style.left = posX + 'px';
            bio.style.top = posY + 'px';
            
            // Di chuyển nền ngược hướng (hiệu ứng parallax)
            const moveX = (window.innerWidth/2 - posX - bio.offsetWidth/2) * 0.1;
            const moveY = (window.innerHeight/2 - posY - bio.offsetHeight/2) * 0.1;
            
            parallaxBg.style.transform = `translate(${moveX}px, ${moveY}px)`;
            
            // Di chuyển các phần tử nền
            moveBgElements(moveX, moveY);
        });
        
        // Tạo các phần tử nền di chuyển
        const bgElements = [];
        function createBgElements() {
            const colors = ['#ff9a9e', '#fad0c4', '#fbc2eb', '#a6c1ee', '#a1c4fd'];
            for (let i = 0; i < 12; i++) {
                const el = document.createElement('div');
                el.className = 'bg-element';
                const size = Math.random() * 150 + 50;
                el.style.width = size + 'px';
                el.style.height = size + 'px';
                el.style.background = colors[Math.floor(Math.random() * colors.length)];
                el.style.left = Math.random() * window.innerWidth + 'px';
                el.style.top = Math.random() * window.innerHeight + 'px';
                document.body.appendChild(el);
                
                bgElements.push({
                    element: el,
                    baseX: parseFloat(el.style.left),
                    baseY: parseFloat(el.style.top),
                    speed: Math.random() * 0.2 + 0.1
                });
            }
        }
        
        function moveBgElements(moveX, moveY) {
            bgElements.forEach(item => {
                const newX = item.baseX + moveX * item.speed;
                const newY = item.baseY + moveY * item.speed;
                item.element.style.transform = `translate(${newX - item.baseX}px, ${newY - item.baseY}px)`;
            });
        }
        
        // Thêm hiệu ứng khi lắc điện thoại
        window.addEventListener('devicemotion', function(e) {
            const acceleration = e.accelerationIncludingGravity;
            const x = acceleration.x;
            const y = acceleration.y;
            
            // Tính toán độ nghiêng
            const tiltX = (x / 10) * 20;
            const tiltY = (y / 10) * 20;
            
            bio.style.transform = `rotateX(${tiltY}deg) rotateY(${-tiltX}deg)`;
        });
        
        // Điều khiển nhạc nền
        musicControl.addEventListener('click', function() {
            if (isMusicPlaying) {
                bgMusic.pause();
                musicControl.innerHTML = '<i class="fas fa-music"></i>';
            } else {
                bgMusic.play();
                musicControl.innerHTML = '<i class="fas fa-pause"></i>';
            }
            isMusicPlaying = !isMusicPlaying;
        });
        
        // Tự động bật nhạc (bị chặn trên nhiều trình duyệt do chính sách autoplay)
        document.addEventListener('click', function initAudio() {
            if (!isMusicPlaying) {
                bgMusic.volume = 0.3; // Giảm âm lượng
                bgMusic.play()
                    .then(() => {
                        isMusicPlaying = true;
                        musicControl.innerHTML = '<i class="fas fa-pause"></i>';
                    })
                    .catch(e => console.log('Autoplay bị chặn:', e));
                document.removeEventListener('click', initAudio);
            }
        }, { once: true });
        
        // Khởi tạo
        window.addEventListener('load', function() {
            createBgElements();
            
            // Đặt lại vị trí khi thay đổi kích thước màn hình
            window.addEventListener('resize', function() {
                posX = window.innerWidth / 2 - bio.offsetWidth / 2;
                posY = window.innerHeight / 2 - bio.offsetHeight / 2;
                bio.style.left = posX + 'px';
                bio.style.top = posY + 'px';
            });
        });
    </script>
</body>
</html>
