# Gisellllle
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>For Giselle ✨</title>
    <style>
        /* This locks the screen into a vertical 9:16 phone view */
        * { box-sizing: border-box; }
        body, html {
            margin: 0; padding: 0; width: 100%; height: 100%;
            overflow: hidden; /* Prevents scrolling away from the card */
            background: #fff0f3;
            font-family: 'Georgia', serif;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Initial Tap Screen */
        #entrance {
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

        .heart-btn { font-size: 70px; cursor: pointer; animation: pulse 1.5s infinite; }
        @keyframes pulse { 0% {transform: scale(1);} 50% {transform: scale(1.1);} 100% {transform: scale(1);} }

        /* The 9:16 Container */
        .mobile-view {
            width: 90vw;
            height: 90vh; /* Scaled to fit perfectly on an iPhone screen */
            max-width: 380px;
            background: white;
            border-radius: 25px;
            border: 2px solid #d4af37; /* Gold border like your photo theme */
            padding: 20px;
            display: flex;
            flex-direction: column;
            justify-content: space-around;
            align-items: center;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            text-align: center;
        }

        .polaroid {
            background: white;
            padding: 10px 10px 40px 10px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
            transform: rotate(-2deg);
            width: 100%;
        }

        .polaroid img {
            width: 100%;
            border-radius: 5px;
            display: block;
        }

        .caption { font-family: 'Brush Script MT', cursive; font-size: 1.6rem; margin-top: 10px; color: #444; }

        .btn-group { display: flex; gap: 15px; width: 100%; justify-content: center; }
        .btn { padding: 12px 30px; border-radius: 50px; border: none; font-weight: bold; cursor: pointer; }
        #yes { background: #ff4d6d; color: white; }
        #no { background: #eee; color: #999; position: relative; }

        #timer { font-size: 0.8rem; color: #d4af37; font-weight: bold; letter-spacing: 1px; }
    </style>
</head>
<body onclick="startMagic()">

    <iframe id="music" width="0" height="0" src="https://www.youtube.com/embed/l74uPrL-M6g?enablejsapi=1" frameborder="0"></iframe>

    <div id="entrance">
        <div class="heart-btn">❤️</div>
        <p style="color: #d4af37; font-weight: bold;">FOR GISELLE</p>
    </div>

    <div class="mobile-view">
        <div>
            <h1 style="color: #ff4d6d; margin: 0;">My Giselle</h1>
            <p style="font-size: 0.8rem; color: #888;">The Architecture of My Heart</p>
        </div>

        <div class="polaroid">
            <img src="us.png" alt="Our Memory">
            <div class="caption">Forever & Always</div>
        </div>

        <div>
            <p style="margin-bottom: 15px;">Will you be my Valentine? 💘</p>
            <div class="btn-group">
                <button class="btn" id="yes" onclick="celebrate()">Yes!</button>
                <button class="btn" id="no" onmouseover="dodge()">No</button>
            </div>
            <div id="timer">SEATTLE IN: <span id="clock"></span></div>
        </div>
    </div>

    <script>
        function startMagic() {
            const over = document.getElementById('entrance');
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
            document.querySelector('.mobile-view').innerHTML = `
                <h1 style="color: #ff4d6d; font-size: 2.5rem;">YAY! 🥰</h1>
                <p>I love you to Seattle and back!</p>
                <div style="font-size: 50px;">🏙️✈️💖</div>
            `;
            setInterval(() => {
                const h = document.createElement('div');
                h.innerHTML = '❤️';
                h.style.position = 'fixed';
                h.style.left = Math.random() * 100 + 'vw';
                h.style.bottom = '0';
                h.style.fontSize = '25px';
                h.style.transition = '4s linear';
                document.body.appendChild(h);
                setTimeout(() => { h.style.transform = 'translateY(-110vh)'; h.style.opacity = '0'; }, 50);
                setTimeout(() => h.remove(), 4000);
            }, 200);
        }

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
</body>
</html>
