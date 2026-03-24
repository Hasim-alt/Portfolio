<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Portfolio — EE Instrumentation & Automation</title>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Exo+2:wght@300;400;600;700;900&family=Rajdhani:wght@400;600;700&display=swap" rel="stylesheet" />
<style>
  :root {
    --bg: #060a10;
    --bg2: #0c1220;
    --bg3: #101828;
    --cyan: #00d4ff;
    --green: #00ff99;
    --amber: #ffb800;
    --red: #ff4060;
    --text: #c8ddf0;
    --muted: #5a7a99;
    --border: rgba(0,212,255,0.15);
    --glow-c: 0 0 18px rgba(0,212,255,0.5);
    --glow-g: 0 0 18px rgba(0,255,153,0.5);
    --font-mono: 'Share Tech Mono', monospace;
    --font-head: 'Exo 2', sans-serif;
    --font-ui: 'Rajdhani', sans-serif;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-ui);
    font-size: 16px;
    overflow-x: hidden;
    cursor: default;
  }

  /* ─── GRID BACKGROUND ─── */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image:
      linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* ─── SCROLLBAR ─── */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--cyan); border-radius: 3px; }

  /* ─── NAV ─── */
  nav {
    position: fixed; top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 0 40px;
    height: 60px;
    background: rgba(6,10,16,0.92);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
  }
  .nav-logo {
    font-family: var(--font-mono);
    font-size: 13px;
    color: var(--cyan);
    letter-spacing: 2px;
  }
  .nav-logo span { color: var(--green); }
  .nav-links { display: flex; gap: 28px; }
  .nav-links a {
    font-family: var(--font-ui);
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    color: var(--muted);
    text-decoration: none;
    transition: color .2s;
    position: relative;
  }
  .nav-links a::after {
    content: '';
    position: absolute; bottom: -4px; left: 0; right: 0; height: 1px;
    background: var(--cyan);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform .25s;
  }
  .nav-links a:hover { color: var(--cyan); }
  .nav-links a:hover::after { transform: scaleX(1); }

  /* ─── SECTION WRAPPER ─── */
  section { position: relative; z-index: 1; }

  /* ─── HERO ─── */
  #hero {
    min-height: 100vh;
    display: grid;
    grid-template-columns: 1fr 1fr;
    align-items: center;
    gap: 60px;
    padding: 100px 80px 60px;
  }

  .hero-left { display: flex; flex-direction: column; gap: 24px; }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    padding: 6px 16px;
    border: 1px solid var(--cyan);
    border-radius: 2px;
    font-family: var(--font-mono);
    font-size: 11px;
    letter-spacing: 2px;
    color: var(--cyan);
    width: fit-content;
    background: rgba(0,212,255,0.05);
    animation: fadeDown .7s .1s both;
  }
  .hero-badge::before {
    content: '';
    width: 8px; height: 8px;
    border-radius: 50%;
    background: var(--green);
    box-shadow: var(--glow-g);
    animation: pulse 2s infinite;
  }

  .hero-name {
    font-family: var(--font-head);
    font-size: clamp(38px, 5vw, 68px);
    font-weight: 900;
    line-height: 1.05;
    letter-spacing: -1px;
    animation: fadeDown .7s .2s both;
  }
  .hero-name .line1 { display: block; color: var(--text); }
  .hero-name .line2 {
    display: block;
    background: linear-gradient(90deg, var(--cyan), var(--green));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-title {
    font-family: var(--font-mono);
    font-size: 14px;
    color: var(--amber);
    letter-spacing: 1px;
    animation: fadeDown .7s .3s both;
  }
  .hero-title::before { content: '> '; color: var(--muted); }

  .hero-about {
    font-family: var(--font-ui);
    font-size: 16px;
    font-weight: 400;
    line-height: 1.75;
    color: var(--text);
    max-width: 520px;
    opacity: .85;
    border-left: 2px solid var(--cyan);
    padding-left: 18px;
    animation: fadeDown .7s .4s both;
  }

  .hero-cta {
    display: flex; gap: 16px; flex-wrap: wrap;
    animation: fadeDown .7s .5s both;
  }
  .btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 12px 28px;
    font-family: var(--font-ui);
    font-size: 13px;
    font-weight: 700;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    text-decoration: none;
    border-radius: 2px;
    transition: all .25s;
    cursor: pointer;
    border: none;
  }
  .btn-primary {
    background: linear-gradient(135deg, var(--cyan), var(--green));
    color: var(--bg);
    box-shadow: 0 0 24px rgba(0,212,255,0.35);
  }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 4px 32px rgba(0,212,255,0.55); }
  .btn-outline {
    background: transparent;
    color: var(--cyan);
    border: 1px solid var(--cyan);
  }
  .btn-outline:hover { background: rgba(0,212,255,0.08); transform: translateY(-2px); }

  /* HERO RIGHT — PHOTO + STATS */
  .hero-right {
    display: flex; flex-direction: column; align-items: center; gap: 32px;
    animation: fadeUp .9s .3s both;
  }

  .photo-frame {
    position: relative;
    width: 260px; height: 260px;
  }
  .photo-frame::before, .photo-frame::after {
    content: '';
    position: absolute;
    border-radius: 50%;
  }
  .photo-frame::before {
    inset: -8px;
    border: 2px solid transparent;
    background: linear-gradient(var(--bg), var(--bg)) padding-box,
                linear-gradient(135deg, var(--cyan), var(--green), var(--cyan)) border-box;
    animation: spin 8s linear infinite;
  }
  .photo-frame::after {
    inset: -16px;
    border: 1px dashed rgba(0,212,255,0.2);
    animation: spin 16s linear infinite reverse;
  }
  .photo-ring-label {
    position: absolute;
    inset: -40px;
    border-radius: 50%;
    animation: spin 20s linear infinite;
  }
  .photo-inner {
    width: 100%; height: 100%;
    border-radius: 50%;
    background: var(--bg3);
    border: 2px solid var(--border);
    overflow: hidden;
    display: flex; align-items: center; justify-content: center;
    position: relative;
    z-index: 1;
  }
  /* Replace this img with your actual photo */
  .photo-inner img {
    width: 100%; height: 100%;
    object-fit: cover;
    border-radius: 50%;
  }
  .photo-placeholder {
    font-family: var(--font-head);
    font-size: 64px;
    font-weight: 900;
    background: linear-gradient(135deg, var(--cyan), var(--green));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .stats-row {
    display: flex; gap: 20px; flex-wrap: wrap; justify-content: center;
  }
  .stat-card {
    text-align: center;
    padding: 14px 20px;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 4px;
    min-width: 90px;
    position: relative;
    overflow: hidden;
  }
  .stat-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, var(--cyan), var(--green));
  }
  .stat-num {
    font-family: var(--font-head);
    font-size: 28px;
    font-weight: 900;
    color: var(--cyan);
  }
  .stat-lbl {
    font-family: var(--font-mono);
    font-size: 10px;
    letter-spacing: 1px;
    color: var(--muted);
    margin-top: 2px;
  }

  /* ─── SECTION HEADERS ─── */
  .section-header {
    text-align: center;
    margin-bottom: 60px;
  }
  .section-tag {
    font-family: var(--font-mono);
    font-size: 11px;
    letter-spacing: 3px;
    color: var(--cyan);
    text-transform: uppercase;
    margin-bottom: 12px;
  }
  .section-title {
    font-family: var(--font-head);
    font-size: clamp(28px, 3vw, 44px);
    font-weight: 800;
    color: var(--text);
    line-height: 1.1;
  }
  .section-title span {
    background: linear-gradient(90deg, var(--cyan), var(--green));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .section-line {
    width: 60px; height: 3px;
    background: linear-gradient(90deg, var(--cyan), var(--green));
    margin: 16px auto 0;
    border-radius: 2px;
  }

  /* ─── SKILLS SECTION ─── */
  #skills {
    padding: 100px 80px;
    background: linear-gradient(180deg, transparent, var(--bg2) 40%, transparent);
  }

  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 20px;
    max-width: 1200px;
    margin: 0 auto;
  }

  .skill-card {
    position: relative;
    background: var(--bg);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 28px 24px;
    cursor: pointer;
    text-decoration: none;
    color: inherit;
    overflow: hidden;
    transition: border-color .3s, transform .3s, box-shadow .3s;
    display: block;
    animation: fadeUp .6s both;
  }
  .skill-card:hover {
    border-color: var(--cyan);
    transform: translateY(-6px);
    box-shadow: 0 12px 40px rgba(0,212,255,0.15), inset 0 0 30px rgba(0,212,255,0.03);
  }
  /* Gradient top bar */
  .skill-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 3px;
    background: var(--grad);
    opacity: 0;
    transition: opacity .3s;
  }
  .skill-card:hover::before { opacity: 1; }

  /* Glow blob */
  .skill-card::after {
    content: '';
    position: absolute;
    width: 120px; height: 120px;
    border-radius: 50%;
    background: var(--glow);
    filter: blur(40px);
    top: -20px; right: -20px;
    opacity: 0;
    transition: opacity .4s;
  }
  .skill-card:hover::after { opacity: 0.4; }

  .skill-icon {
    font-size: 36px;
    margin-bottom: 14px;
    display: block;
  }
  .skill-num {
    position: absolute; top: 20px; right: 20px;
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 1px;
  }
  .skill-name {
    font-family: var(--font-head);
    font-size: 18px;
    font-weight: 700;
    color: var(--text);
    margin-bottom: 8px;
    line-height: 1.2;
  }
  .skill-desc {
    font-family: var(--font-ui);
    font-size: 13px;
    color: var(--muted);
    line-height: 1.6;
    margin-bottom: 16px;
  }
  .skill-tags { display: flex; gap: 6px; flex-wrap: wrap; }
  .skill-tag {
    font-family: var(--font-mono);
    font-size: 10px;
    letter-spacing: 1px;
    padding: 3px 8px;
    background: rgba(0,212,255,0.06);
    border: 1px solid rgba(0,212,255,0.2);
    border-radius: 2px;
    color: var(--cyan);
  }
  .skill-arrow {
    position: absolute; bottom: 20px; right: 20px;
    font-size: 18px;
    color: var(--muted);
    transition: color .3s, transform .3s;
  }
  .skill-card:hover .skill-arrow { color: var(--cyan); transform: translate(3px, -3px); }

  /* ─── PROJECT SECTIONS ─── */
  .project-section {
    padding: 100px 80px;
    border-top: 1px solid rgba(255,255,255,0.04);
    position: relative;
  }
  .project-section:nth-child(odd) { background: var(--bg2); }

  .project-inner {
    max-width: 1100px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 60px;
    align-items: center;
  }
  .project-inner.reverse { direction: rtl; }
  .project-inner.reverse > * { direction: ltr; }

  .project-label {
    font-family: var(--font-mono);
    font-size: 11px;
    letter-spacing: 3px;
    color: var(--green);
    text-transform: uppercase;
    margin-bottom: 12px;
  }
  .project-title {
    font-family: var(--font-head);
    font-size: clamp(22px, 2.5vw, 34px);
    font-weight: 800;
    color: var(--text);
    line-height: 1.2;
    margin-bottom: 16px;
  }
  .project-desc {
    font-size: 15px;
    line-height: 1.8;
    color: var(--muted);
    margin-bottom: 24px;
  }
  .project-tools { display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 28px; }
  .project-tool {
    font-family: var(--font-mono);
    font-size: 11px;
    padding: 4px 12px;
    border: 1px solid var(--border);
    border-radius: 2px;
    color: var(--text);
    letter-spacing: .5px;
  }

  /* PROJECT VISUAL CARD */
  .project-visual {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 32px;
    position: relative;
    overflow: hidden;
    min-height: 280px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  .project-visual::before {
    content: '';
    position: absolute; inset: 0;
    background: var(--vis-bg, radial-gradient(ellipse at top right, rgba(0,212,255,0.08) 0%, transparent 60%));
  }
  .vis-header {
    display: flex; align-items: center; gap: 8px; margin-bottom: 20px;
  }
  .vis-dot { width: 10px; height: 10px; border-radius: 50%; }
  .vis-title {
    font-family: var(--font-mono);
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 1px;
    flex: 1;
    text-align: center;
  }

  /* SVG diagrams inside visuals */
  .vis-svg { width: 100%; max-height: 200px; }

  /* ─── FOOTER ─── */
  footer {
    text-align: center;
    padding: 60px 40px;
    border-top: 1px solid var(--border);
    position: relative; z-index: 1;
  }
  .footer-name {
    font-family: var(--font-head);
    font-size: 28px;
    font-weight: 900;
    background: linear-gradient(90deg, var(--cyan), var(--green));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 8px;
  }
  .footer-sub {
    font-family: var(--font-mono);
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 2px;
    margin-bottom: 24px;
  }
  .footer-links { display: flex; gap: 20px; justify-content: center; margin-bottom: 30px; }
  .footer-links a {
    font-family: var(--font-ui);
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 1px;
    color: var(--muted);
    text-decoration: none;
    border: 1px solid var(--border);
    padding: 8px 20px;
    border-radius: 2px;
    transition: all .25s;
    text-transform: uppercase;
  }
  .footer-links a:hover { border-color: var(--cyan); color: var(--cyan); background: rgba(0,212,255,0.05); }
  .footer-copy {
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--muted);
    opacity: .5;
  }

  /* ─── SCAN LINE EFFECT ─── */
  .scanline {
    position: fixed; inset: 0;
    background: repeating-linear-gradient(
      to bottom,
      transparent 0px,
      transparent 3px,
      rgba(0,0,0,0.03) 3px,
      rgba(0,0,0,0.03) 4px
    );
    pointer-events: none;
    z-index: 9999;
    opacity: .4;
  }

  /* ─── DECORATIVE SIGNAL WAVE ─── */
  .wave-divider {
    display: flex; align-items: center; gap: 16px;
    max-width: 800px; margin: 0 auto 60px;
    opacity: .3;
  }
  .wave-line { flex: 1; height: 1px; background: var(--cyan); }
  .wave-icon { font-family: var(--font-mono); font-size: 14px; color: var(--cyan); }

  /* ─── ANIMATIONS ─── */
  @keyframes fadeDown {
    from { opacity: 0; transform: translateY(-20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes spin {
    to { transform: rotate(360deg); }
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; box-shadow: 0 0 8px var(--green); }
    50% { opacity: .4; box-shadow: none; }
  }
  @keyframes blink {
    50% { opacity: 0; }
  }
  @keyframes dash {
    to { stroke-dashoffset: 0; }
  }
  @keyframes glow-pulse {
    0%, 100% { opacity: .6; }
    50% { opacity: 1; }
  }

  /* ─── SKILL CARD DELAY ─── */
  .skill-card:nth-child(1) { animation-delay: .05s; }
  .skill-card:nth-child(2) { animation-delay: .10s; }
  .skill-card:nth-child(3) { animation-delay: .15s; }
  .skill-card:nth-child(4) { animation-delay: .20s; }
  .skill-card:nth-child(5) { animation-delay: .25s; }
  .skill-card:nth-child(6) { animation-delay: .30s; }
  .skill-card:nth-child(7) { animation-delay: .35s; }
  .skill-card:nth-child(8) { animation-delay: .40s; }

  /* ─── RESPONSIVE ─── */
  @media (max-width: 900px) {
    #hero { grid-template-columns: 1fr; padding: 100px 30px 60px; gap: 40px; }
    .hero-right { order: -1; }
    #skills, .project-section { padding: 70px 30px; }
    .project-inner { grid-template-columns: 1fr; gap: 32px; }
    .project-inner.reverse { direction: ltr; }
    nav { padding: 0 20px; }
    .nav-links { gap: 16px; }
    .skills-grid { grid-template-columns: 1fr 1fr; }
  }
  @media (max-width: 580px) {
    .skills-grid { grid-template-columns: 1fr; }
    .nav-links { display: none; }
    .photo-frame { width: 200px; height: 200px; }
    .hero-name { font-size: 32px; }
  }

  /* ─── LOOP DIAGRAM SVG STYLES ─── */
  .loop-line { stroke: var(--cyan); stroke-width: 1.5; fill: none; }
  .loop-box { fill: var(--bg2); stroke: var(--cyan); stroke-width: 1.5; rx: 4; }
  .loop-txt { fill: var(--text); font-family: 'Share Tech Mono', monospace; font-size: 9px; }
  .loop-signal { stroke: var(--green); stroke-width: 2; fill: none; stroke-dasharray: 5,3; animation: dash 2s linear infinite; stroke-dashoffset: 30; }

  /* ─── SCADA ─── */
  .scada-screen {
    background: #000d18;
    border: 1px solid var(--cyan);
    border-radius: 4px;
    padding: 16px;
    font-family: var(--font-mono);
    font-size: 12px;
    color: var(--green);
    position: relative;
    overflow: hidden;
  }
  .scada-bar { display: flex; justify-content: space-between; margin-bottom: 10px; color: var(--cyan); font-size: 10px; }
  .scada-val { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; }
  .scada-item { background: rgba(0,212,255,0.06); border: 1px solid rgba(0,212,255,0.2); padding: 6px 10px; border-radius: 2px; }
  .scada-lbl { color: var(--muted); font-size: 9px; }
  .scada-num { color: var(--green); font-size: 14px; font-weight: bold; animation: glow-pulse 2s infinite; }

  .pid-box { fill: none; stroke: var(--text); stroke-width: 1; }
  .pid-circle { fill: none; stroke: var(--cyan); stroke-width: 1.5; }
  .pid-line { stroke: var(--muted); stroke-width: 1; fill: none; }
  .pid-txt { fill: var(--muted); font-family: 'Share Tech Mono', monospace; font-size: 8px; }
  .pid-label { fill: var(--cyan); font-family: 'Share Tech Mono', monospace; font-size: 8px; }

  .kicad-visual {
    display: grid; grid-template-columns: repeat(5, 1fr); gap: 10px; padding: 10px;
  }
  .kicad-comp {
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 8px 4px;
    text-align: center;
    font-family: var(--font-mono);
    font-size: 9px;
    color: var(--muted);
    background: var(--bg);
    transition: border-color .3s, color .3s;
  }
  .kicad-comp:hover { border-color: var(--cyan); color: var(--cyan); }
  .kicad-comp .sym { font-size: 18px; margin-bottom: 4px; }

  /* Sensor waveform */
  .wave-svg { animation: glow-pulse 3s infinite; }
</style>
</head>
<body>

<div class="scanline"></div>

<!-- ─── NAV ─── -->
<nav>
  <div class="nav-logo">EE<span>.</span>PORT<span>_</span></div>
  <div class="nav-links">
    <a href="#hero">Home</a>
    <a href="#skills">Skills</a>
    <a href="#loop">Projects</a>
    <a href="#final">Final Project</a>
  </div>
</nav>

<!-- ─── HERO ─── -->
<section id="hero">
  <div class="hero-left">
    <div class="hero-badge">AVAILABLE FOR INTERNSHIP &amp; COLLABORATION</div>

    <h1 class="hero-name">
      <span class="line1">Your Name</span>
      <span class="line2">Here</span>
    </h1>

    <div class="hero-title">Electrical Engineering Student · Instrumentation &amp; Automation</div>

    <p class="hero-about">
      Passionate about building intelligent measurement systems and automation solutions.
      I bridge the gap between sensors, signals, and software — from field instruments
      to SCADA dashboards and everything in between.
    </p>

    <div class="hero-cta">
      <a href="#skills" class="btn btn-primary">&#9881; Explore My Skills</a>
      <a href="mailto:you@email.com" class="btn btn-outline">&#9993; Contact Me</a>
    </div>
  </div>

  <div class="hero-right">
    <div class="photo-frame">
      <div class="photo-inner">
        <!--
          REPLACE THIS with your actual photo:
          <img src="your-photo.jpg" alt="Your Name" />
          Or keep the initials placeholder below.
        -->
        <div class="photo-placeholder">YN</div>
      </div>
    </div>

    <div class="stats-row">
      <div class="stat-card">
        <div class="stat-num">8+</div>
        <div class="stat-lbl">Projects</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">5+</div>
        <div class="stat-lbl">Tools</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">3yr</div>
        <div class="stat-lbl">Learning</div>
      </div>
    </div>
  </div>
</section>

<!-- ─── SKILLS ─── -->
<section id="skills">
  <div class="section-header">
    <div class="section-tag">// competencies</div>
    <h2 class="section-title">Core <span>Skills</span></h2>
    <div class="section-line"></div>
    <p style="font-size:14px;color:var(--muted);margin-top:14px;font-family:var(--font-mono)">Click any skill to jump to the project</p>
  </div>

  <div class="skills-grid">

    <a href="#loop" class="skill-card" style="--grad:linear-gradient(90deg,#00d4ff,#00ff99);--glow:rgba(0,212,255,0.6);">
      <span class="skill-num">01</span>
      <span class="skill-icon">🔁</span>
      <div class="skill-name">Instrument Loop Diagram</div>
      <div class="skill-desc">Design and read ISA-standard loop diagrams for process control systems.</div>
      <div class="skill-tags"><span class="skill-tag">ISA-5.1</span><span class="skill-tag">Loop Design</span></div>
      <span class="skill-arrow">&#8599;</span>
    </a>

    <a href="#sensors" class="skill-card" style="--grad:linear-gradient(90deg,#00ff99,#00d4ff);--glow:rgba(0,255,153,0.6);">
      <span class="skill-num">02</span>
      <span class="skill-icon">📡</span>
      <div class="skill-name">Sensors & Transducers</div>
      <div class="skill-desc">Self-built sensor circuits for temperature, pressure, flow and proximity sensing.</div>
      <div class="skill-tags"><span class="skill-tag">Arduino</span><span class="skill-tag">ADC</span><span class="skill-tag">Calibration</span></div>
      <span class="skill-arrow">&#8599;</span>
    </a>

    <a href="#kicad" class="skill-card" style="--grad:linear-gradient(90deg,#ffb800,#ff7040);--glow:rgba(255,184,0,0.6);">
      <span class="skill-num">03</span>
      <span class="skill-icon">🖥️</span>
      <div class="skill-name">KiCAD PCB Design</div>
      <div class="skill-desc">Schematic capture and PCB layout for instrumentation circuits.</div>
      <div class="skill-tags"><span class="skill-tag">KiCAD 7</span><span class="skill-tag">PCB Layout</span><span class="skill-tag">Gerber</span></div>
      <span class="skill-arrow">&#8599;</span>
    </a>

    <a href="#autocad" class="skill-card" style="--grad:linear-gradient(90deg,#ff4060,#ff00aa);--glow:rgba(255,64,96,0.6);">
      <span class="skill-num">04</span>
      <span class="skill-icon">📐</span>
      <div class="skill-name">AutoCAD Electrical</div>
      <div class="skill-desc">Professional electrical schematics, panel layouts and wire numbering.</div>
      <div class="skill-tags"><span class="skill-tag">AutoCAD</span><span class="skill-tag">Schematics</span><span class="skill-tag">IEC/ANSI</span></div>
      <span class="skill-arrow">&#8599;</span>
    </a>

    <a href="#pid" class="skill-card" style="--grad:linear-gradient(90deg,#aa00ff,#00d4ff);--glow:rgba(170,0,255,0.6);">
      <span class="skill-num">05</span>
      <span class="skill-icon">🗺️</span>
      <div class="skill-name">P&ID Design</div>
      <div class="skill-desc">Piping & Instrumentation Diagrams for oil & gas and process industries.</div>
      <div class="skill-tags"><span class="skill-tag">ISA-5.1</span><span class="skill-tag">Process</span><span class="skill-tag">HAZOP</span></div>
      <span class="skill-arrow">&#8599;</span>
    </a>

    <a href="#scada" class="skill-card" style="--grad:linear-gradient(90deg,#00d4ff,#aa00ff);--glow:rgba(0,212,255,0.6);">
      <span class="skill-num">06</span>
      <span class="skill-icon">🖧</span>
      <div class="skill-name">SCADA Systems</div>
      <div class="skill-desc">HMI/SCADA development with real-time data acquisition and alarm management.</div>
      <div class="skill-tags"><span class="skill-tag">SCADA</span><span class="skill-tag">HMI</span><span class="skill-tag">OPC-UA</span></div>
      <span class="skill-arrow">&#8599;</span>
    </a>

    <a href="#spi" class="skill-card" style="--grad:linear-gradient(90deg,#00ff99,#ffb800);--glow:rgba(0,255,153,0.6);">
      <span class="skill-num">07</span>
      <span class="skill-icon">⚙️</span>
      <div class="skill-name">SPI Project</div>
      <div class="skill-desc">Smart Process Integration using industrial protocols and communication buses.</div>
      <div class="skill-tags"><span class="skill-tag">HART</span><span class="skill-tag">PROFIBUS</span><span class="skill-tag">Modbus</span></div>
      <span class="skill-arrow">&#8599;</span>
    </a>

    <a href="#final" class="skill-card" style="--grad:linear-gradient(90deg,#ffb800,#00ff99);--glow:rgba(255,184,0,0.7);">
      <span class="skill-num">08</span>
      <span class="skill-icon">🏆</span>
      <div class="skill-name">Final Project</div>
      <div class="skill-desc">Capstone project integrating instrumentation, automation and data systems.</div>
      <div class="skill-tags"><span class="skill-tag">Capstone</span><span class="skill-tag">Integration</span></div>
      <span class="skill-arrow">&#8599;</span>
    </a>

  </div>
</section>

<!-- ─── LOOP DIAGRAM ─── -->
<section id="loop" class="project-section">
  <div class="project-inner">
    <div>
      <div class="project-label">// project 01</div>
      <h3 class="project-title">Instrument Loop Diagram Design</h3>
      <p class="project-desc">
        Developed ISA-5.1 compliant loop diagrams for a process control system, 
        documenting signal paths from field instruments through junction boxes to 
        the DCS/PLC. Includes 4–20 mA wiring, power supply, and grounding details.
      </p>
      <div class="project-tools">
        <span class="project-tool">AutoCAD</span>
        <span class="project-tool">ISA-5.1 Standard</span>
        <span class="project-tool">HART Protocol</span>
        <span class="project-tool">DCS Integration</span>
      </div>
      <a href="#" class="btn btn-outline" style="font-size:12px;padding:10px 22px;">&#8599; View Diagrams</a>
    </div>
    <div class="project-visual" style="--vis-bg:radial-gradient(ellipse at top right,rgba(0,212,255,0.1) 0%,transparent 60%);">
      <div class="vis-header">
        <div class="vis-dot" style="background:#ff4060"></div>
        <div class="vis-dot" style="background:#ffb800"></div>
        <div class="vis-dot" style="background:#00ff99"></div>
        <div class="vis-title">loop_diagram.dwg</div>
      </div>
      <svg viewBox="0 0 360 200" class="vis-svg" xmlns="http://www.w3.org/2000/svg">
        <!-- Field Instrument -->
        <rect x="10" y="80" width="70" height="40" rx="4" class="loop-box"/>
        <text x="45" y="96" class="loop-txt" text-anchor="middle">TT-101</text>
        <text x="45" y="108" class="loop-txt" text-anchor="middle" fill="#5a7a99">TEMP TX</text>
        <!-- Signal line -->
        <line x1="80" y1="100" x2="120" y2="100" class="loop-signal"/>
        <text x="100" y="94" class="loop-txt" text-anchor="middle" fill="#ffb800">4-20mA</text>
        <!-- JB -->
        <rect x="120" y="82" width="50" height="36" rx="3" class="loop-box"/>
        <text x="145" y="98" class="loop-txt" text-anchor="middle">JB-101</text>
        <text x="145" y="110" class="loop-txt" text-anchor="middle" fill="#5a7a99">JB</text>
        <line x1="170" y1="100" x2="210" y2="100" class="loop-signal"/>
        <!-- AI Module -->
        <rect x="210" y="75" width="60" height="50" rx="4" class="loop-box"/>
        <text x="240" y="93" class="loop-txt" text-anchor="middle">AI-101</text>
        <text x="240" y="105" class="loop-txt" text-anchor="middle" fill="#5a7a99">DCS/PLC</text>
        <text x="240" y="117" class="loop-txt" text-anchor="middle" fill="#5a7a99">INPUT</text>
        <!-- Indication -->
        <line x1="270" y1="100" x2="310" y2="100" stroke="#00d4ff" stroke-width="1" fill="none"/>
        <circle cx="325" cy="100" r="15" class="pid-circle"/>
        <text x="325" y="97" class="loop-txt" text-anchor="middle" fill="#00d4ff">TI</text>
        <text x="325" y="108" class="loop-txt" text-anchor="middle" fill="#00d4ff">101</text>
        <!-- Power supply line -->
        <line x1="145" y1="60" x2="145" y2="82" stroke="#ffb800" stroke-width="1" stroke-dasharray="3,2"/>
        <rect x="115" y="44" width="60" height="16" rx="2" fill="none" stroke="#ffb800" stroke-width="1"/>
        <text x="145" y="55" class="loop-txt" text-anchor="middle" fill="#ffb800">24 VDC PS</text>
        <!-- GND -->
        <line x1="45" y1="120" x2="45" y2="150" stroke="#5a7a99" stroke-width="1"/>
        <line x1="35" y1="150" x2="55" y2="150" stroke="#5a7a99" stroke-width="1.5"/>
        <line x1="38" y1="154" x2="52" y2="154" stroke="#5a7a99" stroke-width="1"/>
        <line x1="41" y1="158" x2="49" y2="158" stroke="#5a7a99" stroke-width="1"/>
        <text x="62" y="157" class="loop-txt" fill="#5a7a99">GND</text>
        <!-- Labels -->
        <text x="10" y="170" class="loop-txt" fill="#00d4ff">FIELD</text>
        <text x="125" y="170" class="loop-txt" fill="#00d4ff">MARSHALLING</text>
        <text x="215" y="170" class="loop-txt" fill="#00d4ff">CONTROL ROOM</text>
      </svg>
    </div>
  </div>
</section>

<!-- ─── SENSORS ─── -->
<section id="sensors" class="project-section">
  <div class="project-inner reverse">
    <div>
      <div class="project-label">// project 02</div>
      <h3 class="project-title">Sensors Self Projects</h3>
      <p class="project-desc">
        Built sensor interfacing circuits for temperature (PT100/RTD, NTC Thermistor), 
        pressure (MPX5700), proximity (IR, ultrasonic HC-SR04), and flow (YF-S201). 
        Includes signal conditioning, ADC interfacing and calibration routines.
      </p>
      <div class="project-tools">
        <span class="project-tool">Arduino / STM32</span>
        <span class="project-tool">Op-Amp Circuits</span>
        <span class="project-tool">ADC Interfacing</span>
        <span class="project-tool">Python (matplotlib)</span>
      </div>
      <a href="#" class="btn btn-outline" style="font-size:12px;padding:10px 22px;">&#8599; View Projects</a>
    </div>
    <div class="project-visual" style="--vis-bg:radial-gradient(ellipse at bottom left,rgba(0,255,153,0.1) 0%,transparent 60%);">
      <div class="vis-header">
        <div class="vis-dot" style="background:#ff4060"></div>
        <div class="vis-dot" style="background:#ffb800"></div>
        <div class="vis-dot" style="background:#00ff99"></div>
        <div class="vis-title">sensor_data.py</div>
      </div>
      <svg viewBox="0 0 360 190" class="vis-svg wave-svg" xmlns="http://www.w3.org/2000/svg">
        <!-- Grid -->
        <line x1="30" y1="20" x2="30" y2="170" stroke="#1a2a3a" stroke-width="1"/>
        <line x1="30" y1="170" x2="350" y2="170" stroke="#1a2a3a" stroke-width="1"/>
        <!-- Y axis labels -->
        <text x="24" y="40" class="loop-txt" text-anchor="end" fill="#5a7a99">100</text>
        <text x="24" y="80" class="loop-txt" text-anchor="end" fill="#5a7a99">75</text>
        <text x="24" y="120" class="loop-txt" text-anchor="end" fill="#5a7a99">50</text>
        <text x="24" y="160" class="loop-txt" text-anchor="end" fill="#5a7a99">25</text>
        <!-- Temperature waveform (smooth) -->
        <polyline points="30,120 70,110 110,90 150,75 190,68 230,72 270,85 310,100 350,95"
          stroke="#00d4ff" stroke-width="2" fill="none"/>
        <!-- Pressure waveform -->
        <polyline points="30,150 70,148 110,130 150,125 190,115 230,120 270,135 310,140 350,138"
          stroke="#00ff99" stroke-width="2" fill="none" stroke-dasharray="4,2"/>
        <!-- Dots -->
        <circle cx="190" cy="68" r="4" fill="#00d4ff"/>
        <circle cx="190" cy="115" r="4" fill="#00ff99"/>
        <!-- Legend -->
        <line x1="50" y1="22" x2="70" y2="22" stroke="#00d4ff" stroke-width="2"/>
        <text x="75" y="26" class="loop-txt" fill="#00d4ff">Temperature (°C)</text>
        <line x1="160" y1="22" x2="180" y2="22" stroke="#00ff99" stroke-width="2" stroke-dasharray="4,2"/>
        <text x="185" y="26" class="loop-txt" fill="#00ff99">Pressure (kPa)</text>
        <!-- Annotation -->
        <line x1="190" y1="68" x2="220" y2="48" stroke="#00d4ff" stroke-width="1" stroke-dasharray="2,2"/>
        <text x="222" y="45" class="loop-txt" fill="#00d4ff">Peak: 97°C</text>
      </svg>
    </div>
  </div>
</section>

<!-- ─── KICAD ─── -->
<section id="kicad" class="project-section">
  <div class="project-inner">
    <div>
      <div class="project-label">// project 03</div>
      <h3 class="project-title">KiCAD PCB Design</h3>
      <p class="project-desc">
        Designed instrumentation amplifier PCBs for sensor signal conditioning, 
        including 4-layer stack-ups with controlled impedance traces and ground pours.
        From schematic capture to Gerber file generation and BOM export.
      </p>
      <div class="project-tools">
        <span class="project-tool">KiCAD 7.0</span>
        <span class="project-tool">4-Layer PCB</span>
        <span class="project-tool">DRC / ERC</span>
        <span class="project-tool">Gerber Export</span>
      </div>
      <a href="#" class="btn btn-outline" style="font-size:12px;padding:10px 22px;">&#8599; View Schematics</a>
    </div>
    <div class="project-visual" style="--vis-bg:radial-gradient(ellipse at top right,rgba(255,184,0,0.08) 0%,transparent 60%);">
      <div class="vis-header">
        <div class="vis-dot" style="background:#ff4060"></div>
        <div class="vis-dot" style="background:#ffb800"></div>
        <div class="vis-dot" style="background:#00ff99"></div>
        <div class="vis-title">instrumentation_amp.kicad_pcb</div>
      </div>
      <div class="kicad-visual">
        <div class="kicad-comp"><div class="sym">⚡</div>U1<br>INA128</div>
        <div class="kicad-comp"><div class="sym">〰</div>R1<br>10kΩ</div>
        <div class="kicad-comp"><div class="sym">⊟</div>C1<br>100nF</div>
        <div class="kicad-comp"><div class="sym">🔌</div>J1<br>4-Pin</div>
        <div class="kicad-comp"><div class="sym">▣</div>U2<br>REF02</div>
        <div class="kicad-comp"><div class="sym">〰</div>R2<br>1kΩ</div>
        <div class="kicad-comp"><div class="sym">〰</div>R3<br>47Ω</div>
        <div class="kicad-comp"><div class="sym">⊟</div>C2<br>10µF</div>
        <div class="kicad-comp"><div class="sym">⊡</div>U3<br>MCP602</div>
        <div class="kicad-comp"><div class="sym">🔌</div>J2<br>SMA</div>
      </div>
      <div style="text-align:center;margin-top:10px;">
        <span style="font-family:var(--font-mono);font-size:10px;color:var(--green);">✓ DRC: 0 Errors &nbsp;|&nbsp; ✓ ERC: 0 Warnings &nbsp;|&nbsp; 4 Layers</span>
      </div>
    </div>
  </div>
</section>

<!-- ─── AUTOCAD ─── -->
<section id="autocad" class="project-section">
  <div class="project-inner reverse">
    <div>
      <div class="project-label">// project 04</div>
      <h3 class="project-title">AutoCAD Electrical Design</h3>
      <p class="project-desc">
        Created professional electrical panel layouts and wiring schematics using 
        AutoCAD Electrical. Implements IEC/ANSI symbols, automatic wire numbering, 
        and reports generation for BOM and terminal strips.
      </p>
      <div class="project-tools">
        <span class="project-tool">AutoCAD Electrical</span>
        <span class="project-tool">IEC 60617</span>
        <span class="project-tool">Panel Layout</span>
        <span class="project-tool">Wire Numbering</span>
      </div>
      <a href="#" class="btn btn-outline" style="font-size:12px;padding:10px 22px;">&#8599; View Drawings</a>
    </div>
    <div class="project-visual" style="--vis-bg:radial-gradient(ellipse at bottom right,rgba(255,64,96,0.08) 0%,transparent 60%);">
      <div class="vis-header">
        <div class="vis-dot" style="background:#ff4060"></div>
        <div class="vis-dot" style="background:#ffb800"></div>
        <div class="vis-dot" style="background:#00ff99"></div>
        <div class="vis-title">panel_layout.dwg</div>
      </div>
      <svg viewBox="0 0 360 190" class="vis-svg" xmlns="http://www.w3.org/2000/svg">
        <!-- Panel outline -->
        <rect x="20" y="10" width="320" height="170" rx="4" fill="none" stroke="#5a7a99" stroke-width="1.5"/>
        <!-- Title block -->
        <rect x="20" y="150" width="320" height="30" fill="#0c1220" stroke="#5a7a99" stroke-width="1"/>
        <text x="35" y="168" class="loop-txt" fill="#5a7a99">PANEL: MCC-01</text>
        <text x="200" y="168" class="loop-txt" fill="#5a7a99">SHEET: 01/05</text>
        <text x="300" y="168" class="loop-txt" fill="#ffb800">REV: A</text>
        <!-- Circuit breaker row -->
        <rect x="35" y="25" width="18" height="30" rx="2" fill="#0c1220" stroke="#00d4ff" stroke-width="1"/>
        <text x="44" y="43" class="loop-txt" text-anchor="middle" fill="#00d4ff">CB1</text>
        <rect x="60" y="25" width="18" height="30" rx="2" fill="#0c1220" stroke="#00d4ff" stroke-width="1"/>
        <text x="69" y="43" class="loop-txt" text-anchor="middle" fill="#00d4ff">CB2</text>
        <rect x="85" y="25" width="18" height="30" rx="2" fill="#0c1220" stroke="#00d4ff" stroke-width="1"/>
        <text x="94" y="43" class="loop-txt" text-anchor="middle" fill="#00d4ff">CB3</text>
        <!-- Contactor -->
        <rect x="130" y="20" width="40" height="45" rx="3" fill="#0c1220" stroke="#ffb800" stroke-width="1.5"/>
        <text x="150" y="37" class="loop-txt" text-anchor="middle" fill="#ffb800">KM1</text>
        <text x="150" y="49" class="loop-txt" text-anchor="middle" fill="#5a7a99">Contactor</text>
        <text x="150" y="61" class="loop-txt" text-anchor="middle" fill="#5a7a99">25A</text>
        <!-- Relay -->
        <rect x="190" y="22" width="35" height="40" rx="3" fill="#0c1220" stroke="#00ff99" stroke-width="1.5"/>
        <text x="207" y="38" class="loop-txt" text-anchor="middle" fill="#00ff99">K1</text>
        <text x="207" y="50" class="loop-txt" text-anchor="middle" fill="#5a7a99">Relay</text>
        <!-- PLC -->
        <rect x="245" y="18" width="80" height="50" rx="4" fill="#0c1220" stroke="#00d4ff" stroke-width="1.5"/>
        <text x="285" y="35" class="loop-txt" text-anchor="middle" fill="#00d4ff">PLC MODULE</text>
        <text x="285" y="47" class="loop-txt" text-anchor="middle" fill="#5a7a99">CPU + 16DI/DO</text>
        <text x="285" y="59" class="loop-txt" text-anchor="middle" fill="#5a7a99">Modbus RTU</text>
        <!-- Terminal strip -->
        <rect x="35" y="100" width="290" height="20" rx="2" fill="#0a0e14" stroke="#5a7a99" stroke-width="1"/>
        <text x="180" y="113" class="loop-txt" text-anchor="middle" fill="#5a7a99">TERMINAL STRIP X1 — Wire Numbers: 101–132</text>
        <!-- Wires -->
        <line x1="44" y1="55" x2="44" y2="100" stroke="#ff4060" stroke-width="1.5"/>
        <line x1="69" y1="55" x2="69" y2="100" stroke="#00d4ff" stroke-width="1.5"/>
        <line x1="150" y1="65" x2="150" y2="100" stroke="#ffb800" stroke-width="1.5"/>
        <line x1="285" y1="68" x2="285" y2="100" stroke="#00ff99" stroke-width="1.5"/>
        <!-- Wire numbers -->
        <text x="47" y="80" class="loop-txt" fill="#ff4060">L</text>
        <text x="72" y="80" class="loop-txt" fill="#00d4ff">N</text>
        <text x="153" y="80" class="loop-txt" fill="#ffb800">101</text>
        <text x="288" y="80" class="loop-txt" fill="#00ff99">102</text>
      </svg>
    </div>
  </div>
</section>

<!-- ─── P&ID ─── -->
<section id="pid" class="project-section">
  <div class="project-inner">
    <div>
      <div class="project-label">// project 05</div>
      <h3 class="project-title">P&ID Design Project</h3>
      <p class="project-desc">
        Created Piping and Instrumentation Diagrams for a heat exchanger process unit
        following ISA-5.1 and ISO 10628 standards. Includes control loops, safety 
        instrumented systems, and alarm/trip logic documentation.
      </p>
      <div class="project-tools">
        <span class="project-tool">ISA-5.1 / ISO 10628</span>
        <span class="project-tool">Visio / AutoCAD</span>
        <span class="project-tool">Control Loops</span>
        <span class="project-tool">SIS / SIL</span>
      </div>
      <a href="#" class="btn btn-outline" style="font-size:12px;padding:10px 22px;">&#8599; View P&ID</a>
    </div>
    <div class="project-visual" style="--vis-bg:radial-gradient(ellipse at top left,rgba(170,0,255,0.08) 0%,transparent 60%);">
      <div class="vis-header">
        <div class="vis-dot" style="background:#ff4060"></div>
        <div class="vis-dot" style="background:#ffb800"></div>
        <div class="vis-dot" style="background:#00ff99"></div>
        <div class="vis-title">heat_exchanger_PID.dwg</div>
      </div>
      <svg viewBox="0 0 360 190" class="vis-svg" xmlns="http://www.w3.org/2000/svg">
        <!-- Process pipe (horizontal main) -->
        <line x1="20" y1="95" x2="340" y2="95" stroke="#5a7a99" stroke-width="3"/>
        <!-- Heat Exchanger -->
        <rect x="140" y="65" width="80" height="60" rx="4" class="pid-box" stroke="#00d4ff"/>
        <text x="180" y="88" class="pid-label" text-anchor="middle">HE-101</text>
        <text x="180" y="100" class="pid-txt" text-anchor="middle">Heat Exchanger</text>
        <text x="180" y="113" class="pid-txt" text-anchor="middle">Shell &amp; Tube</text>
        <!-- Valve 1 (control) -->
        <polygon points="60,85 60,105 80,95" fill="#0c1220" stroke="#00ff99" stroke-width="1.5"/>
        <polygon points="80,85 80,105 60,95" fill="#0c1220" stroke="#00ff99" stroke-width="1.5"/>
        <line x1="70" y1="75" x2="70" y2="85" stroke="#00ff99" stroke-width="1.5"/>
        <!-- FIC -->
        <circle cx="70" cy="62" r="13" class="pid-circle"/>
        <text x="70" y="59" class="loop-txt" text-anchor="middle" fill="#00d4ff">FIC</text>
        <text x="70" y="70" class="loop-txt" text-anchor="middle" fill="#00d4ff">101</text>
        <!-- Flow transmitter -->
        <circle cx="110" cy="95" r="10" fill="#0c1220" stroke="#5a7a99" stroke-width="1"/>
        <text x="110" y="92" class="pid-txt" text-anchor="middle">FT</text>
        <text x="110" y="102" class="pid-txt" text-anchor="middle">101</text>
        <line x1="110" y1="85" x2="70" y2="75" stroke="#ffb800" stroke-width="1" stroke-dasharray="3,2"/>
        <!-- Temperature indicator -->
        <circle cx="240" cy="95" r="10" fill="#0c1220" stroke="#5a7a99" stroke-width="1"/>
        <text x="240" y="92" class="pid-txt" text-anchor="middle">TT</text>
        <text x="240" y="102" class="pid-txt" text-anchor="middle">101</text>
        <!-- Valve 2 (safety) -->
        <polygon points="290,85 290,105 310,95" fill="#0c1220" stroke="#ff4060" stroke-width="1.5"/>
        <polygon points="310,85 310,105 290,95" fill="#0c1220" stroke="#ff4060" stroke-width="1.5"/>
        <line x1="300" y1="75" x2="300" y2="85" stroke="#ff4060" stroke-width="1.5"/>
        <circle cx="300" cy="62" r="13" class="pid-circle" stroke="#ff4060"/>
        <text x="300" y="59" class="loop-txt" text-anchor="middle" fill="#ff4060">PSV</text>
        <text x="300" y="70" class="loop-txt" text-anchor="middle" fill="#ff4060">101</text>
        <!-- Labels -->
        <text x="30" y="85" class="pid-txt" fill="#5a7a99">IN</text>
        <text x="320" y="85" class="pid-txt" fill="#5a7a99">OUT</text>
      </svg>
    </div>
  </div>
</section>

<!-- ─── SCADA ─── -->
<section id="scada" class="project-section">
  <div class="project-inner reverse">
    <div>
      <div class="project-label">// project 06</div>
      <h3 class="project-title">SCADA Project</h3>
      <p class="project-desc">
        Built a SCADA system for a water treatment plant simulation using WinCC / 
        Ignition. Features real-time trending, alarm management, historian, and 
        remote access over OPC-UA. Connected to a simulated S7-1200 PLC.
      </p>
      <div class="project-tools">
        <span class="project-tool">Ignition / WinCC</span>
        <span class="project-tool">OPC-UA</span>
        <span class="project-tool">S7-1200 PLC</span>
        <span class="project-tool">Historian</span>
      </div>
      <a href="#" class="btn btn-outline" style="font-size:12px;padding:10px 22px;">&#8599; View SCADA Demo</a>
    </div>
    <div class="project-visual" style="--vis-bg:radial-gradient(ellipse at top right,rgba(0,212,255,0.07) 0%,transparent 60%);">
      <div class="vis-header">
        <div class="vis-dot" style="background:#ff4060"></div>
        <div class="vis-dot" style="background:#ffb800"></div>
        <div class="vis-dot" style="background:#00ff99"></div>
        <div class="vis-title">SCADA_HMI — Water Treatment</div>
      </div>
      <div class="scada-screen">
        <div class="scada-bar">
          <span>&#9679; ONLINE</span>
          <span>PLANT: WTP-01</span>
          <span id="scada-time">--:--:--</span>
        </div>
        <div class="scada-val">
          <div class="scada-item">
            <div class="scada-lbl">FLOW RATE</div>
            <div class="scada-num" id="sv1">124.3 m³/h</div>
          </div>
          <div class="scada-item">
            <div class="scada-lbl">PRESSURE</div>
            <div class="scada-num" id="sv2">3.42 bar</div>
          </div>
          <div class="scada-item">
            <div class="scada-lbl">LEVEL TANK-1</div>
            <div class="scada-num" id="sv3">78.5 %</div>
          </div>
          <div class="scada-item">
            <div class="scada-lbl">TEMP OUTLET</div>
            <div class="scada-num" id="sv4">24.1 °C</div>
          </div>
        </div>
        <div style="margin-top:10px;font-size:10px;color:#ff4060;">
          ⚠ ALARM: High Level Tank-2 — 09:14:22
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ─── SPI ─── -->
<section id="spi" class="project-section">
  <div class="project-inner">
    <div>
      <div class="project-label">// project 07</div>
      <h3 class="project-title">SPI Project</h3>
      <p class="project-desc">
        Smart Process Integration project connecting field devices through HART 
        multiplexers, Modbus RTU networks, and PROFIBUS DP segments to a unified 
        asset management system. Validates instrument health and generates PMC reports.
      </p>
      <div class="project-tools">
        <span class="project-tool">HART 7</span>
        <span class="project-tool">Modbus RTU/TCP</span>
        <span class="project-tool">PROFIBUS DP</span>
        <span class="project-tool">AMS Device Manager</span>
      </div>
      <a href="#" class="btn btn-outline" style="font-size:12px;padding:10px 22px;">&#8599; View Integration</a>
    </div>
    <div class="project-visual" style="--vis-bg:radial-gradient(ellipse at bottom right,rgba(0,255,153,0.08) 0%,transparent 60%);">
      <div class="vis-header">
        <div class="vis-dot" style="background:#ff4060"></div>
        <div class="vis-dot" style="background:#ffb800"></div>
        <div class="vis-dot" style="background:#00ff99"></div>
        <div class="vis-title">network_topology.svg</div>
      </div>
      <svg viewBox="0 0 360 190" class="vis-svg" xmlns="http://www.w3.org/2000/svg">
        <!-- Top layer: Enterprise -->
        <rect x="130" y="10" width="100" height="28" rx="4" fill="#0c1220" stroke="#ffb800" stroke-width="1.5"/>
        <text x="180" y="22" class="pid-label" text-anchor="middle" fill="#ffb800">AMS SERVER</text>
        <text x="180" y="33" class="pid-txt" text-anchor="middle">Ethernet / OPC-UA</text>
        <!-- Middle layer: Gateway -->
        <rect x="75" y="65" width="80" height="28" rx="3" fill="#0c1220" stroke="#00d4ff" stroke-width="1.5"/>
        <text x="115" y="78" class="pid-label" text-anchor="middle">HART MUX</text>
        <text x="115" y="88" class="pid-txt" text-anchor="middle">32 channels</text>
        <rect x="200" y="65" width="85" height="28" rx="3" fill="#0c1220" stroke="#00d4ff" stroke-width="1.5"/>
        <text x="242" y="78" class="pid-label" text-anchor="middle">MODBUS GW</text>
        <text x="242" y="88" class="pid-txt" text-anchor="middle">RTU → TCP</text>
        <!-- Lines top-mid -->
        <line x1="180" y1="38" x2="115" y2="65" stroke="#ffb800" stroke-width="1" stroke-dasharray="4,2"/>
        <line x1="180" y1="38" x2="242" y2="65" stroke="#ffb800" stroke-width="1" stroke-dasharray="4,2"/>
        <!-- Bottom layer: Field -->
        <circle cx="60" cy="155" r="14" fill="#0c1220" stroke="#00ff99" stroke-width="1.5"/>
        <text x="60" y="152" class="pid-txt" text-anchor="middle" fill="#00ff99">TT-1</text>
        <text x="60" y="163" class="pid-txt" text-anchor="middle" fill="#00ff99">HART</text>
        <circle cx="115" cy="155" r="14" fill="#0c1220" stroke="#00ff99" stroke-width="1.5"/>
        <text x="115" y="152" class="pid-txt" text-anchor="middle" fill="#00ff99">PT-1</text>
        <text x="115" y="163" class="pid-txt" text-anchor="middle" fill="#00ff99">HART</text>
        <circle cx="200" cy="155" r="14" fill="#0c1220" stroke="#00d4ff" stroke-width="1.5"/>
        <text x="200" y="152" class="pid-txt" text-anchor="middle" fill="#00d4ff">FT-1</text>
        <text x="200" y="163" class="pid-txt" text-anchor="middle" fill="#00d4ff">MB</text>
        <circle cx="255" cy="155" r="14" fill="#0c1220" stroke="#00d4ff" stroke-width="1.5"/>
        <text x="255" y="152" class="pid-txt" text-anchor="middle" fill="#00d4ff">LT-1</text>
        <text x="255" y="163" class="pid-txt" text-anchor="middle" fill="#00d4ff">MB</text>
        <circle cx="310" cy="155" r="14" fill="#0c1220" stroke="#aa00ff" stroke-width="1.5"/>
        <text x="310" y="152" class="pid-txt" text-anchor="middle" fill="#aa00ff">VFD</text>
        <text x="310" y="163" class="pid-txt" text-anchor="middle" fill="#aa00ff">PB</text>
        <!-- Lines mid-field -->
        <line x1="115" y1="93" x2="60" y2="141" stroke="#00ff99" stroke-width="1"/>
        <line x1="115" y1="93" x2="115" y2="141" stroke="#00ff99" stroke-width="1"/>
        <line x1="242" y1="93" x2="200" y2="141" stroke="#00d4ff" stroke-width="1"/>
        <line x1="242" y1="93" x2="255" y2="141" stroke="#00d4ff" stroke-width="1"/>
        <line x1="242" y1="93" x2="310" y2="141" stroke="#aa00ff" stroke-width="1"/>
      </svg>
    </div>
  </div>
</section>

<!-- ─── FINAL PROJECT ─── -->
<section id="final" class="project-section" style="background:linear-gradient(180deg,var(--bg2),var(--bg));">
  <div style="max-width:900px;margin:0 auto;">
    <div class="section-header">
      <div class="section-tag">// capstone</div>
      <h2 class="section-title">My Final <span>Project</span></h2>
      <div class="section-line"></div>
    </div>
    <div style="
      background:var(--bg3);
      border:1px solid var(--border);
      border-radius:8px;
      padding:48px;
      position:relative;
      overflow:hidden;
    ">
      <!-- Decorative corner accent -->
      <div style="position:absolute;top:0;left:0;width:120px;height:120px;background:radial-gradient(circle at 0 0,rgba(0,212,255,0.12),transparent 70%);"></div>
      <div style="position:absolute;bottom:0;right:0;width:120px;height:120px;background:radial-gradient(circle at 100% 100%,rgba(0,255,153,0.1),transparent 70%);"></div>

      <div style="position:relative;z-index:1;">
        <div style="display:flex;align-items:center;gap:16px;margin-bottom:24px;">
          <span style="font-size:48px;">🏆</span>
          <div>
            <div style="font-family:var(--font-mono);font-size:11px;letter-spacing:2px;color:var(--amber);margin-bottom:6px;">FINAL YEAR PROJECT</div>
            <h3 style="font-family:var(--font-head);font-size:28px;font-weight:800;color:var(--text);">
              Your Capstone Project Title Here
            </h3>
          </div>
        </div>

        <p style="font-size:16px;line-height:1.85;color:var(--muted);margin-bottom:32px;max-width:700px;">
          Describe your final project here. For example: "Designed and implemented an 
          automated monitoring system for a small-scale industrial boiler, integrating 
          PT100 temperature sensors, pressure transmitters, and a PLC-based control loop 
          with SCADA visualization and remote alarm notification via GSM module."
        </p>

        <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-bottom:32px;">
          <div style="background:var(--bg);border:1px solid var(--border);border-radius:4px;padding:16px;text-align:center;">
            <div style="font-family:var(--font-head);font-size:24px;font-weight:800;color:var(--cyan);">8</div>
            <div style="font-family:var(--font-mono);font-size:10px;letter-spacing:1px;color:var(--muted);margin-top:4px;">SENSOR NODES</div>
          </div>
          <div style="background:var(--bg);border:1px solid var(--border);border-radius:4px;padding:16px;text-align:center;">
            <div style="font-family:var(--font-head);font-size:24px;font-weight:800;color:var(--green);">4</div>
            <div style="font-family:var(--font-mono);font-size:10px;letter-spacing:1px;color:var(--muted);margin-top:4px;">CONTROL LOOPS</div>
          </div>
          <div style="background:var(--bg);border:1px solid var(--border);border-radius:4px;padding:16px;text-align:center;">
            <div style="font-family:var(--font-head);font-size:24px;font-weight:800;color:var(--amber);">A</div>
            <div style="font-family:var(--font-mono);font-size:10px;letter-spacing:1px;color:var(--muted);margin-top:4px;">FINAL GRADE</div>
          </div>
        </div>

        <div style="display:flex;gap:12px;flex-wrap:wrap;margin-bottom:32px;">
          <span class="project-tool">PLC S7-1200</span>
          <span class="project-tool">SCADA Ignition</span>
          <span class="project-tool">PT100 Sensors</span>
          <span class="project-tool">KiCAD PCB</span>
          <span class="project-tool">P&ID Design</span>
          <span class="project-tool">Python Analysis</span>
        </div>

        <div style="display:flex;gap:16px;flex-wrap:wrap;">
          <a href="#" class="btn btn-primary">&#9654; View Full Project</a>
          <a href="#" class="btn btn-outline">&#8962; GitHub Repo</a>
          <a href="#" class="btn btn-outline">&#8681; Download Report</a>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ─── FOOTER ─── -->
<footer>
  <div class="footer-name">Your Name</div>
  <div class="footer-sub">EE · Instrumentation & Automation · Indonesia</div>
  <div class="footer-links">
    <a href="#">GitHub</a>
    <a href="#">LinkedIn</a>
    <a href="#">Email</a>
    <a href="#">Resume</a>
  </div>
  <div class="footer-copy">
    Built with precision. Designed with signal. &copy; 2025
  </div>
</footer>

<!-- ─── JS ─── -->
<script>
  // SCADA live clock
  function updateScadaTime() {
    const now = new Date();
    const t = now.toTimeString().slice(0,8);
    const el = document.getElementById('scada-time');
    if (el) el.textContent = t;
  }
  setInterval(updateScadaTime, 1000);
  updateScadaTime();

  // SCADA live values (simulated)
  const fields = [
    { id: 'sv1', base: 124.3, unit: ' m³/h', range: 3 },
    { id: 'sv2', base: 3.42,  unit: ' bar',  range: 0.15 },
    { id: 'sv3', base: 78.5,  unit: ' %',    range: 1.5 },
    { id: 'sv4', base: 24.1,  unit: ' °C',   range: 0.3 },
  ];
  setInterval(() => {
    fields.forEach(f => {
      const el = document.getElementById(f.id);
      if (!el) return;
      const v = f.base + (Math.random() - 0.5) * f.range;
      el.textContent = v.toFixed(1) + f.unit;
    });
  }, 2000);

  // Scroll reveal animation
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.style.opacity = '1';
        e.target.style.transform = 'translateY(0)';
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.project-inner, .section-header').forEach(el => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(30px)';
    el.style.transition = 'opacity .7s ease, transform .7s ease';
    observer.observe(el);
  });

  // Typing effect for hero title
  const titleEl = document.querySelector('.hero-title');
  const originalText = titleEl.textContent;
  titleEl.textContent = '';
  let i = 0;
  function typeWriter() {
    if (i < originalText.length) {
      titleEl.textContent += originalText[i++];
      setTimeout(typeWriter, 40);
    }
  }
  setTimeout(typeWriter, 800);

  // Cursor blink on title
  titleEl.style.borderRight = '2px solid var(--amber)';
  titleEl.style.animation = 'blink 1s step-end infinite';
  setTimeout(() => {
    titleEl.style.borderRight = 'none';
    titleEl.style.animation = 'none';
  }, originalText.length * 40 + 1500);
</script>

</body>
</html>
