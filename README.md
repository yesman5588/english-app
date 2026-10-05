[1005.html](https://github.com/user-attachments/files/33050405/1005.html)
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>English Vocabulary Learning Hub - 大家說英語廣播單字教材</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <style>
        :root {
            --primary: #2563eb;
            --primary-hover: #1d4ed8;
            --bg-slate: #f8fafc;
            --card-bg: #ffffff;
            --text-dark: #1e293b;
            --text-muted: #64748b;
            --accent-green: #059669;
            --accent-purple: #7c3aed;
            --highlight-bg: #fef08a;
            --border-color: #e2e8f0;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
        }

        body {
            background-color: var(--bg-slate);
            color: var(--text-dark);
            line-height: 1.6;
            padding-bottom: 60px;
        }

        header {
            background: linear-gradient(135deg, #1e40af, #3b82f6);
            color: white;
            padding: 2rem 1rem;
            text-align: center;
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.1);
        }

        header h1 {
            font-size: 1.8rem;
            margin-bottom: 0.5rem;
        }

        header p {
            font-size: 0.95rem;
            opacity: 0.9;
        }

        .container {
            max-width: 900px;
            margin: -20px auto 0;
            padding: 0 1rem;
        }

        .control-panel {
            background: var(--card-bg);
            border-radius: 12px;
            padding: 1.5rem;
            box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1);
            margin-bottom: 2rem;
        }

        .input-group {
            display: flex;
            gap: 10px;
            margin-bottom: 1.2rem;
        }

        input[type="text"] {
            flex: 1;
            padding: 0.8rem 1rem;
            border: 2px solid var(--border-color);
            border-radius: 8px;
            font-size: 1rem;
            outline: none;
            transition: border-color 0.2s;
        }

        input[type="text"]:focus {
            border-color: var(--primary);
        }

        .btn {
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 0.8rem 1.2rem;
            border-radius: 8px;
            font-size: 0.95rem;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.2s, transform 0.1s;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .btn:hover {
            background-color: var(--primary-hover);
        }

        .btn:active {
            transform: scale(0.98);
        }

        .btn-green {
            background-color: var(--accent-green);
        }
        .btn-green:hover {
            background-color: #047857;
        }

        .btn-purple {
            background-color: var(--accent-purple);
        }
        .btn-purple:hover {
            background-color: #6d28d9;
        }

        .master-player {
            background: #eff6ff;
            border: 2px solid #bfdbfe;
            border-radius: 10px;
            padding: 1rem;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .player-info {
            display: flex;
            align-items: center;
            gap: 10px;
            font-weight: 600;
            color: var(--primary);
        }

        .player-controls {
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            gap: 10px;
        }

        .speed-selector {
            padding: 0.5rem 0.6rem;
            border-radius: 6px;
            border: 1px solid #93c5fd;
            background: white;
            color: var(--primary);
            font-weight: 600;
            cursor: pointer;
        }

        .section-card {
            background: var(--card-bg);
            border-radius: 12px;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05);
            border: 1px solid var(--border-color);
            transition: border-color 0.3s, box-shadow 0.3s;
        }

        .section-card.speaking {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.2);
            background-color: #f8fafc;
        }

        .section-title {
            font-size: 1.25rem;
            color: var(--primary);
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 8px;
            border-bottom: 2px solid #f1f5f9;
            padding-bottom: 0.5rem;
        }

        .section-title .source-tag {
            font-size: 0.75rem;
            background: #e0e7ff;
            color: #3730a3;
            padding: 2px 8px;
            border-radius: 12px;
            font-weight: normal;
            margin-left: auto;
        }

        .word-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1rem;
        }

        .word-item {
            background: #f8fafc;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 1rem;
        }

        .word-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 0.5rem;
        }

        .word-title {
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--text-dark);
        }

        .phoneme-container {
            display: flex;
            gap: 6px;
            flex-wrap: wrap;
            margin: 6px 0;
        }

        .phoneme-badge {
            background: #f3e8ff;
            color: var(--accent-purple);
            font-family: monospace;
            padding: 3px 8px;
            border-radius: 6px;
            font-size: 0.9rem;
            font-weight: bold;
        }

        .phoneme-count {
            font-size: 0.85rem;
            color: #6b21a8;
            font-weight: 600;
            margin-bottom: 4px;
        }

        .rule-desc {
            font-size: 0.85rem;
            color: var(--text-muted);
            margin-top: 4px;
        }

        .cambridge-item {
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 1rem;
            margin-bottom: 1rem;
        }

        .cambridge-item:last-child {
            border-bottom: none;
            margin-bottom: 0;
            padding-bottom: 0;
        }

        .pos-tag {
            font-style: italic;
            color: #d97706;
            font-size: 0.9rem;
            font-weight: bold;
            margin-left: 6px;
        }

        .definition {
            font-size: 1rem;
            font-weight: 600;
            margin: 4px 0 8px;
            color: #1e293b;
        }

        .example-box {
            background: #f0fdf4;
            border-left: 4px solid var(--accent-green);
            padding: 0.6rem 0.8rem;
            border-radius: 0 6px 6px 0;
            font-size: 0.9rem;
        }

        .example-en {
            color: #14532d;
            font-weight: 600;
        }

        .example-zh {
            color: #374151;
            font-size: 0.85rem;
            margin-top: 2px;
        }

        .story-paragraph {
            background: #fafafa;
            border-radius: 8px;
            padding: 1.2rem;
            margin-bottom: 1.2rem;
            border: 1px solid #e2e8f0;
        }

        .story-paragraph.active-part {
            background-color: var(--highlight-bg);
            border-color: #fde047;
        }

        .story-en {
            font-size: 1.05rem;
            font-weight: 600;
            color: #1e3a8a;
            margin-bottom: 0.3rem;
        }

        .story-zh {
            font-size: 0.95rem;
            color: #334155;
            font-weight: 500;
            margin-bottom: 0.6rem;
        }

        .broadcast-explain {
            background: #f0f9ff;
            border-left: 4px solid #0284c7;
            padding: 0.8rem;
            border-radius: 0 6px 6px 0;
            font-size: 0.92rem;
            color: #0369a1;
            line-height: 1.7;
        }

        .btn-speak {
            background: none;
            border: none;
            color: var(--primary);
            cursor: pointer;
            font-size: 1rem;
            padding: 4px;
        }

        @media (max-width: 640px) {
            .input-group {
                flex-direction: column;
            }
            .player-controls {
                flex-direction: column;
                align-items: stretch;
            }
        }
    </style>
</head>
<body>

    <header>
        <h1>English Vocabulary Learning Hub</h1>
        <p>大家說英語廣播風格 • 5分鐘高效聽力實戰與單字拆解</p>
    </header>

    <div class="container">
        <!-- Control Panel -->
        <div class="control-panel">
            <div class="input-group">
                <input type="text" id="wordInput" value="safety, document, consolidation, plan, wire" placeholder="請輸入 5 個單字，用逗號或空格隔開">
                <button class="btn" onclick="processAndGenerate()"><i class="fa-solid fa-wand-magic-sparkles"></i> 立即生成教材</button>
            </div>

            <!-- Dual Button Master Player -->
            <div class="master-player">
                <div class="player-info">
                    <i class="fa-solid fa-radio fa-bounce" id="radioIcon" style="display:none;"></i>
                    <span id="playerStatus">請選擇要收聽的學習環節：</span>
                </div>
                <div class="player-controls">
                    <select class="speed-selector" id="speedSelect">
                        <option value="1.0" selected>1.0x 預設語速 (英0.82x / 中1.25x)</option>
                        <option value="0.8">0.8x 慢速聽力</option>
                        <option value="1.2">1.2x 快速複習</option>
                    </select>

                    <button class="btn btn-green" id="btnPlayCambridge" onclick="playCambridgeMode()">
                        <i class="fa-solid fa-book-open"></i> 1. 播放「繁體中文意思與造句」
                    </button>

                    <button class="btn btn-purple" id="btnPlayListening" onclick="playListeningMode()">
                        <i class="fa-solid fa-headphones"></i> 2. 播放「5分鐘廣播聽力實戰」
                    </button>

                    <button class="btn" style="background:#ef4444;" onclick="stopAudio()">
                        <i class="fa-solid fa-stop"></i> 停止
                    </button>
                </div>
            </div>
        </div>

        <!-- Content Area -->
        <div id="contentArea">
            <!-- 1. Phonemes Breakdown -->
            <div class="section-card" id="card-phonemes">
                <div class="section-title">
                    <i class="fa-solid fa-cubes"></i> 1. 單字發音拆解
                    <span class="source-tag">參考來源：Hanna et al. 音素拆解規則</span>
                </div>
                <div class="word-grid" id="phonemesContainer"></div>
            </div>

            <!-- 2. Cambridge Definitions -->
            <div class="section-card" id="card-cambridge">
                <div class="section-title">
                    <i class="fa-solid fa-book-open"></i> 2. 繁體中文意思與造句
                    <span class="source-tag">參考來源：劍橋辭典風格 (Cambridge Style)</span>
                </div>
                <div id="cambridgeContainer"></div>
            </div>

            <!-- 3. Radio Classroom Listening Story -->
            <div class="section-card" id="card-listening">
                <div class="section-title">
                    <i class="fa-solid fa-headphones"></i> 3. 5分鐘廣播聽力實戰故事與重點解說
                    <span class="source-tag">風格：《大家說英語》廣播雙語教學風格</span>
                </div>
                <p style="font-size:0.85rem; color:var(--text-muted); margin-bottom:1rem;">
                    💡 朗讀順序：小號高音提示音 ➔ 英文故事 ➔ 中文直譯朗讀 ➔ 雙語廣播深度解說，段落間自動安靜停頓 3 秒！
                </p>
                <div id="storyContainer"></div>
            </div>
        </div>
    </div>

    <script>
        // 單字知識庫
        const knowledgeBase = {
            "safety": { pos: "n.", zh: "安全，平安", exEn: "Safety is always our top priority at work.", exZh: "在工作場所中，安全永遠是我們最優先的事項。" },
            "document": { pos: "n.", zh: "文件，公文", exEn: "Please check the important document carefully.", exZh: "請仔細檢查這份重要的文件。" },
            "consolidation": { pos: "n.", zh: "整合，鞏固，聯合", exEn: "The consolidation of data makes our work easier.", exZh: "資料的整合使我們的工作變得更加容易。" },
            "plan": { pos: "n. / v.", zh: "計畫，方案", exEn: "We need a clear plan to complete this project.", exZh: "我們需要一個清晰的計畫來完成這個專案。" },
            "wire": { pos: "n.", zh: "電線，金屬線", exEn: "Be careful not to touch the loose wire.", exZh: "小心不要碰到鬆脫的電線。" }
        };

        // Hanna 音素數據
        const phonemeDb = {
            "safety": { list: ["/ s /", "/ eɪ /", "/ f /", "/ t /", "/ i /"], count: 5, rule: "開音節 a 發長音 /eɪ/，字尾 -ty 發 /ti/。" },
            "document": { list: ["/ d /", "/ ɑː /", "/ k /", "/ j /", "/ u /", "/ m /", "/ ə /", "/ n /", "/ t /"], count: 9, rule: "c 在 u 前發 /k/，-ment 為常見名詞字尾發 /mənt/。" },
            "consolidation": { list: ["/ k /", "/ ə /", "/ n /", "/ s /", "/ ɑː /", "/ l /", "/ ɪ /", "/ d /", "/ eɪ /", "/ ʃ /", "/ ə /", "/ n /"], count: 12, rule: "字尾 -tion 四個字母組合發 2 個音素 /ʃən/。" },
            "plan": { list: ["/ p /", "/ l /", "/ æ /", "/ n /"], count: 4, rule: "pl- 為雙輔音連讀 /pl/，閉音節 a 發短音 /æ/。" },
            "wire": { list: ["/ w /", "/ aɪ /", "/ ər /"], count: 3, rule: "i-e 相應發長音 /aɪ/，字尾 -re 結合發 /ər/。" }
        };

        let currentDataset = [];

        function analyzePhonemes(word) {
            const clean = word.toLowerCase().trim();
            if (phonemeDb[clean]) {
                return phonemeDb[clean];
            }
            let letters = clean.split('');
            return {
                list: letters.map(l => `/ ${l} /`),
                count: letters.length,
                rule: "符合自然拼讀與音素對應規則。"
            };
        }

        function getSmartData(word) {
            const clean = word.toLowerCase().trim();
            if (knowledgeBase[clean]) {
                return { word: clean, ...knowledgeBase[clean] };
            }
            return {
                word: clean,
                pos: "n. / v.",
                zh: `【常用單字】${clean} 的中文應用`,
                exEn: `It is very helpful to practice the word ${clean} in daily life.`,
                exZh: `在日常生活中練習「${clean}」這個單字非常有幫助。`
            };
        }

        function processAndGenerate() {
            const input = document.getElementById('wordInput').value.trim();
            if (!input) return;

            const words = input.split(/[, ]+/).filter(w => w.length > 0);
            currentDataset = words.map(w => getSmartData(w));

            renderAllSections();
        }

        function renderAllSections() {
            const phonemesContainer = document.getElementById('phonemesContainer');
            const cambridgeContainer = document.getElementById('cambridgeContainer');
            const storyContainer = document.getElementById('storyContainer');

            phonemesContainer.innerHTML = '';
            cambridgeContainer.innerHTML = '';
            storyContainer.innerHTML = '';

            currentDataset.forEach(item => {
                const hanna = analyzePhonemes(item.word);

                // 1. 極簡音素卡片
                phonemesContainer.innerHTML += `
                    <div class="word-item">
                        <div class="word-header">
                            <span class="word-title">${item.word}</span>
                            <button class="btn-speak" onclick="playSingle('${item.word}', 'en')"><i class="fa-solid fa-volume-high"></i></button>
                        </div>
                        <div class="phoneme-count">音素數量：${hanna.count} 個</div>
                        <div class="phoneme-container">
                            ${hanna.list.map(p => `<span class="phoneme-badge">${p}</span>`).join('')}
                        </div>
                        <div class="rule-desc">${hanna.rule}</div>
                    </div>
                `;

                // 2. 劍橋卡片
                cambridgeContainer.innerHTML += `
                    <div class="cambridge-item">
                        <div>
                            <strong style="font-size:1.1rem; color:var(--primary);">${item.word}</strong>
                            <span class="pos-tag">(${item.pos})</span>
                            <button class="btn-speak" onclick="playFullCambridge('${item.word}', '${item.zh}', '${item.exEn}', '${item.exZh}')"><i class="fa-solid fa-volume-high"></i></button>
                        </div>
                        <div class="definition">中文釋義：${item.zh}</div>
                        <div class="example-box">
                            <div class="example-en">例句：${item.exEn} <button class="btn-speak" onclick="playSingle('${item.exEn}', 'en')"><i class="fa-solid fa-volume-high"></i></button></div>
                            <div class="example-zh">翻譯：${item.exZh}</div>
                        </div>
                    </div>
                `;
            });

            // 3. 5分鐘聽力故事
            const w0 = currentDataset[0] ? currentDataset[0].word : "safety";
            const w1 = currentDataset[1] ? currentDataset[1].word : "document";
            const w2 = currentDataset[2] ? currentDataset[2].word : "consolidation";
            const w3 = currentDataset[3] ? currentDataset[3].word : "plan";
            const w4 = currentDataset[4] ? currentDataset[4].word : "wire";

            const storyParts = [
                {
                    en: `Sam is a smart engineer who always pays close attention to workplace ${w0}.`,
                    zh: `Sam 是一位聰明的工程師，他總是非常注意職場安全。`,
                    explain: `關鍵字 ${w0}，中文意思是 ${currentDataset[0]?.zh || '安全'}。故事使用了 pay close attention to 代表「密切注意...」。廣播老師延伸：在生活與工作場所中，Safety First 代表「安全第一」，這是最常見的安全標語喔！`
                },
                {
                    en: `Before starting his job, he reads every official ${w1} and checks the area for any dangerous loose ${w4}.`,
                    zh: `在開始工作前，他會閱讀每一份官方文件，並檢查工作區是否有任何危險的鬆脫電線。`,
                    explain: `關鍵字 ${w1}（${currentDataset[1]?.zh || '文件'}）與 ${w4}（${currentDataset[4]?.zh || '電線'}）。句中的 check for 代表「檢查是否有...」。老師小叮嚀：document 當名詞是指「文件」，若當動詞使用，則有「記錄/用文件證明」的意思喔！`
                },
                {
                    en: `Today, Sam needs to complete a comprehensive data ${w2} for his department.`,
                    zh: `今天，Sam 需要為他的部門完成一份全面的資料整合。`,
                    explain: `關鍵字 ${w2}，中文意思是 ${currentDataset[2]?.zh || '整合/鞏固'}。字根 consolidate 是動詞「整合」，加上字尾 -tion 就轉變成名詞 ${w2}！在職場中，資料整理與資源合併都可以使用這個字。`
                },
                {
                    en: `He carefully creates a step-by-step ${w3} to ensure all teams can work together smoothly and safely.`,
                    zh: `他仔細制定了一個循序漸進的計畫，以確保所有團隊都能順暢且安全地協同工作。`,
                    explain: `關鍵字 ${w3}，中文意思是 ${currentDataset[3]?.zh || '計畫'}。句中的 step-by-step 代表「按部就班的/一步步的」。廣播老師總結：有了周全的 ${w3}，不管多複雜的工作都能井然有序地完成！`
                }
            ];

            storyParts.forEach((part, index) => {
                storyContainer.innerHTML += `
                    <div class="story-paragraph" id="story-part-${index}">
                        <div class="story-en">${part.en} <button class="btn-speak" onclick="playSingle('${part.en}', 'en')"><i class="fa-solid fa-volume-high"></i></button></div>
                        <div class="story-zh">${part.zh} <button class="btn-speak" onclick="playSingle('${part.zh}', 'zh')"><i class="fa-solid fa-volume-high"></i></button></div>
                        <div class="broadcast-explain">
                            <strong>廣播雙語深度解說：</strong>${part.explain}
                        </div>
                    </div>
                `;
            });
        }

        // 語音與音效引擎
        const synth = window.speechSynthesis;
        let isPlaying = false;
        let masterQueue = [];
        let currentQueueIndex = 0;

        // 小號高音提示音「燈！燈！燈！」(Web Audio API)
        function playTrumpetJingle(onEndCallback) {
            try {
                const AudioCtx = window.AudioContext || window.webkitAudioContext;
                const ctx = new AudioCtx();
                
                const notes = [783.99, 987.77, 1174.66];
                let startTime = ctx.currentTime;

                notes.forEach((freq, index) => {
                    const osc = ctx.createOscillator();
                    const gain = ctx.createGain();

                    osc.type = 'triangle';
                    osc.frequency.setValueAtTime(freq, startTime + index * 0.22);

                    gain.gain.setValueAtTime(0.3, startTime + index * 0.22);
                    gain.gain.exponentialRampToValueAtTime(0.001, startTime + index * 0.22 + 0.35);

                    osc.connect(gain);
                    gain.connect(ctx.destination);

                    osc.start(startTime + index * 0.22);
                    osc.stop(startTime + index * 0.22 + 0.35);
                });

                setTimeout(() => {
                    if (onEndCallback) onEndCallback();
                }, 1000);

            } catch (e) {
                if (onEndCallback) onEndCallback();
            }
        }

        function playSingle(text, lang = 'en') {
            synth.cancel();
            const u = new SpeechSynthesisUtterance(text);
            const userSpeed = parseFloat(document.getElementById('speedSelect').value);
            
            if (lang === 'en') {
                u.lang = 'en-US';
                u.rate = userSpeed * 0.82;
            } else {
                u.lang = 'zh-TW';
                u.rate = userSpeed * 1.25;
            }
            synth.speak(u);
        }

        function playFullCambridge(word, zh, exEn, exZh, callback = null) {
            synth.cancel();
            const userSpeed = parseFloat(document.getElementById('speedSelect').value);

            const u1 = new SpeechSynthesisUtterance(word);
            u1.lang = 'en-US';
            u1.rate = userSpeed * 0.82;

            const u2 = new SpeechSynthesisUtterance(`中文意思是：${zh}`);
            u2.lang = 'zh-TW';
            u2.rate = userSpeed * 1.25;

            const u3 = new SpeechSynthesisUtterance(`Example: ${exEn}`);
            u3.lang = 'en-US';
            u3.rate = userSpeed * 0.82;

            const u4 = new SpeechSynthesisUtterance(`例句翻譯：${exZh}`);
            u4.lang = 'zh-TW';
            u4.rate = userSpeed * 1.25;

            u1.onend = () => synth.speak(u2);
            u2.onend = () => synth.speak(u3);
            u3.onend = () => synth.speak(u4);
            if (callback) {
                u4.onend = callback;
            }

            synth.speak(u1);
        }

        function stopAudio() {
            synth.cancel();
            isPlaying = false;
            document.getElementById('playerStatus').innerText = "廣播播放已停止";
            document.getElementById('radioIcon').style.display = "none";
            document.querySelectorAll('.section-card').forEach(c => c.classList.remove('speaking'));
            document.querySelectorAll('.story-paragraph').forEach(s => s.classList.remove('active-part'));
        }

        // 按鈕 1：播放「繁體中文意思與造句」（排除發音拆解）
        function playCambridgeMode() {
            stopAudio();
            isPlaying = true;
            document.getElementById('radioIcon').style.display = "inline-block";

            masterQueue = [];

            currentDataset.forEach(item => {
                masterQueue.push({
                    type: 'cambridge',
                    cardId: 'card-cambridge',
                    word: item.word,
                    zh: item.zh,
                    exEn: item.exEn,
                    exZh: item.exZh,
                    status: `正在講解單字與造句：${item.word}`
                });
            });

            currentQueueIndex = 0;
            processQueue();
        }

        // 按鈕 2：播放「5分鐘廣播聽力實戰」（含小號高音燈燈燈音效）
        function playListeningMode() {
            stopAudio();
            isPlaying = true;
            document.getElementById('radioIcon').style.display = "inline-block";
            document.getElementById('playerStatus').innerText = "【廣播片頭】小號高音提示音播放中...";

            playTrumpetJingle(() => {
                if (!isPlaying) return;

                masterQueue = [];

                const storyParts = document.querySelectorAll('.story-paragraph');
                storyParts.forEach((part, index) => {
                    const enText = part.querySelector('.story-en').innerText;
                    const zhText = part.querySelector('.story-zh').innerText;
                    const explainText = part.querySelector('.broadcast-explain').innerText.replace('廣播雙語深度解說：', '');

                    masterQueue.push({
                        type: 'story',
                        cardId: 'card-listening',
                        partId: `story-part-${index}`,
                        en: enText,
                        zh: zhText,
                        explain: explainText,
                        status: `收聽廣播聽力講堂第 ${index + 1} 段`
                    });
                });

                currentQueueIndex = 0;
                processQueue();
            });
        }

        function processQueue() {
            if (!isPlaying || currentQueueIndex >= masterQueue.length) {
                stopAudio();
                document.getElementById('playerStatus').innerText = "當前學習環節播放完畢！";
                return;
            }

            const item = masterQueue[currentQueueIndex];
            document.getElementById('playerStatus').innerText = item.status;

            document.querySelectorAll('.section-card').forEach(c => c.classList.remove('speaking'));
            document.querySelectorAll('.story-paragraph').forEach(s => s.classList.remove('active-part'));

            const card = document.getElementById(item.cardId);
            if (card) {
                card.classList.add('speaking');
                card.scrollIntoView({ behavior: 'smooth', block: 'center' });
            }

            if (item.partId) {
                const part = document.getElementById(item.partId);
                if (part) part.classList.add('active-part');
            }

            if (item.type === 'cambridge') {
                playFullCambridge(item.word, item.zh, item.exEn, item.exZh, () => {
                    if (isPlaying) { currentQueueIndex++; processQueue(); }
                });

            } else if (item.type === 'story') {
                const uEn = new SpeechSynthesisUtterance(item.en);
                uEn.lang = 'en-US';
                uEn.rate = parseFloat(document.getElementById('speedSelect').value) * 0.82;

                const uZh = new SpeechSynthesisUtterance(`中文意思是：${item.zh}`);
                uZh.lang = 'zh-TW';
                uZh.rate = parseFloat(document.getElementById('speedSelect').value) * 1.25;

                const uExplain = new SpeechSynthesisUtterance(`廣播老師解說：${item.explain}`);
                uExplain.lang = 'zh-TW';
                uExplain.rate = parseFloat(document.getElementById('speedSelect').value) * 1.25;

                uEn.onend = () => synth.speak(uZh);
                uZh.onend = () => synth.speak(uExplain);
                uExplain.onend = () => {
                    if (!isPlaying) return;
                    document.getElementById('playerStatus').innerText = "【安靜休息】大腦消化時間 (3秒)...";
                    setTimeout(() => {
                        if (isPlaying) {
                            currentQueueIndex++;
                            processQueue();
                        }
                    }, 3000);
                };

                synth.speak(uEn);
            }
        }

        // 初始化載入
        processAndGenerate();
    </script>
</body>
</html>
