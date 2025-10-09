<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Daniel Liu</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', 'Segoe UI', Roboto, sans-serif;
            -webkit-font-smoothing: antialiased;
            background: #000;
            color: #f5f5f7;
            overflow-x: hidden;
        }

        .nav {
            position: fixed;
            top: 0;
            width: 100%;
            height: 44px;
            background: rgba(0, 0, 0, 0.8);
            backdrop-filter: saturate(180%) blur(20px);
            z-index: 9999;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .nav-content {
            max-width: 1000px;
            margin: 0 auto;
            height: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 22px;
        }

        .nav-logo {
            font-size: 21px;
            font-weight: 600;
            color: #f5f5f7;
            text-decoration: none;
            letter-spacing: -0.5px;
            cursor: pointer;
        }

        .nav-links {
            display: flex;
            gap: 0;
            list-style: none;
            height: 100%;
            align-items: center;
        }

        .nav-item {
            position: relative;
            height: 100%;
        }

        .nav-link {
            color: #f5f5f7;
            text-decoration: none;
            font-size: 12px;
            font-weight: 400;
            padding: 0 12px;
            height: 100%;
            display: flex;
            align-items: center;
            transition: opacity 0.3s;
            cursor: pointer;
        }

        .nav-link:hover {
            opacity: 0.7;
        }

        .dropdown {
            position: absolute;
            top: 44px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0, 0, 0, 0.92);
            backdrop-filter: saturate(180%) blur(20px);
            min-width: 180px;
            border-radius: 0 0 18px 18px;
            padding: 20px 0;
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.3s, visibility 0.3s;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
        }

        .nav-item:hover .dropdown {
            opacity: 1;
            visibility: visible;
        }

        .dropdown a {
            display: block;
            color: #f5f5f7;
            text-decoration: none;
            padding: 8px 24px;
            font-size: 14px;
            transition: background 0.2s;
        }

        .dropdown a:hover {
            background: rgba(255, 255, 255, 0.08);
        }

        .page {
            display: none;
            min-height: 100vh;
            padding-top: 44px;
        }

        .page.active {
            display: block;
        }

        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
            background: radial-gradient(ellipse at center, #1a1a1a 0%, #000 70%);
            position: relative;
        }

        .hero h1 {
            font-size: 96px;
            font-weight: 700;
            letter-spacing: -3px;
            margin-bottom: 20px;
            background: linear-gradient(90deg, #f5f5f7 0%, #999 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero .tagline {
            font-size: 28px;
            font-weight: 500;
            color: #86868b;
            margin-bottom: 30px;
            letter-spacing: -0.5px;
        }

        .hero .subtitle {
            font-size: 17px;
            color: #86868b;
            max-width: 700px;
            line-height: 1.5;
            margin-bottom: 40px;
        }

        .cta {
            display: flex;
            gap: 20px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .btn-apple {
            padding: 12px 24px;
            border-radius: 980px;
            text-decoration: none;
            font-size: 17px;
            font-weight: 400;
            transition: all 0.3s;
            border: none;
            cursor: pointer;
        }

        .btn-primary {
            background: #0071e3;
            color: #fff;
        }

        .btn-primary:hover {
            background: #0077ed;
        }

        .btn-secondary {
            background: transparent;
            color: #2997ff;
            border: 1px solid #2997ff;
        }

        .btn-secondary:hover {
            background: #2997ff;
            color: #fff;
        }

        .content-section {
            padding: 120px 20px 80px;
            max-width: 1000px;
            margin: 0 auto;
        }

        .section-title {
            font-size: 64px;
            font-weight: 700;
            letter-spacing: -2px;
            margin-bottom: 20px;
        }

        .section-desc {
            font-size: 21px;
            color: #86868b;
            margin-bottom: 60px;
            letter-spacing: -0.5px;
        }

        .card-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            margin-top: 40px;
        }

        .card {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 18px;
            padding: 40px 30px;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            cursor: default;
        }

        .card:hover {
            background: rgba(255, 255, 255, 0.05);
            border-color: rgba(255, 255, 255, 0.2);
            transform: translateY(-8px);
        }

        .card-icon {
            font-size: 48px;
            margin-bottom: 20px;
        }

        .card h3 {
            font-size: 24px;
            font-weight: 600;
            margin-bottom: 12px;
            letter-spacing: -0.5px;
        }

        .card p {
            font-size: 17px;
            color: #86868b;
            line-height: 1.5;
        }

        .timeline {
            position: relative;
            padding-left: 40px;
            margin-top: 60px;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            bottom: 0;
            width: 2px;
            background: linear-gradient(180deg, #2997ff 0%, rgba(41, 151, 255, 0) 100%);
        }

        .timeline-item {
            margin-bottom: 60px;
            position: relative;
        }

        .timeline-item::before {
            content: '';
            position: absolute;
            left: -46px;
            top: 8px;
            width: 12px;
            height: 12px;
            background: #2997ff;
            border-radius: 50%;
            box-shadow: 0 0 0 4px rgba(41, 151, 255, 0.2);
        }

        .timeline-header {
            display: flex;
            justify-content: space-between;
            align-items: start;
            margin-bottom: 12px;
            flex-wrap: wrap;
            gap: 10px;
        }

        .timeline-title {
            font-size: 28px;
            font-weight: 600;
            letter-spacing: -0.5px;
        }

        .timeline-org {
            font-size: 21px;
            color: #2997ff;
            margin-bottom: 4px;
        }

        .timeline-date {
            font-size: 15px;
            color: #86868b;
        }

        .timeline-desc {
            font-size: 17px;
            color: #86868b;
            line-height: 1.6;
        }

        .research-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 30px;
            margin-top: 60px;
        }

        .research-card {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 18px;
            padding: 40px;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
        }

        .research-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, #2997ff, #0071e3);
            transform: scaleX(0);
            transition: transform 0.4s;
        }

        .research-card:hover::before {
            transform: scaleX(1);
        }

        .research-card:hover {
            background: rgba(255, 255, 255, 0.05);
            transform: translateY(-8px);
        }

        .research-tag {
            display: inline-block;
            padding: 6px 14px;
            background: rgba(41, 151, 255, 0.15);
            color: #2997ff;
            border-radius: 980px;
            font-size: 13px;
            font-weight: 500;
            margin-bottom: 20px;
        }

        .research-card h3 {
            font-size: 24px;
            font-weight: 600;
            margin-bottom: 16px;
            letter-spacing: -0.5px;
        }

        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 60px;
        }

        .contact-card {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 18px;
            padding: 40px;
            text-align: center;
            transition: all 0.3s;
            text-decoration: none;
            color: inherit;
            display: block;
        }

        .contact-card:hover {
            background: rgba(255, 255, 255, 0.05);
            transform: translateY(-8px);
        }

        .contact-icon {
            font-size: 48px;
            margin-bottom: 20px;
        }

        .contact-card h3 {
            font-size: 24px;
            margin-bottom: 12px;
        }

        .contact-card p {
            color: #86868b;
            font-size: 17px;
        }

        .scroll-hint {
            position: absolute;
            bottom: 40px;
            left: 50%;
            transform: translateX(-50%);
            width: 24px;
            height: 36px;
            border: 2px solid rgba(255, 255, 255, 0.3);
            border-radius: 12px;
            display: flex;
            justify-content: center;
            padding-top: 6px;
        }

        .scroll-hint::before {
            content: '';
            width: 4px;
            height: 8px;
            background: rgba(255, 255, 255, 0.5);
            border-radius: 2px;
            animation: scroll 2s infinite;
        }

        @keyframes scroll {
            0% { opacity: 1; transform: translateY(0); }
            100% { opacity: 0; transform: translateY(16px); }
        }

        @media (max-width: 768px) {
            .hero h1 {
                font-size: 56px;
            }

            .hero .tagline {
                font-size: 21px;
            }

            .section-title {
                font-size: 40px;
            }

            .section-desc {
                font-size: 17px;
            }

            .nav-links {
                gap: 0;
                font-size: 11px;
            }

            .nav-link {
                padding: 0 8px;
            }

            .timeline {
                padding-left: 30px;
            }

            .timeline-title {
                font-size: 21px;
            }
        }
    </style>
</head>
<body>
    <nav class="nav">
        <div class="nav-content">
            <a class="nav-logo" onclick="showPage('home')">Daniel Liu</a>
            <ul class="nav-links">
                <li class="nav-item">
                    <div class="nav-link">About</div>
                    <div class="dropdown">
                        <a onclick="showPage('about')">Overview</a>
                        <a onclick="showPage('research-focus')">Research Focus</a>
                    </div>
                </li>
                <li class="nav-item">
                    <div class="nav-link">Research</div>
                    <div class="dropdown">
                        <a onclick="showPage('publications')">Publications</a>
                        <a onclick="showPage('projects')">Projects</a>
                    </div>
                </li>
                <li class="nav-item">
                    <div class="nav-link">Experience</div>
                    <div class="dropdown">
                        <a onclick="showPage('experience')">Professional</a>
                        <a onclick="showPage('leadership')">Leadership</a>
                    </div>
                </li>
                <li class="nav-item">
                    <div class="nav-link">Education</div>
                    <div class="dropdown">
                        <a onclick="showPage('education')">Academic</a>
                    </div>
                </li>
                <li class="nav-item">
                    <a class="nav-link" onclick="showPage('contact')">Contact</a>
                </li>
            </ul>
        </div>
    </nav>

    <!-- HOME PAGE -->
    <div id="home" class="page active">
        <section class="hero">
            <h1>Daniel Liu</h1>
            <div class="tagline">Research. Policy. Innovation.</div>
            <p class="subtitle">
                Advancing national security through research in space governance, Chinese strategy, and international policy at Indiana University and The Ostrom Workshop.
            </p>
            <div class="cta">
                <a class="btn-apple btn-primary" onclick="showPage('publications')">View Research</a>
                <a class="btn-apple btn-secondary" onclick="showPage('contact')">Get in Touch</a>
            </div>
            <div class="scroll-hint"></div>
        </section>
    </div>

    <!-- ABOUT PAGE -->
    <div id="about" class="page">
        <div class="content-section">
            <h2 class="section-title">About</h2>
            <p class="section-desc">Pursuing a Bachelor of Science in Public Affairs at Indiana University, majoring in Law and Public Policy with a minor in International Relations. My academic and professional interests focus on U.S. foreign policy, national security, and Mainland Chinese domestic policy through their impact on global security and relations.</p>
            <p class="section-desc">With firsthand experience in Taiwan and Mainland China, I bring a practical understanding of the region's political and security challenges. I am committed to research that strengthens U.S. grand defense strategy and alliances, advocating for the international recognition of the Republic of China on Taiwan, and promoting democratic resiliency in the Indo-Pacific.</p>
        </div>
    </div>

    <!-- RESEARCH FOCUS PAGE -->
    <div id="research-focus" class="page">
        <div class="content-section">
            <h2 class="section-title">Research Focus</h2>
            <p class="section-desc">Exploring critical intersections of security, governance, and international relations</p>
            
            <div class="card-grid">
                <div class="card">
                    <div class="card-icon">🛡️</div>
                    <h3>National Security</h3>
                    <p>U.S. grand defense strategy and alliance strengthening in the Indo-Pacific region</p>
                </div>
                <div class="card">
                    <div class="card-icon">🚀</div>
                    <h3>Space Governance</h3>
                    <p>International frameworks and strategic risk management in commercial space operations</p>
                </div>
                <div class="card">
                    <div class="card-icon">🌏</div>
                    <h3>Indo-Pacific Policy</h3>
                    <p>Chinese grand strategy, PLA doctrine, and democratic resiliency</p>
                </div>
                <div class="card">
                    <div class="card-icon">⚖️</div>
                    <h3>International Law</h3>
                    <p>Space law and global governance frameworks</p>
                </div>
            </div>
        </div>
    </div>

    <!-- PUBLICATIONS PAGE -->
    <div id="publications" class="page">
        <div class="content-section">
            <h2 class="section-title">Publications</h2>
            <p class="section-desc">Contributing to critical discussions in space governance and national security</p>
            
            <div class="research-grid">
                <div class="research-card">
                    <span class="research-tag">Space Governance</span>
                    <h3>Managing Strategic Risk as A Commercial Space Company</h3>
                    <p>Examining the intersection of private-public sector cooperation in space, strategic risk assessment, and governance frameworks for commercial space operations.</p>
                </div>
                
                <div class="research-card">
                    <span class="research-tag">Chinese Strategy</span>
                    <h3>Chinese Grand Strategy in Space</h3>
                    <p>Comprehensive analysis of PLA doctrine, space capabilities, and strategic objectives in the context of international security and competition.</p>
                </div>
                
                <div class="research-card">
                    <span class="research-tag">Policy Research</span>
                    <h3>Cyberspace Insurance Development</h3>
                    <p>Research on emerging frameworks for cyber insurance in the context of space operations and international governance structures.</p>
                </div>
            </div>
        </div>
    </div>

    <!-- PROJECTS PAGE -->
    <div id="projects" class="page">
        <div class="content-section">
            <h2 class="section-title">Current Projects</h2>
            <p class="section-desc">Active research initiatives and collaborations</p>
            
            <div class="research-grid">
                <div class="research-card">
                    <span class="research-tag">Collaboration</span>
                    <h3>DoD Air Force Partnership</h3>
                    <p>Contributing to the 2025 launch event of the Space Governance Lab and Department of the Air Force collaboration, including material preparation and research support.</p>
                </div>
                
                <div class="research-card">
                    <span class="research-tag">Policy Analysis</span>
                    <h3>International Space Law Research</h3>
                    <p>Conducting comprehensive research on international cooperation and governance frameworks in space operations.</p>
                </div>
            </div>
        </div>
    </div>

    <!-- EXPERIENCE PAGE -->
    <div id="experience" class="page">
        <div class="content-section">
            <h2 class="section-title">Professional Experience</h2>
            <p class="section-desc">Building expertise through research, policy, and public service</p>
            
            <div class="timeline">
                <div class="timeline-item">
                    <div class="timeline-header">
                        <div>
                            <div class="timeline-org">The Ostrom Workshop</div>
                            <div class="timeline-title">Research Assistant</div>
                        </div>
                        <div class="timeline-date">Mar 2025 - Present</div>
                    </div>
                    <p class="timeline-desc">
                        Working with Research Professor Eytan Tepper on space law, Chinese grand strategy in space, PLA doctrine, international cooperation frameworks, and private-public sector cooperation. Contributed to DoD Air Force collaboration and conference materials.
                    </p>
                </div>

                <div class="timeline-item">
                    <div class="timeline-header">
                        <div>
                            <div class="timeline-org">United States Senate</div>
                            <div class="timeline-title">Congressional Intern</div>
                        </div>
                        <div class="timeline-date">May 2025 - Aug 2025</div>
                    </div>
                    <p class="timeline-desc">
                        Supported constituent services with federal agency casework. Represented Senator Jim Banks at official events. Assisted in House-to-Senate transition operations and infrastructure setup.
                    </p>
                </div>

                <div class="timeline-item">
                    <div class="timeline-header">
                        <div>
                            <div class="timeline-org">Brotherhood Mutual Insurance</div>
                            <div class="timeline-title">Legal Intern</div>
                        </div>
                        <div class="timeline-date">May 2024 - Aug 2024</div>
                    </div>
                    <p class="timeline-desc">
                        Conducted legal research on reinsurance contracts with corporate attorneys. Attended executive meetings and drafted summaries. Digitized legal records and founding documents.
                    </p>
                </div>
            </div>
        </div>
    </div>

    <!-- LEADERSHIP PAGE -->
    <div id="leadership" class="page">
        <div class="content-section">
            <h2 class="section-title">Leadership</h2>
            <p class="section-desc">Student organizations and community engagement</p>
            
            <div class="timeline">
                <div class="timeline-item">
                    <div class="timeline-header">
                        <div>
                            <div class="timeline-org">Alexander Hamilton Society</div>
                            <div class="timeline-title">Executive Board Member</div>
                        </div>
                        <div class="timeline-date">May 2025 - Present</div>
                    </div>
                    <p class="timeline-desc">
                        Operations team handling event coordination, speaker logistics, and weekly materials with focus on East Asian developments. Planning the Paul H O'Neill Crisis Simulation.
                    </p>
                </div>

                <div class="timeline-item">
                    <div class="timeline-header">
                        <div>
                            <div class="timeline-org">IUCRs</div>
                            <div class="timeline-title">Secretary</div>
                        </div>
                        <div class="timeline-date">Jan 2025 - Present</div>
                    </div>
                    <p class="timeline-desc">
                        Managing organizational communications and administrative operations for Indiana University's College Republicans chapter.
                    </p>
                </div>
            </div>
        </div>
    </div>

    <!-- EDUCATION PAGE -->
    <div id="education" class="page">
        <div class="content-section">
            <h2 class="section-title">Education</h2>
            <p class="section-desc">Building a foundation in law, policy, and international relations</p>
            
            <div class="timeline">
                <div class="timeline-item">
                    <div class="timeline-header">
                        <div>
                            <div class="timeline-org">Indiana University</div>
                            <div class="timeline-title">Bachelor of Science in Public Affairs</div>
                        </div>
                        <div class="timeline-date">Aug 2024 - May 2027</div>
                    </div>
                    <p class="timeline-desc">
                        O'Neill School of Public and Environmental Affairs<br>
                        Major: Law and Public Policy | Minor: International Relations<br><br>
                        <strong>Relevant Coursework:</strong><br>
                        • Chinese Politics (POLS-Y 333)<br>
                        • Law & Authoritarianism - China (INTL-L 351)<br><br>
                        <strong>Honors & Programs:</strong><br>
                        • Washington Leadership Program (Spring 2026)<br>
                        • Paul H O'Neill Crisis Simulation<br>
                        • Research Assistant
                    </p>
                </div>
            </div>
        </div>
    </div>

    <!-- CONTACT PAGE -->
    <div id="contact" class="page">
        <div class="content-section">
            <h2 class="section-title">Let's Connect</h2>
            <p class="section-desc">
                Interested in collaboration, research opportunities, or discussing national security and space governance?
            </p>
            
            <div class="contact-grid">
                <a href="https://www.linkedin.com/in/danyliu/" target="_blank" class="contact-card">
                    <div class="contact-icon">💼</div>
                    <h3>LinkedIn</h3>
                    <p>Professional network</p>
                </a>
                
                <a href="mailto:your.email@example.com" class="contact-card">
                    <div class="contact-icon">✉️</div>
                    <h3>Email</h3>
                    <p>Direct contact</p>
                </a>
                
                <div class="contact-card" style="cursor: default;">
                    <div class="contact-icon">📍</div>
                    <h3>Location</h3>
                    <p>Bloomington, Indiana</p>
                </div>
            </div>
        </div>
    </div>

    <script>
        function showPage(pageId) {
            const pages = document.querySelectorAll('.page');
            pages.forEach(page => page.classList.remove('active'));
            
            const targetPage = document.getElementById(pageId);
            if (targetPage) {
                targetPage.classList.add('active');
                window.scrollTo(0, 0);
            }
        }
    </script>
</body>
</html>
