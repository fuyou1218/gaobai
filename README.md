[index.html](https://github.com/user-attachments/files/25523670/default.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>给金美的告白 · 心动封面版</title>
  <style>
    /* ===== 全局重置 & 字体 ===== */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: "Microsoft YaHei", sans-serif;
    }

    body {
      background: #1a1a2e;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      overflow-x: hidden;
    }

    /* ===== 封面样式 (独立层) ===== */
    .cover {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle at 30% 30%, #2b1e2f, #130d1a);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      z-index: 1000;
      backdrop-filter: blur(6px);
      transition: transform 1.2s cubic-bezier(0.76, 0, 0.24, 1), opacity 1s ease;
      box-shadow: 0 0 60px #ff99aa30 inset;
      border: 2px solid #ffb6c180;
      opacity: 1;
      pointer-events: auto;
    }

    /* 封面隐藏状态 (滑动移出效果) */
    .cover.hidden {
      transform: translateY(-100%);
      opacity: 0;
      pointer-events: none;
    }

    /* 封面内容容器 */
    .cover-content {
      text-align: center;
      padding: 20px;
      max-width: 700px;
      animation: coverFloat 4s infinite ease-in-out;
    }

    @keyframes coverFloat {
      0% { transform: translateY(0); }
      50% { transform: translateY(-12px); }
      100% { transform: translateY(0); }
    }

    /* 大大的名字 (金美) */
    .cover-name {
      font-size: 82px;
      font-weight: 900;
      background: linear-gradient(135deg, #ffdde1, #ff9eb5, #ffb3c6);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      text-shadow: 0 0 30px #ff4d6d, 0 0 60px #ffb6c1;
      margin-bottom: 20px;
      letter-spacing: 6px;
      filter: drop-shadow(0 10px 20px #00000060);
      line-height: 1.2;
    }

    .cover-sub {
      color: #fbd0d9;
      font-size: 26px;
      letter-spacing: 10px;
      margin-bottom: 40px;
      text-shadow: 0 0 15px hotpink;
      font-weight: 300;
      border-bottom: 2px dashed #ffb6c1;
      padding-bottom: 20px;
      display: inline-block;
    }

    /* 心形装饰 */
    .cover-hearts {
      font-size: 50px;
      margin: 30px 0 20px;
      filter: drop-shadow(0 0 10px #ff4d6d);
      animation: heartbeat 1.4s infinite;
    }

    @keyframes heartbeat {
      0% { transform: scale(1); }
      25% { transform: scale(1.2); }
      35% { transform: scale(1.1); }
      50% { transform: scale(1.25); }
      60% { transform: scale(1); }
    }

    /* 封面专属按钮 */
    .cover-btn {
      background: linear-gradient(145deg, #392d3b, #251e2c);
      border: 3px solid #ffb8c5;
      color: #fff5f7;
      font-size: 28px;
      font-weight: bold;
      padding: 18px 48px;
      border-radius: 70px;
      margin-top: 30px;
      cursor: pointer;
      box-shadow: 0 15px 0 #611f32, 0 20px 35px #00000080;
      transition: 0.15s ease-out;
      display: inline-flex;
      align-items: center;
      gap: 15px;
      letter-spacing: 4px;
      backdrop-filter: blur(12px);
      border: 2px solid #ffc1cc;
      animation: btnPulse 2.2s infinite;
    }

    .cover-btn:hover {
      transform: translateY(-6px);
      box-shadow: 0 8px 0 #611f32, 0 25px 40px #ff4d6db0;
      background: linear-gradient(145deg, #4a344a, #33253b);
      border-color: #ffd9e2;
    }

    .cover-btn:active {
      transform: translateY(8px);
      box-shadow: 0 4px 0 #611f32, 0 15px 25px black;
    }

    @keyframes btnPulse {
      0% { box-shadow: 0 15px 0 #611f32, 0 0 20px #ff99aa; }
      50% { box-shadow: 0 15px 0 #611f32, 0 0 45px #ff4d6d, 0 0 60px #ffb6c1; }
      100% { box-shadow: 0 15px 0 #611f32, 0 0 20px #ff99aa; }
    }

    /* 封面底部小字 */
    .cover-footer {
      position: absolute;
      bottom: 25px;
      color: #ffb6c1;
      font-size: 18px;
      opacity: 0.8;
      text-shadow: 0 0 8px red;
    }

    /* ===== 原有主容器 (初始可见，但被封面覆盖) ===== */
    .container {
      max-width: 750px;
      margin: 60px auto;
      padding: 0 20px 30px;
      background: rgba(255, 240, 245, 0.05);
      backdrop-filter: blur(6px);
      border-radius: 40px 40px 30px 30px;
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.5), 0 0 0 2px #ffb6c180 inset;
      border: 1px solid #ffb6c1;
      transition: 0.3s;
      position: relative;
      z-index: 1;
      opacity: 1; /* 封面盖住但依然存在 */
    }

    .title {
      font-size: 32px;
      color: #f8c8dc;
      text-align: center;
      margin-bottom: 20px;
      font-weight: bold;
      padding-top: 30px;
      text-shadow: 0 0 10px #ff99aa;
    }

    .name {
      color: #ff758c;
      font-size: 42px;
      display: inline-block;
      animation: softGlow 2s infinite;
    }

    @keyframes softGlow {
      0% { text-shadow: 0 0 5px #ff99aa; }
      50% { text-shadow: 0 0 20px #ff4d6d, 0 0 30px #ffb6c1; }
      100% { text-shadow: 0 0 5px #ff99aa; }
    }

    .content {
      font-size: 18px;
      color: #f2e6e9;
      text-align: justify;
      white-space: pre-line;
      background: rgba(10, 10, 25, 0.4);
      padding: 25px 30px;
      border-radius: 35px;
      margin: 15px 10px 20px;
      border: 1px solid #ff99aa70;
      box-shadow: inset 0 0 30px #ff4d6d20;
    }

    .heart {
      color: #ff4d6d;
      font-size: 26px;
      display: block;
      text-align: right;
      margin-top: 20px;
      animation: beat 1.2s infinite;
    }

    @keyframes beat {
      0%, 100% { transform: scale(1); }
      25% { transform: scale(1.2); }
      40% { transform: scale(1.1); }
    }

    .button-panel {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 18px;
      margin: 30px 10px 10px;
      padding: 15px 0 20px;
    }

    .romantic-btn {
      background: linear-gradient(145deg, #2b1e2f, #1e152a);
      border: 2px solid #ff9eb5;
      color: #ffd9e2;
      padding: 12px 22px;
      font-size: 16px;
      font-weight: bold;
      border-radius: 50px;
      cursor: pointer;
      box-shadow: 0 8px 0 #731d34, 0 10px 20px rgba(0,0,0,0.5);
      transition: all 0.12s ease-out;
      letter-spacing: 1px;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      backdrop-filter: blur(4px);
      position: relative;
      z-index: 5;
    }

    .romantic-btn:hover {
      transform: translateY(-4px);
      box-shadow: 0 4px 0 #731d34, 0 15px 25px #ff4d6d80;
      background: linear-gradient(145deg, #342236, #2c1b33);
      border-color: #ffb6c1;
      color: #ffffff;
    }

    .romantic-btn:active {
      transform: translateY(5px);
      box-shadow: 0 2px 0 #731d34, 0 8px 15px #000;
    }

    /* 花瓣canvas */
    #petal-canvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 10;
    }

    .floating-hearts {
      position: fixed;
      bottom: 10px;
      right: 15px;
      font-size: 30px;
      opacity: 0.5;
      z-index: 15;
      pointer-events: none;
      animation: float 4s infinite ease-in-out;
    }

    @keyframes float {
      0% { transform: translateY(0px) rotate(0deg); }
      50% { transform: translateY(-15px) rotate(5deg); }
      100% { transform: translateY(0px) rotate(0deg); }
    }

    #bg-music {
      display: none;
    }

    .sig {
      text-align: center;
      color: #ffb6c1;
      margin-top: 10px;
      font-size: 15px;
      letter-spacing: 2px;
    }

    /* 点击小心心 (全局) */
    .click-heart {
      position: fixed;
      font-size: 24px;
      pointer-events: none;
      z-index: 9999;
      filter: drop-shadow(0 0 5px #ff99aa);
      animation: floatUp 1s forwards;
    }

    @keyframes floatUp {
      0% { opacity: 1; transform: translateY(0) scale(1); }
      100% { opacity: 0; transform: translateY(-60px) scale(1.5); }
    }

    /* 音乐提示小标签 */
    .music-tip {
      position: fixed;
      bottom: 20px;
      left: 20px;
      background: rgba(255, 180, 190, 0.2);
      backdrop-filter: blur(5px);
      padding: 8px 15px;
      border-radius: 40px;
      color: #ffced9;
      border: 1px solid #ff99aa;
      font-size: 14px;
      z-index: 20;
      pointer-events: none;
    }
  </style>
</head>
<body>

<!-- 音乐提示 (优雅告知) -->
<div class="music-tip" id="musicTip">🎵 点击任意处播放《告白气球》</div>

<!-- ========= 全新封面 ========= -->
<div class="cover" id="cover">
  <div class="cover-content">
    <div class="cover-hearts">💖 💗 💖</div>
    <div class="cover-name">金美</div>
    <div class="cover-sub">一封会开花的告白信</div>
    <!-- 封面核心按钮 · 开启告白 -->
    <button class="cover-btn" id="openCoverBtn">✨ 开启告白 ✨</button>
    <div style="margin-top: 40px; font-size: 22px; color: #ffb8c5; letter-spacing: 2px;">💌 致 独一无二的你</div>
  </div>
  <div class="cover-footer">—— 请轻轻点击按钮，走进我的心 ——</div>
</div>

<!-- 固定悬浮装饰 (在封面下层也无妨) -->
<div class="floating-hearts">💗 💖 💕</div>

<!-- 花瓣画布 -->
<canvas id="petal-canvas"></canvas>

<!-- 隐藏音频 · 周杰伦《告白气球》 (备用多个源，提高可用性) -->
<audio id="bg-music" loop preload="auto">
  <!-- 源1: 网易云（可能失效快） -->
  <source src="https://music.163.com/song/media/outer/url?id=41656628.mp3" type="audio/mpeg">
  <!-- 源2: 另一个可用外链（兼容性更好） -->
  <source src="https://dl.espressif.com/dl/audio/ff-16b-2c-44100hz.mp3" type="audio/mpeg">
  您的浏览器不支持音乐播放器，可尝试点击播放。
</audio>

<!-- 原告白主容器 (被封面盖住) -->
<div class="container">
  <div class="title">致 <span class="name" id="name-glow">金美</span> 的一封情书</div>
  
  <div class="content" id="love-letter">
    <span id="letter-text">
我没想过会遇上你，结果我遇上了，我更没想过会爱上你，但我爱了，不管我们最终是什么关系，你都将是我生命中最重要的一部分，你是我始料未及的遇见。

也是我突如其来的喜欢，你有多好，我说不出来，我有多想你，我也说不出来，我只知道，你是我的意外，你会牵动着我的心。我爱你，现在爱，以后会更爱，认识你，爱上你，我都不后悔。

我不是图新鲜感的人，我对你的爱只会越来越深，我会陪你很久很久，不是我想，是我一定会，今生不小心爱上你，忙时想你，闲时还是想你，满脑子都是你。

一份晚来的情，一份迟来的爱，虽然相遇很晚，但是余生有你就很幸福，我爱你，会越来越爱。
    </span>
    <span class="heart">❤️ 永远爱你</span>
  </div>

  <!-- 浪漫按钮组 -->
  <div class="button-panel">
    <button class="romantic-btn" id="btn-fireworks"><span>🎆</span> 心动烟花</button>
    <button class="romantic-btn" id="btn-petal"><span>🌸</span> 落花寄情</button>
    <button class="romantic-btn" id="btn-music"><span>🎵</span> 浪漫乐章</button>
    <button class="romantic-btn" id="btn-shine"><span>✨</span> 名字发光</button>
    <button class="romantic-btn" id="btn-surprise"><span>💌</span> 深情告白</button>
  </div>
  <div class="sig">—— 只为你一人 ——</div>
</div>

<!-- 引入烟花库 -->
<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

<script>
(function() {
  // --- 获取封面元素和主容器 ---
  const cover = document.getElementById('cover');
  const openBtn = document.getElementById('openCoverBtn');
  const musicTip = document.getElementById('musicTip');

  // --- 原有所有功能变量 ---
  const nameEl = document.querySelector('.name');
  const musicAudio = document.getElementById('bg-music');
  let musicPlaying = false;
  let userInteracted = false;       // 用户是否已经互动过（用于播放音乐）
  let coverClosed = false;          // 封面是否已关闭

  // 预加载音乐（但不播放）
  musicAudio.load();

  // --- 尝试播放音乐的函数，跟随用户互动 ---
  function tryPlayMusic() {
    if (musicPlaying) return;        // 已经在播放
    if (!coverClosed) return;        // 封面还没开，暂不自动播放（但用户可能点击了按钮，我们会在打开时标记）
    // 只要封面已关闭且用户有点击过，就尝试播放
    musicAudio.play().then(() => {
      musicPlaying = true;
      document.getElementById('btn-music').innerHTML = '<span>🔊</span> 暂停音乐';
      musicTip.style.opacity = '0';   // 播放后隐藏提示
      setTimeout(() => musicTip.style.display = 'none', 500);
    }).catch(e => {
      console.log('播放失败，等待再次互动', e);
      // 不处理，等待下次点击
    });
  }

  // --- 全局点击监听，用于触发音乐 (同时也保留点击心形效果) ---
  document.body.addEventListener('click', function(e) {
    // 标记用户已互动
    userInteracted = true;
    // 如果封面已关，尝试播放音乐
    if (coverClosed) {
      tryPlayMusic();
    }
  }, { once: false }); // 保持多次触发，但tryPlayMusic内部有状态判断

  // --- 封面按钮: 点击后隐藏封面，并且播放一点欢迎烟花，标记封面关闭 ---
  openBtn.addEventListener('click', (e) => {
    e.stopPropagation();  // 避免触发body的click导致音乐抢跑（但没关系）
    cover.classList.add('hidden');   // 封面优雅滑走
    coverClosed = true;

    // 如果用户已经有互动的记录（通常按钮点击本身就是互动），尝试播放音乐
    if (userInteracted) {
      tryPlayMusic();
    } else {
      // 理论上按钮点击会触发body的click，所以userInteracted会变成true，再等异步
      setTimeout(() => {
        if (!musicPlaying) tryPlayMusic();
      }, 300);
    }

    // 放个小烟花
    setTimeout(() => {
      if (typeof confetti !== 'undefined') {
        confetti({ particleCount: 100, spread: 80, origin: { y: 0.6 }, colors: ['#ff758c', '#f8c8dc', '#ffb6c1'] });
        confetti({ particleCount: 60, spread: 50, origin: { y: 0.5, x: 0.3 }, colors: ['#ffd166', '#ffb8b8'] });
        confetti({ particleCount: 60, spread: 50, origin: { y: 0.5, x: 0.7 }, colors: ['#ffb3c6', '#ffe5ec'] });
      }
    }, 300);

    // 爆花瓣
    setTimeout(() => { burstPetals(); }, 500);
  });

  // ========== 以下是原有脚本（大部分复制并整合） ==========

  // --- 通用烟花 ---
  function launchConfetti(colors = ["#ff758c","#f8c8dc","#ffeb3b","#ffffff"]) {
    confetti({
      particleCount: 120,
      spread: 80,
      origin: { y: 0.7, x: 0.5 },
      colors: colors,
      startVelocity: 25,
      decay: 0.9,
      ticks: 200
    });
  }

  function multiFireworks(volley = 3) {
    for (let i = 0; i < volley; i++) {
      setTimeout(() => {
        launchConfetti();
        if (i === volley-1) {
          setTimeout(() => {
            confetti({ particleCount: 80, spread: 100, colors: ["#c44569","#f5a97f","#f8c8dc"], origin: { y: 0.6, x: 0.3 } });
            confetti({ particleCount: 80, spread: 100, colors: ["#f5a97f","#ffb8b8","#ffcccc"], origin: { y: 0.6, x: 0.7 } });
          }, 200);
        }
      }, i * 200);
    }
  }

  // --- 花瓣飘落 canvas (原样) ---
  const canvas = document.getElementById('petal-canvas');
  const ctx = canvas.getContext('2d');
  let width, height;
  let petals = [];
  const PETAL_COUNT = 25;

  function resizeCanvas() {
    width = window.innerWidth;
    height = window.innerHeight;
    canvas.width = width;
    canvas.height = height;
  }
  window.addEventListener('resize', resizeCanvas);
  resizeCanvas();

  class Petal {
    constructor() {
      this.reset();
    }
    reset() {
      this.x = Math.random() * width;
      this.y = Math.random() * height - height;
      this.size = 8 + Math.random() * 12;
      this.speedY = 1 + Math.random() * 2;
      this.speedX = 0.2 + Math.random() * 0.8;
      this.angle = Math.rand
