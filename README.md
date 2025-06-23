<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Confession</title>

  <!-- Google Fonts untuk page2 tetap bisa pakai Averta -->
  <link href="https://fonts.googleapis.com/css2?family=Averta+Standard:wght@400&display=swap" rel="stylesheet">

  <!-- Font Awesome -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">

  <style>
    /* import font Gidok */
    @font-face {
      font-family: 'Gidok';
      src: url('fonts/Gidok.ttf') format('truetype');
      font-weight: normal;
      font-style: normal;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      overflow: hidden;
      height: 100vh;
      font-family: 'Averta Standard', sans-serif;
    }

    /* halaman pertama pakai Gidok */
    .page1 {
      font-family: 'Gidok', cursive;
    }

    .page1, .page2 {
      width: 100%;
      min-height: 100vh;
      background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 100%);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      position: absolute;
      top: 0;
      left: 0;
      transition: transform 1s ease-in-out, opacity 1s ease;
      will-change: transform, opacity;
    }

    .page1.slide-up {
      transform: translateY(-100%);
      opacity: 0;
    }
    .page2 {
      display: none;
    }
    .page2.slide-in {
      display: flex !important;
      transform: translateY(100%);
      animation: slideIn 1s forwards;
    }
    @keyframes slideIn {
      to { transform: translateY(0); }
    }

    .hearts { position: absolute; width: 100%; height: 100%; pointer-events: none; z-index: 0; }
    .heart { position: absolute; width: 20px; height: 20px; background: rgba(255,255,255,0.3); transform: rotate(45deg); animation: float 15s linear infinite; }
    .heart:before, .heart:after { content: ''; width: 20px; height: 20px; background: rgba(255,255,255,0.3); border-radius:50%; position:absolute; }
    .heart:before { top:-10px; left:0; }
    .heart:after { top:0; left:-10px; }
    @keyframes float {
      0%   { transform:rotate(45deg) translateY(0) translateX(0); opacity:0; }
      10%  { opacity:0.3; }
      100%{ transform:rotate(45deg) translateY(-100vh) translateX(100vw); opacity:0; }
    }

    @keyframes bubbleBounce { 0%,100%{transform:translateY(0);} 50%{transform:translateY(-15px);} }
    @keyframes bubbleFloat { 0%{transform:translateY(0) scale(1);} 100%{transform:translateY(-20px) scale(1.05);} }

    .photo {
      position: absolute; width:90px; height:90px;
      background-size:cover; background-position:center;
      border-radius:10px; box-shadow:0 4px 12px rgba(0,0,0,0.2);
      z-index:1;
      animation: bubbleBounce 3s ease-in-out infinite, bubbleFloat 6s ease-in-out infinite;
    }

    .sender {
      position:absolute; top:50px;
      font-size:26px; color:#000; z-index:2;
    }
    .instruction-text {
      position:absolute; top:100px;
      font-size:18px; color:#000; z-index:2;
    }

    .envelope-container { cursor:pointer; z-index:2; }
    .envelope-container img {
      width:300px;
      transition:transform 0.3s ease, filter 0.3s ease;
      transform-origin: bottom;
    }
    .envelope-container:hover img {
      transform: scale(1.05) rotateX(25deg);
      filter: brightness(1.1);
    }

    .music-control {
      position:absolute; bottom:30px; right:30px; z-index:10;
      background:white; width:50px; height:50px; border-radius:50%;
      display:flex; justify-content:center; align-items:center;
      box-shadow:0 4px 10px rgba(0,0,0,0.1); cursor:pointer; border:1px solid #000;
    }
    .music-control:hover { transform: scale(1.1); }
    .music-control i { font-size:20px; color:#800000; }

    .page2-content {
      width:90%; max-width:800px; max-height:70vh; margin-top:120px;
      background-image:url('https://www.transparenttextures.com/patterns/cubes.png');
      padding:30px; border-radius:20px; overflow-y:auto;
      box-shadow:0 10px 30px rgba(0,0,0,0.1); border:2px solid #000; z-index:2;
      font-family: 'Averta Standard', sans-serif;
    }
    .letter-content { font-size:18px; line-height:1.8; color:#333; text-align:justify; }
    .signature { margin-top:40px; text-align:right; font-style:italic; font-size:20px; color:#800000; }
    .back-button {
      position:fixed; bottom:20px; left:50%; transform:translateX(-50%);
      background:#ff9a9e; padding:12px 24px; border-radius:30px;
      box-shadow:0 4px 10px rgba(0,0,0,0.15); cursor:pointer; z-index:10;
      font-size:18px; color:white; border:none; font-family:'Averta Standard',sans-serif;
    }
    .back-button:hover { background:#fad0c4; }
  </style>
</head>
<body>

  <div class="page1" id="page1">
    <div class="hearts" id="hearts1"></div>
    <img src="https://lh3.googleusercontent.com/d/1vt3Hp-ELrBoScyEazsv7prngI6tirRqW=w1000" class="photo" style="top: 40px; left: 40px; width: 120px; height: 120px; transform: rotate(90deg);">
<img src="https://lh3.googleusercontent.com/d/1YU8mr3Sfg9PDXr2-mCANpwufIq3id4EE=w1000" class="photo" style="top: 130px; right: 50px; width: 120px; height: 120px; transform: rotate(15deg);">
<img src="https://lh3.googleusercontent.com/d/1DzPHNrq6PzSK7UD54Im0mEBJqE7cWMuz=w1000" class="photo" style="bottom: 90px; left: 30px; width: 120px; height: 120px; transform: rotate(20deg);">
<img src="https://lh3.googleusercontent.com/d/1OvERUtQ5CVwKQb2SqLd3go7pcfMCR14v=w1000" class="photo" style="bottom: 50px; right: 70px; width: 120px; height: 120px; transform: rotate(-25deg);">

    <div class="sender">Ini dari Wika Ganteng </div>
    <div class="instruction-text">click below</div>
    <div class="envelope-container" id="envelopeContainer">
      <img src="https://lh3.googleusercontent.com/d/1hniWAam4XY5TKgY6GdgeSIeHlZlkcDGd=w1000" alt="Amplop Cinta" />
    </div>
    <div class="music-control" id="musicControl">
      <i class="fas fa-play" id="musicIcon"></i>
    </div>
  </div>

  <div class="page2" id="page2">
    <div class="hearts" id="hearts2"></div>
    <div class="page2-content">
      <div class="letter-content">
        <!-- isi surat tetap sama -->
         Retno...
Mungkin ini terdengar tiba-tiba,
tapi setiap pertemuan kita, sekecil apa pun itu,
meninggalkan jejak hangat yang tak pernah hilang dari pikiranku.

Aku masih ingat saat pertama melihatmu,
di tengah riuhnya pameran,
ada satu ketenangan yang entah bagaimana, hanya datang dari tatapanmu.
Sejak itu, entah kenapa, dunia terasa sedikit lebih indah setiap kali aku mengingat senyummu.

Aku bukan orang yang mudah jatuh hati,
tapi pada dirimu, aku tidak jatuh — aku terseret perlahan,
tanpa pernah tahu kapan mulai dan bagaimana bisa sedalam ini.

Aku menyukai caramu mendengarkan,
caramu tertawa,
dan bahkan caramu diam.
Kamu adalah perempuan pertama
yang dengan tulus aku ceritakan ke keluargaku,
bukan karena aku yakin kamu jodohku,
tapi karena aku berharap — kamu bisa jadi rumah yang kutuju di masa depan.

Aku tidak ingin memaksakan apa pun,
tidak meminta balasan,
aku hanya ingin kamu tahu
ada seseorang yang diam-diam mendoakanmu dalam setiap malamnya,
yang menjaga jarak bukan karena tak peduli,
tapi karena terlalu peduli dan tak ingin menyakitimu dengan harapan yang belum tentu kau inginkan.

Dan kini...
izinkan aku mengakhiri perasaan ini,
bukan karena aku ingin berhenti menyukaimu,
tapi karena aku ingin mencintaimu
dengan cara yang lebih diam — dengan fokus memperbaiki diriku sendiri.

Aku ingin berjalan lebih jauh,
bukan untuk membuat siapa pun menyesal,
tapi agar kelak,
aku siap menjadi tempat pulang yang pantas
untuk perempuan yang Allah pilihkan untukku.

Jika itu kamu, semoga hatimu menungguku.
Jika bukan, semoga doaku tetap menjagamu,
dari jauh, tanpa harus memiliki. "Sungguh na malu aku ngakuang ini, tp sering jari aku merariang kabarmu di media sosial. Kdg di Instagrammu, kadang ti repost Tiktokmu. Kdg jari aku bejari kabarmu ti Aurel.

Kalean rencanang su aku, lamon bisa saling sama kamu. Tujuan aku jelas, bkn mau ngajak pacaran doang yang ndak pasti, tapi ni ati yang beletiang.

Tau mo kamu, aku orang romantis sebetulnya, cuman kita dua belum tau dekat ja. Meskipun aku belum pernah pacaran waktu-waktu lalu, tetap aku belajar mo hormati perempuan, tau caranya ngerawat perempuan bareng halus.

Entah kamu kenapa, masalahmu apa, atau latar belakangmu bagaimana, sampai susah benarkah mo komunikasi.

Waktu kita belete soal aku pengen main ke Sumbawa, nda' becanda aku. Tapi su aku urung niatku.

Semoga kamu baike terus mo. Salam sehat juga buat keluarga kamu, Retno.

        <!-- dst -->
      </div>
      <div class="signature">- erdananirwikara</div>
    </div>
    <button class="back-button" id="backButton">Molah</button>
  </div>

  <audio id="backgroundMusic" loop>
    <source src="https://media1.vocaroo.com/mp3/1bFM3F3BSzFr" type="audio/mpeg">
  </audio>

  <script>
    const envelopeContainer = document.getElementById('envelopeContainer');
    const page1 = document.getElementById('page1');
    const page2 = document.getElementById('page2');
    const musicControl = document.getElementById('musicControl');
    const musicIcon = document.getElementById('musicIcon');
    const backgroundMusic = document.getElementById('backgroundMusic');
    const backButton = document.getElementById('backButton');
    let isMusicPlaying = false;

    envelopeContainer.addEventListener('click', () => {
      page1.classList.add('slide-up');
      page2.classList.add('slide-in');
      window.scrollTo(0, 0);
    });

    musicControl.addEventListener('click', () => {
      if (isMusicPlaying) {
        backgroundMusic.pause();
        musicIcon.classList.replace('fa-pause','fa-play');
      } else {
        backgroundMusic.play();
        musicIcon.classList.replace('fa-play','fa-pause');
      }
      isMusicPlaying = !isMusicPlaying;
    });

    backButton.addEventListener('click', () => {
      page2.classList.remove('slide-in');
      page1.classList.remove('slide-up');
      page2.style.display = 'none';
      page1.style.display = 'flex';
      backgroundMusic.currentTime = 0;
      if (isMusicPlaying) backgroundMusic.play();
    });

    function createHearts(id){
      const c = document.getElementById(id);
      for(let i=0;i<20;i++){
        const h = document.createElement('div');
        h.classList.add('heart');
        h.style.left = Math.random()*100+'vw';
        h.style.top = Math.random()*100+'vh';
        h.style.opacity = Math.random();
        h.style.transform = `rotate(45deg) scale(${Math.random()*0.5+0.5})`;
        h.style.animationDuration = Math.random()*10+10+'s';
        h.style.animationDelay = Math.random()*5+'s';
        c.appendChild(h);
      }
    }
    createHearts('hearts1');
    createHearts('hearts2');
  </script>
</body>
</html>
