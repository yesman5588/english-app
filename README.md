<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>大家說英語 - 廣播單字學習卡生成器</title>
  <style>
    :root {
      --primary: #1a73e8;
      --primary-hover: #1557b0;
      --primary-light: #e8f0fe;
      --accent: #34a853;
      --accent-light: #e6f4ea;
      --text: #202124;
      --text-muted: #5f6368;
      --bg: #f8f9fa;
      --card-bg: #ffffff;
      --border: #dadce0;
    }
    
    * {
      box-sizing: border-box;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans TC", sans-serif;
      background-color: var(--bg);
      color: var(--text);
      margin: 0;
      padding: 24px 16px;
      line-height: 1.6;
    }

    .container {
      max-width: 900px;
      margin: 0 auto;
    }

    header {
      text-align: center;
      margin-bottom: 24px;
    }

    header h1 {
      color: var(--primary);
      margin: 0 0 8px 0;
      font-size: 1.8rem;
    }

    header p {
      color: var(--text-muted);
      margin: 0;
      font-size: 0.95rem;
    }

    /* 輸入區域 */
    .input-card {
      background: var(--card-bg);
      padding: 20px;
      border-radius: 12px;
      border: 1px solid var(--border);
      box-shadow: 0 2px 6px rgba(0,0,0,0.04);
      margin-bottom: 20px;
    }

    .input-group {
      display: flex;
      gap: 10px;
      margin-top: 10px;
      flex-wrap: wrap;
    }

    input[type="text"] {
      flex: 1;
      min-width: 260px;
      padding: 12px 16px;
      border: 2px solid var(--border);
      border-radius: 8px;
      font-size: 1rem;
      outline: none;
      transition: border-color 0.2s;
    }

    input[type="text"]:focus {
      border-color: var(--primary);
    }

    .btn-submit {
      background-color: var(--primary);
      color: #fff;
      border: none;
      padding: 12px 24px;
      border-radius: 8px;
      font-size: 1rem;
      font-weight: 600;
      cursor: pointer;
      transition: background 0.2s;
    }

    .btn-submit:hover {
      background-color: var(--primary-hover);
    }

    .loading-text {
      margin-top: 10px;
      color: var(--primary);
      font-size: 0.9rem;
      font-weight: bold;
      display: none;
    }

    /* 頂部控制列 */
    .controls-card {
      display: flex;
      gap: 16px;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      background: var(--primary-light);
      padding: 16px 20px;
      border-radius: 12px;
      margin-bottom: 24px;
      border: 1px solid #d2e3fc;
    }

    .control-btns {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
    }

    .btn-audio {
      background-color: #ffffff;
      color: var(--primary);
      border: 2px solid var(--primary);
      padding: 10px 18px;
      border-radius: 20px;
      font-size: 0.95rem;
      font-weight: bold;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      transition: all 0.2s;
    }

    .btn-audio:hover {
      background-color: var(--primary);
      color: #ffffff;
    }

    .speed-group {
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 0.95rem;
    }

    select {
      padding: 8px 12px;
      border-radius: 6px;
      border: 1px solid var(--border);
      background-color: #fff;
      font-size: 0.9rem;
      outline: none;
    }

    /* 三大核心卡片風格 */
    .card {
      background: var(--card-bg);
      border-radius: 12px;
      padding: 24px;
      margin-bottom: 24px;
      border: 1px solid var(--border);
      border-left: 6px solid var(--primary);
      box-shadow: 0 2px 6px rgba(0,0,0,0.04);
    }

    .card h2 {
      margin-top: 0;
      color: var(--primary);
      font-size: 1.25rem;
      border-bottom: 2px solid var(--primary-light);
      padding-bottom: 10px;
      margin-bottom: 20px;
    }

    /* 卡片 1：發音拆解 */
    .phonics-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 16px;
    }

    .phonics-item {
      background: var(--primary-light);
      padding: 16px;
      border-radius: 8px;
      border: 1px solid #d2e3fc;
    }

    .phonics-item .word-title {
      font-size: 1.2rem;
      font-weight: bold;
      color: var(--primary);
      margin-bottom: 8px;
      display: block;
    }

    .tag {
      display: inline-block;
      background: var(--primary);
      color: white;
      padding: 2px 8px;
      border-radius: 4px;
      font-size: 0.85rem;
      font-weight: 500;
    }

    .phonics-detail {
      font-size: 0.9rem;
      color: var(--text-muted);
      margin-top: 8px;
    }

    /* 卡片 2：單字例句 */
    .vocab-item {
      padding-bottom: 16px;
      margin-bottom: 16px;
      border-bottom: 1px dashed var(--border);
    }

    .vocab-item:last-child {
      border-bottom: none;
      padding-bottom: 0;
      margin-bottom: 0;
    }

    .vocab-header {
      font-size: 1.15rem;
      color: var(--primary);
      margin-bottom: 6px;
    }

    .vocab-pos {
      font-size: 0.9rem;
      color: var(--text-muted);
      font-style: italic;
    }

    .vocab-en {
      font-size: 1rem;
      color: var(--text);
      margin: 4px 0;
    }

    .vocab-zh {
      font-size: 0.95rem;
      color: var(--text-muted);
    }

    /* 卡片 3：廣播故事 */
    .story-section {
      background: #f8f9fa;
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 18px;
      margin-bottom: 16px;
    }

    .story-section:last-child {
      margin-bottom: 0;
    }

    .story-section h3 {
      margin-top: 0;
      font-size: 1.05rem;
      color: var(--primary);
      margin-bottom: 8px;
    }

    .story-en {
      font-size: 1.05rem;
      font-weight: 600;
      color: var(--text);
      margin-bottom: 4px;
    }

    .story-zh {
      font-size: 0.95rem;
      color: var(--text-muted);
      margin-bottom: 12px;
    }

    .teacher-note {
      background: var(--accent-light);
      border-left: 4px solid var(--accent);
      padding: 10px 14px;
      border-radius: 0 6px 6px 0;
      font-size: 0.9rem;
      color: #137333;
    }
  </style>
</head>
<body>

<div class="container">
  <header>
    <h1>🎙️ 大家說英語 - 廣播單字學習卡生成器</h1>
    <p>藍白簡約現代風格卡片 ｜ 免費 API 即時線上辭典檢索</p>
  </header>

  <!-- 單字輸入區 -->
  <div class="input-card">
    <label for="wordInput"><strong>請輸入 5 個英文單字（用逗號或空格隔開）：</strong></label>
    <div class="input-group">
      <input type="text" id="wordInput" value="witch, forest, magic, broom, fly" placeholder="例如: witch, forest, magic, broom, fly">
      <button class="btn-submit" onclick="handleGenerate()">產生廣播學習卡</button>
    </div>
    <div class="loading-text" id="loadingStatus">🔄 正在連線字典 API 獲取劍橋風格釋義與例句...</div>
  </div>

  <!-- 頂部雙控制按鈕與語速切換 -->
  <div class="controls-card">
    <div class="control-btns">
      <button class="btn-audio" onclick="playVocabulary()">🔊 播放繁體中文意思與造句</button>
      <button class="btn-audio" onclick="playRadioStory()">📻 播放 5 分鐘廣播聽力實戰</button>
    </div>
    <div class="speed-group">
      <label for="speedSelect"><strong>語速切換：</strong></label>
      <select id="speedSelect">
        <option value="1.0" selected>1.0x 預設（英文 0.82x / 中文 1.25x）</option>
        <option value="0.8">0.8x 慢速對照</option>
        <option value="1.2">1.2x 挑戰語速</option>
      </select>
    </div>
  </div>

  <!-- 卡片 1：單字發音拆解 -->
  <div class="card">
    <h2>1. 單字發音拆解</h2>
    <div class="phonics-grid" id="phonicsContent"></div>
  </div>

  <!-- 卡片 2：繁體中文意思與造句 -->
  <div class="card">
    <h2>2. 繁體中文意思與造句</h2>
    <div id="vocabContent"></div>
  </div>

  <!-- 卡片 3：5分鐘廣播聽力實戰故事與重點解說 -->
  <div class="card">
    <h2>3. 5分鐘廣播聽力實戰故事與重點解說</h2>
    <div id="storyContent"></div>
  </div>
</div>

<script>
let currentWordsData = [];

// Free Dictionary API & MyMemory Translate API 即時動態檢索
async function fetchWordDetails(word) {
  let pos = "n.";
  let sentenceEn = "";
  let sentenceZh = "";
  let zh = "";

  try {
    // 1. 查詢 Free Dictionary API 取得實體詞性與例句
    const dictRes = await fetch(`https://api.dictionaryapi.dev/api/v2/entries/en/${encodeURIComponent(word)}`);
    if (dictRes.ok) {
      const data = await dictRes.json();
      const firstMeaning = data[0]?.meanings[0];
      if (firstMeaning) {
        pos = firstMeaning.partOfSpeech ? `${firstMeaning.partOfSpeech}.` : "n.";
        const exampleObj = firstMeaning.definitions.find(d => d.example);
        if (exampleObj) {
          sentenceEn = exampleObj.example;
        }
      }
    }
  } catch (e) {
    console.warn("Free Dictionary API 連線失敗，啟動備用發音邏輯", e);
  }

  // 若 API 未提供例句，自動生成標準基礎例句
  if (!sentenceEn) {
    sentenceEn = `Sam found a special ${word} near the garden.`;
  }

  try {
    // 2. 查詢 MyMemory Translation API 獲取劍橋風格精準繁體中文釋義
    const transRes = await fetch(`https://api.mymemory.translated.net/get?q=${encodeURIComponent(word)}&langpair=en|zh-TW`);
    if (transRes.ok) {
      const transData = await transRes.json();
      zh = transData.responseData?.translatedText || word;
      zh = zh.replace(/[.\r\n]/g, '').trim();
    }
  } catch (e) {
    zh = `${word}（繁中釋義）`;
  }

  try {
    // 3. 查詢例句中文翻譯
    const sentenceTransRes = await fetch(`https://api.mymemory.translated.net/get?q=${encodeURIComponent(sentenceEn)}&langpair=en|zh-TW`);
    if (sentenceTransRes.ok) {
      const sData = await sentenceTransRes.json();
      sentenceZh = sData.responseData?.translatedText || sentenceEn;
    }
  } catch (e) {
    sentenceZh = `Sam 在花園附近發現了一個特別的 ${zh}。`;
  }

  return { pos, zh, sentenceEn, sentenceZh };
}

// Hanna et al. 音素拆解解析器
function analyzePhonics(word) {
  const w = word.toLowerCase();
  let phonemes = [];
  let i = 0;
  
  while (i < w.length) {
    if (w.substr(i, 2) === 'ch') { phonemes.push('/tʃ/'); i += 2; }
    else if (w.substr(i, 2) === 'sh') { phonemes.push('/ʃ/'); i += 2; }
    else if (w.substr(i, 2) === 'th') { phonemes.push('/θ/'); i += 2; }
    else if (w.substr(i, 2) === 'oo') { phonemes.push('/uː/'); i += 2; }
    else if (w.substr(i, 2) === 'ee') { phonemes.push('/iː/'); i += 2; }
    else if (w.substr(i, 2) === 'ck') { phonemes.push('/k/'); i += 2; }
    else {
      let c = w[i];
      if (c === 'a') phonemes.push('/æ/');
      else if (c === 'e') phonemes.push('/e/');
      else if (c === 'i') phonemes.push('/ɪ/');
      else if (c === 'o') phonemes.push('/ɒ/');
      else if (c === 'u') phonemes.push('/ʌ/');
      else if (c === 'w') phonemes.push('/w/');
      else if (c === 'f') phonemes.push('/f/');
      else if (c === 'r') phonemes.push('/r/');
      else if (c === 's') phonemes.push('/s/');
      else if (c === 't') phonemes.push('/t/');
      else if (c === 'b') phonemes.push('/b/');
      else if (c === 'm') phonemes.push('/m/');
      else if (c === 'l') phonemes.push('/l/');
      else if (c === 'y') phonemes.push('/aɪ/');
      else phonemes.push(`/${c}/`);
      i++;
    }
  }

  let ruleText = "子音與單母音聲學對應拼讀";
  if (w.includes('ch') || w.includes('sh') || w.includes('th')) ruleText = "複合子音組合，雙字母發單一音素";
  else if (w.includes('oo') || w.includes('ee')) ruleText = "雙母音長音組合規則";
  else if (w.length <= 4) ruleText = "CVC 短母音自然拼讀基本規則";

  return {
    count: phonemes.length,
    tags: phonemes.join(' '),
    rule: ruleText
  };
}

// 主處理函式：輸入單字並線上擷取後渲染
async function handleGenerate() {
  const input = document.getElementById('wordInput').value;
  let rawWords = input.split(/[,，\s]+/).map(w => w.trim().toLowerCase()).filter(w => w.length > 0);
  
  if (rawWords.length === 0) {
    alert("請輸入至少 1 個英文單字！");
    return;
  }

  const fallbackList = ["witch", "forest", "magic", "broom", "fly"];
  while(rawWords.length < 5) {
    rawWords.push(fallbackList[rawWords.length]);
  }
  rawWords = rawWords.slice(0, 5);

  const statusEl = document.getElementById('loadingStatus');
  statusEl.style.display = 'block';

  currentWordsData = [];
  for (let w of rawWords) {
    const details = await fetchWordDetails(w);
    currentWordsData.push({
      word: w,
      pos: details.pos,
      zh: details.zh,
      sentenceEn: details.sentenceEn,
      sentenceZh: details.sentenceZh,
      phonics: analyzePhonics(w)
    });
  }

  statusEl.style.display = 'none';

  renderPhonicsCard();
  renderVocabCard();
  renderStoryCard();
}

// 1. 單字發音拆解渲染
function renderPhonicsCard() {
  const container = document.getElementById('phonicsContent');
  container.innerHTML = '';
  currentWordsData.forEach(item => {
    const div = document.createElement('div');
    div.className = 'phonics-item';
    div.innerHTML = `
      <span class="word-title">${item.word.toUpperCase()}</span>
      <div>音素數量：<span class="tag">${item.phonics.count} 個</span></div>
      <div style="margin-top:4px;">音素標籤：<code style="font-size:1rem; color:#1a73e8;">${item.phonics.tags}</code></div>
      <div class="phonics-detail">拼讀規則：${item.phonics.rule}</div>
    `;
    container.appendChild(div);
  });
}

// 2. 繁體中文意思與造句渲染
function renderVocabCard() {
  const container = document.getElementById('vocabContent');
  container.innerHTML = '';
  currentWordsData.forEach(item => {
    const div = document.createElement('div');
    div.className = 'vocab-item';
    div.innerHTML = `
      <div class="vocab-header">
        <strong>${item.word}</strong> <span class="vocab-pos">[${item.pos}]</span> - <strong>${item.zh}</strong>
      </div>
      <div class="vocab-en"><strong>英文例句：</strong>${item.sentenceEn}</div>
      <div class="vocab-zh"><strong>中文翻譯：</strong>${item.sentenceZh}</div>
    `;
    container.appendChild(div);
  });
}

// 3. 5分鐘廣播聽力實戰故事與重點解說渲染
function renderStoryCard() {
  const container = document.getElementById('storyContent');
  container.innerHTML = '';
  
  const w = currentWordsData.map(d => d.word);
  const z = currentWordsData.map(d => d.zh);

  const storySections = [
    {
      en: `Deep inside the quiet ${w[1]}, there lived a friendly old ${w[0]} named Sam.`,
      zh: `在安靜的${z[1]}深處，住著一位名叫 Sam 的友善老${z[0]}。`,
      note: `重點解說：注意名詞 ${w[1]}（${z[1]}）與 ${w[0]}（${z[0]}）的搭配，自然發音連讀非常流暢喔！`,
      targetWord: `${w[0]} / ${w[1]}`
    },
    {
      en: `Every morning, she used her ${w[2]} to make colorful flowers bloom everywhere.`,
      zh: `每天早晨，她都會使用她的${z[2]}，讓五彩繽紛的花朵隨處盛開。`,
      note: `片語延伸：used her ${w[2]} 表示「使用她的${z[2]}」，用來描繪神奇充滿活力的景象。`,
      targetWord: w[2]
    },
    {
      en: `One sunny day, she picked up her wooden ${w[3]} and decided to explore the town.`,
      zh: `在一個晴朗的日子，她拿起她的木頭${z[3]}，決定去探索這個小鎮。`,
      note: `文法重點：decided to + 動詞原形 表示「決定去做某事」，是國小非常實用的經典句型！`,
      targetWord: w[3]
    },
    {
      en: `With a happy smile, she started to ${w[4]} high above the clouds and waved to everyone!`,
      zh: `帶著開心的微笑，她開始在雲端高高地${z[4]}，並向大家揮手致意！`,
      note: `小叮嚀：動詞 ${w[4]}（${z[4]}）在此搭配 start to ${w[4]} 代表「開始${z[4]}」，注意英文發音語調！`,
      targetWord: w[4]
    }
  ];

  storySections.forEach((sec, idx) => {
    const div = document.createElement('div');
    div.className = 'story-section';
    div.innerHTML = `
      <h3>第 ${idx + 1} 節：廣播小故事實戰</h3>
      <div id="story-en-${idx+1}" class="story-en">${sec.en}</div>
      <div id="story-zh-${idx+1}" class="story-zh">${sec.zh}</div>
      <div class="teacher-note">
        💡 <strong>廣播老師雙語深度解說：</strong> ${sec.note}（關鍵字：<code>${sec.targetWord}</code>）
      </div>
    `;
    container.appendChild(div);
  });
}

// Web Audio API 小號高音提示音「燈！燈！燈！」
function playTrumpetSound() {
  return new Promise((resolve) => {
    const AudioContext = window.AudioContext || window.webkitAudioContext;
    if (!AudioContext) { resolve(); return; }
    const ctx = new AudioContext();
    const notes = [523.25, 659.25, 783.99]; // High C5, E5, G5
    
    notes.forEach((freq, idx) => {
      const osc = ctx.createOscillator();
      const gain = ctx.createGain();
      osc.type = 'triangle';
      osc.frequency.value = freq;
      
      const startTime = ctx.currentTime + idx * 0.18;
      gain.gain.setValueAtTime(0.3, startTime);
      gain.gain.exponentialRampToValueAtTime(0.001, startTime + 0.3);
      
      osc.connect(gain);
      gain.connect(ctx.destination);
      osc.start(startTime);
      osc.stop(startTime + 0.3);
    });
    setTimeout(resolve, 800);
  });
}

// 語音朗讀 TTS 引擎 (英文 0.82x, 中文 1.25x 預設)
function speakText(text, lang = 'en-US') {
  return new Promise((resolve) => {
    window.speechSynthesis.cancel();
    const utterance = new SpeechSynthesisUtterance(text);
    const speedMult = parseFloat(document.getElementById('speedSelect').value) || 1.0;

    if (lang === 'zh-TW') {
      utterance.lang = 'zh-TW';
      utterance.rate = 1.25 * speedMult;
    } else {
      utterance.lang = 'en-US';
      utterance.rate = 0.82 * speedMult;
    }

    utterance.onend = () => resolve();
    utterance.onerror = () => resolve();
    window.speechSynthesis.speak(utterance);
  });
}

// 按鈕 1：播放繁體中文意思與造句（完全排除發音拆解語音）
async function playVocabulary() {
  if (currentWordsData.length === 0) return;
  for (let item of currentWordsData) {
    await speakText(item.word, 'en-US');
    await speakText(`${item.word}，繁體中文意思是：${item.zh}`, 'zh-TW');
    await speakText(item.sentenceEn, 'en-US');
    await speakText(item.sentenceZh, 'zh-TW');
  }
}

// 按鈕 2：播放 5 分鐘廣播聽力實戰
async function playRadioStory() {
  if (currentWordsData.length === 0) return;

  // 1. 先播放小號高音提示音「燈！燈！燈！」
  await playTrumpetSound();
  
  // 2. 開場白
  await speakText("Welcome to Let's Talk English Radio! Let's listen to today's story.", 'en-US');
  await speakText("歡迎來到大家說英語廣播電台，讓我們一起來聽今天的廣播小故事！", 'zh-TW');

  // 3. 依序朗讀：英文故事段落 -> 中文直譯朗讀 -> 廣播老師雙語深度解說 -> 安靜休息 3 秒
  for (let i = 1; i <= 4; i++) {
    const storyEn = document.getElementById(`story-en-${i}`);
    const storyZh = document.getElementById(`story-zh-${i}`);
    if (storyEn && storyZh) {
      await speakText(storyEn.innerText, 'en-US');
      await speakText(storyZh.innerText, 'zh-TW');
      await speakText(`廣播老師解說：請同學們特別注意第 ${i} 段中的文法與單字發音重點喔！`, 'zh-TW');
      await new Promise(r => setTimeout(r, 3000)); // 安靜休息 3 秒
    }
  }
}

// 頁面載入時自動執行一次
window.onload = handleGenerate;
</script>

</body>
</html>
