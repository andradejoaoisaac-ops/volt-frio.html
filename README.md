<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>VoltFrio Serviços | Elétrica & Ar Condicionado</title>
<link href="https://fonts.googleapis.com/css2?family=Barlow:wght@400;600;700;800&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --navy: #0A1628;
    --navy2: #112240;
    --amber: #F5A623;
    --amber2: #E8941A;
    --white: #FFFFFF;
    --light: #F0F4F8;
    --mid: #8A9BB0;
    --slate: #4A5A70;
    --ice: #E8EFF7;
    --success: #22C55E;
    --danger: #EF4444;
    box-sizing: border-box;
    padding-top: env(safe-area-inset-top, 0px);
    padding-bottom: env(safe-area-inset-bottom, 0px);
  }
  *, *::before, *::after { box-sizing: inherit; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; scroll-padding-top: 80px; }
  body { font-family: 'Inter', sans-serif; background: var(--navy); color: var(--white); overflow-x: hidden; }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    background: rgba(10,22,40,0.95); backdrop-filter: blur(12px);
    border-bottom: 1px solid rgba(245,166,35,0.15);
    height: 70px; display: flex; align-items: center;
    padding: 0 5vw;
  }
  .nav-inner { width: 100%; max-width: 1200px; margin: 0 auto; display: flex; align-items: center; justify-content: space-between; }
  .logo { font-family: 'Barlow', sans-serif; font-weight: 800; font-size: 1.5rem; color: var(--white); text-decoration: none; display: flex; align-items: center; gap: 8px; }
  .logo span { color: var(--amber); }
  .logo-bolt { font-size: 1.3rem; }
  .nav-links { display: flex; align-items: center; gap: 28px; list-style: none; }
  .nav-links a { color: var(--mid); text-decoration: none; font-size: 0.875rem; font-weight: 500; transition: color .2s; }
  .nav-links a:hover { color: var(--amber); }
  .nav-cta { background: var(--amber); color: var(--navy); padding: 9px 20px; border-radius: 6px; font-weight: 700; font-size: 0.85rem; text-decoration: none; transition: background .2s; white-space: nowrap; }
  .nav-cta:hover { background: var(--amber2); color: var(--navy) !important; }
  .hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; padding: 4px; }
  .hamburger span { display: block; width: 24px; height: 2px; background: var(--white); border-radius: 2px; }
  .mobile-menu { display: none; position: fixed; top: 70px; left: 0; right: 0; background: var(--navy2); border-bottom: 1px solid rgba(245,166,35,0.2); padding: 20px 5vw; z-index: 99; flex-direction: column; gap: 16px; }
  .mobile-menu.open { display: flex; }
  .mobile-menu a { color: var(--mid); text-decoration: none; font-size: 1rem; padding: 8px 0; border-bottom: 1px solid rgba(255,255,255,0.05); font-weight: 500; }
  .mobile-menu a:hover { color: var(--amber); }

  /* HERO */
  .hero {
    min-height: 100vh; padding-top: 70px;
    display: flex; align-items: center;
    background: var(--navy);
    position: relative; overflow: hidden;
  }
  .hero-grid {
    position: absolute; inset: 0;
    background-image: linear-gradient(rgba(245,166,35,0.04) 1px, transparent 1px), linear-gradient(90deg, rgba(245,166,35,0.04) 1px, transparent 1px);
    background-size: 60px 60px;
  }
  .hero-glow { position: absolute; top: -200px; right: -200px; width: 600px; height: 600px; background: radial-gradient(circle, rgba(245,166,35,0.12) 0%, transparent 70%); pointer-events: none; }
  .hero-inner { position: relative; z-index: 2; max-width: 1200px; margin: 0 auto; padding: 80px 5vw; display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: center; }
  .hero-badge { display: inline-flex; align-items: center; gap: 8px; background: rgba(245,166,35,0.1); border: 1px solid rgba(245,166,35,0.3); padding: 6px 14px; border-radius: 20px; font-size: 0.75rem; font-weight: 600; color: var(--amber); letter-spacing: 0.05em; margin-bottom: 24px; }
  .hero-badge::before { content: '●'; font-size: 0.5rem; animation: pulse 2s infinite; }
  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.3} }
  .hero h1 { font-family: 'Barlow', sans-serif; font-size: clamp(2.4rem,5vw,3.8rem); font-weight: 800; line-height: 1.1; margin-bottom: 20px; }
  .hero h1 em { font-style: normal; color: var(--amber); }
  .hero p { color: var(--mid); font-size: 1.05rem; line-height: 1.7; margin-bottom: 36px; max-width: 480px; }
  .hero-btns { display: flex; gap: 14px; flex-wrap: wrap; }
  .btn-primary { background: var(--amber); color: var(--navy); padding: 14px 28px; border-radius: 8px; font-weight: 700; font-size: 0.95rem; text-decoration: none; border: none; cursor: pointer; transition: background .2s, transform .15s; display: inline-block; }
  .btn-primary:hover { background: var(--amber2); transform: translateY(-1px); }
  .btn-secondary { background: transparent; color: var(--white); padding: 14px 28px; border-radius: 8px; font-weight: 600; font-size: 0.95rem; border: 1.5px solid rgba(255,255,255,0.2); cursor: pointer; text-decoration: none; transition: border-color .2s, color .2s; display: inline-block; }
  .btn-secondary:hover { border-color: var(--amber); color: var(--amber); }
  .hero-stats { display: grid; grid-template-columns: repeat(3,1fr); gap: 16px; }
  .stat-card { background: var(--navy2); border: 1px solid rgba(255,255,255,0.07); border-radius: 12px; padding: 20px 16px; border-left: 3px solid var(--amber); }
  .stat-num { font-family: 'Barlow', sans-serif; font-size: 2rem; font-weight: 800; color: var(--amber); }
  .stat-label { font-size: 0.78rem; color: var(--mid); margin-top: 4px; line-height: 1.4; }

  /* SECTIONS COMMON */
  section { padding: 90px 5vw; }
  .section-inner { max-width: 1200px; margin: 0 auto; }
  .section-tag { display: inline-block; font-size: 0.75rem; font-weight: 700; color: var(--amber); letter-spacing: 0.1em; margin-bottom: 12px; text-transform: uppercase; }
  .section-title { font-family: 'Barlow', sans-serif; font-size: clamp(1.8rem,3.5vw,2.6rem); font-weight: 800; line-height: 1.2; margin-bottom: 16px; }
  .section-sub { color: var(--mid); font-size: 1rem; line-height: 1.7; max-width: 560px; }

  /* SERVICES */
  #servicos { background: var(--navy2); }
  .services-header { display: flex; justify-content: space-between; align-items: flex-end; margin-bottom: 50px; flex-wrap: wrap; gap: 20px; }
  .services-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px,1fr)); gap: 20px; }
  .service-card {
    background: var(--navy); border: 1px solid rgba(255,255,255,0.06);
    border-radius: 14px; padding: 28px 24px;
    border-left: 4px solid var(--amber);
    transition: transform .2s, border-color .2s, box-shadow .2s;
    cursor: default;
  }
  .service-card:hover { transform: translateY(-3px); box-shadow: 0 12px 40px rgba(0,0,0,0.3); border-color: var(--amber); }
  .service-icon { font-size: 2rem; margin-bottom: 14px; }
  .service-name { font-family: 'Barlow', sans-serif; font-size: 1.1rem; font-weight: 700; margin-bottom: 8px; }
  .service-desc { color: var(--mid); font-size: 0.88rem; line-height: 1.6; margin-bottom: 16px; }
  .service-price { font-size: 0.82rem; color: var(--amber); font-weight: 600; background: rgba(245,166,35,0.08); padding: 4px 10px; border-radius: 4px; display: inline-block; }

  /* COMO FUNCIONA */
  #como-funciona { background: var(--navy); }
  .steps { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px,1fr)); gap: 24px; margin-top: 50px; }
  .step { text-align: center; padding: 30px 20px; }
  .step-num { width: 48px; height: 48px; border-radius: 12px; background: rgba(245,166,35,0.1); border: 2px solid var(--amber); display: flex; align-items: center; justify-content: center; font-family: 'Barlow', sans-serif; font-weight: 800; font-size: 1.1rem; color: var(--amber); margin: 0 auto 16px; }
  .step h3 { font-family: 'Barlow', sans-serif; font-weight: 700; margin-bottom: 8px; font-size: 1rem; }
  .step p { color: var(--mid); font-size: 0.85rem; line-height: 1.6; }
  .step-connector { display: flex; align-items: center; justify-content: center; padding-top: 24px; color: rgba(245,166,35,0.3); font-size: 1.5rem; }

  /* AGENDA / ORÇAMENTO */
  #agendar { background: var(--navy2); }
  .agenda-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; margin-top: 50px; }
  .form-panel { background: var(--navy); border: 1px solid rgba(255,255,255,0.07); border-radius: 16px; padding: 32px; }
  .form-panel h3 { font-family: 'Barlow', sans-serif; font-weight: 700; font-size: 1.3rem; margin-bottom: 6px; }
  .form-panel .fpd { color: var(--mid); font-size: 0.85rem; margin-bottom: 24px; }
  .form-group { margin-bottom: 18px; }
  .form-group label { display: block; font-size: 0.8rem; font-weight: 600; color: var(--mid); margin-bottom: 6px; letter-spacing: 0.03em; }
  .form-group input, .form-group select, .form-group textarea {
    width: 100%; background: rgba(255,255,255,0.04); border: 1.5px solid rgba(255,255,255,0.1);
    border-radius: 8px; padding: 11px 14px; color: var(--white); font-family: 'Inter', sans-serif;
    font-size: 0.9rem; outline: none; transition: border-color .2s;
  }
  .form-group input:focus, .form-group select:focus, .form-group textarea:focus { border-color: var(--amber); }
  .form-group textarea { resize: vertical; min-height: 90px; }
  .form-group select option { background: var(--navy2); color: var(--white); }
  .form-group input::placeholder, .form-group textarea::placeholder { color: var(--slate); }
  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; }
  .btn-full { width: 100%; padding: 13px; font-size: 0.95rem; border-radius: 8px; }

  /* ORÇAMENTO MODAL */
  .orcamento-trigger { text-align: center; margin-top: 16px; }
  .orcamento-trigger a { color: var(--amber); font-size: 0.85rem; text-decoration: underline; cursor: pointer; }
  .modal-overlay {
    display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.75);
    z-index: 200; align-items: center; justify-content: center; padding: 20px;
    backdrop-filter: blur(4px);
  }
  .modal-overlay.open { display: flex; }
  .modal { background: var(--navy2); border: 1px solid rgba(245,166,35,0.2); border-radius: 18px; padding: 36px; max-width: 560px; width: 100%; max-height: 85vh; overflow-y: auto; position: relative; }
  .modal h2 { font-family: 'Barlow', sans-serif; font-weight: 800; font-size: 1.5rem; margin-bottom: 6px; }
  .modal .modal-sub { color: var(--mid); font-size: 0.85rem; margin-bottom: 28px; }
  .modal-close { position: absolute; top: 16px; right: 20px; background: none; border: none; color: var(--mid); font-size: 1.4rem; cursor: pointer; line-height: 1; }
  .modal-close:hover { color: var(--white); }
  .service-checklist { display: flex; flex-direction: column; gap: 10px; margin-bottom: 24px; }
  .check-item { display: flex; align-items: flex-start; gap: 12px; background: rgba(255,255,255,0.03); border: 1.5px solid rgba(255,255,255,0.07); border-radius: 10px; padding: 14px 16px; cursor: pointer; transition: border-color .2s, background .2s; }
  .check-item:hover { border-color: var(--amber); background: rgba(245,166,35,0.05); }
  .check-item.selected { border-color: var(--amber); background: rgba(245,166,35,0.08); }
  .check-item input[type=checkbox] { accent-color: var(--amber); width: 18px; height: 18px; margin-top: 1px; flex-shrink: 0; cursor: pointer; }
  .check-item-info { flex: 1; }
  .check-item-name { font-weight: 600; font-size: 0.9rem; margin-bottom: 2px; }
  .check-item-price { font-size: 0.78rem; color: var(--amber); }
  .orcamento-footer { display: flex; gap: 12px; }
  .orcamento-footer .btn-primary { flex: 1; }
  .success-banner { display: none; background: rgba(34,197,94,0.1); border: 1px solid rgba(34,197,94,0.3); border-radius: 10px; padding: 16px 20px; color: #86efac; font-size: 0.9rem; line-height: 1.6; margin-top: 16px; align-items: flex-start; gap: 10px; }
  .success-banner.show { display: flex; }
  .success-icon { font-size: 1.2rem; margin-top: 1px; }

  /* CONTATO */
  #contato { background: var(--navy); }
  .contato-grid { display: grid; grid-template-columns: 1fr 1.5fr; gap: 60px; margin-top: 50px; align-items: start; }
  .contato-info { display: flex; flex-direction: column; gap: 24px; }
  .contact-item { display: flex; gap: 16px; align-items: flex-start; }
  .contact-icon { width: 44px; height: 44px; background: rgba(245,166,35,0.1); border-radius: 10px; display: flex; align-items: center; justify-content: center; font-size: 1.2rem; flex-shrink: 0; border: 1px solid rgba(245,166,35,0.2); }
  .contact-item h4 { font-weight: 600; font-size: 0.9rem; margin-bottom: 4px; }
  .contact-item p, .contact-item a { color: var(--mid); font-size: 0.85rem; text-decoration: none; }
  .contact-item a:hover { color: var(--amber); }
  .whatsapp-btn { display: flex; align-items: center; gap: 10px; background: #22c55e; color: #fff; padding: 14px 24px; border-radius: 10px; text-decoration: none; font-weight: 700; font-size: 0.95rem; transition: background .2s; margin-top: 8px; justify-content: center; }
  .whatsapp-btn:hover { background: #16a34a; }

  /* CHAT FLUTUANTE */
  .chat-fab {
    position: fixed; bottom: 28px; right: 28px; z-index: 150;
    width: 58px; height: 58px; background: var(--amber); border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    cursor: pointer; box-shadow: 0 8px 24px rgba(245,166,35,0.4);
    font-size: 1.6rem; border: none; transition: transform .2s, box-shadow .2s;
  }
  .chat-fab:hover { transform: scale(1.08); box-shadow: 0 12px 32px rgba(245,166,35,0.5); }
  .chat-bubble {
    display: none; position: fixed; bottom: 100px; right: 28px; z-index: 149;
    background: var(--navy2); border: 1px solid rgba(245,166,35,0.2);
    border-radius: 16px; width: 320px; box-shadow: 0 16px 48px rgba(0,0,0,0.5);
    overflow: hidden;
  }
  .chat-bubble.open { display: block; }
  .chat-header { background: var(--amber); padding: 14px 18px; display: flex; align-items: center; gap: 12px; }
  .chat-avatar { width: 36px; height: 36px; background: var(--navy); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 1.1rem; }
  .chat-header h4 { font-family: 'Barlow', sans-serif; font-weight: 700; color: var(--navy); font-size: 0.95rem; }
  .chat-header p { font-size: 0.72rem; color: rgba(10,22,40,0.7); }
  .chat-close { margin-left: auto; background: none; border: none; cursor: pointer; color: var(--navy); font-size: 1.2rem; }
  .chat-msgs { padding: 16px; min-height: 180px; max-height: 240px; overflow-y: auto; display: flex; flex-direction: column; gap: 10px; }
  .chat-msg { padding: 10px 14px; border-radius: 12px; font-size: 0.85rem; line-height: 1.5; max-width: 88%; }
  .chat-msg.agent { background: rgba(255,255,255,0.06); color: var(--white); align-self: flex-start; }
  .chat-msg.user { background: var(--amber); color: var(--navy); align-self: flex-end; font-weight: 500; }
  .chat-input-row { display: flex; gap: 8px; padding: 12px 16px; border-top: 1px solid rgba(255,255,255,0.06); }
  .chat-input-row input { flex: 1; background: rgba(255,255,255,0.05); border: 1px solid rgba(255,255,255,0.1); border-radius: 8px; padding: 9px 12px; color: var(--white); font-size: 0.85rem; outline: none; }
  .chat-input-row input:focus { border-color: var(--amber); }
  .chat-send { background: var(--amber); border: none; border-radius: 8px; width: 36px; height: 36px; cursor: pointer; font-size: 1rem; display: flex; align-items: center; justify-content: center; color: var(--navy); transition: background .2s; flex-shrink: 0; }
  .chat-send:hover { background: var(--amber2); }

  /* FOOTER */
  footer { background: rgba(0,0,0,0.4); border-top: 1px solid rgba(255,255,255,0.06); padding: 40px 5vw; }
  .footer-inner { max-width: 1200px; margin: 0 auto; display: flex; justify-content: space-between; align-items: center; gap: 24px; flex-wrap: wrap; }
  .footer-copy { color: var(--slate); font-size: 0.8rem; }
  .footer-links { display: flex; gap: 20px; }
  .footer-links a { color: var(--slate); font-size: 0.8rem; text-decoration: none; }
  .footer-links a:hover { color: var(--amber); }

  /* URGENCIA BANNER */
  .urgencia-bar { background: linear-gradient(90deg, var(--amber) 0%, #ff8c00 100%); padding: 10px 5vw; text-align: center; }
  .urgencia-bar p { color: var(--navy); font-size: 0.82rem; font-weight: 700; }
  .urgencia-bar a { color: var(--navy); text-decoration: underline; }

  /* RESPONSIVE */
  @media (max-width: 900px) {
    .hero-inner { grid-template-columns: 1fr; }
    .hero-stats { grid-template-columns: repeat(3,1fr); }
    .agenda-grid { grid-template-columns: 1fr; }
    .contato-grid { grid-template-columns: 1fr; }
    .nav-links, nav .nav-cta { display: none; }
    .hamburger { display: flex; }
    .services-header { flex-direction: column; align-items: flex-start; }
  }
  @media (max-width: 600px) {
    .hero-stats { grid-template-columns: 1fr 1fr; }
    .stat-card:last-child { grid-column: span 2; }
    .form-row { grid-template-columns: 1fr; }
    .orcamento-footer { flex-direction: column; }
    .chat-bubble { width: calc(100vw - 40px); right: 20px; }
    .chat-fab { right: 20px; bottom: 20px; }
  }
</style>
</head>
<body>

<!-- URGÊNCIA -->
<div class="urgencia-bar">
  <p>⚡ Emergências 24h: <a href="tel:+5500000000000">(00) 00000-0000</a> — Atendimento rápido em toda a região</p>
</div>

<!-- NAV -->
<nav>
  <div class="nav-inner">
    <a href="#" class="logo"><span class="logo-bolt">⚡</span>Volt<span>Frio</span></a>
    <ul class="nav-links">
      <li><a href="#servicos">Serviços</a></li>
      <li><a href="#como-funciona">Como Funciona</a></li>
      <li><a href="#agendar">Agendar</a></li>
      <li><a href="#contato">Contato</a></li>
    </ul>
    <a href="#" class="nav-cta" onclick="openOrcamento(); return false;">Solicitar Orçamento</a>
    <div class="hamburger" onclick="toggleMobile()">
      <span></span><span></span><span></span>
    </div>
  </div>
</nav>

<div class="mobile-menu" id="mobileMenu">
  <a href="#servicos" onclick="toggleMobile()">Serviços</a>
  <a href="#como-funciona" onclick="toggleMobile()">Como Funciona</a>
  <a href="#agendar" onclick="toggleMobile()">Agendar</a>
  <a href="#contato" onclick="toggleMobile()">Contato</a>
  <a href="#" onclick="openOrcamento(); toggleMobile(); return false;" style="color:var(--amber); font-weight:700;">⚡ Solicitar Orçamento</a>
</div>

<!-- HERO -->
<section class="hero" id="inicio">
  <div class="hero-grid"></div>
  <div class="hero-glow"></div>
  <div class="hero-inner">
    <div>
      <div class="hero-badge">Disponível agora — Atendimento imediato</div>
      <h1>Elétrica & Ar Condicionado<br><em>com quem entende</em></h1>
      <p>Instalações, manutenções e reparos residenciais e comerciais. Técnicos certificados, orçamento sem custo e agendamento online em minutos.</p>
      <div class="hero-btns">
        <a href="#" class="btn-primary" onclick="openOrcamento(); return false;">⚡ Solicitar Orçamento</a>
        <a href="#agendar" class="btn-secondary">Agendar Visita</a>
      </div>
    </div>
    <div class="hero-stats">
      <div class="stat-card">
        <div class="stat-num">+850</div>
        <div class="stat-label">Clientes atendidos</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">12+</div>
        <div class="stat-label">Anos de experiência</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">24h</div>
        <div class="stat-label">Emergências</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">4.9★</div>
        <div class="stat-label">Avaliação média</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">2h</div>
        <div class="stat-label">Tempo médio de resposta</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">100%</div>
        <div class="stat-label">Garantia no serviço</div>
      </div>
    </div>
  </div>
</section>

<!-- SERVIÇOS -->
<section id="servicos">
  <div class="section-inner">
    <div class="services-header">
      <div>
        <span class="section-tag">O que fazemos</span>
        <h2 class="section-title">Tabela de Serviços</h2>
        <p class="section-sub">Preços base por categoria. O valor final é confirmado após avaliação técnica gratuita no local.</p>
      </div>
      <a href="#" class="btn-primary" onclick="openOrcamento(); return false;">Montar Orçamento →</a>
    </div>
    <div class="services-grid">
      <div class="service-card">
        <div class="service-icon">🔌</div>
        <div class="service-name">Instalação Elétrica</div>
        <div class="service-desc">Quadros de distribuição, tomadas, interruptores, fiação nova e revisão completa de instalações residenciais e comerciais.</div>
        <span class="service-price">A partir de R$ 150</span>
      </div>
      <div class="service-card">
        <div class="service-icon">🌡️</div>
        <div class="service-name">Instalação de Ar Condicionado</div>
        <div class="service-desc">Instalação de split, multi-split e janeleiro. Inclui suporte, tubulação e configuração completa.</div>
        <span class="service-price">A partir de R$ 280</span>
      </div>
      <div class="service-card">
        <div class="service-icon">🔧</div>
        <div class="service-name">Manutenção Preventiva de AC</div>
        <div class="service-desc">Limpeza de filtros, verificação de gás, limpeza de serpentinas e relatório técnico completo.</div>
        <span class="service-price">A partir de R$ 120</span>
      </div>
      <div class="service-card">
        <div class="service-icon">❄️</div>
        <div class="service-name">Recarga de Gás (AC)</div>
        <div class="service-desc">Recarga de fluido refrigerante R-22, R-410A e R-32. Teste de vazamento incluso.</div>
        <span class="service-price">A partir de R$ 180</span>
      </div>
      <div class="service-card">
        <div class="service-icon">⚡</div>
        <div class="service-name">Laudos e SPDA</div>
        <div class="service-desc">Laudo técnico elétrico (NR-10), instalação e manutenção de para-raios e sistemas de aterramento.</div>
        <span class="service-price">A partir de R$ 350</span>
      </div>
      <div class="service-card">
        <div class="service-icon">🔦</div>
        <div class="service-name">Iluminação LED</div>
        <div class="service-desc">Projeto e instalação de iluminação LED residencial, comercial e outdoor. Economia garantida na conta.</div>
        <span class="service-price">A partir de R$ 200</span>
      </div>
      <div class="service-card">
        <div class="service-icon">🏭</div>
        <div class="service-name">Elétrica Industrial</div>
        <div class="service-desc">Quadros de comando, CLP, motores elétricos, automação e manutenção de máquinas industriais.</div>
        <span class="service-price">Sob consulta</span>
      </div>
      <div class="service-card">
        <div class="service-icon">🚨</div>
        <div class="service-name">Emergência 24h</div>
        <div class="service-desc">Curto-circuito, cheiro de queimado, disjuntor desarmando, AC parando. Atendimento no mesmo dia.</div>
        <span class="service-price">A partir de R$ 200</span>
      </div>
    </div>
  </div>
</section>

<!-- COMO FUNCIONA -->
<section id="como-funciona">
  <div class="section-inner">
    <div style="text-align:center; margin-bottom: 0;">
      <span class="section-tag">Processo</span>
      <h2 class="section-title">Como Funciona o Atendimento</h2>
      <p class="section-sub" style="margin: 0 auto;">Da solicitação até a conclusão do serviço em passos simples.</p>
    </div>
    <div class="steps">
      <div class="step">
        <div class="step-num">1</div>
        <h3>Solicite o Orçamento</h3>
        <p>Selecione os serviços que precisa na nossa lista interativa. Leva menos de 2 minutos.</p>
      </div>
      <div class="step">
        <div class="step-num">2</div>
        <h3>Técnico Recebe</h3>
        <p>O pedido chega direto no celular do técnico responsável com todos os detalhes.</p>
      </div>
      <div class="step">
        <div class="step-num">3</div>
        <h3>Agendamento Confirmado</h3>
        <p>Em até 2h você recebe confirmação de data e hora pelo WhatsApp.</p>
      </div>
      <div class="step">
        <div class="step-num">4</div>
        <h3>Serviço Realizado</h3>
        <p>Técnico certificado vai até você, executa o serviço com qualidade e emite relatório.</p>
      </div>
    </div>
  </div>
</section>

<!-- AGENDAR -->
<section id="agendar">
  <div class="section-inner">
    <span class="section-tag">Agendamento Online</span>
    <h2 class="section-title">Marque sua Visita</h2>
    <p class="section-sub">Escolha o melhor horário para você. Confirmação em até 2 horas.</p>
    <div class="agenda-grid">
      <!-- FORMULÁRIO DE AGENDAMENTO -->
      <div class="form-panel">
        <h3>📅 Agendar Visita Técnica</h3>
        <p class="fpd">Preencha os dados e escolha um horário. Gratuito para orçamentos.</p>
        <div class="form-group">
          <label>Seu nome completo</label>
          <input type="text" id="ag-nome" placeholder="João da Silva">
        </div>
        <div class="form-row">
          <div class="form-group">
            <label>Telefone / WhatsApp</label>
            <input type="tel" id="ag-tel" placeholder="(00) 90000-0000">
          </div>
          <div class="form-group">
            <label>Tipo de serviço</label>
            <select id="ag-tipo">
              <option value="">Selecione...</option>
              <option>Elétrica residencial</option>
              <option>Instalação de AC</option>
              <option>Manutenção de AC</option>
              <option>Recarga de gás</option>
              <option>Laudo técnico</option>
              <option>Emergência</option>
              <option>Outro</option>
            </select>
          </div>
        </div>
        <div class="form-row">
          <div class="form-group">
            <label>Data preferida</label>
            <input type="date" id="ag-data">
          </div>
          <div class="form-group">
            <label>Turno</label>
            <select id="ag-turno">
              <option value="">Selecione...</option>
              <option>Manhã (8h–12h)</option>
              <option>Tarde (13h–18h)</option>
              <option>Urgente — qualquer hora</option>
            </select>
          </div>
        </div>
        <div class="form-group">
          <label>Endereço completo</label>
          <input type="text" id="ag-endereco" placeholder="Rua, número, bairro, cidade">
        </div>
        <div class="form-group">
          <label>Descreva o problema ou serviço</label>
          <textarea id="ag-obs" placeholder="Ex: AC da sala não está gelando, instalei há 3 anos..."></textarea>
        </div>
        <button class="btn-primary btn-full" onclick="enviarAgendamento()">Confirmar Agendamento →</button>
        <div class="success-banner" id="ag-success">
          <span class="success-icon">✅</span>
          <div>Agendamento enviado com sucesso! O técnico entrará em contato pelo WhatsApp em até 2 horas para confirmar o horário.</div>
        </div>
      </div>

      <!-- FORMULÁRIO CONTATO RÁPIDO -->
      <div class="form-panel">
        <h3>💬 Falar com o Técnico</h3>
        <p class="fpd">Tire dúvidas direto com o técnico. Resposta rápida.</p>
        <div class="form-group">
          <label>Seu nome</label>
          <input type="text" id="ct-nome" placeholder="Maria Oliveira">
        </div>
        <div class="form-group">
          <label>WhatsApp</label>
          <input type="tel" id="ct-tel" placeholder="(00) 90000-0000">
        </div>
        <div class="form-group">
          <label>Assunto</label>
          <select id="ct-assunto">
            <option value="">Selecione...</option>
            <option>Dúvida sobre serviço</option>
            <option>Acompanhar orçamento</option>
            <option>Reclamação / Garantia</option>
            <option>Parceria comercial</option>
            <option>Outro</option>
          </select>
        </div>
        <div class="form-group">
          <label>Mensagem</label>
          <textarea id="ct-msg" placeholder="Escreva sua dúvida ou mensagem aqui..."></textarea>
        </div>
        <button class="btn-primary btn-full" onclick="enviarContato()">Enviar Mensagem →</button>
        <div class="success-banner" id="ct-success">
          <span class="success-icon">✅</span>
          <div>Mensagem enviada! O técnico responderá pelo WhatsApp em breve.</div>
        </div>
        <div style="margin-top: 24px; border-top: 1px solid rgba(255,255,255,0.06); padding-top: 24px;">
          <p style="font-size:0.82rem; color:var(--mid); margin-bottom: 12px;">Prefere falar agora?</p>
          <a href="https://wa.me/5500000000000?text=Olá!%20Gostaria%20de%20solicitar%20um%20orçamento." target="_blank" class="whatsapp-btn">
            <span style="font-size:1.3rem">💬</span> Abrir WhatsApp Agora
          </a>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CONTATO -->
<section id="contato">
  <div class="section-inner">
    <span class="section-tag">Contato</span>
    <h2 class="section-title">Fale Conosco</h2>
    <div class="contato-grid">
      <div class="contato-info">
        <div class="contact-item">
          <div class="contact-icon">📞</div>
          <div>
            <h4>Telefone</h4>
            <a href="tel:+5500000000000">(00) 0000-0000</a><br>
            <a href="tel:+5500000000000" style="color:var(--success)">(00) 90000-0000 — WhatsApp 24h</a>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">📧</div>
          <div>
            <h4>E-mail</h4>
            <a href="mailto:contato@voltfrio.com.br">contato@voltfrio.com.br</a>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">📍</div>
          <div>
            <h4>Área de Atendimento</h4>
            <p>Atendemos toda a cidade e região metropolitana. Consulte disponibilidade para cidades vizinhas.</p>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">🕐</div>
          <div>
            <h4>Horário de Atendimento</h4>
            <p>Segunda a sexta: 7h às 19h<br>Sábado: 8h às 14h<br>Emergências: 24h / 7 dias</p>
          </div>
        </div>
        <a href="https://wa.me/5500000000000" target="_blank" class="whatsapp-btn">
          <span style="font-size:1.4rem">💬</span> Chamar no WhatsApp
        </a>
      </div>
      <div>
        <div class="form-panel">
          <h3>Envie uma mensagem</h3>
          <p class="fpd">Responderemos em até 1 hora em horário comercial.</p>
          <div class="form-group">
            <label>Nome</label>
            <input type="text" id="msg-nome" placeholder="Seu nome completo">
          </div>
          <div class="form-row">
            <div class="form-group">
              <label>Telefone</label>
              <input type="tel" id="msg-tel" placeholder="(00) 00000-0000">
            </div>
            <div class="form-group">
              <label>E-mail</label>
              <input type="email" id="msg-email" placeholder="seu@email.com">
            </div>
          </div>
          <div class="form-group">
            <label>Como podemos ajudar?</label>
            <textarea id="msg-msg" placeholder="Descreva o que precisa..."></textarea>
          </div>
          <button class="btn-primary btn-full" onclick="enviarMsg()">Enviar Mensagem</button>
          <div class="success-banner" id="msg-success">
            <span class="success-icon">✅</span>
            <div>Mensagem recebida! Entraremos em contato em breve.</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-inner">
    <div>
      <div class="logo" style="font-size:1.2rem; text-decoration:none; display:inline-flex;">⚡ Volt<span style="color:var(--amber)">Frio</span></div>
      <p class="footer-copy" style="margin-top:6px;">© 2025 VoltFrio Serviços. Todos os direitos reservados.</p>
    </div>
    <div class="footer-links">
      <a href="#servicos">Serviços</a>
      <a href="#agendar">Agendar</a>
      <a href="#contato">Contato</a>
      <a href="#" onclick="openOrcamento(); return false;">Orçamento</a>
    </div>
  </div>
</footer>

<!-- CHAT FLUTUANTE -->
<button class="chat-fab" onclick="toggleChat()" title="Falar com o técnico">💬</button>
<div class="chat-bubble" id="chatBubble">
  <div class="chat-header">
    <div class="chat-avatar">👷</div>
    <div>
      <h4>Suporte VoltFrio</h4>
      <p>Online agora — responde em minutos</p>
    </div>
    <button class="chat-close" onclick="toggleChat()">✕</button>
  </div>
  <div class="chat-msgs" id="chatMsgs">
    <div class="chat-msg agent">Olá! 👋 Sou o suporte da VoltFrio. Como posso ajudar você hoje?</div>
    <div class="chat-msg agent">Pode me contar qual serviço precisa ou se tem alguma dúvida!</div>
  </div>
  <div class="chat-input-row">
    <input type="text" id="chatInput" placeholder="Digite sua mensagem..." onkeypress="chatEnter(event)">
    <button class="chat-send" onclick="sendChat()">➤</button>
  </div>
</div>

<!-- MODAL ORÇAMENTO -->
<div class="modal-overlay" id="orcamentoModal">
  <div class="modal">
    <button class="modal-close" onclick="closeOrcamento()">✕</button>
    <h2>⚡ Solicitar Orçamento</h2>
    <p class="modal-sub">Selecione os serviços que precisa. Sua lista será enviada direto ao técnico para agendamento.</p>

    <div class="form-group">
      <label>Seu nome</label>
      <input type="text" id="orc-nome" placeholder="Nome completo">
    </div>
    <div class="form-row">
      <div class="form-group">
        <label>WhatsApp</label>
        <input type="tel" id="orc-tel" placeholder="(00) 90000-0000">
      </div>
      <div class="form-group">
        <label>Cidade / Bairro</label>
        <input type="text" id="orc-cidade" placeholder="Ex: Centro, Jardim Sul">
      </div>
    </div>

    <div class="form-group" style="margin-bottom: 8px;">
      <label>Selecione os serviços desejados:</label>
    </div>
    <div class="service-checklist" id="serviceChecklist">
      <label class="check-item" onclick="toggleCheck(this)">
        <input type="checkbox" value="Instalação Elétrica (a partir de R$ 150)"> 
        <div class="check-item-info"><div class="check-item-name">🔌 Instalação Elétrica</div><div class="check-item-price">A partir de R$ 150</div></div>
      </label>
      <label class="check-item" onclick="toggleCheck(this)">
        <input type="checkbox" value="Instalação de Ar Condicionado (a partir de R$ 280)">
        <div class="check-item-info"><div class="check-item-name">🌡️ Instalação de Ar Condicionado</div><div class="check-item-price">A partir de R$ 280</div></div>
      </label>
      <label class="check-item" onclick="toggleCheck(this)">
        <input type="checkbox" value="Manutenção Preventiva de AC (a partir de R$ 120)">
        <div class="check-item-info"><div class="check-item-name">🔧 Manutenção Preventiva de AC</div><div class="check-item-price">A partir de R$ 120</div></div>
      </label>
      <label class="check-item" onclick="toggleCheck(this)">
        <input type="checkbox" value="Recarga de Gás Refrigerante (a partir de R$ 180)">
        <div class="check-item-info"><div class="check-item-name">❄️ Recarga de Gás (AC)</div><div class="check-item-price">A partir de R$ 180</div></div>
      </label>
      <label class="check-item" onclick="toggleCheck(this)">
        <input type="checkbox" value="Laudo Técnico / SPDA (a partir de R$ 350)">
        <div class="check-item-info"><div class="check-item-name">⚡ Laudo Técnico / SPDA</div><div class="check-item-price">A partir de R$ 350</div></div>
      </label>
      <label class="check-item" onclick="toggleCheck(this)">
        <input type="checkbox" value="Iluminação LED (a partir de R$ 200)">
        <div class="check-item-info"><div class="check-item-name">🔦 Iluminação LED</div><div class="check-item-price">A partir de R$ 200</div></div>
      </label>
      <label class="check-item" onclick="toggleCheck(this)">
        <input type="checkbox" value="Elétrica Industrial (sob consulta)">
        <div class="check-item-info"><div class="check-item-name">🏭 Elétrica Industrial</div><div class="check-item-price">Sob consulta</div></div>
      </label>
      <label class="check-item" onclick="toggleCheck(this)">
        <input type="checkbox" value="Emergência 24h (a partir de R$ 200)">
        <div class="check-item-info"><div class="check-item-name">🚨 Emergência 24h</div><div class="check-item-price">A partir de R$ 200</div></div>
      </label>
    </div>

    <div class="form-group">
      <label>Observações (opcional)</label>
      <textarea id="orc-obs" placeholder="Descreva melhor o problema ou qualquer detalhe importante..."></textarea>
    </div>

    <div class="orcamento-footer">
      <button class="btn-primary" onclick="enviarOrcamento()">📲 Enviar ao Técnico</button>
      <button class="btn-secondary" onclick="closeOrcamento()">Cancelar</button>
    </div>

    <div class="success-banner" id="orc-success">
      <span class="success-icon">✅</span>
      <div>
        <strong>Orçamento enviado com sucesso!</strong><br>
        O técnico recebeu sua lista de serviços e entrará em contato pelo WhatsApp em até 2 horas para confirmar disponibilidade e agendamento.
      </div>
    </div>
  </div>
</div>

<script>
  // NAV MOBILE
  function toggleMobile() {
    document.getElementById('mobileMenu').classList.toggle('open');
  }

  // MODAL ORÇAMENTO
  function openOrcamento() {
    document.getElementById('orcamentoModal').classList.add('open');
    document.body.style.overflow = 'hidden';
    document.getElementById('orc-success').classList.remove('show');
  }
  function closeOrcamento() {
    document.getElementById('orcamentoModal').classList.remove('open');
    document.body.style.overflow = '';
  }
  document.getElementById('orcamentoModal').addEventListener('click', function(e) {
    if (e.target === this) closeOrcamento();
  });

  // TOGGLE CHECKBOX
  function toggleCheck(label) {
    const cb = label.querySelector('input[type=checkbox]');
    setTimeout(() => {
      if (cb.checked) label.classList.add('selected');
      else label.classList.remove('selected');
    }, 0);
  }

  // ENVIAR ORÇAMENTO → WHATSAPP
  function enviarOrcamento() {
    const nome = document.getElementById('orc-nome').value.trim();
    const tel = document.getElementById('orc-tel').value.trim();
    const cidade = document.getElementById('orc-cidade').value.trim();
    const obs = document.getElementById('orc-obs').value.trim();

    if (!nome || !tel) { alert('Por favor, preencha seu nome e WhatsApp.'); return; }

    const checks = document.querySelectorAll('#serviceChecklist input[type=checkbox]:checked');
    if (checks.length === 0) { alert('Selecione pelo menos um serviço.'); return; }

    let servicos = '';
    checks.forEach(c => { servicos += `\n• ${c.value}`; });

    const msg = `🔧 *NOVO ORÇAMENTO — VoltFrio*\n\n👤 *Cliente:* ${nome}\n📱 *Contato:* ${tel}\n📍 *Local:* ${cidade || 'Não informado'}\n\n⚡ *Serviços Solicitados:*${servicos}${obs ? `\n\n📝 *Obs:* ${obs}` : ''}\n\n_Enviado via site VoltFrio_`;

    const num = '5500000000000';
    const url = `https://wa.me/${num}?text=${encodeURIComponent(msg)}`;
    window.open(url, '_blank');
    document.getElementById('orc-success').classList.add('show');
    setTimeout(() => closeOrcamento(), 4000);
  }

  // AGENDAMENTO
  function enviarAgendamento() {
    const nome = document.getElementById('ag-nome').value.trim();
    const tel = document.getElementById('ag-tel').value.trim();
    const tipo = document.getElementById('ag-tipo').value;
    const data = document.getElementById('ag-data').value;
    const turno = document.getElementById('ag-turno').value;
    const end = document.getElementById('ag-endereco').value.trim();
    const obs = document.getElementById('ag-obs').value.trim();

    if (!nome || !tel) { alert('Preencha nome e telefone.'); return; }

    const dataFmt = data ? new Date(data + 'T00:00:00').toLocaleDateString('pt-BR') : 'A definir';
    const msg = `📅 *NOVO AGENDAMENTO — VoltFrio*\n\n👤 *Cliente:* ${nome}\n📱 *WhatsApp:* ${tel}\n🔧 *Serviço:* ${tipo || 'Não informado'}\n📅 *Data:* ${dataFmt}\n⏰ *Turno:* ${turno || 'Não informado'}\n📍 *Endereço:* ${end || 'Não informado'}${obs ? `\n📝 *Obs:* ${obs}` : ''}\n\n_Via site VoltFrio_`;

    const url = `https://wa.me/5500000000000?text=${encodeURIComponent(msg)}`;
    window.open(url, '_blank');
    document.getElementById('ag-success').classList.add('show');
  }

  // CONTATO RÁPIDO
  function enviarContato() {
    const nome = document.getElementById('ct-nome').value.trim();
    const tel = document.getElementById('ct-tel').value.trim();
    const assunto = document.getElementById('ct-assunto').value;
    const msg2 = document.getElementById('ct-msg').value.trim();

    if (!nome || !tel) { alert('Preencha nome e telefone.'); return; }

    const msg = `💬 *MENSAGEM — VoltFrio*\n\n👤 *Nome:* ${nome}\n📱 *WhatsApp:* ${tel}\n📌 *Assunto:* ${assunto || 'Não informado'}\n\n💬 *Mensagem:* ${msg2 || '-'}\n\n_Via site VoltFrio_`;
    const url = `https://wa.me/5500000000000?text=${encodeURIComponent(msg)}`;
    window.open(url, '_blank');
    document.getElementById('ct-success').classList.add('show');
  }

  // MENSAGEM CONTATO
  function enviarMsg() {
    const nome = document.getElementById('msg-nome').value.trim();
    const tel = document.getElementById('msg-tel').value.trim();
    const email = document.getElementById('msg-email').value.trim();
    const msg2 = document.getElementById('msg-msg').value.trim();
    if (!nome || !tel) { alert('Preencha ao menos nome e telefone.'); return; }
    const msg = `📩 *CONTATO — VoltFrio*\n\n👤 ${nome}\n📱 ${tel}\n📧 ${email || '-'}\n\n💬 ${msg2 || '-'}\n\n_Via site VoltFrio_`;
    window.open(`https://wa.me/5500000000000?text=${encodeURIComponent(msg)}`, '_blank');
    document.getElementById('msg-success').classList.add('show');
  }

  // CHAT FLUTUANTE
  function toggleChat() {
    document.getElementById('chatBubble').classList.toggle('open');
  }

  const respostas = [
    "Claro! Posso ajudar com isso. Qual é o seu endereço para verificarmos a disponibilidade? 📍",
    "Ótimo! Para mais detalhes, clique em 'Solicitar Orçamento' no menu ou veja nossa tabela de serviços. ⚡",
    "Entendido! Para agendar, você pode usar o formulário de agendamento ou chamar no WhatsApp para atendimento imediato. 📅",
    "O técnico está disponível e pode te atender hoje ou amanhã. Qual horário é melhor para você? ⏰",
    "Para emergências, ligue agora: (00) 0000-0000. Atendimento no mesmo dia! 🚨",
    "Que bom! Nossos preços começam a partir de R$ 120. Quer ver a tabela completa de serviços? 💰"
  ];
  let resIdx = 0;

  function sendChat() {
    const input = document.getElementById('chatInput');
    const msgs = document.getElementById('chatMsgs');
    const text = input.value.trim();
    if (!text) return;
    msgs.innerHTML += `<div class="chat-msg user">${text}</div>`;
    input.value = '';
    msgs.scrollTop = msgs.scrollHeight;
    setTimeout(() => {
      msgs.innerHTML += `<div class="chat-msg agent">${respostas[resIdx % respostas.length]}</div>`;
      resIdx++;
      msgs.scrollTop = msgs.scrollHeight;
    }, 900);
  }

  function chatEnter(e) {
    if (e.key === 'Enter') sendChat();
  }

  // DATE MIN
  const today = new Date().toISOString().split('T')[0];
  document.getElementById('ag-data').min = today;
</script>
</body>
</html>
