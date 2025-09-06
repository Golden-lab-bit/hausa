<!DOCTYPE html>
<html lang="ha">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Shafin Farawa – HTML + CSS + JS</title>
  <meta name="description" content="Tsarin farawa na yanar gizo tare da HTML, CSS, da JavaScript." />
  <style>
    /* ====== Salo na Asali (CSS) ====== */
    :root{
      --bg: #0b1020;
      --panel: #121931;
      --text: #e9edf5;
      --muted:#9aa4c3;
      --brand:#6ea8fe;
      --brand-2:#9b8cff;
      --accent:#2ee6a6;
      --danger:#ff6b6b;
      --ring: rgba(110,168,254,.35);
      --radius: 16px;
      --shadow: 0 10px 25px rgba(0,0,0,.35);
    }

    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family: ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", "Liberation Sans", sans-serif;
      color:var(--text);
      background: radial-gradient(1200px 700px at 10% -10%, rgba(110,168,254,.1), transparent 60%),
                  radial-gradient(1000px 500px at 120% 10%, rgba(155,140,255,.12), transparent 60%),
                  var(--bg);
      line-height:1.6;
    }

    a{color:var(--brand);text-decoration:none}
    a:hover{text-decoration:underline}

    .container{width:min(1100px, 92vw); margin:0 auto}

    /* ====== Navbar ====== */
    .nav{
      position:sticky; top:0; z-index:50;
      backdrop-filter:saturate(140%) blur(8px);
      background:linear-gradient(180deg, rgba(11,16,32,.85), rgba(11,16,32,.35));
      border-bottom:1px solid rgba(255,255,255,.08);
    }
    .nav-inner{display:flex; align-items:center; justify-content:space-between; padding:14px 0}
    .brand{display:flex; align-items:center; gap:10px; font-weight:700; letter-spacing:.3px}
    .logo{width:36px; height:36px; border-radius:12px; background:linear-gradient(135deg,var(--brand),var(--brand-2)); box-shadow:0 6px 16px rgba(110,168,254,.45)}
    .nav-links{display:flex; gap:18px}
    .nav-links a{padding:8px 12px; border-radius:10px; color:var(--text)}
    .nav-links a:hover{background:rgba(255,255,255,.06)}

    .nav-cta{display:flex; align-items:center; gap:10px}
    .btn{appearance:none; border:0; cursor:pointer; font-weight:600; padding:10px 14px; border-radius:12px; transition:transform .06s ease, box-shadow .2s ease}
    .btn:active{transform:translateY(1px)}
    .btn.primary{background:linear-gradient(135deg,var(--brand),var(--brand-2)); color:#0b1020; box-shadow:0 10px 20px rgba(110,168,254,.35)}
    .btn.ghost{background:transparent; color:var(--text); border:1px solid rgba(255,255,255,.12)}

    .menu-btn{display:none}

    /* ====== Hero ====== */
    .hero{padding:64px 0 32px}
    .hero-grid{display:grid; grid-template-columns: 1.2fr .8fr; gap:28px; align-items:center}
    .badge{display:inline-flex; align-items:center; gap:8px; font-size:12px; color:var(--muted); background:rgba(255,255,255,.06); border:1px solid rgba(255,255,255,.12); border-radius:999px; padding:6px 10px}
    .title{font-size: clamp(28px, 4.6vw, 54px); line-height:1.08; margin:14px 0}
    .subtitle{color:var(--muted); max-width:60ch}
    .hero-actions{display:flex; gap:12px; margin-top:18px}

    .card{
      background:linear-gradient(180deg, rgba(255,255,255,.06), rgba(255,255,255,.02));
      border:1px solid rgba(255,255,255,.12);
      border-radius: var(--radius);
      padding:18px; box-shadow:var(--shadow)
    }
    .stat{display:flex; align-items:center; justify-content:space-between; padding:12px; border-radius:14px; background:rgba(255,255,255,.04); margin-bottom:10px}
    .stat b{font-size:24px}

    .phone{
      aspect-ratio: 9/16; border-radius: 28px; border:1px solid rgba(255,255,255,.15);
      padding:18px; background:linear-gradient(180deg,#0e1430,#090e1d); position:relative; overflow:hidden
    }
    .bubble{position:absolute; inset:auto auto 10% -10%; width:200px; height:200px; background:radial-gradient(circle at 30% 30%, rgba(46,230,166,.6), transparent 60%); filter:blur(28px)}

    /* ====== Abubuwan fasali ====== */
    .features{padding:6px 0 50px}
    .grid{display:grid; grid-template-columns: repeat(3, 1fr); gap:16px}
    .feature .icon{width:42px; height:42px; border-radius:12px; display:grid; place-items:center; background:rgba(110,168,254,.1); border:1px solid rgba(110,168,254,.25); margin-bottom:10px}
    .feature h3{margin:6px 0 6px}
    .muted{color:var(--muted)}

    /* ====== Katin Modal & Toast ====== */
    .overlay{position:fixed; inset:0; background:rgba(0,0,0,.5); display:none; place-items:center}
    .overlay.show{display:grid}
    .modal{width:min(520px, 92vw); background:var(--panel); border:1px solid rgba(255,255,255,.12); border-radius:18px; padding:18px; box-shadow:var(--shadow)}

    .toast{position:fixed; right:18px; bottom:18px; background:var(--panel); border:1px solid rgba(255,255,255,.12); border-radius:14px; padding:12px 14px; display:none}
    .toast.show{display:block}

    /* ====== Form ====== */
    form{display:grid; gap:12px}
    .field{display:grid; gap:6px}
    input, textarea{
      width:100%; padding:12px 12px; border-radius:12px;
      background:rgba(255,255,255,.06); border:1px solid rgba(255,255,255,.14);
      color:var(--text); outline:none; transition:border .2s, box-shadow .2s
    }
    input:focus, textarea:focus{border-color:var(--brand); box-shadow:0 0 0 4px var(--ring)}

    /* ====== Footer ====== */
    footer{padding:40px 0; color:var(--muted)}

    /* ====== Responsive ====== */
    @media (max-width: 900px){
      .hero-grid{grid-template-columns: 1fr}
      .grid{grid-template-columns: 1fr 1fr}
      .menu-btn{display:inline-flex}
      .nav-links{display:none}
      .drawer.show{transform:translateX(0)}
    }
    @media (max-width: 580px){
      .grid{grid-template-columns: 1fr}
      .title{font-size: clamp(26px, 8vw, 40px)}
    }

    /* ====== Drawer (Mobile Menu) ====== */
    .drawer{
      position:fixed; inset:0 0 0 auto; width:min(320px, 86vw);
      background:var(--panel); border-left:1px solid rgba(255,255,255,.1);
      transform:translateX(105%); transition:transform .25s ease; z-index:60; padding:18px
    }
    .drawer a{display:block; padding:12px 10px; border-radius:10px; color:var(--text)}
    .drawer a:hover{background:rgba(255,255,255,.06)}

    /* ====== Utility ====== */
    .sr{position:absolute; width:1px; height:1px; overflow:hidden; clip:rect(0 0 0 0)}
    .flex{display:flex}
    .gap-8{gap:8px}
    .gap-12{gap:12px}
    .space-between{justify-content:space-between}
    .center{display:grid; place-items:center}
  </style>
</head>
<body>
  <!-- ====== Navbar ====== -->
  <nav class="nav">
    <div class="container nav-inner">
      <div class="brand"><span class="logo" aria-hidden="true"></span> <span>Shafin Na – Demo</span></div>
      <div class="nav-links">
        <a href="#home">Gida</a>
        <a href="#fasali">Fasali</a>
        <a href="#sadaukarwa">Sadaukarwa</a>
      </div>
      <div class="nav-cta">
        <button id="themeBtn" class="btn ghost" aria-pressed="false">🌗 Dark/Light</button>
        <button id="openModal" class="btn primary">Buɗe Modal</button>
        <button id="openMenu" class="btn ghost menu-btn" aria-label="Buɗe Menu">☰</button>
      </div>
    </div>
  </nav>

  <!-- Drawer -->
  <aside id="drawer" class="drawer" aria-hidden="true">
    <div class="flex space-between" style="align-items:center; margin-bottom:10px">
      <strong>Menu</strong>
      <button id="closeMenu" class="btn ghost">✕</button>
    </div>
    <a href="#home">Gida</a>
    <a href="#fasali">Fasali</a>
    <a href="#sadaukarwa">Sadaukarwa</a>
  </aside>

  <!-- ====== Hero ====== -->
  <header id="home" class="hero container">
    <div class="hero-grid">
      <div>
        <span class="badge">⚡ Tsarin farawa • HTML + CSS + JS</span>
        <h1 class="title">Gina shafi cikin sauƙi. Salo na zamani, ƙananan lodi.</h1>
        <p class="subtitle">Wannan template ɗin ya haɗa abubuwan yau da kullum: menu na waya (drawer), canjin launi (dark/light), modal, toast, da fom mai duba bayanai.</p>
        <div class="hero-actions">
          <button class="btn primary" id="showToast">Nuna Saƙo</button>
          <a class="btn ghost" href="#fasali">Kalli fasali</a>
        </div>

        <div class="card" style="margin-top:16px">
          <div class="stat"><span>Masu amfani yau</span> <b id="counter">0</b></div>
          <div class="stat"><span>Lokaci (UTC)</span> <b id="clock">--:--:--</b></div>
        </div>
      </div>
      <div>
        <div class="phone card center">
          <div class="bubble" aria-hidden="true"></div>
          <div style="text-align:center">
            <h3>Mockup</h3>
            <p class="muted">Ana nuna salo da launuka a nan.</p>
          </div>
        </div>
      </div>
    </div>
  </header>

  <!-- ====== Features ====== -->
  <section id="fasali" class="features container">
    <h2>Fasali</h2>
    <div class="grid">
      <article class="feature card">
        <div class="icon">⚙️</div>
        <h3>Sauri & Tsabta</h3>
        <p class="muted">Babu wani ɗakin karatu; tsabta da sauƙin gyarawa.</p>
      </article>
      <article class="feature card">
        <div class="icon">📱</div>
        <h3>Responsive</h3>
        <p class="muted">Yana aiki kan waya, kwamfutar hannu, da kwamfuta.</p>
      </article>
      <article class="feature card">
        <div class="icon">🧩</div>
        <h3>Abubuwan Hulɗa</h3>
        <p class="muted">Modal, toast, drawer, da duba fom – duk a shirye.</p>
      </article>
    </div>
  </section>

  <!-- ====== Form ====== -->
  <section id="sadaukarwa" class="container" style="padding: 20px 0 50px">
    <div class="card">
      <h2>Tuntube Mu</h2>
      <form id="contactForm" novalidate>
        <div class="field">
          <label for="name">Suna</label>
          <input id="name" name="name" placeholder="Shigar da sunanka" required />
          <small class="muted" id="nameErr"></small>
        </div>
        <div class="field">
          <label for="email">Imel</label>
          <input id="email" name="email" type="email" placeholder="kai@example.com" required />
          <small class="muted" id="emailErr"></small>
        </div>
        <div class="field">
          <label for="msg">Saƙo</label>
          <textarea id="msg" name="msg" rows="4" placeholder="Me kake so ka faɗa?" required></textarea>
          <small class="muted" id="msgErr"></small>
        </div>
        <div class="flex gap-12">
          <button class="btn primary" type="submit">Aika</button>
          <button class="btn ghost" type="reset">Share</button>
        </div>
      </form>
    </div>
  </section>

  <!-- ====== Modal & Toast ====== -->
  <div id="overlay" class="overlay" aria-hidden="true" role="dialog" aria-modal="true">
    <div class="modal">
      <div class="flex space-between" style="align-items:center; margin-bottom:6px">
        <strong>Modal</strong>
        <button id="closeModal" class="btn ghost">✕</button>
      </div>
      <p>Sannu! Wannan shi ne <em>modal</em>. Za ka iya amfani da shi don sanarwa ko fom na gaggawa.</p>
    </div>
  </div>

  <div id="toast" class="toast" role="status">An adana bayanai ✅</div>

  <footer class="container">
    <small>© <span id="year"></span> Shafin Golden. Dukkan haƙƙi an kiyaye.</small>
  </footer>

  <script>
    // ====== JavaScript (JV) ======
    const $ = (sel) => document.querySelector(sel);

    // Clock & counter demo
    const clock = () => { const d = new Date(); $('#clock').textContent = d.toUTCString().split(' ')[4]; };
    setInterval(clock, 1000); clock();
    let n = 0; setInterval(()=>{ n = (n+1)%1000; $('#counter').textContent = n; }, 1500);

    // Theme toggle (dark/light) – ya adana a localStorage
    const themeBtn = $('#themeBtn');
    const root = document.documentElement;
    const light = {
      bg:'#f7f8fc', panel:'#ffffff', text:'#0b1020', muted:'#5b647c', brand:'#3b82f6', brand2:'#8b5cf6', accent:'#10b981'
    };
    const setTheme = (mode) => {
      const map = mode==='light'? light : null; // null => komawa defaults (dark)
      for(const k in light){ root.style.setProperty(`--${k}`, map? map[k] : ''); }
      localStorage.setItem('theme', mode);
      themeBtn.setAttribute('aria-pressed', mode==='light');
    };
    themeBtn.addEventListener('click',()=>{
      const mode = localStorage.getItem('theme')==='light' ? 'dark' : 'light';
      setTheme(mode);
    });
    if(localStorage.getItem('theme')==='light') setTheme('light');

    // Drawer (mobile menu)
    const drawer = $('#drawer');
    $('#openMenu').addEventListener('click', ()=>{ drawer.classList.add('show'); drawer.setAttribute('aria-hidden','false'); });
    $('#closeMenu').addEventListener('click', ()=>{ drawer.classList.remove('show'); drawer.setAttribute('aria-hidden','true'); });

    // Modal
    const overlay = $('#overlay');
    $('#openModal').addEventListener('click', ()=>{ overlay.classList.add('show'); overlay.setAttribute('aria-hidden','false'); });
    $('#closeModal').addEventListener('click', ()=>{ overlay.classList.remove('show'); overlay.setAttribute('aria-hidden','true'); });
    overlay.addEventListener('click', (e)=>{ if(e.target===overlay){ overlay.classList.remove('show'); overlay.setAttribute('aria-hidden','true'); } });

    // Toast
    const toast = $('#toast');
    const showToast = (msg='An adana bayanai ✅')=>{
      toast.textContent = msg; toast.classList.add('show');
      setTimeout(()=> toast.classList.remove('show'), 2200);
    };
    $('#showToast').addEventListener('click', ()=> showToast('Barka da zuwa! 🎉'));

    // Form validation (mai sauƙi)
    const form = $('#contactForm');
    const emailRe = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    form.addEventListener('submit', (e)=>{
      e.preventDefault();
      const name = $('#name').value.trim();
      const email = $('#email').value.trim();
      const msg = $('#msg').value.trim();
      let ok = true;

      const setErr = (id, text) => { $(id).textContent = text || ''; };
      setErr('#nameErr'); setErr('#emailErr'); setErr('#msgErr');

      if(!name){ setErr('#nameErr','Da fatan a shigar da suna.'); ok=false; }
      if(!emailRe.test(email)){ setErr('#emailErr','Shigar da sahihin imel.'); ok=false; }
      if(msg.length < 6){ setErr('#msgErr','Saƙo ya yi gajarta (akalla haruffa 6).'); ok=false; }

      if(ok){
        showToast('An aika! ✅');
        form.reset();
      }
    });

    // Footer year
    $('#year').textContent = new Date().getFullYear();

    // Karamin "reveal on scroll"
    const inView = (el)=>{
      const r = el.getBoundingClientRect();
      return r.top < innerHeight - 80;
    };
    const reveal = ()=>{
      document.querySelectorAll('.card, .feature').forEach(el=>{
        if(!el.dataset.show && inView(el)){
          el.dataset.show = true;
          el.animate([
            {opacity:0, transform:'translateY(12px)'},
            {opacity:1, transform:'translateY(0)'}
          ], {duration:420, easing:'cubic-bezier(.2,.8,.2,1)', fill:'both'});
        }
      });
    };
    addEventListener('scroll', reveal, {passive:true});
    reveal();
  </script>
</body>
</html>
