<!DOCTYPE html>
<html lang="ta">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>Wedding Invitation – Mohan kumar & Sangeetha</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300&family=Lato:wght@300;400&display=swap" rel="stylesheet">
<style>
:root {
  --maroon: #6B1A1A;
  --deep-maroon: #4A0E0E;
  --gold: #C9920A;
  --light-gold: #E8C56A;
  --cream: #FDF8F0;
  --pw: 44px; /* pillar width mobile */
}

@media(min-width:600px){ :root{ --pw: 60px; } }
@media(min-width:900px){ :root{ --pw: 72px; } }

* { margin:0; padding:0; box-sizing:border-box; }

html { scroll-behavior: smooth; }

body {
  background: var(--cream);
  font-family: 'Lato', sans-serif;
  overflow-x: hidden;
  min-height: 100vh;
}

/* ============ GARLAND ============ */
#garland-bar {
  position: fixed;
  top: 0; left: 0; right: 0;
  height: 64px;
  z-index: 1000;
  pointer-events: none;
}
#garland-svg { width: 100%; height: 64px; }

/* ============ PILLARS ============ */
.pillar {
  position: fixed;
  top: 0; bottom: 0;
  width: var(--pw);
  z-index: 100;
  pointer-events: none;
  overflow: hidden;
}
#pillar-left  { left: 0; }
#pillar-right { right: 0; }

.pillar-body {
  position: absolute;
  inset: 0;
  background: linear-gradient(to right, #2e0808, #5A1010, #2e0808);
  border-right: 2px solid #C9920A;
}
#pillar-right .pillar-body {
  background: linear-gradient(to left, #2e0808, #5A1010, #2e0808);
  border-right: none;
  border-left: 2px solid #C9920A;
}

/* Gold edge stripes */
.pillar-stripe-a, .pillar-stripe-b {
  position: absolute;
  top: 0; bottom: 0;
  width: 3px;
  background: #C9920A;
}
.pillar-stripe-a { left: 0; }
.pillar-stripe-b { right: 0; }

/* Capital + base */
.pillar-cap, .pillar-base {
  position: absolute;
  left: 0; right: 0;
  height: 28px;
  background: linear-gradient(135deg, #C9920A, #8B5E08, #C9920A);
  z-index: 2;
}
.pillar-cap  { top: 0; }
.pillar-base { bottom: 0; }
.pillar-cap::after, .pillar-base::after {
  content: '';
  position: absolute;
  left: 4px; right: 4px;
  height: 3px;
  background: rgba(255,224,138,0.5);
  top: 50%; transform: translateY(-50%);
  border-radius: 2px;
}

/* Moving glow orb */
.pillar-glow {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: calc(var(--pw) + 20px);
  height: 80px;
  border-radius: 50%;
  background: radial-gradient(ellipse, rgba(201,146,10,0.55) 0%, rgba(232,197,106,0.2) 50%, transparent 75%);
  animation: glowMove 3.5s ease-in-out infinite;
  pointer-events: none;
}
@keyframes glowMove {
  0%   { top: 5%;  opacity: 0.5; }
  25%  { opacity: 1; }
  50%  { top: 85%; opacity: 0.5; }
  75%  { opacity: 1; }
  100% { top: 5%;  opacity: 0.5; }
}

/* Diamond motifs on pillar */
.pillar-motifs {
  position: absolute;
  inset: 28px 0;
  overflow: hidden;
}

/* Pulse glow on gold stripes */
.pillar-stripe-a, .pillar-stripe-b {
  animation: stripePulse 2.5s ease-in-out infinite alternate;
}
@keyframes stripePulse {
  0%  { box-shadow: 0 0 2px #C9920A, 0 0 6px #C9920A; opacity: 0.8; }
  100%{ box-shadow: 0 0 6px #E8C56A, 0 0 18px rgba(201,146,10,0.6); opacity: 1; }
}

/* ============ BOOK / GATE ============ */
#book-wrapper {
  position: fixed;
  inset: 0;
  z-index: 500;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--deep-maroon);
  cursor: pointer;
}

.book-scene {
  width: min(300px, 82vw);
  height: min(420px, 72vh);
  perspective: 1000px;
  position: relative;
}

.book-cover {
  width: 100%;
  height: 100%;
  transform-style: preserve-3d;
  transform-origin: left center;
  transition: transform 1.4s cubic-bezier(0.77,0,0.175,1);
  position: relative;
  border-radius: 3px 10px 10px 3px;
  box-shadow: 6px 6px 32px rgba(0,0,0,0.7);
}
.book-cover.flipped { transform: rotateY(-160deg); }

.cover-front, .cover-back {
  position: absolute;
  inset: 0;
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
  border-radius: 3px 10px 10px 3px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
.cover-front {
  background: linear-gradient(160deg, var(--maroon), var(--deep-maroon));
  border: 2px solid var(--gold);
}
.cover-front::before {
  content: '';
  position: absolute;
  inset: 8px;
  border: 1px solid rgba(201,146,10,0.35);
  border-radius: 5px;
  pointer-events: none;
}
.cover-front-text {
  color: var(--light-gold);
  text-align: center;
  padding: 1.5rem;
}
.cover-front-text .cover-om { font-size: 2.2rem; margin-bottom: 0.4rem; }
.cover-front-text h2 {
  font-family: 'Playfair Display', serif;
  font-size: clamp(1.1rem,4vw,1.5rem);
  letter-spacing: 2px;
  margin-bottom: 0.4rem;
}
.cover-front-text p { font-size: 0.8rem; letter-spacing: 3px; color: var(--gold); margin-bottom: 1rem; }
.tap-hint { font-size: 0.72rem; letter-spacing:1px; color: rgba(232,197,106,0.55); animation: pulse-hint 2s ease-in-out infinite; }
@keyframes pulse-hint { 0%,100%{opacity:0.35} 50%{opacity:1} }

.cover-back {
  background: var(--cream);
  transform: rotateY(180deg);
  border-radius: 10px 3px 3px 10px;
  padding: 1.5rem;
  text-align: center;
  color: var(--maroon);
  font-family: 'Cormorant Garamond', serif;
  font-size: 1rem;
  line-height: 1.8;
}

.book-spine {
  position: absolute;
  left: -10px; top: 0; bottom: 0;
  width: 10px;
  background: linear-gradient(to right, #2e0a0a, var(--maroon));
  border-radius: 3px 0 0 3px;
  border: 1px solid rgba(201,146,10,0.3);
  border-right: none;
}

.book-inner-page {
  position: absolute;
  inset: 0;
  background: #fff9f0;
  border-radius: 3px 10px 10px 3px;
  border: 1px solid rgba(201,146,10,0.2);
  z-index: -1;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  color: var(--maroon);
  font-family: 'Cormorant Garamond', serif;
  font-size: 0.95rem;
  padding: 1.5rem;
  text-align: center;
  gap: 0.5rem;
}

@keyframes gate-out {
  0%  { opacity:1; transform:scale(1); }
  60% { opacity:1; transform:scale(1.04); }
  100%{ opacity:0; transform:scale(1.1); }
}
.gate-exit { animation: gate-out 0.8s 1.2s forwards; }

/* ============ MAIN CONTENT ============ */
#main-content {
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.8s ease 0.4s;
  /* Side padding accounts for pillars */
  padding-left: calc(var(--pw) + 8px);
  padding-right: calc(var(--pw) + 8px);
  padding-top: 64px;
}
#main-content.visible { opacity:1; pointer-events:auto; }

/* ============ PETAL CANVAS ============ */
#petal-canvas {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 200;
}

/* ============ HERO ============ */
#hero {
  min-height: 100svh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 4rem 1rem 3rem;
}

.om-symbol {
  font-size: 2.6rem;
  color: var(--gold);
  margin-bottom: 0.8rem;
  animation: fadeInDown 1.5s ease both;
}

@keyframes fadeInDown { from{opacity:0;transform:translateY(-24px)} to{opacity:1;transform:translateY(0)} }
@keyframes fadeInUp   { from{opacity:0;transform:translateY(24px)}  to{opacity:1;transform:translateY(0)} }
@keyframes fadeIn     { from{opacity:0} to{opacity:1} }

.invite-label {
  font-size: clamp(0.65rem,2.5vw,0.8rem);
  letter-spacing: 4px;
  color: var(--gold);
  text-transform: uppercase;
  margin-bottom: 1.2rem;
  animation: fadeIn 1.5s 0.3s both;
}

.couple-names {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2.4rem,9vw,4.5rem);
  color: var(--maroon);
  line-height: 1.1;
  animation: fadeInUp 1.5s 0.5s both;
}
.couple-names .ampersand {
  font-style: italic;
  color: var(--gold);
  display: block;
  font-size: 0.65em;
  margin: 0.1rem 0;
}

.date-line {
  margin: 1.6rem 0 0.8rem;
  font-family: 'Cormorant Garamond', serif;
  font-size: clamp(0.9rem,3vw,1.2rem);
  color: var(--maroon);
  letter-spacing: 3px;
  animation: fadeIn 1.5s 1s both;
}

.divider {
  width: 100px;
  height: 1px;
  background: var(--gold);
  margin: 0.8rem auto;
  position: relative;
}
.divider::before {
  content: '✦';
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%,-50%);
  background: var(--cream);
  padding: 0 7px;
  color: var(--gold);
  font-size: 0.65rem;
}

.rings-wrap { margin: 1.2rem auto; animation: fadeIn 1.5s 0.8s both; }

/* ============ COUNTDOWN ============ */
#countdown-section {
  background: var(--maroon);
  padding: 2.5rem 1rem;
  text-align: center;
  margin: 0 calc(-1*(var(--pw) + 8px));
}
#countdown-section h2 {
  font-family: 'Playfair Display', serif;
  color: var(--light-gold);
  font-size: clamp(0.85rem,3vw,1.2rem);
  letter-spacing: 3px;
  margin-bottom: 1.5rem;
}
.countdown-grid {
  display: flex;
  justify-content: center;
  gap: clamp(1rem,4vw,2.5rem);
  flex-wrap: wrap;
}
.countdown-item { text-align: center; min-width: 60px; }
.countdown-num {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2.2rem,7vw,3rem);
  color: var(--light-gold);
  line-height: 1;
  display: block;
}
.countdown-lbl {
  font-size: 0.65rem;
  letter-spacing: 3px;
  color: rgba(232,197,106,0.6);
  text-transform: uppercase;
  margin-top: 0.25rem;
  display: block;
}

/* ============ SECTIONS COMMON ============ */
.section-wrap {
  padding: 3.5rem 1rem;
  text-align: center;
}
.section-wrap.alt {
  background: #fff9f0;
  margin: 0 calc(-1*(var(--pw) + 8px));
  padding-left: calc(var(--pw) + 16px);
  padding-right: calc(var(--pw) + 16px);
}
.section-header {
  font-family: 'Playfair Display', serif;
  font-size: clamp(1.5rem,5vw,2rem);
  color: var(--maroon);
  margin-bottom: 0.4rem;
}
.section-sub {
  font-size: 0.72rem;
  letter-spacing: 4px;
  color: var(--gold);
  text-transform: uppercase;
  margin-bottom: 1.2rem;
}

/* ============ COUPLE PHOTO ============ */
.couple-photo-frame {
  width: min(240px, 65vw);
  height: min(310px, 84vw);
  margin: 0 auto 1.5rem;
  border: 3px solid var(--gold);
  border-radius: 50% 50% 48% 52% / 60% 60% 40% 40%;
  overflow: hidden;
  box-shadow: 0 0 0 7px rgba(201,146,10,0.12), 0 16px 48px rgba(107,26,26,0.18);
}
.couple-photo-frame img { width:100%; height:100%; object-fit:cover; }
.couple-photo-placeholder {
  width:100%; height:100%;
  background: linear-gradient(135deg,#f5e6d0,#e8c9a0);
  display:flex; align-items:center; justify-content:center;
  flex-direction:column; gap:0.4rem;
  color:var(--maroon);
  font-family:'Cormorant Garamond',serif; font-size:0.9rem;
}

/* ============ EVENTS ============ */
.events-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(220px,85vw),1fr));
  gap: 1.2rem;
  margin-top: 2rem;
}
.event-card {
  background: white;
  border: 1px solid rgba(201,146,10,0.3);
  border-top: 4px solid var(--gold);
  border-radius: 8px;
  padding: 1.6rem 1rem;
  text-align: center;
  box-shadow: 0 4px 18px rgba(107,26,26,0.07);
  transition: transform 0.3s, box-shadow 0.3s;
}
.event-card:active { transform: translateY(-3px); box-shadow: 0 10px 32px rgba(107,26,26,0.14); }
@media(hover:hover){ .event-card:hover { transform:translateY(-4px); box-shadow:0 12px 36px rgba(107,26,26,0.15); } }
.event-icon { font-size:2rem; margin-bottom:0.7rem; }
.event-name { font-family:'Playfair Display',serif; font-size:1.2rem; color:var(--maroon); margin-bottom:0.4rem; }
.event-date { font-size:0.78rem; color:var(--gold); letter-spacing:2px; font-weight:600; margin-bottom:0.4rem; }
.event-time { font-size:0.85rem; color:#666; }
.event-venue { margin-top:0.7rem; font-family:'Cormorant Garamond',serif; font-size:0.95rem; color:var(--maroon); font-style:italic; }

/* ============ VENUE ============ */
.venue-photo-wrap {
  width:100%;
  max-width:600px;
  margin:1.5rem auto;
  border:3px solid var(--gold);
  border-radius:10px;
  overflow:hidden;
  box-shadow:0 8px 32px rgba(107,26,26,0.18);
  min-height:200px;
  background:linear-gradient(135deg,#f0e0c0,#e0c8a0);
  display:flex; align-items:center; justify-content:center;
  flex-direction:column; gap:0.4rem;
  color:var(--maroon);
  font-family:'Cormorant Garamond',serif; font-size:1rem;
}
.venue-photo-wrap img { width:100%; height:min(260px,55vw); object-fit:cover; display:block; }
.venue-address {
  font-family:'Cormorant Garamond',serif;
  font-size:1rem;
  color:var(--maroon);
  margin:1rem 0;
  line-height:1.8;
}
.directions-btn {
  display:inline-flex; align-items:center; gap:0.4rem;
  background:var(--maroon); color:var(--light-gold);
  border:none; padding:0.75rem 1.8rem;
  border-radius:30px; font-size:0.85rem;
  letter-spacing:2px; text-transform:uppercase;
  text-decoration:none; cursor:pointer;
  transition:background 0.3s,transform 0.2s;
  box-shadow:0 4px 14px rgba(107,26,26,0.3);
  margin-top:1rem;
  -webkit-tap-highlight-color: transparent;
}
.directions-btn:active { background:var(--deep-maroon); transform:translateY(-1px); }
@media(hover:hover){ .directions-btn:hover { background:var(--deep-maroon); transform:translateY(-2px); } }

/* ============ FOOTER ============ */
footer {
  background:var(--deep-maroon);
  color:rgba(232,197,106,0.55);
  text-align:center;
  padding:2rem 1rem;
  font-size:0.75rem;
  letter-spacing:2px;
  margin:0 calc(-1*(var(--pw)+8px));
}
footer .footer-names {
  font-family:'Playfair Display',serif;
  font-size:1.1rem;
  color:var(--light-gold);
  margin-bottom:0.4rem;
}

/* ============ SCROLL REVEAL ============ */
.reveal {
  opacity:0;
  transform:translateY(24px);
  transition:opacity 0.7s ease, transform 0.7s ease;
}
.reveal.visible { opacity:1; transform:translateY(0); }

/* ============ SAFE AREA (NOTCH) ============ */
@supports(padding:env(safe-area-inset-left)){
  #main-content {
    padding-left: calc(var(--pw) + 8px + env(safe-area-inset-left));
    padding-right: calc(var(--pw) + 8px + env(safe-area-inset-right));
  }
}
</style>
</head>
<body>

<!-- GARLAND BAR -->
<div id="garland-bar">
  <svg id="garland-svg" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1000 64" preserveAspectRatio="none">
    <defs>
      <style>
        @keyframes sway  { 0%,100%{transform:translateY(0)} 50%{transform:translateY(3px)} }
        @keyframes bloom { 0%,100%{transform:scale(1)}      50%{transform:scale(1.1)} }
      </style>
    </defs>
    <path d="M0,14 Q250,30 500,14 Q750,0 1000,14" fill="none" stroke="#8B6914" stroke-width="1.5" opacity="0.7"/>
    <g id="garland-items"></g>
  </svg>
</div>

<!-- PILLAR LEFT -->
<div class="pillar" id="pillar-left">
  <div class="pillar-body"></div>
  <div class="pillar-stripe-a"></div>
  <div class="pillar-stripe-b"></div>
  <div class="pillar-cap"></div>
  <div class="pillar-base"></div>
  <div class="pillar-glow"></div>
  <div class="pillar-motifs" id="lp-motifs"></div>
</div>

<!-- PILLAR RIGHT -->
<div class="pillar" id="pillar-right">
  <div class="pillar-body"></div>
  <div class="pillar-stripe-a"></div>
  <div class="pillar-stripe-b"></div>
  <div class="pillar-cap"></div>
  <div class="pillar-base"></div>
  <div class="pillar-glow" style="animation-delay:-1.75s"></div>
  <div class="pillar-motifs" id="rp-motifs"></div>
</div>

<!-- BOOK GATE -->
<div id="book-wrapper">
  <div class="book-scene">
    <div class="book-inner-page">
      <div style="font-size:1.8rem">🙏</div>
      <p style="font-family:'Playfair Display',serif;font-size:1.05rem;color:#6B1A1A;line-height:1.7">With joy in our hearts,<br>we invite you to<br>bless our union.</p>
    </div>
    <div class="book-cover" id="book-cover">
      <div class="book-spine"></div>
      <div class="cover-front">
        <div class="cover-front-text">
          <div class="cover-om">ॐ</div>
          <h2>Wedding Invitation</h2>
          <p>Mohan kumar &amp; Sangeetha</p>
          <div style="width:50px;height:1px;background:rgba(201,146,10,0.5);margin:0.7rem auto"></div>
          <p class="tap-hint">✦ Tap to open ✦</p>
        </div>
      </div>
      <div class="cover-back">
        <p>ॐ நமசிவாய</p><br>
        <p style="font-size:0.85rem;color:#6B1A1A">Beginning a new chapter…</p>
      </div>
    </div>
  </div>
</div>

<!-- PETAL CANVAS -->
<canvas id="petal-canvas"></canvas>

<!-- MAIN CONTENT -->
<div id="main-content">

  <!-- HERO -->
  <section id="hero">
    <div class="om-symbol">ॐ</div>
    <div class="invite-label">With the blessings of our families</div>

    <div class="rings-wrap">
      <svg width="110" height="56" viewBox="0 0 110 56" xmlns="http://www.w3.org/2000/svg">
        <circle cx="36" cy="28" r="20" fill="none" stroke="#C9920A" stroke-width="3"
          style="animation:ringPulse 2s ease-in-out infinite"/>
        <circle cx="74" cy="28" r="20" fill="none" stroke="#6B1A1A" stroke-width="3"
          style="animation:ringPulse 2s 0.4s ease-in-out infinite"/>
        <style>@keyframes ringPulse{0%,100%{filter:drop-shadow(0 0 0px #C9920A)}50%{filter:drop-shadow(0 0 5px #C9920A)}}</style>
        <polygon points="55,7 59,16 55,20 51,16" fill="#C9920A" opacity="0.9"/>
      </svg>
    </div>

    <div class="couple-names">
      Mohan kumar
      <span class="ampersand">&amp;</span>
      Sangeetha
    </div>

    <div class="divider"></div>

    <div class="date-line">WEDNESDAY · 1 JULY 2026</div>
    <div style="font-family:'Cormorant Garamond',serif;font-size:0.95rem;color:#999;letter-spacing:2px;animation:fadeIn 1.5s 1.2s both;margin-top:0.4rem">
      Kolla chattiram . Kanchipuram
    </div>
  </section>

  <!-- COUNTDOWN -->
  <div id="countdown-section">
    <h2>THE CELEBRATION BEGINS IN</h2>
    <div class="countdown-grid">
      <div class="countdown-item"><span class="countdown-num" id="cd-days">00</span><span class="countdown-lbl">Days</span></div>
      <div class="countdown-item"><span class="countdown-num" id="cd-hours">00</span><span class="countdown-lbl">Hours</span></div>
      <div class="countdown-item"><span class="countdown-num" id="cd-mins">00</span><span class="countdown-lbl">Minutes</span></div>
      <div class="countdown-item"><span class="countdown-num" id="cd-secs">00</span><span class="countdown-lbl">Seconds</span></div>
    </div>
  </div>

  <!-- COUPLE PHOTO -->
  <section class="section-wrap reveal">
    <div class="section-sub">Together Forever</div>
    <h2 class="section-header">The Couple</h2>
    <div class="divider" style="margin-bottom:1.8rem"></div>
    <div class="couple-photo-frame">
      <div class="couple-photo-placeholder">
        <img src="C:\Users\ELCOT\Desktop\project 2\file_00000000ede871fa9834f90e5daf7e08.png"&gt;</span>
      </div>
      <!-- <img src="couple-photo.jpg" alt="Arjun and Meera"> -->
    </div>
    <p style="font-family:'Cormorant Garamond',serif;font-size:1.1rem;color:var(--maroon);font-style:italic;max-width:340px;margin:0 auto;line-height:1.8">
      "Two souls, one heartbeat — bound by love and destined to walk this journey together."
    </p>
  </section>

  <!-- EVENTS -->
  <section class="section-wrap alt">
    <div class="reveal">
      <div class="section-sub">Join Us For</div>
      <h2 class="section-header">The Celebrations</h2>
      <div class="divider"></div>
    </div>
    <div class="events-grid">
      <div class="event-card reveal">
        <div class="event-icon">💑</div>
        <div class="event-name">Reception</div>
        <div class="event-date">1 JUL 2026 · WEDNESDAY</div>
        <div class="event-time">6:30 PM onwards</div>
        <div class="event-venue">Kolla Chattiram, (SSKV Girls School opposite)<br>Kanchipuram</div>
      </div>
      <div class="event-card reveal">
        <div class="event-icon">💍</div>
        <div class="event-name">Wedding</div>
        <div class="event-date">2 JUL 2026 · TUESDAY</div>
        <div class="event-time">Muhurtham: 9:30 AM 10:30 AM</div>
        <div class="event-venue"> Sri Kachabeswarar Temple,<br>Kanchipuram</div>
      </div>
    </div>
  </section>

  <!-- VENUE -->
  <section class="section-wrap reveal">
    <div class="section-sub">Find Us Here</div>
    <h2 class="section-header">Venue</h2>
    <div class="divider"></div>
    <div class="venue-photo-wrap">
      <!-- <img src="mandapam.jpg" alt="Sri Murugan Mahal"> -->
      <img src="C:\Users\ELCOT\Desktop\project 2\1000_F_667495853_ioWBMm32u7UFvcYz0Sb3KrGj8YjnfrQA.jpg"&gt;</span>
    </div>
    <div class="venue-address">
      <strong style="font-size:1.15rem;display:block;margin-bottom:0.4rem">Sri Murugan Mahal</strong>
      Kolla Chattiram, Kanchipuram (SSKV Girls School opposite),<br>Kanchipuram – 631 502,<br>Tamil Nadu, India
    </div>
    <a class="directions-btn" href="https://maps.app.goo.gl/jJH4DCSJ8WhA6XvY9?g_st=ac" target="_blank" rel="noopener">
      📍 Get Directions
    </a>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-names">Mohan kumar &amp; Sangeetha</div>
    <div>With love &amp; blessings · 01.07.2026</div>
    <div style="margin-top:0.8rem;font-size:1.3rem">🌸 ✦ 🌸</div>
  </footer>

</div><!-- /main-content -->

<script>
/* ===== GARLAND ===== */
(function(){
  const g = document.getElementById('garland-items');
  const W = 1000;
  const ropeY = x => {
    if(x <= 500){ const t=x/500; return (1-t)*(1-t)*14+2*(1-t)*t*30+t*t*14; }
    else{ const t=(x-500)/500; return (1-t)*(1-t)*14+2*(1-t)*t*0+t*t*14; }
  };
  for(let x=30, i=0; x<=W-30; x+=40, i++){
    const ry = ropeY(x);
    const delay = ((i*0.1)%1.6).toFixed(2);
    if(i%3===1){
      let s=`<g transform="translate(${x},${ry+14})" style="animation:bloom ${(1.6+i%3*0.3).toFixed(1)}s ${delay}s ease-in-out infinite">`;
      for(let p=0;p<8;p++){
        const a=p/8*360, cx=Math.cos(a*Math.PI/180)*6, cy=Math.sin(a*Math.PI/180)*6;
        s+=`<ellipse cx="${cx.toFixed(1)}" cy="${cy.toFixed(1)}" rx="4.5" ry="2.5" fill="#F4A820" transform="rotate(${a} 0 0)" opacity="0.95"/>`;
      }
      s+=`<circle cx="0" cy="0" r="3.5" fill="#D4810A"/></g>`;
      g.insertAdjacentHTML('beforeend',s);
    } else {
      const fl=i%2===0?1:-1;
      g.insertAdjacentHTML('beforeend',
        `<g transform="translate(${x},${ry+8}) rotate(${fl*14})" style="animation:sway ${(1.5+i%4*0.28).toFixed(2)}s ${delay}s ease-in-out infinite">
          <path d="M0,0 C${fl*3},-10 ${fl*8},-20 0,-25 C${-fl*8},-20 ${-fl*3},-10 0,0 Z" fill="#4A7C3F" opacity="0.88"/>
          <line x1="0" y1="0" x2="0" y2="-23" stroke="#2d5a25" stroke-width="0.7" opacity="0.55"/>
        </g>`
      );
    }
  }
})();

/* ===== PILLAR DIAMOND MOTIFS ===== */
(function(){
  ['lp-motifs','rp-motifs'].forEach((id,pi) => {
    const el = document.getElementById(id);
    if(!el) return;
    const pw = parseInt(getComputedStyle(document.documentElement).getPropertyValue('--pw')) || 44;
    const cx = pw/2;
    let html='';
    for(let y=50; y<2000; y+=55){
      const delay = ((y/55*0.18)%2).toFixed(2);
      html += `<div style="position:absolute;left:50%;top:${y}px;transform:translateX(-50%);animation:diamondPulse 2.8s ${delay}s ease-in-out infinite">
        <svg width="20" height="20" viewBox="0 0 20 20">
          <polygon points="10,1 18,10 10,19 2,10" fill="#C9920A" opacity="0.75"/>
          <circle cx="10" cy="10" r="3" fill="#FFE08A" opacity="0.9"/>
        </svg>
      </div>`;
    }
    el.innerHTML = html;
  });
})();

/* ===== ADD KEYFRAME FOR DIAMOND PULSE ===== */
(function(){
  const st = document.createElement('style');
  st.textContent = `@keyframes diamondPulse{
    0%,100%{opacity:0.5;filter:drop-shadow(0 0 0px #C9920A)}
    50%{opacity:1;filter:drop-shadow(0 0 5px #E8C56A)}
  }`;
  document.head.appendChild(st);
})();

/* ===== BOOK / GATE ===== */
(function(){
  const wrap  = document.getElementById('book-wrapper');
  const cover = document.getElementById('book-cover');
  const main  = document.getElementById('main-content');
  let opened  = false;
  wrap.addEventListener('click',()=>{
    if(opened) return;
    opened = true;
    cover.classList.add('flipped');
    wrap.classList.add('gate-exit');
    setTimeout(()=>{
      wrap.style.display='none';
      main.classList.add('visible');
      startPetals();
    },2000);
  });
})();

/* ===== COUNTDOWN ===== */
(function(){
  const target = new Date('2026-07-01T08:42:00');
  const pad = n => String(n).padStart(2,'0');
  function tick(){
    let d = target - Date.now();
    if(d<0) d=0;
    document.getElementById('cd-days').textContent  = pad(Math.floor(d/86400000));
    document.getElementById('cd-hours').textContent = pad(Math.floor(d%86400000/3600000));
    document.getElementById('cd-mins').textContent  = pad(Math.floor(d%3600000/60000));
    document.getElementById('cd-secs').textContent  = pad(Math.floor(d%60000/1000));
  }
  tick(); setInterval(tick,1000);
})();

/* ===== FALLING PETALS ===== */
function startPetals(){
  const cv  = document.getElementById('petal-canvas');
  const ctx = cv.getContext('2d');
  const resize=()=>{ cv.width=window.innerWidth; cv.height=window.innerHeight; };
  resize(); window.addEventListener('resize',resize);
  const COLS=['#E8A0A0','#F4A820','#E85A8A','#FFD0D0','#FFBCBC'];
  const mk=()=>({
    x:Math.random()*cv.width, y:-20,
    sz:5+Math.random()*7,
    vx:(Math.random()-.5)*1.3, vy:0.9+Math.random()*1.8,
    rot:Math.random()*Math.PI*2, rv:(Math.random()-.5)*0.05,
    col:COLS[Math.random()*5|0], op:0.55+Math.random()*0.4,
    wb:Math.random()*Math.PI*2, ws:0.018+Math.random()*0.018
  });
  const petals=Array.from({length:30},()=>{ const p=mk(); p.y=Math.random()*cv.height; return p; });
  function draw(p){
    ctx.save(); ctx.globalAlpha=p.op;
    ctx.translate(p.x,p.y); ctx.rotate(p.rot);
    ctx.fillStyle=p.col; ctx.beginPath();
    ctx.moveTo(0,-p.sz);
    ctx.bezierCurveTo(p.sz*.8,-p.sz*.5,p.sz*.8,p.sz*.5,0,p.sz);
    ctx.bezierCurveTo(-p.sz*.8,p.sz*.5,-p.sz*.8,-p.sz*.5,0,-p.sz);
    ctx.fill(); ctx.restore();
  }
  (function loop(){
    ctx.clearRect(0,0,cv.width,cv.height);
    petals.forEach(p=>{
      p.wb+=p.ws; p.x+=p.vx+Math.sin(p.wb)*.7; p.y+=p.vy; p.rot+=p.rv;
      if(p.y>cv.height+20) Object.assign(p,mk());
      draw(p);
    });
    requestAnimationFrame(loop);
  })();
}

/* ===== SCROLL REVEAL ===== */
(function(){
  const io=new IntersectionObserver(entries=>{
    entries.forEach(e=>{ if(e.isIntersecting){ e.target.classList.add('visible'); io.unobserve(e.target); } });
  },{threshold:0.12});
  document.querySelectorAll('.reveal').forEach(el=>io.observe(el));
})();
</script>
</body>
</html>
