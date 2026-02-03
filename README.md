# Gisellllle
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>For Giselle ✨</title>
    <style>
        :root {
            --gold: #d4af37;
            --pink: #ff4d6d;
        }

        /* Forces the 9:16 feel and prevents scrolling */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background: #fff0f3;
            font-family: 'Georgia', serif;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Background Sparkle Effect */
        #canvas {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: linear-gradient(180deg, #fff0f3 0%, #ffe4e8 100%);
            z-index: -1;
        }

        /* Tap to Start Overlay */
        #overlay {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: white;
            z-index: 100;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            transition: opacity 0.8s ease;
        }

        /* The Main 9:16 Mobile Container */
        .mobile-container {
            width: 90vw;
            height: 85vh; /* Fits 9:16 proportions on most phones */
            max-width: 400px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            align-items: center;
            padding: 20px;
            box-sizing: border-box;
            background: rgba(255, 255, 255, 0.8);
            backdrop-filter: blur(10px);
            border-radius: 30px;
            border: 2px solid var(--gold);
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            text-align: center;
        }

        /* Polaroid Frame */
        .polaroid {
            background: white;
            padding: 10px 10px 40px 10px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
            transform: rotate(-2deg);
            width: 100%;
            box-sizing: border-box;
        }

        .polaroid img {
            width: 100%;
            aspect-ratio: 3/4;
            object-fit: cover;
            border-radius: 2px;
        }

        .caption {
            font-family: 'Brush Script MT', cursive;
            font-size: 1.8rem;
            margin-top: 15px;
            color: #444;
        }

        .message-box h1 {
            color: var(--pink);
            font-size: 2rem;
            margin: 0;
        }

        /* Buttons */
        .btn-group {
            width: 100%;
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 10px;
        }

        .btn {
            flex: 1;
            max-width: 120px;
            padding: 15px 0;
            border-radius: 50px;
            border: none;
            font-weight: bold;
            font-size: 1.1rem;
            cursor: pointer;
            transition: 0.3s;
        }

        #yes { background: var(--pink); color: white; }
        #no { background: #eee; color: #999; }

        #timer-text {
            font-size: 0.8rem;
            color: var(--gold);
            font-weight: bold;
            letter-spacing: 1px;
        }

    </style>
</head>
<body onclick="playMagic()">

    <iframe id="music" width="0" height="0" src="https://www.youtube.com/embed/l74uPrL-M6g?enablejsapi=1" frameborder="0"></iframe>

    <div id="overlay">
        <div style="font-size: 60px; animation: heartbeat 1.5s infinite;">❤️</div>
        <p style="color: var(--gold); font-weight: bold;">FOR GISELLE</p>
        <p style="color: #ccc; font-size: 0.8rem;">Tap to open</p>
    </div>

    <div class="mobile-container">
        <div class="message-box">
            <h1>My Giselle</h1>
            <p style="color: #888; font-size: 0.9rem; margin-top: 5px;">The Architecture of My Heart</p>
        </div>

        <div class="polaroid">
            <img src="us.png" alt="Our Memory">
            <div class="caption">Forever & Always</div>
        </div>

        <div class="action-box">
            <p style="margin-bottom: 15px;">Will you be my Valentine? 💘</p>
            <div class="btn-group">
                <button class="btn" id="yes" onclick="celebrate()">Yes!</button>
                <button class="btn" id="no" onmouseover="dodge()" onclick="dodge()">No</button>
            </div>
            <div id="timer-text">SEATTLE IN: <span id="clock"></span></div>
        </div>
    </div>

    <script>
        function playMagic() {
            const over = document.getElementById('overlay');
            if(over.style.display !== 'none') {
                over.style.opacity = '0';
                setTimeout(() => over.style.display = 'none', 800);
                document.getElementById('music').src += "&autoplay=1";
            }
        }

        function dodge() {
            const btn = document.getElementById('no');
            btn.style.position = 'fixed';
            btn.style.left = Math.random() * (window.innerWidth - 100) + 'px';
            btn.style.top = Math.random() * (window.innerHeight - 50) + 'px';
        }

        function celebrate() {
            document.querySelector('.mobile-container').innerHTML = `
                <div style="display:flex; flex-direction:column; justify-content:center; height:100%;">
                    <h1 style="color:var(--pink); font-size: 3rem;">YAY! 🥰</h1>
                    <p style="font-size: 1.2rem;">You've made me the happiest person alive!</p>
                    <div style="font-size: 60px; margin: 20px;">🌹🏙️✈️</div>
                    <p style="color:var(--gold); font-weight:bold;">I love you, Giselle!</p>
                </div>
            `;
            setInterval(spawnHeart, 200);
        }

        // Heart animation
        function spawnHeart() {
            const h = document.createElement('div');
            h.innerHTML = '❤️';
            h.style.position = 'fixed';
            h.style.left = Math.random() * 100 + 'vw';
            h.style.bottom = '-20px';
            h.style.fontSize = (Math.random() * 20 + 20) + 'px';
            h.style.transition = '4s linear';
            document.body.appendChild(h);
            setTimeout(() => {
                h.style.transform = `translateY(-110vh) rotate(${Math.random() * 360}deg)`;
                h.style.opacity = '0';
            }, 50);
            setTimeout(() => h.remove(), 4000);
        }

        // Countdown
        const vDay = new Date("Feb 14, 2026 00:00:00").getTime();
        setInterval(() => {
            const now = new Date().getTime();
            const diff = vDay - now;
            const d = Math.floor(diff / 86400000);
            const h = Math.floor((diff % 86400000) / 3600000);
            const m = Math.floor((diff % 3600000) / 60000);
            const s = Math.floor((diff % 60000) / 1000);
            document.getElementById("clock").innerHTML = `${d}d ${h}h ${m}m ${s}s`;
        }, 1000);
    </script>

    <style>
        @keyframes heartbeat {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
    </style>
</body>
</html>
