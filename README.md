<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tahmid Al Mamun</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=DM+Mono:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #080a0e;
    --surface: #0e1117;
    --border: rgba(255,255,255,0.07);
    --border-hover: rgba(255,255,255,0.14);
    --text: #e8eaf0;
    --muted: #6b7280;
    --accent-green: #22c55e;
    --accent-amber: #f59e0b;
    --glow-r: 120, 40, 30;
    --glow-g: 20, 90, 50;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
    cursor: default;
  }

  /* ── Noise grain overlay ── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    opacity: 0.35;
    pointer-events: none;
    z-index: 100;
  }

  .page { max-width: 760px; margin: 0 auto; padding: 0 24px 80px; }

  /* ── Hero ── */
  .hero {
    position: relative;
    min-height: 340px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 80px 24px 60px;
    overflow: hidden;
    border-radius: 0 0 24px 24px;
  }

  .hero-bg {
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 60% 55% at 25% 60%, rgba(var(--glow-r), 0.28) 0%, transparent 65%),
      radial-gradient(ellipse 50% 50% at 75% 40%, rgba(var(--glow-g), 0.22) 0%, transparent 65%),
      radial-gradient(ellipse 80% 40% at 50% 90%, rgba(10,20,40,0.9) 0%, transparent 80%);
    background-color: #0c0e12;
    animation: bgShift 12s ease-in-out infinite alternate;
  }

  @keyframes bgShift {
    0%   { filter: hue-rotate(0deg) brightness(1); }
    100% { filter: hue-rotate(15deg) brightness(1.08); }
  }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2.4rem, 6vw, 4rem);
    font-weight: 800;
    letter-spacing: -0.03em;
    color: #fff;
    position: relative;
    z-index: 1;
    animation: fadeUp 0.9s cubic-bezier(0.22,1,0.36,1) both;
    text-shadow: 0 0 60px rgba(255,255,255,0.08);
  }

  .hero-role {
    font-size: 0.72rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
    position: relative;
    z-index: 1;
    margin-top: 10px;
    animation: fadeUp 0.9s 0.1s cubic-bezier(0.22,1,0.36,1) both;
  }

  .hero-role span { color: rgba(255,255,255,0.4); margin: 0 8px; }

  .hero-desc {
    font-size: 0.82rem;
    color: rgba(255,255,255,0.45);
    line-height: 1.8;
    max-width: 440px;
    position: relative;
    z-index: 1;
    margin-top: 20px;
    animation: fadeUp 0.9s 0.2s cubic-bezier(0.22,1,0.36,1) both;
  }

  /* ── Contact buttons ── */
  .contacts {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    justify-content: center;
    margin-top: 28px;
    position: relative;
    z-index: 1;
    animation: fadeUp 0.9s 0.3s cubic-bezier(0.22,1,0.36,1) both;
  }

  .btn {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 9px 18px;
    border-radius: 100px;
    background: rgba(255,255,255,0.06);
    border: 0.5px solid rgba(255,255,255,0.12);
    color: rgba(255,255,255,0.75);
    font-family: 'DM Mono', monospace;
    font-size: 0.73rem;
    text-decoration: none;
    transition: background 0.2s, border-color 0.2s, color 0.2s, transform 0.15s;
    backdrop-filter: blur(8px);
  }
  .btn:hover {
    background: rgba(255,255,255,0.11);
    border-color: rgba(255,255,255,0.22);
    color: #fff;
    transform: translateY(-1px);
  }
  .btn svg { width: 14px; height: 14px; flex-shrink: 0; }

  /* ── Section ── */
  .section { margin-top: 40px; animation: fadeUp 0.7s 0.4s both; }

  .section-label {
    font-size: 0.62rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 16px;
    padding-bottom: 10px;
    border-bottom: 0.5px solid var(--border);
  }

  /* ── About card ── */
  .about-card {
    background: rgba(255,255,255,0.03);
    border: 0.5px solid var(--border);
    border-radius: 16px;
    padding: 28px 32px;
    position: relative;
    overflow: hidden;
  }
  .about-card::before {
    content: '';
    position: absolute;
    top: -40px; left: -40px;
    width: 200px; height: 200px;
    background: radial-gradient(circle, rgba(var(--glow-r),0.15) 0%, transparent 70%);
    pointer-events: none;
    animation: orb 8s ease-in-out infinite alternate;
  }
  @keyframes orb {
    0% { transform: translate(0,0); }
    100% { transform: translate(40px, 30px); }
  }
  .about-title {
    font-family: 'Syne', sans-serif;
    font-size: 1.5rem;
    font-weight: 700;
    color: #fff;
    line-height: 1.3;
    margin-bottom: 12px;
  }
  .about-sub {
    font-size: 0.75rem;
    color: rgba(255,255,255,0.3);
    letter-spacing: 0.05em;
  }
  .open-tag {
    display: inline-block;
    margin-top: 16px;
    font-size: 0.72rem;
    color: var(--accent-green);
    border: 0.5px solid rgba(34,197,94,0.3);
    border-radius: 100px;
    padding: 4px 12px;
    background: rgba(34,197,94,0.06);
  }
  .open-tag::before { content: '> '; opacity: 0.5; }

  /* ── Stack pills ── */
  .pills {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }
  .pill {
    font-size: 0.72rem;
    padding: 6px 14px;
    border-radius: 100px;
    border: 0.5px solid var(--border);
    background: rgba(255,255,255,0.03);
    color: rgba(255,255,255,0.6);
    transition: border-color 0.2s, color 0.2s, background 0.2s;
    cursor: default;
  }
  .pill:hover {
    border-color: rgba(255,255,255,0.2);
    color: rgba(255,255,255,0.9);
    background: rgba(255,255,255,0.06);
  }

  /* ── Projects ── */
  .projects-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
  }
  @media (max-width: 560px) { .projects-grid { grid-template-columns: 1fr; } }

  .proj-card {
    background: rgba(255,255,255,0.025);
    border: 0.5px solid var(--border);
    border-radius: 14px;
    padding: 20px 22px;
    text-decoration: none;
    color: inherit;
    display: block;
    transition: border-color 0.2s, background 0.2s, transform 0.2s;
    position: relative;
    overflow: hidden;
  }
  .proj-card::after {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(circle at var(--mx,50%) var(--my,50%), rgba(255,255,255,0.04) 0%, transparent 60%);
    opacity: 0;
    transition: opacity 0.3s;
    pointer-events: none;
  }
  .proj-card:hover::after { opacity: 1; }
  .proj-card:hover {
    border-color: var(--border-hover);
    background: rgba(255,255,255,0.04);
    transform: translateY(-2px);
  }
  .proj-card.featured { grid-column: 1 / -1; }

  .proj-header { display: flex; align-items: center; justify-content: space-between; margin-bottom: 8px; }
  .proj-name {
    font-family: 'Syne', sans-serif;
    font-size: 0.95rem;
    font-weight: 600;
    color: #fff;
  }
  .proj-badge {
    font-size: 0.62rem;
    padding: 3px 9px;
    border-radius: 100px;
    font-family: 'DM Mono', monospace;
  }
  .badge-live { background: rgba(34,197,94,0.12); color: var(--accent-green); border: 0.5px solid rgba(34,197,94,0.25); }
  .badge-dev  { background: rgba(245,158,11,0.1);  color: var(--accent-amber);  border: 0.5px solid rgba(245,158,11,0.25); }
  .badge-store{ background: rgba(255,255,255,0.06); color: var(--muted); border: 0.5px solid var(--border); }

  .proj-desc {
    font-size: 0.76rem;
    color: var(--muted);
    line-height: 1.65;
    margin-bottom: 12px;
  }
  .proj-tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .proj-tag {
    font-size: 0.63rem;
    padding: 3px 9px;
    border-radius: 6px;
    background: rgba(255,255,255,0.04);
    color: rgba(255,255,255,0.35);
    border: 0.5px solid var(--border);
  }
  .proj-url {
    margin-top: 14px;
    font-size: 0.68rem;
    color: rgba(255,255,255,0.2);
    letter-spacing: 0.03em;
  }

  /* ── CP ── */
  .cp-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; }
  .cp-card {
    background: rgba(255,255,255,0.025);
    border: 0.5px solid var(--border);
    border-radius: 14px;
    padding: 20px;
    text-align: center;
    transition: border-color 0.2s;
  }
  .cp-card:hover { border-color: var(--border-hover); }
  .cp-platform { font-size: 0.63rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--muted); margin-bottom: 10px; }
  .cp-num {
    font-family: 'Syne', sans-serif;
    font-size: 2rem;
    font-weight: 800;
    color: #fff;
    line-height: 1;
  }
  .cp-sub { font-size: 0.63rem; color: var(--muted); margin-top: 4px; }
  .cp-total {
    margin-top: 10px;
    background: rgba(255,255,255,0.03);
    border: 0.5px solid var(--border);
    border-radius: 12px;
    padding: 14px 20px;
    text-align: center;
    font-size: 0.75rem;
    color: var(--muted);
  }
  .cp-total strong { font-family: 'Syne', sans-serif; font-size: 1.1rem; color: #fff; margin-right: 6px; }

  /* ── Stats ── */
  .stats-note {
    font-size: 0.7rem;
    color: var(--muted);
    text-align: center;
    margin-bottom: 12px;
    font-style: italic;
  }

  /* ── Footer ── */
  .footer {
    margin-top: 60px;
    text-align: center;
    font-size: 0.68rem;
    color: rgba(255,255,255,0.15);
    letter-spacing: 0.08em;
  }

  /* ── Animations ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .section:nth-child(1) { animation-delay: 0.35s; }
  .section:nth-child(2) { animation-delay: 0.45s; }
  .section:nth-child(3) { animation-delay: 0.55s; }
  .section:nth-child(4) { animation-delay: 0.65s; }
  .section:nth-child(5) { animation-delay: 0.75s; }
</style>
</head>
<body>

<!-- ── HERO ── -->
<div class="hero">
  <div class="hero-bg"></div>
  <div class="hero-name">Tahmid Al Mamun</div>
  <div class="hero-role">Founder @ Bridge Byte Tech <span>·</span> Leading University, CSE</div>
  <p class="hero-desc">Software engineer focused on backend systems, mobile apps, and end-to-end product development. Building scalable, clean-architected products — from idea to deployment.</p>
  <div class="contacts">
    <a class="btn" href="https://bridgebytetech.com/" target="_blank">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><circle cx="12" cy="12" r="10"/><path d="M2 12h20M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>
      Bridge Byte Tech
    </a>
    <a class="btn" href="https://www.linkedin.com/in/tahmid-al-mamun-042236215/" target="_blank">
      <svg viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
      LinkedIn
    </a>
    <a class="btn" href="mailto:tahmid.mamun@bridgebytetech.com">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
      Email
    </a>
  </div>
</div>

<div class="page">

  <!-- ── ABOUT ── -->
  <div class="section">
    <div class="section-label">About</div>
    <div class="about-card">
      <div class="about-title">Building things<br>that scale.</div>
      <div class="about-sub">Backend · Mobile · Systems · Product</div>
      <div class="open-tag">open to collaborations</div>
    </div>
  </div>

  <!-- ── STACK ── -->
  <div class="section">
    <div class="section-label">Stack</div>
    <div class="pills">
      <span class="pill">Java</span>
      <span class="pill">Spring Boot</span>
      <span class="pill">Spring Security</span>
      <span class="pill">REST API</span>
      <span class="pill">Kotlin</span>
      <span class="pill">Android</span>
      <span class="pill">Flutter</span>
      <span class="pill">PostgreSQL</span>
      <span class="pill">MySQL</span>
      <span class="pill">Redis</span>
      <span class="pill">MongoDB</span>
      <span class="pill">Microservices</span>
      <span class="pill">Clean Architecture</span>
      <span class="pill">System Design</span>
    </div>
  </div>

  <!-- ── PROJECTS ── -->
  <div class="section">
    <div class="section-label">Projects</div>
    <div class="projects-grid">

      <a class="proj-card featured" href="https://hadiarchive.com/" target="_blank">
        <div class="proj-header">
          <div class="proj-name">Hadi Archive</div>
          <span class="proj-badge badge-live">Live</span>
        </div>
        <div class="proj-desc">In the memory of great revolutionary Shaheed Sharif Osman Gani Bin Hadi. A comprehensive Islamic knowledge archive — structured, scalable, and built for long-term accessibility.</div>
        <div class="proj-tags">
          <span class="proj-tag">Spring Boot</span>
          <span class="proj-tag">PostgreSQL</span>
          <span class="proj-tag">Clean Architecture</span>
        </div>
        <div class="proj-url">hadiarchive.com ↗</div>
      </a>

      <a class="proj-card" href="https://resezy.com/" target="_blank">
        <div class="proj-header">
          <div class="proj-name">Resezy</div>
          <span class="proj-badge badge-live">Live</span>
        </div>
        <div class="proj-desc">Seamless experience platform, designed and deployed end-to-end with a focus on usability.</div>
        <div class="proj-tags">
          <span class="proj-tag">Flutter</span>
          <span class="proj-tag">REST API</span>
          <span class="proj-tag">JWT</span>
        </div>
        <div class="proj-url">resezy.com ↗</div>
      </a>

      <a class="proj-card" href="https://play.google.com/store/apps/details?id=com.abir.sylhetpedia" target="_blank">
        <div class="proj-header">
          <div class="proj-name">Sylhet Pedia</div>
          <span class="proj-badge badge-store">Play Store</span>
        </div>
        <div class="proj-desc">Regional knowledge app for Sylhet — offline-ready, fast, and user-friendly.</div>
        <div class="proj-tags">
          <span class="proj-tag">Kotlin</span>
          <span class="proj-tag">Android</span>
          <span class="proj-tag">Offline-first</span>
        </div>
        <div class="proj-url">Google Play ↗</div>
      </a>

      <a class="proj-card" href="https://pussho.com/" target="_blank">
        <div class="proj-header">
          <div class="proj-name">Pussho</div>
          <span class="proj-badge badge-dev">In Dev</span>
        </div>
        <div class="proj-desc">A new mobile product currently in active development. Stay tuned for the release.</div>
        <div class="proj-tags">
          <span class="proj-tag">Mobile</span>
          <span class="proj-tag">In Progress</span>
        </div>
        <div class="proj-url">pussho.com ↗</div>
      </a>

      <a class="proj-card" href="https://www.dfitcentre.com/" target="_blank">
        <div class="proj-header">
          <div class="proj-name">DF IT Centre</div>
          <span class="proj-badge badge-live">Live</span>
        </div>
        <div class="proj-desc">Clean, functional IT centre platform built for real users and real workflows.</div>
        <div class="proj-tags">
          <span class="proj-tag">Web</span>
          <span class="proj-tag">Client Work</span>
        </div>
        <div class="proj-url">dfitcentre.com ↗</div>
      </a>

    </div>
  </div>

  <!-- ── COMPETITIVE PROGRAMMING ── -->
  <div class="section">
    <div class="section-label">Competitive Programming</div>
    <div class="cp-grid">
      <div class="cp-card">
        <div class="cp-platform">LeetCode</div>
        <div class="cp-num">1,429</div>
        <div class="cp-sub">Rating</div>
      </div>
      <div class="cp-card">
        <div class="cp-platform">Codeforces</div>
        <div class="cp-num">1,153</div>
        <div class="cp-sub">Rating</div>
      </div>
      <div class="cp-card">
        <div class="cp-platform">CodeChef</div>
        <div class="cp-num">1,259</div>
        <div class="cp-sub">Rating</div>
      </div>
    </div>
    <div class="cp-total"><strong>600+</strong> problems solved across all platforms</div>
  </div>

  <!-- ── FOOTER ── -->
  <div class="footer">Building things that scale. Solving problems that matter.</div>

</div>

<script>
  // Mouse-tracking glow on project cards
  document.querySelectorAll('.proj-card').forEach(card => {
    card.addEventListener('mousemove', e => {
      const r = card.getBoundingClientRect();
      card.style.setProperty('--mx', ((e.clientX - r.left) / r.width * 100) + '%');
      card.style.setProperty('--my', ((e.clientY - r.top) / r.height * 100) + '%');
    });
  });

  // Intersection observer for staggered section reveals
  const sections = document.querySelectorAll('.section');
  const io = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.style.opacity = 1; io.unobserve(e.target); } });
  }, { threshold: 0.1 });
  sections.forEach(s => { s.style.opacity = 0; io.observe(s); });
</script>
</body>
</html>
