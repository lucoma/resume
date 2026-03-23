<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Luis Coll Martinez, PMP®</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400;1,700&family=Lora:ital,wght@0,400;0,500;0,600;1,400;1,500&display=swap" rel="stylesheet">
<style>
       :root {
           --green-deep:   #0f1f13;
           --green-mid:    #172a1c;
           --green-card:   #1e3526;
           --gold:         #e8b84b;
           --gold-light:   #f0c96a;
           --cream:        #f0e8d5;
           --cream-muted:  #c8c3b8;
           --text-body:    #e8e4dd;
           --glass-bg:     rgba(12, 28, 17, 0.82);
           --glass-border: rgba(255,255,255,0.13);
       }
```
   *, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }
   html { scroll-behavior: smooth; }
   body {
       background-color: var(--green-deep);
       color: var(--cream);
       font-family: 'Lora', Georgia, serif;
       overflow-x: hidden;
   }
   /* grain overlay */
   body::after {
       content:'';
       position:fixed; inset:0;
       background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");
       pointer-events:none;
       z-index:9999;
   }
   /* ── NAV ── */
   nav {
       position:fixed; top:0; left:0; right:0; z-index:200;
       padding:18px 60px;
       display:flex; align-items:center; justify-content:space-between;
       backdrop-filter:blur(24px); -webkit-backdrop-filter:blur(24px);
       background:rgba(21,37,25,0.72);
       border-bottom:1px solid var(--glass-border);
       transition:background .3s;
   }
   .nav-logo {
       font-family:'Playfair Display',serif;
       font-weight:700; font-size:1rem;
       color:var(--cream); letter-spacing:.03em;
   }
   .nav-logo span { color:var(--gold); }
   .nav-links { display:flex; gap:36px; list-style:none; }
   .nav-links a {
       font-size:.78rem; letter-spacing:.12em; text-transform:uppercase;
       color:var(--text-body); text-decoration:none;
       transition:color .2s;
   }
   .nav-links a:hover { color:var(--gold); }
   /* ── HERO ── */
   #hero {
       min-height:100vh;
       display:flex; align-items:center;
       padding:130px 60px 90px;
       position:relative; overflow:hidden;
   }
   .hero-bg-circles {
       position:absolute; inset:0;
       pointer-events:none;
   }
   .hero-bg-circles circle {
       fill:none;
       stroke:rgba(232,184,75,.07);
       stroke-width:1;
   }
   /* ambient glow blobs */
   .blob {
       position:absolute;
       border-radius:50%;
       filter:blur(120px);
       pointer-events:none;
   }
   .blob-1 {
       width:600px; height:600px;
       background:radial-gradient(circle, rgba(232,184,75,.09) 0%, transparent 70%);
       top:-100px; right:-100px;
   }
   .blob-2 {
       width:400px; height:400px;
       background:radial-gradient(circle, rgba(34,80,50,.4) 0%, transparent 70%);
       bottom:0; left:-80px;
   }
   .hero-inner {
       position:relative; z-index:2;
       max-width:1160px; margin:0 auto; width:100%;
       display:grid; grid-template-columns:1fr 260px;
       gap:80px; align-items:center;
   }
   .hero-eyebrow {
       display:inline-flex; align-items:center; gap:10px;
       font-size:.72rem; letter-spacing:.18em; text-transform:uppercase;
       color:var(--gold); margin-bottom:22px;
       opacity:0; animation:fadeUp .7s ease .15s forwards;
   }
   .hero-eyebrow::before {
       content:''; display:block;
       width:28px; height:1px; background:var(--gold);
   }
   h1.hero-name {
       font-family:'Playfair Display',serif;
       font-size:clamp(3.2rem,5.5vw,5.8rem);
       font-weight:900; line-height:1.03;
       color:var(--cream); margin-bottom:10px;
       opacity:0; animation:fadeUp .7s ease .3s forwards;
   }
   h1.hero-name em { font-style:italic; color:var(--gold); }
   .hero-title {
       font-family:'Playfair Display',serif;
       font-style:italic; font-weight:400;
       font-size:clamp(1rem,1.8vw,1.3rem);
       color:var(--text-body); margin-bottom:30px;
       opacity:0; animation:fadeUp .7s ease .45s forwards;
   }
   .hero-bio {
       font-size:1rem; line-height:1.85;
       color:var(--text-body); max-width:600px;
       margin-bottom:36px;
       opacity:0; animation:fadeUp .7s ease .6s forwards;
   }
   .hero-pills {
       display:flex; flex-wrap:wrap; gap:9px;
       margin-bottom:44px;
       opacity:0; animation:fadeUp .7s ease .75s forwards;
   }
   .pill {
       padding:5px 15px; border-radius:100px;
       font-size:.7rem; letter-spacing:.1em; text-transform:uppercase;
       border:1px solid rgba(232,184,75,.45);
       color:var(--gold-light);
       background:rgba(232,184,75,.1);
   }
   .hero-cta {
       display:flex; gap:14px; flex-wrap:wrap;
       opacity:0; animation:fadeUp .7s ease .9s forwards;
   }
   .btn-gold {
       padding:13px 30px;
       background:var(--gold); color:var(--green-deep);
       font-family:'Lora',serif; font-size:.8rem;
       font-weight:700; letter-spacing:.08em; text-transform:uppercase;
       text-decoration:none; border-radius:5px;
       transition:all .25s ease;
   }
   .btn-gold:hover { background:var(--gold-light); transform:translateY(-2px); }
   .btn-ghost {
       padding:13px 30px;
       background:rgba(255,255,255,.07); color:var(--cream);
       font-family:'Lora',serif; font-size:.8rem;
       letter-spacing:.08em; text-transform:uppercase;
       text-decoration:none; border-radius:5px;
       border:1px solid rgba(255,255,255,.28);
       backdrop-filter:blur(12px);
       transition:all .25s ease;
   }
   .btn-ghost:hover { border-color:var(--gold); color:var(--gold); }
   /* Typographic Avatar */
   .avatar-wrap {
       opacity:0; animation:fadeIn 1s ease 1s forwards;
       display:flex; justify-content:center;
   }
   .avatar-ring {
       width:230px; height:230px; border-radius:50%;
       border:1px solid rgba(232,184,75,.28);
       display:flex; align-items:center; justify-content:center;
       position:relative;
       backdrop-filter:blur(24px); -webkit-backdrop-filter:blur(24px);
       background:radial-gradient(circle at 35% 35%, rgba(232,184,75,.13), rgba(21,37,25,.55));
       box-shadow:0 0 70px rgba(232,184,75,.1), inset 0 0 50px rgba(232,184,75,.05);
       animation:float 9s ease-in-out infinite;
   }
   .avatar-ring::before {
       content:''; position:absolute; inset:-10px;
       border-radius:50%;
       border:1px solid rgba(232,184,75,.1);
   }
   .avatar-ring::after {
       content:''; position:absolute; inset:-24px;
       border-radius:50%;
       border:1px solid rgba(232,184,75,.05);
   }
   .avatar-initials {
       font-family:'Playfair Display',serif;
       font-size:4.2rem; font-weight:900;
       color:var(--cream); letter-spacing:-.02em;
       line-height:1;
   }
   .avatar-initials span { color:var(--gold); }
   /* ── SECTION BASE ── */
   section { padding:100px 60px; position:relative; }
   .section-inner { max-width:1100px; margin:0 auto; }
   .section-eyebrow {
       display:flex; align-items:center; gap:12px;
       font-size:.7rem; letter-spacing:.2em; text-transform:uppercase;
       color:var(--gold); margin-bottom:14px; font-family:'Lora',serif;
   }
   .section-eyebrow::after {
       content:''; width:48px; height:1px;
       background:rgba(232,184,75,.45);
   }
   .section-h2 {
       font-family:'Playfair Display',serif;
       font-size:clamp(2rem,3.8vw,3rem); font-weight:700;
       color:var(--cream); line-height:1.2; margin-bottom:60px;
   }
   /* ── GLASS CARD ── */
   .glass {
       background:var(--glass-bg);
       backdrop-filter:blur(22px); -webkit-backdrop-filter:blur(22px);
       border:1px solid var(--glass-border);
       border-radius:18px;
       box-shadow:0 8px 40px rgba(0,0,0,.35), inset 0 1px 0 rgba(255,255,255,.06);
   }
   /* ── TIMELINE ── */
   #experience {
       background:linear-gradient(180deg, var(--green-deep) 0%, rgba(28,51,35,.6) 100%);
   }
   .timeline { position:relative; padding:10px 0; }
   .timeline::before {
       content:''; position:absolute;
       left:50%; top:0; bottom:0; width:1px;
       background:linear-gradient(180deg,
           transparent 0%,
           rgba(232,184,75,.35) 8%,
           rgba(232,184,75,.35) 92%,
           transparent 100%);
       transform:translateX(-50%);
   }
   .tl-item {
       display:grid;
       grid-template-columns:1fr 64px 1fr;
       margin-bottom:48px; align-items:center;
       opacity:0; transform:translateY(32px);
       transition:opacity .7s cubic-bezier(.25,.46,.45,.94),
                   transform .7s cubic-bezier(.25,.46,.45,.94);
   }
   .tl-item.vis { opacity:1; transform:translateY(0); }
   /* odd → card left, even → card right */
   .tl-item:nth-child(odd)  .tl-card  { grid-column:1; margin-right:24px; }
   .tl-item:nth-child(odd)  .tl-node  { grid-column:2; }
   .tl-item:nth-child(odd)  .tl-empty { grid-column:3; }
   .tl-item:nth-child(even) .tl-empty { grid-column:1; }
   .tl-item:nth-child(even) .tl-node  { grid-column:2; }
   .tl-item:nth-child(even) .tl-card  { grid-column:3; margin-left:24px; }
   .tl-node {
       display:flex; align-items:center; justify-content:center;
       position:relative; z-index:2;
   }
   .tl-dot {
       width:13px; height:13px; border-radius:50%;
       background:var(--gold);
       border:3px solid var(--green-deep);
       box-shadow:0 0 0 1px var(--gold), 0 0 18px rgba(232,184,75,.45);
   }
   .tl-dot::after {
       content:''; position:absolute;
       inset:-7px; border-radius:50%;
       border:1px solid rgba(232,184,75,.18);
       animation:pulse 2.2s ease-in-out infinite;
   }
   .tl-card { padding:26px 30px; }
   .tl-date {
       font-size:.7rem; letter-spacing:.1em; text-transform:uppercase;
       color:var(--gold); margin-bottom:6px;
   }
   .tl-role {
       font-family:'Playfair Display',serif;
       font-size:1.1rem; font-weight:700;
       color:var(--cream); margin-bottom:4px; line-height:1.3;
   }
   .tl-company {
       font-size:.85rem; font-style:italic;
       color:var(--cream-muted); margin-bottom:12px;
   }
   .tl-desc {
       font-size:.85rem; line-height:1.78;
       color:var(--text-body);
   }
   /* ── NEWSLETTER ── */
   #newsletter { background:var(--green-deep); }
   .nl-brand { text-align:center; margin-bottom:64px; }
   .nl-logo {
       font-family:'Playfair Display',serif;
       font-size:clamp(2.8rem,5vw,5rem);
       font-weight:900; color:var(--cream); line-height:1.05;
   }
   .nl-logo em { font-style:italic; color:var(--gold); }
   .nl-sub {
       margin-top:12px; font-style:italic;
       font-size:.95rem; color:var(--text-body);
   }
   .nl-grid {
       display:grid; grid-template-columns:repeat(3,1fr);
       gap:22px; margin-bottom:44px;
   }
   .nl-card {
       padding:30px; position:relative; overflow:hidden;
       transition:transform .3s ease, box-shadow .3s ease;
   }
   .nl-card:hover {
       transform:translateY(-5px);
       box-shadow:0 20px 56px rgba(0,0,0,.45), inset 0 1px 0 rgba(255,255,255,.09);
   }
   .nl-card::before {
       content:''; position:absolute;
       top:0; left:0; right:0; height:2px;
       background:linear-gradient(90deg, transparent, var(--gold), transparent);
       opacity:.55;
   }
   .nl-num {
       position:absolute; top:14px; right:18px;
       font-family:'Playfair Display',serif;
       font-size:3.8rem; font-weight:900;
       color:rgba(255,255,255,.035); line-height:1;
   }
   .nl-tag {
       display:inline-block;
       padding:3px 11px;
       background:var(--gold); color:var(--green-deep);
       font-size:.62rem; font-weight:700; letter-spacing:.16em;
       text-transform:uppercase; border-radius:3px;
       margin-bottom:14px;
   }
   .nl-headline {
       font-family:'Playfair Display',serif;
       font-size:1.08rem; font-weight:700;
       color:var(--cream); line-height:1.4; margin-bottom:11px;
   }
   .nl-body {
       font-size:.83rem; line-height:1.75;
       color:var(--text-body);
   }
   .nl-cta-row {
       text-align:center;
       padding:36px 40px;
       border:1px dashed rgba(232,184,75,.2);
       border-radius:16px;
   }
   .nl-cta-row p {
       font-family:'Playfair Display',serif;
       font-style:italic; font-size:1.05rem;
       color:var(--text-body); margin-bottom:22px;
   }
   /* ── CONTACT ── */
   #contact {
       background:linear-gradient(180deg, rgba(28,51,35,.35) 0%, var(--green-deep) 100%);
   }
   .contact-grid { display:grid; grid-template-columns:1fr 1fr; gap:48px; align-items:start; }
   .contact-h2 {
       font-family:'Playfair Display',serif;
       font-size:clamp(1.8rem,3.5vw,2.8rem);
       font-weight:700; color:var(--cream); line-height:1.2; margin-bottom:18px;
   }
   .contact-h2 em { font-style:italic; color:var(--gold); }
   .contact-bio {
       font-size:.95rem; line-height:1.85;
       color:var(--text-body); margin-bottom:36px;
   }
   .contact-items { display:flex; flex-direction:column; gap:12px; }
   .c-link {
       display:flex; align-items:center; gap:16px;
       text-decoration:none; padding:16px 20px; border-radius:12px;
       transition:all .25s ease;
   }
   .c-link:hover { background:rgba(255,255,255,.05); transform:translateX(4px); }
   .c-icon {
       width:40px; height:40px; border-radius:10px; flex-shrink:0;
       background:rgba(232,184,75,.1); border:1px solid rgba(232,184,75,.2);
       display:flex; align-items:center; justify-content:center;
   }
   .c-icon svg { width:17px; height:17px; fill:var(--gold); }
   .c-meta { display:flex; flex-direction:column; }
   .c-label {
       font-size:.66rem; letter-spacing:.13em; text-transform:uppercase;
       color:var(--cream-muted);
   }
   .c-val { font-size:.9rem; color:var(--cream); }
   /* Skills panel */
   .skills-panel { padding:32px 34px; }
   .sk-group { margin-bottom:26px; }
   .sk-group:last-child { margin-bottom:0; }
   .sk-title {
       font-size:.66rem; letter-spacing:.18em; text-transform:uppercase;
       color:var(--gold); margin-bottom:11px;
   }
   .sk-tags { display:flex; flex-wrap:wrap; gap:7px; }
   .sk-tag {
       padding:4px 13px; font-size:.78rem; border-radius:100px;
       background:rgba(255,255,255,.07);
       border:1px solid rgba(255,255,255,.16);
       color:var(--text-body);
   }
   /* ── FOOTER ── */
   footer {
       padding:28px 60px;
       border-top:1px solid var(--glass-border);
       display:flex; justify-content:space-between; align-items:center;
   }
   .footer-brand {
       font-family:'Playfair Display',serif;
       font-size:.85rem; color:var(--cream-muted);
   }
   .footer-brand span { color:var(--gold); }
   .footer-note {
       font-size:.72rem; font-style:italic;
       color:rgba(184,174,152,.38);
   }
   /* ── KEYFRAMES ── */
   @keyframes fadeUp {
       from { opacity:0; transform:translateY(22px); }
       to   { opacity:1; transform:translateY(0); }
   }
   @keyframes fadeIn {
       from { opacity:0; } to { opacity:1; }
   }
   @keyframes pulse {
       0%,100% { opacity:.4; transform:scale(1); }
       50%      { opacity:.08; transform:scale(1.7); }
   }
   @keyframes float {
       0%,100% { transform:translateY(0)    rotate(0deg);  }
       33%      { transform:translateY(-14px) rotate(.8deg);  }
       66%      { transform:translateY(-7px)  rotate(-.8deg); }
   }
   /* ── RESPONSIVE ── */
   @media(max-width:940px){
       nav { padding:16px 24px; }
       section { padding:70px 24px; }
       #hero { padding:110px 24px 60px; }
       .hero-inner { grid-template-columns:1fr; gap:44px; }
       .avatar-wrap { justify-content:flex-start; }
       .timeline::before { left:28px; }
       .tl-item { grid-template-columns:56px 1fr !important; }
       .tl-item .tl-node  { grid-column:1 !important; grid-row:1; }
       .tl-item .tl-card  { grid-column:2 !important; grid-row:1; margin:0 0 0 14px !important; }
       .tl-item .tl-empty { display:none !important; }
       .nl-grid { grid-template-columns:1fr; }
       .contact-grid { grid-template-columns:1fr; }
       footer { flex-direction:column; gap:6px; text-align:center; }
   }
</style>
```
</head>
<body>
<!-- NAV -->
<nav id="nav">
<div class="nav-logo">Luis Coll <span>Martinez</span></div>
<ul class="nav-links">
<li><a href="#experience">Experience</a></li>
<li><a href="#newsletter">Newsletter</a></li>
<li><a href="#contact">Contact</a></li>
</ul>
</nav>
<!-- ══ HERO ══ -->
<section id="hero">
<svg class="hero-bg-circles" viewBox="0 0 1440 900" preserveAspectRatio="xMidYMid slice">
<circle cx="980"  cy="260" r="380"/>
<circle cx="1160" cy="160" r="260"/>
<circle cx="760"  cy="480" r="210"/>
<circle cx="1300" cy="600" r="160"/>
</svg>
<div class="blob blob-1"></div>
<div class="blob blob-2"></div>
```
<div class="hero-inner">
<div class="hero-text">
<div class="hero-eyebrow">Valencia, Spain &nbsp;·&nbsp; Available for Relocation</div>
<h1 class="hero-name">Luis Coll<br><em>Martinez</em></h1>
<p class="hero-title">Program Director &nbsp;·&nbsp; PMP® &nbsp;·&nbsp; AI & Enterprise Transformation</p>
<p class="hero-bio">
           Executive-level program leader with 9+ years delivering multi-million dollar digital
           transformations for global industry leaders. I bridge the gap between legacy enterprise
           systems and Generative AI — and help executives understand what it all means for their business.
</p>
<div class="hero-pills">
<span class="pill">Supply Chain</span>
<span class="pill">Generative AI</span>
<span class="pill">Digital Transformation</span>
<span class="pill">SaaS</span>
<span class="pill">B2B Integration</span>
<span class="pill">PMP®</span>
</div>
<div class="hero-cta">
<a href="#newsletter" class="btn-gold">In the Loop ↓</a>
<a href="#experience" class="btn-ghost">View Experience</a>
</div>
</div>
<div class="avatar-wrap">
<div class="avatar-ring">
<div class="avatar-initials">L<span>C</span></div>
</div>
</div>
</div>
```
</section>
<!-- ══ EXPERIENCE ══ -->
<section id="experience">
<div class="section-inner">
<div class="section-eyebrow">Career</div>
<h2 class="section-h2">Where I've Been,<br>What I've Built</h2>
```
<div class="timeline">
<div class="tl-item">
<div class="tl-card glass">
<div class="tl-date">Feb 2025 — Present</div>
<div class="tl-role">Senior Program Manager</div>
<div class="tl-company">e2open · Remote, Spain</div>
<div class="tl-desc">Leading $1.5M+ SaaS implementation portfolios via Planview and Salesforce. Built a data-first project health framework in Jira that reduced scope creep by 15%. Mentoring a cross-functional team of 5 in a culture of continuous improvement.</div>
</div>
<div class="tl-node"><div class="tl-dot"></div></div>
<div class="tl-empty"></div>
</div>
<div class="tl-item">
<div class="tl-empty"></div>
<div class="tl-node"><div class="tl-dot"></div></div>
<div class="tl-card glass">
<div class="tl-date">2024 — Jan 2025</div>
<div class="tl-role">Global Product Owner</div>
<div class="tl-company">A.P. Moller – Maersk · Remote, Spain</div>
<div class="tl-desc">Launched 3 new global transport integration products, driving a 60% increase in implementation efficiency. Enhanced the self-service API Developer Portal, cutting customer integration time by 30%.</div>
</div>
</div>
<div class="tl-item">
<div class="tl-card glass">
<div class="tl-date">2022 — 2024</div>
<div class="tl-role">Project Manager</div>
<div class="tl-company">A.P. Moller – Maersk · Remote, Spain</div>
<div class="tl-desc">Managed complex end-to-end delivery of supply chain EDI and integration projects across OpenText, SEEBURGER, SAP, and Oracle OCI. Achieved a 100% customer satisfaction score across all engagements.</div>
</div>
<div class="tl-node"><div class="tl-dot"></div></div>
<div class="tl-empty"></div>
</div>
<div class="tl-item">
<div class="tl-empty"></div>
<div class="tl-node"><div class="tl-dot"></div></div>
<div class="tl-card glass">
<div class="tl-date">2020 — 2022</div>
<div class="tl-role">Department Manager, Asia/Pacific</div>
<div class="tl-company">EDICOM · Valencia, Spain</div>
<div class="tl-desc">Scaled the APAC division from zero across India, China, and Japan. Indirectly managed a team of 40 engineers and drove double-digit revenue growth, reporting directly to the CTO.</div>
</div>
</div>
<div class="tl-item">
<div class="tl-card glass">
<div class="tl-date">2016 — 2020</div>
<div class="tl-role">Program Manager → Integration Engineer</div>
<div class="tl-company">EDICOM · Valencia, Spain</div>
<div class="tl-desc">Built operational frameworks for the top 5 clients in the Americas, delivering 60+ simultaneous integration projects. Started as a technical Integration Engineer, developing data transformation scripts and aligning solutions with business requirements.</div>
</div>
<div class="tl-node"><div class="tl-dot"></div></div>
<div class="tl-empty"></div>
</div>
</div>
</div>
```
</section>
<!-- ══ IN THE LOOP ══ -->
<section id="newsletter">
<div class="section-inner">
<div class="nl-brand">
<div class="nl-logo">In The Loop<br><em>with Luis</em></div>
<p class="nl-sub">AI moves fast. Stay in the loop.</p>
</div>
```
<div class="nl-grid">
<div class="nl-card glass">
<div class="nl-num">01</div>
<div class="nl-tag">AI Models</div>
<div class="nl-headline">GPT-5 just scored above human baseline on real work tasks</div>
<div class="nl-body">OpenAI's GPT-5 hit 75% on OSWorld-V — a benchmark of real desktop tasks. It can now autonomously run multi-step workflows across apps, without a human in the loop. Humans scored 72.4% on the same tasks.</div>
</div>
<div class="nl-card glass">
<div class="nl-num">02</div>
<div class="nl-tag">Future of Work</div>
<div class="nl-headline">McKinsey now interviews candidates with AI — not just for AI roles</div>
<div class="nl-body">Final-round applicants must use "Lilli," McKinsey's internal AI platform, to solve live business cases. They're not testing if you know AI exists — they're testing if you can think alongside it under pressure.</div>
</div>
<div class="nl-card glass">
<div class="nl-num">03</div>
<div class="nl-tag">Enterprise AI</div>
<div class="nl-headline">AI adoption up 13%. Worker confidence just collapsed 18%.</div>
<div class="nl-body">The gap between deployment speed and human readiness is widening. Companies are rolling out AI faster than their people can adapt — and the confidence data shows exactly where the fracture lines are.</div>
</div>
</div>
<div class="nl-cta-row">
<p>More issues coming to this page soon — follow along on LinkedIn in the meantime.</p>
<a href="https://www.linkedin.com/in/luis-coll-martinez/" target="_blank" class="btn-gold">Follow on LinkedIn →</a>
</div>
</div>
```
</section>
<!-- ══ CONTACT ══ -->
<section id="contact">
<div class="section-inner">
<div class="section-eyebrow">Get in Touch</div>
<div class="contact-grid">
<div>
<h2 class="contact-h2">Let's build something<br><em>meaningful together</em></h2>
<p class="contact-bio">Whether you're navigating a complex digital transformation, exploring how AI fits into your strategy, or just want to talk enterprise — I'm always up for a good conversation.</p>
<div class="contact-items">
<a href="mailto:luis.coll.martinez@gmail.com" class="c-link">
<div class="c-icon">
<svg viewBox="0 0 24 24"><path d="M20 4H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg>
</div>
<div class="c-meta">
<span class="c-label">Email</span>
<span class="c-val">luis.coll.martinez@gmail.com</span>
</div>
</a>
<a href="https://www.linkedin.com/in/luis-coll-martinez/" target="_blank" class="c-link">
<div class="c-icon">
<svg viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
</div>
<div class="c-meta">
<span class="c-label">LinkedIn</span>
<span class="c-val">/in/luis-coll-martinez</span>
</div>
</a>
<a href="tel:+34651381183" class="c-link">
<div class="c-icon">
<svg viewBox="0 0 24 24"><path d="M6.62 10.79c1.44 2.83 3.76 5.14 6.59 6.59l2.2-2.2c.27-.27.67-.36 1.02-.24 1.12.37 2.33.57 3.57.57.55 0 1 .45 1 1V20c0 .55-.45 1-1 1-9.39 0-17-7.61-17-17 0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.25.2 2.45.57 3.57.11.35.03.74-.25 1.02l-2.2 2.2z"/></svg>
</div>
<div class="c-meta">
<span class="c-label">Phone</span>
<span class="c-val">+34 651 38 11 83</span>
</div>
</a>
</div>
</div>
```
<div class="skills-panel glass">
<div class="sk-group">
<div class="sk-title">Strategic Leadership</div>
<div class="sk-tags">
<span class="sk-tag">Portfolio Management</span>
<span class="sk-tag">Enterprise Risk</span>
<span class="sk-tag">Global Transformation</span>
<span class="sk-tag">SDLC Optimization</span>
<span class="sk-tag">OKR & KPI</span>
<span class="sk-tag">Vendor Management</span>
</div>
</div>
<div class="sk-group">
<div class="sk-title">AI & Innovation</div>
<div class="sk-tags">
<span class="sk-tag">Generative AI</span>
<span class="sk-tag">RAG Architecture</span>
<span class="sk-tag">AI Use Case Design</span>
<span class="sk-tag">n8n Automation</span>
<span class="sk-tag">Vector DBs</span>
</div>
</div>
<div class="sk-group">
<div class="sk-title">Domain Expertise</div>
<div class="sk-tags">
<span class="sk-tag">Supply Chain</span>
<span class="sk-tag">B2B Integration</span>
<span class="sk-tag">EDI / API / XML</span>
<span class="sk-tag">SaaS Lifecycle</span>
<span class="sk-tag">Cloud Migration</span>
</div>
</div>
</div>
</div>
</div>
```
</section>
<footer>
<div class="footer-brand">Luis Coll <span>Martinez</span> &nbsp;·&nbsp; PMP®</div>
<div class="footer-note">Valencia, Spain · Available for relocation</div>
</footer>
<script>
   // ── Timeline scroll animation ──
   const tlItems = document.querySelectorAll('.tl-item');
   const tlObs = new IntersectionObserver((entries) => {
       entries.forEach((entry, i) => {
           if (entry.isIntersecting) {
               setTimeout(() => entry.target.classList.add('vis'), i * 80);
           }
       });
   }, { threshold: 0.12, rootMargin:'0px 0px -40px 0px' });
   tlItems.forEach(el => tlObs.observe(el));
   // ── Newsletter cards stagger ──
   const nlCards = document.querySelectorAll('.nl-card');
   const nlObs = new IntersectionObserver((entries) => {
       entries.forEach((entry, i) => {
           if (entry.isIntersecting) {
               setTimeout(() => {
                   entry.target.style.opacity = '1';
                   entry.target.style.transform = 'translateY(0)';
               }, i * 130);
           }
       });
   }, { threshold: 0.1 });
   nlCards.forEach(card => {
       card.style.opacity = '0';
       card.style.transform = 'translateY(26px)';
       card.style.transition = 'opacity .65s cubic-bezier(.25,.46,.45,.94), transform .65s cubic-bezier(.25,.46,.45,.94)';
       nlObs.observe(card);
   });
   // ── Nav tint on scroll ──
   window.addEventListener('scroll', () => {
       document.getElementById('nav').style.background =
           window.scrollY > 60
               ? 'rgba(21,37,25,0.96)'
               : 'rgba(21,37,25,0.72)';
   }, { passive: true });
</script>
</body>
</html>
