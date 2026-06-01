<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Cash Canvas – Micro Lending</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --ink: #0e0c0a;
    --cream: #f5f0e8;
    --canvas: #ede8dc;
    --orange: #ff6b1a;
    --orange-deep: #d94f00;
    --orange-glow: rgba(255, 107, 26, 0.18);
    --gold: #c8953a;
    --light-stroke: rgba(14,12,10,0.1);
    --white: #ffffff;
    --success: #1b8a5a;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--cream);
    color: var(--ink);
    overflow-x: hidden;
  }

  /* ─── NAV ─────────────────────────────────── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 18px 60px;
    background: rgba(245,240,232,0.9);
    backdrop-filter: blur(14px);
    border-bottom: 1px solid var(--light-stroke);
  }

  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem; font-weight: 900;
    letter-spacing: -0.5px;
    color: var(--ink);
  }
  .nav-logo span { color: var(--orange); }

  .nav-links { display: flex; gap: 36px; list-style: none; }
  .nav-links a {
    font-size: 0.88rem; font-weight: 500;
    color: var(--ink); text-decoration: none;
    letter-spacing: 0.5px; text-transform: uppercase;
    opacity: 0.7; transition: opacity .2s;
  }
  .nav-links a:hover { opacity: 1; color: var(--orange); }

  .nav-cta {
    background: var(--orange); color: #fff;
    padding: 10px 24px; border-radius: 4px;
    font-size: 0.85rem; font-weight: 600;
    text-decoration: none; letter-spacing: 0.3px;
    transition: background .2s, transform .15s;
  }
  .nav-cta:hover { background: var(--orange-deep); transform: translateY(-1px); }

  /* ─── HERO ────────────────────────────────── */
  .hero {
    min-height: 100vh;
    display: grid; grid-template-columns: 1fr 1fr;
    align-items: center;
    padding: 120px 60px 80px;
    position: relative;
    overflow: hidden;
  }

  .hero::before {
    content: '';
    position: absolute; top: -100px; right: -200px;
    width: 700px; height: 700px;
    background: radial-gradient(circle, var(--orange-glow) 0%, transparent 70%);
    border-radius: 50%;
    animation: pulse 6s ease-in-out infinite;
  }

  @keyframes pulse {
    0%,100% { transform: scale(1); opacity: 1; }
    50% { transform: scale(1.08); opacity: 0.6; }
  }

  .hero-text { position: relative; z-index: 2; }

  .hero-eyebrow {
    display: inline-flex; align-items: center; gap: 8px;
    font-size: 0.78rem; font-weight: 600;
    text-transform: uppercase; letter-spacing: 2px;
    color: var(--orange);
    background: var(--orange-glow);
    padding: 6px 14px; border-radius: 20px;
    margin-bottom: 24px;
    animation: fadeUp .8s ease both;
  }

  .hero-eyebrow::before {
    content: '●'; font-size: 0.5rem; animation: blink 1.4s infinite;
  }

  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.2} }

  .hero h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(3rem, 5vw, 5rem);
    font-weight: 900; line-height: 1.05;
    letter-spacing: -2px;
    animation: fadeUp .9s ease .1s both;
  }

  .hero h1 em {
    font-style: normal; color: var(--orange);
    position: relative;
  }

  .hero h1 em::after {
    content: '';
    position: absolute; bottom: -4px; left: 0; right: 0;
    height: 3px; background: var(--orange);
    transform: scaleX(0); transform-origin: left;
    animation: lineIn 1s ease .8s both;
  }

  @keyframes lineIn { to { transform: scaleX(1); } }

  .hero-sub {
    font-size: 1.1rem; line-height: 1.7;
    color: rgba(14,12,10,0.62);
    margin: 24px 0 40px;
    max-width: 480px;
    animation: fadeUp 1s ease .2s both;
  }

  .hero-btns {
    display: flex; gap: 16px;
    animation: fadeUp 1s ease .3s both;
  }

  .btn-primary {
    background: var(--orange); color: #fff;
    padding: 15px 32px; border-radius: 4px;
    font-size: 0.95rem; font-weight: 600;
    text-decoration: none; display: inline-block;
    transition: background .2s, transform .15s, box-shadow .2s;
    box-shadow: 0 6px 24px rgba(255,107,26,0.35);
  }
  .btn-primary:hover {
    background: var(--orange-deep);
    transform: translateY(-2px);
    box-shadow: 0 10px 30px rgba(255,107,26,0.45);
  }

  .btn-outline {
    border: 2px solid var(--ink); color: var(--ink);
    padding: 13px 30px; border-radius: 4px;
    font-size: 0.95rem; font-weight: 600;
    text-decoration: none; display: inline-block;
    transition: background .2s, color .2s;
  }
  .btn-outline:hover { background: var(--ink); color: var(--cream); }

  .hero-stats {
    display: flex; gap: 40px; margin-top: 60px;
    animation: fadeUp 1s ease .4s both;
  }

  .stat-item { border-left: 3px solid var(--orange); padding-left: 14px; }
  .stat-num {
    font-family: 'Playfair Display', serif;
    font-size: 2rem; font-weight: 900;
    color: var(--ink); line-height: 1;
  }
  .stat-label { font-size: 0.8rem; color: rgba(14,12,10,0.5); margin-top: 2px; }

  .hero-visual {
    position: relative; z-index: 2;
    display: flex; justify-content: center; align-items: center;
  }

  .canvas-card {
    background: var(--ink);
    border-radius: 20px;
    padding: 40px;
    width: 340px;
    box-shadow: 40px 40px 80px rgba(0,0,0,0.22), -8px -8px 30px rgba(255,255,255,0.5);
    animation: floatCard 5s ease-in-out infinite, fadeUp .9s ease .2s both;
    position: relative;
    overflow: hidden;
  }

  @keyframes floatCard {
    0%,100% { transform: translateY(0) rotate(-1deg); }
    50% { transform: translateY(-14px) rotate(1deg); }
  }

  .canvas-card::before {
    content: '';
    position: absolute; top: -60px; right: -60px;
    width: 200px; height: 200px;
    background: radial-gradient(circle, rgba(255,107,26,0.3) 0%, transparent 70%);
    border-radius: 50%;
  }

  .card-chip {
    width: 40px; height: 28px;
    background: linear-gradient(135deg, var(--gold), #e8c46a);
    border-radius: 6px;
    margin-bottom: 30px;
    position: relative; z-index: 1;
  }

  .card-brand {
    font-family: 'Playfair Display', serif;
    color: #fff; font-size: 1.1rem; font-weight: 700;
    position: relative; z-index: 1;
  }
  .card-brand span { color: var(--orange); }

  .card-number {
    color: rgba(255,255,255,0.5);
    font-size: 0.85rem; letter-spacing: 4px;
    margin: 20px 0 8px;
    position: relative; z-index: 1;
  }

  .card-amount {
    font-family: 'Playfair Display', serif;
    color: #fff; font-size: 2.4rem; font-weight: 900;
    position: relative; z-index: 1;
  }

  .card-meta {
    display: flex; justify-content: space-between;
    margin-top: 24px;
    position: relative; z-index: 1;
  }

  .card-meta-item label {
    display: block; font-size: 0.68rem;
    color: rgba(255,255,255,0.4); text-transform: uppercase;
    letter-spacing: 1px;
  }
  .card-meta-item span {
    color: #fff; font-size: 0.85rem; font-weight: 500;
  }

  .card-badge {
    position: absolute; bottom: 20px; right: 20px;
    background: var(--orange); color: #fff;
    font-size: 0.7rem; font-weight: 700;
    padding: 4px 10px; border-radius: 20px;
    text-transform: uppercase; letter-spacing: 1px;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ─── SECTION SHARED ─────────────────────── */
  section { padding: 100px 60px; }

  .section-label {
    font-size: 0.75rem; font-weight: 700;
    text-transform: uppercase; letter-spacing: 3px;
    color: var(--orange); margin-bottom: 12px;
    display: flex; align-items: center; gap: 10px;
  }
  .section-label::after {
    content: ''; flex: 1; height: 1px;
    background: var(--orange); max-width: 40px;
  }

  .section-heading {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 3.5vw, 3rem);
    font-weight: 900; line-height: 1.1;
    letter-spacing: -1px; margin-bottom: 16px;
  }

  .section-sub {
    font-size: 1rem; line-height: 1.7;
    color: rgba(14,12,10,0.55); max-width: 500px;
  }

  /* ─── HOW IT WORKS ────────────────────────── */
  .how-it-works { background: var(--canvas); }

  .steps-grid {
    display: grid; grid-template-columns: repeat(4, 1fr);
    gap: 32px; margin-top: 60px;
  }

  .step-card {
    background: var(--cream); border-radius: 16px;
    padding: 32px 24px;
    border: 1px solid var(--light-stroke);
    position: relative; overflow: hidden;
    transition: transform .25s, box-shadow .25s;
  }

  .step-card:hover { transform: translateY(-6px); box-shadow: 0 20px 50px rgba(0,0,0,0.1); }

  .step-num {
    font-family: 'Playfair Display', serif;
    font-size: 4rem; font-weight: 900;
    color: var(--orange); opacity: 0.15;
    position: absolute; top: 10px; right: 16px;
    line-height: 1;
  }

  .step-icon {
    width: 48px; height: 48px;
    background: var(--orange-glow);
    border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.4rem; margin-bottom: 20px;
  }

  .step-card h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.15rem; font-weight: 700;
    margin-bottom: 8px;
  }
  .step-card p { font-size: 0.88rem; line-height: 1.6; color: rgba(14,12,10,0.58); }

  /* ─── ORANGE MONEY SECTION ─────────────────── */
  #payment { background: var(--ink); color: var(--cream); }

  #payment .section-label { color: #ff8c44; }
  #payment .section-sub { color: rgba(245,240,232,0.55); }

  .om-layout {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 80px; align-items: center; margin-top: 60px;
  }

  .om-phone {
    display: flex; justify-content: center;
  }

  .phone-mockup {
    width: 280px;
    background: #1a1714;
    border-radius: 40px;
    padding: 16px;
    box-shadow: 0 30px 80px rgba(0,0,0,0.6), 0 0 0 1px rgba(255,255,255,0.07);
    animation: floatCard 5s ease-in-out infinite;
  }

  .phone-screen {
    background: #fff;
    border-radius: 28px;
    overflow: hidden;
    min-height: 500px;
  }

  .om-header {
    background: var(--orange);
    padding: 24px 20px 20px;
  }

  .om-logo-row {
    display: flex; align-items: center; gap: 10px;
    margin-bottom: 16px;
  }

  .om-icon {
    width: 36px; height: 36px;
    background: #fff; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.1rem;
  }

  .om-logo-text { color: #fff; font-weight: 700; font-size: 1rem; }

  .om-balance {
    color: rgba(255,255,255,0.8); font-size: 0.72rem;
    text-transform: uppercase; letter-spacing: 1px;
    margin-bottom: 4px;
  }

  .om-amount {
    color: #fff; font-family: 'Playfair Display', serif;
    font-size: 2rem; font-weight: 900;
  }

  .om-body { padding: 20px; }

  .om-section-title {
    font-size: 0.7rem; font-weight: 700;
    text-transform: uppercase; letter-spacing: 1.5px;
    color: rgba(14,12,10,0.4); margin: 0 0 12px;
  }

  .om-grid {
    display: grid; grid-template-columns: repeat(3, 1fr);
    gap: 10px; margin-bottom: 20px;
  }

  .om-btn-item {
    background: #f5f0e8; border-radius: 12px;
    padding: 14px 8px;
    display: flex; flex-direction: column;
    align-items: center; gap: 6px;
    cursor: pointer; transition: background .2s, transform .15s;
  }

  .om-btn-item:hover { background: var(--orange-glow); transform: scale(1.04); }

  .om-btn-item span:first-child { font-size: 1.3rem; }
  .om-btn-item span:last-child { font-size: 0.62rem; font-weight: 600; color: var(--ink); text-align: center; }

  .om-transaction {
    background: #f9f6f0; border-radius: 12px;
    padding: 12px 14px;
    display: flex; justify-content: space-between; align-items: center;
    margin-bottom: 8px;
    border: 1px solid rgba(14,12,10,0.07);
  }

  .om-tx-left { display: flex; align-items: center; gap: 10px; }
  .om-tx-icon {
    width: 32px; height: 32px; border-radius: 50%;
    background: var(--orange-glow);
    display: flex; align-items: center; justify-content: center;
    font-size: 0.85rem;
  }
  .om-tx-name { font-size: 0.78rem; font-weight: 600; color: var(--ink); }
  .om-tx-date { font-size: 0.65rem; color: rgba(14,12,10,0.4); }
  .om-tx-amount { font-size: 0.85rem; font-weight: 700; }
  .om-tx-amount.credit { color: var(--success); }
  .om-tx-amount.debit { color: #c0392b; }

  .om-features { }

  .om-features h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.8rem; font-weight: 900;
    color: var(--cream); margin-bottom: 20px;
  }

  .om-feature-list { list-style: none; display: flex; flex-direction: column; gap: 18px; }

  .om-feature-list li {
    display: flex; align-items: flex-start; gap: 14px;
    font-size: 0.92rem; line-height: 1.6;
    color: rgba(245,240,232,0.75);
  }

  .om-feature-list li::before {
    content: '◆'; color: var(--orange);
    font-size: 0.6rem; margin-top: 5px; flex-shrink: 0;
  }

  .om-pay-form {
    background: rgba(255,255,255,0.05);
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 20px; padding: 32px;
    margin-top: 36px;
  }

  .om-pay-form h4 {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem; color: #fff; margin-bottom: 20px;
    display: flex; align-items: center; gap: 10px;
  }

  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }

  .form-group { display: flex; flex-direction: column; gap: 6px; margin-bottom: 16px; }
  .form-group.full { grid-column: 1/-1; }

  .form-group label {
    font-size: 0.75rem; font-weight: 600;
    color: rgba(245,240,232,0.55);
    text-transform: uppercase; letter-spacing: 0.8px;
  }

  .form-group input, .form-group select {
    background: rgba(255,255,255,0.07);
    border: 1px solid rgba(255,255,255,0.12);
    border-radius: 8px; padding: 12px 16px;
    color: #fff; font-size: 0.9rem;
    font-family: 'DM Sans', sans-serif;
    transition: border-color .2s;
    outline: none;
  }

  .form-group input::placeholder { color: rgba(255,255,255,0.25); }
  .form-group input:focus, .form-group select:focus {
    border-color: var(--orange);
    box-shadow: 0 0 0 3px rgba(255,107,26,0.18);
  }

  .form-group select option { background: #1a1714; }

  .btn-pay {
    width: 100%; padding: 15px;
    background: var(--orange); color: #fff;
    border: none; border-radius: 8px;
    font-size: 1rem; font-weight: 700;
    font-family: 'DM Sans', sans-serif;
    cursor: pointer;
    display: flex; align-items: center; justify-content: center; gap: 10px;
    transition: background .2s, transform .15s;
    margin-top: 4px;
  }

  .btn-pay:hover { background: var(--orange-deep); transform: translateY(-1px); }

  .pay-security {
    display: flex; align-items: center; justify-content: center; gap: 8px;
    margin-top: 14px; font-size: 0.75rem; color: rgba(245,240,232,0.4);
  }

  /* ─── LOAN APPLICATION ─────────────────────── */
  #loan { background: var(--cream); }

  .loan-layout {
    display: grid; grid-template-columns: 1fr 1.5fr;
    gap: 80px; align-items: start; margin-top: 60px;
  }

  .loan-info h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem; font-weight: 700;
    margin-bottom: 20px;
  }

  .loan-perks { list-style: none; display: flex; flex-direction: column; gap: 14px; margin-bottom: 36px; }

  .loan-perks li {
    display: flex; align-items: flex-start; gap: 12px;
    font-size: 0.9rem; line-height: 1.6; color: rgba(14,12,10,0.65);
  }

  .perk-dot {
    width: 22px; height: 22px; background: var(--orange);
    border-radius: 50%; flex-shrink: 0;
    display: flex; align-items: center; justify-content: center;
    color: #fff; font-size: 0.65rem; font-weight: 700;
    margin-top: 1px;
  }

  .loan-range-card {
    background: var(--ink); border-radius: 16px;
    padding: 28px; color: #fff;
  }

  .loan-range-card h4 {
    font-size: 0.75rem; font-weight: 600;
    text-transform: uppercase; letter-spacing: 1.5px;
    color: rgba(255,255,255,0.45); margin-bottom: 20px;
  }

  .range-row {
    display: flex; justify-content: space-between;
    align-items: center; padding: 12px 0;
    border-bottom: 1px solid rgba(255,255,255,0.08);
  }

  .range-row:last-child { border-bottom: none; }

  .range-label { font-size: 0.82rem; color: rgba(255,255,255,0.5); }
  .range-value {
    font-family: 'Playfair Display', serif;
    font-size: 1rem; font-weight: 700; color: var(--orange);
  }

  /* Application Form */
  .loan-form-card {
    background: #fff;
    border-radius: 24px; padding: 44px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.08);
    border: 1px solid var(--light-stroke);
  }

  .form-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem; font-weight: 900;
    margin-bottom: 6px;
  }

  .form-desc { font-size: 0.87rem; color: rgba(14,12,10,0.5); margin-bottom: 32px; }

  .form-progress {
    display: flex; gap: 8px; margin-bottom: 32px;
  }

  .progress-step {
    height: 4px; flex: 1; border-radius: 2px;
    background: #e8e0d0;
    transition: background .4s;
  }
  .progress-step.active { background: var(--orange); }

  .loan-form .form-group label { color: rgba(14,12,10,0.55); }

  .loan-form .form-group input,
  .loan-form .form-group select,
  .loan-form .form-group textarea {
    background: var(--cream);
    border: 1.5px solid rgba(14,12,10,0.12);
    border-radius: 8px; padding: 13px 16px;
    color: var(--ink); font-size: 0.9rem;
    font-family: 'DM Sans', sans-serif;
    transition: border-color .2s; outline: none;
    width: 100%;
  }

  .loan-form .form-group textarea { resize: vertical; min-height: 90px; }

  .loan-form .form-group input:focus,
  .loan-form .form-group select:focus,
  .loan-form .form-group textarea:focus {
    border-color: var(--orange);
    background: #fff;
    box-shadow: 0 0 0 3px rgba(255,107,26,0.1);
  }

  .loan-form .form-group select option { background: #fff; }

  .amount-slider-wrap { margin-bottom: 8px; }

  .amount-display {
    font-family: 'Playfair Display', serif;
    font-size: 2rem; font-weight: 900;
    color: var(--orange); margin-bottom: 10px;
  }

  input[type="range"] {
    -webkit-appearance: none;
    width: 100%; height: 6px;
    background: linear-gradient(to right, var(--orange) 0%, var(--orange) 40%, #e8e0d0 40%);
    border-radius: 3px; outline: none;
    cursor: pointer;
  }

  input[type="range"]::-webkit-slider-thumb {
    -webkit-appearance: none;
    width: 22px; height: 22px;
    background: var(--orange); border-radius: 50%;
    border: 3px solid #fff;
    box-shadow: 0 2px 8px rgba(255,107,26,0.5);
    cursor: pointer;
  }

  .range-labels {
    display: flex; justify-content: space-between;
    font-size: 0.72rem; color: rgba(14,12,10,0.4);
    margin-top: 6px;
  }

  .terms-check {
    display: flex; align-items: flex-start; gap: 12px;
    font-size: 0.83rem; color: rgba(14,12,10,0.6);
    line-height: 1.5;
    margin-bottom: 24px;
  }

  .terms-check input[type="checkbox"] {
    width: 18px; height: 18px;
    accent-color: var(--orange);
    cursor: pointer; flex-shrink: 0;
    margin-top: 2px;
  }

  .terms-check a { color: var(--orange); text-decoration: none; }

  .btn-submit {
    width: 100%; padding: 16px;
    background: var(--orange); color: #fff;
    border: none; border-radius: 8px;
    font-size: 1rem; font-weight: 700;
    font-family: 'DM Sans', sans-serif;
    cursor: pointer;
    display: flex; align-items: center; justify-content: center; gap: 10px;
    transition: background .2s, transform .15s, box-shadow .2s;
    box-shadow: 0 6px 24px rgba(255,107,26,0.3);
  }

  .btn-submit:hover {
    background: var(--orange-deep);
    transform: translateY(-2px);
    box-shadow: 0 10px 30px rgba(255,107,26,0.45);
  }

  .submit-note {
    text-align: center; margin-top: 14px;
    font-size: 0.75rem; color: rgba(14,12,10,0.4);
    display: flex; align-items: center; justify-content: center; gap: 6px;
  }

  /* ─── TESTIMONIALS ────────────────────────── */
  .testimonials { background: var(--canvas); }

  .testi-grid {
    display: grid; grid-template-columns: repeat(3, 1fr);
    gap: 28px; margin-top: 60px;
  }

  .testi-card {
    background: var(--cream); border-radius: 18px;
    padding: 32px 28px;
    border: 1px solid var(--light-stroke);
    position: relative;
    transition: transform .25s;
  }

  .testi-card:hover { transform: translateY(-4px); }

  .quote-mark {
    font-family: 'Playfair Display', serif;
    font-size: 4rem; color: var(--orange);
    opacity: 0.25; line-height: 0.8;
    margin-bottom: 16px; display: block;
  }

  .testi-text {
    font-size: 0.9rem; line-height: 1.75;
    color: rgba(14,12,10,0.65); margin-bottom: 24px;
  }

  .testi-author { display: flex; align-items: center; gap: 12px; }

  .testi-avatar {
    width: 42px; height: 42px; border-radius: 50%;
    background: linear-gradient(135deg, var(--orange), var(--gold));
    display: flex; align-items: center; justify-content: center;
    font-family: 'Playfair Display', serif;
    font-size: 1rem; font-weight: 900; color: #fff;
  }

  .testi-name { font-weight: 700; font-size: 0.88rem; }
  .testi-role { font-size: 0.75rem; color: rgba(14,12,10,0.45); }

  /* ─── FOOTER ──────────────────────────────── */
  footer {
    background: var(--ink); color: rgba(245,240,232,0.55);
    padding: 60px;
  }

  .footer-inner {
    display: grid; grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 60px; margin-bottom: 60px;
  }

  .footer-brand .nav-logo { font-size: 1.4rem; margin-bottom: 14px; display: block; }
  .footer-tagline { font-size: 0.87rem; line-height: 1.7; max-width: 260px; }

  .footer-col h5 {
    color: var(--cream); font-size: 0.78rem;
    text-transform: uppercase; letter-spacing: 1.5px;
    margin-bottom: 16px;
  }

  .footer-col ul { list-style: none; display: flex; flex-direction: column; gap: 10px; }
  .footer-col ul a { color: rgba(245,240,232,0.45); text-decoration: none; font-size: 0.87rem; transition: color .2s; }
  .footer-col ul a:hover { color: var(--orange); }

  .footer-bottom {
    border-top: 1px solid rgba(255,255,255,0.07);
    padding-top: 28px;
    display: flex; justify-content: space-between; align-items: center;
    font-size: 0.78rem;
  }

  .footer-bottom a { color: rgba(245,240,232,0.45); text-decoration: none; }

  /* ─── SUCCESS MODAL ───────────────────────── */
  .modal-overlay {
    display: none;
    position: fixed; inset: 0; z-index: 1000;
    background: rgba(0,0,0,0.6);
    backdrop-filter: blur(8px);
    align-items: center; justify-content: center;
  }

  .modal-overlay.open { display: flex; }

  .modal-box {
    background: var(--cream);
    border-radius: 24px; padding: 50px 44px;
    text-align: center; max-width: 420px; width: 90%;
    animation: popIn .4s cubic-bezier(.34,1.56,.64,1);
  }

  @keyframes popIn {
    from { transform: scale(0.7); opacity: 0; }
    to { transform: scale(1); opacity: 1; }
  }

  .modal-icon {
    width: 72px; height: 72px;
    background: rgba(27,138,90,0.12);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 2rem; margin: 0 auto 24px;
  }

  .modal-box h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem; margin-bottom: 10px;
  }
  .modal-box p { font-size: 0.9rem; color: rgba(14,12,10,0.55); line-height: 1.6; margin-bottom: 28px; }

  .modal-close {
    background: var(--orange); color: #fff;
    border: none; border-radius: 8px;
    padding: 13px 32px; font-size: 0.95rem; font-weight: 700;
    font-family: 'DM Sans', sans-serif;
    cursor: pointer; transition: background .2s;
  }
  .modal-close:hover { background: var(--orange-deep); }

  /* ─── RESPONSIVE ──────────────────────────── */
  @media (max-width: 1024px) {
    nav { padding: 16px 30px; }
    section { padding: 80px 30px; }
    .hero { padding: 120px 30px 60px; gap: 40px; }
    .steps-grid { grid-template-columns: repeat(2, 1fr); }
    .testi-grid { grid-template-columns: 1fr 1fr; }
    .footer-inner { grid-template-columns: 1fr 1fr; gap: 40px; }
  }

  @media (max-width: 768px) {
    nav { padding: 14px 20px; }
    .nav-links { display: none; }
    .hero { grid-template-columns: 1fr; padding: 100px 20px 60px; }
    .hero-visual { display: none; }
    section { padding: 60px 20px; }
    .om-layout { grid-template-columns: 1fr; gap: 40px; }
    .loan-layout { grid-template-columns: 1fr; gap: 40px; }
    .form-row { grid-template-columns: 1fr; }
    .steps-grid { grid-template-columns: 1fr; }
    .testi-grid { grid-template-columns: 1fr; }
    .footer-inner { grid-template-columns: 1fr; gap: 32px; }
    .hero-stats { gap: 24px; }
    .loan-form-card { padding: 28px 20px; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">Cash<span>Canvas</span></div>
  <ul class="nav-links">
    <li><a href="#how">How It Works</a></li>
    <li><a href="#payment">Payments</a></li>
    <li><a href="#loan">Apply</a></li>
    <li><a href="#testimonials">Stories</a></li>
  </ul>
  <a href="#loan" class="nav-cta">Get a Loan →</a>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-text">
    <div class="hero-eyebrow">Micro Lending Made Simple</div>
    <h1>Funding Your <em>Story</em>, One Canvas at a Time</h1>
    <p class="hero-sub">The Cash Canvas offers fast, transparent micro-loans to help individuals and small businesses grow. Apply in minutes, get funded in hours via Orange Money.</p>
    <div class="hero-btns">
      <a href="#loan" class="btn-primary">Apply for a Loan</a>
      <a href="#how" class="btn-outline">How It Works</a>
    </div>
    <div class="hero-stats">
      <div class="stat-item">
        <div class="stat-num">4,200+</div>
        <div class="stat-label">Clients Funded</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">GHS 2M+</div>
        <div class="stat-label">Disbursed</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">98%</div>
        <div class="stat-label">Approval Rate</div>
      </div>
    </div>
  </div>
  <div class="hero-visual">
    <div class="canvas-card">
      <div class="card-chip"></div>
      <div class="card-brand">Cash<span>Canvas</span></div>
      <div class="card-number">●●●● ●●●● ●●●● 4291</div>
      <div class="card-amount">GHS 5,000</div>
      <div class="card-meta">
        <div class="card-meta-item">
          <label>Issued To</label>
          <span>K. Mensah</span>
        </div>
        <div class="card-meta-item">
          <label>Term</label>
          <span>3 Months</span>
        </div>
      </div>
      <div class="card-badge">Active</div>
    </div>
  </div>
</section>

<!-- HOW IT WORKS -->
<section class="how-it-works" id="how">
  <div class="section-label">Process</div>
  <h2 class="section-heading">Four Steps to Your Funds</h2>
  <p class="section-sub">No paperwork mountains. No hidden fees. Just a clear, honest path to the capital you need.</p>
  <div class="steps-grid">
    <div class="step-card">
      <div class="step-num">01</div>
      <div class="step-icon">📝</div>
      <h3>Fill the Form</h3>
      <p>Complete the simple online application with your personal and financial details in under 5 minutes.</p>
    </div>
    <div class="step-card">
      <div class="step-num">02</div>
      <div class="step-icon">⚡</div>
      <h3>Quick Review</h3>
      <p>Our team reviews your application within 1–2 hours. No lengthy credit checks or bureaucracy.</p>
    </div>
    <div class="step-card">
      <div class="step-num">03</div>
      <div class="step-icon">✅</div>
      <h3>Get Approved</h3>
      <p>Receive your approval notification via SMS and email with a clear breakdown of your loan terms.</p>
    </div>
    <div class="step-card">
      <div class="step-num">04</div>
      <div class="step-icon">📱</div>
      <h3>Funds via Orange Money</h3>
      <p>Cash is disbursed instantly to your Orange Money wallet. Repay conveniently the same way.</p>
    </div>
  </div>
</section>

<!-- ORANGE MONEY PAYMENT -->
<section id="payment">
  <div class="section-label">Payment System</div>
  <h2 class="section-heading" style="color:var(--cream)">Powered by Orange Money</h2>
  <p class="section-sub">Send repayments, check loan balance, and receive disbursements — all through Orange Money's secure mobile platform.</p>

  <div class="om-layout">
    <!-- Phone mockup -->
    <div class="om-phone">
      <div class="phone-mockup">
        <div class="phone-screen">
          <div class="om-header">
            <div class="om-logo-row">
              <div class="om-icon">🟠</div>
              <div class="om-logo-text">Orange Money</div>
            </div>
            <div class="om-balance">Available Balance</div>
            <div class="om-amount">GHS 1,340.00</div>
          </div>
          <div class="om-body">
            <div class="om-section-title">Quick Actions</div>
            <div class="om-grid">
              <div class="om-btn-item">
                <span>💸</span><span>Send Money</span>
              </div>
              <div class="om-btn-item">
                <span>📥</span><span>Receive</span>
              </div>
              <div class="om-btn-item">
                <span>🏦</span><span>Pay Loan</span>
              </div>
              <div class="om-btn-item">
                <span>📊</span><span>Statement</span>
              </div>
              <div class="om-btn-item">
                <span>🔁</span><span>Top Up</span>
              </div>
              <div class="om-btn-item">
                <span>📞</span><span>Airtime</span>
              </div>
            </div>
            <div class="om-section-title">Recent Transactions</div>
            <div class="om-transaction">
              <div class="om-tx-left">
                <div class="om-tx-icon">💰</div>
                <div>
                  <div class="om-tx-name">Cash Canvas – Loan</div>
                  <div class="om-tx-date">Today, 10:22 AM</div>
                </div>
              </div>
              <div class="om-tx-amount credit">+GHS 500</div>
            </div>
            <div class="om-transaction">
              <div class="om-tx-left">
                <div class="om-tx-icon">🔄</div>
                <div>
                  <div class="om-tx-name">Repayment – June</div>
                  <div class="om-tx-date">Jun 1, 9:00 AM</div>
                </div>
              </div>
              <div class="om-tx-amount debit">-GHS 180</div>
            </div>
            <div class="om-transaction">
              <div class="om-tx-left">
                <div class="om-tx-icon">📲</div>
                <div>
                  <div class="om-tx-name">Cash Canvas – Loan</div>
                  <div class="om-tx-date">May 15, 2:15 PM</div>
                </div>
              </div>
              <div class="om-tx-amount credit">+GHS 1,000</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Right side -->
    <div class="om-features">
      <h3>Fast, Secure &amp; Instant Mobile Payments</h3>
      <ul class="om-feature-list">
        <li>Loan disbursements go directly to your Orange Money wallet — no bank account needed.</li>
        <li>Make loan repayments anytime by dialing <strong style="color:var(--orange)">*144#</strong> or via the Orange Money app.</li>
        <li>Get instant SMS confirmation for every transaction, keeping you always informed.</li>
        <li>Zero transfer fees on Cash Canvas repayments — we cover the transaction cost.</li>
        <li>Fully encrypted end-to-end transactions powered by Orange Money's infrastructure.</li>
      </ul>

      <!-- Quick Pay Form -->
      <div class="om-pay-form">
        <h4>🟠 Quick Loan Repayment</h4>
        <div class="form-row">
          <div class="form-group">
            <label>Orange Money Number</label>
            <input type="tel" placeholder="024 XXX XXXX">
          </div>
          <div class="form-group">
            <label>Loan Reference</label>
            <input type="text" placeholder="CC-XXXXXX">
          </div>
          <div class="form-group">
            <label>Amount (GHS)</label>
            <input type="number" placeholder="0.00">
          </div>
          <div class="form-group">
            <label>Payment Type</label>
            <select>
              <option>Monthly Instalment</option>
              <option>Full Repayment</option>
              <option>Partial Payment</option>
            </select>
          </div>
        </div>
        <button class="btn-pay" onclick="showModal('pay')">🟠 Pay via Orange Money</button>
        <div class="pay-security">🔒 Secured by Orange Money Encryption</div>
      </div>
    </div>
  </div>
</section>

<!-- LOAN APPLICATION -->
<section id="loan">
  <div class="section-label">Applications</div>
  <h2 class="section-heading">Apply for a Micro Loan</h2>
  <p class="section-sub">Fill in your details below. Our team will review and respond within 2 hours on business days.</p>

  <div class="loan-layout">
    <!-- Info -->
    <div class="loan-info">
      <h3>Why Choose The Cash Canvas?</h3>
      <ul class="loan-perks">
        <li><div class="perk-dot">✓</div><span>No collateral required for loans under GHS 2,000</span></li>
        <li><div class="perk-dot">✓</div><span>Competitive flat interest rates starting at just 5%/month</span></li>
        <li><div class="perk-dot">✓</div><span>Flexible repayment: weekly, bi-weekly, or monthly schedules</span></li>
        <li><div class="perk-dot">✓</div><span>No penalties for early repayment — pay off anytime</span></li>
        <li><div class="perk-dot">✓</div><span>Repeat borrowers enjoy discounted rates and higher limits</span></li>
        <li><div class="perk-dot">✓</div><span>Funds disbursed via Orange Money within hours of approval</span></li>
      </ul>

      <div class="loan-range-card">
        <h4>Loan Tiers at a Glance</h4>
        <div class="range-row">
          <span class="range-label">Starter Loan</span>
          <span class="range-value">GHS 100 – 500</span>
        </div>
        <div class="range-row">
          <span class="range-label">Growth Loan</span>
          <span class="range-value">GHS 500 – 2,000</span>
        </div>
        <div class="range-row">
          <span class="range-label">Business Loan</span>
          <span class="range-value">GHS 2,000 – 10,000</span>
        </div>
        <div class="range-row">
          <span class="range-label">Max Term</span>
          <span class="range-value">12 Months</span>
        </div>
        <div class="range-row">
          <span class="range-label">Interest Rate</span>
          <span class="range-value">From 5%/month</span>
        </div>
      </div>
    </div>

    <!-- Form -->
    <div class="loan-form-card">
      <div class="form-title">Loan Application Form</div>
      <p class="form-desc">Complete all sections. Fields marked * are required.</p>
      <div class="form-progress">
        <div class="progress-step active" id="prog1"></div>
        <div class="progress-step active" id="prog2"></div>
        <div class="progress-step" id="prog3"></div>
        <div class="progress-step" id="prog4"></div>
      </div>

      <form class="loan-form" onsubmit="handleSubmit(event)">
        <!-- Personal Info -->
        <div class="form-row">
          <div class="form-group">
            <label>First Name *</label>
            <input type="text" placeholder="Kofi" required>
          </div>
          <div class="form-group">
            <label>Last Name *</label>
            <input type="text" placeholder="Mensah" required>
          </div>
          <div class="form-group">
            <label>Phone Number *</label>
            <input type="tel" placeholder="024 XXX XXXX" required>
          </div>
          <div class="form-group">
            <label>National ID Number *</label>
            <input type="text" placeholder="GHA-XXXXXXXXX-X" required>
          </div>
          <div class="form-group">
            <label>Email Address</label>
            <input type="email" placeholder="kofi@example.com">
          </div>
          <div class="form-group">
            <label>Region *</label>
            <select required>
              <option value="">— Select Region —</option>
              <option>Greater Accra</option>
              <option>Ashanti</option>
              <option>Western</option>
              <option>Central</option>
              <option>Eastern</option>
              <option>Northern</option>
              <option>Volta</option>
              <option>Upper East</option>
              <option>Upper West</option>
              <option>Brong-Ahafo</option>
            </select>
          </div>
        </div>

        <!-- Loan Details -->
        <div class="form-group" style="margin-top:8px">
          <label>Loan Amount (GHS) *</label>
          <div class="amount-slider-wrap">
            <div class="amount-display" id="amountDisplay">GHS 1,000</div>
            <input type="range" min="100" max="10000" step="100" value="1000"
              oninput="updateAmount(this.value)" id="loanRange">
            <div class="range-labels"><span>GHS 100</span><span>GHS 10,000</span></div>
          </div>
        </div>

        <div class="form-row">
          <div class="form-group">
            <label>Repayment Term *</label>
            <select required>
              <option value="">— Select Term —</option>
              <option>1 Month</option>
              <option>2 Months</option>
              <option>3 Months</option>
              <option>6 Months</option>
              <option>9 Months</option>
              <option>12 Months</option>
            </select>
          </div>
          <div class="form-group">
            <label>Repayment Schedule *</label>
            <select required>
              <option value="">— Select Schedule —</option>
              <option>Weekly</option>
              <option>Bi-Weekly</option>
              <option>Monthly</option>
            </select>
          </div>
          <div class="form-group">
            <label>Employment Status *</label>
            <select required>
              <option value="">— Select —</option>
              <option>Employed (Salaried)</option>
              <option>Self-Employed</option>
              <option>Business Owner</option>
              <option>Trader / Market Vendor</option>
              <option>Farmer</option>
              <option>Other</option>
            </select>
          </div>
          <div class="form-group">
            <label>Monthly Income (GHS) *</label>
            <input type="number" placeholder="e.g. 800" required>
          </div>
        </div>

        <div class="form-group">
          <label>Orange Money Number (Disbursement) *</label>
          <input type="tel" placeholder="024 XXX XXXX" required>
        </div>

        <div class="form-group">
          <label>Purpose of Loan *</label>
          <textarea placeholder="Briefly describe what you will use the funds for (e.g. buying stock for my shop, school fees, medical expenses...)"></textarea>
        </div>

        <div class="terms-check">
          <input type="checkbox" id="terms" required>
          <label for="terms">
            I agree to The Cash Canvas <a href="#">Terms &amp; Conditions</a> and <a href="#">Privacy Policy</a>. I confirm that all information provided is accurate and complete.
          </label>
        </div>

        <button type="submit" class="btn-submit">
          Submit Application →
        </button>
        <div class="submit-note">🔒 Your data is encrypted and never shared with third parties</div>
      </form>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section class="testimonials" id="testimonials">
  <div class="section-label">Stories</div>
  <h2 class="section-heading">Clients Who Painted Their Future</h2>
  <p class="section-sub">Real people, real growth — powered by The Cash Canvas.</p>
  <div class="testi-grid">
    <div class="testi-card">
      <span class="quote-mark">"</span>
      <p class="testi-text">I applied at 8am and had GHS 1,500 on my Orange Money by noon. I restocked my shop and doubled sales that same week. The process was unbelievably smooth.</p>
      <div class="testi-author">
        <div class="testi-avatar">A</div>
        <div>
          <div class="testi-name">Abena Osei</div>
          <div class="testi-role">Market Trader, Kumasi</div>
        </div>
      </div>
    </div>
    <div class="testi-card">
      <span class="quote-mark">"</span>
      <p class="testi-text">As a sole trader, banks always turned me away. Cash Canvas understood my situation and gave me my second chance. I'm now on my fourth loan and growing strong.</p>
      <div class="testi-author">
        <div class="testi-avatar">K</div>
        <div>
          <div class="testi-name">Kwame Darko</div>
          <div class="testi-role">Tailor &amp; Fashion Designer, Accra</div>
        </div>
      </div>
    </div>
    <div class="testi-card">
      <span class="quote-mark">"</span>
      <p class="testi-text">Repaying through Orange Money is incredibly convenient. No queues, no bank visits. I send my instalment from my phone in seconds. Totally recommend.</p>
      <div class="testi-author">
        <div class="testi-avatar">E</div>
        <div>
          <div class="testi-name">Efua Asante</div>
          <div class="testi-role">Food Vendor, Cape Coast</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-inner">
    <div class="footer-brand">
      <div class="nav-logo">Cash<span style="color:var(--orange)">Canvas</span></div>
      <p class="footer-tagline">Empowering individuals and small businesses across Ghana with fast, fair micro-loans since 2019.</p>
    </div>
    <div class="footer-col">
      <h5>Company</h5>
      <ul>
        <li><a href="#">About Us</a></li>
        <li><a href="#">Our Team</a></li>
        <li><a href="#">Careers</a></li>
        <li><a href="#">Press</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h5>Services</h5>
      <ul>
        <li><a href="#loan">Micro Loans</a></li>
        <li><a href="#payment">Orange Money</a></li>
        <li><a href="#">Business Loans</a></li>
        <li><a href="#">Repayment Portal</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h5>Support</h5>
      <ul>
        <li><a href="#">FAQ</a></li>
        <li><a href="#">Contact Us</a></li>
        <li><a href="#">Privacy Policy</a></li>
        <li><a href="#">Terms</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <span>© 2026 The Cash Canvas. All rights reserved.</span>
    <span>🟠 Powered by Orange Money &nbsp;|&nbsp; <a href="#">Licensed by Bank of Ghana</a></span>
  </div>
</footer>

<!-- MODAL -->
<div class="modal-overlay" id="modal">
  <div class="modal-box">
    <div class="modal-icon" id="modalIcon">✅</div>
    <h3 id="modalTitle">Submitted!</h3>
    <p id="modalText">Your application has been received. Our team will contact you within 1–2 hours.</p>
    <button class="modal-close" onclick="closeModal()">Done</button>
  </div>
</div>

<script>
  function updateAmount(val) {
    const num = parseInt(val);
    document.getElementById('amountDisplay').textContent = 'GHS ' + num.toLocaleString();
    const pct = ((num - 100) / (10000 - 100)) * 100;
    document.getElementById('loanRange').style.background =
      `linear-gradient(to right, var(--orange) 0%, var(--orange) ${pct}%, #e8e0d0 ${pct}%)`;
    const steps = ['prog1','prog2','prog3','prog4'];
    const active = num < 500 ? 1 : num < 2000 ? 2 : num < 6000 ? 3 : 4;
    steps.forEach((id, i) => {
      document.getElementById(id).classList.toggle('active', i < active);
    });
  }

  function handleSubmit(e) {
    e.preventDefault();
    document.getElementById('modalIcon').textContent = '✅';
    document.getElementById('modalTitle').textContent = 'Application Submitted!';
    document.getElementById('modalText').textContent =
      'Thank you! Your loan application has been received. Our team will review it and reach out to your Orange Money number within 1–2 business hours.';
    document.getElementById('modal').classList.add('open');
  }

  function showModal(type) {
    document.getElementById('modalIcon').textContent = '🟠';
    document.getElementById('modalTitle').textContent = 'Payment Initiated!';
    document.getElementById('modalText').textContent =
      'Your Orange Money repayment has been initiated. You will receive an SMS confirmation shortly. Dial *144# to confirm the transaction.';
    document.getElementById('modal').classList.add('open');
  }

  function closeModal() {
    document.getElementById('modal').classList.remove('open');
  }

  document.getElementById('modal').addEventListener('click', function(e) {
    if (e.target === this) closeModal();
  });
</script>
</body>
</html>

