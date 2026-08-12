<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>aurora</title>
<link href="https://fonts.cdnfonts.com/css/google-sans" rel="stylesheet" />
<style>
  :root{--bg0:#03040c;--bg1:#070b1c;--ink:#f4f7ff;--blue:#6fc2ff;--teal:#2dd4bf;--violet:#8b5cf6;--sky:#38bdf8;--fallback:-apple-system,'Segoe UI',Roboto,Helvetica,Arial,sans-serif;--sans:'Product Sans','Google Sans',var(--fallback);}
  *{box-sizing:border-box;}html,body{height:100%;}
  body{margin:0;font-family:var(--sans);color:var(--ink);background:radial-gradient(120% 90% at 50% 110%, rgba(45,212,191,.14), transparent 60%),linear-gradient(180deg, var(--bg0) 0%, var(--bg1) 55%, #0a1128 100%);overflow:hidden;-webkit-font-smoothing:antialiased;}
  .aurora{position:fixed;inset:-10% -10% auto -10%;height:80%;z-index:1;pointer-events:none;will-change:transform;}
  .ribbon{position:absolute;border-radius:50%;filter:blur(64px);mix-blend-mode:screen;opacity:.55;}
  .r1{width:55vw;height:46vh;left:4%;top:-6%;background:radial-gradient(ellipse at center, rgba(45,212,191,.75), transparent 62%);animation:drift1 26s ease-in-out infinite alternate;}
  .r2{width:46vw;height:40vh;left:34%;top:-14%;background:radial-gradient(ellipse at center, rgba(52,211,153,.65), transparent 60%);animation:drift2 34s ease-in-out infinite alternate;}
  .r3{width:50vw;height:42vh;right:2%;top:-8%;background:radial-gradient(ellipse at center, rgba(139,92,246,.62), transparent 60%);animation:drift3 30s ease-in-out infinite alternate;}
  .r4{width:44vw;height:38vh;left:14%;top:16%;background:radial-gradient(ellipse at center, rgba(56,189,248,.5), transparent 60%);animation:drift4 38s ease-in-out infinite alternate;}
  @keyframes drift1{from{transform:translate3d(0,0,0) rotate(-8deg) scale(1);}to{transform:translate3d(6vw,5vh,0) rotate(6deg) scale(1.18);}}
  @keyframes drift2{from{transform:translate3d(0,0,0) rotate(5deg) scale(1.1);}to{transform:translate3d(-5vw,6vh,0) rotate(-6deg) scale(.96);}}
  @keyframes drift3{from{transform:translate3d(0,0,0) rotate(7deg) scale(1);}to{transform:translate3d(-6vw,4vh,0) rotate(-5deg) scale(1.15);}}
  @keyframes drift4{from{transform:translate3d(0,0,0) rotate(-6deg) scale(1.05);opacity:.4;}to{transform:translate3d(5vw,-3vh,0) rotate(4deg) scale(1.2);opacity:.6;}}
  .mountains{position:fixed;left:0;right:0;bottom:0;z-index:2;pointer-events:none;will-change:transform;}
  .mountains svg{display:block;width:100%;height:38vh;}
  .vignette{position:fixed;inset:0;z-index:3;pointer-events:none;background:radial-gradient(120% 120% at 50% 40%, transparent 55%, rgba(2,4,12,.55) 100%);}
  .noise{position:fixed;inset:0;z-index:30;pointer-events:none;opacity:.05;mix-blend-mode:overlay;background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='2' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");}
  #snow{position:fixed;inset:0;z-index:20;pointer-events:none;}
  .scene{position:relative;z-index:10;min-height:100svh;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:2rem 1.5rem;gap:1.1rem;}
  .badge{display:inline-flex;align-items:center;gap:.6rem;font-family:'Product Sans Medium',var(--sans);font-weight:500;font-size:.8rem;letter-spacing:.42em;text-transform:uppercase;background:linear-gradient(90deg,#9ff5e6,var(--sky),#c4b5fd);-webkit-background-clip:text;background-clip:text;color:transparent;animation:rise .9s .1s cubic-bezier(.2,.7,.3,1) both;}
  .badge::before,.badge::after{content:"";height:1px;width:34px;}
  .badge::before{background:linear-gradient(90deg,transparent,rgba(160,200,255,.5));}
  .badge::after{background:linear-gradient(90deg,rgba(160,200,255,.5),transparent);}
  .headline{margin:0;font-family:'Product Sans Black','Google Sans',var(--sans);font-weight:900;font-size:clamp(2.1rem,6vw,4.4rem);line-height:1.06;letter-spacing:-0.01em;max-width:16ch;color:#fff;text-shadow:0 4px 40px rgba(120,180,255,.25);animation:rise .9s .22s cubic-bezier(.2,.7,.3,1) both;}
  .sub{margin:0;font-family:var(--sans);font-weight:400;font-size:clamp(1.25rem,3.4vw,2.1rem);background:linear-gradient(180deg,#9fd4ff,var(--blue) 60%,#4a9eff);-webkit-background-clip:text;background-clip:text;color:transparent;filter:drop-shadow(0 2px 18px rgba(90,170,255,.35));animation:rise .9s .34s cubic-bezier(.2,.7,.3,1) both;}
  .actions{display:flex;flex-wrap:wrap;align-items:center;justify-content:center;gap:.9rem;margin-top:1.4rem;animation:rise .9s .46s cubic-bezier(.2,.7,.3,1) both;}
  .btn{display:inline-flex;align-items:center;gap:.6rem;padding:.95rem 1.7rem;border-radius:14px;font-family:'Product Sans Medium','Google Sans',var(--sans);font-weight:500;font-size:1.02rem;letter-spacing:.01em;text-decoration:none;cursor:pointer;border:1px solid transparent;transition:transform .28s cubic-bezier(.2,.7,.3,1), box-shadow .28s ease, background .28s ease, border-color .28s ease;}
  .btn svg{width:1.15rem;height:1.15rem;flex:none;transition:transform .28s ease;}
  .btn:active{transform:translateY(0) scale(.98);}
  .btn:focus-visible{outline:2px solid var(--blue);outline-offset:3px;}
  .btn-primary{color:#04121a;background:linear-gradient(135deg,#5eead4,var(--sky) 55%,#818cf8);box-shadow:0 10px 34px rgba(56,189,248,.4), inset 0 1px 0 rgba(255,255,255,.5);}
  .btn-primary:hover{transform:translateY(-3px);box-shadow:0 16px 44px rgba(56,189,248,.55), inset 0 1px 0 rgba(255,255,255,.6);}
  .btn-primary:hover svg{transform:translateY(1px);}
  .btn-ghost{color:#e6f1ff;background:rgba(148,197,255,.07);border-color:rgba(148,197,255,.35);backdrop-filter:blur(6px);-webkit-backdrop-filter:blur(6px);}
  .btn-ghost:hover{transform:translateY(-3px);background:rgba(148,197,255,.14);border-color:rgba(170,210,255,.6);box-shadow:0 12px 32px rgba(90,160,255,.22);}
  .btn-ghost:hover svg{transform:translate(1px,-1px);}
  .btn-accent{color:#0c0820;background:linear-gradient(135deg,#c4b5fd,var(--violet) 55%,#ec4899);box-shadow:0 10px 34px rgba(139,92,246,.38), inset 0 1px 0 rgba(255,255,255,.45);}
  .btn-accent:hover{transform:translateY(-3px);box-shadow:0 16px 44px rgba(139,92,246,.55), inset 0 1px 0 rgba(255,255,255,.55);}
  .btn-accent:hover svg{transform:rotate(-8deg) scale(1.06);}
  .coming-soon{margin-top:.4rem;min-height:1.6rem;font-family:'Product Sans Medium',var(--sans);font-weight:500;font-size:1rem;letter-spacing:.28em;text-transform:uppercase;background:linear-gradient(90deg,#9ff5e6,var(--sky),#c4b5fd,#9ff5e6);background-size:220% auto;-webkit-background-clip:text;background-clip:text;color:transparent;opacity:0;transform:translateY(12px);pointer-events:none;transition:opacity .6s ease, transform .6s cubic-bezier(.2,.7,.3,1);}
  .coming-soon.show{opacity:1;transform:translateY(0);animation:sheen 3.2s linear infinite;}
  @keyframes sheen{to{background-position:220% center;}}
  @keyframes rise{from{opacity:0;transform:translateY(22px);}to{opacity:1;transform:translateY(0);}}
  @media (max-width:560px){ .actions{flex-direction:column;width:100%;} .btn{width:100%;justify-content:center;} }
  @media (prefers-reduced-motion: reduce){.ribbon,.badge,.headline,.sub,.actions,.coming-soon.show{animation:none !important;}.btn,.btn svg{transition:none !important;}.coming-soon{transition:opacity .2s linear;transform:none;}}
</style>
</head>
<body>
  <div class="aurora" id="aurora">
    <div class="ribbon r1"></div><div class="ribbon r2"></div><div class="ribbon r3"></div><div class="ribbon r4"></div>
  </div>
  <div class="mountains" id="mountains">
    <svg viewBox="0 0 1440 320" preserveAspectRatio="xMidYMax slice" aria-hidden="true">
      <path fill="rgba(11,17,42,.9)" d="M0 210 L110 140 L230 195 L350 105 L470 175 L600 88 L720 165 L850 100 L980 175 L1100 120 L1230 185 L1360 130 L1440 175 L1440 320 L0 320 Z"/>
      <path fill="rgba(5,8,22,.96)" d="M0 258 L140 205 L260 245 L400 185 L540 235 L680 172 L820 225 L960 185 L1100 235 L1240 195 L1380 238 L1440 212 L1440 320 L0 320 Z"/>
      <g fill="#04060f"><path d="M96 320 L116 246 L136 320 Z"/><path d="M150 320 L166 262 L182 320 Z"/><path d="M1180 320 L1200 250 L1220 320 Z"/><path d="M1240 320 L1256 268 L1272 320 Z"/><path d="M620 320 L638 258 L656 320 Z"/></g>
    </svg>
  </div>
  <div class="vignette"></div>
  <canvas id="snow"></canvas>
  <main class="scene">
    <span class="badge">❆ aurora</span>
    <h1 class="headline">Are you tired of dying to cheaters?</h1>
    <p class="sub">Then get aurora</p>
    <div class="actions">
      <a class="btn btn-primary" href="https://dsc.gg/getaroura">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg>
        Get script
      </a>
      <button class="btn btn-ghost" id="externalBtn" type="button">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
        Get external
      </button>
      <a class="btn btn-accent" href="obf.html">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="11" width="18" height="11" rx="2" ry="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
        Try our Obfuscator
      </a>
    </div>
    <div class="coming-soon" id="comingSoon">coming soon ✦</div>
  </main>
  <div class="noise"></div>

<script>
  const REDUCED = matchMedia('(prefers-reduced-motion: reduce)').matches;
  const cvs = document.getElementById('snow'), ctx = cvs.getContext('2d');
  let W, H, flakes = [];
  function resize(){W = cvs.width = innerWidth; H = cvs.height = innerHeight;const count = Math.min(220, Math.floor(W * H / 9000));flakes = Array.from({length: count}, () => ({x: Math.random()*W, y: Math.random()*H,r: Math.random()*2.2 + 0.6,s: Math.random()*0.7 + 0.25,o: Math.random()*0.6 + 0.25,w: Math.random()*0.6 + 0.2,p: Math.random()*Math.PI*2,d: Math.random()*0.4 - 0.2}));}
  function draw(){ctx.clearRect(0,0,W,H);ctx.fillStyle = '#fff';for(const f of flakes){ctx.globalAlpha = f.o;ctx.beginPath(); ctx.arc(f.x, f.y, f.r, 0, 6.283); ctx.fill();}ctx.globalAlpha = 1;}
  resize(); addEventListener('resize', resize);
  const auroraEl = document.getElementById('aurora');const mountEl = document.getElementById('mountains');
  let mx=0,my=0,tx=0,ty=0,t=0;
  addEventListener('mousemove', e=>{tx = (e.clientX/innerWidth - 0.5);ty = (e.clientY/innerHeight - 0.5);});
  function tick(){t += 0.008;ctx.clearRect(0,0,W,H);ctx.fillStyle = '#fff';for(const f of flakes){f.y += f.s;f.x += Math.sin(t*f.w*2 + f.p)*0.3 + f.d;if(f.y > H+4){ f.y = -4; f.x = Math.random()*W; }if(f.x > W+4) f.x = -4; if(f.x < -4) f.x = W+4;ctx.globalAlpha = f.o;ctx.beginPath(); ctx.arc(f.x, f.y, f.r, 0, 6.283); ctx.fill();}ctx.globalAlpha = 1;mx += (tx-mx)*0.04; my += (ty-my)*0.04;auroraEl.style.transform = 'translate3d(' + (mx*-22) + 'px,' + (my*-14) + 'px,0)';mountEl.style.transform  = 'translate3d(' + (mx*16) + 'px,' + (my*9) + 'px,0)';requestAnimationFrame(tick);}
  if(REDUCED){ draw(); } else { tick(); }
  const extBtn = document.getElementById('externalBtn');const comingSoon   = document.getElementById('comingSoon');
  extBtn.addEventListener('click', ()=> comingSoon.classList.toggle('show'));
</script>
</body>
</html>
