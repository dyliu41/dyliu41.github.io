<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Daniel Liu — Portfolio</title>
  <meta name="description" content="Professional website for Daniel Liu: experiences, extracurriculars, education, and hobbies." />
  <!-- Self-contained. No external fonts/resources. Apple.com-inspired light theme -->
  <style>
    :root{
      --bg:#ffffff;           /* page */
      --ink:#0f1115;          /* headings/body */
      --muted:#6b7280;        /* secondary text */
      --line:#e5e7eb;         /* hairline */
      --card:#ffffff;         /* cards */
      --accent:#0071e3;       /* Apple blue */
      --radius:16px;
      --shadow:0 10px 30px rgba(0,0,0,.06);
      --maxw:1120px;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{margin:0; background:var(--bg); color:var(--ink); font-family:system-ui,-apple-system,Segoe UI,Roboto,Helvetica,Arial,sans-serif}
    a{color:inherit; text-decoration:none}

    /* ===== Header (frosted) ===== */
    .topbar{position:sticky; top:0; z-index:50; backdrop-filter:saturate(150%) blur(14px); background:rgba(255,255,255,.75); border-bottom:1px solid var(--line)}
    .topbar .wrap{max-width:var(--maxw); margin:0 auto; padding:10px 18px; display:flex; align-items:center; gap:14px}
    .logo{width:28px; height:28px; border-radius:8px; background:#111; color:#fff; display:grid; place-items:center; font-weight:800}
    .name{font-weight:700}

    .nav{margin-left:auto; display:flex; align-items:center; gap:8px; position:relative}
    .nav .item{position:relative}
    .nav .link{padding:8px 10px; border-radius:10px; font-weight:600}
    .nav .link:hover{background:#f7f7f8}
    .dropdown{position:absolute; top:100%; left:0; display:none; background:#fff; border:1px solid var(--line); border-radius:14px; box-shadow:var(--shadow); padding:12px; min-width:340px}
    .item:hover .dropdown{display:block}
    .dropdown a{display:block; padding:10px; border-radius:10px; color:#0f1115}
    .dropdown a:hover{background:#f7f7f8}

    /* ===== Hero (full-bleed image, white text) ===== */
    .hero{position:relative; min-height:70vh; border-bottom:1px solid var(--line);}
    .hero figure{position:absolute; inset:0; margin:0}
    .hero img{width:100%; height:100%; object-fit:cover; filter:saturate(105%) brightness(.65)}
    .hero .inner{position:relative; z-index:2; max-width:var(--maxw); margin:0 auto; padding:72px 18px 48px; color:#fff; text-align:center}
    .hero h1{font-size:56px; line-height:1.05; margin:0}
    .hero p{font-size:20px; color:#e5e7eb; margin:10px auto 18px; max-width:820px}
    .cta{display:flex; gap:12px; justify-content:center}
    .btn{display:inline-flex; align-items:center; justify-content:center; padding:12px 18px; border-radius:999px; font-weight:700; border:1px solid rgba(255,255,255,.25)}
    .btn.primary{background:var(--accent); color:#fff; border:none}
    .btn.ghost{background:transparent; color:#fff}
    .btn.ghost:hover{background:rgba(255,255,255,.12)}

    /* ===== Sections & cards ===== */
    .wrap-main{max-width:var(--maxw); margin:0 auto; padding:28px 18px}
    section[role="tabpanel"]{display:none}
    section.active{display:block}
    .section{padding:48px 0}
    .section h2{font-size:32px; margin:0 0 6px}
    .lead{color:var(--muted); margin:0 0 20px}

    .grid{display:grid; gap:16px}
    .cols-2{grid-template-columns:repeat(2,minmax(0,1fr))}
    .cols-3{grid-template-columns:repeat(3,minmax(0,1fr))}
    @media (max-width: 900px){ .cols-2,.cols-3{grid-template-columns:1fr} .hero h1{font-size:40px} }

    .card{background:var(--card); border:1px solid var(--line); border-radius:var(--radius); padding:18px; box-shadow:var(--shadow)}
    .item{display:flex; gap:14px}
    .logoimg{width:56px; height:56px; border-radius:12px; background:#f5f5f5; border:1px solid var(--line); object-fit:cover}
    .meta{color:var(--muted); font-size:14px}
    .tags{margin-top:6px; display:flex; gap:8px; flex-wrap:wrap}
    .tag{border:1px solid var(--line); padding:6px 10px; border-radius:999px; font-size:12px; background:#f7f7f8}

    /* Gallery */
    .gallery{display:grid; grid-template-columns:repeat(3,1fr); gap:12px}
    .gallery figure{border-radius:16px; overflow:hidden; border:1px solid var(--line); background:#f7f7f8; height:240px; margin:0}
    .gallery img{width:100%; height:100%; object-fit:cover}

    /* Footer */
    footer{padding:40px 0 64px; color:#8a8f98; text-align:center; border-top:1px solid var(--line)}
  </style>
</head>
<body>
  <!-- ===== HEADER ===== -->
  <header class="topbar" id="topbar">
    <div class="wrap">
      <div class="logo" aria-hidden="true">DL</div>
      <div class="name">Daniel Liu</div>
      <nav class="nav" aria-label="Primary">
        <div class="item">
          <a class="link" href="#home" data-tab-link="home">Home</a>
        </div>
        <div class="item">
          <a class="link" href="#experiences" data-tab-link="experiences">Professional</a>
          <div class="dropdown">
            <a href="#experiences" data-tab-link="experiences">Internships</a>
            <a href="#experiences" data-tab-link="experiences">Research</a>
            <a href="#experiences" data-tab-link="experiences">Leadership</a>
          </div>
        </div>
        <div class="item"><a class="link" href="#extracurriculars" data-tab-link="extracurriculars">Extracurriculars</a></div>
        <div class="item"><a class="link" href="#education" data-tab-link="education">Education</a></div>
        <div class="item"><a class="link" href="#hobbies" data-tab-link="hobbies">Hobbies</a></div>
        <div class="item"><a class="link" href="#contact" data-tab-link="contact">Contact</a></div>
      </nav>
    </div>
  </header>

  <!-- ===== HERO ===== -->
  <section id="home" role="tabpanel" class="active hero">
    <figure><img src="images/hero-placeholder.jpg" alt="Cover image placeholder"></figure>
    <div class="inner">
      <h1>Policy & Space Governance<br/>with a builder mindset.</h1>
      <p>Research assistant at The Ostrom Workshop • B.S. Public Affairs (Law & Public Policy), Indiana University.</p>
      <div class="cta">
        <a class="btn primary" href="#experiences" data-tab-link="experiences">See Professional Work</a>
        <a class="btn ghost" href="#contact" data-tab-link="contact">Get in Touch</a>
      </div>
    </div>
  </section>

  <!-- ===== FEATURED STRIP ===== -->
  <main class="wrap-main">
    <section id="gallery" class="section" role="tabpanel">
      <h2>Featured snapshots</h2>
      <p class="lead">Paste large photos or organization logos below.</p>
      <div class="gallery">
        <figure><img src="images/placeholder-1.jpg" alt="Placeholder 1"></figure>
        <figure><img src="images/placeholder-2.jpg" alt="Placeholder 2"></figure>
        <figure><img src="images/placeholder-3.jpg" alt="Placeholder 3"></figure>
      </div>
    </section>
  </main>

  <!-- ===== MAIN SECTIONS (updated info kept) ===== -->
  <main class="wrap-main">
    <!-- PROFESSIONAL -->
    <section id="experiences" role="tabpanel" class="section">
      <h2>Professional</h2>
      <p class="lead">Internships, research, and leadership with clear, outcome-oriented impact.</p>
      <div class="grid cols-2">
        <article class="card item">
          <img class="logoimg" src="images/logos/ahs.png" alt="AHS">
          <div>
            <h3 style="margin:0 0 6px">Executive Board Member — Alexander Hamilton Society at Indiana University</h3>
            <div class="meta">May 2025 — Present · Bloomington, IN (hybrid)</div>
            <p>Lead programming on foreign policy and national security. Built partnerships with campus orgs and D.C. think-tank speakers; coordinated budgets, logistics, and marketing.</p>
            <div class="tags"><span class="tag">Leadership</span><span class="tag">Programming</span><span class="tag">Event Ops</span></div>
          </div>
        </article>

        <article class="card item">
          <img class="logoimg" src="images/logos/ostrom-workshop.png" alt="Ostrom Workshop logo">
          <div>
            <h3 style="margin:0 0 6px">Research Assistant — The Ostrom Workshop (Space Governance Lab)</h3>
            <div class="meta">Oct 2024 — Present · Remote / Bloomington, IN</div>
            <p>Assessed risks to commercial space (electronic warfare & cybersecurity), synthesized interview insights with industry leaders, and drafted policy memos for governance recommendations.</p>
            <div class="tags"><span class="tag">Cybersecurity</span><span class="tag">Space Policy</span><span class="tag">Qualitative Research</span></div>
          </div>
        </article>

        <article class="card item">
          <img class="logoimg" src="images/logos/us-senate.png" alt="US Senate">
          <div>
            <h3 style="margin:0 0 6px">Congressional Intern — United States Senate</h3>
            <div class="meta">Jun 2024 — Aug 2024 · Washington, D.C.</div>
            <p>Supported constituent services, hearing prep, and research across State, DoD, Homeland Security, and Veterans Affairs. Drafted policy briefs and memos used in member meetings.</p>
            <div class="tags"><span class="tag">Legislative Research</span><span class="tag">Constituent Services</span><span class="tag">Briefing</span></div>
          </div>
        </article>

        <article class="card item">
          <img class="logoimg" src="images/logos/iurepublicans.png" alt="IU College Republicans">
          <div>
            <h3 style="margin:0 0 6px">Secretary — Indiana University College Republicans</h3>
            <div class="meta">2023 — 2024 · Bloomington, IN (hybrid)</div>
            <p>Coordinated meetings and speaker logistics, wrote minutes, and maintained good-standing compliance and documentation.</p>
            <div class="tags"><span class="tag">Operations</span><span class="tag">Comms</span></div>
          </div>
        </article>

        <article class="card item">
          <img class="logoimg" src="images/logos/insurance.png" alt="Brotherhood Mutual">
          <div>
            <h3 style="margin:0 0 6px">Legal Intern — Brotherhood Mutual Insurance Company</h3>
            <div class="meta">May 2023 — Aug 2023 · Fort Wayne, IN (hybrid)</div>
            <p>Drafted executive summaries on A/R and VPN policies, created casefile templates, and digitized legal records; collaborated with counsel on contracts and funding documents.</p>
            <div class="tags"><span class="tag">Legal Writing</span><span class="tag">Compliance</span><span class="tag">Process</span></div>
          </div>
        </article>
      </div>
    </section>

    <!-- EXTRACURRICULARS -->
    <section id="extracurriculars" role="tabpanel" class="section">
      <h2>Extracurriculars</h2>
      <p class="lead">Leadership, community, and music.</p>
      <div class="grid cols-2">
        <article class="card item">
          <img class="logoimg" src="images/logos/ahs.png" alt="AHS">
          <div>
            <h3 style="margin:0 0 6px">Alexander Hamilton Society at IU — Executive Board</h3>
            <div class="meta">2025 — Present</div>
            <p>Plan debates and speaker series on national security and U.S.–China relations; manage event ops and student engagement.</p>
          </div>
        </article>
        <article class="card item">
          <img class="logoimg" src="images/logos/iucis.png" alt="IUCIS">
          <div>
            <h3 style="margin:0 0 6px">IU Chinese Students & Scholars Association — Member</h3>
            <div class="meta">2023 — Present</div>
            <p>Cross-cultural programming and community support.</p>
          </div>
        </article>
      </div>
    </section>

    <!-- EDUCATION -->
    <section id="education" role="tabpanel" class="section">
      <h2>Education</h2>
      <p class="lead">Indiana University coursework, awards, and programs.</p>
      <div class="grid cols-2">
        <article class="card item">
          <img class="logoimg" src="images/logos/iu.png" alt="IU logo">
          <div>
            <h3 style="margin:0 0 6px">Indiana University Bloomington — O’Neill School of Public & Environmental Affairs</h3>
            <div class="meta">B.S. Public Affairs (Law & Public Policy), 2023–2027</div>
            <p>Activities: Alexander Hamilton Society (Executive Board); Paul H. O’Neill Crisis Simulation; Research Assistant (Ostrom Workshop).</p>
            <div class="tags"><span class="tag">Chinese Politics</span><span class="tag">Law & Authoritarianism</span><span class="tag">Research Methods</span></div>
          </div>
        </article>

        <article class="card item">
          <img class="logoimg" src="images/logos/award.png" alt="award icon">
          <div>
            <h3 style="margin:0 0 6px">Honors & Programs</h3>
            <div class="meta">Selected</div>
            <ul style="margin:8px 0 0 18px; color:#4b4b4b; line-height:1.6">
              <li>Washington Leadership Program (2024 cohort).</li>
              <li>2023 Fort Wayne Philharmonic Youth Symphony Concerto Competition — performed Tchaikovsky Piano Concerto No.1, Mvt. 3.</li>
              <li>Work & Study in Washington, D.C. (O’Neill School).</li>
            </ul>
          </div>
        </article>
      </div>

      <div class="grid cols-2" style="margin-top:16px">
        <article class="card">
          <h3 style="margin:0 0 6px">Licenses & Certifications</h3>
          <p class="meta">Level 1 Certificate Advancement Program — American String Teachers Association (ASTA)</p>
        </article>
        <article class="card">
          <h3 style="margin:0 0 6px">Languages</h3>
          <p>English (native) · Chinese (basic) · German (basic)</p>
        </article>
      </div>
    </section>

    <!-- HOBBIES / PERSONAL -->
    <section id="hobbies" role="tabpanel" class="section">
      <h2>Hobbies</h2>
      <p class="lead">Music, languages, and the outdoors.</p>
      <div class="grid cols-3">
        <article class="card">
          <h3 style="margin:0 0 6px">Classical Piano</h3>
          <p>Active in the IU music scene; fond of Rachmaninoff & Tchaikovsky. Open to chamber collaborations.</p>
        </article>
        <article class="card">
          <h3 style="margin:0 0 6px">Languages</h3>
          <p>English • Chinese (basic) • German (basic). Always learning.</p>
        </article>
        <article class="card">
          <h3 style="margin:0 0 6px">Outdoors</h3>
          <p>Hiking & landscape photography; chasing sunrise trails.</p>
        </article>
      </div>
    </section>

    <!-- CONTACT -->
    <section id="contact" role="tabpanel" class="section">
      <h2>Contact</h2>
      <p class="lead">Let’s connect.</p>
      <div class="grid cols-2">
        <article class="card">
          <h3 style="margin:0 0 6px">Email</h3>
          <p><a href="mailto:daniel@example.com">daniel@example.com</a></p>
          <p class="meta">Prefer concise, actionable notes.</p>
        </article>
        <article class="card">
          <h3 style="margin:0 0 6px">Profiles</h3>
          <p>LinkedIn, Google Scholar, and GitHub links can go here.</p>
        </article>
      </div>
    </section>
  </main>

  <footer>
    © <span id="yr"></span> Daniel Liu. All rights reserved.
  </footer>

  <script>
    // Tabs
    const panels = document.querySelectorAll('section[role="tabpanel"]');
    function showPanel(id){ panels.forEach(p=>p.classList.toggle('active', p.id===id)); if(id) location.hash=id; }
    document.querySelectorAll('[data-tab-link]').forEach(a=>a.addEventListener('click',e=>{e.preventDefault(); showPanel(a.dataset.tabLink);}));
    const start = location.hash.replace('#',''); if(start) showPanel(start);
  </script>
</body>
</html>
