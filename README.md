<!DOCTYPE html>
<html lang="en" data-theme="light">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Essere Presente Practice</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;700&family=Instrument+Serif:ital@0;1&display=swap" rel="stylesheet">
  <style>
    :root, [data-theme="light"] {
      --text-xs: clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem);
      --text-sm: clamp(0.875rem, 0.8rem + 0.35vw, 1rem);
      --text-base: clamp(1rem, 0.95rem + 0.25vw, 1.125rem);
      --text-lg: clamp(1.125rem, 1rem + 0.75vw, 1.5rem);
      --text-xl: clamp(1.5rem, 1.2rem + 1.25vw, 2.25rem);
      --text-2xl: clamp(2rem, 1.2rem + 2.5vw, 3.5rem);
      --space-1: 0.25rem; --space-2: 0.5rem; --space-3: 0.75rem; --space-4: 1rem; --space-5: 1.25rem; --space-6: 1.5rem; --space-8: 2rem; --space-10: 2.5rem; --space-12: 3rem; --space-16: 4rem;
      --color-bg: #f7f6f2; --color-surface: #f9f8f5; --color-surface-2: #fbfbf9; --color-surface-offset: #edeae5; --color-border: #d4d1ca;
      --color-text: #28251d; --color-text-muted: #6f6c66; --color-text-faint: #9e9b94; --color-text-inverse: #f9f8f4;
      --color-primary: #01696f; --color-primary-hover: #0c4e54; --color-primary-highlight: #d7e7e5;
      --color-success: #437a22; --color-success-highlight: #dce8d5;
      --color-error: #a12c7b; --color-error-highlight: #edd7e4;
      --radius-sm: 0.375rem; --radius-md: 0.5rem; --radius-lg: 0.75rem; --radius-xl: 1rem; --radius-full: 9999px;
      --shadow-sm: 0 1px 2px rgba(40,37,29,0.06); --shadow-md: 0 10px 30px rgba(40,37,29,0.08);
      --font-display: 'Instrument Serif', Georgia, serif; --font-body: 'DM Sans', system-ui, sans-serif;
    }
    [data-theme="dark"] {
      --color-bg: #171614; --color-surface: #1c1b19; --color-surface-2: #201f1d; --color-surface-offset: #2a2927; --color-border: #393836;
      --color-text: #cdccca; --color-text-muted: #9b9893; --color-text-faint: #6d6a65; --color-text-inverse: #171614;
      --color-primary: #4f98a3; --color-primary-hover: #227f8b; --color-primary-highlight: #313b3b;
      --color-success: #6daa45; --color-success-highlight: #364130;
      --color-error: #d163a7; --color-error-highlight: #4a3442;
      --shadow-sm: 0 1px 2px rgba(0,0,0,0.25); --shadow-md: 0 14px 40px rgba(0,0,0,0.35);
    }
    * { box-sizing: border-box; }
    html, body { margin: 0; min-height: 100%; }
    body {
      font-family: var(--font-body);
      font-size: var(--text-base);
      color: var(--color-text);
      background: radial-gradient(circle at top right, color-mix(in oklab, var(--color-primary) 8%, var(--color-bg)) 0%, var(--color-bg) 42%), var(--color-bg);
      overflow: hidden;
    }
    button, input { font: inherit; }
    .app { min-height: 100dvh; display: grid; grid-template-rows: auto 1fr auto; }
    .topbar {
      display: flex; justify-content: space-between; align-items: center; gap: var(--space-4);
      padding: var(--space-4) var(--space-5);
      border-bottom: 1px solid color-mix(in oklab, var(--color-text) 10%, transparent);
      background: color-mix(in oklab, var(--color-surface) 88%, transparent);
      backdrop-filter: blur(10px);
    }
    .brand { display: flex; align-items: center; gap: var(--space-3); }
    .logo { width: 2.25rem; height: 2.25rem; border-radius: var(--radius-lg); background: linear-gradient(135deg, var(--color-primary), color-mix(in oklab, var(--color-primary) 40%, white)); display: grid; place-items: center; color: white; font-weight: 700; box-shadow: var(--shadow-sm); }
    .brand h1 { margin: 0; font-size: var(--text-lg); font-family: var(--font-display); font-weight: 400; }
    .brand p { margin: 0; color: var(--color-text-muted); font-size: var(--text-sm); }
    .controls { display: flex; align-items: center; gap: var(--space-2); }
    .btn, .ghost-btn {
      border: 1px solid color-mix(in oklab, var(--color-text) 12%, transparent);
      border-radius: var(--radius-full);
      padding: 0.75rem 1rem;
      min-height: 44px;
      background: var(--color-surface-2);
      color: var(--color-text);
      cursor: pointer;
      transition: 180ms ease;
    }
    .btn.primary { background: var(--color-primary); color: var(--color-text-inverse); border-color: transparent; }
    .btn.primary:hover { background: var(--color-primary-hover); }
    .ghost-btn:hover, .btn:hover { transform: translateY(-1px); box-shadow: var(--shadow-sm); }
    .deck { position: relative; width: 100%; height: 100%; }
    .slide {
      position: absolute; inset: 0; opacity: 0; pointer-events: none; transform: translateX(24px) scale(0.98);
      transition: opacity 320ms ease, transform 320ms ease;
      padding: clamp(1rem, 3vw, 2rem);
      display: grid; place-items: center;
    }
    .slide.active { opacity: 1; pointer-events: auto; transform: translateX(0) scale(1); }
    .panel {
      width: min(960px, 100%);
      background: color-mix(in oklab, var(--color-surface) 96%, transparent);
      border: 1px solid color-mix(in oklab, var(--color-text) 10%, transparent);
      border-radius: var(--radius-xl);
      box-shadow: var(--shadow-md);
      overflow: hidden;
    }
    .panel-inner { padding: clamp(1.25rem, 3vw, 2rem); }
    .eyebrow { text-transform: uppercase; letter-spacing: 0.12em; font-size: var(--text-xs); color: var(--color-text-muted); margin-bottom: var(--space-3); }
    h2 { margin: 0 0 var(--space-3); font-size: var(--text-2xl); line-height: 1.05; font-family: var(--font-display); font-weight: 400; }
    p { margin: 0 0 var(--space-4); color: var(--color-text-muted); }
    .grid-2 { display: grid; grid-template-columns: 1.1fr 0.9fr; gap: var(--space-8); }
    .info-card, .practice-card {
      background: var(--color-surface-2); border: 1px solid color-mix(in oklab, var(--color-text) 8%, transparent);
      border-radius: var(--radius-lg); padding: var(--space-5);
    }
    .verb-grid { display: grid; grid-template-columns: repeat(2, minmax(0,1fr)); gap: var(--space-3); }
    .verb-item { display: flex; justify-content: space-between; gap: var(--space-3); padding: 0.9rem 1rem; border-radius: var(--radius-md); background: var(--color-surface-offset); }
    .verb-item strong { color: var(--color-primary); }
    .tip-list { padding-left: 1.1rem; color: var(--color-text-muted); margin: 0; }
    .tip-list li { margin-bottom: var(--space-3); }
    .question-block { display: grid; gap: var(--space-4); }
    .sentence { font-size: var(--text-lg); color: var(--color-text); }
    .options { display: grid; grid-template-columns: repeat(auto-fit, minmax(110px, 1fr)); gap: var(--space-3); }
    .option-btn {
      min-height: 48px; padding: 0.85rem 1rem; border-radius: var(--radius-md); border: 1px solid color-mix(in oklab, var(--color-text) 12%, transparent);
      background: var(--color-surface-2); cursor: pointer;
    }
    .option-btn.selected { border-color: var(--color-primary); background: var(--color-primary-highlight); }
    .option-btn.correct { border-color: var(--color-success); background: var(--color-success-highlight); }
    .option-btn.wrong { border-color: var(--color-error); background: var(--color-error-highlight); }
    .feedback { min-height: 1.5em; font-size: var(--text-sm); }
    .feedback.good { color: var(--color-success); }
    .feedback.bad { color: var(--color-error); }
    .form-row { display: grid; grid-template-columns: 1fr auto; gap: var(--space-3); align-items: center; margin-bottom: var(--space-4); }
    .form-row label { color: var(--color-text); }
    .blank-input {
      width: min(180px, 100%); min-height: 44px; padding: 0.8rem 0.9rem; border-radius: var(--radius-md);
      border: 1px solid color-mix(in oklab, var(--color-text) 14%, transparent); background: var(--color-surface);
    }
    .blank-input:focus { outline: 2px solid var(--color-primary); outline-offset: 2px; }
    .tag-row { display: flex; flex-wrap: wrap; gap: var(--space-2); margin-top: var(--space-3); }
    .tag { padding: 0.45rem 0.8rem; border-radius: var(--radius-full); background: var(--color-primary-highlight); color: var(--color-primary); font-size: var(--text-sm); }
    .footer {
      display: flex; justify-content: space-between; align-items: center; gap: var(--space-4);
      padding: var(--space-4) var(--space-5); border-top: 1px solid color-mix(in oklab, var(--color-text) 10%, transparent);
      background: color-mix(in oklab, var(--color-surface) 88%, transparent);
    }
    .progress { color: var(--color-text-muted); font-size: var(--text-sm); }
    .nav { display: flex; gap: var(--space-2); }
    .dots { display: flex; gap: 0.45rem; align-items: center; }
    .dot { width: 10px; height: 10px; border-radius: 999px; background: color-mix(in oklab, var(--color-text) 16%, transparent); }
    .dot.active { background: var(--color-primary); transform: scale(1.2); }
    .summary-box { margin-top: var(--space-4); padding: var(--space-4); border-radius: var(--radius-lg); background: var(--color-surface-offset); color: var(--color-text); }
    @media (max-width: 800px) {
      .grid-2 { grid-template-columns: 1fr; gap: var(--space-4); }
      .form-row { grid-template-columns: 1fr; }
      .footer, .topbar { flex-wrap: wrap; }
      .controls, .nav { width: 100%; justify-content: space-between; }
    }
  </style>
</head>
<body>
  <div class="app">
    <header class="topbar">
      <div class="brand">
        <div class="logo" aria-hidden="true">È</div>
        <div>
          <h1>Essere al presente</h1>
          <p>Interactive practice for all 6 persons</p>
        </div>
      </div>
      <div class="controls">
        <button class="ghost-btn" id="themeToggle" aria-label="Switch theme">🌙 / ☀️</button>
        <button class="ghost-btn" id="resetAll">Reset</button>
      </div>
    </header>

    <main class="deck" aria-live="polite">
      <section class="slide active" data-slide="1">
        <div class="panel">
          <div class="panel-inner grid-2">
            <div>
              <div class="eyebrow">Slide 1 · Review</div>
              <h2>Il verbo <em>essere</em> al presente</h2>
              <p>First, review the six forms. Then move to the exercises and use <em>essere</em> in short, real sentences.</p>
              <div class="info-card">
                <div class="verb-grid">
                  <div class="verb-item"><span>Io</span><strong>sono</strong></div>
                  <div class="verb-item"><span>Tu</span><strong>sei</strong></div>
                  <div class="verb-item"><span>Lui / Lei</span><strong>è</strong></div>
                  <div class="verb-item"><span>Noi</span><strong>siamo</strong></div>
                  <div class="verb-item"><span>Voi</span><strong>siete</strong></div>
                  <div class="verb-item"><span>Loro</span><strong>sono</strong></div>
                </div>
                <div class="tag-row">
                  <span class="tag">Sono inglese.</span>
                  <span class="tag">Sei pronta?</span>
                  <span class="tag">Siamo amici.</span>
                  <span class="tag">Loro sono a casa.</span>
                </div>
              </div>
            </div>
            <div class="practice-card">
              <div class="eyebrow">How to use it</div>
              <ul class="tip-list">
                <li>Match the form to the subject: <strong>io → sono</strong>, <strong>tu → sei</strong>, and so on.</li>
                <li>Use it to talk about identity, nationality, feelings, and location.</li>
                <li>Remember: in Italian the subject can be omitted, for example <strong>Sono stanca</strong>.</li>
              </ul>
              <div class="summary-box">
                Mini goal: read the forms aloud twice before starting the exercises.
              </div>
            </div>
          </div>
        </div>
      </section>

      <section class="slide" data-slide="2">
        <div class="panel">
          <div class="panel-inner">
            <div class="eyebrow">Slide 2 · Multiple choice</div>
            <h2>Scegli la forma corretta</h2>
            <p>Read each sentence and choose the correct present form of <em>essere</em>.</p>
            <div id="mcqContainer" class="question-block"></div>
          </div>
        </div>
      </section>

      <section class="slide" data-slide="3">
        <div class="panel">
          <div class="panel-inner">
            <div class="eyebrow">Slide 3 · Fill in the blank</div>
            <h2>Completa le frasi</h2>
            <p>Type the correct form of <em>essere</em>. Use accents when needed: <strong>è</strong>.</p>
            <form id="fillForm"></form>
            <div class="feedback" id="fillFeedback"></div>
            <div style="display:flex; gap:0.75rem; flex-wrap:wrap; margin-top:1rem;">
              <button class="btn primary" type="button" id="checkFill">Check answers</button>
              <button class="ghost-btn" type="button" id="showFill">Show answers</button>
            </div>
          </div>
        </div>
      </section>

      <section class="slide" data-slide="4">
        <div class="panel">
          <div class="panel-inner">
            <div class="eyebrow">Slide 4 · Final review</div>
            <h2>Ripasso finale</h2>
            <p>Use this slide to review mistakes and repeat the full pattern one last time.</p>
            <div class="grid-2">
              <div class="info-card">
                <div class="eyebrow">Pattern</div>
                <div class="verb-grid">
                  <div class="verb-item"><span>Io</span><strong>sono</strong></div>
                  <div class="verb-item"><span>Tu</span><strong>sei</strong></div>
                  <div class="verb-item"><span>Lui / Lei</span><strong>è</strong></div>
                  <div class="verb-item"><span>Noi</span><strong>siamo</strong></div>
                  <div class="verb-item"><span>Voi</span><strong>siete</strong></div>
                  <div class="verb-item"><span>Loro</span><strong>sono</strong></div>
                </div>
              </div>
              <div class="practice-card">
                <div class="eyebrow">Teacher prompt ideas</div>
                <ul class="tip-list">
                  <li>Ask for quick oral transformations: io → noi, tu → voi.</li>
                  <li>Ask personal questions: <strong>Sei stanca?</strong>, <strong>Siete in Italia?</strong></li>
                  <li>Invite short production: “Io sono…, noi siamo…”</li>
                </ul>
                <div class="summary-box" id="scoreBox">Progress updates will appear here after the exercises.</div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>

    <footer class="footer">
      <div class="progress"><span id="counter">1 / 4</span></div>
      <div class="dots" id="dots"></div>
      <div class="nav">
        <button class="ghost-btn" id="prevBtn">← Prev</button>
        <button class="btn primary" id="nextBtn">Next →</button>
      </div>
    </footer>
  </div>

  <script>
    const slides = Array.from(document.querySelectorAll('.slide'));
    const dots = document.getElementById('dots');
    const counter = document.getElementById('counter');
    const prevBtn = document.getElementById('prevBtn');
    const nextBtn = document.getElementById('nextBtn');
    let currentSlide = 0;
    let mcqScore = 0;
    let fillScore = 0;

    slides.forEach((_, i) => {
      const dot = document.createElement('button');
      dot.className = 'dot' + (i === 0 ? ' active' : '');
      dot.setAttribute('aria-label', 'Go to slide ' + (i + 1));
      dot.addEventListener('click', () => goToSlide(i));
      dots.appendChild(dot);
    });

    function renderNav() {
      slides.forEach((slide, i) => slide.classList.toggle('active', i === currentSlide));
      Array.from(dots.children).forEach((dot, i) => dot.classList.toggle('active', i === currentSlide));
      counter.textContent = (currentSlide + 1) + ' / ' + slides.length;
      prevBtn.disabled = currentSlide === 0;
      nextBtn.disabled = currentSlide === slides.length - 1;
      prevBtn.style.opacity = currentSlide === 0 ? 0.5 : 1;
      nextBtn.style.opacity = currentSlide === slides.length - 1 ? 0.5 : 1;
    }
    function goToSlide(index) { currentSlide = Math.max(0, Math.min(slides.length - 1, index)); renderNav(); }
    prevBtn.addEventListener('click', () => goToSlide(currentSlide - 1));
    nextBtn.addEventListener('click', () => goToSlide(currentSlide + 1));
    document.addEventListener('keydown', e => {
      if (e.key === 'ArrowRight') goToSlide(currentSlide + 1);
      if (e.key === 'ArrowLeft') goToSlide(currentSlide - 1);
    });

    const mcqData = [
      { sentence: 'Io ___ inglese.', options: ['sono', 'sei', 'è'], answer: 'sono' },
      { sentence: 'Tu ___ molto gentile.', options: ['sono', 'sei', 'siete'], answer: 'sei' },
      { sentence: 'Lei ___ a scuola.', options: ['è', 'sono', 'siamo'], answer: 'è' },
      { sentence: 'Noi ___ in classe.', options: ['siamo', 'siete', 'sono'], answer: 'siamo' },
      { sentence: 'Voi ___ pronti?', options: ['è', 'siete', 'sei'], answer: 'siete' },
      { sentence: 'Loro ___ italiani.', options: ['siamo', 'sono', 'è'], answer: 'sono' }
    ];

    const mcqContainer = document.getElementById('mcqContainer');
    mcqData.forEach((item, index) => {
      const wrap = document.createElement('div');
      wrap.className = 'practice-card';
      wrap.innerHTML = `
        <div class="sentence">${index + 1}. ${item.sentence}</div>
        <div class="options" role="group" aria-label="Question ${index + 1}"></div>
        <div class="feedback" id="mcq-feedback-${index}"></div>
      `;
      const optionsWrap = wrap.querySelector('.options');
      item.options.forEach(option => {
        const btn = document.createElement('button');
        btn.type = 'button';
        btn.className = 'option-btn';
        btn.textContent = option;
        btn.addEventListener('click', () => {
          if (wrap.dataset.answered === 'true') return;
          wrap.dataset.answered = 'true';
          const feedback = wrap.querySelector('.feedback');
          Array.from(optionsWrap.children).forEach(child => {
            if (child.textContent === item.answer) child.classList.add('correct');
          });
          if (option === item.answer) {
            btn.classList.add('selected', 'correct');
            feedback.textContent = 'Correct!';
            feedback.className = 'feedback good';
            mcqScore += 1;
          } else {
            btn.classList.add('selected', 'wrong');
            feedback.textContent = 'Not quite. The correct answer is “' + item.answer + '”.';
            feedback.className = 'feedback bad';
          }
          updateScoreBox();
        });
        optionsWrap.appendChild(btn);
      });
      mcqContainer.appendChild(wrap);
    });

    const fillData = [
      { prompt: 'Io ___ felice.', answer: 'sono' },
      { prompt: 'Tu ___ in Italia.', answer: 'sei' },
      { prompt: 'Lui ___ stanco.', answer: 'è' },
      { prompt: 'Noi ___ amici.', answer: 'siamo' },
      { prompt: 'Voi ___ al ristorante.', answer: 'siete' },
      { prompt: 'Loro ___ a casa.', answer: 'sono' }
    ];

    const fillForm = document.getElementById('fillForm');
    fillData.forEach((item, index) => {
      const row = document.createElement('div');
      row.className = 'form-row practice-card';
      row.innerHTML = `
        <label for="blank-${index}" class="sentence">${index + 1}. ${item.prompt}</label>
        <input id="blank-${index}" class="blank-input" autocomplete="off" />
      `;
      fillForm.appendChild(row);
    });

    function normalize(text) {
      return text.trim().toLowerCase().normalize('NFC');
    }

    document.getElementById('checkFill').addEventListener('click', () => {
      let correct = 0;
      fillData.forEach((item, index) => {
        const input = document.getElementById('blank-' + index);
        const value = normalize(input.value);
        input.style.borderColor = '';
        if (value === normalize(item.answer)) {
          input.style.borderColor = 'var(--color-success)';
          correct += 1;
        } else {
          input.style.borderColor = 'var(--color-error)';
        }
      });
      fillScore = correct;
      const fb = document.getElementById('fillFeedback');
      fb.textContent = 'You got ' + correct + ' out of ' + fillData.length + ' correct.';
      fb.className = 'feedback ' + (correct === fillData.length ? 'good' : 'bad');
      updateScoreBox();
    });

    document.getElementById('showFill').addEventListener('click', () => {
      fillData.forEach((item, index) => {
        const input = document.getElementById('blank-' + index);
        input.value = item.answer;
        input.style.borderColor = 'var(--color-primary)';
      });
      document.getElementById('fillFeedback').textContent = 'Answers shown.';
      document.getElementById('fillFeedback').className = 'feedback good';
    });

    function updateScoreBox() {
      document.getElementById('scoreBox').textContent = 'Current progress: multiple choice ' + mcqScore + '/6, fill in the blank ' + fillScore + '/6.';
    }

    document.getElementById('themeToggle').addEventListener('click', () => {
      const root = document.documentElement;
      root.setAttribute('data-theme', root.getAttribute('data-theme') === 'dark' ? 'light' : 'dark');
    });

    document.getElementById('resetAll').addEventListener('click', () => location.reload());
    renderNav();
    updateScoreBox();
  </script>
</body>
</html>
