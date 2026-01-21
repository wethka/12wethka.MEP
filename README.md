<html lang="th" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>คณิตศาสตร์การเงิน ป.5</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600;700&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
      font-family: 'Kanit', sans-serif;
    }
    .coin {
      animation: bounce 2s ease-in-out infinite;
    }
    .coin:nth-child(2) { animation-delay: 0.2s; }
    .coin:nth-child(3) { animation-delay: 0.4s; }
    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }
    @keyframes celebrate {
      0% { transform: scale(1); }
      50% { transform: scale(1.1); }
      100% { transform: scale(1); }
    }
    .celebrate {
      animation: celebrate 0.5s ease-in-out;
    }
    @keyframes shake {
      0%, 100% { transform: translateX(0); }
      25% { transform: translateX(-5px); }
      75% { transform: translateX(5px); }
    }
    .shake {
      animation: shake 0.3s ease-in-out;
    }
    .money-bg {
      background: linear-gradient(135deg, #ffe5e5 0%, #ffd4d4 50%, #ffc9c9 100%);
      position: relative;
    }
    .bow {
      position: absolute;
      font-size: 2rem;
      opacity: 0.3;
      animation: float 6s ease-in-out infinite;
    }
    .bow:nth-child(2) { top: 10%; left: 15%; animation-delay: 0s; }
    .bow:nth-child(3) { top: 25%; right: 20%; animation-delay: 1s; font-size: 2.5rem; }
    .bow:nth-child(4) { top: 45%; left: 10%; animation-delay: 2s; font-size: 1.8rem; }
    .bow:nth-child(5) { top: 60%; right: 15%; animation-delay: 3s; }
    .bow:nth-child(6) { top: 75%; left: 25%; animation-delay: 4s; font-size: 2.2rem; }
    .bow:nth-child(7) { top: 85%; right: 30%; animation-delay: 5s; font-size: 1.9rem; }
    @keyframes float {
      0%, 100% { transform: translateY(0) rotate(0deg); }
      50% { transform: translateY(-20px) rotate(10deg); }
    }
    .card-shadow {
      box-shadow: 0 10px 40px rgba(0,0,0,0.15);
    }
    .btn-primary {
      background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);
      transition: all 0.3s ease;
    }
    .btn-primary:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 20px rgba(245, 158, 11, 0.4);
    }
    .progress-bar {
      background: linear-gradient(90deg, #10b981, #34d399);
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full">
  <div id="app-wrapper" class="h-full w-full money-bg overflow-auto"><span class="bow">🎀</span> <span class="bow">🎀</span> <span class="bow">🎀</span> <span class="bow">🎀</span> <span class="bow">🎀</span> <span class="bow">🎀</span>
   <div class="min-h-full p-4 md:p-6" style="position: relative; z-index: 1;"><!-- Header -->
    <header class="text-center mb-6">
     <div class="flex justify-center gap-2 mb-3"><span class="coin text-4xl">🪙</span> <span class="coin text-4xl">💰</span> <span class="coin text-4xl">🪙</span>
     </div>
     <h1 id="app-title" class="text-2xl md:text-4xl font-bold text-white drop-shadow-lg">คณิตศาสตร์การเงิน ป.5</h1>
     <p id="welcome-message" class="text-emerald-100 mt-2 text-lg">เรียนรู้เรื่องเงินอย่างสนุกสนาน!</p>
    </header><!-- Score Display -->
    <div class="max-w-2xl mx-auto mb-4">
     <div class="bg-white/20 backdrop-blur rounded-2xl p-4 flex justify-between items-center">
      <div class="text-white"><span class="text-sm">คะแนน</span>
       <div id="score" class="text-2xl font-bold">
        0
       </div>
      </div>
      <div class="text-white text-center"><span class="text-sm">ข้อที่</span>
       <div id="question-num" class="text-2xl font-bold">
        1/10
       </div>
      </div>
      <div class="text-white text-right"><span class="text-sm">ถูกต้อง</span>
       <div id="correct-count" class="text-2xl font-bold">
        0
       </div>
      </div>
     </div><!-- Progress Bar -->
     <div class="mt-3 bg-white/30 rounded-full h-3 overflow-hidden">
      <div id="progress-bar" class="progress-bar h-full rounded-full transition-all duration-500" style="width: 10%"></div>
     </div>
    </div><!-- Main Game Area -->
    <main id="main-content" class="max-w-2xl mx-auto"><!-- Menu Screen -->
     <div id="menu-screen" class="bg-white rounded-3xl card-shadow p-6 md:p-8">
      <div class="text-center mb-8">
       <div class="text-6xl mb-4">
        🏦
       </div>
       <h2 class="text-2xl font-bold text-emerald-800 mb-2">เลือกบทเรียน</h2>
       <p class="text-gray-600">เลือกหัวข้อที่ต้องการฝึกฝน</p>
      </div>
      <div class="grid gap-4"><button onclick="startGame('counting')" class="btn-primary text-white font-semibold py-4 px-6 rounded-2xl flex items-center gap-4 w-full"> <span class="text-3xl">🪙</span>
        <div class="text-left">
         <div class="text-lg">
          นับเงิน
         </div>
         <div class="text-sm opacity-80">
          ฝึกนับธนบัตรและเหรียญ
         </div>
        </div></button> <button onclick="startGame('change')" class="btn-primary text-white font-semibold py-4 px-6 rounded-2xl flex items-center gap-4 w-full"> <span class="text-3xl">💵</span>
        <div class="text-left">
         <div class="text-lg">
          ทอนเงิน
         </div>
         <div class="text-sm opacity-80">
          คำนวณเงินทอน
         </div>
        </div></button> <button onclick="startGame('shopping')" class="btn-primary text-white font-semibold py-4 px-6 rounded-2xl flex items-center gap-4 w-full"> <span class="text-3xl">🛒</span>
        <div class="text-left">
         <div class="text-lg">
          ซื้อของ
         </div>
         <div class="text-sm opacity-80">
          รวมราคาสินค้า
         </div>
        </div></button> <button onclick="startGame('saving')" class="btn-primary text-white font-semibold py-4 px-6 rounded-2xl flex items-center gap-4 w-full"> <span class="text-3xl">🐷</span>
        <div class="text-left">
         <div class="text-lg">
          ออมเงิน
         </div>
         <div class="text-sm opacity-80">
          วางแผนการออม
         </div>
        </div></button>
      </div>
     </div><!-- Game Screen -->
     <div id="game-screen" class="hidden">
      <div class="bg-white rounded-3xl card-shadow p-6 md:p-8">
       <div id="question-area" class="text-center"><!-- Question content will be inserted here -->
       </div>
       <div id="answer-area" class="mt-6"><!-- Answer options will be inserted here -->
       </div>
       <div id="feedback-area" class="mt-4 text-center hidden"><!-- Feedback will be shown here -->
       </div>
      </div>
      <div class="mt-4 flex gap-3"><button onclick="showMenu()" class="flex-1 bg-white/20 hover:bg-white/30 text-white font-semibold py-3 px-6 rounded-xl transition"> 🏠 กลับหน้าหลัก </button> <button id="next-btn" onclick="nextQuestion()" class="flex-1 bg-white text-emerald-700 font-semibold py-3 px-6 rounded-xl hover:bg-emerald-50 transition hidden"> ข้อถัดไป ➡️ </button>
      </div>
     </div><!-- Result Screen -->
     <div id="result-screen" class="hidden">
      <div class="bg-white rounded-3xl card-shadow p-6 md:p-8 text-center">
       <div id="result-emoji" class="text-7xl mb-4">
        🎉
       </div>
       <h2 id="result-title" class="text-2xl font-bold text-emerald-800 mb-2">ยอดเยี่ยม!</h2>
       <p id="result-message" class="text-gray-600 mb-6">คุณทำได้ดีมาก!</p>
       <div class="bg-emerald-50 rounded-2xl p-6 mb-6">
        <div class="text-4xl font-bold text-emerald-600" id="final-score">
         100
        </div>
        <div class="text-gray-500">
         คะแนนที่ได้
        </div>
        <div class="mt-3 text-lg">
         ตอบถูก <span id="final-correct" class="font-bold text-emerald-600">10</span> จาก 10 ข้อ
        </div>
       </div>
       <div class="grid grid-cols-2 gap-3"><button onclick="showMenu()" class="bg-gray-100 hover:bg-gray-200 text-gray-700 font-semibold py-3 px-6 rounded-xl transition"> 🏠 หน้าหลัก </button> <button onclick="restartGame()" class="btn-primary text-white font-semibold py-3 px-6 rounded-xl"> 🔄 เล่นอีกครั้ง </button>
       </div>
      </div>
     </div>
    </main><!-- Footer -->
    <footer class="text-center mt-6 text-emerald-100 text-sm">
     <p>💡 เรียนรู้คณิตศาสตร์การเงินให้สนุก!</p>
    </footer>
   </div>
  </div>
  <script>
    // Default configuration
    const defaultConfig = {
      app_title: 'คณิตศาสตร์การเงิน ป.5',
      welcome_message: 'เรียนรู้เรื่องเงินอย่างสนุกสนาน!',
      primary_color: '#fce7f3',
      secondary_color: '#ffffff',
      text_color: '#ec4899',
      accent_color: '#f59e0b',
      button_color: '#d97706',
      font_family: 'Kanit'
    };

    let config = { ...defaultConfig };

    // Game state
    let currentGame = '';
    let currentQuestion = 0;
    let score = 0;
    let correctCount = 0;
    let questions = [];
    const totalQuestions = 10;

    // Thai currency
    const bills = [1000, 500, 100, 50, 20];
    const coins = [10, 5, 2, 1];
    const billEmojis = { 1000: '💵', 500: '💴', 100: '💶', 50: '💷', 20: '💸' };

    // Products for shopping game
    const products = [
      { name: 'ดินสอ', price: 5, emoji: '✏️' },
      { name: 'ยางลบ', price: 8, emoji: '🧽' },
      { name: 'สมุด', price: 15, emoji: '📓' },
      { name: 'ไม้บรรทัด', price: 12, emoji: '📏' },
      { name: 'กล่องดินสอ', price: 35, emoji: '🎁' },
      { name: 'ปากกา', price: 10, emoji: '🖊️' },
      { name: 'กาว', price: 20, emoji: '🧴' },
      { name: 'กรรไกร', price: 25, emoji: '✂️' },
      { name: 'สีไม้', price: 45, emoji: '🖍️' },
      { name: 'กระเป๋า', price: 199, emoji: '🎒' },
      { name: 'ขนม', price: 10, emoji: '🍪' },
      { name: 'น้ำดื่ม', price: 7, emoji: '💧' },
      { name: 'นม', price: 12, emoji: '🥛' },
      { name: 'ขนมปัง', price: 25, emoji: '🍞' },
      { name: 'ไอศกรีม', price: 20, emoji: '🍦' }
    ];

    // Initialize SDK
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange: async (newConfig) => {
          config = { ...defaultConfig, ...newConfig };
          updateUI();
        },
        mapToCapabilities: (cfg) => ({
          recolorables: [
            {
              get: () => cfg.primary_color || defaultConfig.primary_color,
              set: (v) => { cfg.primary_color = v; window.elementSdk.setConfig({ primary_color: v }); }
            },
            {
              get: () => cfg.secondary_color || defaultConfig.secondary_color,
              set: (v) => { cfg.secondary_color = v; window.elementSdk.setConfig({ secondary_color: v }); }
            },
            {
              get: () => cfg.text_color || defaultConfig.text_color,
              set: (v) => { cfg.text_color = v; window.elementSdk.setConfig({ text_color: v }); }
            },
            {
              get: () => cfg.accent_color || defaultConfig.accent_color,
              set: (v) => { cfg.accent_color = v; window.elementSdk.setConfig({ accent_color: v }); }
            },
            {
              get: () => cfg.button_color || defaultConfig.button_color,
              set: (v) => { cfg.button_color = v; window.elementSdk.setConfig({ button_color: v }); }
            }
          ],
          borderables: [],
          fontEditable: {
            get: () => cfg.font_family || defaultConfig.font_family,
            set: (v) => { cfg.font_family = v; window.elementSdk.setConfig({ font_family: v }); }
          },
          fontSizeable: undefined
        }),
        mapToEditPanelValues: (cfg) => new Map([
          ['app_title', cfg.app_title || defaultConfig.app_title],
          ['welcome_message', cfg.welcome_message || defaultConfig.welcome_message]
        ])
      });
    }

    function updateUI() {
      const title = document.getElementById('app-title');
      const welcome = document.getElementById('welcome-message');
      const wrapper = document.getElementById('app-wrapper');
      
      title.textContent = config.app_title || defaultConfig.app_title;
      welcome.textContent = config.welcome_message || defaultConfig.welcome_message;
      
      // Apply colors
      const primaryColor = config.primary_color || defaultConfig.primary_color;
      const secondaryColor = config.secondary_color || defaultConfig.secondary_color;
      const textColor = config.text_color || defaultConfig.text_color;
      const accentColor = config.accent_color || defaultConfig.accent_color;
      const buttonColor = config.button_color || defaultConfig.button_color;
      
      wrapper.style.background = `linear-gradient(135deg, ${textColor} 0%, ${primaryColor} 50%, ${primaryColor}dd 100%)`;
      
      document.querySelectorAll('.btn-primary').forEach(btn => {
        btn.style.background = `linear-gradient(135deg, ${accentColor} 0%, ${buttonColor} 100%)`;
      });
      
      document.querySelectorAll('.bg-white, .card-shadow').forEach(el => {
        if (el.classList.contains('rounded-3xl')) {
          el.style.backgroundColor = secondaryColor;
        }
      });
      
      // Apply font
      const fontFamily = config.font_family || defaultConfig.font_family;
      document.body.style.fontFamily = `${fontFamily}, Kanit, sans-serif`;
    }

    // Generate random number in range
    function randomInt(min, max) {
      return Math.floor(Math.random() * (max - min + 1)) + min;
    }

    // Shuffle array
    function shuffle(array) {
      const arr = [...array];
      for (let i = arr.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [arr[i], arr[j]] = [arr[j], arr[i]];
      }
      return arr;
    }

    // Generate counting money question
    function generateCountingQuestion() {
      const amounts = [];
      let total = 0;
      
      // Add some bills
      const numBills = randomInt(1, 3);
      for (let i = 0; i < numBills; i++) {
        const bill = bills[randomInt(0, 4)];
        amounts.push({ type: 'bill', value: bill });
        total += bill;
      }
      
      // Add some coins
      const numCoins = randomInt(1, 4);
      for (let i = 0; i < numCoins; i++) {
        const coin = coins[randomInt(0, 3)];
        amounts.push({ type: 'coin', value: coin });
        total += coin;
      }
      
      return {
        type: 'counting',
        amounts: shuffle(amounts),
        answer: total,
        question: 'นับจำนวนเงินทั้งหมด'
      };
    }

    // Generate change question
    function generateChangeQuestion() {
      const payAmounts = [20, 50, 100, 500, 1000];
      const price = randomInt(5, 95);
      const validPay = payAmounts.filter(p => p > price);
      const pay = validPay[randomInt(0, validPay.length - 1)];
      const change = pay - price;
      
      return {
        type: 'change',
        price: price,
        pay: pay,
        answer: change,
        question: `ซื้อของราคา ${price} บาท จ่ายเงิน ${pay} บาท ได้เงินทอนเท่าไร?`
      };
    }

    // Generate shopping question
    function generateShoppingQuestion() {
      const numItems = randomInt(2, 4);
      const selectedProducts = shuffle(products).slice(0, numItems);
      const total = selectedProducts.reduce((sum, p) => sum + p.price, 0);
      
      return {
        type: 'shopping',
        items: selectedProducts,
        answer: total,
        question: 'รวมราคาสินค้าทั้งหมดเท่าไร?'
      };
    }

    // Generate saving question
    function generateSavingQuestion() {
      const types = [
        () => {
          const perDay = randomInt(5, 20) * 5;
          const days = randomInt(5, 14);
          return {
            answer: perDay * days,
            question: `ถ้าออมเงินวันละ ${perDay} บาท เป็นเวลา ${days} วัน จะมีเงินออมเท่าไร?`
          };
        },
        () => {
          const target = randomInt(10, 50) * 10;
          const has = randomInt(1, target / 10 - 1) * 10;
          return {
            answer: target - has,
            question: `ต้องการซื้อของราคา ${target} บาท มีเงินอยู่ ${has} บาท ต้องออมเงินอีกเท่าไร?`
          };
        },
        () => {
          const perWeek = randomInt(10, 50) * 5;
          const weeks = randomInt(2, 8);
          return {
            answer: perWeek * weeks,
            question: `ถ้าออมเงินสัปดาห์ละ ${perWeek} บาท เป็นเวลา ${weeks} สัปดาห์ จะมีเงินออมเท่าไร?`
          };
        }
      ];
      
      const selected = types[randomInt(0, types.length - 1)]();
      return {
        type: 'saving',
        ...selected
      };
    }

    // Generate questions based on game type
    function generateQuestions(type) {
      const questionGenerators = {
        counting: generateCountingQuestion,
        change: generateChangeQuestion,
        shopping: generateShoppingQuestion,
        saving: generateSavingQuestion
      };
      
      const generator = questionGenerators[type];
      return Array.from({ length: totalQuestions }, () => generator());
    }

    // Generate answer choices
    function generateChoices(answer) {
      const choices = [answer];
      const offsets = [-20, -10, -5, 5, 10, 20, -15, 15, -25, 25];
      
      while (choices.length < 4) {
        const offset = offsets[randomInt(0, offsets.length - 1)];
        const choice = Math.max(1, answer + offset);
        if (!choices.includes(choice)) {
          choices.push(choice);
        }
      }
      
      return shuffle(choices);
    }

    // Display current question
    function displayQuestion() {
      const q = questions[currentQuestion];
      const questionArea = document.getElementById('question-area');
      const answerArea = document.getElementById('answer-area');
      
      let html = '';
      
      if (q.type === 'counting') {
        html = `
          <div class="text-lg text-gray-600 mb-4">${q.question}</div>
          <div class="flex flex-wrap justify-center gap-3 mb-4">
            ${q.amounts.map(a => {
              if (a.type === 'bill') {
                return `<div class="bg-green-100 border-2 border-green-300 rounded-xl px-4 py-3 text-center">
                  <div class="text-2xl">${billEmojis[a.value]}</div>
                  <div class="text-green-700 font-bold">${a.value} บาท</div>
                </div>`;
              } else {
                return `<div class="bg-yellow-100 border-2 border-yellow-300 rounded-full w-16 h-16 flex flex-col items-center justify-center">
                  <div class="text-lg">🪙</div>
                  <div class="text-yellow-700 font-bold text-sm">${a.value}</div>
                </div>`;
              }
            }).join('')}
          </div>
        `;
      } else if (q.type === 'shopping') {
        html = `
          <div class="text-lg text-gray-600 mb-4">${q.question}</div>
          <div class="flex flex-wrap justify-center gap-3 mb-4">
            ${q.items.map(item => `
              <div class="bg-blue-50 border-2 border-blue-200 rounded-xl px-4 py-3 text-center">
                <div class="text-3xl mb-1">${item.emoji}</div>
                <div class="text-gray-700">${item.name}</div>
                <div class="text-blue-600 font-bold">${item.price} บาท</div>
              </div>
            `).join('')}
          </div>
        `;
      } else {
        html = `
          <div class="text-5xl mb-4">${q.type === 'change' ? '💵' : '🐷'}</div>
          <div class="text-xl text-gray-700">${q.question}</div>
        `;
      }
      
      questionArea.innerHTML = html;
      
      // Generate and display choices
      const choices = generateChoices(q.answer);
      answerArea.innerHTML = `
        <div class="grid grid-cols-2 gap-3">
          ${choices.map(choice => `
            <button onclick="checkAnswer(${choice}, ${q.answer})" 
                    class="choice-btn bg-emerald-50 hover:bg-emerald-100 border-2 border-emerald-200 
                           text-emerald-700 font-bold py-4 px-6 rounded-xl text-xl transition
                           hover:border-emerald-400 hover:scale-105">
              ${choice} บาท
            </button>
          `).join('')}
        </div>
      `;
      
      // Update progress
      document.getElementById('question-num').textContent = `${currentQuestion + 1}/${totalQuestions}`;
      document.getElementById('progress-bar').style.width = `${((currentQuestion + 1) / totalQuestions) * 100}%`;
      
      // Hide feedback and next button
      document.getElementById('feedback-area').classList.add('hidden');
      document.getElementById('next-btn').classList.add('hidden');
    }

    // Check answer
    function checkAnswer(selected, correct) {
      const isCorrect = selected === correct;
      const feedbackArea = document.getElementById('feedback-area');
      const buttons = document.querySelectorAll('.choice-btn');
      
      // Disable all buttons
      buttons.forEach(btn => {
        btn.disabled = true;
        const btnValue = parseInt(btn.textContent);
        if (btnValue === correct) {
          btn.classList.remove('bg-emerald-50', 'border-emerald-200', 'text-emerald-700');
          btn.classList.add('bg-green-500', 'border-green-500', 'text-white');
        } else if (btnValue === selected && !isCorrect) {
          btn.classList.remove('bg-emerald-50', 'border-emerald-200', 'text-emerald-700');
          btn.classList.add('bg-red-500', 'border-red-500', 'text-white', 'shake');
        }
      });
      
      if (isCorrect) {
        correctCount++;
        score += 10;
        feedbackArea.innerHTML = `
          <div class="bg-green-100 text-green-700 py-3 px-6 rounded-xl inline-block celebrate">
            <span class="text-2xl">🎉</span> ถูกต้อง! +10 คะแนน
          </div>
        `;
      } else {
        feedbackArea.innerHTML = `
          <div class="bg-red-100 text-red-700 py-3 px-6 rounded-xl inline-block">
            <span class="text-2xl">😢</span> เสียใจด้วย คำตอบคือ ${correct} บาท
          </div>
        `;
      }
      
      feedbackArea.classList.remove('hidden');
      document.getElementById('score').textContent = score;
      document.getElementById('correct-count').textContent = correctCount;
      document.getElementById('next-btn').classList.remove('hidden');
    }

    // Next question
    function nextQuestion() {
      currentQuestion++;
      if (currentQuestion >= totalQuestions) {
        showResult();
      } else {
        displayQuestion();
      }
    }

    // Show result screen
    function showResult() {
      document.getElementById('game-screen').classList.add('hidden');
      document.getElementById('result-screen').classList.remove('hidden');
      
      const percentage = (correctCount / totalQuestions) * 100;
      
      let emoji, title, message;
      if (percentage >= 90) {
        emoji = '🏆';
        title = 'ยอดเยี่ยมมาก!';
        message = 'คุณเก่งมาก! เป็นนักคณิตศาสตร์ตัวยง!';
      } else if (percentage >= 70) {
        emoji = '🎉';
        title = 'ดีมาก!';
        message = 'ทำได้ดีเลย! ฝึกเพิ่มอีกนิดจะสุดยอดเลย!';
      } else if (percentage >= 50) {
        emoji = '👍';
        title = 'ดีแล้ว!';
        message = 'พยายามต่อไป! ฝึกฝนแล้วจะเก่งขึ้น!';
      } else {
        emoji = '💪';
        title = 'พยายามอีกนิด!';
        message = 'ไม่เป็นไร ลองเล่นอีกครั้งนะ!';
      }
      
      document.getElementById('result-emoji').textContent = emoji;
      document.getElementById('result-title').textContent = title;
      document.getElementById('result-message').textContent = message;
      document.getElementById('final-score').textContent = score;
      document.getElementById('final-correct').textContent = correctCount;
    }

    // Start game
    function startGame(type) {
      currentGame = type;
      currentQuestion = 0;
      score = 0;
      correctCount = 0;
      questions = generateQuestions(type);
      
      document.getElementById('score').textContent = '0';
      document.getElementById('correct-count').textContent = '0';
      
      document.getElementById('menu-screen').classList.add('hidden');
      document.getElementById('result-screen').classList.add('hidden');
      document.getElementById('game-screen').classList.remove('hidden');
      
      displayQuestion();
    }

    // Restart game
    function restartGame() {
      startGame(currentGame);
    }

    // Show menu
    function showMenu() {
      document.getElementById('game-screen').classList.add('hidden');
      document.getElementById('result-screen').classList.add('hidden');
      document.getElementById('menu-screen').classList.remove('hidden');
      
      // Reset
      currentQuestion = 0;
      score = 0;
      correctCount = 0;
      document.getElementById('score').textContent = '0';
      document.getElementById('correct-count').textContent = '0';
      document.getElementById('question-num').textContent = '1/10';
      document.getElementById('progress-bar').style.width = '10%';
    }

    // Initial UI update
    updateUI();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9c133e8f70207336',t:'MTc2ODk2MTEwMy4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
