<!DOCTYPE html>
<html lang="zh-CN">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>单词趣味消消乐 - Unit 5</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: "Microsoft YaHei", sans-serif;
    }

    :root {
      --primary: #6a5acd;
      --primary-light: #9370db;
      --warn: #ff6347;
      --success: #32cd32;
      --tip-bg: #fff2cc;
      --tip-text: #d97706;
      --card-p1: linear-gradient(135deg, #ffb6c1, #ff69b4);
      --card-p2: linear-gradient(135deg, #87ceeb, #1e90ff);
      --disable: #cccccc;
      --trans: all 0.3s ease;
    }

    body {
      background: linear-gradient(135deg, #e6f7ff, #c2e9fb);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      position: relative;
      overflow-x: hidden;
    }

    /* 背景装饰 */
    .wave {
      position: fixed;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 100px;
      background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none"><path d="M0,0V46.29c47.79,22.2,103.59,32.17,158,28,70.36-5.37,136.33-33.31,206.8-37.5C438.64,32.43,512.34,53.67,583,72.05c69.27,18,138.3,24.88,209.4,13.08,36.15-6,69.85-17.84,104.45-29.34C989.49,25,1113-14.29,1200,52.47V0Z" opacity=".25" fill="%2346a0f5"/><path d="M0,0V15.81C13,36.92,27.64,56.86,47.69,72.05,99.41,111.27,165,111,224.58,91.58c31.15-10.15,60.09-26.07,89.67-39.8,40.92-19,84.73-46,130.83-49.67,36.26-2.85,70.9,9.42,98.6,31.56,31.77,25.39,62.32,62,103.63,73,40.44,10.79,81.35-6.69,119.13-24.28s75.16-39,116.92-43.05c59.73-5.85,113.28,22.88,168.9,38.84,30.2,8.66,59,6.17,87.09-7.5,22.43-10.89,48-26.93,60.65-49.24V0Z" opacity=".5" fill="%2346a0f5"/><path d="M0,0V5.63C149.93,59,314.09,71.32,475.83,42.57c43-7.64,84.23-20.12,127.61-26.46,59-8.63,112.48,12.24,165.56,35.4C827.93,77.22,886,95.24,951.2,90c86.53-7,172.46-45.71,248.8-84.81V0Z" fill="%2346a0f5"/></svg>');
      background-size: cover;
      z-index: 1;
    }

    .books {
      position: fixed;
      bottom: 30px;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      gap: 10px;
      z-index: 2;
    }

    .book {
      width: 40px;
      height: 50px;
      background: #8B4513;
      border-radius: 3px;
      position: relative;
    }

    .book:nth-child(2) {
      background: #A0522D;
      height: 55px;
    }

    .book:nth-child(3) {
      background: #CD853F;
      height: 45px;
    }

    .book::after {
      content: "";
      position: absolute;
      top: 5px;
      left: 5px;
      right: 5px;
      bottom: 5px;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 2px;
    }

    .flower-branch {
      position: fixed;
      top: 20px;
      right: 20px;
      width: 100px;
      height: 120px;
      z-index: 2;
    }

    .branch {
      position: absolute;
      width: 5px;
      height: 100px;
      background: #8B7355;
      top: 0;
      right: 50px;
      border-radius: 3px;
      transform: rotate(-10deg);
    }

    .flower {
      position: absolute;
      width: 25px;
      height: 25px;
      background: #FFB6C1;
      border-radius: 50%;
      top: 15px;
      right: 35px;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .flower::before {
      content: "";
      position: absolute;
      width: 10px;
      height: 10px;
      background: #FFD700;
      border-radius: 50%;
    }

    .petal {
      position: absolute;
      width: 8px;
      height: 8px;
      background: #FFB6C1;
      border-radius: 50%;
    }

    .petal:nth-child(1) {
      top: -5px;
      left: 50%;
      transform: translateX(-50%);
    }

    .petal:nth-child(2) {
      top: 50%;
      right: -5px;
      transform: translateY(-50%);
    }

    .petal:nth-child(3) {
      bottom: -5px;
      left: 50%;
      transform: translateX(-50%);
    }

    .petal:nth-child(4) {
      top: 50%;
      left: -5px;
      transform: translateY(-50%);
    }

    .leaf {
      position: absolute;
      width: 15px;
      height: 10px;
      background: #90EE90;
      border-radius: 50% 0 50% 0;
      top: 40px;
      right: 45px;
      transform: rotate(45deg);
    }

    .leaf:nth-child(2) {
      top: 60px;
      right: 40px;
      transform: rotate(-30deg);
    }

    /* 容器与页面通用 */
    .container {
      width: 100%;
      max-width: 1200px;
      background: white;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
      padding: 30px;
      margin: 0 auto;
      z-index: 3;
      position: relative;
    }

    .page {
      display: none;
      width: 100%;
      opacity: 0;
      transition: var;
    }

    .page.active {
      display: block;
      opacity: 1;
    }

    /* 首页选择页 */
    .unit-selection-page h1 {
      text-align: center;
      color: var(--primary);
      margin-bottom: 30px;
      font-size: 2.5rem;
    }

    .units-container {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      justify-content: center;
    }

    .unit-item {
      display: flex;
      width: 100%;
      max-width: 350px;
      margin-bottom: 20px;
    }

    .unit-circle {
      width: 80px;
      height: 80px;
      background: #FFD700;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      box-shadow: 0 5px 15px rgba(255, 215, 0, 0.3);
      margin-right: 20px;
      flex-shrink: 0;
    }

    .unit-circle span {
      font-size: 1.5rem;
      font-weight: bold;
      color: #333;
    }

    .unit-card {
      flex-grow: 1;
      background: #f9f9f9;
      border-radius: 15px;
      padding: 15px;
      text-align: left;
      cursor: pointer;
      transition: var;
      border: 2px solid transparent;
    }

    .unit-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
      border-color: var(--primary);
    }

    .unit-card h3 {
      color: #333;
      margin-bottom: 5px;
      font-size: 1.2rem;
    }

    .unit-card p {
      color: #666;
      font-size: 0.9rem;
    }

    /* 单元详情页 */
    .unit-detail-page {
      text-align: center;
    }

    .btn-back {
      position: absolute;
      top: 20px;
      left: 20px;
      background: var(--primary);
      color: white;
      border: none;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      font-size: 1.5rem;
      cursor: pointer;
      display: flex;
      justify-content: center;
      align-items: center;
      transition: var;
    }

    .btn-back:hover {
      background: #5a4abd;
      transform: scale(1.1);
    }

    .unit-detail-page .unit-circle {
      width: 120px;
      height: 120px;
      margin: 0 auto 30px;
    }

    .unit-detail-page .unit-circle span {
      font-size: 2.5rem;
    }

    .dropdown-area {
      margin: 30px 0;
      position: relative;
    }

    .dropdown {
      width: 100%;
      padding: 15px 20px;
      background: white;
      border: 2px solid #E0E0E0;
      border-radius: 10px;
      font-size: 1.2rem;
      text-align: center;
      cursor: pointer;
      transition: var;
    }

    .dropdown:hover {
      border-color: var(--primary);
    }

    .button-group {
      display: flex;
      flex-direction: column;
      gap: 15px;
      margin-top: 30px;
    }

    .btn {
      padding: 15px 30px;
      border: none;
      border-radius: 10px;
      font-size: 1.2rem;
      font-weight: bold;
      cursor: pointer;
      transition: var;
    }

    .btn-challenge {
      background: #D2B48C;
      color: white;
    }

    .btn-challenge:hover {
      background: #C19A6B;
      transform: translateY(-3px);
      box-shadow: 0 5px 15px rgba(194, 154, 107, 0.3);
    }

    .btn-pk {
      background: #FFD700;
      color: #333;
    }

    .btn-pk:hover {
      background: #FFC400;
      transform: translateY(-3px);
      box-shadow: 0 5px 15px rgba(255, 196, 0, 0.3);
    }

    /* 游戏页 */
    .game-page h1 {
      text-align: center;
      color: var(--primary);
      margin-bottom: 10px;
      font-size: 2.5rem;
    }

    .current-player-tip {
      text-align: center;
      font-size: 1.4rem;
      font-weight: bold;
      padding: 10px 20px;
      border-radius: 12px;
      background: var(--tip-bg);
      color: var(--tip-text);
      margin-bottom: 15px;
      display: none;
      transition: var;
      animation: tipFlash 1s ease;
    }

    @keyframes tipFlash {

      0,
      100 {
        transform: scale(1);
      }

      50 {
        transform: scale(1.05);
      }
    }

    .game-controls {
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
      margin-bottom: 20px;
      gap: 15px;
      background: #f8f9ff;
      padding: 15px;
      border-radius: 15px;
    }

    /* =====新增：可点击标签样式===== */
    .click-label {
      cursor: pointer;
      padding: 2px 6px;
      border-radius: 6px;
      transition: all 0.25s ease;
    }

    .click-label.active {
      font-size: 1.3em;
      color: #7b2cbf;
      background: #e9d5ff;
    }

    .click-label:hover {
      background: #f3e8ff;
    }

    .control-group {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      align-items: center;
    }

    select,
    button {
      padding: 10px 15px;
      border: none;
      border-radius: 10px;
      font-size: 1rem;
      cursor: pointer;
      transition: var;
    }

    select {
      background: #f0f8ff;
      border: 2px solid #b0e0e6;
      min-width: 120px;
    }

    .ctrl-btn {
      background: linear-gradient(to right, var(--primary), var(--primary-light));
      color: white;
      font-weight: bold;
    }

    .ctrl-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    }

    .mute-btn {
      background: #444;
    }

    .game-info {
      display: flex;
      justify-content: space-between;
      margin-bottom: 20px;
      font-size: 1.2rem;
      font-weight: bold;
      color: #555;
      background: #f0f8ff;
      padding: 10px 20px;
      border-radius: 10px;
    }

    .timer {
      font-size: 1.8rem;
      text-align: center;
      margin: 20px 0;
      color: var(--warn);
      font-weight: bold;
      background: #fff9f0;
      padding: 10px;
      border-radius: 10px;
    }

    .game-board {
      display: flex;
      gap: 20px;
      margin-bottom: 20px;
    }

    .player-section {
      flex: 1;
      background: #f9f9f9;
      border-radius: 15px;
      padding: 15px;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
      min-height: 400px;
    }

    .player-header {
      text-align: center;
      margin-bottom: 15px;
      font-size: 1.3rem;
      color: var(--primary);
      padding-bottom: 10px;
      border-bottom: 2px solid #e6e6fa;
    }

    .player-header {
      text-align: center;
      margin-bottom: 15px;
      font-size: 1.3rem;
      color: var(--primary);
      padding-bottom: 10px;
      border-bottom: 2px solid #e6e6fa;
    }

    .cards-container {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      justify-content: center;
      min-height: 300px;
      align-content: flex-start;
    }

    /* 卡片样式 */
    .card {
      padding: 15px 10px;
      border-radius: 12px;
      font-weight: bold;
      text-align: center;
      cursor: pointer;
      transition: var;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      user-select: none;
      min-width: 120px;
      min-height: 80px;
      display: flex;
      align-items: center;
      justify-content: center;
      word-break: break-word;
      font-size: clamp(0.9rem, 1.4vw, 1.5rem);
    }

    .card-p1-en {
      background: var(--card-p1);
      color: #8b0000;
    }

    .card-p2-en {
      background: linear-gradient(135deg, #dda0dd, #9370db);
      color: #330066;
    }

    .card-p1-cn {
      background: var(--card-p2);
      color: #000080;
    }

    .card-p2-cn {
      background: linear-gradient(135deg, #98fb98, #2e8b57);
      color: #004422;
    }

    .card.selected {
      transform: scale(1.1);
      box-shadow: 0 0 15px 5px rgba(255, 215, 0, 0.7);
      z-index: 10;
    }

    .card.matched {
      visibility: hidden;
      opacity: 0;
      transform: scale(0);
      transition: 0.5s all;
    }

    .card.wrong {
      animation: shake 0.5s;
      background: linear-gradient(135deg, #ff9999, #ff3333);
    }

    .card.disabled {
      opacity: 0.4;
      pointer-events: none;
      cursor: not-allowed;
    }

    @keyframes shake {

      0%,
      100% {
        transform: translateX(0);
      }

      20%,
      60% {
        transform: translateX(-5px);
      }

      40%,
      80% {
        transform: translateX(5px);
      }
    }

    .score-float {
      position: absolute;
      font-weight: bold;
      color: var(--success);
      font-size: 1.8rem;
      pointer-events: none;
      animation: floatUp 0.8s forwards;
    }

    @keyframes floatUp {
      0 {
        opacity: 1;
        transform: translateY(0);
      }

      100 {
        opacity: 0;
        transform: translateY(-60px);
      }
    }

    .current-player-indicator {
      background: #ffeb3b;
      color: #333;
      padding: 5px 15px;
      border-radius: 20px;
      font-weight: bold;
      margin-top: 10px;
      display: inline-block;
    }

    /* 弹窗通用 */
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.7);
      z-index: 100;
      justify-content: center;
      align-items: center;
    }

    .modal-content {
      background: white;
      padding: 30px;
      border-radius: 20px;
      text-align: center;
      max-width: 500px;
      width: 90%;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
    }

    .modal h2 {
      color: var(--primary);
      margin-bottom: 15px;
    }

    .modal p {
      margin-bottom: 20px;
      font-size: 1.2rem;
    }

    .winner-section {
      display: flex;
      justify-content: center;
      align-items: center;
      margin: 20px 0;
      gap: 20px;
    }

    .winner-trophy {
      font-size: 3rem;
      color: gold;
    }

    .pause-overlay {
      display: none;
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.7);
      z-index: 5;
      justify-content: center;
      align-items: center;
      border-radius: 20px;
    }

    .pause-content {
      background: white;
      padding: 30px;
      border-radius: 15px;
      text-align: center;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
    }

    .pause-content h2 {
      color: var(--primary);
      margin-bottom: 15px;
    }

    /* 生词弹窗 */
    .word-list-box {
      max-height: 300px;
      overflow-y: auto;
      text-align: left;
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 10px;
      margin: 15px 0;
    }

    .word-item {
      padding: 6px 0;
      border-bottom: 1px #eee solid;
    }

    /* 移动端适配 */
    @media (max-width: 768px) {
      .container {
        padding: 20px;
      }

      .unit-selection-page h1 {
        font-size: 2rem;
      }

      .unit-item {
        flex-direction: column;
        align-items: center;
        text-align: center;
      }

      .unit-circle {
        margin-right: 0;
        margin-bottom: 15px;
      }

      .unit-detail-page .unit-circle {
        width: 100px;
        height: 100px;
      }

      .unit-detail-page .unit-circle span {
        font-size: 2rem;
      }

      .dropdown {
        font-size: 1rem;
      }

      .btn {
        font-size: 1rem;
        padding: 12px 25px;
      }

      .game-board {
        flex-direction: column;
      }

      .game-controls {
        flex-direction: column;
        align-items: center;
      }

      h1 {
        font-size: 1.8rem;
      }

      .card {
        min-width: 100px;
        min-height: 70px;
        padding: 10px;
      }

      .control-group {
        justify-content: center;
      }
    }
  </style>
</head>

<body>
  <div class="wave"></div>
  <div class="books">
    <div class="book"></div>
    <div class="book"></div>
    <div class="book"></div>
  </div>
  <div class="flower-branch">
    <div class="branch"></div>
    <div class="flower">
      <div class="petal"></div>
      <div class="petal"></div>
      <div class="petal"></div>
      <div class="petal"></div>
    </div>
    <div class="leaf"></div>
    <div class="leaf"></div>
  </div>
  <div class="container">
    <!-- 单元选择页 -->
    <div class="page unit-selection-page active" id="unitSelectionPage">
      <h1>单词趣味消消乐</h1>
      <div class="units-container">
        <div class="unit-item">
          <div class="unit-circle"><span>Unit 5</span></div>
          <div class="unit-card" data-unit="5">
            <h3>Unit 5</h3>
            <p>共30个词汇</p>
          </div>
        </div>
      </div>
    </div>
    <!-- 单元详情页 -->
    <div class="page unit-detail-page" id="unitDetailPage">
      <button class="btn-back" id="backButton">←</button>
      <div class="unit-circle"><span id="currentUnit">Unit 5</span></div>
      <div class="dropdown-area">
        <div class="dropdown" id="unitDropdown">Unit 5</div>
      </div>
      <div class="game-controls">
        <div class="control-group">
          <label for="difficulty">难度选择：</label>
          <select id="difficulty">
            <option value="5">容易（5词）</option>
            <option value="10" selected>普通（10词）</option>
            <option value="15">困难（15词）</option>
          </select>
        </div>
      </div>
      <div class="button-group">
        <button class="btn btn-challenge" id="challengeButton">单人闯关</button>
        <button class="btn btn-pk" id="pkButton">双人PK</button>
      </div>
    </div>
    <!-- 游戏页面 -->
    <div class="page game-page" id="gamePage">
      <button class="btn-back" id="backToDetailButton">←</button>
      <h1>单词趣味消消乐</h1>
      <div class="current-player-tip" id="playerTip"></div>
      <div class="game-controls">
        <div class="control-group">
          <!-- 增加click-label类，点击交互 -->
          <div>单元:<span class="click-label" id="currentUnitDisplay">Unit 5</span></div>
          <div>模式:<span class="click-label" id="currentModeDisplay">单人模式</span></div>
          <div>难度:<span class="click-label" id="currentDifficultyDisplay">普通（10词）</span></div>
        </div>
        <div class="control-group">
          <button class="ctrl-btn" id="startBtn">开始游戏</button>
          <button class="ctrl-btn" id="pauseBtn">暂停</button>
          <button class="ctrl-btn" id="restartBtn">重开</button>
          <button class="ctrl-btn mute-btn" id="muteBtn">静音</button>
        </div>
      </div>
      <div class="game-info">
        <div>玩家1得分:<span id="player1Score">0</span></div>
        <div>玩家2得分:<span id="player2Score">0</span></div>
        <div>连击:<span id="combo">0</span></div>
      </div>
      <div class="timer">用时:<span id="timerDisplay">00:00</span></div>
      <div class="pause-overlay" id="pauseOverlay">
        <div class="pause-content">
          <h2>游戏暂停</h2>
          <p>点击继续恢复游戏</p>
          <button class="ctrl-btn" id="resumeBtn">继续</button>
        </div>
      </div>
      <div class="game-board">
        <div class="player-section">
          <div class="player-header">玩家1（粉色卡片）</div>
          <div id="player1Indicator" class="current-player-indicator" style="display:none;">当前操作</div>
          <div class="cards-container" id="player1Cards"></div>
        </div>
        <div class="player-section">
          <div class="player-header">玩家2（绿蓝卡片）</div>
          <div id="player2Indicator" class="current-player-indicator" style="display:none;">当前操作</div>
          <div class="cards-container" id="player2Cards"></div>
        </div>
      </div>
    </div>
  </div>
  <!-- 结算弹窗 -->
  <div class="modal" id="successModal">
    <div class="modal-content">
      <h2>游戏完成！</h2>
      <div class="winner-section">
        <div class="winner-trophy">🏆</div>
        <div>
          <p id="winnerText">恭喜通关！</p>
          <p>用时:<span id="completionTime">00:00</span></p>
          <p>最高连击:<span id="maxCombo">0</span></p>
        </div>
        <div class="winner-trophy">🏆</div>
      </div>
      <p>本次生词列表：</p>
      <div class="word-list-box" id="wrongWordBox"></div>
      <button class="ctrl-btn" id="restartFromModal">再来一局</button>
      <button class="ctrl-btn" id="closeModal" style="margin-top:10px;">返回首页</button>
    </div>
  </div>
  <!-- 确认弹窗 -->
  <div class="modal" id="confirmModal">
    <div class="modal-content">
      <h2 id="confirmTitle">确认操作</h2>
      <p id="confirmText">确定要重置本局进度吗？</p>
      <div style="display:flex;gap:15px;justify-content:center;margin-top:20px;">
        <button class="ctrl-btn" id="confirmYes">确认</button>
        <button class="ctrl-btn mute-btn" id="confirmNo">取消</button>
      </div>
    </div>
  </div>
  <script>
    // ====================== 全局配置与常量（模块化拆分） ======================
    const CONFIG = {
      wordLibrary: {
        5: [
          { english: "eternal", chinese: "a.①永远的；永恒的 ②似乎无休止的；没完没了的" },
          { english: "ceremony", chinese: "n.①[C]典礼；仪式 ②[U]礼仪；礼节" },
          { english: "honorary", chinese: "a.①（称号、头衔或学位）荣誉的 ②（职位）名誉的，无报酬的" },
          { english: "award", chinese: "vt.授予，给予（奖品或奖金）；奖励 n.[C]奖；奖赏；奖金；奖品" },
          { english: "applause", chinese: "n.[U]鼓掌；喝彩" },
          { english: "prompt", chinese: "vt.促使；导致；激起 a.迅速的；立刻的；及时的" },
          { english: "blockade", chinese: "n.[C, usu. sing.]（对某地的）封锁" },
          { english: "revolutionary", chinese: "a.①革命的 ②革命性的；突破性的；创新的" },
          { english: "relevant", chinese: "a.相关的；有关的；切题的" },
          { english: "reform", chinese: "n.[C,U]改进；改革 vt.改革；改进；改良" },
          { english: "predecessor", chinese: "n.[C]①（被取代的）原有事物；前身 ②前任；前辈" },
          { english: "conscientious", chinese: "a.勤勉认真的；细心负责的" },
          { english: "derive", chinese: "v.源自；（从某物中）取得，得到" },
          { english: "enable", chinese: "vt.使可能；使发生" },
          { english: "cease", chinese: "v.(fml.)停止；终止；结束" },
          { english: "integrate", chinese: "v.①（使）融入（某群体或社会）；（使）成为一体 ②（使）合并，成为一体" },
          { english: "pad", chinese: "vt.给（某物）填充软物；用软物保护（某物）" },
          { english: "initiative", chinese: "n.①(the ~)主动权 ②[U]自主决断能力；主动性" },
          { english: "harsh", chinese: "a.①（天气或生活环境）恶劣的，艰苦的 ②严厉的；残酷的；苛刻的" },
          { english: "affectionate", chinese: "a.表示爱的；充满深情的；温柔亲切的" },
          { english: "premier", chinese: "n.[C]总理；首相 a.(only before noun)(fml.)最好的；最重要的" },
          { english: "cordial", chinese: "a.(fml.)热情友好的；和蔼可亲的" },
          { english: "blaze", chinese: "vt.(~ a trail)开路；带头；做先导 vi.熊熊燃烧" },
          { english: "trail", chinese: "n.[C]①（乡间或森林里的）小路或小径 ②痕迹" },
          { english: "finance", chinese: "n.[U]财政；金融 vt.为…提供资金" },
          { english: "journalism", chinese: "n.[U]新闻业；新闻工作" },
          { english: "withdraw", chinese: "v.①（使）退出（活动、组织等） vt.取消，不再给予，停止提供（支持或金钱）" },
          { english: "economic", chinese: "a.(only before noun)经济（上）的" },
          { english: "crucial", chinese: "a.至关重要的；关键的；决定性的" },
          { english: "hesitation", chinese: "n.[C, U]（尤指因紧张或不确定而产生的）犹豫，踌躇" }
        ]
      },
      unitInfo: { 5: { title: "Unit 5", topic: "Unit 5", desc: "共30个词汇" } },
      audioMute: false,
      audioCtx: null
    };
    // 游戏状态全局变量
    let gameState = {
      active: false, started: false, paused: false,
      startTime: 0, pauseStart: 0, totalPause: 0, timer: null,
      currentPlayer: 1, selectedCard: null,
      p1Score: 0, p2Score: 0, p1Match: 0, p2Match: 0, totalPair: 0,
      combo: 0, maxCombo: 0, wrongWords: [],
      mode: "single", unit: 5, diff: 10
    };
    // DOM缓存（一次性获取，减少重复查询）
    const DOM = {
      // 页面
      pageSel: document.getElementById('unitSelectionPage'),
      pageDetail: document.getElementById('unitDetailPage'),
      pageGame: document.getElementById('gamePage'),
      unitCards: document.querySelectorAll('.unit-card'),
      // 详情页
      backBtn: document.getElementById('backButton'),
      currUnitText: document.getElementById('currentUnit'),
      unitDrop: document.getElementById('unitDropdown'),
      diffSel: document.getElementById('difficulty'),
      btnSingle: document.getElementById('challengeButton'),
      btnPk: document.getElementById('pkButton'),
      // 游戏页
      backGame: document.getElementById('backToDetailButton'),
      tipBox: document.getElementById('playerTip'),
      unitDisp: document.getElementById('currentUnitDisplay'),
      modeDisp: document.getElementById('currentModeDisplay'),
      diffDisp: document.getElementById('currentDifficultyDisplay'),
      startBtn: document.getElementById('startBtn'),
      pauseBtn: document.getElementById('pauseBtn'),
      restartBtn: document.getElementById('restartBtn'),
      muteBtn: document.getElementById('muteBtn'),
      score1: document.getElementById('player1Score'),
      score2: document.getElementById('player2Score'),
      comboDisp: document.getElementById('combo'),
      timerText: document.getElementById('timerDisplay'),
      pauseOverlay: document.getElementById('pauseOverlay'),
      resumeBtn: document.getElementById('resumeBtn'),
      card1Wrap: document.getElementById('player1Cards'),
      card2Wrap: document.getElementById('player2Cards'),
      ind1: document.getElementById('player1Indicator'),
      ind2: document.getElementById('player2Indicator'),
      //弹窗标签
      clickLabels: document.querySelectorAll('.click-label'),
      // 弹窗
      modalWin: document.getElementById('successModal'),
      winText: document.getElementById('winnerText'),
      timeFinish: document.getElementById('completionTime'),
      maxComboText: document.getElementById('maxCombo'),
      wrongListBox: document.getElementById('wrongWordBox'),
      modalRestart: document.getElementById('restartFromModal'),
      modalClose: document.getElementById('closeModal'),
      modalConfirm: document.getElementById('confirmModal'),
      confirmTitle: document.getElementById('confirmTitle'),
      confirmTxt: document.getElementById('confirmText'),
      confirmYes: document.getElementById('confirmYes'),
      confirmNo: document.getElementById('confirmNo')
    };
    // ====================== 工具函数 ======================
    // 页面切换
    function showPage(id) {
      document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
      document.getElementById(id).classList.add('active');
    }
    // 洗牌
    function shuffle(arr) {
      let a = [...arr];
      for (let i = a.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [a[i], a[j]] = [a[j], a[i]];
      }
      return a;
    }
    // 获取难度文字
    function getDiffStr(num) {
      const map = { 5: "容易（5词）", 10: "普通（10词）", 15: "困难（15词）" };
      return map[num] || "普通（10词）";
    }
    // 弹窗控制
    function openConfirm(title, text, cb) {
      DOM.confirmTitle.innerText = title;
      DOM.confirmTxt.innerText = text;
      DOM.modalConfirm.style.display = 'flex';
      DOM.confirmYes.onclick = () => {
        DOM.modalConfirm.style.display = 'none';
        cb();
      };
      DOM.confirmNo.onclick = () => DOM.modalConfirm.style.display = 'none';
    }
    // 加分浮动文字
    function showFloatScore(container, scoreNum) {
      const float = document.createElement('div');
      float.className = 'score-float';
      float.innerText = `+${scoreNum}`;
      const rect = container.getBoundingClientRect();
      float.style.left = rect.left + rect.width / 2 + 'px';
      float.style.top = rect.top + 'px';
      document.body.appendChild(float);
      setTimeout(() => float.remove(), 800);
    }
    // ====================== 音频模块（全局复用AudioContext） ======================
    function initAudio() {
      if (!CONFIG.audioCtx) {
        CONFIG.audioCtx = new (window.AudioContext || window.webkitAudioContext)();
      }
    }
    function playAudio(type) {
      if (CONFIG.audioMute) return;
      initAudio();
      const ctx = CONFIG.audioCtx;
      const osc = ctx.createOscillator();
      const gain = ctx.createGain();
      osc.connect(gain); gain.connect(ctx.destination);
      const now = ctx.currentTime;
      switch (type) {
        case "select":
          osc.frequency.value = 659.25;
          gain.gain.setValueAtTime(0.3, now);
          gain.gain.exponentialRampToValueAtTime(0.01, now + 0.2);
          osc.start(now); osc.stop(now + 0.2); break;
        case "match":
          osc.frequency.value = 880;
          gain.gain.setValueAtTime(0.5, now);
          gain.gain.exponentialRampToValueAtTime(0.01, now + 0.5);
          osc.start(now); osc.stop(now + 0.5); break;
        case "error":
          osc.frequency.value = 220;
          gain.gain.setValueAtTime(0.5, now);
          gain.gain.exponentialRampToValueAtTime(0.01, now + 0.3);
          osc.start(now); osc.stop(now + 0.3);
          gameState.combo = 0; updateCombo(); break;
        case "win":
          const freqs = [523.25, 659.25, 783.99, 1046.5];
          const ts = [0, 0.2, 0.4, 0.6];
          freqs.forEach((f, i) => {
            setTimeout(() => {
              const o = ctx.createOscillator();
              const g = ctx.createGain();
              o.connect(g); g.connect(ctx.destination);
              o.frequency.value = f;
              g.gain.setValueAtTime(0.3, ctx.currentTime);
              g.gain.exponentialRampToValueAtTime(0.01, ctx.currentTime + 0.3);
              o.start(ctx.currentTime); o.stop(ctx.currentTime + 0.3);
            }, ts[i] * 1000);
          }); break;
        case "pause":
          osc.frequency.value = 440;
          gain.gain.setValueAtTime(0.3, now);
          gain.gain.exponentialRampToValueAtTime(0.01, now + 0.3);
          osc.start(now); osc.stop(now + 0.3); break;
      }
    }
    // 单词朗读Web Speech
    function speakWord(word) {
      if (CONFIG.audioMute) return;
      const utter = new SpeechSynthesisUtterance(word);
      utter.lang = "en-US";
      speechSynthesis.speak(utter);
    }
    // 静音切换
    function toggleMute() {
      CONFIG.audioMute = !CONFIG.audioMute;
      DOM.muteBtn.innerText = CONFIG.audioMute ? "取消静音" : "静音";
    }
    //==== 新增：顶部标签点击交互 ====
    function clearLabelActive() {
      DOM.clickLabels.forEach(el => el.classList.remove('active'));
    }
    //绑定点击事件
    DOM.unitDisp.onclick = function () {
      playAudio("select");
      this.classList.toggle("active");
    }
    DOM.modeDisp.onclick = function () {
      playAudio("select");
      this.classList.toggle("active");
      //切换单人/双人
      if (gameState.mode === "single") {
        gameState.mode = "double";
        DOM.modeDisp.innerText = "双人对战";
      } else {
        gameState.mode = "single";
        DOM.modeDisp.innerText = "单人模式";
      }
    }
    DOM.diffDisp.onclick = function () {
      playAudio("select");
      this.classList.toggle("active");
      //循环切换难度
      const diffList = [5, 10, 15];
      let idx = diffList.indexOf(gameState.diff);
      idx = (idx + 1) % diffList.length;
      gameState.diff = diffList[idx];
      DOM.diffSel.value = gameState.diff;
      DOM.diffDisp.innerText = getDiffStr(gameState.diff);
    }
    //点击页面空白清除高亮
    document.body.addEventListener('click', (e) => {
      if (!e.target.classList.contains("click-label")) {
        clearLabelActive();
      }
    })
    // ====================== 玩家提示更新 ======================
    function updatePlayerTip() {
      if (gameState.mode !== "double") {
        DOM.tipBox.style.display = "none";
        return;
      }
      DOM.tipBox.style.display = "block";
      DOM.tipBox.innerText = `现在轮到【玩家${gameState.currentPlayer}】操作，仅可点击自己区域卡片！`;
      DOM.tipBox.style.animation = "none";
      DOM.tipBox.offsetHeight; // 重绘触发动画
      DOM.tipBox.style.animation = "tipFlash 1s ease";
      DOM.ind1.style.display = gameState.currentPlayer === 1 ? "block" : "none";
      DOM.ind2.style.display = gameState.currentPlayer === 2 ? "block" : "none";
    }
    // 连击更新
    function updateCombo() {
      DOM.comboDisp.innerText = gameState.combo;
      if (gameState.combo > gameState.maxCombo) gameState.maxCombo = gameState;
    }
    // ====================== 计时器 ======================
    function clearTimer() {
      if (gameState.timer) clearInterval(gameState.timer);
      gameState.timer = null;
    }
    function tickTimer() {
      if (!gameState.active) return;
      const now = Date.now();
      const pass = Math.floor((now - gameState.startTime - gameState.totalPause) / 1000);
      const m = Math.floor(pass / 60).toString().padStart(2, '0');
      const s = (pass % 60).toString().padStart(2, '0');
      DOM.timerText.innerText = `${m}:${s}`;
    }
    // ====================== 卡片渲染（事件委托，不批量绑定） ======================
    function renderCards(wordList, wrapEl, playerNum) {
      wrapEl.innerHTML = "";
      const enArr = [], cnArr = [];
      wordList.forEach(w => {
        // 英文卡片
        const en = document.createElement('div');
        en.className = playerNum === 1 ? "card card-p1-en" : "card card-p2-en";
        en.dataset.word = w.english;
        en.dataset.type = "english";
        en.dataset.player = playerNum;
        en.innerText = w.english;
        enArr.push(en);
        // 点击发音
        en.onclick = (e) => {
          e.stopPropagation();
          speakWord(w.english);
          handleCardClick(en, playerNum);
        }
        // 中文卡片
        const cn = document.createElement('div');
        cn.className = playerNum === 1 ? "card card-p1-cn" : "card card-p2-cn";
        cn.dataset.word = w.english;
        cn.dataset.type = "chinese";
        cn.dataset.player = playerNum;
        cn.innerText = w.chinese;
        cnArr.push(cn);
        cn.onclick = (e) => {
          e.stopPropagation();
          handleCardClick(cn, playerNum);
        }
      })
      const all = shuffle([...enArr, ...cnArr]);
      all.forEach(c => wrapEl.appendChild(c));
    }
    // 禁用非当前玩家卡片
    function lockOtherPlayerCards() {
      if (gameState.mode !== "double") return;
      const otherWrap = gameState.currentPlayer === 1 ? DOM.card2Wrap : DOM.card1Wrap;
      const selfWrap = gameState.currentPlayer === 1 ? DOM.card1Wrap : DOM.card2Wrap;
      otherWrap.querySelectorAll('.card:not(.matched)').forEach(c => c.classList.add('disabled'));
      selfWrap.querySelectorAll('.card:not(.matched)').forEach(c => c.classList.remove('disabled'));
    }
    // 卡片点击核心逻辑
    function handleCardClick(card, pNum) {
      if (!gameState.active || gameState.paused || card.classList.contains('matched') || card.classList.contains('disabled')) return;
      if (gameState.selectedCard === card) return;
      playAudio("select");
      card.classList.add('selected');
      if (!gameState.selectedCard) {
        gameState.selectedCard = card;
        return;
      }
      const prev = gameState.selectedCard;
      // 匹配成功
      if (prev.dataset.word === card.dataset.word && prev.dataset.type !== card.dataset.type) {
        setTimeout(() => {
          prev.classList.add('matched');
          card.classList.add('matched');
          gameState.selectedCard = null;
          playAudio("match");
          gameState.combo += 1;
          updateCombo();
          const addScore = 5 + (gameState.combo > 2 ? 2 : 0);
          showFloatScore(card, addScore);
          if (gameState.mode === "single") {
            gameState.p1Score += addScore;
            gameState.p1Match += 1;
            DOM.score1.innerText = gameState.p1Score;
          } else {
            if (gameState.currentPlayer === 1) {
              gameState.p1Score += addScore;
              gameState.p1Match += 1;
              DOM.score1.innerText = gameState.p1Score;
            } else {
              gameState.p2Score += addScore;
              gameState.p2Match += 1;
              DOM.score2.innerText = gameState.p2Score;
            }
          }
          checkFinish();
        }, 300);
      } else {
        // 匹配失败，加入生词本
        setTimeout(() => {
          prev.classList.remove('selected');
          card.classList.remove('selected');
          card.classList.add('wrong');
          const wordObj = CONFIG.wordLibrary[gameState.unit].find(x => x.english === card.dataset.word);
          if (!gameState.wrongWords.some(i => i.english === wordObj.english)) gameState.wrongWords.push(wordObj);
          gameState.selectedCard = null;
          playAudio("error");
          setTimeout(() => card.classList.remove('wrong'), 500);
          // 双人切换玩家
          if (gameState.mode === "double") {
            gameState.currentPlayer = gameState.currentPlayer === 1 ? 2 : 1;
            updatePlayerTip();
            lockOtherPlayerCards();
          }
        }, 500);
      }
    }
    // 检测游戏通关
    function checkFinish() {
      const target = gameState.totalPair;
      if (gameState.mode === "single") {
        if (gameState.p1Match >= target) endGame();
      } else {
        if (gameState.p1Match >= target || gameState.p2Match >= target) endGame();
      }
    }
    // 游戏结束结算
    function endGame() {
      gameState.active = false;
      clearTimer();
      playAudio("win");
      let winStr = "";
      if (gameState.mode === "single") {
        winStr = "恭喜你完成单人闯关！";
      } else {
        if (gameState.p1Match === gameState.p2Match) {
          winStr = gameState.p1Score > gameState.p2Score ? "玩家1获胜" : gameState.p2Score > gameState.p1Score ? "玩家2获胜" : "平局！";
        } else {
          winStr = gameState.p1Match === gameState.totalPair ? "玩家1获胜" : "玩家2获胜";
        }
      }
      DOM.winText.innerText = winStr;
      DOM.maxComboText.innerText = gameState.maxCombo;
      DOM.timeFinish.innerText = DOM.timerText.innerText;
      // 填充生词列表
      DOM.wrongListBox.innerHTML = "";
      if (gameState.wrongWords.length === 0) {
        DOM.wrongListBox.innerHTML = "<div class='word-item'>全部配对正确，无生词！</div>";
      } else {
        gameState.wrongWords.forEach(w => {
          const div = document.createElement('div');
          div.className = "word-item";
          div.innerText = `${w.english} —— ${w.chinese}`;
          DOM.wrongListBox.appendChild(div);
        })
      }
      DOM.modalWin.style.display = 'flex';
    }
    // 初始化本局游戏
    function setupGame() {
      clearTimer();
      // 重置状态
      gameState = {
        active: false, started: false, paused: false,
        startTime: 0, pauseStart: 0, totalPause: 0, timer: null,
        currentPlayer: 1, selectedCard: null,
        p1Score: 0, p2Score: 0, p1Match: 0, p2Match: 0,
        totalPair: 0, combo: 0, maxCombo: 0, wrongWords: [],
        mode: gameState.mode, unit: 5, diff: Number(DOM.diffSel.value)
      };
      // 更新页面显示文字
      const unitInfo = CONFIG.unitInfo[5];
      DOM.unitDisp.innerText = unitInfo.title;
      DOM.modeDisp.innerText = gameState.mode === "single" ? "单人模式" : "双人对战";
      DOM.diffDisp.innerText = getDiffStr(gameState.diff);
      DOM.score1.innerText = "0"; DOM.score2.innerText = "0";
      DOM.comboDisp.innerText = "0";
      DOM.timerText.innerText = "00:00";
      DOM.pauseOverlay.style.display = "none";
      DOM.pauseBtn.innerText = "暂停";
      DOM.startBtn.disabled = false;
      DOM.pauseBtn.disabled = true;
      updatePlayerTip();
      // 清空卡片容器
      DOM.card1Wrap.innerHTML = ""; DOM.card2Wrap.innerHTML = "";
      // 随机抽取指定数量单词
      const allWords = CONFIG.wordLibrary[5];
      const selected = shuffle(allWords).slice(0, gameState.diff);
      gameState.totalPair = selected.length;
      // 渲染卡片
      renderCards(selected, DOM.card1Wrap, 1);
      if (gameState.mode === "double") {
        document.querySelector('.player-section:nth-child(2)').style.display = "block";
        renderCards(selected, DOM.card2Wrap, 2);
        lockOtherPlayerCards();
      } else {
        document.querySelector('.player-section:nth-child(2)').style.display = "none";
      }
    }
    // 开始游戏
    function startGame() {
      if (gameState.started) return;
      gameState.active = true;
      gameState.started = true;
      gameState.startTime = Date.now();
      clearTimer();
      gameState.timer = setInterval(tickTimer, 1000);
      tickTimer();
      DOM.startBtn.disabled = true;
      DOM.pauseBtn.disabled = false;
      playAudio("select");
      lockOtherPlayerCards();
    }
    // 暂停游戏
    function pauseGame() {
      if (!gameState.active || gameState.paused) return;
      gameState.paused = true;
      gameState.pauseStart = Date.now();
      clearTimer();
      DOM.pauseOverlay.style.display = "flex";
      DOM.pauseBtn.innerText = "已暂停";
      playAudio("pause");
    }
    // 恢复游戏
    function resumeGame() {
      if (!gameState.paused) return;
      gameState.paused = false;
      gameState.totalPause += Date.now() - gameState.pauseStart;
      gameState.timer = setInterval(tickTimer, 1000);
      DOM.pauseOverlay.style.display = "none";
      DOM.pauseBtn.innerText = "暂停";
      playAudio("select");
    }
    // 重新开局（弹窗确认）
    function restartGame() {
      openConfirm("重新开局", "当前所有进度会清空，确认重新开始吗？", () => {
        setupGame();
      })
    }
    // 返回单元选择页
    function backToSelect() {
      clearTimer();
      DOM.modalWin.style.display = "none";
      DOM.card1Wrap.innerHTML = "";
      DOM.card2Wrap.innerHTML = "";
      showPage('unitSelectionPage');
    }
    // ====================== 绑定全部事件 ======================
    // 单元卡片点击
    DOM.unitCards.forEach(card => {
      card.onclick = () => {
        const u = Number(card.dataset.unit);
        const info = CONFIG.unitInfo[u];
        DOM.currUnitText.innerText = info.title;
        DOM.unitDrop.innerText = info.topic;
        showPage('unitDetailPage');
      }
    })
    // 返回按钮
    DOM.backBtn.onclick = () => showPage('unitSelectionPage');
    DOM.backGame.onclick = () => {
      openConfirm("返回上一页", "本局进度将丢失，确认返回吗？", () => {
        clearTimer();
        showPage('unitDetailPage');
      })
    }
    // 模式选择
    DOM.btnSingle.onclick = () => {
      gameState.mode = "single";
      showPage('gamePage');
      setupGame();
    }
    DOM.btnPk.onclick = () => {
      gameState.mode = "double";
      showPage('gamePage');
      setupGame();
    }
    // 游戏控制按钮
    DOM.startBtn.onclick = startGame;
    DOM.pauseBtn.onclick = pauseGame;
    DOM.resumeBtn.onclick = resumeGame;
    DOM.restartBtn.onclick = restartGame;
    DOM.muteBtn.onclick = toggleMute;
    // 结算弹窗按钮
    DOM.modalRestart.onclick = () => {
      DOM.modalWin.style.display = "none";
      setupGame();
    }
    DOM.modalClose.onclick = backToSelect;
    DOM.confirmNo.onclick = () => DOM.modalConfirm.style.display = 'none';
    // 初始化页面
    showPage('unitSelectionPage');
  </script>
</body>

</html>
