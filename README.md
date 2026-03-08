<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>README — Modélisation des Matériaux Composites</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=DM+Mono:wght@300;400;500&family=Lato:wght@300;400;700&display=swap" rel="stylesheet"/>
<style>
  :root {
    --ink:     #0e0e12;
    --paper:   #f5f2eb;
    --cream:   #ede9df;
    --accent:  #1a3a5c;
    --gold:    #b8922a;
    --rule:    #c9c1b0;
    --mono:    'DM Mono', monospace;
    --serif:   'Playfair Display', Georgia, serif;
    --sans:    'Lato', sans-serif;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--paper);
    color: var(--ink);
    font-family: var(--sans);
    font-weight: 300;
    line-height: 1.75;
    font-size: 15px;
  }

  /* ── MASTHEAD ─────────────────────────────────────────────── */
  .masthead {
    background: var(--accent);
    color: var(--paper);
    padding: 0;
    position: relative;
    overflow: hidden;
  }

  .masthead::before {
    content: '';
    position: absolute;
    inset: 0;
    background:
      repeating-linear-gradient(
        90deg,
        transparent,
        transparent 59px,
        rgba(255,255,255,.04) 59px,
        rgba(255,255,255,.04) 60px
      ),
      repeating-linear-gradient(
        0deg,
        transparent,
        transparent 59px,
        rgba(255,255,255,.04) 59px,
        rgba(255,255,255,.04) 60px
      );
    pointer-events: none;
  }

  .masthead-inner {
    position: relative;
    max-width: 1100px;
    margin: 0 auto;
    padding: 72px 48px 60px;
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 32px;
    align-items: end;
  }

  .journal-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: .25em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .journal-label::before {
    content: '';
    display: inline-block;
    width: 32px;
    height: 1px;
    background: var(--gold);
  }

  h1.title {
    font-family: var(--serif);
    font-size: clamp(1.8rem, 4vw, 3rem);
    font-weight: 900;
    line-height: 1.15;
    letter-spacing: -.01em;
    color: #fff;
    margin-bottom: 8px;
  }
  h1.title em {
    font-style: italic;
    color: var(--gold);
  }

  .subtitle {
    font-family: var(--sans);
    font-weight: 300;
    font-size: .95rem;
    color: rgba(255,255,255,.65);
    letter-spacing: .03em;
    margin-top: 14px;
  }

  .meta-chip {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: .1em;
    text-transform: uppercase;
    background: rgba(255,255,255,.08);
    border: 1px solid rgba(255,255,255,.15);
    border-radius: 4px;
    padding: 6px 12px;
    color: rgba(255,255,255,.75);
    white-space: nowrap;
    display: flex;
    flex-direction: column;
    gap: 6px;
    align-self: start;
    margin-top: 28px;
  }
  .meta-chip span { display: block; }
  .meta-chip .val { color: var(--gold); font-size: 11px; }

  .rule-gold {
    height: 2px;
    background: linear-gradient(90deg, var(--gold) 0%, transparent 100%);
    margin-top: 40px;
  }

  /* ── AUTHOR STRIP ─────────────────────────────────────────── */
  .author-strip {
    background: var(--cream);
    border-bottom: 1px solid var(--rule);
    padding: 16px 0;
  }
  .author-strip-inner {
    max-width: 1100px;
    margin: 0 auto;
    padding: 0 48px;
    display: flex;
    flex-wrap: wrap;
    gap: 32px;
    font-family: var(--mono);
    font-size: 11px;
    color: #666;
    align-items: center;
  }
  .author-strip-inner strong { color: var(--accent); font-size: 12px; }

  /* ── LANG TOGGLE ──────────────────────────────────────────── */
  .lang-toggle {
    max-width: 1100px;
    margin: 48px auto 0;
    padding: 0 48px;
    display: flex;
    gap: 0;
    width: fit-content;
  }
  .lang-btn {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: .12em;
    text-transform: uppercase;
    padding: 9px 22px;
    border: 1px solid var(--rule);
    background: var(--paper);
    cursor: pointer;
    color: #888;
    transition: all .2s;
  }
  .lang-btn:first-child { border-radius: 3px 0 0 3px; }
  .lang-btn:last-child  { border-radius: 0 3px 3px 0; border-left: none; }
  .lang-btn.active {
    background: var(--accent);
    border-color: var(--accent);
    color: #fff;
  }

  /* ── LAYOUT ───────────────────────────────────────────────── */
  .page { max-width: 1100px; margin: 0 auto; padding: 0 48px 96px; }

  .version { display: none; }
  .version.active { display: block; }

  /* ── SECTION HEADERS ──────────────────────────────────────── */
  .section { margin-top: 72px; }

  .section-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: .3em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 6px;
  }

  h2.section-title {
    font-family: var(--serif);
    font-size: 1.7rem;
    font-weight: 700;
    color: var(--accent);
    line-height: 1.2;
    padding-bottom: 14px;
    border-bottom: 1px solid var(--rule);
    margin-bottom: 28px;
  }

  h3.sub-title {
    font-family: var(--serif);
    font-size: 1.15rem;
    font-weight: 700;
    color: var(--ink);
    margin: 36px 0 12px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  h3.sub-title::before {
    content: '';
    display: inline-block;
    width: 4px;
    height: 18px;
    background: var(--gold);
    border-radius: 2px;
    flex-shrink: 0;
  }

  p { margin-bottom: 14px; }

  /* ── OBJECTIVE CARDS ──────────────────────────────────────── */
  .obj-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-top: 8px;
  }
  .obj-card {
    background: var(--cream);
    border: 1px solid var(--rule);
    border-top: 3px solid var(--accent);
    border-radius: 4px;
    padding: 24px 24px 20px;
  }
  .obj-num {
    font-family: var(--serif);
    font-size: 2.5rem;
    font-weight: 900;
    color: var(--rule);
    line-height: 1;
    margin-bottom: 8px;
  }
  .obj-card h4 {
    font-family: var(--sans);
    font-weight: 700;
    font-size: .9rem;
    text-transform: uppercase;
    letter-spacing: .06em;
    color: var(--accent);
    margin-bottom: 10px;
  }

  /* ── TREE ─────────────────────────────────────────────────── */
  .tree-box {
    background: #0e1825;
    color: #d4cfc4;
    font-family: var(--mono);
    font-size: 12.5px;
    line-height: 1.8;
    padding: 28px 32px;
    border-radius: 6px;
    overflow-x: auto;
    border-left: 3px solid var(--gold);
  }
  .tree-box .t-root  { color: #eac97a; font-weight: 500; }
  .tree-box .t-ch    { color: #7ab8ea; }
  .tree-box .t-leaf  { color: #a8d8a8; }
  .tree-box .t-note  { color: #888; font-style: italic; }

  /* ── NOTEBOOK CARDS ───────────────────────────────────────── */
  .nb-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    margin-top: 4px;
  }
  .nb-card {
    border: 1px solid var(--rule);
    border-radius: 6px;
    overflow: hidden;
    transition: transform .2s, box-shadow .2s;
  }
  .nb-card:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 24px rgba(0,0,0,.1);
  }
  .nb-header {
    padding: 18px 20px 14px;
    color: #fff;
    position: relative;
  }
  .nb-card:nth-child(1) .nb-header { background: #1a3a5c; }
  .nb-card:nth-child(2) .nb-header { background: #2a4a35; }
  .nb-card:nth-child(3) .nb-header { background: #4a2a35; }

  .nb-num {
    font-family: var(--serif);
    font-size: 3rem;
    font-weight: 900;
    opacity: .15;
    position: absolute;
    right: 16px;
    top: 8px;
    line-height: 1;
  }
  .nb-tag {
    font-family: var(--mono);
    font-size: 9px;
    letter-spacing: .2em;
    text-transform: uppercase;
    opacity: .7;
    margin-bottom: 4px;
  }
  .nb-name {
    font-family: var(--mono);
    font-size: 11px;
    opacity: .85;
    margin-bottom: 8px;
  }
  .nb-title {
    font-family: var(--serif);
    font-size: 1rem;
    font-weight: 700;
  }
  .nb-body { padding: 18px 20px; background: var(--cream); }
  .nb-body p { font-size: .85rem; line-height: 1.6; color: #555; margin-bottom: 12px; }

  /* ── PARAM TABLE ──────────────────────────────────────────── */
  .param-table {
    width: 100%;
    border-collapse: collapse;
    font-size: .83rem;
    margin-top: 6px;
  }
  .param-table th {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: .15em;
    text-transform: uppercase;
    color: var(--gold);
    background: #0e1825;
    padding: 9px 12px;
    text-align: left;
    font-weight: 400;
  }
  .param-table td {
    padding: 8px 12px;
    border-bottom: 1px solid var(--rule);
    vertical-align: top;
    font-family: var(--mono);
    font-size: 12px;
    color: #444;
  }
  .param-table tr:last-child td { border-bottom: none; }
  .param-table tr:nth-child(even) td { background: var(--cream); }

  /* ── CODE BLOCK ───────────────────────────────────────────── */
  pre {
    background: #0e1825;
    color: #c8d8e8;
    font-family: var(--mono);
    font-size: 12px;
    line-height: 1.7;
    padding: 20px 24px;
    border-radius: 5px;
    overflow-x: auto;
    margin: 12px 0;
    border-left: 3px solid var(--gold);
  }
  code {
    font-family: var(--mono);
    font-size: .85em;
    background: var(--cream);
    padding: 2px 6px;
    border-radius: 3px;
    color: var(--accent);
  }
  pre code { background: transparent; padding: 0; color: inherit; }

  /* ── FUNCTION TABLE ───────────────────────────────────────── */
  .fn-table {
    width: 100%;
    border-collapse: collapse;
    font-size: .83rem;
    margin-top: 16px;
  }
  .fn-table th {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: .15em;
    text-transform: uppercase;
    background: var(--accent);
    color: rgba(255,255,255,.75);
    padding: 10px 16px;
    text-align: left;
    font-weight: 400;
  }
  .fn-table td {
    padding: 10px 16px;
    border-bottom: 1px solid var(--rule);
    vertical-align: top;
  }
  .fn-table td:first-child {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--accent);
    white-space: nowrap;
  }
  .fn-table td:last-child { font-size: .88rem; color: #555; }
  .fn-table tr:last-child td { border-bottom: none; }

  /* ── GLOBAL PARAMS ────────────────────────────────────────── */
  .param-chips {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    margin-top: 12px;
  }
  .param-chip {
    border: 1px solid var(--rule);
    border-radius: 4px;
    padding: 10px 16px;
    font-family: var(--mono);
    font-size: 11px;
    background: var(--cream);
  }
  .param-chip .pk { color: #888; font-size: 10px; letter-spacing: .1em; text-transform: uppercase; }
  .param-chip .pv { color: var(--accent); font-weight: 500; font-size: 13px; margin-top: 3px; }

  /* ── NOTE BOX ─────────────────────────────────────────────── */
  .note-box {
    border: 1px solid var(--gold);
    border-left: 4px solid var(--gold);
    background: #fffbf0;
    padding: 20px 24px;
    border-radius: 4px;
    margin-top: 12px;
  }
  .note-box .note-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: .2em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 8px;
  }
  .note-box p { font-size: .9rem; color: #444; margin-bottom: 8px; }
  .note-box .formula {
    text-align: center;
    font-family: var(--mono);
    font-size: 1rem;
    color: var(--accent);
    padding: 10px;
    background: rgba(26,58,92,.05);
    border-radius: 4px;
    margin: 10px 0;
  }

  /* ── RESULTS ──────────────────────────────────────────────── */
  .result-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    margin-top: 8px;
  }
  .result-card {
    border: 1px solid var(--rule);
    border-radius: 6px;
    overflow: hidden;
  }
  .result-header {
    background: var(--accent);
    color: #fff;
    padding: 14px 18px;
    font-family: var(--serif);
    font-size: .95rem;
    font-weight: 700;
  }
  .result-header span {
    font-family: var(--mono);
    font-size: 9px;
    letter-spacing: .15em;
    text-transform: uppercase;
    opacity: .6;
    display: block;
    margin-bottom: 3px;
    font-weight: 400;
  }
  .result-body { padding: 16px 18px; background: var(--cream); }
  .result-body ul { padding-left: 0; list-style: none; }
  .result-body li {
    font-size: .85rem;
    color: #444;
    padding: 6px 0;
    border-bottom: 1px solid var(--rule);
    padding-left: 14px;
    position: relative;
  }
  .result-body li:last-child { border-bottom: none; }
  .result-body li::before {
    content: '→';
    position: absolute;
    left: 0;
    color: var(--gold);
    font-size: .8rem;
  }

  /* ── REFERENCES ───────────────────────────────────────────── */
  .ref-list { list-style: none; padding: 0; margin-top: 8px; }
  .ref-list li {
    font-size: .88rem;
    padding: 12px 0 12px 48px;
    border-bottom: 1px solid var(--rule);
    position: relative;
    color: #444;
  }
  .ref-list li:last-child { border-bottom: none; }
  .ref-num {
    position: absolute;
    left: 0;
    font-family: var(--mono);
    font-size: 10px;
    color: var(--gold);
    background: var(--cream);
    border: 1px solid var(--rule);
    padding: 2px 7px;
    border-radius: 3px;
    top: 14px;
  }
  .ref-list a { color: var(--accent); text-decoration: none; border-bottom: 1px solid var(--rule); }
  .ref-list a:hover { border-bottom-color: var(--accent); }

  /* ── DIVIDER ──────────────────────────────────────────────── */
  .lang-divider {
    max-width: 1100px;
    margin: 80px auto 0;
    padding: 0 48px;
  }
  .lang-divider-inner {
    border-top: 2px solid var(--accent);
    padding-top: 20px;
    display: flex;
    align-items: center;
    gap: 20px;
  }
  .lang-divider-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: .3em;
    text-transform: uppercase;
    color: var(--accent);
    white-space: nowrap;
  }
  .lang-divider-line { flex: 1; height: 1px; background: var(--rule); }

  /* ── FOOTER ───────────────────────────────────────────────── */
  footer {
    background: var(--accent);
    color: rgba(255,255,255,.5);
    text-align: center;
    padding: 28px 48px;
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: .08em;
    margin-top: 80px;
  }
  footer strong { color: var(--gold); }

  /* ── RESPONSIVE ───────────────────────────────────────────── */
  @media (max-width: 800px) {
    .masthead-inner { grid-template-columns: 1fr; padding: 48px 24px 40px; }
    .page { padding: 0 24px 64px; }
    .obj-grid, .nb-grid, .result-grid { grid-template-columns: 1fr; }
    .author-strip-inner { padding: 0 24px; }
    .lang-toggle { padding: 0 24px; }
    .lang-divider { padding: 0 24px; }
  }

  /* ── ANIMATIONS ───────────────────────────────────────────── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .masthead-inner > * { animation: fadeUp .6s ease both; }
  .masthead-inner > *:nth-child(2) { animation-delay: .15s; }
</style>
</head>
<body>

<!-- ═══════════════════════════════ MASTHEAD ══════════════════════════════ -->
<header class="masthead">
  <div class="masthead-inner">
    <div>
      <div class="journal-label">Mémoire de Master · Université de Lomé · 2023–2025</div>
      <h1 class="title">
        Modélisation des<br>
        <em>Propriétés Mécaniques</em><br>
        des Matériaux Composites
      </h1>
      <p class="subtitle">
        Homogénéisation analytique · Mori–Tanaka · Hervé–Zaoui · Python echoes
      </p>
    </div>
    <div class="meta-chip">
      <span class="pk">Auteur</span>
      <span class="val">HOUNKPE M. Roland</span>
      <span class="pk" style="margin-top:8px">Directeur</span>
      <span class="val">Dr. A. Adessina</span>
      <span class="pk" style="margin-top:8px">Co-directeur</span>
      <span class="val">Prof. K. N'Wuitcha</span>
      <span class="pk" style="margin-top:8px">Spécialité</span>
      <span class="val">Physique Théorique</span>
    </div>
  </div>
  <div class="rule-gold"></div>
</header>

<!-- ═══════════════════════════ AUTHOR STRIP ══════════════════════════════ -->
<div class="author-strip">
  <div class="author-strip-inner">
    <span>📍 Université de Lomé — Département de Physique</span>
    <span>🔬 Physique Fondamentale &amp; Applications</span>
    <span>🐍 <strong>echoes</strong> · NumPy · Matplotlib · Jupyter</span>
    <span>📦 3 Notebooks · 1 Rapport LaTeX</span>
  </div>
</div>

<!-- ═══════════════════════════════ FRENCH ════════════════════════════════ -->
<div id="fr" class="page">

  <!-- DESCRIPTION -->
  <div class="section">
    <div class="section-label">01 — Présentation</div>
    <h2 class="section-title">Description du projet</h2>
    <p>
      Ce projet constitue le support numérique du mémoire de Master en Physique
      Théorique. Il regroupe <strong>trois notebooks Jupyter</strong> qui implémentent
      l'homogénéisation analytique de matériaux composites selon le schéma de
      Mori–Tanaka, via la bibliothèque Python <code>echoes</code>. Les simulations
      couvrent trois configurations de volumes élémentaires représentatifs (VER) de
      complexité croissante, et permettent des études paramétriques systématiques
      reliant microstructure et propriétés élastiques effectives.
    </p>
  </div>

  <!-- OBJECTIF -->
  <div class="section">
    <div class="section-label">02 — Motivation</div>
    <h2 class="section-title">Objectif du mémoire</h2>
    <div class="obj-grid">
      <div class="obj-card">
        <div class="obj-num">01</div>
        <h4>Maîtrise du formalisme</h4>
        <p>
          S'approprier le formalisme micromécanique en élasticité linéaire isotrope —
          solution d'Eshelby (1957), tenseurs de localisation, schéma de Mori–Tanaka,
          et modèle analytique de Hervé–Zaoui pour les inclusions multicouches.
        </p>
      </div>
      <div class="obj-card">
        <div class="obj-num">02</div>
        <h4>Études paramétriques</h4>
        <p>
          Quantifier l'influence de chaque paramètre microstructural — fraction
          volumique, contraste de module, forme des inclusions, épaisseur et rigidité
          de l'interphase — sur les propriétés élastiques effectives du composite, afin
          de dégager des <strong>règles de conception exploitables</strong>.
        </p>
      </div>
    </div>
  </div>

  <!-- STRUCTURE MEMOIRE -->
  <div class="section">
    <div class="section-label">03 — Architecture</div>
    <h2 class="section-title">Structure du mémoire</h2>
    <p>Le mémoire est rédigé en LaTeX (<code>1-RAPPORT_ROLAND.tex</code>).</p>
    <div class="tree-box">
<span class="t-root">Introduction générale</span>
│
├── <span class="t-ch">Chapitre 1</span> — Recherche bibliographique
│   ├── <span class="t-leaf">Matériaux composites</span> <span class="t-note">(historique, constituants, applications)</span>
│   ├── <span class="t-leaf">Méthodes de modélisation</span> <span class="t-note">(analytique, numérique FEM/FFT, expérimental)</span>
│   ├── <span class="t-leaf">Micromécanique &amp; homogénéisation</span> <span class="t-note">(VER, Voigt, Reuss, Hill–Mandel)</span>
│   ├── <span class="t-leaf">Élasticité linéaire</span> <span class="t-note">(isotropie, notation Kelvin–Mandel)</span>
│   ├── <span class="t-leaf">Problème d'Eshelby</span> <span class="t-note">(inclusion + inhomogénéité)</span>
│   └── <span class="t-leaf">Schémas d'homogénéisation</span> <span class="t-note">(dilué, auto-cohérent, Mori–Tanaka)</span>
│
├── <span class="t-ch">Chapitre 2</span> — Modélisation des propriétés effectives
│   ├── <span class="t-leaf">VER à inclusions simples</span>
│   ├── <span class="t-leaf">VER à inclusions composites</span> <span class="t-note">(bicouches)</span>
│   ├── <span class="t-leaf">VER à inclusions mixtes</span>
│   └── <span class="t-leaf">Modèle d'Hervé–Zaoui</span> <span class="t-note">(n couches, matrices de transfert)</span>
│       ├── <span class="t-note">Chargement hydrostatique  →  k_eff</span>
│       └── <span class="t-note">Chargement déviatorique   →  μ_eff</span>
│
├── <span class="t-ch">Chapitre 3</span> — Résultats &amp; Discussions
│   ├── <span class="t-leaf">VER 1</span> <span class="t-note">fraction vol. · contraste · forme (oblate/sphère/prolate)</span>
│   ├── <span class="t-leaf">VER 2</span> <span class="t-note">fraction vol. · contraste · épaisseur interphase (ε)</span>
│   └── <span class="t-leaf">VER 3</span> <span class="t-note">fractions · contrastes C1–C4 · forme · couplage forme–ε</span>
│
└── <span class="t-root">Conclusion générale</span>
    </div>
  </div>

  <!-- NOTEBOOKS -->
  <div class="section">
    <div class="section-label">04 — Code</div>
    <h2 class="section-title">Organisation des notebooks</h2>
    <p>Trois notebooks indépendants — exécutables dans n'importe quel ordre.</p>

    <div class="nb-grid">
      <!-- VER 1 -->
      <div class="nb-card">
        <div class="nb-header">
          <div class="nb-num">1</div>
          <div class="nb-tag">VER Simple</div>
          <div class="nb-name">ver_simple_spherique.ipynb</div>
          <div class="nb-title">Inclusions sphéroïdales</div>
        </div>
        <div class="nb-body">
          <p>Matrice + inclusions homogènes. Mori–Tanaka appliqué directement.</p>
          <table class="param-table">
            <tr><th>Étude</th><th>Paramètre</th></tr>
            <tr><td>Fraction vol.</td><td>f∈[0,0.6], Ei∈{5,10,20,50} GPa</td></tr>
            <tr><td>Contraste</td><td>Ei/Em∈[0.1,5], fi∈{0.3–0.6}</td></tr>
            <tr><td>Forme (contrasté)</td><td>ω∈[0.1,10] log, Ei=70 GPa</td></tr>
            <tr><td>Forme (validation)</td><td>ω∈[0.1,10] log, Ei=Em</td></tr>
          </table>
        </div>
      </div>

      <!-- VER 2 -->
      <div class="nb-card">
        <div class="nb-header">
          <div class="nb-num">2</div>
          <div class="nb-tag">VER Composite</div>
          <div class="nb-name">ver_composite.ipynb</div>
          <div class="nb-title">Inclusions bicouches</div>
        </div>
        <div class="nb-body">
          <p>Cœur E₁ + interphase E₂. Hervé–Zaoui → C<sup>eff</sup><sub>inc</sub> → Mori–Tanaka.</p>
          <table class="param-table">
            <tr><th>Étude</th><th>Paramètre</th></tr>
            <tr><td>Fraction vol. (×3)</td><td>E₂∈{5,10,15} GPa</td></tr>
            <tr><td>Contraste E₁/Em</td><td>E₂=15 GPa fixe</td></tr>
            <tr><td>Contraste E₂/Em</td><td>E₁=Em (cœur neutre)</td></tr>
            <tr><td>Gradient E₂/E₁</td><td>E₁=10 GPa fixe</td></tr>
            <tr><td>Épaisseur ε (×3)</td><td>fi, E₁ ou E₂ variable</td></tr>
          </table>
        </div>
      </div>

      <!-- VER 3 -->
      <div class="nb-card">
        <div class="nb-header">
          <div class="nb-num">3</div>
          <div class="nb-tag">VER Mixte</div>
          <div class="nb-name">ver_mixte.ipynb</div>
          <div class="nb-title">Deux populations</div>
        </div>
        <div class="nb-body">
          <p>Inclusions simples (E_s, ω) + composites (E_c, E_sh) dans la même matrice.</p>
          <table class="param-table">
            <tr><th>Étude</th><th>Paramètre</th></tr>
            <tr><td>Fractions (×3)</td><td>fs=fc, fs var., fc var.</td></tr>
            <tr><td>Contrastes C1–C4</td><td>Es, Ec, Esh, Esh/Ec</td></tr>
            <tr><td>Forme (×3)</td><td>ω∈[0.1,10], modes A/B</td></tr>
            <tr><td>ε + forme (×3)</td><td>5 valeurs ω, validation</td></tr>
          </table>
        </div>
      </div>
    </div>
  </div>

  <!-- ECHOES -->
  <div class="section">
    <div class="section-label">05 — Outil</div>
    <h2 class="section-title">Bibliothèque <em>echoes</em></h2>
    <p>
      <code>echoes</code> (<em>Extended Calculator of HOmogEnization Schemes</em>) est
      développée par <strong>Jean-François Barthélémy</strong> (Cerema – Université
      Gustave Eiffel), directeur de ce mémoire. Noyau C++, interface Python.
    </p>
    <p>
      📘 <strong>Documentation :</strong>
      <a href="https://jfbarthelemy.github.io/echoes" style="color:var(--accent)">
        https://jfbarthelemy.github.io/echoes</a> &nbsp;|&nbsp;
      <strong>DOI :</strong>
      <a href="https://doi.org/10.5281/zenodo.14959866" style="color:var(--accent)">
        10.5281/zenodo.14959866</a>
    </p>
    <pre><code># Télécharger le .whl depuis le lien DOI, puis :
pip install -U echoes-XYZ.whl</code></pre>

    <table class="fn-table">
      <tr><th>Fonction</th><th>Rôle</th></tr>
      <tr><td>stiff_Enu(E, nu)</td><td>Tenseur de rigidité isotrope depuis E et ν</td></tr>
      <tr><td>sphere(C0)</td><td>Tenseur de Hill — inclusion sphérique</td></tr>
      <tr><td>spheroidal(C0, omega)</td><td>Tenseur de Hill — inclusion sphéroïdale de rapport ω</td></tr>
      <tr><td>sphere_nlayers(radii, stiffs)</td><td>Modèle Hervé–Zaoui : inclusion à n couches concentriques</td></tr>
      <tr><td>rve(C0)</td><td>Crée un VER avec matrice C₀</td></tr>
      <tr><td>ellipsoid(C_i, P, f)</td><td>Ajoute une phase d'inclusion au VER</td></tr>
      <tr><td>homogenize(MT)</td><td>Calcule le tenseur effectif par Mori–Tanaka</td></tr>
    </table>
  </div>

  <!-- GLOBAL PARAMS -->
  <div class="section">
    <div class="section-label">06 — Convention</div>
    <h2 class="section-title">Paramètres globaux</h2>
    <div class="param-chips">
      <div class="param-chip"><div class="pk">Module matrice</div><div class="pv">Em = 10 GPa</div></div>
      <div class="param-chip"><div class="pk">Poisson (VER 1 &amp; 3)</div><div class="pv">ν = 0.2</div></div>
      <div class="param-chip"><div class="pk">Poisson (VER 2)</div><div class="pv">ν = 0.1</div></div>
      <div class="param-chip"><div class="pk">Fraction max</div><div class="pv">f ≤ 0.6</div></div>
      <div class="param-chip"><div class="pk">Dimensions figures</div><div class="pv">(9, 6) pouces</div></div>
      <div class="param-chip"><div class="pk">Couleurs</div><div class="pv">blue · green · black · red</div></div>
      <div class="param-chip"><div class="pk">Marqueurs</div><div class="pv">○ □ △ ◇</div></div>
    </div>
    <pre style="margin-top:18px"><code>plt.rcParams.update({
    "axes.linewidth": 2,       "axes.labelsize": 16,    "axes.labelweight": "bold",
    "xtick.labelsize": 12,     "ytick.labelsize": 12,
    "xtick.major.width": 1.5,  "ytick.major.width": 1.5
})</code></pre>
  </div>

  <!-- NOTE E_EFF -->
  <div class="section">
    <div class="section-label">07 — Important</div>
    <h2 class="section-title">Note sur les résultats</h2>
    <div class="note-box">
      <div class="note-label">⚠ Portée des commentaires dans le rapport</div>
      <p>
        Dans le mémoire, <strong>seul le module de Young effectif Ẽ est commenté et
        analysé</strong> dans le corps du texte. Les modules de compressibilité k̃ et
        de cisaillement μ̃ sont calculés et tracés par les notebooks pour chaque étude
        (trois figures systématiques : Ẽ, k̃, μ̃), mais leur analyse détaillée n'est pas
        développée dans le rapport — ces figures constituent des données complémentaires.
      </p>
      <p>Ce choix repose sur la relation liant les trois modules :</p>
      <div class="formula">Ẽ = 9 k̃ μ̃ / (3 k̃ + μ̃)</div>
      <p>
        Les tendances observées sur k̃ et μ̃ étant cohérentes avec celles de Ẽ, analyser
        ce dernier suffit à caractériser la réponse élastique globale du composite.
      </p>
    </div>
  </div>

  <!-- RESULTATS -->
  <div class="section">
    <div class="section-label">08 — Conclusions</div>
    <h2 class="section-title">Résultats principaux</h2>
    <div class="result-grid">
      <div class="result-card">
        <div class="result-header">
          <span>VER 1</span>
          Inclusions simples
        </div>
        <div class="result-body">
          <ul>
            <li>La fraction volumique amplifie l'effet du contraste de manière non linéaire</li>
            <li>La <strong>sphère est la géométrie la moins efficace</strong> parmi toutes les formes sphéroïdales</li>
            <li>Sans contraste (Ei = Em), la forme n'a aucun effet — test de cohérence du modèle</li>
          </ul>
        </div>
      </div>
      <div class="result-card">
        <div class="result-header">
          <span>VER 2</span>
          Inclusions bicouches
        </div>
        <div class="result-body">
          <ul>
            <li>L'interphase (~27% vol.) est <strong>plus influente que le cœur (~73%)</strong> car elle est au contact direct de la matrice</li>
            <li>Le signe de E₁ − E₂ gouverne la monotonie de Ẽ avec l'épaisseur</li>
            <li>La conception doit cibler la couche périphérique</li>
          </ul>
        </div>
      </div>
      <div class="result-card">
        <div class="result-header">
          <span>VER 3</span>
          Inclusions mixtes
        </div>
        <div class="result-body">
          <ul>
            <li>À fraction égale, <strong>l'inclusion simple est toujours plus efficace</strong> que l'inclusion composite</li>
            <li>La hiérarchie interphase > cœur est robuste dans le contexte mixte</li>
            <li>Forme et épaisseur d'interphase sont des leviers <strong>additifs et indépendants</strong></li>
          </ul>
        </div>
      </div>
    </div>
  </div>

  <!-- REFERENCES -->
  <div class="section">
    <div class="section-label">09 — Bibliographie</div>
    <h2 class="section-title">Références clés</h2>
    <ul class="ref-list">
      <li><span class="ref-num">[1]</span>
        <strong>Eshelby, J.D. (1957)</strong> — The determination of the elastic field of an
        ellipsoidal inclusion, and related problems.
        <em>Proc. R. Soc. London A</em>, 241, 376–396.
      </li>
      <li><span class="ref-num">[2]</span>
        <strong>Mori, T. &amp; Tanaka, K. (1973)</strong> — Average stress in matrix and average
        elastic energy of materials with misfitting inclusions.
        <em>Acta Metallurgica</em>, 21(5), 571–574.
      </li>
      <li><span class="ref-num">[3]</span>
        <strong>Hervé, E. &amp; Zaoui, A. (1993)</strong> — n-layered inclusion-based
        micromechanical modelling. <em>Int. J. Eng. Sci.</em>, 31(1), 1–10.
      </li>
      <li><span class="ref-num">[4]</span>
        <strong>Barthélémy, J.-F. (2022)</strong> — <em>echoes: Extended Calculator of
        HOmogEnization Schemes</em>. Zenodo.
        <a href="https://doi.org/10.5281/zenodo.14959866">doi:10.5281/zenodo.14959866</a> —
        <a href="https://jfbarthelemy.github.io/echoes">Documentation</a>
      </li>
    </ul>
  </div>

</div><!-- /fr -->

<!-- ══════════════════════ LANGUAGE DIVIDER ═══════════════════════════════ -->
<div class="lang-divider">
  <div class="lang-divider-inner">
    <div class="lang-divider-line"></div>
    <div class="lang-divider-label">English Version</div>
    <div class="lang-divider-line"></div>
  </div>
</div>

<!-- ═══════════════════════════════ ENGLISH ═══════════════════════════════ -->
<div id="en" class="page">

  <!-- DESCRIPTION -->
  <div class="section">
    <div class="section-label">01 — Overview</div>
    <h2 class="section-title">Project Description</h2>
    <p>
      This project is the numerical support for a Master's thesis in Theoretical
      Physics. It contains <strong>three Jupyter notebooks</strong> implementing
      analytical homogenization of composite materials using the Mori–Tanaka scheme,
      via the Python library <code>echoes</code>. Simulations cover three representative
      volume element (RVE) configurations of increasing complexity, enabling systematic
      parametric studies linking microstructure to effective elastic properties.
    </p>
  </div>

  <!-- OBJECTIVE -->
  <div class="section">
    <div class="section-label">02 — Motivation</div>
    <h2 class="section-title">Thesis Objective</h2>
    <div class="obj-grid">
      <div class="obj-card">
        <div class="obj-num">01</div>
        <h4>Mastering the Formalism</h4>
        <p>
          Acquire proficiency in the micromechanical formalism of isotropic linear
          elasticity — Eshelby's solution (1957), localization tensors, the Mori–Tanaka
          scheme, and the Hervé–Zaoui analytical model for multi-layer inclusions.
        </p>
      </div>
      <div class="obj-card">
        <div class="obj-num">02</div>
        <h4>Parametric Studies</h4>
        <p>
          Quantify the influence of each microstructural parameter — volume fraction,
          modulus contrast, inclusion shape, interphase thickness and stiffness — on
          the effective elastic properties, and derive
          <strong>actionable design rules</strong>.
        </p>
      </div>
    </div>
  </div>

  <!-- STRUCTURE -->
  <div class="section">
    <div class="section-label">03 — Architecture</div>
    <h2 class="section-title">Thesis Structure</h2>
    <p>The thesis is written in LaTeX (<code>1-RAPPORT_ROLAND.tex</code>).</p>
    <div class="tree-box">
<span class="t-root">General Introduction</span>
│
├── <span class="t-ch">Chapter 1</span> — Literature Review
│   ├── <span class="t-leaf">Composite materials</span> <span class="t-note">(history, constituents, applications)</span>
│   ├── <span class="t-leaf">Modelling methods</span> <span class="t-note">(analytical, FEM/FFT numerical, experimental)</span>
│   ├── <span class="t-leaf">Micromechanics &amp; homogenization</span> <span class="t-note">(RVE, Voigt, Reuss, Hill–Mandel)</span>
│   ├── <span class="t-leaf">Linear elasticity</span> <span class="t-note">(isotropy, Kelvin–Mandel notation)</span>
│   ├── <span class="t-leaf">Eshelby problem</span> <span class="t-note">(inclusion + inhomogeneity)</span>
│   └── <span class="t-leaf">Homogenization schemes</span> <span class="t-note">(dilute, self-consistent, Mori–Tanaka)</span>
│
├── <span class="t-ch">Chapter 2</span> — Modelling of Effective Properties
│   ├── <span class="t-leaf">RVE with simple inclusions</span>
│   ├── <span class="t-leaf">RVE with composite inclusions</span> <span class="t-note">(two-layer)</span>
│   ├── <span class="t-leaf">RVE with mixed inclusions</span>
│   └── <span class="t-leaf">Hervé–Zaoui model</span> <span class="t-note">(n layers, transfer matrices)</span>
│       ├── <span class="t-note">Hydrostatic loading  →  k_eff</span>
│       └── <span class="t-note">Deviatoric loading   →  μ_eff</span>
│
├── <span class="t-ch">Chapter 3</span> — Results &amp; Discussion
│   ├── <span class="t-leaf">RVE 1</span> <span class="t-note">vol. fraction · contrast · shape (oblate/sphere/prolate)</span>
│   ├── <span class="t-leaf">RVE 2</span> <span class="t-note">vol. fraction · contrast · interphase thickness (ε)</span>
│   └── <span class="t-leaf">RVE 3</span> <span class="t-note">fractions · contrasts C1–C4 · shape · shape–ε coupling</span>
│
└── <span class="t-root">General Conclusion</span>
    </div>
  </div>

  <!-- NOTEBOOKS -->
  <div class="section">
    <div class="section-label">04 — Code</div>
    <h2 class="section-title">Notebook Organization</h2>
    <p>Three independent notebooks — can be run in any order.</p>

    <div class="nb-grid">
      <div class="nb-card">
        <div class="nb-header">
          <div class="nb-num">1</div>
          <div class="nb-tag">Simple RVE</div>
          <div class="nb-name">ver_simple_spherique.ipynb</div>
          <div class="nb-title">Spheroidal Inclusions</div>
        </div>
        <div class="nb-body">
          <p>Matrix + homogeneous inclusions. Mori–Tanaka applied directly.</p>
          <table class="param-table">
            <tr><th>Study</th><th>Parameter</th></tr>
            <tr><td>Vol. fraction</td><td>f∈[0,0.6], Ei∈{5,10,20,50} GPa</td></tr>
            <tr><td>Contrast</td><td>Ei/Em∈[0.1,5], fi∈{0.3–0.6}</td></tr>
            <tr><td>Shape (contrasted)</td><td>ω∈[0.1,10] log, Ei=70 GPa</td></tr>
            <tr><td>Shape (validation)</td><td>ω∈[0.1,10] log, Ei=Em</td></tr>
          </table>
        </div>
      </div>

      <div class="nb-card">
        <div class="nb-header">
          <div class="nb-num">2</div>
          <div class="nb-tag">Composite RVE</div>
          <div class="nb-name">ver_composite.ipynb</div>
          <div class="nb-title">Two-Layer Inclusions</div>
        </div>
        <div class="nb-body">
          <p>Core E₁ + interphase E₂. Hervé–Zaoui → C<sup>eff</sup><sub>inc</sub> → Mori–Tanaka.</p>
          <table class="param-table">
            <tr><th>Study</th><th>Parameter</th></tr>
            <tr><td>Vol. frac. (×3)</td><td>E₂∈{5,10,15} GPa</td></tr>
            <tr><td>Contrast E₁/Em</td><td>E₂=15 GPa fixed</td></tr>
            <tr><td>Contrast E₂/Em</td><td>E₁=Em (neutral core)</td></tr>
            <tr><td>Gradient E₂/E₁</td><td>E₁=10 GPa fixed</td></tr>
            <tr><td>Thickness ε (×3)</td><td>fi, E₁ or E₂ variable</td></tr>
          </table>
        </div>
      </div>

      <div class="nb-card">
        <div class="nb-header">
          <div class="nb-num">3</div>
          <div class="nb-tag">Mixed RVE</div>
          <div class="nb-name">ver_mixte.ipynb</div>
          <div class="nb-title">Two Populations</div>
        </div>
        <div class="nb-body">
          <p>Simple inclusions (E_s, ω) + composite inclusions (E_c, E_sh) in the same matrix.</p>
          <table class="param-table">
            <tr><th>Study</th><th>Parameter</th></tr>
            <tr><td>Fractions (×3)</td><td>fs=fc, fs var., fc var.</td></tr>
            <tr><td>Contrasts C1–C4</td><td>Es, Ec, Esh, Esh/Ec</td></tr>
            <tr><td>Shape (×3)</td><td>ω∈[0.1,10], modes A/B</td></tr>
            <tr><td>ε + shape (×3)</td><td>5 ω values, validation</td></tr>
          </table>
        </div>
      </div>
    </div>
  </div>

  <!-- ECHOES -->
  <div class="section">
    <div class="section-label">05 — Tool</div>
    <h2 class="section-title">The <em>echoes</em> Library</h2>
    <p>
      <code>echoes</code> (<em>Extended Calculator of HOmogEnization Schemes</em>) is
      developed by <strong>Jean-François Barthélémy</strong> (Cerema – Université
      Gustave Eiffel), thesis supervisor. C++ core, Python interface.
    </p>
    <p>
      📘 <strong>Documentation:</strong>
      <a href="https://jfbarthelemy.github.io/echoes" style="color:var(--accent)">
        https://jfbarthelemy.github.io/echoes</a> &nbsp;|&nbsp;
      <strong>DOI:</strong>
      <a href="https://doi.org/10.5281/zenodo.14959866" style="color:var(--accent)">
        10.5281/zenodo.14959866</a>
    </p>
    <pre><code># Download the .whl file from the DOI link above, then:
pip install -U echoes-XYZ.whl</code></pre>

    <table class="fn-table">
      <tr><th>Function</th><th>Role</th></tr>
      <tr><td>stiff_Enu(E, nu)</td><td>Build isotropic stiffness tensor from E and ν</td></tr>
      <tr><td>sphere(C0)</td><td>Hill tensor — spherical inclusion</td></tr>
      <tr><td>spheroidal(C0, omega)</td><td>Hill tensor — spheroidal inclusion with aspect ratio ω</td></tr>
      <tr><td>sphere_nlayers(radii, stiffs)</td><td>Hervé–Zaoui: n-layer concentric spherical inclusion</td></tr>
      <tr><td>rve(C0)</td><td>Create an RVE with matrix C₀</td></tr>
      <tr><td>ellipsoid(C_i, P, f)</td><td>Add an inclusion phase to the RVE</td></tr>
      <tr><td>homogenize(MT)</td><td>Compute effective tensor via Mori–Tanaka</td></tr>
    </table>
  </div>

  <!-- GLOBAL PARAMS -->
  <div class="section">
    <div class="section-label">06 — Conventions</div>
    <h2 class="section-title">Global Parameters</h2>
    <div class="param-chips">
      <div class="param-chip"><div class="pk">Matrix modulus</div><div class="pv">Em = 10 GPa</div></div>
      <div class="param-chip"><div class="pk">Poisson (RVE 1 &amp; 3)</div><div class="pv">ν = 0.2</div></div>
      <div class="param-chip"><div class="pk">Poisson (RVE 2)</div><div class="pv">ν = 0.1</div></div>
      <div class="param-chip"><div class="pk">Max volume fraction</div><div class="pv">f ≤ 0.6</div></div>
      <div class="param-chip"><div class="pk">Figure size</div><div class="pv">(9, 6) inches</div></div>
      <div class="param-chip"><div class="pk">Colors</div><div class="pv">blue · green · black · red</div></div>
      <div class="param-chip"><div class="pk">Markers</div><div class="pv">○ □ △ ◇</div></div>
    </div>
    <pre style="margin-top:18px"><code>plt.rcParams.update({
    "axes.linewidth": 2,       "axes.labelsize": 16,    "axes.labelweight": "bold",
    "xtick.labelsize": 12,     "ytick.labelsize": 12,
    "xtick.major.width": 1.5,  "ytick.major.width": 1.5
})</code></pre>
  </div>

  <!-- NOTE -->
  <div class="section">
    <div class="section-label">07 — Important</div>
    <h2 class="section-title">Note on Results</h2>
    <div class="note-box">
      <div class="note-label">⚠ Scope of commentary in the thesis</div>
      <p>
        In the thesis, <strong>only the effective Young's modulus Ẽ is commented and
        analysed</strong> in the main text. The bulk modulus k̃ and shear modulus μ̃
        are computed and plotted by the notebooks for every parametric study (three
        figures are systematically produced: Ẽ, k̃, μ̃), but their detailed analysis is
        not developed in the report — these figures serve as supplementary data.
      </p>
      <p>This choice is justified by the relation linking the three moduli:</p>
      <div class="formula">Ẽ = 9 k̃ μ̃ / (3 k̃ + μ̃)</div>
      <p>
        Since the trends in k̃ and μ̃ are consistent with those in Ẽ, analysing the
        latter is sufficient to characterise the global elastic response.
      </p>
    </div>
  </div>

  <!-- RESULTS -->
  <div class="section">
    <div class="section-label">08 — Conclusions</div>
    <h2 class="section-title">Key Results</h2>
    <div class="result-grid">
      <div class="result-card">
        <div class="result-header">
          <span>RVE 1</span>
          Simple Inclusions
        </div>
        <div class="result-body">
          <ul>
            <li>Volume fraction amplifies contrast effects in a non-linear manner</li>
            <li>The <strong>sphere is the least efficient geometry</strong> among all spheroidal shapes</li>
            <li>Without contrast (Ei = Em), shape has no effect — internal consistency test</li>
          </ul>
        </div>
      </div>
      <div class="result-card">
        <div class="result-header">
          <span>RVE 2</span>
          Two-Layer Inclusions
        </div>
        <div class="result-body">
          <ul>
            <li>Interphase (~27% vol.) is <strong>more influential than the core (~73%)</strong> due to direct matrix contact</li>
            <li>Sign of E₁ − E₂ governs monotonicity of Ẽ with thickness</li>
            <li>Design should target the peripheral layer</li>
          </ul>
        </div>
      </div>
      <div class="result-card">
        <div class="result-header">
          <span>RVE 3</span>
          Mixed Inclusions
        </div>
        <div class="result-body">
          <ul>
            <li>At equal fraction, <strong>simple inclusions are always more efficient</strong> than composite ones</li>
            <li>Interphase > core hierarchy is structural and robust in the mixed context</li>
            <li>Shape and interphase thickness are <strong>additive, independent</strong> levers</li>
          </ul>
        </div>
      </div>
    </div>
  </div>

  <!-- REFERENCES -->
  <div class="section">
    <div class="section-label">09 — Bibliography</div>
    <h2 class="section-title">Key References</h2>
    <ul class="ref-list">
      <li><span class="ref-num">[1]</span>
        <strong>Eshelby, J.D. (1957)</strong> — The determination of the elastic field of an
        ellipsoidal inclusion, and related problems.
        <em>Proc. R. Soc. London A</em>, 241, 376–396.
      </li>
      <li><span class="ref-num">[2]</span>
        <strong>Mori, T. &amp; Tanaka, K. (1973)</strong> — Average stress in matrix and
        average elastic energy of materials with misfitting inclusions.
        <em>Acta Metallurgica</em>, 21(5), 571–574.
      </li>
      <li><span class="ref-num">[3]</span>
        <strong>Hervé, E. &amp; Zaoui, A. (1993)</strong> — n-layered inclusion-based
        micromechanical modelling. <em>Int. J. Eng. Sci.</em>, 31(1), 1–10.
      </li>
      <li><span class="ref-num">[4]</span>
        <strong>Barthélémy, J.-F. (2022)</strong> — <em>echoes: Extended Calculator of
        HOmogEnization Schemes</em>. Zenodo.
        <a href="https://doi.org/10.5281/zenodo.14959866">doi:10.5281/zenodo.14959866</a> —
        <a href="https://jfbarthelemy.github.io/echoes">Online Documentation</a>
      </li>
    </ul>
  </div>

</div><!-- /en -->

<!-- ═══════════════════════════════ FOOTER ════════════════════════════════ -->
<footer>
  <strong>HOUNKPE Mawulikplimi Roland</strong> · Master Physique Théorique · Université de Lomé · 2023–2025<br>
  <span style="margin-top:6px; display:block; opacity:.6">
    Supervisé par Dr. A. Adessina (Cerema – Univ. Gustave Eiffel) &amp; Prof. K. N'Wuitcha (UL)
  </span>
</footer>

</body>
</html>