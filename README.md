<!-- Поставьте этот блок в тело вашей страницы -->
<style>
  :root {
    --bg1: #0f172a;
    --bg2: #071224;
    --card-bg: rgba(255,255,255,0.04);
    --card-bg-dark: rgba(255,255,255,0.03);
    --accent: #36BCF7;
    --glass: rgba(255,255,255,0.06);
    --glass-border: rgba(255,255,255,0.06);
    --radius: 16px;
    color-scheme: dark;
  }

  [data-theme="light"] {
    --bg1: #f6f8fb;
    --bg2: #e8eefb;
    --card-bg: rgba(0,0,0,0.04);
    --card-bg-dark: rgba(0,0,0,0.03);
    --accent: #0366d6;
    --glass: rgba(0,0,0,0.04);
    --glass-border: rgba(0,0,0,0.06);
    color-scheme: light;
  }

  html,body{
    height:100%;
    margin:0;
    font-family: Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    background: linear-gradient(120deg, var(--bg1), var(--bg2));
    -webkit-font-smoothing:antialiased;
    -moz-osx-font-smoothing:grayscale;
  }

  .profile-wrap{
    min-height:100vh;
    display:flex;
    align-items:center;
    justify-content:center;
    padding:40px;
    box-sizing:border-box;
    position:relative;
    overflow:hidden;
  }

  /* subtle animated shapes */
  .bg-shape {
    position:absolute;
    width:700px;
    height:700px;
    border-radius:50%;
    filter: blur(80px);
    opacity:0.12;
    transform: translate3d(0,0,0);
    animation: float 10s ease-in-out infinite;
  }
  .bg-shape.s1 { background: linear-gradient(90deg, rgba(54,188,247,0.3), rgba(54,188,247,0)); top:-200px; left:-200px; }
  .bg-shape.s2 { background: linear-gradient(90deg, rgba(103,124,255,0.25), rgba(103,124,255,0)); bottom:-240px; right:-160px; animation-duration:14s; }

  @keyframes float {
    0% { transform: translateY(0) rotate(0deg); }
    50% { transform: translateY(18px) rotate(10deg); }
    100% { transform: translateY(0) rotate(0deg); }
  }

  .card {
    position:relative;
    z-index:5;
    max-width:880px;
    width:100%;
    border-radius:var(--radius);
    padding:28px;
    box-shadow: 0 10px 30px rgba(2,6,23,0.6);
    background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
    border: 1px solid var(--glass-border);
    backdrop-filter: blur(6px) saturate(120%);
  }

  .top {
    display:flex;
    gap:18px;
    align-items:center;
  }

  .avatar {
    width:86px;
    height:86px;
    border-radius:12px;
    background: linear-gradient(135deg, rgba(255,255,255,0.03), rgba(255,255,255,0.01));
    display:flex;
    align-items:center;
    justify-content:center;
    font-weight:700;
    font-size:28px;
    color:var(--accent);
    border:1px solid rgba(255,255,255,0.04);
    box-shadow: 0 6px 18px rgba(2,6,23,0.5);
  }

  .titles {
    flex:1;
  }

  .name {
    font-size:20px;
    font-weight:700;
    margin:0;
    color:var(--accent);
    display:flex;
    gap:10px;
    align-items:center;
  }

  .subtitle {
    margin:4px 0 0 0;
    font-size:14px;
    color: #9aa6b2;
  }

  /* typing */
  .typing {
    margin-top:12px;
    font-family: "Fira Code", monospace;
    font-size:18px;
    min-height:28px;
    color: #e6eef7;
  }
  .cursor {
    display:inline-block;
    width:10px;
    height:22px;
    margin-left:6px;
    background:var(--accent);
    animation: blink 1s steps(2,end) infinite;
    vertical-align:middle;
  }
  @keyframes blink { 50% { opacity:0 } }

  .badges {
    margin-top:14px;
    display:flex;
    gap:8px;
    flex-wrap:wrap;
    align-items:center;
  }
  .badge {
    display:inline-flex;
    align-items:center;
    gap:8px;
    padding:8px 12px;
    border-radius:999px;
    background:var(--glass);
    font-size:13px;
    color:#e6eef7;
    border:1px solid rgba(255,255,255,0.03);
    transform:translateY(0);
    transition:transform .22s ease, box-shadow .22s ease;
    cursor:default;
  }
  .badge:hover { transform: translateY(-6px); box-shadow: 0 8px 22px rgba(2,6,23,0.5); }

  .actions {
    margin-top:18px;
    display:flex;
    gap:12px;
    align-items:center;
  }

  .btn {
    padding:10px 14px;
    border-radius:10px;
    border: none;
    cursor:pointer;
    font-weight:600;
    font-size:14px;
    background:linear-gradient(90deg,var(--accent), #6ad1ff);
    color:#021223;
    box-shadow: 0 6px 18px rgba(54,188,247,0.12);
    transition:transform .15s ease, box-shadow .15s ease;
  }
  .btn:active { transform: translateY(2px); }
  .btn.ghost {
    background:transparent;
    border:1px solid rgba(255,255,255,0.06);
    color:#cfefff;
  }

  .right-col {
    display:flex;
    gap:12px;
    align-items:center;
    margin-left:12px;
  }

  .stats {
    margin-top:18px;
    display:flex;
    gap:14px;
    flex-wrap:wrap;
  }
  .stat {
    padding:10px 12px;
    border-radius:10px;
    background:rgba(255,255,255,0.02);
    font-size:13px;
    color:#cfefff;
    border:1px solid rgba(255,255,255,0.02);
  }

  /* theme prompt banner */
  .theme-banner {
    position:fixed;
    left:16px;
    right:16px;
    bottom:24px;
    z-index:9999;
    display:flex;
    align-items:center;
    gap:12px;
    justify-content:space-between;
    padding:12px 16px;
    border-radius:12px;
    background: linear-gradient(90deg, rgba(0,0,0,0.45), rgba(0,0,0,0.25));
    color:#f3fbff;
    box-shadow: 0 12px 30px rgba(2,6,23,0.6);
    border:1px solid rgba(255,255,255,0.04);
  }
  .theme-banner .info { font-size:14px; color:#e6eef7; }
  .theme-banner button { margin-left:8px; }

  @media (max-width:720px){
    .top { flex-direction:column; align-items:flex-start; gap:10px; }
    .right-col { margin-left:0; }
    .card { padding:20px; }
  }

</style>

<div class="profile-wrap" id="profile">
  <div class="bg-shape s1"></div>
  <div class="bg-shape s2"></div>

  <div class="card" role="region" aria-label="Profile card">
    <div class="top">
      <div class="avatar" aria-hidden="true">Q</div>
      <div class="titles">
        <h1 class="name">Qynon <span style="font-size:12px;color:#9fbfe9;font-weight:600">Fullstack • DevOps</span></h1>
        <p class="subtitle">Data Engineer · Fullstack Developer · DevOps Enthusiast</p>

        <div class="typing" id="typing"></div>
      </div>

      <div class="right-col" aria-hidden="true">
        <!-- badges can be images or text -->
        <div class="badge"> <img src="https://img.shields.io/badge/Telegram-2CA5E0?style=flat-square&logo=telegram&logoColor=white" alt="" style="height:18px"/> </div>
        <div class="badge"> <img src="https://img.shields.io/badge/Vercel-000?style=flat-square&logo=vercel&logoColor=white" alt="" style="height:18px"/> </div>
        <div class="badge"> <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white" alt="" style="height:18px"/> </div>
      </div>
    </div>

    <div class="badges" aria-hidden="true">
      <!-- animated tech icons (uses skillicons) -->
      <img src="https://skillicons.dev/icons?i=ts,js,react,nextjs,tailwind,cpp,nodejs,git,vercel,vscode" height="36" alt="tech icons" style="filter:grayscale(0.05);opacity:0.95" />
      <span class="badge">Languages: Chinese · English · Russian</span>
      <span class="badge">Open Source · Web · Cloud</span>
    </div>

    <div class="actions">
      <button class="btn" id="moreInfoBtn" title="Перейти на qynon.site">Больше инфо</button>
      <button class="btn ghost" id="themeToggle">Переключить тему</button>
      <a class="btn" href="https://github.com/ChQynon" target="_blank" rel="noopener">GitHub</a>
    </div>

    <div class="stats" aria-hidden="true">
      <div class="stat">Tech: TypeScript · React · Next.js · Node.js · C++</div>
      <div class="stat">Motto: 掌控时间者，方能掌控天下</div>
      <div class="stat">Current: Learning & Building</div>
    </div>
  </div>
</div>

<!-- Theme banner (hidden by default) -->
<div id="themeBanner" class="theme-banner" style="display:none" role="region" aria-live="polite">
  <div class="info">
    Похоже, у вас светлая тема. Для лучшего контраста переключитесь на тёмную тему.
  </div>
  <div style="display:flex;align-items:center;">
    <button class="btn" id="switchToDark">Переключить на тёмную</button>
    <button class="btn ghost" id="dismissBanner">Закрыть</button>
  </div>
</div>

<script>
  // Simple typing effect (type + backspace, loop)
  (function(){
    const lines = [
      "Hi there, I'm Qynon.",
      "Fullstack Developer | DevOps Enthusiast | Vercel Lover",
      "I build web apps, help infra, and love optimizations."
    ];
    const el = document.getElementById('typing');
    const cursor = document.createElement('span');
    cursor.className = 'cursor';
    el.appendChild(cursor);

    let lineIndex = 0;
    let charIndex = 0;
    let forward = true;
    const typingSpeed = 40;
    const pauseAfter = 1400;

    function tick(){
      const current = lines[lineIndex];
      if(forward){
        charIndex++;
        el.childNodes[0] && el.childNodes[0].remove(); // remove old text node
        el.insertBefore(document.createTextNode(current.slice(0,charIndex)), cursor);
        if(charIndex >= current.length){
          forward = false;
          setTimeout(tick, pauseAfter);
          return;
        }
      } else {
        charIndex--;
        el.childNodes[0] && el.childNodes[0].remove();
        el.insertBefore(document.createTextNode(current.slice(0,charIndex)), cursor);
        if(charIndex <= 0){
          forward = true;
          lineIndex = (lineIndex + 1) % lines.length;
        }
      }
      setTimeout(tick, forward ? typingSpeed : 24);
    }
    tick();
  })();

  // More info button
  document.getElementById('moreInfoBtn').addEventListener('click', function(){
    window.open('https://qynon.site', '_blank', 'noopener');
  });

  // Theme handling: store in localStorage, detect prefers-color-scheme
  const root = document.documentElement;
  const stored = localStorage.getItem('qynon-theme');
  if(stored){
    root.setAttribute('data-theme', stored);
  } else {
    // set default from OS
    const prefersLight = window.matchMedia && window.matchMedia('(prefers-color-scheme: light)').matches;
    root.setAttribute('data-theme', prefersLight ? 'light' : 'dark');
  }

  function toggleTheme(){
    const cur = root.getAttribute('data-theme') === 'light' ? 'dark' : 'light';
    root.setAttribute('data-theme', cur);
    localStorage.setItem('qynon-theme', cur);
  }

  document.getElementById('themeToggle').addEventListener('click', toggleTheme);

  // Banner for users with light theme
  const themeBanner = document.getElementById('themeBanner');
  const dismissBtn = document.getElementById('dismissBanner');
  const switchToDark = document.getElementById('switchToDark');

  function maybeShowBanner(){
    const alreadyDismissed = localStorage.getItem('qynon-theme-banner-dismissed');
    const effectiveTheme = root.getAttribute('data-theme');
    if(effectiveTheme === 'light' && !alreadyDismissed){
      themeBanner.style.display = 'flex';
    } else {
      themeBanner.style.display = 'none';
    }
  }
  maybeShowBanner();

  dismissBtn.addEventListener('click', function(){
    themeBanner.style.display = 'none';
    localStorage.setItem('qynon-theme-banner-dismissed', '1');
  });

  switchToDark.addEventListener('click', function(){
    root.setAttribute('data-theme', 'dark');
    localStorage.setItem('qynon-theme', 'dark');
    themeBanner.style.display = 'none';
  });

  // Accessibility: hide banner after 12s if user didn't interact (failsafe)
  setTimeout(() => {
    if(themeBanner.style.display === 'flex') {
      themeBanner.style.opacity = 0.98;
    }
  }, 12000);

</script>
