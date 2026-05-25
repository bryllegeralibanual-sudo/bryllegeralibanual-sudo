<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Brylle Gerali Banual — Developer Profile</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;700;800&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #12121a;
    --surface2: #1a1a26;
    --border: rgba(255,255,255,0.07);
    --border2: rgba(255,255,255,0.12);
    --text: #f0eeff;
    --muted: #8888aa;
    --hint: #55556a;
    --accent: #7f77dd;
    --accent2: #1d9e75;
    --accent3: #d85a30;
    --accent-soft: rgba(127,119,221,0.12);
    --font: 'Syne', sans-serif;
    --mono: 'DM Mono', monospace;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(127,119,221,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(127,119,221,0.03) 1px, transparent 1px);
    background-size: 48px 48px;
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 800px;
    margin: 0 auto;
    padding: 3rem 1.5rem 4rem;
    position: relative;
    z-index: 1;
  }

  /* ── HERO ── */
  .hero {
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 2rem;
    align-items: start;
    margin-bottom: 3rem;
    animation: fadeUp 0.6s ease both;
  }

  .avatar-wrap {
    position: relative;
  }

  .avatar {
    width: 88px;
    height: 88px;
    border-radius: 50%;
    background: var(--accent-soft);
    border: 1px solid var(--accent);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
    font-weight: 800;
    color: var(--accent);
    letter-spacing: 0.05em;
  }

  .avatar-ring {
    position: absolute;
    inset: -5px;
    border-radius: 50%;
    border: 1px dashed rgba(127,119,221,0.3);
    animation: spin 20s linear infinite;
  }

  .status-dot {
    position: absolute;
    bottom: 4px;
    right: 4px;
    width: 14px;
    height: 14px;
    background: var(--accent2);
    border-radius: 50%;
    border: 2px solid var(--bg);
  }

  .status-dot::after {
    content: '';
    position: absolute;
    inset: -3px;
    border-radius: 50%;
    background: var(--accent2);
    opacity: 0.3;
    animation: pulse 2s ease infinite;
  }

  .hero-text { padding-top: 4px; }

  .eyebrow {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 6px;
  }

  h1 {
    font-size: clamp(26px, 4vw, 38px);
    font-weight: 800;
    line-height: 1.1;
    letter-spacing: -0.02em;
    margin-bottom: 8px;
  }

  .tagline {
    font-size: 14px;
    color: var(--muted);
    line-height: 1.6;
    max-width: 420px;
    margin-bottom: 14px;
  }

  .chips {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .chip {
    display: inline-flex;
    align-items: center;
    gap: 5px;
    font-size: 12px;
    padding: 4px 10px;
    border-radius: 20px;
    background: var(--surface);
    border: 0.5px solid var(--border2);
    color: var(--muted);
  }

  .chip svg { width: 12px; height: 12px; flex-shrink: 0; }
  .chip.open { background: rgba(29,158,117,0.1); border-color: rgba(29,158,117,0.4); color: #5dcaa5; }

  /* ── NAV TABS ── */
  .tabs {
    display: flex;
    gap: 2px;
    background: var(--surface);
    border: 0.5px solid var(--border);
    border-radius: 12px;
    padding: 4px;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.6s 0.1s ease both;
  }

  .tab {
    flex: 1;
    padding: 9px 12px;
    border: none;
    background: transparent;
    color: var(--muted);
    font-family: var(--font);
    font-size: 13px;
    font-weight: 500;
    border-radius: 9px;
    cursor: pointer;
    transition: all 0.2s;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 6px;
  }

  .tab:hover { color: var(--text); background: var(--surface2); }

  .tab.active {
    background: var(--accent-soft);
    color: #b8b2ff;
    border: 0.5px solid rgba(127,119,221,0.3);
  }

  .tab svg { width: 14px; height: 14px; }

  /* ── PANELS ── */
  .panel { display: none; animation: fadeUp 0.3s ease both; }
  .panel.active { display: block; }

  /* ── SECTION CARD ── */
  .card {
    background: var(--surface);
    border: 0.5px solid var(--border);
    border-radius: 16px;
    padding: 1.5rem;
    margin-bottom: 1rem;
  }

  .card-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--hint);
    margin-bottom: 1rem;
  }

  /* ── SKILL BARS ── */
  .skill-row { margin-bottom: 1.1rem; }
  .skill-row:last-child { margin-bottom: 0; }

  .skill-head {
    display: flex;
    justify-content: space-between;
    font-size: 13px;
    margin-bottom: 8px;
    color: var(--text);
  }

  .skill-pct {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--hint);
  }

  .bar-track {
    background: var(--surface2);
    border-radius: 3px;
    height: 4px;
    overflow: hidden;
  }

  .bar-fill {
    height: 100%;
    border-radius: 3px;
    width: 0;
    transition: width 1.2s cubic-bezier(0.22, 1, 0.36, 1);
  }

  /* ── STAT ROW ── */
  .stat-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
    margin-bottom: 1rem;
  }

  .stat {
    background: var(--surface);
    border: 0.5px solid var(--border);
    border-radius: 12px;
    padding: 1rem;
    text-align: center;
  }

  .stat-n {
    font-size: 28px;
    font-weight: 800;
    color: var(--text);
    letter-spacing: -0.03em;
  }

  .stat-l {
    font-size: 11px;
    color: var(--hint);
    margin-top: 3px;
    font-family: var(--mono);
  }

  /* ── PROJECTS ── */
  .proj {
    background: var(--surface2);
    border: 0.5px solid var(--border);
    border-radius: 12px;
    padding: 1.25rem;
    margin-bottom: 0.75rem;
    transition: border-color 0.2s;
  }

  .proj:hover { border-color: var(--border2); }

  .proj-head {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 6px;
  }

  .proj-name {
    font-size: 15px;
    font-weight: 700;
    color: var(--text);
  }

  .proj-wip {
    font-family: var(--mono);
    font-size: 10px;
    padding: 3px 8px;
    border-radius: 20px;
    background: rgba(127,119,221,0.12);
    color: #b8b2ff;
    border: 0.5px solid rgba(127,119,221,0.3);
  }

  .proj-desc {
    font-size: 13px;
    color: var(--muted);
    line-height: 1.6;
    margin-bottom: 10px;
  }

  .tags { display: flex; flex-wrap: wrap; gap: 6px; }

  .tag {
    font-size: 11px;
    font-family: var(--mono);
    padding: 3px 8px;
    border-radius: 4px;
  }

  .tag-a { background: rgba(127,119,221,0.1); color: #afa9ec; }
  .tag-b { background: rgba(29,158,117,0.1); color: #5dcaa5; }
  .tag-c { background: rgba(216,90,48,0.1); color: #f0997b; }

  .proj-dashed {
    border-style: dashed;
    opacity: 0.5;
  }

  /* ── GOALS ── */
  .goal {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    padding: 12px 0;
    border-bottom: 0.5px solid var(--border);
    cursor: pointer;
    transition: opacity 0.2s;
  }

  .goal:last-child { border-bottom: none; }

  .goal-check {
    width: 20px;
    height: 20px;
    border-radius: 50%;
    border: 1px solid var(--hint);
    flex-shrink: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.2s;
    margin-top: 2px;
  }

  .goal-check svg { width: 10px; height: 10px; display: none; }

  .goal.done .goal-check {
    background: var(--accent2);
    border-color: var(--accent2);
  }

  .goal.done .goal-check svg { display: block; }

  .goal-text {
    font-size: 14px;
    color: var(--text);
    line-height: 1.5;
    transition: color 0.2s;
  }

  .goal.done .goal-text {
    text-decoration: line-through;
    color: var(--hint);
  }

  .progress-bar-wrap {
    background: var(--surface2);
    border-radius: 4px;
    height: 4px;
    margin-bottom: 1.25rem;
    overflow: hidden;
  }

  .progress-bar-fill {
    height: 100%;
    background: var(--accent2);
    border-radius: 4px;
    width: 0;
    transition: width 0.4s ease;
  }

  .progress-label {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--hint);
    margin-bottom: 8px;
  }

  /* ── CONTACT ── */
  .contact-item {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 13px 0;
    border-bottom: 0.5px solid var(--border);
    text-decoration: none;
    transition: opacity 0.2s;
  }

  .contact-item:hover { opacity: 0.7; }
  .contact-item:last-child { border-bottom: none; }

  .contact-icon {
    width: 36px;
    height: 36px;
    border-radius: 9px;
    background: var(--surface2);
    border: 0.5px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }

  .contact-icon svg { width: 16px; height: 16px; color: var(--muted); }

  .contact-info { flex: 1; }
  .contact-name { font-size: 13px; color: var(--muted); margin-bottom: 2px; }
  .contact-val { font-size: 14px; color: var(--text); }

  .contact-arrow {
    color: var(--hint);
    font-size: 18px;
  }

  /* ── QUOTE ── */
  .quote {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--hint);
    border-left: 2px solid var(--accent);
    padding-left: 12px;
    margin-top: 1.25rem;
    line-height: 1.7;
  }

  /* ── FOOTER ── */
  .footer {
    margin-top: 3rem;
    text-align: center;
    font-family: var(--mono);
    font-size: 11px;
    color: var(--hint);
    animation: fadeUp 0.6s 0.4s ease both;
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(12px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes spin {
    to { transform: rotate(360deg); }
  }

  @keyframes pulse {
    0%, 100% { transform: scale(1); opacity: 0.3; }
    50% { transform: scale(1.8); opacity: 0; }
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 520px) {
    .hero { grid-template-columns: 1fr; gap: 1.25rem; }
    .tab span { display: none; }
    .stat-row { grid-template-columns: repeat(3, 1fr); }
  }
</style>
</head>
<body>

<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div class="avatar-wrap">
      <div class="avatar">BGB</div>
      <div class="avatar-ring"></div>
      <div class="status-dot"></div>
    </div>
    <div class="hero-text">
      <div class="eyebrow">// developer profile</div>
      <h1>Brylle Gerali<br>Banual</h1>
      <p class="tagline">Aspiring developer from the Philippines — building skills, shipping code, and looking for an internship to grow with.</p>
      <div class="chips">
        <span class="chip open">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="3"/></svg>
          Open to internships
        </span>
        <span class="chip">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7z"/></svg>
          Quezon City, PH
        </span>
        <span class="chip">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 2L2 7l10 5 10-5-10-5z"/><path d="M2 17l10 5 10-5"/><path d="M2 12l10 5 10-5"/></svg>
          Started 2024
        </span>
      </div>
    </div>
  </div>

  <!-- TABS -->
  <div class="tabs" role="tablist">
    <button class="tab active" onclick="switchTab('skills', this)" role="tab">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg>
      <span>Skills</span>
    </button>
    <button class="tab" onclick="switchTab('projects', this)" role="tab">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 3h6l2 3h10a2 2 0 0 1 2 2v11a2 2 0 0 1-2 2H3a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2z"/></svg>
      <span>Projects</span>
    </button>
    <button class="tab" onclick="switchTab('goals', this)" role="tab">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
      <span>Goals</span>
    </button>
    <button class="tab" onclick="switchTab('contact', this)" role="tab">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
      <span>Contact</span>
    </button>
  </div>

  <!-- SKILLS PANEL -->
  <div id="panel-skills" class="panel active">
    <div class="stat-row">
      <div class="stat"><div class="stat-n">4+</div><div class="stat-l">technologies</div></div>
      <div class="stat"><div class="stat-n" id="stat-goals">0</div><div class="stat-l">goals done</div></div>
      <div class="stat"><div class="stat-n">∞</div><div class="stat-l">curiosity</div></div>
    </div>
    <div class="card">
      <div class="card-label">// current proficiency</div>
      <div class="skill-row">
        <div class="skill-head"><span>HTML & CSS</span><span class="skill-pct">55%</span></div>
        <div class="bar-track"><div class="bar-fill" style="background:#7f77dd" data-w="55"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-head"><span>JavaScript</span><span class="skill-pct">30%</span></div>
        <div class="bar-track"><div class="bar-fill" style="background:#378add" data-w="30"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-head"><span>Git & GitHub</span><span class="skill-pct">40%</span></div>
        <div class="bar-track"><div class="bar-fill" style="background:#1d9e75" data-w="40"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-head"><span>Problem solving</span><span class="skill-pct">45%</span></div>
        <div class="bar-track"><div class="bar-fill" style="background:#ba7517" data-w="45"></div></div>
      </div>
      <div class="quote">These bars are honest — they show progress, not perfection.<br>Every expert was once a beginner.</div>
    </div>
  </div>

  <!-- PROJECTS PANEL -->
  <div id="panel-projects" class="panel">
    <div class="proj">
      <div class="proj-head">
        <div class="proj-name">Personal Portfolio Site</div>
        <span class="proj-wip">v1.0</span>
      </div>
      <div class="proj-desc">A simple HTML/CSS portfolio to showcase my work and introduce myself to potential employers. My first real project — built from scratch.</div>
      <div class="tags">
        <span class="tag tag-a">HTML</span>
        <span class="tag tag-a">CSS</span>
        <span class="tag tag-b">GitHub Pages</span>
      </div>
    </div>
    <div class="proj">
      <div class="proj-head">
        <div class="proj-name">JS Mini Projects</div>
        <span class="proj-wip">in progress</span>
      </div>
      <div class="proj-desc">A growing collection of small JavaScript exercises — to-do list, calculator, quote generator. Built to learn the DOM and JS fundamentals hands-on.</div>
      <div class="tags">
        <span class="tag tag-c">JavaScript</span>
        <span class="tag tag-b">DOM</span>
        <span class="tag tag-a">Vanilla JS</span>
      </div>
    </div>
    <div class="proj proj-dashed">
      <div class="proj-head">
        <div class="proj-name">Next Project</div>
        <span class="proj-wip">planning</span>
      </div>
      <div class="proj-desc">Currently deciding what to build next. Ideas welcome!</div>
      <div class="tags">
        <span class="tag tag-a">???</span>
      </div>
    </div>
  </div>

  <!-- GOALS PANEL -->
  <div id="panel-goals" class="panel">
    <div class="card">
      <div class="card-label">// 2025 roadmap — tap to check off</div>
      <div class="progress-label" id="progress-label">0 / 5 completed</div>
      <div class="progress-bar-wrap"><div class="progress-bar-fill" id="progress-fill"></div></div>
      <div id="goals-list">
        <div class="goal" onclick="toggleGoal(this)">
          <div class="goal-check"><svg viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="3"><polyline points="20 6 9 17 4 12"/></svg></div>
          <div class="goal-text">Complete a structured web development course</div>
        </div>
        <div class="goal" onclick="toggleGoal(this)">
          <div class="goal-check"><svg viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="3"><polyline points="20 6 9 17 4 12"/></svg></div>
          <div class="goal-text">Land my first internship or part-time dev role</div>
        </div>
        <div class="goal" onclick="toggleGoal(this)">
          <div class="goal-check"><svg viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="3"><polyline points="20 6 9 17 4 12"/></svg></div>
          <div class="goal-text">Build 3 projects I'm proud to show off</div>
        </div>
        <div class="goal" onclick="toggleGoal(this)">
          <div class="goal-check"><svg viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="3"><polyline points="20 6 9 17 4 12"/></svg></div>
          <div class="goal-text">Contribute to an open-source project</div>
        </div>
        <div class="goal" onclick="toggleGoal(this)">
          <div class="goal-check"><svg viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="3"><polyline points="20 6 9 17 4 12"/></svg></div>
          <div class="goal-text">Learn a JavaScript framework (React or Vue)</div>
        </div>
      </div>
    </div>
  </div>

  <!-- CONTACT PANEL -->
  <div id="panel-contact" class="panel">
    <div class="card">
      <div class="card-label">// get in touch</div>
      <a class="contact-item" href="https://github.com/bryllebanual" target="_blank">
        <div class="contact-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"/></svg>
        </div>
        <div class="contact-info">
          <div class="contact-name">GitHub</div>
          <div class="contact-val">github.com/bryllebanual</div>
        </div>
        <div class="contact-arrow">→</div>
      </a>
      <a class="contact-item" href="mailto:bryllebanual@email.com">
        <div class="contact-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
        </div>
        <div class="contact-info">
          <div class="contact-name">Email</div>
          <div class="contact-val">bryllebanual@email.com</div>
        </div>
        <div class="contact-arrow">→</div>
      </a>
      <a class="contact-item" href="https://linkedin.com/in/bryllebanual" target="_blank">
        <div class="contact-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>
        </div>
        <div class="contact-info">
          <div class="contact-name">LinkedIn</div>
          <div class="contact-val">linkedin.com/in/bryllebanual</div>
        </div>
        <div class="contact-arrow">→</div>
      </a>
      <div class="contact-item" style="cursor:default">
        <div class="contact-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>
        </div>
        <div class="contact-info">
          <div class="contact-name">Location</div>
          <div class="contact-val">Quezon City, Philippines</div>
        </div>
      </div>
    </div>
    <div style="text-align:center;font-family:var(--mono);font-size:12px;color:var(--hint);line-height:1.8">
      Open to internships, collabs &amp; coffee chats about tech.<br>
      <span style="color:var(--accent)">Let's build something together.</span>
    </div>
  </div>

  <div class="footer">
    built with curiosity · brylle gerali banual · 2025
  </div>

</div>

<script>
  function switchTab(name, btn) {
    document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
    document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
    btn.classList.add('active');
    document.getElementById('panel-' + name).classList.add('active');
    if (name === 'skills') animateBars();
  }

  function animateBars() {
    setTimeout(() => {
      document.querySelectorAll('.bar-fill').forEach(b => {
        b.style.width = b.dataset.w + '%';
      });
    }, 100);
  }

  function toggleGoal(el) {
    el.classList.toggle('done');
    const done = document.querySelectorAll('.goal.done').length;
    const total = document.querySelectorAll('.goal').length;
    document.getElementById('progress-label').textContent = done + ' / ' + total + ' completed';
    document.getElementById('progress-fill').style.width = Math.round((done / total) * 100) + '%';
    document.getElementById('stat-goals').textContent = done;
  }

  window.addEventListener('load', () => {
    setTimeout(animateBars, 400);
  });
</script>
</body>
</html>
