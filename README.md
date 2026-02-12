<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>My Valentine 💖</title>

<style>
body{
    margin:0;
    font-family:'Segoe UI',sans-serif;
    background:#ffd6d6;
    overflow:hidden;
    text-align:center;
}

/* COMMON */
.page{
    display:none;
    height:100vh;
    justify-content:center;
    align-items:center;
    flex-direction:column;
}

.show{ display:flex; }

.box{
    background:white;
    padding:25px;
    border-radius:15px;
    box-shadow:0 10px 30px rgba(0,0,0,0.3);
}

/* LETTER */
.letter{
    width:180px;
    height:120px;
    background:#ff4d6d;
    color:white;
    display:flex;
    justify-content:center;
    align-items:center;
    border-radius:12px;
    cursor:pointer;
    font-size:18px;
    transform:perspective(600px) rotateX(10deg);
    box-shadow:0 10px 25px rgba(0,0,0,0.4);
}

/* BUTTONS */
button{
    padding:10px 25px;
    margin:10px;
    border:none;
    border-radius:8px;
    cursor:pointer;
    font-size:16px;
}

#yesBtn{ background:#ff4d6d;color:white; }
#noBtn{ background:#ccc; }

/* GIFTS */
.gift{
    background:white;
    padding:20px;
    border-radius:12px;
    margin:20px;
    cursor:pointer;
    box-shadow:0 10px 25px rgba(0,0,0,0.3);
}

/* PAPER */
.paper{
    background:#fffdf5;
    padding:25px;
    border-radius:12px;
    width:80%;
    max-width:500px;
    box-shadow:inset 0 0 10px rgba(0,0,0,0.15);
}

/* FALLING */
.fall{
    position:fixed;
    top:-50px;
    animation:fall linear infinite;
}

@keyframes fall{
    to{ transform:translateY(110vh); }
}
</style>
</head>

<body>

<!-- PAGE 1 -->
<div id="page1" class="page show">
    <h2>I have a message for you My dear 💌</h2>
    <div class="letter" onclick="openDialog()">Click me here</div>
</div>

<!-- PAGE 2 -->
<div id="page2" class="page">
    <div class="box">
        <h3>Will you be my Valentine? 💖</h3>
        <button id="yesBtn" onclick="yesClicked()">Yes</button>
        <button id="noBtn" onclick="noClicked()">No</button>
        <br><br><br><br>
        <img src="imag1.jpg" width="200">
    </div>
</div>

<!-- PAGE 3 -->
<div id="page3" class="page">
    <div class="box">
        <h3>Close your eyes and Feel the moment 💕</h3>
        <p><b>My Heart belongs to you</b></p>
    </div>
</div>

<!-- PAGE 4 -->
<div id="page4" class="page">
    <div class="gift" onclick="openGift1()">🎁 This is Gift 1</div>
</div>

<!-- PAGE 5 -->
<div id="page5" class="page">
    <div class="paper">
        En Viral Idukula Un Viral Kedakanu,<br>
        Nasungura Alavuku Irukki Nan Pudikanum 💞
    </div>
</div>

<!-- PAGE 6 -->
<div id="page6" class="page">
    <div class="gift" onclick="openGift2()">🎁 A Small Message for You my Love</div>
</div>

<!-- PAGE 7 -->
<div id="page7" class="page">
    <div class="paper">
        I Love You Manoj ❤️<br><br>
        Na una romba miss panra..<br>
        Enaku edhavadhu problem varumbothu,<br>
        ne first person ah irundhu adha solve pananum.<br><br>
        Na sad ah feel panalo, low ah feel panalo,<br>
        ne en kaiya pudichu <b>"Na iruka, ellame paathukla"</b> nu solanum.<br><br>
        Ena happy ah paathuko 💕<br>
        Happy Valentine’s Day 💖
    </div>
    <div class="gift" onclick="openGift3()">Move Next ➡️</div>
</div>

<!-- PAGE 8 -->
<div id="page8" class="page">
    <img id="memoryImg" width="300">
</div>

<audio id="song1" src="song1.mp3"></audio>
<audio id="song2" src="song2.mp3"></audio>
<audio id="bgSong" src="song1.mp3" loop></audio>

<script>
let noCount=0;
let images=["pics1.png","pics2.png","pics3.png","pics4.png","pics5.png"];
let imgIndex=0;

function showPage(id){
    document.querySelectorAll('.page').forEach(p=>p.classList.remove('show'));
    document.getElementById(id).classList.add('show');
}

function openDialog(){ showPage('page2'); }

function noClicked(){
    noCount++;
    if(noCount===1) alert("Mandaiya Odachuruva 😤");
    else{
        let btn=document.getElementById("noBtn");
        btn.style.position="absolute";
        btn.style.left=Math.random()*80+"%";
        btn.style.top=Math.random()*80+"%";
    }
}

function yesClicked(){
    showPage('page3');
    playSong('song1',0.3,30000);
    createFalls("🌹",30);
    setTimeout(()=>createFalls("🦋",15),3000);
    setTimeout(()=>showPage('page4'),30000);
}

function openGift1(){
    showPage('page5');
    playSong('song2',1,30000);
    setTimeout(()=>showPage('page6'),30000);
}

function openGift2(){
    document.getElementById("bgSong").volume=0.3;
    document.getElementById("bgSong").play();
    createFalls("🌸",20);
    createFalls("🦋",15);
    showPage('page7');
}

function openGift3(){
    showPage('page8');
    document.getElementById("bgSong").play();
    let img=document.getElementById("memoryImg");
    let interval=setInterval(()=>{
        img.src=images[imgIndex];
        imgIndex++;
        if(imgIndex===images.length){
            clearInterval(interval);
            document.body.innerHTML += `<h1 style="color:#ff4d6d;">I Love You ❤️</h1>`;
        }
    },2000);
}

function playSong(id,vol,time){
    let s=document.getElementById(id);
    s.volume=vol;
    s.play();
    setTimeout(()=>s.pause(),time);
}

function createFalls(symbol,count){
    for(let i=0;i<count;i++){
        let f=document.createElement("div");
        f.className="fall";
        f.innerText=symbol;
        f.style.left=Math.random()*100+"%";
        f.style.animationDuration=(3+Math.random()*5)+"s";
        document.body.appendChild(f);
    }
}
</script>

</body>
</html>
