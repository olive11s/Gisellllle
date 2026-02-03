# Gisellllle
<!giselle >
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For My Giselle 🌷</title>

<style>
html,body{
    margin:0;
    width:100%;
    height:100%;
    font-family:'Georgia',serif;
    overflow:hidden;
    background:black;
}

/* Background Video */
#bgVideo{
    position:fixed;
    top:0;left:0;
    width:100%;
    height:100%;
    object-fit:cover;
    z-index:-2;
}

/* Dark overlay for readability */
#overlay{
    position:fixed;
    inset:0;
    background:rgba(0,0,0,.45);
    z-index:-1;
}

/* Entrance */
#entrance{
    position:fixed;
    inset:0;
    background:white;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    z-index:999;
    transition:opacity 1s ease;
}

.heart{
    font-size:90px;
    animation:pulse 1.5s infinite;
    cursor:pointer;
}

@keyframes pulse{
    0%{transform:scale(1)}
    50%{transform:scale(1.15)}
    100%{transform:scale(1)}
}

/* Card */
.card{
    width:90vw;
    max-width:380px;
    height:85vh;
    background:rgba(255,255,255,.95);
    border-radius:30px;
    padding:25px;
    display:flex;
    flex-direction:column;
    justify-content:space-between;
    text-align:center;
    margin:auto;
    margin-top:5vh;
}

h1{color:#d63384;margin:0}

button{
    border:none;
    border-radius:50px;
    padding:15px;
    font-size:1.2rem;
    font-weight:bold;
    cursor:pointer;
}

#yes{background:#2a9d8f;color:white}
#no{background:#e63946;color:white;font-size:.9rem}

.sparkle{
    position:fixed;
    pointer-events:none;
    animation:fade 1s forwards;
}

@keyframes fade{
    to{opacity:0;transform:scale(0)}
}
</style>
</head>

<body>

<!-- BACKGROUND TULIP VIDEO -->
<iframe id="bgVideo"
src="https://www.youtube.com/embed/B0EYHFSCkNU?autoplay=1&mute=1&loop=1&playlist=B0EYHFSCkNU&controls=0&showinfo=0"
frameborder="0" allow="autoplay"></iframe>

<div id="overlay"></div>

<!-- MUSIC -->
<iframe id="music"
width="0" height="0"
src="https://www.youtube.com/embed/l74uPrL-M6g?enablejsapi=1"
allow="autoplay"></iframe>

<!-- ENTRANCE -->
<div id="entrance">
    <div class="heart" onclick="start()">❤️</div>
    <p style="color:#d63384;font-weight:bold;">FOR GISELLE</p>
</div>

<!-- MAIN -->
<div class="card" id="card">
    <div>
        <h1>My Giselle</h1>
        <p style="color:#777;">The Love of My Life</p>
    </div>

    <p style="font-size:1.2rem;">
        Will you be my Valentine? 💘
    </p>

    <div>
        <button id="yes" onclick="celebrate()">Yes ❤️</button><br><br>
        <button id="no" onclick="grow()">No</button>
    </div>

    <p style="font-size:.8rem;color:#d63384;">
        Forever starts with us 🌷
    </p>
</div>

<script>
let size=1.2;

function start(){
    document.getElementById("entrance").style.opacity=0;
    setTimeout(()=>document.getElementById("entrance").remove(),1000);
    document.getElementById("music").src+="&autoplay=1";
    if(navigator.vibrate) navigator.vibrate(50);
}

function grow(){
    size+=.3;
    const yes=document.getElementById("yes");
    yes.style.fontSize=size+"rem";
}

function celebrate(){
    document.getElementById("card").innerHTML=`
    <div style="height:100%;display:flex;flex-direction:column;justify-content:center;">
        <h1 style="font-size:3rem;">She Said Yes 🥹</h1>
        <p style="font-size:1.3rem;">Giselle, you are my forever.</p>
        <p style="font-style:italic;color:#777;">
        (Tap anywhere)</p>
    </div>`;
    setInterval(heartRain,200);
}

function heartRain(){
    const h=document.createElement("div");
    h.innerHTML="❤️";
    h.style.position="fixed";
    h.style.left=Math.random()*100+"vw";
    h.style.bottom="-50px";
    h.style.fontSize="24px";
    h.style.transition="4s linear";
    document.body.appendChild(h);
    setTimeout(()=>{
        h.style.transform="translateY(-120vh)";
        h.style.opacity=0;
    },50);
    setTimeout(()=>h.remove(),4000);
}

document.addEventListener("touchmove",e=>{
    const s=document.createElement("div");
    s.className="sparkle";
    s.innerHTML="✨";
    s.style.left=e.touches[0].pageX+"px";
    s.style.top=e.touches[0].pageY+"px";
    document.body.appendChild(s);
    setTimeout(()=>s.remove(),1000);
});
</script>

</body>
</html>
