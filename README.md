<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>runfalse — разработчик</title>
  <!-- Шрифты -->
  <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      background-color: #030712;
      color: #e2e8f0;
      font-family: 'JetBrains Mono', monospace;
      display: flex;
      justify-content: center;
      padding: 20px 10px;
    }
    .container {
      max-width: 1000px;
      width: 100%;
      background: #0b1120;
      border-radius: 32px;
      padding: 30px 20px 10px;
      box-shadow: 0 25px 50px -12px rgba(0,0,0,0.8);
      border: 1px solid #1e293b;
      overflow: hidden;
    }
    /* Анимированные блоки */
    .fade-in {
      opacity: 0;
      animation: fadeUp 0.8s ease forwards;
    }
    .delay-1 { animation-delay: 0.1s; }
    .delay-2 { animation-delay: 0.3s; }
    .delay-3 { animation-delay: 0.5s; }
    .delay-4 { animation-delay: 0.7s; }
    .delay-5 { animation-delay: 0.9s; }
    .delay-6 { animation-delay: 1.1s; }

    @keyframes fadeUp {
      0% { opacity: 0; transform: translateY(20px); }
      100% { opacity: 1; transform: translateY(0); }
    }

    .glow-text {
      color: #818cf8;
      text-shadow: 0 0 12px rgba(99, 102, 241, 0.3);
      transition: text-shadow 0.3s;
    }
    .glow-text:hover {
      text-shadow: 0 0 24px rgba(99, 102, 241, 0.7);
    }

    .terminal-box {
      background: #0f172a;
      border: 1px solid #1e293b;
      border-radius: 16px;
      padding: 20px 24px;
      margin: 20px 0;
      font-size: 14px;
      line-height: 1.8;
      box-shadow: inset 0 0 30px rgba(0,0,0,0.5);
      backdrop-filter: blur(2px);
      transition: all 0.2s;
    }
    .terminal-box:hover {
      border-color: #6366f1;
      box-shadow: 0 0 30px rgba(99, 102, 241, 0.1), inset 0 0 30px rgba(99, 102, 241, 0.02);
    }

    .badge-group {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 12px;
      margin: 16px 0;
    }
    .badge {
      background: #111827;
      padding: 6px 18px;
      border-radius: 40px;
      font-size: 13px;
      font-weight: 500;
      color: #cbd5e1;
      border: 1px solid #1e293b;
      letter-spacing: 0.3px;
      transition: 0.2s;
    }
    .badge:hover {
      background: #1e293b;
      color: #f1f5f9;
      border-color: #6366f1;
      transform: scale(1.03);
      box-shadow: 0 0 20px rgba(99, 102, 241, 0.15);
    }

    .grid-4 {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 16px;
      margin: 20px 0;
    }
    .grid-card {
      background: #0f172a;
      border: 1px solid #1e293b;
      border-radius: 20px;
      padding: 20px 12px;
      text-align: center;
      transition: 0.25s ease;
      backdrop-filter: blur(2px);
    }
    .grid-card:hover {
      transform: translateY(-6px);
      border-color: #6366f1;
      background: #131d35;
      box-shadow: 0 12px 30px -10px #6366f140;
    }
    .grid-card h4 {
      color: #a5b4fc;
      font-size: 18px;
      margin-bottom: 10px;
      letter-spacing: 0.5px;
    }
    .grid-card p {
      color: #94a3b8;
      font-size: 13px;
      line-height: 1.5;
    }

    .divider {
      border: none;
      height: 1px;
      background: linear-gradient(to right, transparent, #6366f1, transparent);
      margin: 32px 0 24px;
      opacity: 0.3;
    }

    .stats-grid {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 18px;
      margin: 20px 0;
    }
    .stats-grid a {
      transition: transform 0.2s;
      display: inline-block;
    }
    .stats-grid a:hover {
      transform: scale(1.02);
    }
    .stats-grid img {
      border-radius: 16px;
      border: 1px solid #1e293b;
      background: #0b1120;
      max-width: 100%;
      height: auto;
    }

    .contact-links {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin: 20px 0 10px;
    }
    .contact-links a {
      background: #111827;
      padding: 10px 28px;
      border-radius: 60px;
      font-weight: 500;
      color: #e2e8f0;
      border: 1px solid #1e293b;
      text-decoration: none;
      transition: 0.25s;
      display: inline-flex;
      align-items: center;
      gap: 10px;
    }
    .contact-links a:hover {
      background: #1e293b;
      border-color: #818cf8;
      box-shadow: 0 0 28px rgba(99, 102, 241, 0.2);
      transform: scale(1.03);
    }

    .quote-block {
      background: linear-gradient(135deg, #0f172a 0%, #111827 100%);
      border-left: 4px solid #6366f1;
      padding: 20px 28px;
      border-radius: 16px;
      margin: 20px 0;
      font-style: italic;
      color: #cbd5e1;
      box-shadow: 0 8px 20px -8px #00000050;
    }

    .snake-wrap {
      background: #0b1120;
      border-radius: 24px;
      padding: 10px 0;
      margin: 20px 0;
      border: 1px solid #1e293b;
      overflow: hidden;
    }
    .snake-wrap img {
      width: 100%;
      display: block;
      border-radius: 12px;
    }

    /* кастом для печатающего текста */
    .typing-demo {
      display: inline-block;
      border-right: 2px solid #818cf8;
      white-space: nowrap;
      overflow: hidden;
      animation: blinkCursor 0.9s step-end infinite;
    }
    @keyframes blinkCursor {
      0%, 100% { border-color: #818cf8; }
      50% { border-color: transparent; }
    }

    /* адаптив */
    @media (max-width: 600px) {
      .container { padding: 16px 8px; }
      .terminal-box { padding: 14px 12px; font-size: 12px; }
      .grid-4 { grid-template-columns: 1fr 1fr; }
    }
  </style>
</head>
<body>
<div class="container">

  <!-- ШАПКА с волной и анимацией -->
  <div class="fade-in delay-1" style="text-align:center;">
    <img src="https://capsule-render.vercel.app/api?type=waving&height=260&section=header&text=runfalse&fontSize=86&fontAlignY=38&fontColor=ffffff&animation=fadeIn&color=0:030712,35:111827,70:312e81,100:6366f1" width="100%" alt="header" style="border-radius: 20px 20px 0 0;"/>
  </div>

  <!-- Тайпинг-анимация -->
  <div class="fade-in delay-1" style="text-align:center; margin: 10px 0 6px;">
    <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=21&duration=2600&pause=900&color=818CF8&center=true&vCenter=true&width=850&lines=Разрабатываю+вещи%2C+которыми+приятно+пользоваться.;Сайты+%E2%80%A2+Backend+%E2%80%A2+API+%E2%80%A2+Автоматизация;TypeScript+%2B+Node.js+%2B+Python;Идея+%E2%86%92+Архитектура+%E2%86%92+Код+%E2%86%92+Результат" alt="Typing animation" style="max-width:100%;"/>
  </div>

  <!-- Бейджи -->
  <div class="badge-group fade-in delay-2">
    <span class="badge">⚡ РАЗРАБОТКА</span>
    <span class="badge">🛠 BACKEND</span>
    <span class="badge">🤖 AUTOMATION</span>
    <span class="badge">🔷 SYSTEMS</span>
  </div>

  <!-- Счётчик -->
  <div style="text-align:center; margin: 6px 0 16px;" class="fade-in delay-2">
    <img src="https://komarev.com/ghpvc/?username=runfalse&label=ЗАШЛИ_ПОСМОТРЕТЬ&color=6366f1&style=flat-square" alt="views" />
  </div>

  <hr class="divider">

  <!-- Приветствие в терминальном стиле (анимировано) -->
  <div class="terminal-box fade-in delay-2" style="text-align:center;">
    <div style="font-size: 15px; color: #a5b4fc;">╭──────────────────────────────────────────────────────────────╮</div>
    <div style="font-size: 15px; color: #a5b4fc;">│                                                              │</div>
    <div style="font-size: 18px; font-weight: 600; color: #e2e8f0; letter-spacing: 2px;">│                     <span class="glow-text">П Р И В Е Т</span> .                            │</div>
    <div style="font-size: 15px; color: #a5b4fc;">│                                                              │</div>
    <div style="font-size: 16px; color: #f1f5f9;">│                    <span style="color:#818cf8;">Я — KIRILL / runfalse</span>                     │</div>
    <div style="font-size: 15px; color: #a5b4fc;">│                                                              │</div>
    <div style="font-size: 14px; color: #94a3b8;">│       web developer • backend • automation • systems        │</div>
    <div style="font-size: 15px; color: #a5b4fc;">│                                                              │</div>
    <div style="font-size: 15px; color: #a5b4fc;">╰──────────────────────────────────────────────────────────────╯</div>
  </div>

  <!-- 01 / немного обо мне -->
  <div class="fade-in delay-3">
    <h2 style="color:#818cf8; font-weight:400; margin:28px 0 12px; letter-spacing:1px;">`01 / немного обо мне`</h2>
    <p style="color:#cbd5e1; line-height:1.7; font-size:15px; margin-bottom:14px;">
      Я разработчик, который любит превращать идеи в <strong style="color:#a5b4fc;">полноценные работающие продукты</strong>.
      Не просто код, а цельная система:
    </p>
    <div class="terminal-box" style="font-size:14px; background:#0b1426;">
      <span style="color:#818cf8;">идея</span> <span style="color:#64748b;">↓</span><br>
      <span style="color:#818cf8;">архитектура</span> <span style="color:#64748b;">↓</span><br>
      <span style="color:#818cf8;">интерфейс</span> <span style="color:#64748b;">↓</span><br>
      <span style="color:#818cf8;">backend</span> <span style="color:#64748b;">↓</span><br>
      <span style="color:#818cf8;">database</span> <span style="color:#64748b;">↓</span><br>
      <span style="color:#818cf8;">API / интеграции</span> <span style="color:#64748b;">↓</span><br>
      <span style="color:#818cf8;">автоматизация</span> <span style="color:#64748b;">↓</span><br>
      <span style="color:#a5b4fc; font-weight:600;">✔ готовый продукт</span>
    </div>
    <p style="color:#94a3b8; font-size:14px; margin-top:10px;">
      Основной стек — <strong style="color:#cbd5e1;">TypeScript / JavaScript / Node.js / Python</strong>.
      Обожаю проекты, где нужно соединять несколько технологий в одну систему.
    </p>
  </div>

  <hr class="divider">

  <!-- 02 / стек с иконками -->
  <div class="fade-in delay-3" style="text-align:center;">
    <h2 style="color:#818cf8; font-weight:400; margin:10px 0 6px;">`02 / мой стек`</h2>
    <div style="margin:14px 0;">
      <img src="https://skillicons.dev/icons?i=ts,js,nodejs,python,php,html,css,nextjs,react,mysql,git,github,linux,docker&perline=7&theme=dark" alt="stack" style="max-width:100%; border-radius:20px;"/>
    </div>
    <div class="terminal-box" style="text-align:left; max-width:380px; margin:10px auto; font-size:13px;">
      <span style="color:#a5b4fc;">╭───────────────────────╮</span><br>
      <span style="color:#a5b4fc;">│                       │</span><br>
      <span style="color:#f1f5f9;">│  ЯЗЫКИ                │</span><br>
      <span style="color:#64748b;">│  ───────────────────  │</span><br>
      <span style="color:#cbd5e1;">│  TypeScript           │</span><br>
      <span style="color:#cbd5e1;">│  JavaScript           │</span><br>
      <span style="color:#cbd5e1;">│  Python               │</span><br>
      <span style="color:#cbd5e1;">│  PHP                  │</span><br>
      <span style="color:#a5b4fc;">│                       │</span><br>
      <span style="color:#f1f5f9;">│  BACKEND              │</span><br>
      <span style="color:#64748b;">│  ───────────────────  │</span><br>
      <span style="color:#cbd5e1;">│  Node.js              │</span><br>
      <span style="color:#cbd5e1;">│  REST API             │</span><br>
      <span style="color:#cbd5e1;">│  MySQL                │</span><br>
      <span style="color:#a5b4fc;">│                       │</span><br>
      <span style="color:#f1f5f9;">│  FRONTEND             │</span><br>
      <span style="color:#64748b;">│  ───────────────────  │</span><br>
      <span style="color:#cbd5e1;">│  HTML / CSS           │</span><br>
      <span style="color:#cbd5e1;">│  React                │</span><br>
      <span style="color:#cbd5e1;">│  Next.js              │</span><br>
      <span style="color:#a5b4fc;">│                       │</span><br>
      <span style="color:#a5b4fc;">╰───────────────────────╯</span>
    </div>
  </div>

  <hr class="divider">

  <!-- 03 / что я делаю (карточки) -->
  <div class="fade-in delay-4">
    <h2 style="color:#818cf8; font-weight:400; text-align:center; margin:8px 0 12px;">`03 / что я делаю`</h2>
    <div class="grid-4">
      <div class="grid-card"><h4>◈ Сайты</h4><p>Современные сайты, лендинги, кабинеты и веб-приложения.</p></div>
      <div class="grid-card"><h4>◈ Backend</h4><p>API, серверная логика, авторизация, базы данных и архитектура.</p></div>
      <div class="grid-card"><h4>◈ Автоматизация</h4><p>Скрипты, парсеры, боты и автоматизация рутинных процессов.</p></div>
      <div class="grid-card"><h4>◈ Интеграции</h4><p>Discord, Telegram, внешние API и сторонние сервисы.</p></div>
    </div>
  </div>

  <hr class="divider">

  <!-- 04 / проекты -->
  <div class="fade-in delay-4">
    <h2 style="color:#818cf8; font-weight:400; text-align:center; margin:8px 0 12px;">`04 / избранные проекты`</h2>
    
    <div class="terminal-box" style="margin-bottom:16px;">
      <h3 style="color:#a5b4fc; font-weight:500;">`01` — Hardy FamQ</h3>
      <p style="color:#94a3b8; font-size:14px;">Большая система, объединяющая <strong style="color:#cbd5e1;">Discord-бота, сайт, личный кабинет, админ-панель и MySQL</strong>.</p>
      <div style="background:#0b1120; padding:12px; border-radius:12px; margin:10px 0; font-size:13px; border:1px solid #1e293b;">
        <span style="color:#818cf8;">Discord</span> <span style="color:#64748b;">→</span> Bot · Roles · Events <span style="color:#64748b;">→</span> <span style="color:#818cf8;">Backend</span> <span style="color:#64748b;">→</span> Website + Admin Panel <span style="color:#64748b;">↔</span> <span style="color:#a5b4fc;">MySQL</span>
      </div>
      <div style="display:flex; gap:10px; flex-wrap:wrap; margin-top:6px;">
        <span class="badge">Discord API</span><span class="badge">Node.js</span><span class="badge">JavaScript</span><span class="badge">MySQL</span><span class="badge">REST</span>
      </div>
    </div>

    <div class="terminal-box" style="margin-bottom:16px;">
      <h3 style="color:#a5b4fc; font-weight:500;">`02` — AI Call Platform</h3>
      <p style="color:#94a3b8; font-size:14px;">Desktop-приложение для автоматизации звонков и работы с данными.</p>
      <div style="background:#0b1120; padding:12px; border-radius:12px; margin:10px 0; font-size:13px; border:1px solid #1e293b;">
        <span style="color:#818cf8;">Excel</span> <span style="color:#64748b;">→</span> Импорт <span style="color:#64748b;">→</span> Обработка <span style="color:#64748b;">→</span> Логика звонка <span style="color:#64748b;">→</span> Голос/текст <span style="color:#64748b;">→</span> Результат <span style="color:#64748b;">→</span> Логи
      </div>
      <div style="display:flex; gap:10px; flex-wrap:wrap; margin-top:6px;">
        <span class="badge">Python</span><span class="badge">PySide6</span><span class="badge">Excel</span><span class="badge">Automation</span>
      </div>
    </div>

    <div class="terminal-box">
      <h3 style="color:#a5b4fc; font-weight:500;">`03` — Web Projects</h3>
      <p style="color:#94a3b8; font-size:14px;">Разработка сайтов и внутренних систем с нуля.</p>
      <div style="background:#0b1120; padding:12px; border-radius:12px; margin:10px 0; font-size:13px; border:1px solid #1e293b;">
        <span style="color:#818cf8;">UI/UX</span> <span style="color:#64748b;">→</span> Frontend <span style="color:#64748b;">→</span> Backend <span style="color:#64748b;">→</span> Database <span style="color:#64748b;">→</span> API <span style="color:#64748b;">→</span> Deploy
      </div>
    </div>
  </div>

  <hr class="divider">

  <!-- 05 / подход -->
  <div class="fade-in delay-5" style="text-align:center;">
    <h2 style="color:#818cf8; font-weight:400;">`05 / как я подхожу к разработке`</h2>
    <div style="display:flex; flex-wrap:wrap; justify-content:center; gap:8px; margin:16px 0 10px; font-size:14px;">
      <span class="badge" style="background:#0f172a;">ИДЕЯ</span>
      <span style="color:#475569;">⬇</span>
      <span class="badge" style="background:#0f172a;">АРХИТЕКТУРА</span>
      <span style="color:#475569;">⬇</span>
      <span class="badge" style="background:#0f172a;">CODE</span>
      <span style="color:#475569;">⬇</span>
      <span class="badge" style="background:#0f172a;">TESTING</span>
      <span style="color:#475569;">⬇</span>
      <span class="badge" style="background:#0f172a;">OPTIMIZATION</span>
      <span style="color:#475569;">⬇</span>
      <span class="badge" style="background:#6366f1; color:#fff;">PRODUCTION</span>
    </div>
    <p style="color:#a5b4fc; font-size:16px; letter-spacing:1px;">✨ не просто работает — работает нормально.</p>
  </div>

  <hr class="divider">

  <!-- 06 / stats -->
  <div class="fade-in delay-5" style="text-align:center;">
    <h2 style="color:#818cf8; font-weight:400;">`06 / github stats`</h2>
    <div class="stats-grid">
      <a href="https://github.com/runfalse"><img src="https://github-readme-stats.vercel.app/api?username=runfalse&show_icons=true&hide_border=true&bg_color=00000000&title_color=818cf8&icon_color=6366f1&text_color=94a3b8&include_all_commits=true&count_private=true" alt="stats" /></a>
      <a href="https://github.com/runfalse"><img src="https://github-readme-stats.vercel.app/api/top-langs/?username=runfalse&layout=compact&hide_border=true&bg_color=00000000&title_color=818cf8&text_color=94a3b8&langs_count=8" alt="langs" /></a>
    </div>
    <div style="margin:12px 0;">
      <img src="https://streak-stats.demolab.com?user=runfalse&hide_border=true&background=00000000&ring=6366f1&fire=818cf8&currStreakLabel=818cf8&sideLabels=94a3b8&dates=64748b" alt="streak" style="max-width:100%;" />
    </div>
  </div>

  <hr class="divider">

  <!-- 07 / активность -->
  <div class="fade-in delay-5" style="text-align:center;">
    <h2 style="color:#818cf8; font-weight:400;">`07 / активность`</h2>
    <div style="margin:12px 0;">
      <img src="https://github-readme-activity-graph.vercel.app/graph?username=runfalse&bg_color=00000000&color=94a3b8&line=6366f1&point=ffffff&area=true&hide_border=true&custom_title=Активность%20на%20GitHub" alt="activity" style="width:100%; border-radius:16px;" />
    </div>
  </div>

  <hr class="divider">

  <!-- 08 / trophies -->
  <div class="fade-in delay-5" style="text-align:center;">
    <h2 style="color:#818cf8; font-weight:400;">`08 / trophies`</h2>
    <div style="margin:12px 0; overflow-x:auto;">
      <img src="https://github-profile-trophy.vercel.app/?username=runfalse&theme=darkhub&no-frame=true&no-bg=true&margin-w=10&column=7" alt="trophy" style="max-width:100%;" />
    </div>
  </div>

  <hr class="divider">

  <!-- 09 / сейчас -->
  <div class="fade-in delay-6" style="text-align:center;">
    <h2 style="color:#818cf8; font-weight:400;">`09 / сейчас`</h2>
    <div class="terminal-box" style="max-width:600px; margin:10px auto; font-size:14px; text-align:left;">
      <span style="color:#a5b4fc;">╭──────────────────────────────────────────────────────────────╮</span><br>
      <span style="color:#a5b4fc;">│                                                              │</span><br>
      <span style="color:#e2e8f0;">│  🔭  Делаю          веб-приложения и backend-системы         │</span><br>
      <span style="color:#e2e8f0;">│  ⚡  Люблю           автоматизацию и сложные интеграции      │</span><br>
      <span style="color:#e2e8f0;">│  🧠  Изучаю          архитектуру и новые инструменты        │</span><br>
      <span style="color:#e2e8f0;">│  🛠️  Использую      TypeScript / Node.js / Python            │</span><br>
      <span style="color:#e2e8f0;">│  🚀  Двигаюсь        от идеи к готовому продукту            │</span><br>
      <span style="color:#a5b4fc;">│                                                              │</span><br>
      <span style="color:#a5b4fc;">╰──────────────────────────────────────────────────────────────╯</span>
    </div>
  </div>

  <hr class="divider">

  <!-- 10 / snake -->
  <div class="fade-in delay-6" style="text-align:center;">
    <h2 style="color:#818cf8; font-weight:400;">`10 / contribution snake`</h2>
    <div class="snake-wrap">
      <img src="https://raw.githubusercontent.com/Platane/snk/output/github-contribution-grid-snake-dark.svg" alt="snake" />
    </div>
  </div>

  <hr class="divider">

  <!-- 11 / философия -->
  <div class="fade-in delay-6" style="text-align:center;">
    <h2 style="color:#818cf8; font-weight:400;">`11 / немного философии`</h2>
    <div class="quote-block">
      <p style="font-size:16px; line-height:1.6;">«Хороший код — это не тот, который сложно написать.<br>
      <span style="color:#a5b4fc;">Хороший код — тот, который потом легко поддерживать.»</span></p>
      <div style="margin-top:12px; color:#64748b; font-size:13px; letter-spacing:2px;">build → break → fix → improve → repeat</div>
    </div>
  </div>

  <hr class="divider">

  <!-- 12 / контакты -->
  <div class="fade-in delay-6" style="text-align:center; padding-bottom:12px;">
    <h2 style="color:#818cf8; font-weight:400;">`12 / контакты`</h2>
    <div class="contact-links">
      <a href="https://github.com/runfalse"><span style="font-size:20px;">🐙</span> GITHUB</a>
      <a href="#"><span style="font-size:20px;">✈️</span> TELEGRAM</a>
    </div>
    <p style="color:#a5b4fc; margin:16px 0 6px; font-size:18px; letter-spacing:1px;">есть идея?</p>
    <p style="color:#94a3b8; font-size:15px; margin-bottom:20px;"><strong style="color:#cbd5e1;">давай превратим её в код.</strong></p>
    <!-- подвал-волна -->
    <img src="https://capsule-render.vercel.app/api?type=waving&height=160&section=footer&color=0:6366f1,40:312e81,75:111827,100:030712&animation=fadeIn" width="100%" alt="footer" style="border-radius:0 0 20px 20px; margin-top:8px;" />
  </div>

</div>
</body>
</html>
