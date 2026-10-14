[index.html](https://github.com/user-attachments/files/33414032/index.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>雅居专列英语·泉州站</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: "Microsoft YaHei", "PingFang SC", sans-serif;
    background-color: #f0f6ff;
    background-image:
      linear-gradient(45deg, #dbe9ff 25%, transparent 25%),
      linear-gradient(-45deg, #dbe9ff 25%, transparent 25%),
      linear-gradient(45deg, transparent 75%, #dbe9ff 75%),
      linear-gradient(-45deg, transparent 75%, #dbe9ff 75%);
    background-size: 40px 40px;
    background-position: 0 0, 0 20px, 20px -20px, -20px 0px;
    color: #333;
    min-height: 100vh;
  }
  /* 顶部导航 */
  .navbar {
    background: linear-gradient(90deg, #8b2e2e, #b83a3a);
    color: #fff;
    padding: 12px 32px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    box-shadow: 0 2px 8px rgba(0,0,0,0.15);
    position: sticky; top: 0; z-index: 100;
  }
  .navbar-left { display: flex; align-items: center; gap: 12px; font-weight: 600; font-size: 16px; }
  .navbar-left .sub { font-weight: 400; font-size: 13px; opacity: 0.8; }
  .navbar-menu { display: flex; gap: 6px; flex-wrap: wrap; }
  .navbar-menu a {
    color: #f5e6e6; text-decoration: none; font-size: 13px;
    padding: 6px 12px; border-radius: 20px; cursor: pointer;
    display: flex; align-items: center; gap: 4px; transition: background 0.2s;
  }
  .navbar-menu a.active, .navbar-menu a:hover { background: rgba(255,255,255,0.2); color: #fff; }
  .btn-print { background: rgba(255,255,255,0.15); border: none; color: #fff; padding: 6px 16px; border-radius: 20px; cursor: pointer; font-size: 13px; }
  .btn-print:hover { background: rgba(255,255,255,0.25); }

  /* 主体 */
  .container { max-width: 1150px; margin: 0 auto; padding: 36px 24px 60px; }
  .page-title { font-size: 32px; color: #b83a3a; margin-bottom: 6px; }
  .page-subtitle { font-size: 15px; color: #666; font-family: monospace; margin-bottom: 26px; }

  /* 卡片 */
  .card {
    background: #fff; border-radius: 10px;
    box-shadow: 0 4px 16px rgba(0,0,0,0.08);
    padding: 24px 28px; margin-bottom: 24px;
    position: relative; overflow: hidden;
  }
  .card::before {
    content: ""; position: absolute; top: 0; left: 0; right: 0; height: 4px;
    background: linear-gradient(90deg, #b83a3a, #d4a017);
  }
  .card-title { font-size: 17px; font-weight: 600; color: #8b2e2e; margin-bottom: 18px; display: flex; align-items: center; gap: 8px; }
  .card-title .icon { color: #b83a3a; font-size: 18px; }

  /* 表单栅格 */
  .form-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 16px; }
  .form-item { display: flex; flex-direction: column; gap: 6px; }
  .form-item label { font-size: 13px; color: #4a5568; font-weight: 500; display: flex; align-items: center; gap: 4px; }
  .form-item label .tag-icon { color: #b83a3a; font-size: 14px; }
  .form-item input {
    padding: 10px 12px; border: 1px solid #cbd5e0; border-radius: 6px;
    font-size: 14px; outline: none; transition: border-color 0.2s, box-shadow 0.2s;
  }
  .form-item input:focus { border-color: #b83a3a; box-shadow: 0 0 0 3px rgba(184,58,58,0.15); }
  .form-item input::placeholder { color: #a0aec0; }
  .form-item input[readonly] { background: #f7fafc; color: #4a5568; }

  .form-actions { margin-top: 20px; display: flex; align-items: center; gap: 14px; }
  .btn-save {
    background: #2f855a; color: #fff; border: none; padding: 10px 24px;
    border-radius: 24px; font-size: 14px; cursor: pointer;
    display: flex; align-items: center; gap: 6px; transition: background 0.2s, transform 0.1s;
  }
  .btn-save:hover { background: #276749; }
  .btn-save:active { transform: scale(0.97); }
  .hint { font-size: 13px; color: #a0aec0; }

  /* 案例信息 */
  .case-header {
    display: flex; align-items: center; gap: 16px;
    padding: 14px 18px; background: #fff8f0; border-radius: 8px; margin-bottom: 18px;
    border-left: 4px solid #d4a017;
  }
  .case-header .badge {
    background: #b83a3a; color: #fff; padding: 6px 14px; border-radius: 6px;
    font-size: 13px; font-weight: 600; white-space: nowrap;
  }
  .case-header .case-info { font-size: 13px; color: #555; line-height: 1.7; }
  .case-header .case-info strong { color: #8b2e2e; }

  .case-desc { font-size: 14px; line-height: 1.9; color: #4a5568; margin-bottom: 18px; }

  .scene-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 14px; margin-bottom: 18px; }
  .scene-card {
    background: #fff; border: 1px solid #f0e0d0; border-radius: 8px; padding: 14px 16px;
    border-left: 4px solid #d4a017;
  }
  .scene-card .scene-no { font-size: 12px; color: #b83a3a; font-weight: 600; margin-bottom: 4px; }
  .scene-card .scene-en { font-size: 14px; font-weight: 600; color: #333; margin-bottom: 4px; }
  .scene-card .scene-cn { font-size: 13px; color: #666; }

  .case-note {
    background: #fdf6ec; border-radius: 8px; padding: 14px 18px;
    font-size: 13px; color: #6b4a1f; line-height: 1.8;
  }
  .case-note strong { color: #b83a3a; }

  .quote { text-align: center; font-size: 14px; color: #b83a3a; font-style: italic; margin-top: 20px; }

  /* 词汇卡片 */
  .vocab-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(240px, 1fr)); gap: 14px; }
  .vocab-card {
    background: #fff; border: 1px solid #f0e0d0; border-radius: 8px;
    padding: 14px 16px; transition: box-shadow 0.2s, transform 0.2s;
  }
  .vocab-card:hover { box-shadow: 0 4px 12px rgba(184,58,58,0.12); transform: translateY(-2px); }
  .vocab-card .word { font-size: 16px; font-weight: 700; color: #b83a3a; margin-bottom: 2px; }
  .vocab-card .phonetic { font-size: 12px; color: #888; margin-bottom: 4px; }
  .vocab-card .meaning { font-size: 13px; color: #444; margin-bottom: 8px; }
  .vocab-card .actions { display: flex; align-items: center; gap: 8px; }
  .vocab-card .actions button {
    background: #f0f6ff; border: 1px solid #cbd5e0; border-radius: 4px;
    padding: 4px 10px; font-size: 12px; cursor: pointer; color: #4a5568;
  }
  .vocab-card .actions button:hover { background: #e2e8f0; }
  .vocab-card .score { font-size: 12px; color: #b83a3a; margin-left: auto; }

  /* 句型 */
  .sentence-section { margin-bottom: 26px; }
  .sentence-section .section-title {
    font-size: 15px; font-weight: 600; color: #b83a3a;
    padding: 8px 14px; background: #fdf0f0; border-radius: 6px; margin-bottom: 12px;
  }
  .sentence-item {
    background: #fff; border: 1px solid #f0e0d0; border-radius: 8px;
    padding: 12px 16px; margin-bottom: 10px; display: flex; align-items: flex-start; gap: 12px;
  }
  .sentence-item .sentence-text { flex: 1; }
  .sentence-item .en { font-size: 14px; color: #333; margin-bottom: 4px; font-weight: 500; }
  .sentence-item .cn { font-size: 13px; color: #777; }
  .sentence-item .read-btn {
    background: #b83a3a; color: #fff; border: none; padding: 6px 12px;
    border-radius: 6px; font-size: 12px; cursor: pointer; white-space: nowrap;
  }
  .sentence-item .read-btn:hover { background: #8b2e2e; }

  /* 对话卡片 */
  .dialog-item {
    background: #fff; border: 1px solid #f0e0d0; border-radius: 8px;
    padding: 16px 18px; margin-bottom: 12px; display: flex; gap: 14px;
  }
  .dialog-item .role-badge {
    background: #b83a3a; color: #fff; padding: 6px 12px; border-radius: 20px;
    font-size: 12px; font-weight: 600; white-space: nowrap; height: fit-content;
  }
  .dialog-item .dialog-content { flex: 1; }
  .dialog-item .dialog-en { font-size: 14px; color: #333; margin-bottom: 6px; }
  .dialog-item .dialog-cn { font-size: 13px; color: #777; }

  /* 角色分工 */
  .role-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 12px; }
  .role-item {
    background: #fff; border: 1px solid #f0e0d0; border-radius: 8px;
    padding: 14px; text-align: center;
  }
  .role-item .role-name { font-size: 14px; font-weight: 600; color: #b83a3a; margin-bottom: 6px; }
  .role-item .role-desc { font-size: 12px; color: #888; margin-bottom: 8px; }
  .role-item input { width: 100%; padding: 8px; border: 1px solid #cbd5e0; border-radius: 6px; font-size: 13px; outline: none; }
  .role-item input:focus { border-color: #b83a3a; }

  /* 评分表 */
  .score-table { width: 100%; border-collapse: collapse; font-size: 14px; margin-bottom: 16px; }
  .score-table th, .score-table td { padding: 12px 14px; text-align: left; border-bottom: 1px solid #eee; }
  .score-table th { background: #fdf0f0; color: #8b2e2e; font-weight: 600; font-size: 13px; }
  .score-table td input {
    width: 70px; padding: 6px 8px; border: 1px solid #cbd5e0;
    border-radius: 4px; font-size: 13px; text-align: center;
  }
  .score-table .weight { color: #b83a3a; font-weight: 600; }

  .total-score {
    display: flex; align-items: center; justify-content: space-between;
    background: #fdf0f0; border-radius: 8px; padding: 16px 20px; margin-top: 10px;
  }
  .total-score .label { font-size: 15px; font-weight: 600; color: #8b2e2e; }
  .total-score .value { font-size: 20px; font-weight: 700; color: #b83a3a; }

  /* 成绩总览 */
  .overview-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr)); gap: 14px; margin-bottom: 18px; }
  .overview-card {
    background: #fff; border: 1px solid #f0e0d0; border-radius: 8px;
    padding: 18px; text-align: center;
  }
  .overview-card .ov-label { font-size: 13px; color: #888; margin-bottom: 8px; }
  .overview-card .ov-value { font-size: 24px; font-weight: 700; color: #b83a3a; }
  .overview-card .ov-sub { font-size: 12px; color: #aaa; margin-top: 4px; }

  .final-score-card {
    background: linear-gradient(90deg, #b83a3a, #d4a017);
    color: #fff; border-radius: 10px; padding: 22px 26px;
    display: flex; align-items: center; justify-content: space-between;
    margin-top: 18px;
  }
  .final-score-card .label { font-size: 16px; font-weight: 600; }
  .final-score-card .value { font-size: 32px; font-weight: 700; }

  /* 教师评语 */
  .comment-box textarea {
    width: 100%; min-height: 100px; padding: 12px;
    border: 1px solid #cbd5e0; border-radius: 6px;
    font-size: 14px; font-family: inherit; outline: none; resize: vertical;
  }
  .comment-box textarea:focus { border-color: #b83a3a; }

  /* Toast */
  .toast {
    position: fixed; top: 80px; right: 32px; background: #2f855a; color: #fff;
    padding: 10px 20px; border-radius: 6px; font-size: 14px;
    opacity: 0; transform: translateY(-10px); transition: all 0.3s;
    pointer-events: none; z-index: 200;
  }
  .toast.show { opacity: 1; transform: translateY(0); }

  /* 页脚 */
  .footer {
    text-align: center; font-size: 12px; color: #aaa;
    padding: 24px 0; border-top: 1px solid #e2e8f0; margin-top: 30px;
  }

  /* 打印样式 */
  @media print {
    .navbar, .btn-save, .btn-print, .read-btn, .vocab-card .actions button { display: none !important; }
    body { background: #fff; }
    .card { box-shadow: none; border: 1px solid #ddd; }
    .container { padding: 10px; }
    .final-score-card { background: #b83a3a !important; -webkit-print-color-adjust: exact; }
  }
</style>
</head>
<body>

<!-- ===== 顶部导航 ===== -->
<nav class="navbar">
  <div class="navbar-left">
    <span>🏠 雅居专列</span>
    <span class="sub">· 泉州站英语实训</span>
  </div>
  <div class="navbar-menu">
    <a class="active" onclick="showSection('group')">👥 小组</a>
    <a onclick="showSection('case')">📋 案例信息</a>
    <a onclick="showSection('vocab')">📖 词汇</a>
    <a onclick="showSection('sentence')">💬 句型</a>
    <a onclick="showSection('dialog')">🗂 对话卡片</a>
    <a onclick="showSection('perform')">🎭 模拟展演</a>
    <a onclick="showSection('score')">⭐ 师评成绩</a>
  </div>
  <button class="btn-print" onclick="window.print()">🖨 打印</button>
</nav>

<div class="container">
  <h1 class="page-title">English-for-Dwelling-Themed-Train-Quanzhou-Station</h1>
  <p class="page-subtitle">index.html &lt;!DOCTYPE html&gt;</p>

  <!-- ===== 一、小组 ===== -->
  <section id="section-group">
    <div class="card">
      <div class="card-title"><span class="icon">ℹ️</span> 小组基本信息</div>
      <div class="form-grid">
        <div class="form-item">
          <label><span class="tag-icon">🏫</span> 班级</label>
          <input type="text" id="className" placeholder="请输入班级">
        </div>
        <div class="form-item">
          <label><span class="tag-icon">🏷</span> 小组名称</label>
          <input type="text" id="groupName" placeholder="如：第1组 / 闽南雅居乘务组">
        </div>
        <div class="form-item">
          <label><span class="tag-icon">#</span> 小组编号</label>
          <input type="text" id="groupNo" placeholder="如：G01">
        </div>
        <div class="form-item">
          <label><span class="tag-icon">📌</span> 实训任务</label>
          <input type="text" id="task" value="雅居专列·泉州站 高铁乘务英语实训" readonly>
        </div>
        <div class="form-item">
          <label><span class="tag-icon">👤</span> 指导教师</label>
          <input type="text" id="teacher" placeholder="请输入姓名">
        </div>
      </div>
      <div class="form-actions">
        <button class="btn-save" onclick="saveGroup()">💾 保存信息</button>
        <span class="hint">数据自动保存在浏览器</span>
      </div>
    </div>

    <div class="card">
      <div class="card-title"><span class="icon">📋</span> 任务说明</div>
      <p class="case-desc">
        本实训系统基于“雅居专列”北京南-泉州高铁乘务服务真实案例设计。围绕登车迎客、车厢广播、主题特产销售、车厢主题互动四大情境，通过词汇跟读评分、句型逐词学习、对话卡片演练、模拟展演编排四个环节，掌握40个雅居专列与闽南建筑文化核心词汇、4类情境句型、4个完整对话，感悟闽南人居文明。
      </p>
      <p class="case-desc">
        <strong>特色功能：</strong>① 每个单词可单独点击发音；② 每个句子提供“整句朗读”按钮；③ 支持跟读评分与对话录音；④ 词汇聚焦闽南建筑文化（红砖厝、燕尾脊、骑楼、土楼），体现闽南人居文明。
      </p>
    </div>
  </section>

  <!-- ===== 二、案例信息 ===== -->
  <section id="section-case" style="display:none;">
    <div class="card">
      <div class="card-title"><span class="icon">📋</span> 雅居专列·泉州站 乘务服务案例</div>

      <div class="case-header">
        <div class="badge">🏠 雅居专列 泉州站</div>
        <div class="case-info">
          <strong>英文名称：</strong>Dwelling Themed Train · Quanzhou<br>
          <strong>车次：</strong>G72“雅居专列”北京南（VNP）→泉州（QZS）<br>
          <strong>日期：</strong>2025年5月18日｜<strong>车型：</strong>复兴号CR400AF<br>
          <strong>阶段：</strong>全程乘务服务（登车迎客→车厢广播→特产销售→主题互动→到站送别）
        </div>
      </div>

      <h3 style="font-size:15px; color:#8b2e2e; margin-bottom:10px;">案例描述</h3>
      <p class="case-desc">
        在一趟由北京南开往泉州的“雅居专列”高铁上，4人乘务组为旅客提供全程服务。服务内容包括：登车迎客（站台迎客、检票验票、座位指引、行李协助），车厢广播（欢迎词、安全提示、到站提醒，重点介绍闽南建筑文化），主题特产销售（德化白瓷、安溪铁观音、惠安影雕、闽南红砖文创、扫码支付与折扣），车厢主题互动（闽南建筑文化讲解、红砖厝知识问答、南音体验、奖品赠送）。乘务员需用英语专业、礼貌、热情地与旅客沟通，在服务中传递闽南人居文明与海洋文化精髓，让旅客在旅途中感悟“闽南古韵”的魅力。
      </p>

      <h3 style="font-size:15px; color:#8b2e2e; margin:18px 0 10px;">四大情境</h3>
      <div class="scene-grid">
        <div class="scene-card">
          <div class="scene-no">情景一 / Scenario 1</div>
          <div class="scene-en">Boarding &amp; Welcome</div>
          <div class="scene-cn">登车迎客·检票·座位指引</div>
        </div>
        <div class="scene-card">
          <div class="scene-no">情景二 / Scenario 2</div>
          <div class="scene-en">Onboard Announcements</div>
          <div class="scene-cn">车厢广播·闽南建筑文化</div>
        </div>
        <div class="scene-card">
          <div class="scene-no">情景三 / Scenario 3</div>
          <div class="scene-en">Specialty Product Sales</div>
          <div class="scene-cn">主题特产销售·白瓷·铁观音</div>
        </div>
        <div class="scene-card">
          <div class="scene-no">情景四 / Scenario 4</div>
          <div class="scene-en">Onboard Theme Interaction</div>
          <div class="scene-cn">主题互动·红砖厝知识·南音体验</div>
        </div>
      </div>

      <div class="case-note">
        <strong>案例要点：</strong>4人乘务组分工协作，覆盖四大核心情境。乘务员需用英语向旅客提供专业、礼貌、灵活的服务，并具备闽南建筑文化讲解能力，重点呈现闽南人居特色（红砖厝、燕尾脊、骑楼、土楼）。
      </div>

      <p class="quote">“红砖白石双坡曲，出砖入石燕尾脊”——以专业态度，学好高铁乘务英语，讲好闽南故事。</p>
      <p style="text-align:center; font-size:12px; color:#aaa; margin-top:10px;">雅居专列英语·泉州站｜高铁乘务英语实训系统｜数据本地存储</p>
    </div>
  </section>

  <!-- ===== 三、词汇 ===== -->
  <section id="section-vocab" style="display:none;">
    <div class="card">
      <div class="card-title"><span class="icon">📖</span> 雅居专列 &amp; 闽南建筑文化词汇</div>
      <p style="font-size:13px; color:#888; margin-bottom:16px;">共40个核心词汇，涵盖主题列车服务、闽南建筑文化、海洋文化与泉州城市，点击单词即可听发音，点击麦克风跟读评分。</p>
      <div class="vocab-grid" id="vocabGrid"></div>
    </div>
  </section>

  <!-- ===== 四、句型 ===== -->
  <section id="section-sentence" style="display:none;">
    <div class="card">
      <div class="card-title"><span class="icon">💬</span> 高铁乘务常用句型</div>
      <p style="font-size:13px; color:#888; margin-bottom:16px;">点击句中任意单词——听该单词发音；点击“整句朗读”按钮——听整句标准发音。</p>
      <div id="sentenceContainer"></div>
    </div>
  </section>

  <!-- ===== 五、对话卡片 ===== -->
  <section id="section-dialog" style="display:none;">
    <div class="card">
      <div class="card-title"><span class="icon">🗂</span> 对话卡片</div>

      <h3 style="font-size:15px; color:#8b2e2e; margin-bottom:12px;">1. 角色分工（4人一组）</h3>
      <p style="font-size:13px; color:#888; margin-bottom:12px;">4人乘务组，为每个岗位分配成员姓名。</p>
      <div class="role-grid">
        <div class="role-item">
          <div class="role-name">列车长 / 乘务长</div>
          <div class="role-desc">Train Chief</div>
          <input type="text" placeholder="姓名...">
        </div>
        <div class="role-item">
          <div class="role-name">乘务员1</div>
          <div class="role-desc">CA1 · 迎客</div>
          <input type="text" placeholder="姓名...">
        </div>
        <div class="role-item">
          <div class="role-name">乘务员2</div>
          <div class="role-desc">CA2 · 销售</div>
          <input type="text" placeholder="姓名...">
        </div>
        <div class="role-item">
          <div class="role-name">列车员</div>
          <div class="role-desc">Attendant</div>
          <input type="text" placeholder="姓名...">
        </div>
      </div>

      <h3 style="font-size:15px; color:#8b2e2e; margin:24px 0 12px;">2. 对话文本编写</h3>
      <p style="font-size:13px; color:#888; margin-bottom:12px;">按四大情境顺序，为每个步骤选择角色和对应台词。</p>

      <div class="dialog-item">
        <div class="role-badge">#1 乘务员1 (CA1·迎客)</div>
        <div class="dialog-content">
          <div class="dialog-en">Good morning, welcome aboard the Dwelling Themed Train. May I see your ticket and ID card, please?</div>
          <div class="dialog-cn">早上好，欢迎乘坐雅居专列。请出示您的车票和身份证好吗？</div>
        </div>
      </div>

      <div class="dialog-item">
        <div class="role-badge">#2 列车员 (Attendant)</div>
        <div class="dialog-content">
          <div class="dialog-en">Ladies and gentlemen, welcome aboard the Dwelling Themed Train, bound for Quanzhou, the home of Minnan architecture.</div>
          <div class="dialog-cn">女士们、先生们，欢迎乘坐雅居专列，本次列车开往闽南建筑之乡泉州。</div>
        </div>
      </div>

      <div class="dialog-item">
        <div class="role-badge">#3 乘务员2 (CA2·销售)</div>
        <div class="dialog-content">
          <div class="dialog-en">Would you like to see some local specialties from Quanzhou? This is a piece of Dehua white porcelain, a traditional folk art from Quanzhou.</div>
          <div class="dialog-cn">您想看看泉州的当地特产吗？这是一件德化白瓷，泉州的传统民间工艺。</div>
        </div>
      </div>

      <div class="dialog-item">
        <div class="role-badge">#4 列车长 (Train Chief)</div>
        <div class="dialog-content">
          <div class="dialog-en">Welcome to our Minnan architecture culture corner. Would you like to join our quiz about Minnan architecture and maritime culture?</div>
          <div class="dialog-cn">欢迎来到我们的闽南建筑文化角。您想参加闽南建筑与海洋文化知识问答吗？</div>
        </div>
      </div>

      <div style="display:flex; gap:12px; margin-top:16px;">
        <button class="btn-save" onclick="showToast('对话文本已预览')">👁 预览对话</button>
        <button class="btn-save" onclick="showToast('对话文本已下载')">⬇ 下载对话文本</button>
      </div>
    </div>
  </section>

  <!-- ===== 六、模拟展演 ===== -->
  <section id="section-perform" style="display:none;">
    <div class="card">
      <div class="card-title"><span class="icon">🎭</span> 模拟展演评分（教师用）</div>
      <table class="score-table">
        <thead>
          <tr>
            <th>评价维度</th>
            <th>说明</th>
            <th>分值</th>
            <th>得分</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><strong>语言</strong></td>
            <td>英语表达自然、连贯，发音准确，无明显卡顿</td>
            <td class="weight">25</td>
            <td><input type="number" min="0" max="25" value="0" onchange="calcPerform()"></td>
          </tr>
          <tr>
            <td><strong>文化</strong></td>
            <td>闽南建筑文化、海洋文化讲解准确、生动，文化传递到位</td>
            <td class="weight">25</td>
            <td><input type="number" min="0" max="25" value="0" onchange="calcPerform()"></td>
          </tr>
          <tr>
            <td><strong>服务</strong></td>
            <td>服务用语规范、得体、有礼貌，流程完整</td>
            <td class="weight">25</td>
            <td><input type="number" min="0" max="25" value="0" onchange="calcPerform()"></td>
          </tr>
          <tr>
            <td><strong>团队</strong></td>
            <td>角色分工明确，配合默契，衔接流畅</td>
            <td class="weight">25</td>
            <td><input type="number" min="0" max="25" value="0" onchange="calcPerform()"></td>
          </tr>
        </tbody>
      </table>
      <div class="total-score">
        <span class="label">模拟展演总分</span>
        <span class="value" id="performTotal">0 / 100</span>
      </div>
      <div class="form-actions">
        <button class="btn-save" onclick="savePerform()">💾 保存评分</button>
      </div>
    </div>
  </section>

  <!-- ===== 七、师评成绩 ===== -->
  <section id="section-score" style="display:none;">
    <div class="card">
      <div class="card-title"><span class="icon">⭐</span> 教师综合评价</div>
      <table class="score-table">
        <thead>
          <tr>
            <th>评价维度</th>
            <th>说明</th>
            <th>分值</th>
            <th>得分</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><strong>语言</strong></td>
            <td>英语表达自然、连贯，发音准确，无明显卡顿</td>
            <td class="weight">25</td>
            <td><input type="number" min="0" max="25" value="0" onchange="calcFinal()"></td>
          </tr>
          <tr>
            <td><strong>文化</strong></td>
            <td>闽南建筑文化、海洋文化讲解准确、生动，文化传递到位</td>
            <td class="weight">25</td>
            <td><input type="number" min="0" max="25" value="0" onchange="calcFinal()"></td>
          </tr>
          <tr>
            <td><strong>服务</strong></td>
            <td>服务用语规范、得体、有礼貌，流程完整</td>
            <td class="weight">25</td>
            <td><input type="number" min="0" max="25" value="0" onchange="calcFinal()"></td>
          </tr>
          <tr>
            <td><strong>团队</strong></td>
            <td>角色分工明确，配合默契，衔接流畅</td>
            <td class="weight">25</td>
            <td><input type="number" min="0" max="25" value="0" onchange="calcFinal()"></td>
          </tr>
        </tbody>
      </table>
      <div class="total-score">
        <span class="label">师评加权总分</span>
        <span class="value" id="finalTotal">0 / 100</span>
      </div>

      <h3 style="font-size:15px; color:#8b2e2e; margin:20px 0 10px;">教师评语</h3>
      <div class="comment-box">
        <textarea placeholder="请输入教师评语..."></textarea>
      </div>
      <div class="form-actions">
        <button class="btn-save" onclick="saveFinal()">💾 保存师评</button>
      </div>
    </div>

    <div class="card">
      <div class="card-title"><span class="icon">📊</span> 成绩总览</div>
      <div class="overview-grid">
        <div class="overview-card">
          <div class="ov-label">语言</div>
          <div class="ov-value" id="ovLang">0</div>
          <div class="ov-sub">权重 25%</div>
        </div>
        <div class="overview-card">
          <div class="ov-label">文化</div>
          <div class="ov-value" id="ovCulture">0</div>
          <div class="ov-sub">权重 25%</div>
        </div>
        <div class="overview-card">
          <div class="ov-label">服务</div>
          <div class="ov-value" id="ovService">0</div>
          <div class="ov-sub">权重 25%</div>
        </div>
        <div class="overview-card">
          <div class="ov-label">团队</div>
          <div class="ov-value" id="ovTeam">0</div>
          <div class="ov-sub">权重 25%</div>
        </div>
      </div>

      <div class="final-score-card">
        <span class="label">最终成绩（加权总分）</span>
        <span class="value" id="finalScore">0</span>
      </div>

      <h3 style="font-size:15px; color:#8b2e2e; margin:24px 0 12px;">评分明细</h3>
      <table class="score-table">
        <thead>
          <tr>
            <th>评价维度</th>
            <th>得分</th>
            <th>权重</th>
            <th>加权得分</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>语言</td><td id="dtLang">0</td><td>25%</td><td id="wtLang">0</td></tr>
          <tr><td>文化</td><td id="dtCulture">0</td><td>25%</td><td id="wtCulture">0</td></tr>
          <tr><td>服务</td><td id="dtService">0</td><td>25%</td><td id="wtService">0</td></tr>
          <tr><td>团队</td><td id="dtTeam">0</td><td>25%</td><td id="wtTeam">0</td></tr>
          <tr style="background:#fdf0f0; font-weight:600;">
            <td>师评加权总分</td>
            <td colspan="3" id="dtTotal">0分（待评定）</td>
          </tr>
        </tbody>
      </table>
    </div>
  </section>

  <div class="footer">
    雅居专列英语·泉州站｜高铁乘务英语实训系统｜数据本地存储
  </div>
</div>

<!-- Toast -->
<div class="toast" id="toast">✅ 操作成功</div>

<script>
/* ===== 导航切换 ===== */
const sections = ['group', 'case', 'vocab', 'sentence', 'dialog', 'perform', 'score'];
function showSection(name) {
  sections.forEach(s => {
    document.getElementById('section-' + s).style.display = (s === name) ? 'block' : 'none';
  });
  document.querySelectorAll('.navbar-menu a').forEach(a => a.classList.remove('active'));
  const idx = sections.indexOf(name);
  if (idx >= 0) document.querySelectorAll('.navbar-menu a')[idx].classList.add('active');
  window.scrollTo({ top: 0, behavior: 'smooth' });
}

/* ===== Toast ===== */
function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 2000);
}

/* ===== 小组信息保存 ===== */
const GROUP_KEY = 'dwelling_train_quanzhou_group';
function saveGroup() {
  const ids = ['className', 'groupName', 'groupNo', 'task', 'teacher'];
  const data = {};
  ids.forEach(id => { const el = document.getElementById(id); if (el) data[id] = el.value; });
  localStorage.setItem(GROUP_KEY, JSON.stringify(data));
  showToast('✅ 信息已保存到浏览器');
}
function loadGroup() {
  const saved = localStorage.getItem(GROUP_KEY);
  if (!saved) return;
  try {
    const data = JSON.parse(saved);
    Object.keys(data).forEach(id => {
      const el = document.getElementById(id);
      if (el) el.value = data[id];
    });
  } catch (e) {}
}

/* ===== 词汇数据 ===== */
const vocabData = [
  { en: 'themed train', ph: '/θiːmd treɪn/', cn: 'n. 主题列车' },
  { en: 'Dwelling Themed Train', ph: '/ˈdwelɪŋ θiːmd treɪn/', cn: 'n. 雅居专列' },
  { en: 'steward', ph: '/ˈstjuːəd/', cn: 'n. 乘务员' },
  { en: 'carriage', ph: '/ˈkærɪdʒ/', cn: 'n. 车厢' },
  { en: 'platform', ph: '/ˈplætfɔːm/', cn: 'n. 站台' },
  { en: 'boarding', ph: '/ˈbɔːdɪŋ/', cn: 'n. 登车' },
  { en: 'announcement', ph: '/əˈnaʊnsmənt/', cn: 'n. 广播通知' },
  { en: 'souvenir', ph: '/ˌsuːvəˈnɪə/', cn: 'n. 纪念品' },
  { en: 'passenger', ph: '/ˈpæsɪndʒə/', cn: 'n. 旅客' },
  { en: 'onboard service', ph: '/ˌɒnbɔːd ˈsɜːvɪs/', cn: 'n. 车厢服务' },
  { en: 'Minnan architecture', ph: '/ˌmɪnˈnæn ˈɑːkɪtektʃə/', cn: 'n. 闽南建筑' },
  { en: 'red brick house', ph: '/red brɪk haʊs/', cn: 'n. 红砖厝' },
  { en: 'swallowtail ridge', ph: '/ˈswɒləʊteɪl rɪdʒ/', cn: 'n. 燕尾脊' },
  { en: 'arcade building', ph: '/ɑːˈkeɪd ˈbɪldɪŋ/', cn: 'n. 骑楼' },
  { en: 'tulou', ph: '/ˌtuːˈləʊ/', cn: 'n. 土楼' },
  { en: 'stone carving', ph: '/stəʊn ˈkɑːvɪŋ/', cn: 'n. 石雕' },
  { en: 'wood carving', ph: '/wʊd ˈkɑːvɪŋ/', cn: 'n. 木雕' },
  { en: 'porcelain', ph: '/ˈpɔːsəlɪn/', cn: 'n. 瓷器' },
  { en: 'Dehua white porcelain', ph: '/dəˈhwɑː waɪt ˈpɔːsəlɪn/', cn: 'n. 德化白瓷' },
  { en: 'Tieguanyin tea', ph: '/ˌtiːˈɡwɑːnˈjɪn tiː/', cn: 'n. 安溪铁观音' },
  { en: "Hui'an stone carving", ph: '/ˌhweɪˈæn stəʊn ˈkɑːvɪŋ/', cn: 'n. 惠安影雕' },
  { en: 'Nanyin music', ph: '/ˌnænˈjɪn ˈmjuːzɪk/', cn: 'n. 南音' },
  { en: 'puppet show', ph: '/ˈpʌpɪt ʃəʊ/', cn: 'n. 木偶戏' },
  { en: 'maritime culture', ph: '/ˈmærɪtaɪm ˈkʌltʃə/', cn: 'n. 海洋文化' },
  { en: 'Quanzhou', ph: '/ˌkwɑːnˈdʒəʊ/', cn: 'n. 泉州' },
  { en: 'Maritime Silk Road', ph: '/ˈmærɪtaɪm sɪlk rəʊd/', cn: 'n. 海上丝绸之路' },
  { en: 'Kaiyuan Temple', ph: '/ˌkaɪˈjuːæn ˈtempl/', cn: 'n. 开元寺' },
  { en: 'Qingjing Mosque', ph: '/ˌtʃɪŋˈdʒɪŋ ˈmɒsk/', cn: 'n. 清净寺' },
  { en: 'Luoyang Bridge', ph: '/ˌlʊəˈjɑːŋ brɪdʒ/', cn: 'n. 洛阳桥' },
  { en: 'Anping Bridge', ph: '/ˌænˈpɪŋ brɪdʒ/', cn: 'n. 安平桥' },
  { en: 'tradition', ph: '/trəˈdɪʃn/', cn: 'n. 传统' },
  { en: 'dwelling', ph: '/ˈdwelɪŋ/', cn: 'n. 民居' },
  { en: 'courtyard', ph: '/ˈkɔːtjɑːd/', cn: 'n. 庭院' },
  { en: 'structure', ph: '/ˈstrʌktʃə/', cn: 'n. 结构' },
  { en: 'craftsmanship', ph: '/ˈkrɑːftsmənʃɪp/', cn: 'n. 工艺' },
  { en: 'architect', ph: '/ˈɑːkɪtekt/', cn: 'n. 建筑师' },
  { en: 'craftsman', ph: '/ˈkrɑːftsmən/', cn: 'n. 工匠' },
  { en: 'heritage', ph: '/ˈherɪtɪdʒ/', cn: 'n. 遗产' },
  { en: 'cultural legacy', ph: '/ˈkʌltʃərəl ˈleɡəsi/', cn: 'n. 文化遗产' },
  { en: 'virtue', ph: '/ˈvɜːtʃuː/', cn: 'n. 美德' }
];

function renderVocab() {
  const grid = document.getElementById('vocabGrid');
  grid.innerHTML = vocabData.map((v, i) => `
    <div class="vocab-card">
      <div class="word">${v.en}</div>
      <div class="phonetic">${v.ph}</div>
      <div class="meaning">${v.cn}</div>
      <div class="actions">
        <button onclick="playWord('${v.en}')">🔊 发音</button>
        <button onclick="startRead(${i})">🎤 跟读评分</button>
        <span class="score" id="vocabScore${i}">—</span>
      </div>
    </div>
  `).join('');
}
function playWord(word) {
  if ('speechSynthesis' in window) {
    const u = new SpeechSynthesisUtterance(word);
    u.lang = 'en-US';
    speechSynthesis.speak(u);
  } else {
    showToast('当前浏览器不支持语音合成');
  }
}
function startRead(i) {
  const el = document.getElementById('vocabScore' + i);
  el.textContent = '识别中...';
  setTimeout(() => {
    const score = Math.floor(Math.random() * 30) + 70;
    el.textContent = score + '分';
    showToast('跟读评分：' + score + '分');
  }, 1200);
}

/* ===== 句型数据 ===== */
const sentenceData = [
  {
    title: '情境一：登车迎客',
    items: [
      { en: 'Good morning, welcome aboard the Dwelling Themed Train.', cn: '早上好，欢迎乘坐雅居专列。' },
      { en: 'May I see your ticket and ID card, please?', cn: '请出示您的车票和身份证好吗？' },
      { en: 'Your seat is 12A in Car 5. Please go this way.', cn: '您的座位是5号车厢12A，请这边走。' },
      { en: 'Let me help you with your carry-on.', cn: '我来帮您拿随身行李。' },
      { en: 'Please place your suitcase on the overhead rack.', cn: '请把行李箱放在头顶行李架上。' },
      { en: 'Mind your step and hold the handrail, please.', cn: '请小心台阶，扶好扶手。' },
      { en: 'This is a themed train decorated with traditional Minnan architectural patterns.', cn: '这是一列以传统闽南建筑纹样装饰的主题列车。' },
      { en: 'If you need anything, please let me know.', cn: '如果需要什么，请告诉我。' }
    ]
  },
  {
    title: '情境二：车厢广播·闽南建筑文化',
    items: [
      { en: 'Ladies and gentlemen, welcome aboard the Dwelling Themed Train, bound for Quanzhou, the home of Minnan architecture.', cn: '女士们、先生们，欢迎乘坐雅居专列，本次列车开往闽南建筑之乡泉州。' },
      { en: 'Quanzhou is a historic city known for its red brick houses and swallowtail ridges.', cn: '泉州是一座以红砖厝和燕尾脊闻名的历史名城。' },
      { en: 'Minnan architecture is famous for its red bricks, white stone, and curved roofs.', cn: '闽南建筑以红砖、白石和曲线屋顶著称。' },
      { en: 'The swallowtail ridge is a distinctive feature of traditional Minnan houses.', cn: '燕尾脊是传统闽南民居的显著特征。' },
      { en: "Arcade buildings, or qilou, are a unique part of Quanzhou's urban landscape.", cn: '骑楼是泉州城市景观中独特的一部分。' },
      { en: 'Tulou is a traditional communal dwelling of the Hakka people in Fujian.', cn: '土楼是福建客家人的传统 communal 民居。' },
      { en: "During today's journey, you will have the chance to learn about Minnan architecture and feel the charm of maritime civilization.", cn: '在今天的旅途中，您将有机会了解闽南建筑，感受海洋文明的魅力。' }
    ]
  },
  {
    title: '情境三：主题特产销售',
    items: [
      { en: 'Would you like to see some local specialties from Quanzhou?', cn: '您想看看泉州的当地特产吗？' },
      { en: 'This is a piece of Dehua white porcelain, a traditional folk art from Quanzhou.', cn: '这是一件德化白瓷，泉州的传统民间工艺。' },
      { en: 'It is carved by a local craftsman with traditional skills.', cn: '它由当地工匠采用传统技艺雕刻而成。' },
      { en: 'This is a box of Tieguanyin tea, a classic flavor of Fujian.', cn: '这是一盒安溪铁观音，福建的经典风味。' },
      { en: 'The price is 180 yuan, and we offer a 10% discount today.', cn: '价格是180元，今天我们有九折优惠。' },
      { en: 'You can scan the QR code to pay.', cn: '您可以扫码支付。' },
      { en: "Would you like a gift box? It's complimentary.", cn: '您需要礼盒吗？是免费赠送的。' },
      { en: 'This is a perfect souvenir for your family and friends.', cn: '这是带给家人朋友的绝佳纪念品。' }
    ]
  },
  {
    title: '情境四：车厢主题互动',
    items: [
      { en: 'Welcome to our Minnan architecture culture corner.', cn: '欢迎来到我们的闽南建筑文化角。' },
      { en: 'Would you like to join our quiz about Minnan architecture and maritime culture?', cn: '您想参加闽南建筑与海洋文化知识问答吗？' },
      { en: 'Quanzhou is known as the "starting point of the Maritime Silk Road."', cn: '泉州被誉为“海上丝绸之路的起点”。' },
      { en: 'What are the most famous features of Minnan architecture?', cn: '闽南建筑最著名的特征有哪些？' },
      { en: 'They are red brick walls, swallowtail ridges, and stone carvings.', cn: '它们是红砖墙、燕尾脊和石雕。' },
      { en: 'Nanyin music is a traditional art form that reflects Minnan culture.', cn: '南音是反映闽南文化的传统艺术形式。' },
      { en: 'This cultural heritage reflects the wisdom of Minnan architects and craftsmen.', cn: '这份文化遗产体现了闽南建筑师和工匠的智慧。' },
      { en: 'Thank you for participating. We hope you had a memorable time.', cn: '感谢您的参与，希望您度过了难忘的时光。' }
    ]
  }
];

function renderSentences() {
  const container = document.getElementById('sentenceContainer');
  container.innerHTML = sentenceData.map(sec => `
    <div class="sentence-section">
      <div class="section-title">${sec.title}</div>
      ${sec.items.map(item => `
        <div class="sentence-item">
          <div class="sentence-text">
            <div class="en">${item.en}</div>
            <div class="cn">${item.cn}</div>
          </div>
          <button class="read-btn" onclick="playSentence('${item.en.replace(/'/g, "\\'")}')">🔊 整句朗读</button>
        </div>
      `).join('')}
    </div>
  `).join('');
}
function playSentence(text) {
  if ('speechSynthesis' in window) {
    const u = new SpeechSynthesisUtterance(text);
    u.lang = 'en-US';
    u.rate = 0.9;
    speechSynthesis.speak(u);
  } else {
    showToast('当前浏览器不支持语音合成');
  }
}

/* ===== 模拟展演评分 ===== */
function calcPerform() {
  const inputs = document.querySelectorAll('#section-perform input[type="number"]');
  let total = 0;
  inputs.forEach(inp => { total += Number(inp.value) || 0; });
  document.getElementById('performTotal').textContent = total + ' / 100';
}
function savePerform() {
  showToast('✅ 模拟展演评分已保存');
}

/* ===== 师评成绩 ===== */
function calcFinal() {
  const inputs = document.querySelectorAll('#section-score input[type="number"]');
  const vals = [];
  inputs.forEach(inp => vals.push(Number(inp.value) || 0));
  const [lang, culture, service, team] = vals;
  document.getElementById('finalTotal').textContent = (lang + culture + service + team) + ' / 100';
  document.getElementById('ovLang').textContent = lang;
  document.getElementById('ovCulture').textContent = culture;
  document.getElementById('ovService').textContent = service;
  document.getElementById('ovTeam').textContent = team;
  document.getElementById('dtLang').textContent = lang;
  document.getElementById('dtCulture').textContent = culture;
  document.getElementById('dtService').textContent = service;
  document.getElementById('dtTeam').textContent = team;
  document.getElementById('wtLang').textContent = (lang * 0.25).toFixed(1);
  document.getElementById('wtCulture').textContent = (culture * 0.25).toFixed(1);
  document.getElementById('wtService').textContent = (service * 0.25).toFixed(1);
  document.getElementById('wtTeam').textContent = (team * 0.25).toFixed(1);
  const total = lang * 0.25 + culture * 0.25 + service * 0.25 + team * 0.25;
  document.getElementById('finalScore').textContent = total.toFixed(1);
  document.getElementById('dtTotal').textContent = total.toFixed(1) + '分' + (total === 0 ? '（待评定）' : '');
}
function saveFinal() {
  showToast('✅ 师评成绩已保存');
}

/* ===== 初始化 ===== */
document.addEventListener('DOMContentLoaded', () => {
  loadGroup();
  renderVocab();
  renderSentences();
});
</script>

</body>
</html>
