<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Buka Amplop Pink dengan Hati</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(135deg, #ffe6f0, #fff);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .envelope {
      position: relative;
      width: 340px;
      height: 240px;
      cursor: pointer;
      perspective: 1200px;
    }

    /* Flap segitiga */
    .flap {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 55%;
      background: #ff99bb;
      clip-path: polygon(0 0, 100% 0, 50% 100%);
      transform-origin: top;
      transition: transform 0.8s ease;
      z-index: 3;
      border: 2px solid #e75480;
    }

    /* Body amplop */
    .body {
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 75%;
      background: #ffb6c1;
      border: 2px solid #e75480;
      border-bottom-left-radius: 8px;
      border-bottom-right-radius: 8px;
      z-index: 1;
      display: flex;
      justify-content: center;
      align-items: flex-end;
      padding-bottom: 20px;
    }

    /* Nama di luar amplop */
    .recipient {
      font-size: 18px;
      font-weight: bold;
      color: #000000;
      text-align: center;
      text-shadow: 1px 1px 2px rgba(255,255,255,0.6);
    }

    /* Hati di tengah */
    .heart {
      position: absolute;
      top: 45%;
      left: 50%;
      transform: translate(-50%, -50%) scale(1);
      width: 40px;
      height: 36px;
      background: #e75480;
      clip-path: polygon(
        50% 0%,
        61% 11%,
        72% 0%,
        100% 29%,
        50% 100%,
        0% 29%,
        28% 0%,
        39% 11%
      );
      z-index: 4;
      animation: pulse 1.5s infinite;
    }

    @keyframes pulse {
      0%, 100% { transform: translate(-50%, -50%) scale(1); }
      50% { transform: translate(-50%, -50%) scale(1.2); }
    }

    /* Surat di dalam amplop */
    .letter {
      position: absolute;
      top: 30px;
      left: 0px;
      width: 320px;
      height: 300
      px;
      background: white;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      border-radius: 8px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
      transition: top 1s ease;
      z-index: 0;
      padding: 10px;
      text-align: center;
    }

    .letter img {
      max-width: 100%;
      max-height: 150px; /* lebih besar */
      border-radius: 8px;
      margin-bottom: 10px;
    }

    .letter p {
      font-size: 16px;
      color: #333;
      opacity: 0;
      transition: opacity 1s ease;
    }

    /* Efek buka */
    .open .flap {
      transform: rotateX(-180deg);
    }

    .open .letter {
      top: -160px;
      z-index: 5;
    }

    .open .letter p {
      opacity: 1;
      transition-delay: 0.5s;
    }

    /* Teks hint */
    .hint {
      margin-top: 20px;
      font-size: 18px;
      color: #e75480;
      animation: blink 1.2s infinite;
    }

    @keyframes blink {
      0%, 50%, 100% { opacity: 1; }
      25%, 75% { opacity: 0.3; }
    }
  </style>
</head>
<body>
  <div class="envelope" id="envelope" onclick="openEnvelope()">
    <div class="flap"></div>
    <div class="body">
      <div class="recipient">Ramdanul Arifin<br>
    Babakan Caringin</div>
    </div>
    <div class="heart"></div>
    <div class="letter">
      <img src="gambar/terimakasih.jfif" alt="Ucapan Terima Kasih">
      <p>Selamat atas pernikahannya Sinta & Iwang <br> semoga senantiasa di berikan keberkahan <br>serta menjadi keluarga yang Sakinah Mawadah Warohmah.. amiiin🤲🏻 <br> <strong>maaf ya gak bisa datang untuk amplop nya lewat online aja🙏🏻 hehe</strong></p>
    </div>
  </div>

  <div class="hint">👉 Klik untuk membuka amplop</div>

  <!-- Suara buka kertas -->
  <audio id="paperSound" preload="auto">
    <source src="https://www.soundjay.com/misc/sounds/page-flip-01a.mp3" type="audio/mpeg">
    Browser Anda tidak mendukung audio.
  </audio>

  <script>
    let opened = false;
    function openEnvelope() {
      const envelope = document.getElementById("envelope");
      const sound = document.getElementById("paperSound");
      
      if (!opened) {
        envelope.classList.add("open");
        sound.currentTime = 0;
        sound.play();
        opened = true;
      } else {
        envelope.classList.remove("open");
        opened = false;
      }
    }
  </script>
</body>
</html>

