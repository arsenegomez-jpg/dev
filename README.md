<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Resto Presto – Paris 9e</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,700;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --rouge: #c0392b;
    --or: #e2a84b;
    --noir: #111;
    --creme: #fdf6ec;
    --gris: #555;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--creme);
    color: var(--noir);
    overflow-x: hidden;
  }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    background: var(--noir);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    position: relative;
    overflow: hidden;
    padding: 2rem;
  }

  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse at 60% 40%, rgba(192,57,43,0.25) 0%, transparent 60%),
                radial-gradient(ellipse at 20% 80%, rgba(226,168,75,0.15) 0%, transparent 50%);
  }

  .hero-badge {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.7rem;
    font-weight: 500;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--or);
    border: 1px solid rgba(226,168,75,0.4);
    padding: 0.4rem 1.2rem;
    border-radius: 100px;
    margin-bottom: 2rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.2s forwards;
  }

  .hero h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(3.5rem, 10vw, 8rem);
    color: #fff;
    line-height: 0.95;
    letter-spacing: -0.02em;
    opacity: 0;
    animation: fadeUp 0.8s 0.4s forwards;
  }

  .hero h1 em {
    font-style: italic;
    color: var(--or);
  }

  .hero-sub {
    margin-top: 1.5rem;
    font-size: 1rem;
    color: rgba(255,255,255,0.5);
    font-weight: 300;
    letter-spacing: 0.05em;
    opacity: 0;
    animation: fadeUp 0.8s 0.6s forwards;
  }

  .hero-info {
    margin-top: 3rem;
    display: flex;
    gap: 2rem;
    flex-wrap: wrap;
    justify-content: center;
    opacity: 0;
    animation: fadeUp 0.8s 0.8s forwards;
  }

  .hero-pill {
    background: rgba(255,255,255,0.07);
    border: 1px solid rgba(255,255,255,0.12);
    color: #fff;
    padding: 0.6rem 1.4rem;
    border-radius: 100px;
    font-size: 0.85rem;
    font-weight: 300;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .hero-pill span { color: var(--or); }

  .scroll-hint {
    position: absolute;
    bottom: 2.5rem;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.4rem;
    color: rgba(255,255,255,0.3);
    font-size: 0.7rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    animation: fadeUp 1s 1.2s forwards;
    opacity: 0;
  }

  .scroll-line {
    width: 1px;
    height: 40px;
    background: linear-gradient(to bottom, var(--or), transparent);
    animation: scrollPulse 2s infinite;
  }

  /* ── NAV ── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    padding: 1.2rem 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgba(17,17,17,0.85);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid rgba(255,255,255,0.05);
  }

  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.3rem;
    color: #fff;
    text-decoration: none;
  }

  .nav-logo em { color: var(--or); font-style: italic; }

  .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
  }

  .nav-links a {
    color: rgba(255,255,255,0.6);
    text-decoration: none;
    font-size: 0.85rem;
    font-weight: 400;
    letter-spacing: 0.05em;
    transition: color 0.2s;
  }

  .nav-links a:hover { color: var(--or); }

  /* ── SECTIONS ── */
  section { padding: 5rem 2rem; max-width: 900px; margin: 0 auto; }

  .section-label {
    font-size: 0.7rem;
    font-weight: 500;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--rouge);
    margin-bottom: 0.8rem;
  }

  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 5vw, 3.2rem);
    line-height: 1.1;
    margin-bottom: 2rem;
  }

  /* ── À PROPOS ── */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 3rem;
    align-items: center;
  }

  .about-text p {
    font-size: 1rem;
    line-height: 1.8;
    color: var(--gris);
    margin-bottom: 1rem;
  }

  .about-stats {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
  }

  .stat-box {
    background: var(--noir);
    color: #fff;
    padding: 1.5rem;
    border-radius: 12px;
    text-align: center;
  }

  .stat-num {
    font-family: 'Playfair Display', serif;
    font-size: 2.2rem;
    color: var(--or);
    display: block;
  }

  .stat-label {
    font-size: 0.75rem;
    color: rgba(255,255,255,0.5);
    letter-spacing: 0.1em;
    text-transform: uppercase;
  }

  /* ── MENU ── */
  #menu { background: var(--noir); max-width: 100%; padding: 5rem 2rem; }

  #menu > * { max-width: 900px; margin-left: auto; margin-right: auto; }

  #menu .section-title { color: #fff; }
  #menu .section-label { color: var(--or); }

  .menu-tabs {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
    margin-bottom: 2.5rem;
    max-width: 900px;
    margin-left: auto;
    margin-right: auto;
  }

  .tab-btn {
    background: rgba(255,255,255,0.07);
    border: 1px solid rgba(255,255,255,0.1);
    color: rgba(255,255,255,0.6);
    padding: 0.5rem 1.2rem;
    border-radius: 100px;
    font-size: 0.82rem;
    cursor: pointer;
    transition: all 0.2s;
    font-family: 'DM Sans', sans-serif;
  }

  .tab-btn.active, .tab-btn:hover {
    background: var(--rouge);
    border-color: var(--rouge);
    color: #fff;
  }

  .menu-category { display: none; max-width: 900px; margin: 0 auto; }
  .menu-category.active { display: block; }

  .menu-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 1px;
    background: rgba(255,255,255,0.06);
    border: 1px solid rgba(255,255,255,0.06);
    border-radius: 16px;
    overflow: hidden;
  }

  .menu-item {
    background: #1a1a1a;
    padding: 1.4rem 1.6rem;
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    gap: 1rem;
    transition: background 0.2s;
  }

  .menu-item:hover { background: #222; }

  .item-name {
    font-size: 0.92rem;
    font-weight: 500;
    color: #fff;
    margin-bottom: 0.2rem;
  }

  .item-desc {
    font-size: 0.75rem;
    color: rgba(255,255,255,0.35);
    line-height: 1.4;
  }

  .item-price {
    font-family: 'Playfair Display', serif;
    color: var(--or);
    font-size: 1rem;
    white-space: nowrap;
    flex-shrink: 0;
  }

  /* ── CONTACT ── */
  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 3rem;
  }

  .contact-info { display: flex; flex-direction: column; gap: 1.5rem; }

  .contact-item {
    display: flex;
    align-items: flex-start;
    gap: 1rem;
  }

  .contact-icon {
    width: 44px; height: 44px;
    background: var(--rouge);
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.1rem;
    flex-shrink: 0;
  }

  .contact-item h4 {
    font-size: 0.75rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--gris);
    margin-bottom: 0.3rem;
  }

  .contact-item p { font-size: 0.95rem; font-weight: 500; }

  .contact-item a { color: var(--noir); text-decoration: none; }
  .contact-item a:hover { color: var(--rouge); }

  .map-placeholder {
    background: var(--noir);
    border-radius: 16px;
    height: 280px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 1rem;
    color: rgba(255,255,255,0.4);
    font-size: 0.85rem;
    text-align: center;
    padding: 2rem;
  }

  .map-placeholder .map-icon { font-size: 2.5rem; }

  .btn-maps {
    display: inline-block;
    margin-top: 0.5rem;
    background: var(--rouge);
    color: #fff;
    padding: 0.7rem 1.6rem;
    border-radius: 100px;
    text-decoration: none;
    font-size: 0.85rem;
    font-weight: 500;
    transition: background 0.2s;
  }

  .btn-maps:hover { background: #a93226; }

  /* ── FOOTER ── */
  footer {
    background: var(--noir);
    color: rgba(255,255,255,0.4);
    text-align: center;
    padding: 2rem;
    font-size: 0.8rem;
  }

  footer strong { color: var(--or); }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @keyframes scrollPulse {
    0%, 100% { opacity: 0.3; }
    50%       { opacity: 1; }
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 640px) {
    .about-grid, .contact-grid { grid-template-columns: 1fr; }
    .nav-links { display: none; }
    .hero h1 { font-size: 3.2rem; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">Resto <em>Presto</em></a>
  <ul class="nav-links">
    <li><a href="#apropos">À propos</a></li>
    <li><a href="#menu">Menu</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<div class="hero">
  <div class="hero-badge">⭐ 4,6 · Paris 9e</div>
  <h1>Resto<br><em>Presto</em></h1>
  <p class="hero-sub">Kebabs · Burgers · Crêpes · Assiettes</p>
  <div class="hero-info">
    <div class="hero-pill"><span>🕐</span> Ouvert jusqu'à 01h00</div>
    <div class="hero-pill"><span>📍</span> 16 Rue Marguerite de Rochechouart</div>
    <div class="hero-pill"><span>💶</span> À partir de 1€</div>
  </div>
  <div class="scroll-hint">
    <div class="scroll-line"></div>
    Découvrir
  </div>
</div>

<!-- À PROPOS -->
<section id="apropos">
  <p class="section-label">Notre histoire</p>
  <div class="section-title">Un resto de quartier<br>avec du caractère</div>
  <div class="about-grid">
    <div class="about-text">
      <p>Au cœur du 9e arrondissement, Resto Presto vous accueille chaque jour avec une carte généreuse et des saveurs qui font le bonheur du quartier.</p>
      <p>Kebabs maison, burgers smash, crêpes généreuses, assiettes copieuses… De quoi satisfaire toutes les envies, à toute heure.</p>
    </div>
    <div class="about-stats">
      <div class="stat-box"><span class="stat-num">4,6</span><span class="stat-label">Note Google</span></div>
      <div class="stat-box"><span class="stat-num">01h</span><span class="stat-label">Fermeture</span></div>
      <div class="stat-box"><span class="stat-num">1€</span><span class="stat-label">À partir de</span></div>
      <div class="stat-box"><span class="stat-num">9e</span><span class="stat-label">Paris</span></div>
    </div>
  </div>
</section>

<!-- MENU -->
<div id="menu">
  <p class="section-label">Ce qu'on propose</p>
  <div class="section-title">Notre carte</div>

  <div class="menu-tabs">
    <button class="tab-btn active" onclick="showTab('sandwichs')">🥙 Sandwichs</button>
    <button class="tab-btn" onclick="showTab('burgers')">🍔 Burgers</button>
    <button class="tab-btn" onclick="showTab('assiettes')">🍽️ Assiettes</button>
    <button class="tab-btn" onclick="showTab('crepes')">🥞 Crêpes</button>
    <button class="tab-btn" onclick="showTab('boissons')">☕ Boissons</button>
    <button class="tab-btn" onclick="showTab('desserts')">🍮 Desserts</button>
  </div>

  <div class="menu-category active" id="sandwichs">
    <div class="menu-grid">
      <div class="menu-item"><div><div class="item-name">Kebab</div><div class="item-desc">Viande kebab maison</div></div><div class="item-price">9,90€</div></div>
      <div class="menu-item"><div><div class="item-name">Tandoori</div><div class="item-desc">Blanc de poulet mariné aux épices indiennes</div></div><div class="item-price">9,90€</div></div>
      <div class="menu-item"><div><div class="item-name">Curry</div><div class="item-desc">Blanc de poulet mariné au curry</div></div><div class="item-price">9,90€</div></div>
      <div class="menu-item"><div><div class="item-name">Suprême</div><div class="item-desc">Blanc de poulet, yaourt porté, cheddar</div></div><div class="item-price">9,90€</div></div>
      <div class="menu-item"><div><div class="item-name">Mixte</div><div class="item-desc">Kefta + poulet suprême</div></div><div class="item-price">9,90€</div></div>
      <div class="menu-item"><div><div class="item-name">Kefta</div><div class="item-desc">Viande hachée marinée aux épices</div></div><div class="item-price">9,90€</div></div>
      <div class="menu-item"><div><div class="item-name">Bavette</div><div class="item-desc">Pièce du boucher marinée</div></div><div class="item-price">11,90€</div></div>
    </div>
  </div>

  <div class="menu-category" id="burgers">
    <div class="menu-grid">
      <div class="menu-item"><div><div class="item-name">Double Smash</div><div class="item-desc">2 steaks + oignon + cornichon + sauce heure blanc</div></div><div class="item-price">–</div></div>
      <div class="menu-item"><div><div class="item-name">Le Buffalo</div><div class="item-desc">2 steaks + sauce fumée + salade tomate</div></div><div class="item-price">–</div></div>
      <div class="menu-item"><div><div class="item-name">Le Montagnard</div><div class="item-desc">2 steaks + fromage raclette + bacon + sauce montagnard + aubergine</div></div><div class="item-price">–</div></div>
      <div class="menu-item"><div><div class="item-name">Végétarien</div><div class="item-desc">Galette PDT ou aubergine + cheddar + sauce montagnard</div></div><div class="item-price">–</div></div>
      <div class="menu-item"><div><div class="item-name">Menu Enfants – Nuggets</div><div class="item-desc">Nuggets de poulet + Capri-Sun + Pom'potes + frites maison</div></div><div class="item-price">5,50€</div></div>
      <div class="menu-item"><div><div class="item-name">Menu Enfants – Mini Smash</div><div class="item-desc">Mini burger + Capri-Sun + Pom'potes + frites maison</div></div><div class="item-price">5,50€</div></div>
    </div>
  </div>

  <div class="menu-category" id="assiettes">
    <div class="menu-grid">
      <div class="menu-item"><div><div class="item-name">Assiette Poulet ou Kebab</div><div class="item-desc">Accompagnements inclus</div></div><div class="item-price">12€</div></div>
      <div class="menu-item"><div><div class="item-name">Assiette Bavette</div><div class="item-desc">Pièce du boucher marinée</div></div><div class="item-price">13€</div></div>
      <div class="menu-item"><div><div class="item-name">Panini Tomate-Mozza</div><div class="item-desc">Tomate fraîche, mozzarella fondante</div></div><div class="item-price">9,50€ / 10,90€</div></div>
      <div class="menu-item"><div><div class="item-name">Panini Thon</div><div class="item-desc">Thon, légumes</div></div><div class="item-price">9,50€ / 10,90€</div></div>
      <div class="menu-item"><div><div class="item-name">Panini Kebab</div><div class="item-desc">Viande kebab, sauce maison</div></div><div class="item-price">9,50€ / 10,90€</div></div>
    </div>
  </div>

  <div class="menu-category" id="crepes">
    <div class="menu-grid">
      <div class="menu-item"><div><div class="item-name">Crêpe Nutella</div><div class="item-desc">Crêpe sucrée au Nutella</div></div><div class="item-price">3,50€</div></div>
      <div class="menu-item"><div><div class="item-name">Suppléments crêpe</div><div class="item-desc">Banane, Kinder, sucre, miel, confiture, coco, amandes, spéculoos, châtaigne…</div></div><div class="item-price">0,60€</div></div>
      <div class="menu-item"><div><div class="item-name">Crêpe Œuf Fromage</div><div class="item-desc">Crêpe salée</div></div><div class="item-price">6,50€</div></div>
      <div class="menu-item"><div><div class="item-name">Crêpe Œuf Thon</div><div class="item-desc">Crêpe salée</div></div><div class="item-price">6,50€</div></div>
      <div class="menu-item"><div><div class="item-name">Crêpe Œuf Jambon</div><div class="item-desc">Dinde ou poulet</div></div><div class="item-price">6,50€</div></div>
    </div>
  </div>

  <div class="menu-category" id="boissons">
    <div class="menu-grid">
      <div class="menu-item"><div><div class="item-name">Café</div></div><div class="item-price">1€</div></div>
      <div class="menu-item"><div><div class="item-name">Cappuccino</div></div><div class="item-price">3€</div></div>
      <div class="menu-item"><div><div class="item-name">Thé / Tisane</div></div><div class="item-price">3€</div></div>
      <div class="menu-item"><div><div class="item-name">Boisson</div></div><div class="item-price">2€</div></div>
      <div class="menu-item"><div><div class="item-name">Eau</div></div><div class="item-price">1,50€</div></div>
      <div class="menu-item"><div><div class="item-name">Capri-Sun</div></div><div class="item-price">1€</div></div>
      <div class="menu-item"><div><div class="item-name">Pom'potes</div></div><div class="item-price">1€</div></div>
      <div class="menu-item"><div><div class="item-name">Jus frais minute</div><div class="item-desc">Fait maison</div></div><div class="item-price">3,50€</div></div>
    </div>
  </div>

  <div class="menu-category" id="desserts">
    <div class="menu-grid">
      <div class="menu-item"><div><div class="item-name">Tiramisu</div></div><div class="item-price">3,50€</div></div>
      <div class="menu-item"><div><div class="item-name">Moelleux au chocolat</div></div><div class="item-price">3,50€</div></div>
      <div class="menu-item"><div><div class="item-name">Tarte Daim</div></div><div class="item-price">3,80€</div></div>
    </div>
  </div>
</div>

<!-- CONTACT -->
<section id="contact">
  <p class="section-label">Nous trouver</p>
  <div class="section-title">Venez nous rendre visite</div>
  <div class="contact-grid">
    <div class="contact-info">
      <div class="contact-item">
        <div class="contact-icon">📍</div>
        <div>
          <h4>Adresse</h4>
          <p>16 Rue Marguerite de Rochechouart<br>75009 Paris</p>
        </div>
      </div>
      <div class="contact-item">
        <div class="contact-icon">📞</div>
        <div>
          <h4>Téléphone</h4>
          <p><a href="tel:+33140380178">01 40 38 01 78</a></p>
        </div>
      </div>
      <div class="contact-item">
        <div class="contact-icon">🕐</div>
        <div>
          <h4>Horaires</h4>
          <p>Ouvert · Ferme à 01h00</p>
        </div>
      </div>
      <div class="contact-item">
        <div class="contact-icon">⭐</div>
        <div>
          <h4>Note Google</h4>
          <p>4,6 / 5 · Très bien noté</p>
        </div>
      </div>
    </div>
    <div class="map-placeholder">
      <div class="map-icon">🗺️</div>
      <p>16 Rue Marguerite de Rochechouart<br>75009 Paris</p>
      <a class="btn-maps" href="https://maps.google.com/?q=16+Rue+Marguerite+de+Rochechouart+75009+Paris" target="_blank">Ouvrir dans Maps</a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <p>© 2025 <strong>Resto Presto</strong> · 16 Rue Marguerite de Rochechouart, Paris 9e · <a href="tel:+33140380178" style="color:inherit">01 40 38 01 78</a></p>
</footer>

<script>
  function showTab(id) {
    document.querySelectorAll('.menu-category').forEach(c => c.classList.remove('active'));
    document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
    document.getElementById(id).classList.add('active');
    event.target.classList.add('active');
  }
</script>
</body>
</html>