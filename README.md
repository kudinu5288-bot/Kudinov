<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="slides-format" content="viewport" />
  <title>Вдохновение в эпоху перемен</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
  <style type="text/tailwindcss">
    @theme {
      --color-bg: #0c1020;
      --color-bg-deep: #070b16;
      --color-surface: #171d34;
      --color-text: #f8fafc;
      --color-text-secondary: #dbe4f0;
      --color-text-muted: #8fa2c0;
      --color-accent-1: #8b5cf6;
      --color-accent-2: #22d3ee;
      --color-accent-3: #f59e0b;
      --color-glass-bg: rgba(255,255,255,0.06);
      --color-glass-border: rgba(255,255,255,0.10);
      --color-vignette: rgba(0,0,0,0.42);
      --font-display: 'Instrument Serif', Georgia, serif;
      --font-body: 'Inter', sans-serif;
    }
  </style>
  <style>
    :root { --color-bg: #0c1020; --color-text: #f8fafc; --glow-color-rgb: 139,92,246; }
    * { box-sizing: border-box; }
    html, body { margin: 0; background: var(--color-bg); }
    body { font-family: var(--font-body); color: var(--color-text); overflow: hidden; width: 100vw; height: 100vh; }
    .deck { width: 100vw; height: 100vh; position: relative; }
    .slide { position: absolute; inset: 0; background: var(--color-bg); display: flex; align-items: center; justify-content: center; opacity: 0; transform: scale(.96); transition: opacity .7s ease, transform .7s ease; pointer-events: none; overflow: hidden; }
    .slide.active { opacity: 1; transform: scale(1); pointer-events: all; }
    .slide > .content { position: relative; z-index: 2; width: 100%; max-width: 1180px; padding: clamp(1.5rem, 4vw, 4rem); }
    .nav-controls { position: fixed; bottom: 24px; left: 50%; transform: translateX(-50%); display: flex; align-items: center; gap: 14px; z-index: 100; background: rgba(255,255,255,0.08); backdrop-filter: blur(10px); padding: 10px 20px; border-radius: 999px; border: 1px solid rgba(255,255,255,0.12); }
    .nav-btn { width: 38px; height: 38px; border-radius: 50%; border: none; cursor: pointer; background: rgba(255,255,255,0.07); color: #fff; font-size: 20px; }
    .slide-dots { display: flex; gap: 8px; }
    .dot { width: 10px; height: 10px; border-radius: 50%; background: rgba(255,255,255,0.2); cursor: pointer; transition: .3s; }
    .dot.active { background: var(--color-accent-2); transform: scale(1.25); }
    .slide-counter { min-width: 44px; text-align: center; color: var(--color-text-muted); font-size: 12px; }
    .reveal { opacity: 0; transform: translateY(20px); }
    .gradient-mesh { position: absolute; inset: 0; z-index: 0; overflow: hidden; pointer-events: none; }
    .blob { position: absolute; border-radius: 50%; filter: blur(90px); animation: float-slow 16s ease-in-out infinite; }
    .blob:nth-child(2) { animation: float-drift 19s ease-in-out infinite; }
    .blob:nth-child(3) { animation: float-slow 22s ease-in-out infinite reverse; }
    @keyframes float-slow { 0% { transform: translate(0,0) scale(1);} 25% { transform: translate(60px,-40px) scale(1.08);} 50% { transform: translate(-30px,35px) scale(.94);} 75% { transform: translate(45px,25px) scale(1.05);} 100% { transform: translate(0,0) scale(1);} }
    @keyframes float-drift { 0% { transform: translate(0,0) scale(1) rotate(0deg);} 33% { transform: translate(-40px,-60px) scale(1.12) rotate(3deg);} 66% { transform: translate(50px,20px) scale(.9) rotate(-2deg);} 100% { transform: translate(0,0) scale(1) rotate(0deg);} }
    @keyframes float { 0%,100% { transform: translateY(0);} 50% { transform: translateY(-14px);} }
    .slide::before { content:''; position:absolute; inset:0; z-index:1; pointer-events:none; background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.7' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.05'/%3E%3C/svg%3E"); opacity:.03; mix-blend-mode:overlay; }
    .slide::after { content:''; position:absolute; inset:0; z-index:1; pointer-events:none; background: radial-gradient(ellipse at center, transparent 50%, var(--color-vignette) 100%); }
    .mouse-spotlight { position:fixed; inset:0; z-index:99; pointer-events:none; }
    .card { background: rgba(255,255,255,0.07); border: 1px solid rgba(255,255,255,0.12); backdrop-filter: blur(14px); border-radius: 24px; }
    .pill { display:inline-flex; padding:.45rem .9rem; border-radius:999px; background: rgba(255,255,255,0.09); border:1px solid rgba(255,255,255,0.12); color: var(--color-text-secondary); font-size:.9rem; }
    .quote-line { border-left: 4px solid var(--color-accent-2); padding-left: 18px; }
    .deco-shape { position:absolute; z-index:0; border-radius:999px; opacity:.12; filter: blur(4px); }
    .grid-auto { display:grid; gap: 22px; }
    .particle-canvas, .particle-canvas-ambient { position:absolute; inset:0; z-index:1; }
    @media (prefers-reduced-motion: reduce) { * { animation-duration: .01ms !important; transition-duration: .2s !important; } }
  </style>
</head>
<body>
<div class="mouse-spotlight"></div>
<div class="deck">

  <section class="slide active" data-slide="1">
    <div class="gradient-mesh">
      <div class="blob" style="width:460px;height:460px;top:-120px;right:-90px;background:var(--color-accent-1);opacity:.16"></div>
      <div class="blob" style="width:320px;height:320px;bottom:-90px;left:-60px;background:var(--color-accent-2);opacity:.13"></div>
      <div class="blob" style="width:220px;height:220px;top:44%;left:18%;background:var(--color-accent-3);opacity:.1"></div>
    </div>
    <canvas class="particle-canvas"></canvas>
    <div class="content text-center">
      <div class="text-[110px] mb-5 animate-[float_3s_ease-in-out_infinite] reveal">✨</div>
      <div class="pill mx-auto mb-5 reveal">для подростков поколения Z</div>
      <h1 class="font-display text-[clamp(2.8rem,7vw,5.8rem)] leading-[0.92] tracking-tight mb-5 reveal bg-linear-to-br from-accent-1 via-accent-2 to-accent-3 bg-clip-text text-transparent">Вдохновение<br>в эпоху перемен</h1>
      <p class="text-[clamp(1rem,1.8vw,1.35rem)] text-text-muted uppercase tracking-[6px] reveal">как не сдаться миру, который меняется, а вырасти вместе с ним</p>
    </div>
  </section>

  <section class="slide" data-slide="2">
    <div class="gradient-mesh">
      <div class="blob" style="width:360px;height:360px;top:-70px;right:-70px;background:var(--color-accent-1);opacity:.08"></div>
      <div class="blob" style="width:260px;height:260px;bottom:-60px;left:-40px;background:var(--color-accent-2);opacity:.06"></div>
    </div>
    <div class="deco-shape" data-speed="0.04" style="width:180px;height:180px;right:9%;top:16%;background:rgba(34,211,238,.25)"></div>
    <div class="content">
      <div class="grid grid-cols-2 gap-10 items-center">
        <div>
          <div class="pill mb-5 reveal">слайд-захват</div>
          <h2 class="font-display text-[clamp(2.1rem,4.8vw,4rem)] leading-tight mb-6 reveal">Нас учат бояться перемен.<br>А что, если перемены — это наш материал?</h2>
          <p class="text-xl text-text-secondary leading-relaxed reveal">Мир качает, планы ломаются, новости устают быстрее нас. Но именно в этой нестабильности появляется шанс придумать новый язык, новый формат и новую версию себя.</p>
        </div>
        <div class="card p-10 reveal">
          <div class="text-6xl mb-5">🌀</div>
          <div class="grid-auto">
            <div class="flex gap-4 items-start"><span class="text-accent-2 text-2xl">•</span><p class="text-lg text-text-secondary">Старые сценарии уже не дают чувства полной опоры.</p></div>
            <div class="flex gap-4 items-start"><span class="text-accent-2 text-2xl">•</span><p class="text-lg text-text-secondary">Новый мир требует гибкости, а не идеальной предсказуемости.</p></div>
            <div class="flex gap-4 items-start"><span class="text-accent-2 text-2xl">•</span><p class="text-lg text-text-secondary">Творческий человек умеет превращать хаос в форму.</p></div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section class="slide" data-slide="3">
    <div class="gradient-mesh">
      <div class="blob" style="width:340px;height:340px;top:-60px;left:-80px;background:var(--color-accent-1);opacity:.08"></div>
      <div class="blob" style="width:260px;height:260px;bottom:-70px;right:-50px;background:var(--color-accent-3);opacity:.06"></div>
    </div>
    <div class="content">
      <div class="pill mb-6 reveal">признание состояния</div>
      <h2 class="font-display text-[clamp(2rem,4.2vw,3.8rem)] mb-8 reveal">Иногда кажется: слишком много всего</h2>
      <div class="grid grid-cols-2 gap-6 mt-6">
        <div class="card p-8 reveal"><div class="text-4xl mb-4">📱</div><h3 class="text-2xl font-bold mb-3">Информационный шум</h3><p class="text-lg text-text-secondary">Ты просыпаешься — и мир уже требует реакции. Лента не дает тишины, а мозгу нужна пауза.</p></div>
        <div class="card p-8 reveal"><div class="text-4xl mb-4">🎯</div><h3 class="text-2xl font-bold mb-3">Давление ожиданий</h3><p class="text-lg text-text-secondary">Нужно быть успешным, ярким, собранным и постоянно «в ресурсе» — и это выматывает.</p></div>
        <div class="card p-8 reveal"><div class="text-4xl mb-4">🪞</div><h3 class="text-2xl font-bold mb-3">Сравнение себя</h3><p class="text-lg text-text-secondary">Кажется, что у кого-то уже есть путь, стиль, команда, а у тебя пока только вопросы.</p></div>
        <div class="card p-8 reveal"><div class="text-4xl mb-4">💭</div><h3 class="text-2xl font-bold mb-3">Страх не успеть</h3><p class="text-lg text-text-secondary">Иногда тревога говорит: «ты опаздываешь». Но тревога не всегда говорит правду.</p></div>
      </div>
    </div>
  </section>

  <section class="slide" data-slide="4">
    <div class="gradient-mesh">
      <div class="blob" style="width:300px;height:300px;top:10%;right:5%;background:var(--color-accent-2);opacity:.07"></div>
      <div class="blob" style="width:250px;height:250px;bottom:5%;left:8%;background:var(--color-accent-1);opacity:.07"></div>
    </div>
    <div class="content">
      <div class="pill mb-5 reveal">переворот взгляда</div>
      <h2 class="font-display text-[clamp(2.1rem,4.5vw,3.9rem)] mb-8 reveal">Изменчивость — не только стресс. Это еще и шанс</h2>
      <div class="grid grid-cols-3 gap-6">
        <div class="card p-8 reveal"><div class="text-5xl mb-4">🛤️</div><h3 class="text-2xl font-bold mb-3">Нет готового пути</h3><p class="text-lg text-text-secondary">Значит, можно не копировать чужое, а создать свой маршрут.</p></div>
        <div class="card p-8 reveal"><div class="text-5xl mb-4">🧩</div><h3 class="text-2xl font-bold mb-3">Ломаются форматы</h3><p class="text-lg text-text-secondary">Значит, у тебя есть право придумать новую форму, новый жанр, новый ход.</p></div>
        <div class="card p-8 reveal"><div class="text-5xl mb-4">🚀</div><h3 class="text-2xl font-bold mb-3">Нужна гибкость</h3><p class="text-lg text-text-secondary">А гибкость — это одна из главных суперсил творческого человека.</p></div>
      </div>
    </div>
  </section>

  <section class="slide" data-slide="5">
    <div class="gradient-mesh">
      <div class="blob" style="width:320px;height:320px;top:-40px;right:-60px;background:var(--color-accent-3);opacity:.08"></div>
      <div class="blob" style="width:220px;height:220px;bottom:-30px;left:-50px;background:var(--color-accent-2);opacity:.06"></div>
    </div>
    <div class="content">
      <div class="grid grid-cols-[1.1fr_0.9fr] gap-10 items-center">
        <div>
          <div class="pill mb-5 reveal">зачем творчество</div>
          <h2 class="font-display text-[clamp(2.1rem,4.8vw,3.8rem)] mb-6 reveal">Творчество — это не «для художников». Это способ не потерять себя</h2>
          <div class="quote-line text-2xl text-text-secondary leading-relaxed reveal">Через творчество человек не прячет эмоции, а проживает их. Не тонет в хаосе, а собирает из него смысл.</div>
        </div>
        <div class="grid grid-cols-2 gap-5">
          <div class="card p-6 reveal"><div class="text-3xl mb-3">🎭</div><p class="text-lg">Сцена и театр</p></div>
          <div class="card p-6 reveal"><div class="text-3xl mb-3">🎵</div><p class="text-lg">Музыка и звук</p></div>
          <div class="card p-6 reveal"><div class="text-3xl mb-3">🎬</div><p class="text-lg">Видео и монтаж</p></div>
          <div class="card p-6 reveal"><div class="text-3xl mb-3">📝</div><p class="text-lg">Тексты и смыслы</p></div>
          <div class="card p-6 reveal"><div class="text-3xl mb-3">🎨</div><p class="text-lg">Дизайн и визуал</p></div>
          <div class="card p-6 reveal"><div class="text-3xl mb-3">🤝</div><p class="text-lg">Проекты и инициативы</p></div>
        </div>
      </div>
    </div>
  </section>

  <section class="slide" data-slide="6">
    <div class="gradient-mesh">
      <div class="blob" style="width:300px;height:300px;top:-60px;right:10%;background:var(--color-accent-1);opacity:.08"></div>
      <div class="blob" style="width:240px;height:240px;bottom:-60px;left:5%;background:var(--color-accent-2);opacity:.06"></div>
    </div>
    <div class="content">
      <div class="pill mb-5 reveal">новый угол зрения</div>
      <h2 class="font-display text-[clamp(2rem,4.4vw,3.8rem)] mb-8 reveal">Один и тот же мир можно читать по-разному</h2>
      <div class="grid grid-cols-2 gap-8">
        <div class="card p-8 reveal" style="border-color: rgba(245,158,11,.28)">
          <div class="text-sm uppercase tracking-[4px] text-text-muted mb-4">взгляд из бессилия</div>
          <div class="grid-auto">
            <p class="text-xl">«Все слишком нестабильно»</p>
            <p class="text-xl">«Ничего непонятно»</p>
            <p class="text-xl">«Слишком много проблем»</p>
            <p class="text-xl">«Я не успеваю за миром»</p>
          </div>
        </div>
        <div class="card p-8 reveal" style="border-color: rgba(34,211,238,.32)">
          <div class="text-sm uppercase tracking-[4px] text-text-muted mb-4">взгляд из авторства</div>
          <div class="grid-auto">
            <p class="text-xl">«Значит, можно быть гибким и первым пробовать новое»</p>
            <p class="text-xl">«Значит, я могу задавать свои вопросы»</p>
            <p class="text-xl">«Значит, мое поколение может придумать решения»</p>
            <p class="text-xl">«Значит, мне важно не копировать, а создавать»</p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section class="slide" data-slide="7">
    <div class="gradient-mesh">
      <div class="blob" style="width:360px;height:360px;top:-90px;left:-80px;background:var(--color-accent-1);opacity:.08"></div>
      <div class="blob" style="width:260px;height:260px;bottom:-70px;right:-50px;background:var(--color-accent-2);opacity:.07"></div>
    </div>
    <canvas class="particle-canvas-ambient"></canvas>
    <div class="content">
      <div class="pill mb-5 reveal">про поколение Z</div>
      <h2 class="font-display text-[clamp(2rem,4.4vw,3.8rem)] mb-8 reveal">Ваше поколение умеет то, чего не умели раньше</h2>
      <div class="grid grid-cols-3 gap-6">
        <div class="card p-7 reveal"><div class="text-4xl mb-3">⚡</div><h3 class="text-xl font-bold mb-2">Считывать перемены</h3><p class="text-text-secondary">Вы быстро замечаете, что мир сменил правила игры.</p></div>
        <div class="card p-7 reveal"><div class="text-4xl mb-3">🎛️</div><h3 class="text-xl font-bold mb-2">Смешивать форматы</h3><p class="text-text-secondary">Текст, звук, видео, мем, сцена — для вас это один язык.</p></div>
        <div class="card p-7 reveal"><div class="text-4xl mb-3">🧠</div><h3 class="text-xl font-bold mb-2">Чувствовать фальшь</h3><p class="text-text-secondary">Вы сразу видите, где с вами говорят не по-настоящему.</p></div>
        <div class="card p-7 reveal"><div class="text-4xl mb-3">🌐</div><h3 class="text-xl font-bold mb-2">Объединяться вокруг идей</h3><p class="text-text-secondary">Вам важно быть частью смысла, а не только системы.</p></div>
        <div class="card p-7 reveal"><div class="text-4xl mb-3">🎨</div><h3 class="text-xl font-bold mb-2">Создавать атмосферу</h3><p class="text-text-secondary">Вы умеете говорить не только словами, но и эстетикой.</p></div>
        <div class="card p-7 reveal"><div class="text-4xl mb-3">🔓</div><h3 class="text-xl font-bold mb-2">Искать свое</h3><p class="text-text-secondary">Ваш путь может быть нестандартным — и в этом его сила.</p></div>
      </div>
    </div>
  </section>

  <section class="slide" data-slide="8">
    <div class="gradient-mesh">
      <div class="blob" style="width:340px;height:340px;top:-80px;right:-80px;background:var(--color-accent-3);opacity:.08"></div>
      <div class="blob" style="width:240px;height:240px;bottom:-60px;left:-40px;background:var(--color-accent-1);opacity:.06"></div>
    </div>
    <div class="content">
      <div class="pill mb-5 reveal">слайд-вдохновение</div>
      <h2 class="font-display text-[clamp(2rem,4.5vw,3.9rem)] mb-8 reveal">Из кризиса часто рождается стиль, идея, движение</h2>
      <div class="grid grid-cols-[0.95fr_1.05fr] gap-8 items-center">
        <div class="card p-10 reveal text-center">
          <div class="text-[120px] leading-none mb-3">🔥</div>
          <p class="text-2xl text-text-secondary">Когда человеку тесно в старом мире, он начинает создавать новый.</p>
        </div>
        <div class="grid-auto">
          <div class="card p-7 reveal"><p class="text-xl text-text-secondary">Неидеальные времена часто становятся точкой рождения сильных смыслов.</p></div>
          <div class="card p-7 reveal"><p class="text-xl text-text-secondary">Самые живые проекты начинаются с вопроса: «А как можно иначе?»</p></div>
          <div class="card p-7 reveal"><p class="text-xl text-text-secondary">Переживание может стать сценой, образом, текстом, роликом, командой, движением.</p></div>
        </div>
      </div>
    </div>
  </section>

  <section class="slide" data-slide="9">
    <div class="gradient-mesh">
      <div class="blob" style="width:360px;height:360px;top:-90px;left:-80px;background:var(--color-accent-2);opacity:.08"></div>
      <div class="blob" style="width:260px;height:260px;bottom:-70px;right:-50px;background:var(--color-accent-1);opacity:.06"></div>
    </div>
    <div class="content">
      <div class="pill mb-5 reveal">что делать</div>
      <h2 class="font-display text-[clamp(2rem,4.4vw,3.8rem)] mb-8 reveal">Что делать, когда мир давит?</h2>
      <div class="grid grid-cols-5 gap-4">
        <div class="card p-6 reveal"><div class="text-3xl mb-3">1</div><p class="text-lg text-text-secondary">Остановиться и честно назвать, что ты чувствуешь.</p></div>
        <div class="card p-6 reveal"><div class="text-3xl mb-3">2</div><p class="text-lg text-text-secondary">Не жить только в плохих новостях и не кормить тревогу бесконечно.</p></div>
        <div class="card p-6 reveal"><div class="text-3xl mb-3">3</div><p class="text-lg text-text-secondary">Искать людей, с которыми можно не просто обсуждать, а создавать.</p></div>
        <div class="card p-6 reveal"><div class="text-3xl mb-3">4</div><p class="text-lg text-text-secondary">Превращать переживание в идею: сцену, текст, ролик, проект.</p></div>
        <div class="card p-6 reveal"><div class="text-3xl mb-3">5</div><p class="text-lg text-text-secondary">Делать маленький шаг сейчас, а не ждать идеального состояния.</p></div>
      </div>
    </div>
  </section>

  <section class="slide" data-slide="10">
    <div class="gradient-mesh">
      <div class="blob" style="width:320px;height:320px;top:-60px;right:-50px;background:var(--color-accent-1);opacity:.08"></div>
      <div class="blob" style="width:230px;height:230px;bottom:-40px;left:-50px;background:var(--color-accent-3);opacity:.06"></div>
    </div>
    <div class="content">
      <div class="pill mb-5 reveal">про команду</div>
      <h2 class="font-display text-[clamp(2rem,4.4vw,3.8rem)] mb-8 reveal">Поодиночке страшно. Вместе — уже движение</h2>
      <div class="grid grid-cols-2 gap-8">
        <div class="card p-8 reveal">
          <div class="text-5xl mb-4">🤝</div>
          <p class="text-2xl leading-relaxed text-text-secondary">Команда помогает не проваливаться в апатию. Рядом с другими искрами появляется огонь.</p>
        </div>
        <div class="grid-auto">
          <div class="card p-6 reveal"><p class="text-lg text-text-secondary">Идеи рождаются быстрее, когда рядом есть разные взгляды.</p></div>
          <div class="card p-6 reveal"><p class="text-lg text-text-secondary">Поддержка среды дает ощущение: «я не один, я часть чего-то большего».</p></div>
          <div class="card p-6 reveal"><p class="text-lg text-text-secondary">Совместное творчество превращает эмоцию в событие, а мысль — в действие.</p></div>
        </div>
      </div>
    </div>
  </section>

  <section class="slide" data-slide="11">
    <div class="gradient-mesh">
      <div class="blob" style="width:380px;height:380px;top:-100px;right:-90px;background:var(--color-accent-2);opacity:.09"></div>
      <div class="blob" style="width:250px;height:250px;bottom:-60px;left:-30px;background:var(--color-accent-1);opacity:.07"></div>
    </div>
    <canvas class="particle-canvas-ambient"></canvas>
    <div class="content text-center">
      <div class="pill mb-6 reveal">слайд-вызов</div>
      <h2 class="font-display text-[clamp(2.4rem,5.4vw,4.6rem)] leading-tight mb-8 reveal">Не вопрос<br>«что происходит с миром?»<br><span class="bg-linear-to-r from-accent-1 via-accent-2 to-accent-3 bg-clip-text text-transparent">А вопрос «что я могу создать внутри этого мира?»</span></h2>
      <p class="text-2xl text-text-secondary max-w-[900px] mx-auto reveal">Не все зависит от нас. Но всегда что-то зависит от нас. И творчество — один из самых сильных ответов на неопределенность.</p>
    </div>
  </section>

  <section class="slide" data-slide="12">
    <div class="gradient-mesh">
      <div class="blob" style="width:470px;height:470px;top:-120px;right:-90px;background:var(--color-accent-1);opacity:.15"></div>
      <div class="blob" style="width:320px;height:320px;bottom:-100px;left:-70px;background:var(--color-accent-2);opacity:.12"></div>
      <div class="blob" style="width:220px;height:220px;top:42%;left:18%;background:var(--color-accent-3);opacity:.1"></div>
    </div>
    <canvas class="particle-canvas"></canvas>
    <div class="content text-center">
      <div class="text-[110px] mb-5 animate-[float_3s_ease-in-out_infinite] reveal">🌟</div>
      <h2 class="font-display text-[clamp(2.6rem,6vw,5rem)] leading-[0.96] mb-6 reveal bg-linear-to-br from-accent-1 via-accent-2 to-accent-3 bg-clip-text text-transparent">Вдохновение — это не ждать,<br>когда станет легко</h2>
      <p class="text-2xl text-text-secondary max-w-[960px] mx-auto mb-8 reveal">Это увидеть смысл даже в переменах. Не позволить миру сломать твою энергию, а сделать так, чтобы он запустил твой рост.</p>
      <div class="pill mx-auto reveal">твоя энергия может стать идеей, действием и творчеством</div>
    </div>
  </section>
</div>

<div class="nav-controls" aria-label="Навигация по слайдам">
  <button class="nav-btn" onclick="changeSlide(-1)" aria-label="Предыдущий слайд">&#8249;</button>
  <div class="slide-dots" id="dots"></div>
  <button class="nav-btn" onclick="changeSlide(1)" aria-label="Следующий слайд">&#8250;</button>
  <span class="slide-counter" id="counter">1 / 12</span>
</div>

<script>
let current = 1;
const total = document.querySelectorAll('.slide').length;
const dotsContainer = document.getElementById('dots');
const counter = document.getElementById('counter');
for (let i = 1; i <= total; i++) { const dot = document.createElement('div'); dot.className = 'dot' + (i === 1 ? ' active' : ''); dot.onclick = () => goToSlide(i); dotsContainer.appendChild(dot); }
function goToSlide(n) { const prev = document.querySelector('.slide.active'); const next = document.querySelector(`.slide[data-slide="${n}"]`); if (prev) prev.classList.remove('active'); if (next) { next.classList.add('active'); animateSlide(next); } current = n; updateNav(); }
function changeSlide(dir) { let next = current + dir; if (next < 1) next = total; if (next > total) next = 1; goToSlide(next); }
function updateNav() { document.querySelectorAll('.dot').forEach((d, i) => d.classList.toggle('active', i + 1 === current)); counter.textContent = current + ' / ' + total; }
document.addEventListener('keydown', (e) => { if (e.key === 'ArrowRight' || e.key === ' ') { e.preventDefault(); changeSlide(1); } if (e.key === 'ArrowLeft') { e.preventDefault(); changeSlide(-1); } });
let touchStartX = 0;
document.addEventListener('touchstart', (e) => { touchStartX = e.touches[0].clientX; });
document.addEventListener('touchend', (e) => { const diff = touchStartX - e.changedTouches[0].clientX; if (Math.abs(diff) > 50) changeSlide(diff > 0 ? 1 : -1); });
function animateSlide(slide) {
  slide.querySelectorAll('.reveal').forEach((el, i) => {
    el.style.transition = 'none'; el.style.opacity = '0'; el.style.transform = 'translateY(20px)'; el.offsetHeight;
    const delay = i * 0.08; el.style.transition = `opacity 0.36s ease ${delay}s, transform 0.36s ease ${delay}s`; el.style.opacity = '1'; el.style.transform = 'translateY(0px)';
  });
}
document.addEventListener('mousemove', (e) => {
  const spotlight = document.querySelector('.mouse-spotlight');
  spotlight.style.background = `radial-gradient(600px circle at ${e.clientX}px ${e.clientY}px, rgba(139,92,246,0.07), transparent 40%)`;
});
(function(){ let mouseX = window.innerWidth / 2, mouseY = window.innerHeight / 2; const cx = window.innerWidth / 2, cy = window.innerHeight / 2; document.addEventListener('mousemove', e => { mouseX = e.clientX; mouseY = e.clientY; }); (function tick(){ const ox = (mouseX - cx) / cx, oy = (mouseY - cy) / cy; document.querySelectorAll('.deco-shape').forEach(shape => { const speed = parseFloat(shape.dataset.speed) || 0.03; shape.style.transform = `translate(${ox * speed * 100}px, ${oy * speed * 100}px)`; }); requestAnimationFrame(tick); })(); })();
window.initParticles = function(canvas, options) {
  if (!canvas) return; const ctx = canvas.getContext('2d'); canvas.width = canvas.offsetWidth; canvas.height = canvas.offsetHeight; const interactive = options.interactive !== false; const count = options.count || (interactive ? 55 : 18); let mx = -1000, my = -1000; const particles = Array.from({ length: count }, () => ({ x: Math.random() * canvas.width, y: Math.random() * canvas.height, vx: (Math.random() - 0.5) * 0.3, vy: (Math.random() - 0.5) * 0.3, size: Math.random() * 2.5 + 0.8, alpha: Math.random() * 0.35 + 0.1 }));
  if (interactive) { canvas.addEventListener('mousemove', (e) => { const rect = canvas.getBoundingClientRect(); mx = e.clientX - rect.left; my = e.clientY - rect.top; }); canvas.addEventListener('mouseleave', () => { mx = -1000; my = -1000; }); }
  (function animate(){ ctx.clearRect(0,0,canvas.width,canvas.height); particles.forEach(p => { if (interactive) { const dx = p.x - mx, dy = p.y - my, dist = Math.sqrt(dx*dx + dy*dy) || 1; if (dist < 120) { const force = (120 - dist) / 120 * 2; p.vx += (dx / dist) * force * 0.1; p.vy += (dy / dist) * force * 0.1; } } p.vx *= 0.98; p.vy *= 0.98; p.x += p.vx; p.y += p.vy; if (p.x < 0) p.x = canvas.width; if (p.x > canvas.width) p.x = 0; if (p.y < 0) p.y = canvas.height; if (p.y > canvas.height) p.y = 0; ctx.beginPath(); ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2); ctx.fillStyle = `rgba(139,92,246,${p.alpha})`; ctx.fill(); }); requestAnimationFrame(animate); })();
};
document.querySelectorAll('.particle-canvas').forEach(c => window.initParticles(c, { interactive: true, count: 55 }));
document.querySelectorAll('.particle-canvas-ambient').forEach(c => window.initParticles(c, { interactive: false, count: 18 }));
animateSlide(document.querySelector('.slide.active'));
</script>
</body>
</html>
