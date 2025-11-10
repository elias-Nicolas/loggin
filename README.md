<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Login — Estilo Steam</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">

<style>
  :root{
    --bg-1: #0b1220;
    --bg-2: #0f1724;
    --card: rgba(18,22,28,0.75);
    --accent: #66c0ff;
    --accent-2: #2b7bb9;
    --muted: #9aa6b2;
    --glass: rgba(255,255,255,0.03);
    --success: #65c26d;
    --danger: #ff6b6b;
  }

  html,body{
    height:100%;
    margin:0;
    font-family: "Roboto", system-ui, -apple-system, sans-serif;
    background: radial-gradient(1200px 600px at 10% 10%, rgba(30,50,90,0.18), transparent),
                radial-gradient(900px 400px at 90% 90%, rgba(40,80,120,0.14), transparent),
                linear-gradient(180deg,var(--bg-1),var(--bg-2));
    color:#e6eef6;
    -webkit-font-smoothing:antialiased;
    -moz-osx-font-smoothing:grayscale;
  }

  /* Centrado */
  .wrap {
    min-height:100vh;
    display:flex;
    align-items:center;
    justify-content:center;
    padding:48px 20px;
    gap:24px;
  }

  /* Card principal */
  .card {
    width:100%;
    max-width:980px;
    display:grid;
    grid-template-columns: 1fr 420px;
    background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
    border-radius:14px;
    box-shadow: 0 10px 30px rgba(2,6,12,0.6);
    overflow:hidden;
    border:1px solid rgba(255,255,255,0.03);
  }

  /* Panel izquierdo: arte + info */
  .left {
    padding:34px;
    background:
      linear-gradient(90deg, rgba(255,255,255,0.01), rgba(255,255,255,0.00)),
      url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="800" height="600"><defs><linearGradient id="g" x1="0" x2="1"><stop stop-color="%2366c0ff" stop-opacity="0.06" offset="0"/><stop stop-color="%232b7bb9" stop-opacity="0.02" offset="1"/></linearGradient></defs><rect fill="url(%23g)" x="0" y="0" width="800" height="600"/><g fill="%2366c0ff" fill-opacity="0.04"><circle cx="150" cy="120" r="120"/><circle cx="520" cy="420" r="180"/></g></svg>') center/cover no-repeat;
    display:flex;
    flex-direction:column;
    gap:18px;
    align-items:flex-start;
    justify-content:center;
  }

  .brand {
    display:flex;
    align-items:center;
    gap:14px;
  }
  .logo {
    width:58px;
    height:58px;
    border-radius:10px;
    background:linear-gradient(135deg,var(--accent-2),var(--accent));
    display:flex;
    align-items:center;
    justify-content:center;
    box-shadow: 0 4px 14px rgba(40,120,190,0.16), inset 0 -6px 18px rgba(255,255,255,0.06);
    font-weight:700;
    color:#042635;
    font-size:20px;
  }
  .brand h1 {
    margin:0;
    font-size:20px;
    letter-spacing:0.6px;
  }
  .brand p { margin:0; color:var(--muted); font-size:13px; }

  .promo {
    margin-top:8px;
    color: #cfeeff;
    font-weight:600;
    font-size:20px;
  }
  .sub {
    color:var(--muted);
    font-size:13px;
    margin-top:6px;
  }

  /* Right: formulario */
  .right {
    padding:28px;
    background: linear-gradient(180deg, rgba(255,255,255,0.015), rgba(255,255,255,0.01));
    border-left:1px solid rgba(255,255,255,0.02);
    display:flex;
    flex-direction:column;
    gap:12px;
    justify-content:center;
  }

  form { display:flex; flex-direction:column; gap:12px; width:100%; }

  label {
    font-size:12px;
    color:var(--muted);
    display:block;
    margin-bottom:6px;
  }

  .field {
    display:flex;
    flex-direction:column;
  }

  input[type="email"], input[type="password"]{
    width:100%;
    padding:12px 14px;
    border-radius:8px;
    border:1px solid rgba(255,255,255,0.06);
    background:transparent;
    color:inherit;
    outline:none;
    font-size:14px;
    transition:box-shadow .15s, border .15s, transform .08s;
    box-shadow: inset 0 -6px 12px rgba(0,0,0,0.25);
  }
  input::placeholder { color: rgba(230,238,246,0.35); }

  input:focus {
    border-color: rgba(102,192,255,0.9);
    box-shadow: 0 0 0 6px rgba(102,192,255,0.06);
    transform: translateY(-1px);
  }

  .row { display:flex; align-items:center; gap:12px; justify-content:space-between; }
  .remember {
    display:flex; align-items:center; gap:8px; color:var(--muted); font-size:14px;
  }
  .remember input { transform:scale(1.05); }

  .btn {
    display:inline-flex;
    align-items:center;
    justify-content:center;
    gap:8px;
    padding:12px 16px;
    border-radius:10px;
    border:none;
    cursor:pointer;
    font-weight:700;
    font-size:15px;
    color:#042635;
    background:linear-gradient(90deg,var(--accent),var(--accent-2));
    box-shadow: 0 8px 20px rgba(40,120,190,0.14);
    transition:transform .12s, box-shadow .12s, opacity .12s;
  }
  .btn:active { transform: translateY(1px) scale(.998); }
  .btn.secondary {
    background:transparent;
    color:var(--muted);
    border:1px solid rgba(255,255,255,0.04);
    box-shadow:none;
    font-weight:600;
  }

  .links { display:flex; gap:10px; font-size:13px; color:var(--muted); }
  .links a { color:var(--muted); text-decoration:none; }
  .links a:hover { color:var(--accent); }

  .hint {
    margin-top:8px;
    color:var(--muted);
    font-size:13px;
  }

  .error {
    color:var(--danger);
    font-size:13px;
  }
  .success {
    color:var(--success);
    font-size:13px;
  }

  /* Footer pequeño */
  .foot { margin-top:12px; color:var(--muted); font-size:12px; }

  /* Animación sutil del fondo */
  @keyframes floaty {
    0% { transform: translateY(0px) rotate(0deg); opacity:0.95; }
    50% { transform: translateY(-8px) rotate(1deg); opacity:1; }
    100% { transform: translateY(0px) rotate(0deg); opacity:0.95; }
  }
  .logo { animation: floaty 6s ease-in-out infinite; }

  /* Responsivo */
  @media (max-width:920px){
    .card { grid-template-columns: 1fr; }
    .left { order:2; padding:20px; }
    .right { order:1; padding:20px; }
  }
</style>
</head>
<body>
<div class="wrap">
  <div class="card" role="region" aria-label="Login panel principal">
    <div class="left" aria-hidden="false">
      <div class="brand" aria-hidden="true">
        <div class="logo" aria-hidden="true">R</div>
        <div>
          <h1>Remise</h1>
          <p>Plataforma de gestión</p>
        </div>
      </div>

      <div class="promo">Accede a tu cuenta</div>
      <div class="sub">Inicia sesión para gestionar choferes, viajes y reservas en tiempo real.</div>

      <div style="margin-top:20px; display:flex; gap:8px; align-items:center;">
        
