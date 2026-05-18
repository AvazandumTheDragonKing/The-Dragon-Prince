<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>The Dragon Prince — A Fan's Guide</title>
        <link rel="preconnect" href="https://fonts.googleapis.com" />
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
        <link
            href="https://fonts.googleapis.com/css2?family=Cinzel+Decorative:wght@400;700;900&family=Crimson+Pro:ital,wght@0,300;0,400;0,600;1,300;1,400&display=swap"
            rel="stylesheet"
        />
        <style>
            /* ═══════════════════════════════
               ROOT VARIABLES
            ═══════════════════════════════ */
            :root {
                --void:       #06080f;
                --deep-night: #0c1220;
                --midnight:   #111827;
                --moon:       #e8e0d0;
                --parchment:  #f0e9d8;
                --gold:       #c9953a;
                --gold-light: #f0c060;
                --dragon-red: #c0392b;
                --sky:        #4a9cc9;
                --sky-pale:   #a8d4e8;
            }

            /* ═══════════════════════════════
               RESET & BASE
            ═══════════════════════════════ */
            *, *::before, *::after {
                box-sizing: border-box;
                margin: 0;
                padding: 0;
            }

            html { scroll-behavior: smooth; }

            body {
                background-color: var(--void);
                color: var(--moon);
                font-family: 'Crimson Pro', Georgia, serif;
                font-size: 18px;
                line-height: 1.75;
                overflow-x: hidden;
            }

            /* Star-field background */
            body::before {
                content: '';
                position: fixed;
                inset: 0;
                background-image:
                    radial-gradient(1px 1px at 15% 20%, rgba(255,255,255,0.8) 0%, transparent 100%),
                    radial-gradient(1px 1px at 40% 55%, rgba(255,255,255,0.5) 0%, transparent 100%),
                    radial-gradient(1.5px 1.5px at 70% 10%, rgba(255,255,255,0.7) 0%, transparent 100%),
                    radial-gradient(1px 1px at 85% 40%, rgba(255,255,255,0.6) 0%, transparent 100%),
                    radial-gradient(1px 1px at 25% 75%, rgba(255,255,255,0.4) 0%, transparent 100%),
                    radial-gradient(1px 1px at 60% 85%, rgba(255,255,255,0.5) 0%, transparent 100%),
                    radial-gradient(1.5px 1.5px at 90% 65%, rgba(255,255,255,0.6) 0%, transparent 100%),
                    radial-gradient(1px 1px at 5%  50%, rgba(255,255,255,0.4) 0%, transparent 100%),
                    radial-gradient(2px 2px at 33% 90%, rgba(201,149,58,0.4) 0%, transparent 100%),
                    radial-gradient(1.5px 1.5px at 77% 78%, rgba(74,156,201,0.4) 0%, transparent 100%);
                pointer-events: none;
                z-index: 0;
                animation: twinkle 8s ease-in-out infinite alternate;
            }

            @keyframes twinkle {
                0%   { opacity: 0.6; }
                50%  { opacity: 1;   }
                100% { opacity: 0.7; }
            }

            /* Ambient glow */
            body::after {
                content: '';
                position: fixed;
                top: -20%;
                left: 50%;
                transform: translateX(-50%);
                width: 80vw;
                height: 60vh;
                background: radial-gradient(ellipse,
                    rgba(74,156,201,0.08) 0%,
                    rgba(201,149,58,0.05) 40%,
                    transparent 70%
                );
                pointer-events: none;
                z-index: 0;
            }

            /* ═══════════════════════════════
               NAVIGATION
            ═══════════════════════════════ */
            nav {
                position: sticky;
                top: 0;
                z-index: 200;
                display: flex;
                justify-content: space-between;
                align-items: center;
                padding: 1rem 4rem;
                background: rgba(6,8,15,0.88);
                backdrop-filter: blur(12px);
                border-bottom: 1px solid rgba(201,149,58,0.25);
            }

            .nav-brand {
                font-family: 'Cinzel Decorative', serif;
                font-size: 0.85rem;
                color: var(--gold);
                text-decoration: none;
                letter-spacing: 0.08em;
            }

            nav ul {
                list-style: none;
                display: flex;
                gap: 2.5rem;
            }

            nav ul li a {
                font-family: 'Crimson Pro', serif;
                font-size: 0.95rem;
                letter-spacing: 0.1em;
                text-transform: uppercase;
                color: var(--moon);
                text-decoration: none;
                opacity: 0.8;
                transition: color 0.25s, opacity 0.25s;
            }

            nav ul li a:hover {
                color: var(--gold-light);
                opacity: 1;
            }

            /* ═══════════════════════════════
               HERO
            ═══════════════════════════════ */
            header.hero {
                position: relative;
                z-index: 1;
                min-height: 95vh;
                display: flex;
                flex-direction: column;
                justify-content: center;
                align-items: center;
                text-align: center;
                padding: 6rem 2rem 4rem;
                overflow: hidden;
            }

            .hero-rune-circle {
                position: absolute;
                width: min(650px, 90vw);
                height: min(650px, 90vw);
                border-radius: 50%;
                border: 1px solid rgba(201,149,58,0.12);
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%);
                animation: rotateSlow 60s linear infinite;
                pointer-events: none;
            }

            .hero-rune-circle::before {
                content: '';
                position: absolute;
                inset: 20px;
                border-radius: 50%;
                border: 1px dashed rgba(74,156,201,0.1);
                animation: rotateSlow 40s linear infinite reverse;
            }

            @keyframes rotateSlow {
                from { transform: translate(-50%, -50%) rotate(0deg); }
                to   { transform: translate(-50%, -50%) rotate(360deg); }
            }

            .hero-eyebrow {
                font-size: 0.82rem;
                letter-spacing: 0.35em;
                text-transform: uppercase;
                color: var(--sky);
                margin-bottom: 1.5rem;
                animation: fadeDown 0.8s ease both;
            }

            h1 {
                font-family: 'Cinzel Decorative', serif;
                font-size: clamp(2.4rem, 7vw, 6rem);
                line-height: 1.1;
                margin-bottom: 0.4rem;
                color: var(--parchment);
                text-shadow:
                    0 0 60px rgba(201,149,58,0.4),
                    0 0 120px rgba(74,156,201,0.15);
                animation: fadeDown 0.8s 0.1s ease both;
            }

            .hero-subtitle-title {
                font-family: 'Cinzel Decorative', serif;
                font-size: clamp(1rem, 3vw, 2.2rem);
                color: var(--gold);
                margin-bottom: 2rem;
                letter-spacing: 0.12em;
                animation: fadeDown 0.8s 0.2s ease both;
            }

            .hero-desc {
                font-size: 1.15rem;
                max-width: 52ch;
                color: rgba(232,224,208,0.75);
                font-style: italic;
                margin-bottom: 3rem;
                animation: fadeDown 0.8s 0.3s ease both;
            }

            .hero-badges {
                display: flex;
                gap: 1rem;
                flex-wrap: wrap;
                justify-content: center;
                margin-bottom: 3.5rem;
                animation: fadeDown 0.8s 0.4s ease both;
            }

            .badge {
                border: 1px solid rgba(201,149,58,0.4);
                padding: 0.4rem 1rem;
                font-size: 0.78rem;
                letter-spacing: 0.15em;
                text-transform: uppercase;
                color: var(--gold);
                background: rgba(201,149,58,0.06);
            }

            .hero-image {
                position: relative;
                width: min(480px, 88vw);
                border: 1px solid rgba(201,149,58,0.3);
                overflow: hidden;
                animation: fadeDown 0.8s 0.5s ease both;
                box-shadow:
                    0 0 40px rgba(74,156,201,0.15),
                    0 0 80px rgba(201,149,58,0.08),
                    inset 0 0 30px rgba(0,0,0,0.5);
            }

            .hero-image img {
                width: 100%;
                display: block;
                filter: contrast(1.05) saturate(0.9);
                transition: transform 5s ease;
            }

            .hero-image:hover img { transform: scale(1.04); }

            .hero-image-caption {
                position: absolute;
                bottom: 0;
                left: 0;
                right: 0;
                padding: 2rem 1.5rem 1rem;
                background: linear-gradient(transparent, rgba(6,8,15,0.9));
                font-size: 0.72rem;
                letter-spacing: 0.18em;
                text-transform: uppercase;
                color: var(--gold);
                text-align: center;
            }

            @keyframes fadeDown {
                from { opacity: 0; transform: translateY(-16px); }
                to   { opacity: 1; transform: translateY(0); }
            }

            /* ═══════════════════════════════
               DIVIDER
            ═══════════════════════════════ */
            .rune-divider {
                position: relative;
                z-index: 1;
                text-align: center;
                display: flex;
                align-items: center;
                gap: 1.5rem;
                margin: 0 4rem;
                opacity: 0.45;
            }

            .rune-divider::before,
            .rune-divider::after {
                content: '';
                flex: 1;
                height: 1px;
                background: linear-gradient(90deg, transparent, var(--gold), transparent);
            }

            .rune-divider span {
                font-size: 1.2rem;
                color: var(--gold);
            }

            /* ═══════════════════════════════
               SECTIONS (shared)
            ═══════════════════════════════ */
            section {
                position: relative;
                z-index: 1;
                padding: 5rem 4rem;
            }

            .section-tag {
                font-size: 0.7rem;
                letter-spacing: 0.3em;
                text-transform: uppercase;
                color: var(--sky);
                margin-bottom: 1rem;
                display: block;
            }

            h2 {
                font-family: 'Cinzel Decorative', serif;
                font-size: clamp(1.5rem, 3.5vw, 2.6rem);
                color: var(--parchment);
                line-height: 1.2;
                margin-bottom: 1.8rem;
                text-shadow: 0 0 40px rgba(201,149,58,0.2);
            }

            h3 {
                font-family: 'Cinzel Decorative', serif;
                font-size: 1.05rem;
                color: var(--gold-light);
                margin-bottom: 0.8rem;
                letter-spacing: 0.05em;
            }

            p {
                color: rgba(232,224,208,0.82);
                max-width: 70ch;
                margin-bottom: 1.2rem;
            }

            strong { color: var(--gold-light); font-weight: 600; }
            em     { color: var(--sky-pale);   font-style: italic; }

            /* ═══════════════════════════════
               ABOUT / LORE (two-col)
            ═══════════════════════════════ */
            #about {
                display: grid;
                grid-template-columns: 55% 45%;
                gap: 0;
                border-top: 1px solid rgba(201,149,58,0.15);
            }

            #about .about-left {
                padding-right: 4rem;
                border-right: 1px solid rgba(201,149,58,0.15);
            }

            #about .about-right { padding-left: 4rem; }

            .lore-box {
                background: rgba(201,149,58,0.05);
                border: 1px solid rgba(201,149,58,0.2);
                border-left: 3px solid var(--gold);
                padding: 1.5rem 1.8rem;
                margin: 2rem 0;
                font-style: italic;
                font-size: 1.05rem;
                color: rgba(232,224,208,0.7);
            }

            /* ═══════════════════════════════
               CHARACTERS
            ═══════════════════════════════ */
            #characters {
                border-top: 1px solid rgba(201,149,58,0.15);
                background: linear-gradient(180deg, transparent, rgba(74,156,201,0.03) 50%, transparent);
            }

            .chars-grid {
                display: grid;
                grid-template-columns: repeat(3, 1fr);
                gap: 1px;
                background: rgba(201,149,58,0.1);
                border: 1px solid rgba(201,149,58,0.15);
                margin-top: 3rem;
            }

            .char-card {
                padding: 2rem 1.8rem;
                background: var(--void);
                transition: background 0.3s;
                position: relative;
                overflow: hidden;
            }

            .char-card::before {
                content: '';
                position: absolute;
                top: 0; left: 0; right: 0;
                height: 2px;
                background: linear-gradient(90deg, transparent, var(--gold), transparent);
                opacity: 0;
                transition: opacity 0.3s;
            }

            .char-card:hover { background: rgba(201,149,58,0.04); }
            .char-card:hover::before { opacity: 1; }

            .char-icon {
                font-size: 2.5rem;
                margin-bottom: 1rem;
                display: block;
            }

            .char-role {
                font-size: 0.68rem;
                letter-spacing: 0.2em;
                text-transform: uppercase;
                color: var(--sky);
                margin-bottom: 0.5rem;
                display: block;
            }

            .char-card p { font-size: 0.9rem; max-width: 100%; margin: 0; }

            /* ═══════════════════════════════
               ARCANUM / MAGIC SYSTEM
            ═══════════════════════════════ */
            #arcanum { border-top: 1px solid rgba(201,149,58,0.15); }

            #arcanum .arcanum-inner {
                display: grid;
                grid-template-columns: 1fr 1fr;
                gap: 5rem;
            }

            /* Ordered list */
            ol {
                list-style: none;
                counter-reset: primal-counter;
                padding: 0;
                margin-top: 1.5rem;
            }

            ol li {
                counter-increment: primal-counter;
                display: flex;
                gap: 1.2rem;
                margin-bottom: 1.1rem;
                font-size: 0.95rem;
                align-items: flex-start;
            }

            ol li::before {
                content: counter(primal-counter);
                font-family: 'Cinzel Decorative', serif;
                font-size: 0.75rem;
                color: var(--gold);
                background: rgba(201,149,58,0.12);
                border: 1px solid rgba(201,149,58,0.3);
                min-width: 2rem;
                height: 2rem;
                display: flex;
                align-items: center;
                justify-content: center;
                flex-shrink: 0;
                margin-top: 0.1rem;
            }

            /* Unordered list */
            ul {
                list-style: none;
                padding: 0;
                margin-top: 1.5rem;
            }

            ul li {
                display: flex;
                gap: 1rem;
                margin-bottom: 0.9rem;
                font-size: 0.95rem;
                align-items: flex-start;
            }

            ul li::before {
                content: '✦';
                color: var(--sky);
                font-size: 0.7rem;
                padding-top: 0.3rem;
                flex-shrink: 0;
            }

            /* ═══════════════════════════════
               SEASONS TIMELINE
            ═══════════════════════════════ */
            #seasons {
                border-top: 1px solid rgba(201,149,58,0.15);
                background: linear-gradient(180deg, transparent, rgba(201,149,58,0.02) 50%, transparent);
            }

            .seasons-track {
                margin-top: 3.5rem;
                position: relative;
                padding-left: 3rem;
            }

            .seasons-track::before {
                content: '';
                position: absolute;
                left: 0;
                top: 0.6rem;
                bottom: 0.6rem;
                width: 1px;
                background: linear-gradient(180deg, transparent, var(--gold) 20%, var(--sky) 80%, transparent);
                opacity: 0.4;
            }

            .season-item {
                position: relative;
                margin-bottom: 3rem;
                padding-left: 1.5rem;
            }

            .season-item::before {
                content: '';
                position: absolute;
                left: -3rem;
                top: 0.55rem;
                width: 0.55rem;
                height: 0.55rem;
                background: var(--gold);
                border-radius: 50%;
                box-shadow: 0 0 8px var(--gold);
            }

            .season-num {
                font-size: 0.68rem;
                letter-spacing: 0.25em;
                text-transform: uppercase;
                color: var(--sky);
                margin-bottom: 0.3rem;
                display: block;
            }

            .season-item h3 { font-size: 1.05rem; }
            .season-item p  { font-size: 0.9rem; margin: 0.4rem 0 0; }

            /* ═══════════════════════════════
               EXPLORE / EXTERNAL LINKS
            ═══════════════════════════════ */
            #explore {
                border-top: 1px solid rgba(201,149,58,0.15);
                text-align: center;
            }

            #explore p {
                max-width: 50ch;
                margin: 0 auto 3rem;
                text-align: center;
            }

            .links-row {
                display: flex;
                gap: 1.5rem;
                flex-wrap: wrap;
                justify-content: center;
            }

            .scroll-link {
                display: inline-flex;
                align-items: center;
                gap: 0.6rem;
                text-decoration: none;
                padding: 0.85rem 2rem;
                font-family: 'Crimson Pro', serif;
                font-size: 0.9rem;
                letter-spacing: 0.12em;
                text-transform: uppercase;
                transition: all 0.25s;
                border: 1px solid rgba(201,149,58,0.4);
                color: var(--gold);
                background: transparent;
            }

            .scroll-link:hover {
                background: rgba(201,149,58,0.12);
                border-color: var(--gold-light);
                color: var(--gold-light);
                box-shadow: 0 0 20px rgba(201,149,58,0.15);
            }

            .scroll-link.primary {
                background: rgba(201,149,58,0.15);
                border-color: var(--gold);
            }

            .scroll-link.sky-variant {
                border-color: rgba(74,156,201,0.4);
                color: var(--sky-pale);
            }

            .scroll-link.sky-variant:hover {
                background: rgba(74,156,201,0.1);
                border-color: var(--sky);
                box-shadow: 0 0 20px rgba(74,156,201,0.15);
            }

            /* ═══════════════════════════════
               FOOTER
            ═══════════════════════════════ */
            footer {
                position: relative;
                z-index: 1;
                padding: 2.5rem 4rem;
                border-top: 1px solid rgba(201,149,58,0.15);
                display: flex;
                justify-content: space-between;
                align-items: center;
                font-size: 0.75rem;
                letter-spacing: 0.12em;
                text-transform: uppercase;
                color: rgba(232,224,208,0.3);
            }

            footer a {
                color: rgba(201,149,58,0.5);
                text-decoration: none;
                transition: color 0.2s;
            }

            footer a:hover { color: var(--gold); }

            /* ═══════════════════════════════
               RESPONSIVE
            ═══════════════════════════════ */
            @media (max-width: 900px) {
                nav { padding: 1rem 1.5rem; }
                nav ul { gap: 1.2rem; }
                nav ul li a { font-size: 0.8rem; letter-spacing: 0.06em; }

                section { padding: 3.5rem 1.5rem; }
                .rune-divider { margin: 0 1.5rem; }

                #about { grid-template-columns: 1fr; }
                #about .about-left {
                    padding-right: 0;
                    border-right: none;
                    border-bottom: 1px solid rgba(201,149,58,0.15);
                    padding-bottom: 2.5rem;
                    margin-bottom: 2.5rem;
                }
                #about .about-right { padding-left: 0; }

                .chars-grid { grid-template-columns: 1fr; }

                #arcanum .arcanum-inner { grid-template-columns: 1fr; gap: 3rem; }

                footer { flex-direction: column; gap: 0.8rem; text-align: center; }
            }
        </style>
    </head>
    <body>

        <!-- ══════════════════════════════
             NAVIGATION
        ══════════════════════════════ -->
        <nav>
            <a href="#" class="nav-brand">The Dragon Prince</a>
            <ul>
                <li><a href="#about">Lore</a></li>
                <li><a href="#characters">Characters</a></li>
                <li><a href="#arcanum">Magic</a></li>
                <li><a href="#seasons">Seasons</a></li>
                <li><a href="#explore">Explore</a></li>
            </ul>
        </nav>

        <!-- ══════════════════════════════
             HERO
        ══════════════════════════════ -->
        <header class="hero">
            <div class="hero-rune-circle"></div>

            <p class="hero-eyebrow">A fan's compendium to</p>

            <h1>The Dragon<br />Prince</h1>

            <p class="hero-subtitle-title">Where Dragons &amp; Magic Unite</p>

            <p class="hero-desc">
                An animated epic of two worlds, ancient magic, and the courage
                it takes to bridge them — one step, one spell, one truth at a time.
            </p>

            <div class="hero-badges">
                <span class="badge">Netflix Original</span>
                <span class="badge">Since 2018</span>
                <span class="badge">7 Seasons</span>
                <span class="badge">Aaron Ehasz &amp; Justin Richmond</span>
            </div>

            <figure class="hero-image">
                <img
                    src="https://upload.wikimedia.org/wikipedia/en/0/09/The_Dragon_Prince_season_1_poster.jpg"
                    alt="Official poster for The Dragon Prince Season 1 — Callum, Ezran, and Rayla stand before a glowing dragon egg"
                    onerror="this.style.display='none';"
                />
                <figcaption class="hero-image-caption">
                    Season 1 · Moon · Netflix · 2018
                </figcaption>
            </figure>
        </header>

        <div class="rune-divider"><span>✦</span></div>

        <!-- ══════════════════════════════
             ABOUT / LORE
        ══════════════════════════════ -->
        <section id="about">
            <div class="about-left">
                <span class="section-tag">The World of Xadia</span>
                <h2>Two Continents,<br />One Cracked World</h2>

                <p>
                    <em>The Dragon Prince</em> is a fantasy animated series set in a world
                    divided into two halves: <strong>Xadia</strong>, a land of ancient magic
                    where elves and dragons dwell, and the <strong>Human Kingdoms</strong>,
                    where humans — cut off from the primal magical sources — turned to
                    <em>dark magic</em>, drawing power from the life force of magical creatures.
                </p>

                <p>
                    The divide began when humans were banished from Xadia for practicing dark
                    magic. A great dragon, <strong>Thunder</strong>, and the Dragon King guarded
                    the border — until humans killed the Dragon King and, believing they had
                    destroyed his heir, the Dragon Prince's egg.
                </p>

                <br />
                <!-- Intentional line break for pacing before the key plot summary -->

                <p>
                    The story follows <strong>Callum</strong>, a human prince and unlikely
                    mage; his younger brother <strong>Ezran</strong>; and a Moonshadow elf
                    assassin named <strong>Rayla</strong> — three unlikely companions who
                    discover the egg was not destroyed, and decide to return it to Xadia in
                    hopes of preventing war.
                </p>

                <blockquote class="lore-box">
                    "There is light in the world — in the sun, and the moon, and the stars.
                    In living things, and in the people I love. And I will carry it with me
                    wherever I go." — <strong>Callum</strong>
                </blockquote>
            </div>

            <div class="about-right">
                <span class="section-tag">Why It Matters</span>
                <h2>Storytelling<br />with Heart</h2>

                <p>
                    Created by <strong>Aaron Ehasz</strong> (head writer of <em>Avatar: The
                    Last Airbender</em>) and <strong>Justin Richmond</strong>, The Dragon
                    Prince carries forward a tradition of animated fantasy that takes its
                    audience <em>seriously</em>.
                </p>

                <p>
                    The show weaves themes of <strong>grief, prejudice, found family,
                    and self-discovery</strong> into its adventure narrative. Its diverse
                    cast — including a deaf character who communicates through sign language,
                    and same-sex couples presented matter-of-factly — broke new ground for
                    mainstream animation.
                </p>

                <p>
                    The magic system is one of the most <em>imaginative and internally
                    consistent</em> in modern fantasy: six primal sources governing all
                    natural magic, each with its own philosophy and connected elf culture.
                </p>
            </div>
        </section>

        <div class="rune-divider"><span>◆</span></div>

        <!-- ══════════════════════════════
             CHARACTERS
        ══════════════════════════════ -->
        <section id="characters">
            <span class="section-tag">The Fellowship</span>
            <h2>Key Characters</h2>
            <p>
                A remarkable cast of heroes, villains, and everyone in between —
                each carrying wounds and wisdom in equal measure.
            </p>

            <div class="chars-grid">
                <article class="char-card">
                    <span class="char-icon">🌙</span>
                    <span class="char-role">Moonshadow Elf · Assassin</span>
                    <h3>Rayla</h3>
                    <p>
                        Fierce, loyal, and haunted by her parents' perceived betrayal. Rayla
                        becomes one of the show's most richly developed characters, torn
                        between duty and compassion.
                    </p>
                </article>

                <article class="char-card">
                    <span class="char-icon">⚡</span>
                    <span class="char-role">Human Prince · Mage</span>
                    <h3>Callum</h3>
                    <p>
                        Stepson to King Harrow, Callum is clumsy and earnest — but driven
                        by an extraordinary ability to <em>feel</em> magic. He becomes the
                        first human in history to master a primal source without a primal stone.
                    </p>
                </article>

                <article class="char-card">
                    <span class="char-icon">🐉</span>
                    <span class="char-role">Crown Prince · Dragon Bond</span>
                    <h3>Ezran</h3>
                    <p>
                        Young, gentle, and possessed of an uncanny ability to speak with animals.
                        Ezran carries more wisdom than his years suggest, and his bond with the
                        Dragon Prince Zym is the heart of the story.
                    </p>
                </article>

                <article class="char-card">
                    <span class="char-icon">⚔️</span>
                    <span class="char-role">Human General · Dark Mage</span>
                    <h3>Viren</h3>
                    <p>
                        The story's primary antagonist — and one of its most tragic figures.
                        Viren genuinely believes he is saving humanity, even as he destroys
                        everything he loves to do it.
                    </p>
                </article>

                <article class="char-card">
                    <span class="char-icon">✨</span>
                    <span class="char-role">Startouch Elf · Archmage</span>
                    <h3>Aaravos</h3>
                    <p>
                        Ancient, inscrutable, and terrifyingly powerful. Aaravos communicates
                        through a magical mirror and drives the show's overarching mystery.
                        His true motives remain one of fantasy's great unsolved puzzles.
                    </p>
                </article>

                <article class="char-card">
                    <span class="char-icon">🌿</span>
                    <span class="char-role">Sunfire Elf · General</span>
                    <h3>Janai</h3>
                    <p>
                        Commander of the Sunfire Elves, a formidable warrior whose
                        relationship with Queen Amaya is one of the series' most beloved
                        and warmly rendered storylines.
                    </p>
                </article>
            </div>
        </section>

        <div class="rune-divider"><span>✦</span></div>

        <!-- ══════════════════════════════
             ARCANUM / MAGIC SYSTEM
        ══════════════════════════════ -->
        <section id="arcanum">
            <span class="section-tag">The Arcanum</span>
            <h2>Six Primal Sources</h2>

            <div class="arcanum-inner">

                <div>
                    <p>
                        All natural magic in Xadia flows from <strong>six primal sources</strong> —
                        the fundamental forces of nature. Elves are born connected to one source.
                        Humans, traditionally cut off from this power, invented
                        <em>dark magic</em> as a dangerous shortcut.
                    </p>
                    <p>
                        To wield primal magic, a mage must understand and connect with
                        the <em>arcanum</em> — the deeper truth behind each source. Callum's
                        breakthrough moment, realising he can feel the Sky arcanum in his
                        own breath, is one of the most moving scenes in the series.
                    </p>

                    <!-- ORDERED LIST: The Six Primal Sources -->
                    <h3>The Six Primal Sources</h3>
                    <ol>
                        <li>
                            <strong>Sun</strong> — Fire, heat, and life-giving energy.
                            Domain of the Sunfire Elves.
                        </li>
                        <li>
                            <strong>Moon</strong> — Illusion, transformation, and shadow.
                            Domain of the Moonshadow Elves.
                        </li>
                        <li>
                            <strong>Stars</strong> — The most ancient and mysterious source.
                            Domain of the rare Startouch Elves.
                        </li>
                        <li>
                            <strong>Sky</strong> — Wind, storms, and lightning.
                            The source Callum masters — an unprecedented feat for a human.
                        </li>
                        <li>
                            <strong>Earth</strong> — Stone, nature, and endurance.
                            Domain of the Earthblood Elves.
                        </li>
                        <li>
                            <strong>Ocean</strong> — Water, tide, and the deep.
                            Domain of the Tidebound Elves.
                        </li>
                    </ol>
                </div>

                <div>
                    <p>
                        Beyond the six primal sources lies <strong>Dark Magic</strong> —
                        a power humans created by consuming the life force of magical creatures.
                        Potent but morally corrosive, its use is one of the show's central
                        moral dilemmas.
                    </p>
                    <p>
                        The show treats magic not merely as a combat system but as
                        a <em>philosophical framework</em>: to use magic is to express your
                        deepest understanding of the world around you.
                    </p>

                    <!-- UNORDERED LIST: Why fans love the show -->
                    <h3>Why Fans Love It</h3>
                    <ul>
                        <li>Deeply consistent, philosophically grounded magic system</li>
                        <li>Representation handled with grace and naturalness</li>
                        <li>Villains written with genuine empathy and complexity</li>
                        <li>Stunning hand-drawn-inspired 3D animation style</li>
                        <li>Emotional storytelling that respects audiences of all ages</li>
                        <li>A sprawling world with centuries of hidden lore to uncover</li>
                        <li>Rayla and Callum's relationship — among animation's best</li>
                    </ul>
                </div>

            </div>
        </section>

        <div class="rune-divider"><span>◆</span></div>

        <!-- ══════════════════════════════
             SEASONS TIMELINE
        ══════════════════════════════ -->
        <section id="seasons">
            <span class="section-tag">The Arc So Far</span>
            <h2>Season by Season</h2>

            <div class="seasons-track">
                <div class="season-item">
                    <span class="season-num">Season 01 · 2018</span>
                    <h3>Moon</h3>
                    <p>
                        The journey begins. Rayla, Callum, and Ezran discover Zym's egg and
                        make the fateful choice to return it to Xadia rather than use it as a
                        bargaining chip for war.
                    </p>
                </div>

                <div class="season-item">
                    <span class="season-num">Season 02 · 2019</span>
                    <h3>Sky</h3>
                    <p>
                        The trio crosses into Xadia. Callum wrestles with dark magic's
                        temptation before achieving his miraculous connection to the Sky arcanum.
                    </p>
                </div>

                <div class="season-item">
                    <span class="season-num">Season 03 · 2019</span>
                    <h3>Sun</h3>
                    <p>
                        The climax of the first arc. Zym is returned to his mother Zubeia.
                        Viren's alliance with Aaravos reaches its terrible peak — and the cost
                        of war becomes devastatingly real.
                    </p>
                </div>

                <div class="season-item">
                    <span class="season-num">Seasons 04 – 07 · 2022 – 2025</span>
                    <h3>The Mystery of Aaravos</h3>
                    <p>
                        A new saga begins two years later. The shadow of Aaravos looms over
                        everything as new threats, new alliances, and ancient secrets reshape
                        the world of Xadia once more.
                    </p>
                </div>
            </div>
        </section>

        <div class="rune-divider"><span>✦</span></div>

        <!-- ══════════════════════════════
             EXTERNAL LINKS / EXPLORE
        ══════════════════════════════ -->
        <section id="explore">
            <span class="section-tag">Continue the Journey</span>
            <h2>Explore Further</h2>
            <p>
                Ready to dive into Xadia? These are the best places to watch,
                read, and connect with the wider fan community.
            </p>

            <div class="links-row">
                
                    href="https://www.netflix.com/title/80117552"
                    class="scroll-link primary"
                    target="_blank"
                    rel="noopener noreferrer"
                >
                    Watch on Netflix ↗
                </a>
                
                    href="https://dragonprince.fandom.com/wiki/The_Dragon_Prince_Wiki"
                    class="scroll-link"
                    target="_blank"
                    rel="noopener noreferrer"
                >
                    Fan Wiki ↗
                </a>
                
                    href="https://en.wikipedia.org/wiki/The_Dragon_Prince"
                    class="scroll-link sky-variant"
                    target="_blank"
                    rel="noopener noreferrer"
                >
                    Wikipedia ↗
                </a>
                <a href="#" class="scroll-link sky-variant">↑ Back to Top</a>
            </div>
        </section>

        <!-- ══════════════════════════════
             FOOTER
        ══════════════════════════════ -->
        <footer>
            <span>The Dragon Prince — Fan Compendium · 2026</span>
            <span>
                Created by
                
                    href="https://www.wonderstorm.net"
                    target="_blank"
                    rel="noopener noreferrer"
                >Wonderstorm</a>
                &amp; produced for Netflix · Fan page, not officially affiliated
            </span>
        </footer>

    </body>
</html>
