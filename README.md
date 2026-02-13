<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>🌌 Helico Trigo Pro</title>
  <!-- Google Fonts & Font Awesome -->
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700;800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Montserrat', sans-serif;
    }

    body {
      background: linear-gradient(145deg, #0b1a2e, #1c3a4f);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
    }

    .game-container {
      max-width: 800px;
      width: 100%;
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(10px);
      border-radius: 48px;
      padding: 30px 25px;
      box-shadow: 0 20px 40px rgba(0,0,0,0.6);
      border: 2px solid #ffd966;
      position: relative;
    }

    /* Helico animado */
    .helico-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: #112b3f;
      border-radius: 60px;
      padding: 10px 25px;
      margin-bottom: 30px;
      color: white;
      border: 2px solid #f9d371;
    }

    .helico-icon {
      font-size: 42px;
      color: #fddb3a;
      animation: spinRotor 1s infinite linear;
      text-shadow: 0 0 10px #ffb347;
    }

    @keyframes spinRotor {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    .game-title {
      font-size: 24px;
      font-weight: 800;
      background: #efefef;
      color: #1e3c4f;
      padding: 8px 20px;
      border-radius: 50px;
      letter-spacing: 2px;
      border: 2px solid #ffb703;
    }

    /* Stats bar */
    .stats-panel {
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      background: #0f212e;
      padding: 15px 10px;
      border-radius: 50px;
      margin-bottom: 25px;
      color: white;
      border: 2px solid #f4c542;
      box-shadow: inset 0 0 8px black;
    }

    .stat-item {
      display: flex;
      align-items: center;
      gap: 10px;
      background: #1f4e5f;
      padding: 8px 20px;
      border-radius: 50px;
      font-weight: 700;
      font-size: 18px;
    }

    .fa-heart { color: #ff5e5e; }
    .fa-star { color: #ffe083; }
    .fa-coins { color: #ffd966; }
    .fa-bolt { color: #a9d6e5; }

    .xp-bar-container {
      background: #3a4e5e;
      height: 16px;
      width: 140px;
      border-radius: 20px;
      margin-left: 8px;
      border: 1px solid white;
    }

    .xp-fill {
      height: 100%;
      width: 0%;
      background: linear-gradient(90deg, #6ed4b0, #2ec1ac);
      border-radius: 20px;
      transition: width 0.3s;
    }

    /* Área de misión */
    .mission-area {
      background: #152d3c;
      border: 4px solid #fbb13c;
      border-radius: 40px;
      padding: 30px 20px;
      margin-bottom: 30px;
      box-shadow: 0 8px 0 #9e6d2b;
    }

    .question-box {
      background: #fff9e6;
      padding: 25px;
      border-radius: 30px;
      font-size: 26px;
      font-weight: 700;
      text-align: center;
      color: #0a3142;
      border: 3px dashed #fe9801;
      word-break: break-word;
    }

    .diagram-hint {
      margin-top: 12px;
      font-size: 18px;
      color: #ffe7b6;
      text-align: center;
      font-style: italic;
    }

    /* Botones de respuesta */
    .options-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 20px;
      margin-top: 30px;
    }

    .answer-btn {
      background: #2f5f6e;
      border: none;
      border-bottom: 8px solid #0d2c36;
      color: white;
      padding: 18px 5px;
      font-size: 24px;
      font-weight: bold;
      border-radius: 40px;
      cursor: pointer;
      transition: 0.1s all;
      box-shadow: 0 6px 0 #0a1c22;
      letter-spacing: 1px;
    }

    .answer-btn:hover {
      background: #4096a8;
      transform: scale(0.97);
    }

    .answer-btn:disabled {
      opacity: 0.5;
      cursor: not-allowed;
      border-bottom-width: 4px;
    }

    .feedback {
      margin-top: 25px;
      font-size: 22px;
      font-weight: bold;
      text-align: center;
      min-height: 50px;
      color: #ffd966;
      text-shadow: 2px 2px 0 #1f4e5f;
    }

    .next-btn {
      background: #ff9f1c;
      border: none;
      border-bottom: 8px solid #bb6700;
      color: white;
      font-size: 28px;
      font-weight: 800;
      padding: 15px 30px;
      border-radius: 60px;
      width: 80%;
      margin: 15px auto 0;
      display: block;
      cursor: pointer;
      transition: 0.1s;
      text-transform: uppercase;
    }

    .next-btn:disabled {
      opacity: 0.3;
      border-bottom-width: 4px;
      cursor: not-allowed;
    }

    /* Tienda / Recompensas */
    .shop-panel {
      background: #1a3a47;
      border-radius: 40px;
      padding: 25px 20px;
      margin-top: 25px;
      border: 3px solid #ffb347;
    }

    .shop-title {
      font-size: 26px;
      color: #ffe5a3;
      margin-bottom: 20px;
      display: flex;
      align-items: center;
      gap: 15px;
    }

    .shop-items {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-around;
      gap: 15px;
    }

    .shop-btn {
      background: linear-gradient(145deg, #fdaa4b, #ff7b25);
      border: none;
      border-bottom: 6px solid #b33f00;
      color: white;
      padding: 15px 20px;
      font-size: 18px;
      font-weight: bold;
      border-radius: 50px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 6px;
      cursor: pointer;
      flex: 1 0 160px;
      transition: 0.1s;
      box-shadow: 0 6px 0 #6b2b00;
    }

    .shop-btn:hover {
      transform: translateY(-3px);
      background: #ff9533;
    }

    .shop-btn:disabled {
      opacity: 0.5;
      transform: none;
      cursor: not-allowed;
      border-bottom-width: 4px;
    }

    .restart-btn {
      background: #a31621;
      border-bottom: 6px solid #56070c;
      color: white;
      border-radius: 50px;
      padding: 12px 28px;
      font-size: 20px;
      font-weight: bold;
      border: none;
      margin-top: 20px;
      cursor: pointer;
      border-bottom: 6px solid #4d0b0b;
    }

    .footer {
      display: flex;
      justify-content: center;
      margin-top: 15px;
    }

    @media (max-width: 550px) {
      .options-grid { grid-template-columns: 1fr; }
      .stat-item { font-size: 14px; padding: 5px 12px; }
    }
  </style>
</head>
<body>
  <div class="game-container">
    <!-- Helico animado + título -->
    <div class="helico-header">
      <i class="fas 🌌 helico-icon"></i>
      <span class="game-title">🌌 HELICO TRIGO PRO 🌌</span>
      <i class="fas 🌌 helico-icon" style="font-size: 36px; transform: scaleX(-1);"></i>
    </div>

    <!-- Panel de estadísticas: Vida, XP, Nivel, Monedas -->
    <div class="stats-panel">
      <div class="stat-item"><i class="fas fa-heart"></i> <span id="livesDisplay">3</span> ❤️</div>
      <div class="stat-item">
        <i class="fas fa-bolt"></i> XP
        <div class="xp-bar-container">
          <div id="xpFill" class="xp-fill" style="width: 0%;"></div>
        </div>
        <span id="xpText">0/100</span>
      </div>
      <div class="stat-item"><i class="fas fa-star"></i> Nvl <span id="levelDisplay">1</span></div>
      <div class="stat-item"><i class="fas fa-coins"></i> <span id="coinsDisplay">0</span></div>
    </div>

    <!-- Zona de misión trigonométrica -->
    <div class="mission-area">
      <div class="question-box" id="questionText">
        ¡Prepara tu helicóptero! Cargando...
      </div>
      <div class="diagram-hint" id="diagramHint">
        <i class="fas fa-drafting-compass"></i> Ángulos, senos y cosenos
      </div>

      <!-- Botones de respuestas (4) -->
      <div class="options-grid" id="optionsContainer">
        <button class="answer-btn" id="opt0">-</button>
        <button class="answer-btn" id="opt1">-</button>
        <button class="answer-btn" id="opt2">-</button>
        <button class="answer-btn" id="opt3">-</button>
      </div>

      <!-- Feedback y botón siguiente -->
      <div class="feedback" id="feedbackMsg">💪 Elige una respuesta, piloto.</div>
      <button class="next-btn" id="nextBtn" disabled>🚁 SIGUIENTE MISIÓN</button>
    </div>

    <!-- TIENDA / RECOMPENSAS (gasta tus monedas) -->
    <div class="shop-panel">
      <div class="shop-title">
        <i class="fas fa-store-alt"></i> HÉLICO-TIENDA 
        <i class="fas fa-coins" style="color: #ffd966;"></i>
      </div>
      <div class="shop-items">
        <button class="shop-btn" id="buyLifeBtn">
          <i class="fas fa-heart" style="font-size: 28px;"></i>
          VIDA EXTRA <span style="font-size: 20px;">50🪙</span>
        </button>
        <button class="shop-btn" id="buyXpBtn">
          <i class="fas fa-bolt" style="font-size: 28px;"></i>
          XP BOOST +20 <span style="font-size: 20px;">30🪙</span>
        </button>
        <button class="shop-btn" id="mysteryBtn">
          <i class="fas fa-gift" style="font-size: 28px;"></i>
          CAJA MISTERIO <span style="font-size: 20px;">40🪙</span>
        </button>
      </div>
    </div>

    <!-- Botón de reinicio -->
    <div class="footer">
      <button class="restart-btn" id="restartBtn"><i class="fas fa-undo-alt"></i> RESET_HELICOCHALLENGE</button>
    </div>
  </div>

  <script>
    // ---------- HELICO TRIGO PRO ----------
    // Mecánicas: XP, vidas, monedas, tienda, trigonometría interactiva.
    // Para adolescentes, estilo dinámico y recompensas.

    // ----- ESTADO DEL JUGADOR -----
    let player = {
      lives: 3,
      xp: 0,
      coins: 0,
      level: 1
    };

    // Máximo de vidas
    const MAX_LIVES = 5;

    // Control de juego
    let gameOver = false;
    let canAnswer = true;
    let currentQuestion = null;
    let correctAnswerStr = "";

    // Elementos del DOM
    const livesEl = document.getElementById('livesDisplay');
    const xpFillEl = document.getElementById('xpFill');
    const xpTextEl = document.getElementById('xpText');
    const levelEl = document.getElementById('levelDisplay');
    const coinsEl = document.getElementById('coinsDisplay');
    const questionEl = document.getElementById('questionText');
    const diagramHint = document.getElementById('diagramHint');
    const optBtns = [
      document.getElementById('opt0'),
      document.getElementById('opt1'),
      document.getElementById('opt2'),
      document.getElementById('opt3')
    ];
    const feedbackEl = document.getElementById('feedbackMsg');
    const nextBtn = document.getElementById('nextBtn');

    // Botones de tienda
    const buyLifeBtn = document.getElementById('buyLifeBtn');
    const buyXpBtn = document.getElementById('buyXpBtn');
    const mysteryBtn = document.getElementById('mysteryBtn');
    const restartBtn = document.getElementById('restartBtn');

    // ----- FUNCIONES DE ACTUALIZACIÓN DE UI -----
    function updateStatsUI() {
      // Vidas
      livesEl.textContent = player.lives;

      // XP Bar y texto
      let xpInLevel = player.xp % 100;
      let percent = (xpInLevel / 100) * 100;
      xpFillEl.style.width = percent + '%';
      xpTextEl.textContent = `${xpInLevel}/100`;

      // Nivel
      player.level = Math.floor(player.xp / 100) + 1;
      levelEl.textContent = player.level;

      // Monedas
      coinsEl.textContent = player.coins;

      // Habilitar/deshabilitar shop según gameOver y monedas
      if (gameOver) {
        buyLifeBtn.disabled = true;
        buyXpBtn.disabled = true;
        mysteryBtn.disabled = true;
      } else {
        buyLifeBtn.disabled = (player.coins < 50 || player.lives >= MAX_LIVES);
        buyXpBtn.disabled = (player.coins < 30);
        mysteryBtn.disabled = (player.coins < 40);
      }
    }

    // ----- SISTEMA DE NIVEL: BONUS AL SUBIR -----
    function checkLevelUp(previousXP) {
      let previousLevel = Math.floor(previousXP / 100) + 1;
      let currentLevel = Math.floor(player.xp / 100) + 1;
      if (currentLevel > previousLevel) {
        // Bonus por nivel: +20 monedas y +1 vida (si no está al máximo)
        player.coins += 20;
        if (player.lives < MAX_LIVES) player.lives++;
        feedbackEl.innerHTML += ` 🎉 ¡SUBISTE A NIVEL ${currentLevel}! +20🪙 +1❤️`;
      }
    }

    // ----- GENERADOR DE PREGUNTAS DE TRIGONOMETRÍA -----
    function generateTrigQuestion() {
      const types = [
        'sin_simple', 'cos_simple', 'tan_simple', 
        'inverse_sin', 'inverse_cos', 'triangle_sin'
      ];
      const choice = types[Math.floor(Math.random() * types.length)];

      // Ángulos comunes
      const angles = [0, 30, 45, 60, 90];
      const angle = angles[Math.floor(Math.random() * angles.length)];

      // Valores exactos en string
      const sinVals = {
        0: "0", 30: "1/2", 45: "√2/2", 60: "√3/2", 90: "1"
      };
      const cosVals = {
        0: "1", 30: "√3/2", 45: "√2/2", 60: "1/2", 90: "0"
      };
      const tanVals = {
        0: "0", 30: "1/√3", 45: "1", 60: "√3", 90: "indefinido"
      };

      let questionText = "";
      let correct = "";
      let options = [];
      let hint = "";

      if (choice === 'sin_simple') {
        questionText = `sin(${angle}°) = ?`;
        correct = sinVals[angle];
        // distractores: otros valores comunes
        let dist = shuffle([sinVals[30], sinVals[45], sinVals[60], sinVals[90], cosVals[angle], tanVals[angle]]);
        options = [correct, ...dist.slice(0,3)];
        hint = `✈️ Ángulo ${angle}°, seno en el círculo unitario.`;
      }
      else if (choice === 'cos_simple') {
        questionText = `cos(${angle}°) = ?`;
        correct = cosVals[angle];
        let dist = shuffle([cosVals[30], cosVals[45], cosVals[60], cosVals[0], sinVals[angle], "2"]);
        options = [correct, ...dist.slice(0,3)];
        hint = `🔄 cos(${angle}°) = seno del complemento.`;
      }
      else if (choice === 'tan_simple' && angle !== 90) {
        questionText = `tan(${angle}°) = ?`;
        correct = tanVals[angle];
        let dist = shuffle([tanVals[30], tanVals[45], tanVals[60], "1/2", "√2", "0.5"]);
        options = [correct, ...dist.slice(0,3)];
        hint = `📐 tan = seno/coseno.`;
      }
      else if (choice === 'inverse_sin') {
        let val = sinVals[angle];
        questionText = `Si sin(θ) = ${val}, ¿cuánto es θ? (0° a 90°)`;
        correct = angle + "°";
        let wrongs = [30,45,60,0,90].filter(a => a !== angle).map(a => a + "°");
        let dist = shuffle(wrongs);
        options = [correct, ...dist.slice(0,3)];
        hint = `🎯 Seno inverso. Recuerda valores especiales.`;
      }
      else if (choice === 'inverse_cos') {
        let val = cosVals[angle];
        questionText = `Si cos(θ) = ${val}, ¿cuál es θ? (0° a 90°)`;
        correct = angle + "°";
        let wrongs = [30,45,60,0,90].filter(a => a !== angle).map(a => a + "°");
        let dist = shuffle(wrongs);
        options = [correct, ...dist.slice(0,3)];
        hint = `🎯 Coseno inverso.`;
      }
      else { // triangle_sin (triángulo rectángulo simple)
        const triple = [[3,4,5], [5,12,13], [8,15,17], [7,24,25]];
        const [a, b, c] = triple[Math.floor(Math.random() * triple.length)];
        // preguntar sin del ángulo opuesto a cateto a
        let opposite = a;
        let hypotenuse = c;
        let fraction = `${opposite}/${hypotenuse}`;
        questionText = `En un triángulo rectángulo, cateto opuesto = ${opposite}, hipotenusa = ${hypotenuse}. sin(θ) = ?`;
        correct = fraction;
        let wrong1 = `${hypotenuse}/${opposite}`;
        let wrong2 = `${b}/${c}`;
        let wrong3 = `${opposite}/${b}`;
        options = [correct, wrong1, wrong2, wrong3];
        hint = `✈️ sin(θ) = opuesto / hipotenusa.`;
      }

      // Mezclar opciones y asegurar que sean 4
      options = shuffle(options);
      while (options.length < 4) options.push("---");
      
      return {
        question: questionText,
        correct: correct,
        options: options,
        hint: hint
      };
    }

    // Función para mezclar array
    function shuffle(arr) {
      let copy = [...arr];
      for (let i = copy.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [copy[i], copy[j]] = [copy[j], copy[i]];
      }
      return copy;
    }

    // ----- CARGAR NUEVA PREGUNTA -----
    function loadNewQuestion() {
      if (gameOver) return;
      
      currentQuestion = generateTrigQuestion();
      questionEl.textContent = currentQuestion.question;
      correctAnswerStr = currentQuestion.correct;
      diagramHint.innerHTML = `<i class="fas fa-drafting-compass"></i> ${currentQuestion.hint}`;
      
      // Asignar opciones a los botones
      for (let i = 0; i < 4; i++) {
        optBtns[i].textContent = currentQuestion.options[i] || "?";
        optBtns[i].disabled = false;
        optBtns[i].style.background = "#2f5f6e"; // reset
      }
      
      // Reset feedback y habilitar respuestas
      feedbackEl.innerHTML = "🤔 Elige una opción, piloto.";
      canAnswer = true;
      nextBtn.disabled = true;
    }

    // ----- VERIFICAR RESPUESTA -----
    function handleAnswer(selectedIdx) {
      if (!canAnswer || gameOver) return;
      if (!currentQuestion) return;

      let selectedText = optBtns[selectedIdx].textContent;
      let isCorrect = (selectedText === correctAnswerStr);
      
      // Deshabilitar botones después de responder
      canAnswer = false;
      optBtns.forEach(btn => btn.disabled = true);
      
      // Feedback y consecuencias
      if (isCorrect) {
        // PREMIO: +10 XP, +5 monedas
        let oldXP = player.xp;
        player.xp += 10;
        player.coins += 5;
        
        feedbackEl.innerHTML = "✅ ¡IMPECABLE! +10 XP · +5🪙";
        
        // Chequear subida de nivel
        checkLevelUp(oldXP);
        
        // Efecto visual botón correcto
        optBtns[selectedIdx].style.background = "#2a7a4b";
      } else {
        // PENALIZACIÓN: -1 vida
        player.lives--;
        feedbackEl.innerHTML = `❌ ¡Fallaste! La respuesta era ${correctAnswerStr}. -1❤️`;
        optBtns[selectedIdx].style.background = "#9a2a2a";
        
        // Marcar la correcta para aprender
        for (let i=0; i<optBtns.length; i++) {
          if (optBtns[i].textContent === correctAnswerStr) {
            optBtns[i].style.background = "#2a7a4b";
          }
        }
        
        // Game Over si vidas = 0
        if (player.lives <= 0) {
          player.lives = 0;
          gameOver = true;
          feedbackEl.innerHTML = "💥 HELICO DERRRIBADO. Presiona REINICIAR. 💥";
          nextBtn.disabled = true;
          updateStatsUI();
          return;
        }
      }
      
      // Actualizar UI stats
      updateStatsUI();
      
      // Habilitar botón "Siguiente misión"
      nextBtn.disabled = false;
    }

    // ----- REINICIAR JUEGO -----
    function resetGame() {
      player = {
        lives: 3,
        xp: 0,
        coins: 0,
        level: 1
      };
      gameOver = false;
      canAnswer = true;
      updateStatsUI();
      loadNewQuestion();
      feedbackEl.innerHTML = "🔄 NUEVA MISIÓN. ¡Gana XP y monedas!";
    }

    // ----- TIENDA: RECOMPENSAS -----
    function buyExtraLife() {
      if (player.coins >= 50 && player.lives < MAX_LIVES && !gameOver) {
        player.coins -= 50;
        player.lives++;
        updateStatsUI();
        feedbackEl.innerHTML = "❤️ ¡Vida extra comprada! +1 vida.";
      }
    }

    function buyXpBoost() {
      if (player.coins >= 30 && !gameOver) {
        player.coins -= 30;
        let oldXP = player.xp;
        player.xp += 20;
        updateStatsUI();
        checkLevelUp(oldXP);
        updateStatsUI();
        feedbackEl.innerHTML = "⚡ ¡XP Boost! +20 XP.";
      }
    }

    function buyMystery() {
      if (player.coins >= 40 && !gameOver) {
        player.coins -= 40;
        let reward = Math.floor(Math.random() * 3); // 0,1,2
        if (reward === 0) {
          if (player.lives < MAX_LIVES) {
            player.lives++;
            feedbackEl.innerHTML = "🎁 CAJA MISTERIO: +1 VIDA ❤️";
          } else {
            player.coins += 15; // compensa
            feedbackEl.innerHTML = "🎁 Vidas al máximo, te devolvemos 15🪙";
          }
        } else if (reward === 1) {
          let oldXP = player.xp;
          player.xp += 25;
          feedbackEl.innerHTML = "🎁 CAJA MISTERIO: +25 XP ⚡";
          checkLevelUp(oldXP);
        } else {
          player.coins += 35;
          feedbackEl.innerHTML = "🎁 CAJA MISTERIO: +35 MONEDAS 🪙";
        }
        updateStatsUI();
      }
    }

    // ----- ASIGNAR EVENTOS -----
    function initEventListeners() {
      // Botones de respuesta
      for (let i = 0; i < optBtns.length; i++) {
        optBtns[i].addEventListener('click', () => handleAnswer(i));
      }

      // Botón siguiente
      nextBtn.addEventListener('click', () => {
        if (!gameOver) {
          loadNewQuestion();
        }
      });

      // Tienda
      buyLifeBtn.addEventListener('click', buyExtraLife);
      buyXpBtn.addEventListener('click', buyXpBoost);
      mysteryBtn.addEventListener('click', buyMystery);

      // Reinicio
      restartBtn.addEventListener('click', resetGame);
    }

    // ----- INICIALIZAR JUEGO -----
    function initGame() {
      updateStatsUI();
      loadNewQuestion();
      initEventListeners();
    }

    initGame();
  </script>
</body>
</html>
