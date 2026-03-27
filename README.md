<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DevOps Portfolio — GitHub Projects</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500;600&family=Bebas+Neue&family=IBM+Plex+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">

<style>
  :root {
    --bg: #0a0c10;
    --surface: #111318;
    --surface2: #1a1d25;
    --border: #222632;
    --accent: #00e5ff;
    --accent2: #7c3aed;
    --accent3: #f59e0b;
    --green: #22c55e;
    --red: #ef4444;
    --text: #e2e8f0;
    --muted: #64748b;
    --mono: 'IBM Plex Mono', monospace;
    --sans: 'IBM Plex Sans', sans-serif;
    --display: 'Bebas Neue', sans-serif;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    overflow-x: hidden;
    cursor: none;
  }

  .cursor { width:8px;height:8px;background:var(--accent);border-radius:50%;position:fixed;pointer-events:none;z-index:9999;transition:transform .1s ease;mix-blend-mode:screen; }
  .cursor-ring { width:32px;height:32px;border:1px solid rgba(0,229,255,.4);border-radius:50%;position:fixed;pointer-events:none;z-index:9998;transition:transform .15s ease,opacity .2s; }

  body::before {
    content:'';position:fixed;inset:0;
    background-image:linear-gradient(rgba(0,229,255,.03) 1px,transparent 1px),linear-gradient(90deg,rgba(0,229,255,.03) 1px,transparent 1px);
    background-size:48px 48px;z-index:0;pointer-events:none;
  }
  body::after {
    content:'';position:fixed;inset:0;
    background:repeating-linear-gradient(0deg,transparent,transparent 2px,rgba(0,0,0,.08) 2px,rgba(0,0,0,.08) 4px);
    pointer-events:none;z-index:0;
  }

  nav { position:fixed;top:0;left:0;right:0;z-index:100;display:flex;align-items:center;justify-content:space-between;padding:16px 48px;background:rgba(10,12,16,.85);backdrop-filter:blur(12px);border-bottom:1px solid var(--border); }
  .nav-logo { font-family:var(--mono);font-size:13px;color:var(--accent);letter-spacing:.05em; }
  .nav-logo span { color:var(--muted); }
  .nav-links { display:flex;gap:32px;list-style:none; }
  .nav-links a { font-family:var(--mono);font-size:12px;color:var(--muted);text-decoration:none;letter-spacing:.08em;text-transform:uppercase;transition:color .2s; }
  .nav-links a:hover { color:var(--accent); }
  .nav-status { display:flex;align-items:center;gap:8px;font-family:var(--mono);font-size:11px;color:var(--green); }
  .status-dot { width:6px;height:6px;background:var(--green);border-radius:50%;animation:pulse 2s infinite; }
  @keyframes pulse { 0%,100%{opacity:1;transform:scale(1)}50%{opacity:.5;transform:scale(1.3)} }

  .hero { position:relative;z-index:1;min-height:100vh;display:flex;flex-direction:column;justify-content:center;padding:120px 48px 80px;overflow:hidden; }
  .hero-eyebrow { font-family:var(--mono);font-size:12px;color:var(--accent);letter-spacing:.2em;text-transform:uppercase;margin-bottom:24px;display:flex;align-items:center;gap:12px; }
  .hero-eyebrow::before { content:'';width:40px;height:1px;background:var(--accent); }
  .hero-title { font-family:var(--display);font-size:clamp(72px,10vw,140px);line-height:.9;letter-spacing:.02em;color:var(--text);margin-bottom:32px; }
  .hero-title .highlight { -webkit-text-stroke:1px var(--accent);color:transparent; }
  .hero-desc { font-size:16px;color:var(--muted);max-width:600px;line-height:1.7;margin-bottom:48px;font-weight:300; }
  .hero-stats { display:flex;gap:48px; }
  .stat { display:flex;flex-direction:column;gap:4px; }
  .stat-num { font-family:var(--display);font-size:48px;color:var(--accent);line-height:1; }
  .stat-label { font-family:var(--mono);font-size:11px;color:var(--muted);letter-spacing:.1em;text-transform:uppercase; }
  .hero-blob { position:absolute;right:-100px;top:50%;transform:translateY(-50%);width:600px;height:600px;background:radial-gradient(ellipse,rgba(124,58,237,.15) 0%,rgba(0,229,255,.08) 40%,transparent 70%);border-radius:50%;filter:blur(40px);animation:float 8s ease-in-out infinite; }
  @keyframes float { 0%,100%{transform:translateY(-50%) scale(1)}50%{transform:translateY(-55%) scale(1.05)} }

  .terminal-hero { position:absolute;right:48px;top:50%;transform:translateY(-50%);width:440px;background:var(--surface);border:1px solid var(--border);border-radius:8px;overflow:hidden;box-shadow:0 0 60px rgba(0,229,255,.05),0 40px 80px rgba(0,0,0,.6);animation:slideIn .8s ease both; }
  @keyframes slideIn { from{opacity:0;transform:translateY(-40%) translateX(40px)}to{opacity:1;transform:translateY(-50%) translateX(0)} }
  .terminal-bar { background:var(--surface2);padding:10px 16px;display:flex;align-items:center;gap:8px;border-bottom:1px solid var(--border); }
  .t-dot { width:10px;height:10px;border-radius:50%; }
  .t-dot.r{background:#ef4444}.t-dot.y{background:#f59e0b}.t-dot.g{background:#22c55e}
  .terminal-title { font-family:var(--mono);font-size:11px;color:var(--muted);margin-left:8px; }
  .terminal-body { padding:20px;font-family:var(--mono);font-size:12px;line-height:2; }
  .t-line{display:flex;gap:8px}.t-prompt{color:var(--green)}.t-cmd{color:var(--text)}.t-out{color:var(--muted);padding-left:16px}.t-accent{color:var(--accent)}.t-success{color:var(--green)}.t-warn{color:var(--accent3)}
  .t-cursor { display:inline-block;width:8px;height:14px;background:var(--accent);animation:blink 1s step-end infinite;vertical-align:middle; }
  @keyframes blink{0%,100%{opacity:1}50%{opacity:0}}

  section { position:relative;z-index:1;padding:100px 48px; }
  .section-label { font-family:var(--mono);font-size:11px;color:var(--accent);letter-spacing:.2em;text-transform:uppercase;margin-bottom:16px;display:flex;align-items:center;gap:12px; }
  .section-label::after { content:'';flex:1;max-width:60px;height:1px;background:var(--accent); }
  .section-title { font-family:var(--display);font-size:clamp(40px,5vw,64px);line-height:1;margin-bottom:64px; }

  .projects-grid { display:grid;gap:2px; }
  .project-card { background:var(--surface);border:1px solid var(--border);border-radius:4px;overflow:hidden;display:grid;grid-template-columns:280px 1fr;min-height:240px;transition:border-color .3s,box-shadow .3s;animation:fadeUp .6s ease both; }
  .project-card:hover { border-color:rgba(0,229,255,.3);box-shadow:0 0 40px rgba(0,229,255,.05); }
  @keyframes fadeUp{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}
  .project-card:nth-child(1){animation-delay:.1s}.project-card:nth-child(2){animation-delay:.2s}.project-card:nth-child(3){animation-delay:.3s}.project-card:nth-child(4){animation-delay:.4s}.project-card:nth-child(5){animation-delay:.5s}

  .card-sidebar { padding:32px;border-right:1px solid var(--border);display:flex;flex-direction:column;gap:20px;position:relative;overflow:hidden; }
  .card-sidebar::before { content:'';position:absolute;inset:0;background:linear-gradient(135deg,rgba(0,229,255,.04) 0%,transparent 60%); }
  .project-num { font-family:var(--display);font-size:80px;line-height:1;-webkit-text-stroke:1px var(--border);color:transparent;position:absolute;bottom:16px;right:16px; }
  .project-icon { width:48px;height:48px;border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:24px; }
  .icon-infra{background:rgba(0,229,255,.1)}.icon-cicd{background:rgba(124,58,237,.1)}.icon-mon{background:rgba(245,158,11,.1)}.icon-k8s{background:rgba(34,197,94,.1)}.icon-auto{background:rgba(239,68,68,.1)}

  .project-badge { display:inline-flex;align-items:center;gap:6px;font-family:var(--mono);font-size:10px;letter-spacing:.1em;text-transform:uppercase;padding:4px 10px;border-radius:2px;width:fit-content; }
  .badge-infra{background:rgba(0,229,255,.1);color:var(--accent);border:1px solid rgba(0,229,255,.2)}
  .badge-cicd{background:rgba(124,58,237,.1);color:#a78bfa;border:1px solid rgba(124,58,237,.2)}
  .badge-mon{background:rgba(245,158,11,.1);color:var(--accent3);border:1px solid rgba(245,158,11,.2)}
  .badge-k8s{background:rgba(34,197,94,.1);color:var(--green);border:1px solid rgba(34,197,94,.2)}
  .badge-auto{background:rgba(239,68,68,.1);color:#f87171;border:1px solid rgba(239,68,68,.2)}

  .card-main { padding:32px 40px;display:flex;flex-direction:column;gap:20px; }
  .card-header { display:flex;align-items:flex-start;justify-content:space-between;gap:16px; }
  .project-title { font-family:var(--display);font-size:28px;letter-spacing:.02em;line-height:1.1; }
  .project-desc { font-size:14px;color:var(--muted);line-height:1.7;font-weight:300; }
  .tech-tags { display:flex;flex-wrap:wrap;gap:8px; }
  .tag { font-family:var(--mono);font-size:11px;color:var(--muted);padding:3px 10px;border:1px solid var(--border);border-radius:2px;background:var(--surface2);transition:all .2s; }
  .tag:hover { border-color:var(--accent);color:var(--accent); }

  .features { display:grid;grid-template-columns:1fr 1fr;gap:8px; }
  .feature { display:flex;align-items:flex-start;gap:8px;font-size:13px;color:var(--muted);font-weight:300; }
  .feature::before { content:'→';color:var(--accent);font-family:var(--mono);flex-shrink:0;margin-top:1px; }

  .card-footer { display:flex;align-items:center;justify-content:space-between;margin-top:auto;padding-top:16px;border-top:1px solid var(--border); }
  .repo-link { display:flex;align-items:center;gap:8px;font-family:var(--mono);font-size:12px;color:var(--accent);text-decoration:none;letter-spacing:.05em;transition:gap .2s; }
  .repo-link:hover{gap:12px}
  .github-link { display:flex;align-items:center;gap:8px;font-family:var(--mono);font-size:12px;color:var(--accent);text-decoration:none;letter-spacing:.05em;transition:gap .2s; }
  .github-link:hover{gap:12px}
  .repo-meta { display:flex;gap:16px;font-family:var(--mono);font-size:11px;color:var(--muted); }
  .meta-item { display:flex;align-items:center;gap:4px; }

  .readme-grid { display:grid;grid-template-columns:1fr 1fr;gap:24px; }
  .readme-card { background:var(--surface);border:1px solid var(--border);border-radius:4px;overflow:hidden; }
  .readme-card-header { background:var(--surface2);padding:12px 20px;display:flex;align-items:center;gap:12px;border-bottom:1px solid var(--border);font-family:var(--mono);font-size:12px;color:var(--muted); }
  .readme-card-header .file-icon{font-size:14px}
  .readme-body{padding:24px}
  .readme-section-title { font-family:var(--mono);font-size:13px;color:var(--accent);margin-bottom:12px;display:flex;align-items:center;gap:8px; }
  .readme-section-title::before{content:'#';color:var(--muted)}
  .readme-item { display:flex;align-items:flex-start;gap:10px;padding:8px 0;border-bottom:1px solid var(--border);font-size:13px;color:var(--muted);font-weight:300; }
  .readme-item:last-child{border-bottom:none}
  .readme-bullet { width:16px;height:16px;border-radius:2px;flex-shrink:0;margin-top:1px;display:flex;align-items:center;justify-content:center;font-size:10px; }

  .arch-diagram { background:var(--surface);border:1px solid var(--border);border-radius:4px;padding:48px;position:relative;overflow:hidden; }
  .arch-flow { display:flex;align-items:center;justify-content:center;gap:0;flex-wrap:wrap; }
  .arch-node { display:flex;flex-direction:column;align-items:center;gap:8px; }
  .arch-box { padding:12px 20px;border:1px solid;border-radius:4px;font-family:var(--mono);font-size:12px;text-align:center;min-width:100px; }
  .arch-box.internet{border-color:var(--muted);color:var(--muted);background:rgba(100,116,139,.1)}
  .arch-box.lb{border-color:var(--accent);color:var(--accent);background:rgba(0,229,255,.05)}
  .arch-box.asg{border-color:var(--accent2);color:#a78bfa;background:rgba(124,58,237,.05)}
  .arch-box.db{border-color:var(--accent3);color:var(--accent3);background:rgba(245,158,11,.05)}
  .arch-box.cache{border-color:var(--red);color:#f87171;background:rgba(239,68,68,.05)}
  .arch-box.monitor{border-color:var(--green);color:var(--green);background:rgba(34,197,94,.05)}
  .arch-label{font-family:var(--mono);font-size:10px;color:var(--muted)}
  .arch-arrow{font-family:var(--mono);color:var(--border);font-size:18px;padding:0 8px;align-self:center}
  .arch-group{display:flex;flex-direction:column;gap:12px;padding:20px;border:1px dashed var(--border);border-radius:4px}
  .arch-group-label{font-family:var(--mono);font-size:10px;color:var(--muted);text-align:center;margin-bottom:4px;letter-spacing:.1em;text-transform:uppercase}

  .metrics-row { display:grid;grid-template-columns:repeat(4,1fr);gap:2px;margin-bottom:2px; }
  .metric-card { background:var(--surface);border:1px solid var(--border);border-radius:4px;padding:28px; }
  .metric-label { font-family:var(--mono);font-size:11px;color:var(--muted);letter-spacing:.1em;text-transform:uppercase;margin-bottom:12px; }
  .metric-value { font-family:var(--display);font-size:40px;line-height:1;margin-bottom:8px; }
  .metric-sub { font-size:12px;color:var(--muted);font-weight:300; }
  .sparkline{display:block;margin-top:12px}

  /* CTA */
  .cta-section { text-align:center;padding:120px 48px; }
  .cta-label { font-family:var(--mono);font-size:12px;color:var(--accent);letter-spacing:.2em;text-transform:uppercase;margin-bottom:24px; }
  .cta-title { font-family:var(--display);font-size:clamp(48px,6vw,80px);margin-bottom:24px; }
  .cta-desc { font-size:16px;color:var(--muted);max-width:520px;margin:0 auto 48px;line-height:1.7;font-weight:300; }

  .btn-row { display:flex;gap:16px;justify-content:center;flex-wrap:wrap;align-items:center; }
  .btn { display:inline-flex;align-items:center;gap:8px;padding:14px 32px;font-family:var(--mono);font-size:13px;letter-spacing:.08em;text-transform:uppercase;text-decoration:none;border-radius:2px;cursor:none;transition:all .2s; }
  .btn-primary { background:var(--accent);color:#000;border:1px solid var(--accent); }
  .btn-primary:hover { background:transparent;color:var(--accent); }
  .btn-secondary { background:transparent;color:var(--text);border:1px solid var(--border); }
  .btn-secondary:hover { border-color:var(--accent);color:var(--accent); }

  /* ── CONTACT DROPDOWN ─────────────────────────────────── */
  .contact-wrapper {
    position: relative;
    display: inline-block;
  }

  .btn-contact {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    padding: 14px 28px;
    font-family: var(--mono);
    font-size: 13px;
    letter-spacing: .08em;
    text-transform: uppercase;
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border);
    border-radius: 2px;
    cursor: none;
    transition: all .2s;
    position: relative;
  }

  .btn-contact:hover,
  .contact-wrapper.open .btn-contact {
    border-color: var(--accent);
    color: var(--accent);
  }

  .btn-contact .chevron {
    display: inline-block;
    font-size: 10px;
    transition: transform .2s;
    color: var(--muted);
  }

  .contact-wrapper.open .btn-contact .chevron {
    transform: rotate(180deg);
    color: var(--accent);
  }

  /* Dropdown panel */
  .contact-panel {
    position: absolute;
    bottom: calc(100% + 10px);
    left: 50%;
    transform: translateX(-50%) translateY(8px);
    width: 300px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 4px;
    overflow: hidden;
    opacity: 0;
    pointer-events: none;
    transition: opacity .2s ease, transform .2s ease;
    box-shadow: 0 -20px 60px rgba(0,0,0,.6), 0 0 0 1px rgba(0,229,255,.05);
    z-index: 200;
  }

  .contact-wrapper.open .contact-panel {
    opacity: 1;
    pointer-events: all;
    transform: translateX(-50%) translateY(0);
  }

  .contact-panel-header {
    background: var(--surface2);
    padding: 10px 16px;
    border-bottom: 1px solid var(--border);
    font-family: var(--mono);
    font-size: 10px;
    color: var(--muted);
    letter-spacing: .12em;
    text-transform: uppercase;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .contact-panel-header::before {
    content: '';
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--accent);
    display: inline-block;
    animation: pulse 2s infinite;
  }

  .contact-item {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 16px 20px;
    text-decoration: none;
    color: var(--text);
    transition: background .15s;
    border-bottom: 1px solid var(--border);
    position: relative;
    overflow: hidden;
  }

  .contact-item:last-child { border-bottom: none; }

  .contact-item::before {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 2px;
    background: transparent;
    transition: background .15s;
  }

  .contact-item:hover {
    background: rgba(255,255,255,.02);
  }

  .contact-item.email:hover::before { background: var(--accent); }
  .contact-item.phone:hover::before { background: var(--green); }

  .contact-icon {
    width: 36px; height: 36px;
    border-radius: 6px;
    display: flex; align-items: center; justify-content: center;
    flex-shrink: 0;
    font-size: 16px;
    transition: transform .15s;
  }

  .contact-item:hover .contact-icon { transform: scale(1.1); }

  .contact-item.email .contact-icon { background: rgba(0,229,255,.08); }
  .contact-item.phone .contact-icon { background: rgba(34,197,94,.08); }

  .contact-text { display: flex; flex-direction: column; gap: 2px; min-width: 0; }

  .contact-type {
    font-family: var(--mono);
    font-size: 9px;
    letter-spacing: .15em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .contact-value {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--text);
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    transition: color .15s;
  }

  .contact-item.email:hover .contact-value { color: var(--accent); }
  .contact-item.phone:hover .contact-value { color: var(--green); }

  .contact-arrow {
    margin-left: auto;
    font-family: var(--mono);
    font-size: 12px;
    color: var(--border);
    transition: color .15s, transform .15s;
    flex-shrink: 0;
  }

  .contact-item:hover .contact-arrow {
    transform: translateX(3px);
  }
  .contact-item.email:hover .contact-arrow { color: var(--accent); }
  .contact-item.phone:hover .contact-arrow { color: var(--green); }
  /* ────────────────────────────────────────────────────── */

  footer { position:relative;z-index:1;padding:32px 48px;border-top:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;font-family:var(--mono);font-size:11px;color:var(--muted); }

  .reveal { opacity:0;transform:translateY(24px);transition:opacity .6s ease,transform .6s ease; }
  .reveal.visible { opacity:1;transform:translateY(0); }

  .file-tree { background:var(--surface2);border:1px solid var(--border);border-radius:4px;padding:20px 24px;font-family:var(--mono);font-size:12px;line-height:2; }
  .tree-dir{color:var(--accent)}.tree-file{color:var(--muted)}.tree-comment{color:rgba(100,116,139,.6)}

  .pipeline { display:flex;align-items:center;gap:0;overflow-x:auto;padding:24px 0; }
  .pipe-stage { display:flex;flex-direction:column;align-items:center;gap:8px;flex-shrink:0; }
  .pipe-box { padding:10px 16px;border:1px solid;border-radius:4px;font-family:var(--mono);font-size:11px;letter-spacing:.05em;text-align:center;min-width:90px; }
  .pipe-box.done{border-color:var(--green);color:var(--green);background:rgba(34,197,94,.05)}
  .pipe-box.run{border-color:var(--accent);color:var(--accent);background:rgba(0,229,255,.05);animation:glow 1.5s ease-in-out infinite}
  .pipe-box.pend{border-color:var(--border);color:var(--muted)}
  @keyframes glow{0%,100%{box-shadow:0 0 0 rgba(0,229,255,.3)}50%{box-shadow:0 0 20px rgba(0,229,255,.3)}}
  .pipe-arrow { flex-shrink:0;padding:0 4px;color:var(--border);font-size:18px;align-self:flex-start;margin-top:17px; }
  .pipe-label{font-family:var(--mono);font-size:10px;color:var(--muted)}
  .pipe-time{font-family:var(--mono);font-size:10px;color:var(--muted);opacity:.6}
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<nav>
  <div class="nav-logo">./devops<span>-portfolio</span></div>
  <ul class="nav-links">
    <li><a href="#projects">Projects</a></li>
    <li><a href="#architecture">Architecture</a></li>
    <li><a href="#readme">README</a></li>
  </ul>
  <div class="nav-status">
    <div class="status-dot"></div>
    All systems operational
  </div>
</nav>

<div class="hero">
  <div class="hero-blob"></div>
  <div class="hero-eyebrow">DevOps Engineer — GitHub Portfolio</div>
  <h1 class="hero-title">INFRA.<br>SCALE.<br><span class="highlight">SHIP.</span></h1>
  <p class="hero-desc">A curated collection of production-grade DevOps projects covering infrastructure-as-code, CI/CD pipelines, Kubernetes orchestration, monitoring stacks, and automation tooling.</p>
  <div class="hero-stats">
    <div class="stat"><span class="stat-num">5</span><span class="stat-label">Projects</span></div>
    <div class="stat"><span class="stat-num">3</span><span class="stat-label">Cloud Providers</span></div>
    <div class="stat"><span class="stat-num">12+</span><span class="stat-label">Technologies</span></div>
    <div class="stat"><span class="stat-num">∞</span><span class="stat-label">Scalability</span></div>
  </div>
  <div class="terminal-hero">
    <div class="terminal-bar">
      <div class="t-dot r"></div><div class="t-dot y"></div><div class="t-dot g"></div>
      <span class="terminal-title">bash — devops-portfolio</span>
    </div>
    <div class="terminal-body">
      <div class="t-line"><span class="t-prompt">$</span><span class="t-cmd"> git clone github.com/you/infra-iac</span></div>
      <div class="t-line"><span class="t-out t-success">✓ Cloning into 'infra-iac'...</span></div>
      <div class="t-line"><span class="t-prompt">$</span><span class="t-cmd"> terraform init && terraform plan</span></div>
      <div class="t-line"><span class="t-out t-accent">Plan: 42 resources to add</span></div>
      <div class="t-line"><span class="t-prompt">$</span><span class="t-cmd"> kubectl get pods -n production</span></div>
      <div class="t-line"><span class="t-out t-success">api-6d9f7b8c4-xkp2m    1/1   Running</span></div>
      <div class="t-line"><span class="t-out t-success">worker-5c8d9f4b-vkl7q  1/1   Running</span></div>
      <div class="t-line"><span class="t-out t-success">cache-7b6f8c9d-mnp3r   1/1   Running</span></div>
      <div class="t-line"><span class="t-prompt">$</span><span class="t-cmd"> ./scripts/cost-optimizer.py</span></div>
      <div class="t-line"><span class="t-out t-warn">⚡ Potential savings: $340/mo</span></div>
      <div class="t-line"><span class="t-prompt">$</span><span class="t-cursor"></span></div>
    </div>
  </div>
</div>

<section style="padding:0 48px 80px;">
  <div class="metrics-row reveal">
    <div class="metric-card">
      <div class="metric-label">Deploy Frequency</div>
      <div class="metric-value" style="color:var(--accent)">47×</div>
      <div class="metric-sub">per day, avg across projects</div>
      <svg class="sparkline" width="100%" height="32" viewBox="0 0 200 32"><polyline points="0,28 40,20 80,24 100,8 140,14 160,4 200,10" fill="none" stroke="var(--accent)" stroke-width="1.5" opacity="0.7"/></svg>
    </div>
    <div class="metric-card">
      <div class="metric-label">Mean Recovery Time</div>
      <div class="metric-value" style="color:var(--green)">4m</div>
      <div class="metric-sub">avg incident resolution</div>
      <svg class="sparkline" width="100%" height="32" viewBox="0 0 200 32"><polyline points="0,24 40,28 80,20 100,16 140,12 160,8 200,4" fill="none" stroke="var(--green)" stroke-width="1.5" opacity="0.7"/></svg>
    </div>
    <div class="metric-card">
      <div class="metric-label">Infrastructure Cost</div>
      <div class="metric-value" style="color:var(--accent3)">−34%</div>
      <div class="metric-sub">via cost optimization scripts</div>
      <svg class="sparkline" width="100%" height="32" viewBox="0 0 200 32"><polyline points="0,4 40,8 80,12 100,16 140,20 160,24 200,28" fill="none" stroke="var(--accent3)" stroke-width="1.5" opacity="0.7"/></svg>
    </div>
    <div class="metric-card">
      <div class="metric-label">Test Coverage</div>
      <div class="metric-value" style="color:#a78bfa">94%</div>
      <div class="metric-sub">automated test suite</div>
      <svg class="sparkline" width="100%" height="32" viewBox="0 0 200 32"><polyline points="0,28 40,26 80,20 100,18 140,12 160,8 200,4" fill="none" stroke="#a78bfa" stroke-width="1.5" opacity="0.7"/></svg>
    </div>
  </div>
</section>

<section id="projects">
  <div class="section-label">01 — Repositories</div>
  <h2 class="section-title">FEATURED PROJECTS</h2>
  <div class="projects-grid">

    <div class="project-card reveal">
      <div class="card-sidebar">
        <div class="project-icon icon-infra">☁️</div>
        <div class="project-badge badge-infra">Infrastructure</div>
        <div class="project-num">01</div>
      </div>
      <div class="card-main">
        <div class="card-header"><h3 class="project-title">Infrastructure as Code</h3></div>
        <p class="project-desc">Full AWS/Azure/GCP multi-cloud infrastructure using Terraform modules. Provisions VPCs, security groups, ALBs, auto-scaling groups, RDS clusters, and S3 with lifecycle policies — all with environment-specific tfvars and remote state in S3 + DynamoDB locking.</p>
        <div class="features">
          <div class="feature">VPC with public/private subnets</div><div class="feature">Security groups & NACLs</div>
          <div class="feature">Application Load Balancer</div><div class="feature">Auto Scaling Groups</div>
          <div class="feature">RDS Multi-AZ + read replicas</div><div class="feature">S3 + CloudFront CDN</div>
          <div class="feature">IAM roles & policies</div><div class="feature">Remote state management</div>
        </div>
        <div class="tech-tags"><span class="tag">Terraform</span><span class="tag">AWS</span><span class="tag">Azure</span><span class="tag">GCP</span><span class="tag">HCL</span><span class="tag">Terragrunt</span></div>
        <div class="card-footer">
          <a href="https://github.com/abhishekdk-yml07/InfrastructureAsaCode" class="github-link" target="_blank">⎔ View Repository</a>
          <div class="repo-meta"><span class="meta-item">⭐ 42 resources</span><span class="meta-item">📦 3 environments</span></div>
        </div>
      </div>
    </div>

    <div class="project-card reveal">
      <div class="card-sidebar">
        <div class="project-icon icon-cicd">🚀</div>
        <div class="project-badge badge-cicd">CI/CD</div>
        <div class="project-num">02</div>
      </div>
      <div class="card-main">
        <div class="card-header"><h3 class="project-title">CI/CD Pipeline Demo</h3></div>
        <p class="project-desc">End-to-end CI/CD pipeline using GitHub Actions with matrix testing, Docker multi-stage builds, image scanning, semantic versioning, and GitOps-style deployment to a Kubernetes cluster via ArgoCD with automated rollbacks on failed health checks.</p>
        <div class="pipeline">
          <div class="pipe-stage"><div class="pipe-box done">Lint</div><div class="pipe-label">ESLint + Trivy</div><div class="pipe-time">23s</div></div>
          <div class="pipe-arrow">→</div>
          <div class="pipe-stage"><div class="pipe-box done">Test</div><div class="pipe-label">Unit + Integration</div><div class="pipe-time">1m 42s</div></div>
          <div class="pipe-arrow">→</div>
          <div class="pipe-stage"><div class="pipe-box done">Build</div><div class="pipe-label">Docker Multi-stage</div><div class="pipe-time">2m 11s</div></div>
          <div class="pipe-arrow">→</div>
          <div class="pipe-stage"><div class="pipe-box run">Deploy</div><div class="pipe-label">ArgoCD → K8s</div><div class="pipe-time">running…</div></div>
          <div class="pipe-arrow">→</div>
          <div class="pipe-stage"><div class="pipe-box pend">Smoke Test</div><div class="pipe-label">Health checks</div><div class="pipe-time">—</div></div>
        </div>
        <div class="tech-tags"><span class="tag">GitHub Actions</span><span class="tag">Docker</span><span class="tag">ArgoCD</span><span class="tag">Kubernetes</span><span class="tag">Trivy</span><span class="tag">GHCR</span></div>
        <div class="card-footer">
          <a href="https://github.com/abhishekdk-yml07/CICD-Pipeline_Proj" class="github-link" target="_blank">⎔ View Repository</a>
          <div class="repo-meta"><span class="meta-item">✅ 94% pass rate</span><span class="meta-item">⚡ 4m avg build</span></div>
        </div>
      </div>
    </div>

    <div class="project-card reveal">
      <div class="card-sidebar">
        <div class="project-icon icon-mon">📊</div>
        <div class="project-badge badge-mon">Observability</div>
        <div class="project-num">03</div>
      </div>
      <div class="card-main">
        <div class="card-header"><h3 class="project-title">Monitoring & Observability</h3></div>
        <p class="project-desc">Full-stack observability with Prometheus scraping 40+ custom metrics, Grafana dashboards with variable-driven panels, Loki for log aggregation, Jaeger for distributed tracing, and AlertManager with PagerDuty/Slack routing using severity-based escalation policies.</p>
        <div class="features">
          <div class="feature">Prometheus + custom exporters</div><div class="feature">Grafana dashboards (JSON)</div>
          <div class="feature">Loki log aggregation</div><div class="feature">Jaeger distributed tracing</div>
          <div class="feature">AlertManager routing</div><div class="feature">PagerDuty integration</div>
          <div class="feature">SLO/SLA tracking</div><div class="feature">Runbook automation</div>
        </div>
        <div class="tech-tags"><span class="tag">Prometheus</span><span class="tag">Grafana</span><span class="tag">Loki</span><span class="tag">Jaeger</span><span class="tag">AlertManager</span><span class="tag">PromQL</span></div>
        <div class="card-footer">
          <a href="https://github.com/abhishekdk-yml07/Monitoring_and_observability" class="github-link" target="_blank">⎔ View Repository</a>
          <div class="repo-meta"><span class="meta-item">📈 40+ metrics</span><span class="meta-item">🔔 12 alert rules</span></div>
        </div>
      </div>
    </div>

    <div class="project-card reveal">
      <div class="card-sidebar">
        <div class="project-icon icon-k8s">⎈</div>
        <div class="project-badge badge-k8s">Kubernetes</div>
        <div class="project-num">04</div>
      </div>
      <div class="card-main">
        <div class="card-header"><h3 class="project-title">Kubernetes Deployment</h3></div>
        <p class="project-desc">Production-grade multi-service application on Kubernetes with Helm charts for templating, Nginx ingress with TLS termination, HPA based on custom Prometheus metrics, PodDisruptionBudgets, NetworkPolicies, and RBAC configurations for team-level namespace isolation.</p>
        <div class="features">
          <div class="feature">Helm chart templates</div><div class="feature">Nginx Ingress + cert-manager</div>
          <div class="feature">HPA with custom metrics</div><div class="feature">PodDisruptionBudgets</div>
          <div class="feature">NetworkPolicies</div><div class="feature">RBAC & ServiceAccounts</div>
          <div class="feature">ConfigMaps & Secrets</div><div class="feature">Rolling + canary deploys</div>
        </div>
        <div class="tech-tags"><span class="tag">Kubernetes</span><span class="tag">Helm</span><span class="tag">NGINX Ingress</span><span class="tag">cert-manager</span><span class="tag">KEDA</span><span class="tag">Kustomize</span></div>
        <div class="card-footer">
          <a href="https://github.com/abhishekdk-yml07/Kubernetes_Deployment" class="github-link" target="_blank">⎔ View Repository</a>
          <div class="repo-meta"><span class="meta-item">🎯 3 services</span><span class="meta-item">📦 Helm v3</span></div>
        </div>
      </div>
    </div>

    <div class="project-card reveal">
      <div class="card-sidebar">
        <div class="project-icon icon-auto">⚙️</div>
        <div class="project-badge badge-auto">Automation</div>
        <div class="project-num">05</div>
      </div>
      <div class="card-main">
        <div class="card-header"><h3 class="project-title">Automation Scripts</h3></div>
        <p class="project-desc">Python and Bash toolkit for common DevOps tasks: AWS cost optimization that identifies idle resources and rightsizing opportunities, a log analysis tool with anomaly detection, and a backup automation script with encryption, S3 upload, and retention management.</p>
        <div class="file-tree">
          <div><span class="tree-dir">scripts/</span></div>
          <div>&nbsp;&nbsp;<span class="tree-dir">cost-optimizer/</span></div>
          <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="tree-file">analyzer.py</span> <span class="tree-comment"># EC2, RDS, NAT idle detection</span></div>
          <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="tree-file">rightsizer.py</span> <span class="tree-comment"># CloudWatch metrics-based</span></div>
          <div>&nbsp;&nbsp;<span class="tree-dir">log-analysis/</span></div>
          <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="tree-file">parser.py</span> <span class="tree-comment"># Multi-format log ingestion</span></div>
          <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="tree-file">anomaly.py</span> <span class="tree-comment"># Threshold + ML detection</span></div>
          <div>&nbsp;&nbsp;<span class="tree-dir">backup/</span></div>
          <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="tree-file">backup.sh</span> <span class="tree-comment"># AES-256 + S3 + cron</span></div>
          <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="tree-file">restore.sh</span> <span class="tree-comment"># Point-in-time restore</span></div>
        </div>
        <div class="tech-tags"><span class="tag">Python</span><span class="tag">Bash</span><span class="tag">boto3</span><span class="tag">AWS CLI</span><span class="tag">cron</span><span class="tag">pandas</span></div>
        <div class="card-footer">
          <a href="https://github.com/abhishekdk-yml07/Bash-python_automationScripts" class="github-link" target="_blank">⎔ View Repository</a>
          <div class="repo-meta"><span class="meta-item">💰 −$340/mo</span><span class="meta-item">🔁 Fully automated</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<section id="architecture">
  <div class="section-label">02 — System Design</div>
  <h2 class="section-title">ARCHITECTURE OVERVIEW</h2>
  <div class="arch-diagram reveal">
    <div style="font-family:var(--mono);font-size:11px;color:var(--muted);margin-bottom:32px;letter-spacing:.1em;text-transform:uppercase;">AWS Production Architecture — VPC us-east-1</div>
    <div class="arch-flow">
      <div class="arch-node"><div class="arch-box internet">Internet</div><div class="arch-label">Users / DNS</div></div>
      <div class="arch-arrow">→</div>
      <div class="arch-node"><div class="arch-box lb">ALB<br><small style="font-size:9px">HTTPS/443</small></div><div class="arch-label">Load Balancer</div></div>
      <div class="arch-arrow">→</div>
      <div class="arch-group">
        <div class="arch-group-label">Private Subnet — Auto Scaling Group</div>
        <div style="display:flex;gap:8px;">
          <div class="arch-node"><div class="arch-box asg">EC2<br><small style="font-size:9px">t3.medium</small></div><div class="arch-label">App Server</div></div>
          <div class="arch-node"><div class="arch-box asg">EC2<br><small style="font-size:9px">t3.medium</small></div><div class="arch-label">App Server</div></div>
          <div class="arch-node"><div class="arch-box asg">EC2<br><small style="font-size:9px">t3.medium</small></div><div class="arch-label">App Server</div></div>
        </div>
      </div>
      <div class="arch-arrow">→</div>
      <div style="display:flex;flex-direction:column;gap:12px;">
        <div class="arch-node"><div class="arch-box db">RDS<br><small style="font-size:9px">Multi-AZ</small></div><div class="arch-label">PostgreSQL</div></div>
        <div class="arch-node"><div class="arch-box cache">ElastiCache<br><small style="font-size:9px">Redis</small></div><div class="arch-label">Cache Layer</div></div>
      </div>
    </div>
    <div style="margin-top:32px;display:flex;gap:16px;justify-content:center;">
      <div class="arch-node"><div class="arch-box monitor">Prometheus + Grafana</div><div class="arch-label">Observability Stack</div></div>
      <div class="arch-node" style="margin-left:16px;"><div class="arch-box lb">CloudFront + S3</div><div class="arch-label">Static Assets / CDN</div></div>
    </div>
  </div>
</section>

<section id="readme">
  <div class="section-label">03 — Documentation</div>
  <h2 class="section-title">README STRUCTURE</h2>
  <div class="readme-grid reveal">
    <div class="readme-card">
      <div class="readme-card-header"><span class="file-icon">📄</span>README.md — Every Project</div>
      <div class="readme-body">
        <div class="readme-section-title">Problem / Solution / Impact</div>
        <div class="readme-item"><div class="readme-bullet" style="background:rgba(0,229,255,.1);color:var(--accent);">✦</div><div><strong style="color:var(--text);">Problem Statement</strong> — what specific pain point or gap this solves</div></div>
        <div class="readme-item"><div class="readme-bullet" style="background:rgba(124,58,237,.1);color:#a78bfa;">✦</div><div><strong style="color:var(--text);">Solution Overview</strong> — architecture decisions and trade-offs made</div></div>
        <div class="readme-item"><div class="readme-bullet" style="background:rgba(34,197,94,.1);color:var(--green);">✦</div><div><strong style="color:var(--text);">Measurable Impact</strong> — metrics: cost saved, time reduced, reliability improved</div></div>
        <div class="readme-item"><div class="readme-bullet" style="background:rgba(245,158,11,.1);color:var(--accent3);">✦</div><div><strong style="color:var(--text);">Local Setup</strong> — one-command bootstrap with prerequisites listed</div></div>
        <div class="readme-item"><div class="readme-bullet" style="background:rgba(239,68,68,.1);color:#f87171;">✦</div><div><strong style="color:var(--text);">Architecture Diagram</strong> — Mermaid or draw.io diagram embedded</div></div>
        <div class="readme-item"><div class="readme-bullet" style="background:rgba(0,229,255,.1);color:var(--accent);">✦</div><div><strong style="color:var(--text);">Screenshots / GIFs</strong> — visual proof it works, Grafana dashboards, etc.</div></div>
      </div>
    </div>
    <div class="readme-card">
      <div class="readme-card-header"><span class="file-icon">🗂️</span>Repository Structure — Best Practice</div>
      <div class="readme-body">
        <div class="readme-section-title">File Organization</div>
        <div class="file-tree" style="font-size:11px;line-height:1.8;">
          <div><span class="tree-dir">project-name/</span></div>
          <div>&nbsp;&nbsp;<span class="tree-file">README.md</span> <span class="tree-comment">← problem/solution/impact</span></div>
          <div>&nbsp;&nbsp;<span class="tree-dir">docs/</span></div>
          <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="tree-file">architecture.md</span></div>
          <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="tree-file">decisions.md</span> <span class="tree-comment">← ADRs</span></div>
          <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="tree-file">screenshots/</span></div>
          <div>&nbsp;&nbsp;<span class="tree-dir">src/ or terraform/</span></div>
          <div>&nbsp;&nbsp;<span class="tree-dir">.github/workflows/</span></div>
          <div>&nbsp;&nbsp;<span class="tree-file">Makefile</span> <span class="tree-comment">← make setup, test, deploy</span></div>
          <div>&nbsp;&nbsp;<span class="tree-file">docker-compose.yml</span> <span class="tree-comment">← local dev</span></div>
          <div>&nbsp;&nbsp;<span class="tree-file">CONTRIBUTING.md</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CTA -->
<section class="cta-section">
  <div class="cta-label">Ready to hire</div>
  <h2 class="cta-title">LET'S BUILD<br>TOGETHER</h2>
  <p class="cta-desc">These projects represent real infrastructure decisions, real trade-offs, and real impact. Every README tells the full story.</p>
  <div class="btn-row">

    <a href="https://github.com/abhishekdk-yml07" class="btn btn-primary" target="_blank">
      ⎔ View on GitHub
    </a>

    <!-- IMPROVED CONTACT BUTTON -->
    <div class="contact-wrapper" id="contactWrapper">
      <button class="btn-contact" id="contactBtn" onclick="toggleContact()">
        ✉ Get in Touch
        <span class="chevron">▼</span>
      </button>
      <div class="contact-panel" id="contactPanel">
        <div class="contact-panel-header">Contact channels</div>
        <a href="mailto:abhishekdk949@gmail.com" class="contact-item email">
          <div class="contact-icon">✉</div>
          <div class="contact-text">
            <span class="contact-type">Email</span>
            <span class="contact-value">abhishekdk949@gmail.com</span>
          </div>
          <span class="contact-arrow">→</span>
        </a>
        <a href="tel:+919876543210" class="contact-item phone">
          <div class="contact-icon">☎</div>
          <div class="contact-text">
            <span class="contact-type">Mobile</span>
            <span class="contact-value">+91 8073723452</span>
          </div>
          <span class="contact-arrow">→</span>
        </a>
      </div>
    </div>
    <!-- END CONTACT BUTTON -->

  </div>
</section>

<footer>
  <div>© 2026 — DevOps Portfolio</div>
  <div style="display:flex;gap:4px;align-items:center;"><div class="status-dot"></div>All 5 repos public on GitHub</div>
  <div>Built with intention.</div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx=0,my=0,rx=0,ry=0;
  document.addEventListener('mousemove',e=>{
    mx=e.clientX;my=e.clientY;
    cursor.style.left=mx-4+'px';cursor.style.top=my-4+'px';
  });
  function animRing(){rx+=(mx-rx)*.12;ry+=(my-ry)*.12;ring.style.left=rx-16+'px';ring.style.top=ry-16+'px';requestAnimationFrame(animRing);}
  animRing();

  // Scroll reveal
  const reveals=document.querySelectorAll('.reveal');
  const observer=new IntersectionObserver(entries=>{entries.forEach(e=>{if(e.isIntersecting){e.target.classList.add('visible');observer.unobserve(e.target);}});},{threshold:.1});
  reveals.forEach(el=>observer.observe(el));

  // Contact toggle
  function toggleContact(){
    document.getElementById('contactWrapper').classList.toggle('open');
  }
  // Close on outside click
  document.addEventListener('click',function(e){
    const w=document.getElementById('contactWrapper');
    if(!w.contains(e.target)) w.classList.remove('open');
  });
</script>
</body>
</html>

