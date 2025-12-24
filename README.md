[英語學習平台進階版.html](https://github.com/user-attachments/files/24330519/default.html)
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>英語學習平台 - B1→B2進階</title>
    <style>
        :root {
            --primary: #F5C197;
            --primary-hover: #E8B382;
            --success: #F0B8A8;
            --warning: #FDD9BE;
            --danger: #E8A88E;
            --bg: #FFFEF8;
            --surface: #F5E8D9;
            --text: #5C4A42;
            --text-light: #9A8B81;
            --border: #E0CDB9;
            --accent-light: #FFFEF8;
            --accent-warm: #F5E8D9;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background-color: var(--bg);
            color: var(--text);
            line-height: 1.6;
        }

        .header {
            background: linear-gradient(135deg, var(--primary), #E8B382);
            color: #5C4A42;
            padding: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 8px rgba(0,0,0,0.08);
        }

        .header-left {
            flex: 1;
            text-align: center;
        }

        .header h1 {
            font-size: 28px;
            margin-bottom: 8px;
        }

        .header p {
            font-size: 14px;
            opacity: 0.9;
        }

        .user-controls {
            display: flex;
            gap: 12px;
            align-items: center;
        }

        .current-user {
            background: rgba(255,255,255,0.3);
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: 500;
            font-size: 14px;
        }

        .user-btn {
            background: rgba(255,255,255,0.4);
            color: #5C4A42;
            border: none;
            padding: 8px 16px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 500;
            font-size: 14px;
            transition: background 0.3s ease;
        }

        .user-btn:hover {
            background: rgba(255,255,255,0.6);
        }

        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.4);
        }

        .modal.show {
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background-color: var(--surface);
            padding: 30px;
            border-radius: 12px;
            width: 90%;
            max-width: 400px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.2);
        }

        .modal-content h3 {
            color: var(--primary);
            margin-bottom: 20px;
            text-align: center;
        }

        .user-list {
            max-height: 300px;
            overflow-y: auto;
            margin-bottom: 20px;
        }

        .user-item {
            background: white;
            padding: 12px;
            margin-bottom: 10px;
            border-radius: 6px;
            cursor: pointer;
            border-left: 4px solid var(--primary);
            transition: background 0.3s ease;
        }

        .user-item:hover {
            background: #f5f5f5;
        }

        .user-item.active {
            background: #fffaeb;
            font-weight: 500;
        }

        .user-input {
            width: 100%;
            padding: 12px;
            border: 2px solid var(--border);
            border-radius: 6px;
            margin-bottom: 10px;
            font-size: 14px;
        }

        .modal-buttons {
            display: flex;
            gap: 10px;
        }

        .modal-buttons button {
            flex: 1;
            padding: 10px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 500;
            transition: background 0.3s ease;
        }

        .modal-close {
            background: var(--border);
            color: var(--text);
        }

        .modal-close:hover {
            background: #d0d0d0;
        }

        .modal-confirm {
            background: var(--primary);
            color: white;
        }

        .modal-confirm:hover {
            background: var(--primary-hover);
        }

        .stat-card {
            background: linear-gradient(135deg, #F5C197 0%, #E8B382 100%);
            color: #5C4A42;
            padding: 16px;
            border-radius: 8px;
            text-align: center;
        }

        .grammar-question {
            background: white;
            padding: 12px;
            border-radius: 6px;
            margin-bottom: 12px;
            border-left: 4px solid var(--primary);
        }

        .grammar-options {
            display: flex;
            flex-direction: column;
            gap: 8px;
            margin-bottom: 12px;
        }

        .option {
            background: #FFFEF8;
            padding: 12px;
            border-radius: 6px;
            cursor: pointer;
            border: 2px solid var(--border);
            transition: all 0.3s ease;
        }

        .option:hover {
            border-color: var(--primary);
            background: #fffaeb;
        }

        .option input[type="radio"] {
            margin-right: 8px;
        }

        .option.selected {
            border-color: var(--primary);
            background: var(--primary);
            color: white;
        }

        .grammar-explanation {
            background: #FFF5E6;
            padding: 12px;
            border-radius: 6px;
            border-left: 4px solid var(--warning);
            font-size: 13px;
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 20px auto;
            padding: 0 20px;
        }

        .section {
            background: var(--surface);
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.12), inset 0 1px 0 rgba(255,255,255,0.8);
            border: 1px solid var(--border);
        }

        .section h2 {
            font-size: 20px;
            margin-bottom: 16px;
            color: var(--primary);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            border-bottom: 2px solid var(--border);
            overflow-x: auto;
            padding-bottom: 10px;
        }

        .tab {
            padding: 12px 16px;
            cursor: pointer;
            border: none;
            background: none;
            font-size: 14px;
            font-weight: 500;
            color: var(--text-light);
            border-bottom: 3px solid transparent;
            transition: all 0.3s ease;
        }

        .tab.active {
            color: var(--primary);
            border-bottom-color: var(--primary);
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        .schedule-day {
            background: #FFFEF8;
            border-left: 5px solid var(--primary);
            padding: 12px;
            margin-bottom: 10px;
            border-radius: 6px;
            border-top: 1px solid var(--border);
            border-right: 1px solid var(--border);
            border-bottom: 1px solid var(--border);
        }

        .schedule-day h4 {
            color: var(--primary);
            margin-bottom: 6px;
        }

        .schedule-day p {
            font-size: 14px;
            color: var(--text-light);
            margin: 4px 0;
        }

        .study-blocks {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 16px;
            margin-bottom: 20px;
        }

        .block {
            background: linear-gradient(135deg, #F5C197 0%, #E8B382 100%);
            color: #5C4A42;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
        }

        .block.input {
            background: linear-gradient(135deg, #F5C197 0%, #E8B382 100%);
        }

        .block.output {
            background: linear-gradient(135deg, #EDB89F 0%, #E3A88B 100%);
        }

        .block.integration {
            background: linear-gradient(135deg, #FDD9BE 0%, #F5C9B0 100%);
        }

        .block h3 {
            font-size: 18px;
            margin-bottom: 8px;
        }

        .block-time {
            font-size: 28px;
            font-weight: bold;
            margin: 12px 0;
        }

        .block-desc {
            font-size: 13px;
            opacity: 0.95;
        }

        .writing-exercise {
            background: #FFFEF8;
            padding: 16px;
            border-radius: 8px;
            margin-bottom: 16px;
            border: 1px solid var(--border);
        }

        .writing-exercise h4 {
            color: var(--primary);
            margin-bottom: 8px;
        }

        .writing-exercise .example {
            background: white;
            padding: 10px;
            border-left: 3px solid var(--warning);
            margin: 8px 0;
            font-size: 13px;
            border-radius: 4px;
        }

        .writing-exercise .tips {
            background: #FFFEF8;
            padding: 10px;
            border-radius: 4px;
            font-size: 13px;
            color: #9A8B81;
            margin-top: 8px;
            border-left: 3px solid var(--primary);
        }

        textarea {
            width: 100%;
            padding: 12px;
            border: 2px solid var(--border);
            border-radius: 6px;
            font-family: 'Courier New', monospace;
            font-size: 14px;
            resize: vertical;
            min-height: 100px;
            margin-bottom: 10px;
        }

        textarea:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(33, 150, 243, 0.1);
        }

        .btn {
            background: var(--primary);
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 500;
            transition: background 0.3s ease;
        }

        .btn:hover {
            background: var(--primary-hover);
        }

        .btn-success {
            background: var(--success);
        }

        .btn-success:hover {
            background: #388E3C;
        }

        .feedback {
            margin-top: 12px;
            padding: 12px;
            border-radius: 6px;
            font-size: 13px;
        }

        .feedback.error {
            background: #FFE8DC;
            color: #E8A88E;
            border-left: 4px solid #E8A88E;
        }

        .feedback.success {
            background: #FFFAEB;
            color: #F0B8A8;
            border-left: 4px solid #F0B8A8;
        }

        .feedback.info {
            background: #FFF5E6;
            color: #9A8B81;
            border-left: 4px solid #9A8B81;
        }

        .progress-section {
            margin-top: 20px;
        }

        .progress-item {
            margin-bottom: 12px;
        }

        .progress-label {
            display: flex;
            justify-content: space-between;
            margin-bottom: 6px;
            font-size: 14px;
        }

        .progress-bar {
            width: 100%;
            height: 8px;
            background: var(--border);
            border-radius: 10px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background: var(--success);
            transition: width 0.3s ease;
            border-radius: 10px;
        }

        .vocabulary-card {
            background: #FFFEF8;
            padding: 12px;
            border-radius: 8px;
            margin-bottom: 10px;
            border-left: 5px solid var(--primary);
            border-top: 1px solid var(--border);
            border-right: 1px solid var(--border);
            border-bottom: 1px solid var(--border);
        }

        .vocabulary-card .word {
            font-weight: bold;
            color: var(--primary);
            font-size: 16px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .play-btn {
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 50%;
            width: 28px;
            height: 28px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 14px;
            transition: background 0.3s ease, transform 0.2s ease;
            flex-shrink: 0;
        }

        .play-btn:hover {
            background: var(--primary-hover);
            transform: scale(1.1);
        }

        .play-btn:active {
            transform: scale(0.95);
        }

        .play-btn.playing {
            background: var(--success);
            animation: pulse 0.6s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }

        .vocabulary-card .pronunciation {
            font-style: italic;
            color: var(--text-light);
            font-size: 13px;
        }

        .vocabulary-card .meaning {
            margin-top: 6px;
            color: var(--text);
        }

        .vocabulary-card .example {
            margin-top: 6px;
            color: var(--text-light);
            font-size: 13px;
            border-left: 2px solid var(--warning);
            padding-left: 8px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 12px;
            margin-bottom: 20px;
        }

        .stat-card {
            background: linear-gradient(135deg, #F5C197 0%, #E8B382 100%);
            color: #5C4A42;
            padding: 16px;
            border-radius: 8px;
            text-align: center;
        }

        .stat-number {
            font-size: 28px;
            font-weight: bold;
            margin-bottom: 4px;
        }

        .stat-label {
            font-size: 13px;
            opacity: 0.9;
        }

        @media (max-width: 768px) {
            .header h1 {
                font-size: 22px;
            }

            .study-blocks {
                grid-template-columns: 1fr;
            }

            .tabs {
                flex-wrap: wrap;
            }

            .stats-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>
<body>
    <div class="header">
        <div class="header-left">
            <h1>🎯 英語學習平台</h1>
            <p>B1→B2 進階課程 | 每日15分鐘集中學習</p>
        </div>
        <div class="user-controls">
            <div class="current-user" id="currentUserDisplay">👤 遊客</div>
            <button class="user-btn" onclick="openUserModal()">👥 切換用戶</button>
        </div>
    </div>

    <!-- 用戶管理模態框 -->
    <div id="userModal" class="modal">
        <div class="modal-content">
            <h3>👥 用戶管理</h3>
            <div class="user-list" id="userList"></div>
            <input type="text" id="newUserInput" class="user-input" placeholder="輸入新用戶名...">
            <div class="modal-buttons">
                <button class="modal-close" onclick="closeUserModal()">取消</button>
                <button class="modal-confirm" onclick="createNewUser()">新建用戶</button>
            </div>
        </div>
    </div>

    <div class="container">
        <!-- 統計面板 -->
        <div class="section">
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="stat-number" id="dayCount">0</div>
                    <div class="stat-label">學習天數</div>
                </div>
                <div class="stat-card" style="background: linear-gradient(135deg, #EDB89F 0%, #E3A88B 100%);">
                    <div class="stat-number" id="wordCount">0</div>
                    <div class="stat-label">新單字</div>
                </div>
                <div class="stat-card" style="background: linear-gradient(135deg, #FDD9BE 0%, #F5C9B0 100%);">
                    <div class="stat-number" id="writingCount">0</div>
                    <div class="stat-label">寫作篇數</div>
                </div>
                <div class="stat-card" style="background: linear-gradient(135deg, #F0B8A8 0%, #E8A88E 100%);">
                    <div class="stat-number" id="streak">0</div>
                    <div class="stat-label">連續天數</div>
                </div>
            </div>
        </div>

        <!-- 5-5-5 學習方法 -->
        <div class="section">
            <h2>⏱️ 每日5-5-5學習方法</h2>
            <div class="study-blocks">
                <div class="block input">
                    <h3>📻 Block 1: 聽力輸入</h3>
                    <div class="block-time">5 分鐘</div>
                    <div class="block-desc">
                        播放英文對話、TED演講或新聞片段
                        <br><small>提升聽力理解能力</small>
                    </div>
                </div>
                <div class="block output">
                    <h3>🎤 Block 2: 口說輸出</h3>
                    <div class="block-time">5 分鐘</div>
                    <div class="block-desc">
                        跟讀、自由演講或對話練習
                        <br><small>培養口說流暢度</small>
                    </div>
                </div>
                <div class="block integration">
                    <h3>✍️ Block 3: 寫作整合</h3>
                    <div class="block-time">5 分鐘</div>
                    <div class="block-desc">
                        微寫作練習、句子組織
                        <br><small>強化寫作表達能力</small>
                    </div>
                </div>
            </div>
        </div>

        <!-- 每週學習計劃 -->
        <div class="section">
            <h2>📅 每週學習主題計劃</h2>
            <div id="scheduleContent"></div>
        </div>

        <!-- 文法學習核心 -->
        <div class="section">
            <h2>📖 B2 進階文法學習</h2>
            
            <div class="tabs">
                <button class="tab active" onclick="switchGrammarTab(0)">現在完成式 vs 過去完成式</button>
                <button class="tab" onclick="switchGrammarTab(1)">虛擬語氣 (If Clauses)</button>
                <button class="tab" onclick="switchGrammarTab(2)">被動語態進階</button>
                <button class="tab" onclick="switchGrammarTab(3)">複雜句型結構</button>
                <button class="tab" onclick="switchGrammarTab(4)">時態綜合應用</button>
            </div>

            <!-- 現在完成式 vs 過去完成式 -->
            <div class="tab-content active">
                <div class="writing-exercise">
                    <h4>📖 現在完成式 vs 過去完成式</h4>
                    <div class="grammar-explanation">
                        <strong>現在完成式 (Present Perfect):</strong> 用於描述從過去到現在仍有影響的行為。<br>
                        <strong>過去完成式 (Past Perfect):</strong> 用於描述比另一個過去事件更早發生的行為。<br><br>
                        例句：<br>
                        • I <strong>have lived</strong> here for 5 years. (我住在這裡5年了，現在仍住在這裡)<br>
                        • I <strong>had lived</strong> here for 5 years when I moved. (我搬家前住了5年)
                    </div>
                    <div id="grammarQuiz0"></div>
                </div>
            </div>

            <!-- 虛擬語氣 -->
            <div class="tab-content">
                <div class="writing-exercise">
                    <h4>📖 虛擬語氣 (Conditional Sentences)</h4>
                    <div class="grammar-explanation">
                        <strong>第一類條件句 (Real):</strong> If + Present, will + V<br>
                        <strong>第二類條件句 (Hypothetical):</strong> If + Past, would + V<br>
                        <strong>第三類條件句 (Impossible):</strong> If + Past Perfect, would have + V<br><br>
                        例句：<br>
                        • If you study hard, you will pass the exam.<br>
                        • If you studied hard, you would pass the exam.<br>
                        • If you had studied hard, you would have passed the exam.
                    </div>
                    <div id="grammarQuiz1"></div>
                </div>
            </div>

            <!-- 被動語態 -->
            <div class="tab-content">
                <div class="writing-exercise">
                    <h4>📖 被動語態進階用法</h4>
                    <div class="grammar-explanation">
                        <strong>基本被動語態:</strong> am/is/are + past participle<br>
                        <strong>進階被動語態:</strong> 可用於所有時態和模態動詞<br><br>
                        例句：<br>
                        • The project <strong>is being managed</strong> by the team.<br>
                        • The report <strong>should have been submitted</strong> yesterday.<br>
                        • The document <strong>is said to be</strong> important.
                    </div>
                    <div id="grammarQuiz2"></div>
                </div>
            </div>

            <!-- 複雜句型 -->
            <div class="tab-content">
                <div class="writing-exercise">
                    <h4>📖 複雜句型結構</h4>
                    <div class="grammar-explanation">
                        <strong>名詞子句:</strong> That + 子句<br>
                        <strong>形容詞子句:</strong> 用 which, who, that 引導<br>
                        <strong>副詞子句:</strong> 用 because, although, when, if 等引導<br><br>
                        例句：<br>
                        • <strong>That she succeeded</strong> surprised everyone.<br>
                        • The book <strong>which I read</strong> was fascinating.<br>
                        • <strong>Although it was raining</strong>, we went out.
                    </div>
                    <div id="grammarQuiz3"></div>
                </div>
            </div>

            <!-- 時態綜合 -->
            <div class="tab-content">
                <div class="writing-exercise">
                    <h4>📖 時態綜合應用</h4>
                    <div class="grammar-explanation">
                        在實際使用中，多個時態可能在同一句子中出現。<br><br>
                        例句：<br>
                        • When I <strong>arrived</strong>, she <strong>was cooking</strong>.<br>
                        • I <strong>have lived</strong> here since I <strong>was</strong> born.<br>
                        • By the time he <strong>retires</strong>, he <strong>will have worked</strong> for 40 years.
                    </div>
                    <div id="grammarQuiz4"></div>
                </div>
            </div>
        </div>

        <!-- 寫作練習核心 -->
        <div class="section">
            <h2>✍️ 寫作練習工作區</h2>
            
            <div class="tabs">
                <button class="tab active" onclick="switchWritingTab(0)">級別1：句子組合</button>
                <button class="tab" onclick="switchWritingTab(1)">級別2：段落寫作</button>
                <button class="tab" onclick="switchWritingTab(2)">級別3：短文創作</button>
            </div>

            <!-- 級別1 -->
            <div class="tab-content active">
                <div class="writing-exercise">
                    <h4>📝 句子組合練習</h4>
                    <p style="color: var(--text-light); font-size: 14px; margin-bottom: 10px;">將兩個簡單句子用連接詞組合成複雜句</p>
                    
                    <div id="exercise1" style="background: white; padding: 12px; border-radius: 6px; margin-bottom: 12px;">
                        <p><strong>題目：</strong> <span id="ex1Question"></span></p>
                        <p style="margin-top: 10px;"><strong>提示：</strong> <span id="ex1Hint" style="color: var(--primary);"></span></p>
                    </div>

                    <textarea id="answer1" placeholder="在此輸入你的答案..."></textarea>
                    
                    <button class="btn" onclick="checkLevel1()">提交檢查</button>
                    <div id="feedback1"></div>

                    <div class="tips">
                        💡 提示：使用 because, although, when, if, unless 等連接詞
                    </div>
                </div>
            </div>

            <!-- 級別2 -->
            <div class="tab-content">
                <div class="writing-exercise">
                    <h4>📝 段落寫作練習</h4>
                    <p style="color: var(--text-light); font-size: 14px; margin-bottom: 10px;">根據關鍵詞寫出一個3-5句的段落</p>
                    
                    <div id="exercise2" style="background: white; padding: 12px; border-radius: 6px; margin-bottom: 12px;">
                        <p><strong>主題：</strong> <span id="ex2Topic"></span></p>
                        <p style="margin-top: 10px;"><strong>關鍵詞：</strong> <span id="ex2Keywords" style="color: var(--primary);"></span></p>
                    </div>

                    <textarea id="answer2" placeholder="在此輸入你的答案..."></textarea>
                    
                    <button class="btn" onclick="checkLevel2()">提交檢查</button>
                    <div id="feedback2"></div>

                    <div class="tips">
                        💡 提示：每個段落應該有主題句和支持句。確保使用多樣的句子結構。
                    </div>
                </div>
            </div>

            <!-- 級別3 -->
            <div class="tab-content">
                <div class="writing-exercise">
                    <h4>📝 短文創作練習</h4>
                    <p style="color: var(--text-light); font-size: 14px; margin-bottom: 10px;">根據主題寫出一篇150-200字的短文</p>
                    
                    <div id="exercise3" style="background: white; padding: 12px; border-radius: 6px; margin-bottom: 12px;">
                        <p><strong>寫作主題：</strong> <span id="ex3Topic"></span></p>
                    </div>

                    <textarea id="answer3" placeholder="在此輸入你的答案..."></textarea>
                    <div style="font-size: 13px; color: var(--text-light); margin-bottom: 10px;">字數：<span id="wordCounter">0</span>/150-200</div>
                    
                    <button class="btn" onclick="checkLevel3()">提交檢查</button>
                    <div id="feedback3"></div>

                    <div class="tips">
                        💡 提示：包含引入、主體和結論。使用過渡詞(however, furthermore, in conclusion)增加文章連貫性。
                    </div>
                </div>
            </div>
        </div>

        <!-- 詞彙學習 -->
        <div class="section">
            <h2>📚 B2 進階詞彙學習</h2>
            <div id="vocabularyList"></div>
        </div>

        <!-- 進度追蹤 -->
        <div class="section">
            <h2>📊 學習進度</h2>
            <div class="progress-section">
                <div class="progress-item">
                    <div class="progress-label">
                        <span>聽力理解 (Listening)</span>
                        <span id="listeningPct">65%</span>
                    </div>
                    <div class="progress-bar">
                        <div class="progress-fill" style="width: 65%; background: #2196F3;"></div>
                    </div>
                </div>
                <div class="progress-item">
                    <div class="progress-label">
                        <span>口說流暢 (Speaking)</span>
                        <span id="speakingPct">60%</span>
                    </div>
                    <div class="progress-bar">
                        <div class="progress-fill" style="width: 60%; background: #4CAF50;"></div>
                    </div>
                </div>
                <div class="progress-item">
                    <div class="progress-label">
                        <span>閱讀理解 (Reading)</span>
                        <span id="readingPct">70%</span>
                    </div>
                    <div class="progress-bar">
                        <div class="progress-fill" style="width: 70%; background: #FF9800;"></div>
                    </div>
                </div>
                <div class="progress-item">
                    <div class="progress-label">
                        <span>寫作能力 (Writing)</span>
                        <span id="writingPct">55%</span>
                    </div>
                    <div class="progress-bar">
                        <div class="progress-fill" style="width: 55%; background: #F44336;"></div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // 學習數據
        const scheduleData = [
            { day: '🌙 星期一', theme: '商務英文', focus: 'Email寫作、會議用語', keywords: 'proposal, agenda, deadline' },
            { day: '🌙 星期二', theme: '日常生活', focus: '日常對話、購物、餐廳', keywords: 'I\'d like, could you, absolutely' },
            { day: '📖 星期三', theme: '閱讀日', focus: '新聞文章、部落格', keywords: '複雜句子、長篇文章' },
            { day: '✍️ 星期四', theme: '寫作日', focus: '短文、段落、論文', keywords: '段落結構、銜接詞' },
            { day: '🎤 星期五', theme: '口說練習', focus: '演講、討論、辯論', keywords: 'argue, emphasize, persuade' },
            { day: '🎯 星期六', theme: '綜合複習', focus: '混合技能練習', keywords: '複習所有技能' },
            { day: '📊 星期日', theme: '評估測試', focus: '週測驗、進度評估', keywords: '進度檢測' }
        ];

        const vocabularyData = [
            { word: 'proficiency', pronunciation: '/prəˈfɪʃənsi/', meaning: '熟練度、精通', example: 'Language proficiency is essential for international business.' },
            { word: 'coherent', pronunciation: '/koʊˈhɪrənt/', meaning: '連貫的、清晰的', example: 'Your essay should have a coherent structure.' },
            { word: 'elaborate', pronunciation: '/ɪˈlæbərət/', meaning: '詳細說明、詳細的', example: 'Can you elaborate on your previous point?' },
            { word: 'concise', pronunciation: '/kənˈsaɪs/', meaning: '簡明的、簡潔的', example: 'Write a concise summary of the article.' },
            { word: 'nuance', pronunciation: '/ˈnuːɑːns/', meaning: '細微差別、細節', example: 'B2 learners should understand the nuances of English grammar.' },
            { word: 'pragmatic', pronunciation: '/præɡˈmætɪk/', meaning: '實用主義的、實際的', example: 'Take a pragmatic approach to language learning.' }
        ];

        const writingExercises = [
            {
                level: 1,
                question: 'Combine: "She finished her homework. She went to play." Answer should use a conjunction.',
                hint: 'Use "after" or "before"',
                goodAnswer: ['After she finished her homework, she went to play.', 'Once she completed her homework, she went to play.'],
                feedback: 'Great! You successfully combined two simple sentences using a conjunction. This shows B2-level sentence structure.'
            },
            {
                level: 2,
                topic: 'My favorite hobby',
                keywords: 'enjoy, practice, improve, passion',
                instruction: 'Write 3-5 sentences about your favorite hobby',
                feedback: 'Good paragraph structure! Make sure each sentence contributes to the main idea.'
            },
            {
                level: 3,
                topic: 'The importance of learning English in the digital age',
                instruction: 'Write 150-200 words about how English helps in modern world',
                feedback: 'Excellent! Your essay demonstrates B2-level coherence and complexity.'
            }
        ];

        // 初始化
        function initApp() {
            loadSchedule();
            loadVocabulary();
            loadWritingExercises();
            updateStats();
            addWordCounter();
        }

        function loadSchedule() {
            const container = document.getElementById('scheduleContent');
            container.innerHTML = scheduleData.map(item => `
                <div class="schedule-day">
                    <h4>${item.day}: ${item.theme}</h4>
                    <p><strong>學習重點：</strong> ${item.focus}</p>
                    <p><strong>核心詞彙：</strong> ${item.keywords}</p>
                </div>
            `).join('');
        }

        function loadVocabulary() {
            const container = document.getElementById('vocabularyList');
            container.innerHTML = vocabularyData.map((item, index) => `
                <div class="vocabulary-card">
                    <div class="word">
                        ${item.word}
                        <button class="play-btn" onclick="pronounceWord(${index})" title="播放發音">🔊</button>
                    </div>
                    <div class="pronunciation">${item.pronunciation}</div>
                    <div class="meaning">💡 ${item.meaning}</div>
                    <div class="example">例句：${item.example}</div>
                </div>
            `).join('');
        }

        function loadWritingExercises() {
            // Level 1
            document.getElementById('ex1Question').textContent = writingExercises[0].question;
            document.getElementById('ex1Hint').textContent = writingExercises[0].hint;

            // Level 2
            document.getElementById('ex2Topic').textContent = writingExercises[1].topic;
            document.getElementById('ex2Keywords').textContent = writingExercises[1].keywords;

            // Level 3
            document.getElementById('ex3Topic').textContent = writingExercises[2].topic;
        }

        function switchWritingTab(index) {
            const tabs = document.querySelectorAll('.tab');
            const contents = document.querySelectorAll('.tab-content');
            
            tabs.forEach(tab => tab.classList.remove('active'));
            contents.forEach(content => content.classList.remove('active'));
            
            tabs[index].classList.add('active');
            contents[index].classList.add('active');
        }

        function checkLevel1() {
            const answer = document.getElementById('answer1').value.trim();
            const feedback = document.getElementById('feedback1');
            
            if (!answer) {
                feedback.innerHTML = '<div class="feedback error">❌ 請輸入答案</div>';
                return;
            }

            const hasConnector = ['after', 'before', 'when', 'because', 'although', 'while', 'since'].some(word => answer.toLowerCase().includes(word));
            
            if (hasConnector && answer.length > 30) {
                feedback.innerHTML = `<div class="feedback success">✅ 很好！你成功組合了句子。這是B2級別的句子結構。</div>`;
                incrementStats('wordCount');
                incrementStats('writingCount');
            } else {
                feedback.innerHTML = `<div class="feedback info">💡 試著使用連接詞(because, after, when, although等)來組合句子。</div>`;
            }
        }

        function checkLevel2() {
            const answer = document.getElementById('answer2').value.trim();
            const feedback = document.getElementById('feedback2');
            const sentences = answer.split('.').filter(s => s.trim());
            
            if (!answer) {
                feedback.innerHTML = '<div class="feedback error">❌ 請輸入答案</div>';
                return;
            }

            if (sentences.length >= 3 && sentences.length <= 6 && answer.length > 60) {
                feedback.innerHTML = `<div class="feedback success">✅ 優秀！你寫出了一個結構良好的段落。包含主題句和支持句。</div>`;
                incrementStats('writingCount');
            } else {
                feedback.innerHTML = `<div class="feedback info">💡 一個好段落應該有3-5個句子，並且圍繞一個主題展開。</div>`;
            }
        }

        function checkLevel3() {
            const answer = document.getElementById('answer3').value.trim();
            const feedback = document.getElementById('feedback3');
            const words = answer.split(/\s+/).length;
            
            if (!answer) {
                feedback.innerHTML = '<div class="feedback error">❌ 請輸入答案</div>';
                return;
            }

            if (words >= 150 && words <= 200) {
                feedback.innerHTML = `<div class="feedback success">✅ 完美！你寫出了一篇${words}字的短文，符合B2級別要求。</div>`;
                incrementStats('writingCount');
            } else if (words > 100) {
                feedback.innerHTML = `<div class="feedback info">💡 你的短文有${words}字。B2級別目標是150-200字。試著加入更多細節和例子。</div>`;
            } else {
                feedback.innerHTML = `<div class="feedback info">💡 你的短文只有${words}字。請補充到150-200字。</div>`;
            }
        }

        function addWordCounter() {
            const textarea = document.getElementById('answer3');
            textarea.addEventListener('input', () => {
                const words = textarea.value.split(/\s+/).filter(w => w.length > 0).length;
                document.getElementById('wordCounter').textContent = words;
            });
        }

        function pronounceWord(index) {
            const item = vocabularyData[index];
            const utterance = new SpeechSynthesisUtterance(item.word);
            utterance.lang = 'en-US';
            utterance.rate = 0.9;
            utterance.pitch = 1;
            
            const btn = event.target;
            btn.classList.add('playing');
            
            utterance.onend = () => {
                btn.classList.remove('playing');
            };
            
            speechSynthesis.cancel();
            speechSynthesis.speak(utterance);
        }

        function updateStats() {
            const saved = localStorage.getItem('englishStats');
            if (saved) {
                const stats = JSON.parse(saved);
                document.getElementById('dayCount').textContent = stats.dayCount || 0;
                document.getElementById('wordCount').textContent = stats.wordCount || 0;
                document.getElementById('writingCount').textContent = stats.writingCount || 0;
                document.getElementById('streak').textContent = stats.streak || 0;
            } else {
                document.getElementById('dayCount').textContent = 0;
                document.getElementById('wordCount').textContent = 0;
                document.getElementById('writingCount').textContent = 0;
                document.getElementById('streak').textContent = 0;
            }
        }

        function incrementStats(key) {
            let stats = {};
            const saved = localStorage.getItem('englishStats');
            
            if (saved) {
                stats = JSON.parse(saved);
            }
            
            stats[key] = (stats[key] || 0) + 1;
            localStorage.setItem('englishStats', JSON.stringify(stats));
            updateStats();
        }

        // 文法數據
        const grammarData = [
            {
                topic: '現在完成式 vs 過去完成式',
                questions: [
                    {
                        question: 'I _____ in this city for 10 years.',
                        options: ['lived', 'have lived', 'had lived', 'was living'],
                        correct: 1,
                        explanation: '現在完成式表示從過去到現在的持續狀態。'
                    },
                    {
                        question: 'Before he arrived, they _____ the meeting.',
                        options: ['started', 'have started', 'had started', 'were starting'],
                        correct: 2,
                        explanation: '過去完成式表示在另一個過去動作之前發生的事。'
                    }
                ]
            },
            {
                topic: '虛擬語氣',
                questions: [
                    {
                        question: 'If I _____ you, I would accept the offer.',
                        options: ['was', 'were', 'am', 'had been'],
                        correct: 1,
                        explanation: '虛擬語氣中使用 were，即使主語是單數。'
                    },
                    {
                        question: 'If you _____ harder, you would have passed.',
                        options: ['studied', 'had studied', 'study', 'would study'],
                        correct: 1,
                        explanation: '第三類條件句用過去完成式。'
                    }
                ]
            },
            {
                topic: '被動語態',
                questions: [
                    {
                        question: 'The project _____ by the team next week.',
                        options: ['is completed', 'will be completed', 'was completed', 'has been completed'],
                        correct: 1,
                        explanation: '未來時被動語態使用 will be + past participle。'
                    },
                    {
                        question: 'The report _____ yesterday.',
                        options: ['should submit', 'should be submitted', 'should submitted', 'submit'],
                        correct: 1,
                        explanation: '情態動詞 + be + past participle。'
                    }
                ]
            },
            {
                topic: '複雜句型',
                questions: [
                    {
                        question: '_____ he would come was uncertain.',
                        options: ['That', 'Which', 'Who', 'What'],
                        correct: 0,
                        explanation: '名詞子句需要用 that 引導。'
                    },
                    {
                        question: 'The book _____ I borrowed is excellent.',
                        options: ['who', 'that', 'which', 'where'],
                        correct: 1,
                        explanation: '形容詞子句修飾名詞，用 that 或 which。'
                    }
                ]
            },
            {
                topic: '時態綜合',
                questions: [
                    {
                        question: 'When I _____, she _____ cooking.',
                        options: ['arrive, was cooking', 'arrived, was cooking', 'arrived, is cooking', 'will arrive, was cooking'],
                        correct: 1,
                        explanation: '過去時和過去進行式一起使用，表示一個動作發生時另一個動作正在進行。'
                    },
                    {
                        question: 'By next year, I _____ here for 20 years.',
                        options: ['will work', 'will have worked', 'have worked', 'am working'],
                        correct: 1,
                        explanation: '未來完成式用於表示到未來某個時間點已完成的動作。'
                    }
                ]
            }
        ];

        // 用戶管理變數
        let currentUser = null;
        let allUsers = [];

        // 初始化用戶系統
        function initUserSystem() {
            const savedUsers = localStorage.getItem('allEnglishUsers');
            if (savedUsers) {
                allUsers = JSON.parse(savedUsers);
                const lastUser = localStorage.getItem('lastEnglishUser');
                if (lastUser && allUsers.includes(lastUser)) {
                    currentUser = lastUser;
                }
            }
            if (!currentUser && allUsers.length > 0) {
                currentUser = allUsers[0];
            }
            updateUserDisplay();
        }

        function updateUserDisplay() {
            document.getElementById('currentUserDisplay').textContent = currentUser ? `👤 ${currentUser}` : '👤 遊客';
            if (currentUser) {
                localStorage.setItem('lastEnglishUser', currentUser);
            }
        }

        function getStorageKey(key) {
            return currentUser ? `${currentUser}_${key}` : key;
        }

        function openUserModal() {
            document.getElementById('userModal').classList.add('show');
            renderUserList();
        }

        function closeUserModal() {
            document.getElementById('userModal').classList.remove('show');
        }

        function renderUserList() {
            const userList = document.getElementById('userList');
            userList.innerHTML = allUsers.map(user => `
                <div class="user-item ${user === currentUser ? 'active' : ''}" onclick="switchUser('${user}')">
                    👤 ${user}
                </div>
            `).join('');
        }

        function switchUser(userName) {
            currentUser = userName;
            updateUserDisplay();
            updateStats();
            loadVocabulary();
            loadWritingExercises();
            loadGrammarQuizzes();
            closeUserModal();
        }

        function createNewUser() {
            const input = document.getElementById('newUserInput');
            const userName = input.value.trim();
            if (userName && !allUsers.includes(userName)) {
                allUsers.push(userName);
                localStorage.setItem('allEnglishUsers', JSON.stringify(allUsers));
                switchUser(userName);
                input.value = '';
            }
        }

        // 文法測驗初始化
        function loadGrammarQuizzes() {
            grammarData.forEach((topic, index) => {
                const container = document.getElementById(`grammarQuiz${index}`);
                if (container) {
                    const question = topic.questions[Math.floor(Math.random() * topic.questions.length)];
                    container.innerHTML = `
                        <div class="grammar-question">
                            <p style="margin-bottom: 12px;"><strong>題目：</strong> ${question.question}</p>
                            <div class="grammar-options" id="options${index}">
                                ${question.options.map((opt, i) => `
                                    <label class="option">
                                        <input type="radio" name="grammar${index}" value="${i}" onchange="checkGrammar(${index}, ${i}, ${question.correct}, '${question.explanation}')">
                                        ${opt}
                                    </label>
                                `).join('')}
                            </div>
                            <div id="grammarFeedback${index}"></div>
                        </div>
                    `;
                }
            });
        }

        function checkGrammar(quizIndex, selectedIndex, correctIndex, explanation) {
            const feedback = document.getElementById(`grammarFeedback${quizIndex}`);
            if (selectedIndex === correctIndex) {
                feedback.innerHTML = `<div class="feedback success">✅ 正確！${explanation}</div>`;
                incrementStats('grammarScore');
            } else {
                feedback.innerHTML = `<div class="feedback info">💡 ${explanation}</div>`;
            }
        }

        // 頁面載入時初始化
        function initApp() {
            initUserSystem();
            loadSchedule();
            loadVocabulary();
            loadWritingExercises();
            loadGrammarQuizzes();
            updateStats();
            addWordCounter();
            performDailyCheckIn();
        }

        // 每日打卡系統
        function performDailyCheckIn() {
            const today = new Date().toDateString();
            const lastCheckIn = localStorage.getItem(getStorageKey('lastCheckIn'));
            
            if (lastCheckIn !== today) {
                localStorage.setItem(getStorageKey('lastCheckIn'), today);
                let stats = JSON.parse(localStorage.getItem(getStorageKey('englishStats')) || '{}');
                stats.dayCount = (stats.dayCount || 0) + 1;
                
                const lastStreak = localStorage.getItem(getStorageKey('lastStreakDate'));
                const yesterday = new Date();
                yesterday.setDate(yesterday.getDate() - 1);
                
                if (lastStreak === yesterday.toDateString()) {
                    stats.streak = (stats.streak || 0) + 1;
                } else {
                    stats.streak = 1;
                }
                
                localStorage.setItem(getStorageKey('lastStreakDate'), today);
                localStorage.setItem(getStorageKey('englishStats'), JSON.stringify(stats));
            }
        }

        // 每日自動重置練習
        function performDailyReset() {
            const today = new Date().toDateString();
            const lastReset = localStorage.getItem(getStorageKey('lastPracticeReset'));
            
            if (lastReset !== today) {
                localStorage.setItem(getStorageKey('lastPracticeReset'), today);
                document.getElementById('answer1').value = '';
                document.getElementById('answer2').value = '';
                document.getElementById('answer3').value = '';
            }
        }

        function updateStats() {
            const saved = localStorage.getItem(getStorageKey('englishStats'));
            if (saved) {
                const stats = JSON.parse(saved);
                document.getElementById('dayCount').textContent = stats.dayCount || 0;
                document.getElementById('wordCount').textContent = stats.wordCount || 0;
                document.getElementById('writingCount').textContent = stats.writingCount || 0;
                document.getElementById('streak').textContent = stats.streak || 0;
            } else {
                document.getElementById('dayCount').textContent = 0;
                document.getElementById('wordCount').textContent = 0;
                document.getElementById('writingCount').textContent = 0;
                document.getElementById('streak').textContent = 0;
            }
        }

        function incrementStats(key) {
            let stats = {};
            const saved = localStorage.getItem(getStorageKey('englishStats'));
            
            if (saved) {
                stats = JSON.parse(saved);
            }
            
            stats[key] = (stats[key] || 0) + 1;
            localStorage.setItem(getStorageKey('englishStats'), JSON.stringify(stats));
            updateStats();
        }

        function switchGrammarTab(index) {
            const tabs = document.querySelectorAll('.tabs')[1].querySelectorAll('.tab');
            const contents = Array.from(document.querySelectorAll('.tab-content')).slice(0, 5);
            
            tabs.forEach(tab => tab.classList.remove('active'));
            contents.forEach(content => content.classList.remove('active'));
            
            tabs[index].classList.add('active');
            contents[index].classList.add('active');
        }

        function switchWritingTab(index) {
            const tabs = document.querySelectorAll('.tabs')[2].querySelectorAll('.tab');
            const contents = Array.from(document.querySelectorAll('.tab-content')).slice(5);
            
            tabs.forEach(tab => tab.classList.remove('active'));
            contents.forEach(content => content.classList.remove('active'));
            
            tabs[index].classList.add('active');
            contents[index].classList.add('active');
        }

        function checkLevel1() {
            const answer = document.getElementById('answer1').value.trim();
            const feedback = document.getElementById('feedback1');
            
            if (!answer) {
                feedback.innerHTML = '<div class="feedback error">❌ 請輸入答案</div>';
                return;
            }

            const hasConnector = ['after', 'before', 'when', 'because', 'although', 'while', 'since'].some(word => answer.toLowerCase().includes(word));
            
            if (hasConnector && answer.length > 30) {
                feedback.innerHTML = `<div class="feedback success">✅ 很好！你成功組合了句子。這是B2級別的句子結構。</div>`;
                incrementStats('wordCount');
                incrementStats('writingCount');
            } else {
                feedback.innerHTML = `<div class="feedback info">💡 試著使用連接詞(because, after, when, although等)來組合句子。</div>`;
            }
        }

        function checkLevel2() {
            const answer = document.getElementById('answer2').value.trim();
            const feedback = document.getElementById('feedback2');
            const sentences = answer.split('.').filter(s => s.trim());
            
            if (!answer) {
                feedback.innerHTML = '<div class="feedback error">❌ 請輸入答案</div>';
                return;
            }

            if (sentences.length >= 3 && sentences.length <= 6 && answer.length > 60) {
                feedback.innerHTML = `<div class="feedback success">✅ 優秀！你寫出了一個結構良好的段落。包含主題句和支持句。</div>`;
                incrementStats('writingCount');
            } else {
                feedback.innerHTML = `<div class="feedback info">💡 一個好段落應該有3-5個句子，並且圍繞一個主題展開。</div>`;
            }
        }

        function checkLevel3() {
            const answer = document.getElementById('answer3').value.trim();
            const feedback = document.getElementById('feedback3');
            const words = answer.split(/\s+/).length;
            
            if (!answer) {
                feedback.innerHTML = '<div class="feedback error">❌ 請輸入答案</div>';
                return;
            }

            if (words >= 150 && words <= 200) {
                feedback.innerHTML = `<div class="feedback success">✅ 完美！你寫出了一篇${words}字的短文，符合B2級別要求。</div>`;
                incrementStats('writingCount');
            } else if (words > 100) {
                feedback.innerHTML = `<div class="feedback info">💡 你的短文有${words}字。B2級別目標是150-200字。試著加入更多細節和例子。</div>`;
            } else {
                feedback.innerHTML = `<div class="feedback info">💡 你的短文只有${words}字。請補充到150-200字。</div>`;
            }
        }

        function addWordCounter() {
            const textarea = document.getElementById('answer3');
            if (textarea) {
                textarea.addEventListener('input', () => {
                    const words = textarea.value.split(/\s+/).filter(w => w.length > 0).length;
                    document.getElementById('wordCounter').textContent = words;
                });
            }
        }

        function pronounceWord(index) {
            const item = vocabularyData[index];
            const utterance = new SpeechSynthesisUtterance(item.word);
            utterance.lang = 'en-US';
            utterance.rate = 0.9;
            utterance.pitch = 1;
            
            const btn = event.target;
            btn.classList.add('playing');
            
            utterance.onend = () => {
                btn.classList.remove('playing');
            };
            
            speechSynthesis.cancel();
            speechSynthesis.speak(utterance);
        }

        function loadSchedule() {
            const container = document.getElementById('scheduleContent');
            container.innerHTML = scheduleData.map(item => `
                <div class="schedule-day">
                    <h4>${item.day}: ${item.theme}</h4>
                    <p><strong>學習重點：</strong> ${item.focus}</p>
                    <p><strong>核心詞彙：</strong> ${item.keywords}</p>
                </div>
            `).join('');
        }

        function loadVocabulary() {
            const container = document.getElementById('vocabularyList');
            container.innerHTML = vocabularyData.map((item, index) => `
                <div class="vocabulary-card">
                    <div class="word">
                        ${item.word}
                        <button class="play-btn" onclick="pronounceWord(${index})" title="播放發音">🔊</button>
                    </div>
                    <div class="pronunciation">${item.pronunciation}</div>
                    <div class="meaning">💡 ${item.meaning}</div>
                    <div class="example">例句：${item.example}</div>
                </div>
            `).join('');
        }

        function loadWritingExercises() {
            const today = new Date().toDateString();
            const exIndex = new Date().getDate() % 3;
            
            document.getElementById('ex1Question').textContent = writingExercises[0].question;
            document.getElementById('ex1Hint').textContent = writingExercises[0].hint;
            document.getElementById('ex2Topic').textContent = writingExercises[1].topic;
            document.getElementById('ex2Keywords').textContent = writingExercises[1].keywords;
            document.getElementById('ex3Topic').textContent = writingExercises[2].topic;
            
            performDailyReset();
        }

        // 頁面載入時初始化
        window.addEventListener('DOMContentLoaded', initApp);

        // 定時檢查每日重置 (每小時檢查一次)
        setInterval(performDailyReset, 3600000);
    </script>
</body>
</html>
