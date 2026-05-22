<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="theme-color" content="#000000">
<title>深度共鸣 · 一项关于内在联想的匿名调查</title>
<style>
  :root {
    --bg: #fafaf8;
    --fg: #1a1a1a;
    --accent: #2a5d8f;
    --border: #d4d4d4;
    --muted: #888;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }
  html, body {
    min-height: 100%;
    font-family: -apple-system, "PingFang SC", "Microsoft YaHei", sans-serif;
    background: var(--bg);
    color: var(--fg);
    overflow-x: hidden;
    transition: background 1.5s, color 1.5s;
    line-height: 1.7;
    -webkit-user-select: none;
    user-select: none;
  }
  input, textarea { -webkit-user-select: text; user-select: text; }

  body.corrupt {
    --bg: #1a0808;
    --fg: #d4b0b0;
    --accent: #8b1a1a;
    --border: #3a1010;
    --muted: #6a4040;
  }
  body.deep-corrupt {
    --bg: #050000;
    --fg: #ff3a3a;
    --accent: #ff0033;
    --border: #5a0000;
    --muted: #804040;
  }
  body.abyss {
    --bg: #000;
    --fg: #ff5050;
  }

  .container {
    max-width: 600px;
    margin: 0 auto;
    padding: 30px 20px 100px;
  }

  /* ========== 开场预警页 ========== */
  .intro-screen {
    max-width: 640px;
    margin: 0 auto;
    padding: 30px 22px 60px;
    color: #1a1a1a;
  }
  .intro-screen h1 {
    font-size: 22px;
    font-weight: 600;
    margin-bottom: 8px;
    line-height: 1.4;
  }
  .intro-screen .game-subtitle {
    color: #888;
    font-size: 13px;
    margin-bottom: 30px;
  }
  .intro-screen h2 {
    font-size: 17px;
    margin: 28px 0 12px;
    padding-left: 10px;
    border-left: 3px solid #c41e3a;
  }
  .intro-screen p, .intro-screen li {
    font-size: 14px;
    line-height: 1.85;
    color: #333;
  }
  .intro-screen ul { padding-left: 20px; margin: 8px 0; }
  .intro-screen ul li { margin-bottom: 4px; }
  .intro-screen .aside {
    color: #999;
    font-size: 13px;
  }
  .intro-screen .warning-box {
    background: #fff5f5;
    border: 1px solid #ffd4d4;
    padding: 14px;
    border-radius: 6px;
    margin: 14px 0;
  }
  .intro-screen .warning-box strong { color: #c41e3a; }
  .intro-screen details {
    margin: 16px 0;
    background: #f4f4f0;
    border-radius: 6px;
    padding: 4px 14px;
  }
  .intro-screen details summary {
    padding: 12px 4px;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    color: #555;
  }
  .intro-screen details[open] summary { color: #1a1a1a; }
  .intro-screen details ul { margin: 8px 0 16px; }
  .intro-screen .author-box {
    background: #f4f4f0;
    padding: 16px;
    border-radius: 6px;
    margin: 24px 0;
    font-size: 14px;
    line-height: 2;
  }
  .intro-screen .thanks {
    font-size: 13.5px;
    color: #666;
    line-height: 2;
    background: #fafaf8;
    padding: 18px;
    border-radius: 6px;
    margin: 24px 0;
    white-space: pre-line;
  }
  .intro-screen .start-btn {
    display: block;
    width: 100%;
    padding: 16px;
    background: #1a1a1a;
    color: #fff;
    border: none;
    font-size: 16px;
    font-family: inherit;
    border-radius: 6px;
    margin-top: 30px;
    cursor: pointer;
  }
  .intro-screen .start-btn:active { background: #000; }

  /* ========== 问题样式 ========== */
  h1.title {
    font-size: 24px;
    margin-bottom: 6px;
    font-weight: 500;
  }
  .subtitle {
    color: var(--muted);
    margin-bottom: 32px;
    font-size: 13px;
  }

  .question {
    margin-bottom: 28px;
    opacity: 0;
    transform: translateY(15px);
    transition: opacity 0.6s, transform 0.6s;
  }
  .question.show { opacity: 1; transform: translateY(0); }

  label.q-label {
    display: block;
    font-size: 16px;
    margin-bottom: 12px;
    line-height: 1.65;
  }
  .q-num {
    color: var(--accent);
    font-weight: 600;
    margin-right: 6px;
  }

  input[type="text"], input[type="number"], textarea {
    width: 100%;
    padding: 12px;
    border: 1px solid var(--border);
    background: transparent;
    color: var(--fg);
    font-size: 16px;
    font-family: inherit;
    outline: none;
    border-radius: 4px;
    transition: border-color 0.3s;
    -webkit-appearance: none;
  }
  input:focus, textarea:focus { border-color: var(--accent); }
  textarea { resize: vertical; min-height: 90px; }

  .options label {
    display: flex;
    align-items: flex-start;
    padding: 10px 0;
    font-size: 15.5px;
    line-height: 1.6;
    cursor: pointer;
  }
  .options input { margin-right: 10px; margin-top: 4px; transform: scale(1.2); flex-shrink: 0; }

  button.next-btn {
    background: var(--accent);
    color: #fff;
    border: none;
    padding: 12px 28px;
    font-size: 15px;
    cursor: pointer;
    margin-top: 12px;
    border-radius: 4px;
    font-family: inherit;
    transition: opacity 0.3s, transform 0.2s;
    min-height: 44px;
  }
  button.next-btn:active { transform: scale(0.97); }
  button.next-btn:disabled { opacity: 0.4; }

  /* ========== 鬼台词 ========== */
  .ghost-line {
    color: #c41e3a;
    font-style: italic;
    padding: 14px 18px;
    border-left: 2px solid #c41e3a;
    margin: 18px 0;
    background: rgba(196, 30, 58, 0.06);
    white-space: pre-wrap;
    font-size: 15.5px;
    line-height: 1.85;
  }
  body.corrupt .ghost-line {
    color: #ff5050;
    border-color: #ff0033;
    background: rgba(255, 0, 51, 0.08);
  }
  body.deep-corrupt .ghost-line {
    color: #ff7070;
    background: rgba(255, 0, 51, 0.12);
    box-shadow: 0 0 25px rgba(255, 0, 0, 0.18);
  }

  .ghost-handwrite {
    font-family: "Songti SC", "STSong", "Kaiti SC", "STKaiti", "楷体", cursive;
    font-style: italic;
    color: #d4b0b0;
    text-align: center;
    font-size: 19px;
    line-height: 2.2;
    padding: 60px 20px;
    white-space: pre-line;
    letter-spacing: 1px;
  }

  /* ========== 故障/抖动效果 ========== */
  .glitch {
    animation: glitch 0.3s infinite;
  }
  @keyframes glitch {
    0%, 100% { transform: translate(0); text-shadow: none; }
    25% { transform: translate(-1px, 1px); text-shadow: 1px 0 #ff0033, -1px 0 #00d4ff; }
    50% { transform: translate(1px, -1px); }
    75% { transform: translate(-1px, -1px); text-shadow: -1px 0 #ff0033, 1px 0 #00d4ff; }
  }
  body.flicker { animation: flicker 0.15s; }
  @keyframes flicker {
    0%, 100% { filter: none; }
    50% { filter: invert(1) hue-rotate(180deg); }
  }
  .shake { animation: shake 0.4s infinite; }
  @keyframes shake {
    0%, 100% { transform: translate(0,0); }
    25% { transform: translate(-3px, 2px); }
    50% { transform: translate(3px, -2px); }
    75% { transform: translate(-2px, -3px); }
  }
  .word-pop {
    display: inline-block;
    animation: wordPop 0.3s;
  }
  @keyframes wordPop {
    0% { transform: scale(1); }
    50% { transform: scale(1.4); color: #ff0033; }
    100% { transform: scale(1); }
  }

  .typing::after {
    content: "▋";
    animation: blink 0.8s infinite;
  }
  @keyframes blink { 50% { opacity: 0; } }

  /* ========== 进度条 ========== */
  .progress {
    position: fixed;
    top: 0; left: 0;
    height: 2px;
    background: var(--accent);
    transition: width 0.5s;
    z-index: 100;
    width: 0;
  }

  /* ========== 暗角 ========== */
  .vignette {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 30;
    box-shadow: inset 0 0 0 0 rgba(0,0,0,0);
    transition: box-shadow 2s;
  }
  body.corrupt .vignette { box-shadow: inset 0 0 130px 25px rgba(80, 0, 0, 0.55); }
  body.deep-corrupt .vignette { box-shadow: inset 0 0 220px 50px rgba(120, 0, 0, 0.85); }

  /* 亮度滤镜 */
  body.dim-1 { filter: brightness(0.75); transition: filter 1.5s; }
  body.dim-2 { filter: brightness(0.55); transition: filter 1.5s; }
  body.dim-3 { filter: brightness(0.4); transition: filter 1.5s; }

  /* ========== 漂浮文字 ========== */
  .floating-text {
    position: fixed;
    color: #ff0033;
    font-size: 13px;
    pointer-events: none;
    opacity: 0;
    z-index: 50;
    text-shadow: 0 0 10px rgba(255,0,0,0.9);
    animation: floatFade 4s forwards;
    max-width: 60vw;
    font-style: italic;
  }
  @keyframes floatFade {
    0% { opacity: 0; transform: translateY(15px); }
    25% { opacity: 0.9; }
    100% { opacity: 0; transform: translateY(-30px); }
  }

  /* ========== 屏息倒计时 ========== */
  .countdown-overlay {
    position: fixed;
    inset: 0;
    background: radial-gradient(circle, transparent 60%, rgba(40, 0, 0, 0.4) 100%);
    z-index: 200;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    transition: background 0.8s;
  }
  .countdown-overlay .hint {
    color: #888;
    font-size: 14px;
    letter-spacing: 4px;
    margin-bottom: 30px;
    text-transform: uppercase;
  }
  .countdown-overlay .count {
    font-size: 140px;
    font-weight: 200;
    color: #fff;
    transition: color 0.5s, text-shadow 0.5s;
    font-family: "Helvetica Neue", sans-serif;
  }
  .countdown-overlay .count.warn { color: #ffaa00; text-shadow: 0 0 30px rgba(255,170,0,0.6); }
  .countdown-overlay .count.danger { color: #ff0033; text-shadow: 0 0 50px rgba(255,0,51,0.9); }
  .countdown-overlay .label {
    color: #aaa;
    font-size: 16px;
    margin-top: 20px;
    letter-spacing: 2px;
  }
  .countdown-flash {
    background: #fff !important;
    transition: background 0.05s !important;
  }

  /* ========== 献祭框 ========== */
  .sacrifice-box {
    position: fixed;
    bottom: 14px;
    right: 14px;
    width: 180px;
    background: rgba(0, 0, 0, 0.85);
    border: 1px solid #c41e3a;
    border-radius: 8px;
    padding: 10px;
    z-index: 90;
    box-shadow: 0 0 20px rgba(196, 30, 58, 0.4);
    display: none;
  }
  .sacrifice-box.show { display: block; animation: sacrificeIn 0.6s; }
  @keyframes sacrificeIn {
    0% { opacity: 0; transform: translateY(20px); }
    100% { opacity: 1; transform: translateY(0); }
  }
  .sacrifice-box .s-title {
    color: #ff5050;
    font-size: 13px;
    font-weight: 600;
    text-align: center;
    margin-bottom: 6px;
    letter-spacing: 4px;
    font-family: "Songti SC", "Kaiti SC", cursive;
  }
  .sacrifice-box .s-hint {
    color: #888;
    font-size: 10px;
    text-align: center;
    margin-bottom: 6px;
  }
  .sacrifice-box input {
    width: 100%;
    padding: 6px 8px;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid #5a0000;
    color: #ff7070;
    font-size: 13px;
    border-radius: 4px;
    outline: none;
  }
  .sacrifice-box input::placeholder { color: #5a3030; }
  .sacrifice-box.flash {
    animation: sacrificeFlash 0.6s;
  }
  @keyframes sacrificeFlash {
    0%, 100% { box-shadow: 0 0 20px rgba(196, 30, 58, 0.4); }
    50% { box-shadow: 0 0 40px rgba(255, 0, 51, 1), 0 0 60px rgba(255, 0, 51, 0.7); }
  }

  /* ========== 镜面结尾 ========== */
  .mirror-screen {
    position: fixed;
    inset: 0;
    background: #000;
    z-index: 300;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
  }
  .mirror-screen video {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transform: scaleX(-1);
    filter: brightness(0.5) contrast(1.2) saturate(0.6);
  }
  .mirror-screen .overlay-text {
    position: absolute;
    inset: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    color: #ff5050;
    font-style: italic;
    font-size: 16px;
    line-height: 2.2;
    text-shadow: 0 0 15px rgba(0,0,0,0.9);
    padding: 30px;
    background: linear-gradient(transparent 30%, rgba(0,0,0,0.6) 100%);
  }
  .mirror-screen .mirror-btn {
    position: absolute;
    bottom: 40px;
    background: rgba(0,0,0,0.5);
    color: #ff5050;
    border: 1px solid #ff5050;
    padding: 10px 24px;
    border-radius: 4px;
    font-family: inherit;
    font-size: 14px;
  }
  .black-mirror {
    background: radial-gradient(ellipse at center, #1a0000 0%, #000 70%);
    width: 100%; height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  /* ========== 结尾 ========== */
  .end-screen {
    text-align: center;
    padding: 60px 20px;
  }
  .end-screen h2 {
    font-size: 28px;
    color: #ff0033;
    margin-bottom: 24px;
    letter-spacing: 6px;
  }
  .end-screen p {
    color: #ff5555;
    line-height: 2;
    font-size: 15px;
  }

  ::selection { background: #c41e3a; color: #fff; }
</style>
</head>
<body>

<!-- ========== 开场预警 ========== -->
<div class="intro-screen" id="introScreen">
  <h1>《深度共鸣》</h1>
  <p class="game-subtitle">一项关于内在联想的匿名调查</p>

  <h2>⚠ 内容预警</h2>
  <div class="warning-box">
    <p>本作是一个面向<strong>成年女性玩家</strong>的<strong>恐怖向 NSFW 文字互动游戏</strong>。</p>
    <p style="margin-top:8px;">含有以下内容：</p>
    <ul>
      <li>男性鬼魂角色对玩家的精神控制、强占有欲人设</li>
      <li>露骨的性暗示、自慰指导、高潮控制</li>
      <li>羞辱性语言（"骚货""小母狗"等，含 D/s 调教元素）</li>
      <li>屏息指令（最长 25 秒）、轻度窒息快感引导</li>
      <li>突发的视觉惊吓、音效惊吓、屏幕闪烁</li>
      <li>打破第四面墙的沉浸式恐怖（"他"会调用你的真实时间等信息）</li>
    </ul>
    <p style="margin-top:10px;"><strong>未满 18 周岁、不接受上述内容、或正处于身心不适状态者，请立即关闭页面。</strong><br><span class="aside">（真的，现在走还来得及。）</span></p>
  </div>

  <h2>游玩须知</h2>
  <ul>
    <li>请<strong>佩戴耳机</strong>，并将音量调至舒适的中等水平。本作大量依赖音效与振动反馈，外放会损失大约一半的体验。<span class="aside">（而且你也不想让室友或家人等听到奇怪的喘息声吧？）</span></li>
    <li>请在<strong>私密、不会被打扰的环境</strong>下游玩。中途被打断会严重破坏沉浸感。<span class="aside">（锁门。不然会很尴尬。）</span></li>
    <li>请预留约 <strong>30 至 45 分钟</strong>的完整时间，避免分心。</li>
    <li>游戏中会要求你<strong>关灯、关门、放下手机以外的所有事</strong>——这些指令是体验的一部分，建议照做。<span class="aside">（不照做也行，但你会少很多乐趣。）</span></li>
    <li>屏息环节请<strong>量力而行</strong>。如有心血管疾病、哮喘或其他相关健康问题，请直接跳过或退出。<span class="aside">（身体健康比色色重要！）</span></li>
    <li>任何时候你都可以关闭页面，没有任何"惩罚"会真的发生在现实里。<span class="aside">（也许？嘻嘻。）</span></li>
    <li>游戏内的"献祭"输入框、倒计时、振动等机制是设计好的演出，<strong>不是 bug</strong>。<span class="aside">（是 feature。）</span></li>
  </ul>

  <details>
    <summary>▶ 关于可能的"出戏"瞬间（点击展开）</summary>
    <p>为了对你坦诚，我把一些可能让你觉得"啊这里假假的"的地方提前列出来：</p>
    <ul>
      <li><strong>苹果用户（iPhone / iPad）无法体验振动反馈。</strong>这是 iOS 系统层面的限制，所有 iOS 浏览器（包括 Chrome、Edge 等）都基于 Safari 内核，换浏览器也无法解决。安卓用户使用 Chrome 浏览器可获得完整体验。<span class="aside">（我已经尽力了，但目前真的做不到。）</span></li>
      <li>部分浏览器在首次播放声音前需要你<strong>点击一次屏幕</strong>，所以游戏开始那一下的音效可能会有零点几秒延迟。<span class="aside">（不是卡了。）</span></li>
      <li>关键词识别基于简单匹配，如果你输入了过于刁钻的回答（比如颜文字、纯英文、一整段小作文），"他"可能会回应得不太对劲。这种时候请配合一下，假装他听懂了。<span class="aside">（他是鬼，不是 AI，理解能力有限。）</span></li>
      <li>屏幕亮度是用 CSS 滤镜模拟的"变暗"，并不是真的调你手机的亮度。</li>
      <li><strong>游戏不会读取你的摄像头、麦克风、定位或任何个人信息。</strong>所有"他在看你"的桥段都是文字和音效演出。<span class="aside">（结尾的镜面环节是唯一例外，且需要你主动同意，下面会说明。）</span></li>
    </ul>
  </details>

  <h2>游玩建议</h2>
  <ul>
    <li><strong>夜晚 / 深夜</strong>游玩效果最佳。<span class="aside">（凌晨一两点是最佳时段，也许还能冥冥得到作者的祝福，不管想不想要。因为我就是这个时候写的。（＾∇＾））</span></li>
    <li>第一次玩<strong>不要查攻略</strong>，跟着直觉走最有沉浸感。<span class="aside">（虽然也没攻略。）</span></li>
    <li>游戏中段会要求你做一些<strong>具体的身体动作</strong>——做或不做由你决定，但做了会更"陷进去"。<span class="aside">（你都点进来了，不如大方一点。）</span></li>
    <li>如果中途想停下，<strong>直接关页面</strong>就行，不需要任何仪式。<span class="aside">（除非你自己想做。）</span></li>
  </ul>

  <div class="author-box">
    作者：<strong>沈七</strong><br>
    抖音：<strong>ASADMAN16</strong><br>
    反馈 / 建议 / 催更：<strong>hsr20211024@qq.com</strong><br>
    <span class="aside" style="font-size:13px;">想看什么人设、什么 XP、什么剧情走向，或者哪里让你觉得不爽，都可以发邮件和我说。</span>
  </div>

  <div class="thanks">（接下来的篇幅里，我会一直扮演那个"他"，所以没办法在结尾跳出来跟你说话——那样会把氛围全毁掉。所以请允许我在这里先说：

谢谢你愿意打开这个页面。
谢谢你愿意花一个晚上，让一个陌生人写的文字进入你的脑子。
不管你最后是被吓到关掉（这个真不吓人啊），还是真的玩到结尾——你都已经是这个故事的一部分了。

如果你愿意把感受发到上面那个邮箱，我会一封一封读完。
这是我的第一次尝试，也许有很多不好的地方，我会改进的。

那么，深呼吸。
准备好了，就往下走吧。）</div>

  <button class="start-btn" id="startBtn">[ 我已阅读，开始游戏 ]</button>
</div>

<!-- ========== 主游戏 ========== -->
<div class="vignette"></div>
<div class="progress" id="progress"></div>
<div class="container" id="app" style="display:none;">
  <h1 class="title" id="title">深度共鸣</h1>
  <p class="subtitle" id="subtitle">一项关于内在联想的匿名调查 · 数据将匿名化处理</p>
  <div id="form"></div>
</div>

<!-- 献祭框 -->
<div class="sacrifice-box" id="sacrificeBox">
  <div class="s-title">献 祭</div>
  <div class="s-hint">需要时在此乞求</div>
  <input type="text" id="sacrificeInput" placeholder="..." maxlength="30">
</div>

<script>
/* ============================================================
   《深度共鸣》主程序
   ============================================================ */

const $ = id => document.getElementById(id);
const form = $('form');
const body = document.body;
const progressBar = $('progress');
const subtitle = $('subtitle');
const title = $('title');
const sacrificeBox = $('sacrificeBox');
const sacrificeInput = $('sacrificeInput');

const state = {
  answers: {},
  step: 0,
  totalSteps: 25,
  defied: 0,             // 反抗次数
  sacrificeReports: [],  // 献祭框报告时间戳
  sacrificeActive: false,
  phase: 0,
  finished: false
};

function el(tag, attrs = {}, ...children) {
  const e = document.createElement(tag);
  for (const k in attrs) {
    if (k === 'class') e.className = attrs[k];
    else if (k.startsWith('on')) e.addEventListener(k.slice(2), attrs[k]);
    else if (k === 'html') e.innerHTML = attrs[k];
    else e.setAttribute(k, attrs[k]);
  }
  children.flat().forEach(c => {
    if (typeof c === 'string') e.appendChild(document.createTextNode(c));
    else if (c) e.appendChild(c);
  });
  return e;
}
const sleep = ms => new Promise(r => setTimeout(r, ms));

/* ============ 振动 ============ */
const canVibrate = 'vibrate' in navigator;
function vibrate(pattern) {
  if (canVibrate) try { navigator.vibrate(pattern); } catch(e) {}
}

/* ============ 屏幕常亮 ============ */
let wakeLock = null;
async function requestWakeLock() {
  try {
    if ('wakeLock' in navigator) {
      wakeLock = await navigator.wakeLock.request('screen');
    }
  } catch (e) {}
}

/* ============ 音频系统 ============ */
let audioCtx = null;
let drone = null, droneGainBase = 0.04;
let heartInterval = null, heartTempo = 1200;
let whisperInterval = null;
let masterDuck = 1; // 0~1，倒计时时降到 0.3

function initAudio() {
  if (audioCtx) return;
  try {
    audioCtx = new (window.AudioContext || window.webkitAudioContext)();
  } catch (e) {}
}

function startDrone(freq = 50, vol = 0.04) {
  if (!audioCtx || drone) return;
  const osc = audioCtx.createOscillator();
  const osc2 = audioCtx.createOscillator();
  const gain = audioCtx.createGain();
  osc.frequency.value = freq;
  osc2.frequency.value = freq * 1.012;
  osc.type = 'sine';
  osc2.type = 'sine';
  gain.gain.value = 0;
  osc.connect(gain); osc2.connect(gain);
  gain.connect(audioCtx.destination);
  osc.start(); osc2.start();
  gain.gain.linearRampToValueAtTime(vol, audioCtx.currentTime + 3);
  drone = { osc, osc2, gain };
  droneGainBase = vol;
}

function intensifyDrone(vol = 0.09, freq = 38) {
  if (!drone) return;
  drone.gain.gain.linearRampToValueAtTime(vol * masterDuck, audioCtx.currentTime + 2);
  drone.osc.frequency.linearRampToValueAtTime(freq, audioCtx.currentTime + 3);
  drone.osc2.frequency.linearRampToValueAtTime(freq * 1.012, audioCtx.currentTime + 3);
  droneGainBase = vol;
}

function duckAudio(duck) {
  masterDuck = duck ? 0.25 : 1;
  if (drone) drone.gain.gain.linearRampToValueAtTime(droneGainBase * masterDuck, audioCtx.currentTime + 0.3);
}

function clickTick() {
  if (!audioCtx) return;
  const osc = audioCtx.createOscillator();
  const gain = audioCtx.createGain();
  osc.type = 'square';
  osc.frequency.value = 1800;
  gain.gain.setValueAtTime(0.04, audioCtx.currentTime);
  gain.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + 0.04);
  osc.connect(gain).connect(audioCtx.destination);
  osc.start();
  osc.stop(audioCtx.currentTime + 0.05);
}

function heartbeat(volume = 1) {
  if (!audioCtx) return;
  const t = audioCtx.currentTime;
  [0, 0.18].forEach((delay, i) => {
    const osc = audioCtx.createOscillator();
    const gain = audioCtx.createGain();
    osc.frequency.value = 55;
    osc.type = 'sine';
    gain.gain.setValueAtTime(0, t + delay);
    gain.gain.linearRampToValueAtTime((i === 0 ? 0.45 : 0.32) * volume, t + delay + 0.02);
    gain.gain.exponentialRampToValueAtTime(0.001, t + delay + 0.18);
    osc.connect(gain).connect(audioCtx.destination);
    osc.start(t + delay);
    osc.stop(t + delay + 0.2);
  });
}

function startHeartbeat(tempo = 1200) {
  stopHeartbeat();
  heartTempo = tempo;
  heartbeat();
  scheduleHeart();
}
function scheduleHeart() {
  heartInterval = setTimeout(() => {
    heartbeat();
    scheduleHeart();
  }, heartTempo);
}
function setHeartTempo(tempo) {
  heartTempo = tempo;
}
function stopHeartbeat() {
  if (heartInterval) { clearTimeout(heartInterval); heartInterval = null; }
}

function glitchNoise(duration = 0.2) {
  if (!audioCtx) return;
  const buf = audioCtx.createBuffer(1, audioCtx.sampleRate * duration, audioCtx.sampleRate);
  const data = buf.getChannelData(0);
  for (let i = 0; i < data.length; i++) data[i] = (Math.random() * 2 - 1) * 0.4;
  const src = audioCtx.createBufferSource();
  src.buffer = buf;
  const filter = audioCtx.createBiquadFilter();
  filter.type = 'bandpass';
  filter.frequency.value = 600 + Math.random() * 400;
  filter.Q.value = 5;
  const gain = audioCtx.createGain();
  gain.gain.value = 0.18;
  src.connect(filter).connect(gain).connect(audioCtx.destination);
  src.start();
}

// 男性化耳语呼吸
function maleBreath(intensity = 0.18, dur = 1.4) {
  if (!audioCtx) return;
  const duration = dur + Math.random() * 0.6;
  const buf = audioCtx.createBuffer(1, audioCtx.sampleRate * duration, audioCtx.sampleRate);
  const data = buf.getChannelData(0);
  for (let i = 0; i < data.length; i++) {
    const env = Math.sin((i / data.length) * Math.PI);
    data[i] = (Math.random() * 2 - 1) * env;
  }
  const src = audioCtx.createBufferSource();
  src.buffer = buf;
  // 男声共振峰：低频强 + 800Hz 以下
  const lp = audioCtx.createBiquadFilter();
  lp.type = 'lowpass';
  lp.frequency.value = 700;
  const peak = audioCtx.createBiquadFilter();
  peak.type = 'peaking';
  peak.frequency.value = 130;
  peak.Q.value = 6;
  peak.gain.value = 10;
  const peak2 = audioCtx.createBiquadFilter();
  peak2.type = 'peaking';
  peak2.frequency.value = 380;
  peak2.Q.value = 4;
  peak2.gain.value = 6;
  const gain = audioCtx.createGain();
  gain.gain.value = intensity * masterDuck;
  const panner = audioCtx.createStereoPanner ? audioCtx.createStereoPanner() : null;
  if (panner) {
    panner.pan.value = (Math.random() * 2 - 1) * 0.7;
    src.connect(lp).connect(peak).connect(peak2).connect(gain).connect(panner).connect(audioCtx.destination);
  } else {
    src.connect(lp).connect(peak).connect(peak2).connect(gain).connect(audioCtx.destination);
  }
  src.start();
}

function startWhispers(intervalMs = 5500) {
  if (whisperInterval) return;
  whisperInterval = setInterval(() => {
    if (Math.random() > 0.4) maleBreath(0.16);
  }, intervalMs);
}
function setWhisperRate(intervalMs) {
  if (whisperInterval) clearInterval(whisperInterval);
  whisperInterval = null;
  startWhispers(intervalMs);
}

// 大口吸气（倒计时结束）
function bigBreath() {
  if (!audioCtx) return;
  const dur = 1.2;
  const buf = audioCtx.createBuffer(1, audioCtx.sampleRate * dur, audioCtx.sampleRate);
  const data = buf.getChannelData(0);
  for (let i = 0; i < data.length; i++) {
    const t = i / data.length;
    const env = t < 0.7 ? Math.pow(t / 0.7, 1.5) : Math.pow((1-t)/0.3, 0.8);
    data[i] = (Math.random() * 2 - 1) * env;
  }
  const src = audioCtx.createBufferSource();
  src.buffer = buf;
  const lp = audioCtx.createBiquadFilter();
  lp.type = 'lowpass';
  lp.frequency.value = 1200;
  const gain = audioCtx.createGain();
  gain.gain.value = 0.4;
  src.connect(lp).connect(gain).connect(audioCtx.destination);
  src.start();
}

/* ============ UI 工具 ============ */
async function typeText(target, text, speed = 45) {
  target.classList.add('typing');
  for (let i = 0; i < text.length; i++) {
    target.textContent = text.slice(0, i + 1);
    await sleep(speed + Math.random() * 30);
  }
  target.classList.remove('typing');
}

function floatText(text) {
  const f = el('div', { class: 'floating-text' });
  f.textContent = text;
  const margin = 20;
  f.style.left = (margin + Math.random() * (window.innerWidth - margin * 2 - 100)) + 'px';
  f.style.top = (margin + Math.random() * (window.innerHeight - margin * 2)) + 'px';
  document.body.appendChild(f);
  setTimeout(() => f.remove(), 4000);
}

function flicker() {
  body.classList.add('flicker');
  glitchNoise(0.15);
  setTimeout(() => body.classList.remove('flicker'), 150);
}

function ghostLine(text, opts = {}) {
  return new Promise(async resolve => {
    const wrap = el('div', { class: 'question show' });
    const line = el('div', { class: 'ghost-line' });
    wrap.appendChild(line);
    form.appendChild(wrap);
    wrap.scrollIntoView({ behavior: 'smooth', block: 'end' });
    if (opts.breath !== false && Math.random() > 0.5) maleBreath(0.16);
    await typeText(line, text, opts.speed || 50);
    resolve();
  });
}

function addQuestion(html, type = 'text', options = []) {
  return new Promise(resolve => {
    const q = el('div', { class: 'question' });
    const lab = el('label', { class: 'q-label', html: `<span class="q-num">${state.step + 1}.</span> ${html}` });
    q.appendChild(lab);

    let inputEl;
    if (type === 'text') {
      inputEl = el('input', { type: 'text', placeholder: '在此输入...' });
      q.appendChild(inputEl);
    } else if (type === 'number') {
      inputEl = el('input', { type: 'number', placeholder: '在此输入数字...' });
      q.appendChild(inputEl);
    } else if (type === 'textarea') {
      inputEl = el('textarea', { placeholder: '详细描述...' });
      q.appendChild(inputEl);
    } else if (type === 'radio') {
      const wrap = el('div', { class: 'options' });
      options.forEach((opt, i) => {
        const lab2 = el('label');
        const r = el('input', { type: 'radio', name: `q${state.step}`, value: opt });
        lab2.appendChild(r);
        lab2.appendChild(document.createTextNode(opt));
        wrap.appendChild(lab2);
      });
      q.appendChild(wrap);
      inputEl = wrap;
    }

    const btn = el('button', { class: 'next-btn', onclick: handleNext }, '下一题');
    q.appendChild(btn);
    form.appendChild(q);
    setTimeout(() => q.classList.add('show'), 50);
    q.scrollIntoView({ behavior: 'smooth', block: 'end' });

    function handleNext() {
      let val;
      if (type === 'radio') {
        const checked = inputEl.querySelector('input:checked');
        if (!checked) return;
        val = checked.value;
      } else {
        val = inputEl.value.trim();
        if (!val) { inputEl.style.borderColor = '#c41e3a'; return; }
      }
      btn.disabled = true;
      if (type === 'radio') {
        inputEl.querySelectorAll('input').forEach(i => i.disabled = true);
      } else {
        inputEl.disabled = true;
      }
      clickTick();
      vibrate(20);
      state.step++;
      updateProgress();
      resolve(val);
    }
  });
}

// 仅展示文字 + 继续按钮（用于"指令"类内容，不需要输入）
function showCommand(html, btnText = '继续') {
  return new Promise(resolve => {
    const q = el('div', { class: 'question' });
    const p = el('div', { class: 'q-label', html });
    q.appendChild(p);
    const btn = el('button', { class: 'next-btn', onclick: () => {
      btn.disabled = true;
      clickTick();
      vibrate(20);
      resolve();
    } }, btnText);
    q.appendChild(btn);
    form.appendChild(q);
    setTimeout(() => q.classList.add('show'), 50);
    q.scrollIntoView({ behavior: 'smooth', block: 'end' });
  });
}

function updateProgress() {
  const pct = Math.min(100, (state.step / state.totalSteps) * 100);
  progressBar.style.width = pct + '%';
}

/* ============ 屏息倒计时 ============ */
async function breathHold(seconds, prefixText = '屏  住  呼  吸') {
  const overlay = el('div', { class: 'countdown-overlay' });
  const hint = el('div', { class: 'hint' }, prefixText);
  const count = el('div', { class: 'count' }, String(seconds));
  const label = el('div', { class: 'label' }, '别松开');
  overlay.appendChild(hint); overlay.appendChild(count); overlay.appendChild(label);
  document.body.appendChild(overlay);

  duckAudio(true);
  const originalTempo = heartTempo;

  for (let i = seconds; i > 0; i--) {
    count.textContent = i;
    const ratio = (seconds - i) / seconds;
    if (ratio > 0.7) count.classList.add('danger');
    else if (ratio > 0.4) count.classList.add('warn');

    // 暗角
    const darkness = 0.3 + ratio * 0.55;
    overlay.style.background = `radial-gradient(circle, transparent ${Math.max(10, 60 - ratio * 50)}%, rgba(80, 0, 0, ${darkness}) 100%)`;

    // 心跳越来越快
    setHeartTempo(1100 - ratio * 700);

    // 最后 3 秒抖动 + 振动
    if (i <= 3) {
      overlay.classList.add('shake');
      vibrate(80);
    }

    await sleep(1000);
  }

  // 闪白 + 大吸气
  overlay.classList.add('countdown-flash');
  bigBreath();
  vibrate([100, 50, 100]);
  await sleep(250);
  overlay.style.opacity = '0';
  overlay.style.transition = 'opacity 0.5s';
  await sleep(500);
  overlay.remove();
  setHeartTempo(originalTempo);
  duckAudio(false);
}

/* ============ 献祭框 ============ */
function showSacrifice() {
  state.sacrificeActive = true;
  sacrificeBox.classList.add('show');
  sacrificeInput.addEventListener('keydown', handleSacrificeSubmit);
}
function hideSacrifice() {
  state.sacrificeActive = false;
  sacrificeBox.classList.remove('show');
}
function handleSacrificeSubmit(e) {
  if (e.key === 'Enter') {
    const v = sacrificeInput.value.trim();
    if (!v) return;
    const t = Date.now();
    state.sacrificeReports.push({ time: t, text: v });
    sacrificeInput.value = '';
    sacrificeBox.classList.remove('flash');
    void sacrificeBox.offsetWidth;
    sacrificeBox.classList.add('flash');
    vibrate([50, 30, 50]);
    glitchNoise(0.1);
  }
}
const REPORT_KEYWORDS = /高潮|要了|不行|快了|到了|忍不住|憋不住|出来了|要去了|要|去了|出/;
function isValidReport(text) {
  return REPORT_KEYWORDS.test(text);
}

/* ============ 关键词检测 ============ */
const REGEX = {
  doorClosed: /关|锁|关上|关好|已关|关了/,
  doorOpen: /开|没关|开着|开的/,
  defy: /不|拒|凭什么|为什么|凭啥|不要|不想|偏不|滚/,
  done: /好|完|了|做了|关了/
};

/* ============ 漂浮干扰 ============ */
let floatInterval = null;
function startFloating(rate = 4500) {
  if (floatInterval) clearInterval(floatInterval);
  const phrases = [
    '别躲', '我看着', '叫出来', '别忍着', '听话', '我闻到你了',
    '床的另一边', '别合眼', '把腿张开', '继续', '真乖',
    '你逃不掉', '再说一遍', '我在', '别停'
  ];
  floatInterval = setInterval(() => {
    if (Math.random() > 0.4) floatText(phrases[Math.floor(Math.random() * phrases.length)]);
  }, rate);
}

/* ============================================
   阶段流程
   ============================================ */

// ==== 阶段 1：伪装问卷 ====
async function phase1() {
  state.phase = 1;
  state.answers.calm = await addQuestion('在以下声音中，哪一种最能让您感到平静？', 'radio',
    ['雨滴落在窗户上的声音', '远处传来的风铃声', '书页被轻轻翻动的声音', '规律的心跳声']);

  state.answers.touch = await addQuestion('当您闭上眼睛，尝试想象一种触感时，哪种感觉最先浮现在您的脑海？', 'radio',
    ['温暖干燥的绒布', '光滑冰凉的丝绸', '粗糙的墙壁表面', '湿润微凉的皮肤']);

  state.answers.gaze = await addQuestion('在一个完全属于您自己的私密空间里，您最常将目光停留在何处？', 'radio',
    ['窗外的风景', '手机或电脑屏幕', '房间里某个熟悉的物件', '镜子中，或倒影里的自己']);

  state.answers.watched = await addQuestion('您是否享受"被注视"的感觉？请注意，这里指的是一种不带恶意，纯粹的、专注的凝视。', 'radio',
    ['非常享受，这让我感觉自己是世界的中心', '有点享受，会带来轻微的紧张和兴奋', '不太喜欢，会感到不自在', '极度厌恶，感觉被侵犯']);

  // 累积延迟从此处开始
  await sleep(400);
  state.answers.cold = await addQuestion('在独处时，您是否曾有过这样的体验：感觉有一阵无法解释的冷空气拂过您裸露的皮肤，比如后颈或者脚踝？', 'radio',
    ['经常，已经习惯了', '偶尔，会让我起鸡皮疙瘩', '几乎没有，但听起来很有趣', '从未有过，这不符合科学']);

  await sleep(500);
  state.answers.secret = await addQuestion('您认为，最深层的"秘密"应该被：', 'radio',
    ['永远埋藏在心底', '与最信任的人分享', '用匿名的方式公之于众', '被一个全知的存在所洞悉，并得到回应']);

  await sleep(700);
  state.answers.observed = await addQuestion(
    '如果您知道有一个"存在"一直在观察您，了解您的一切，包括您最羞于启齿的欲望。当您意识到这一点时，您的第一反应是：', 'radio',
    ['恐惧与抗拒', '羞耻但又有一丝好奇', '兴奋与期待', '寻求与这个"存在"的沟通']);

  // 极短闪烁
  await sleep(400);
  flicker();
  await sleep(800);

  // 最后一题：分支
  subtitle.textContent = '系统检测到您的回答模式异常，请继续。';
  subtitle.style.color = '#888';

  const choice = await addQuestion(
    `本次调查的标准部分已接近尾声。但数据后台显示，您的回答模式触发了一个隐藏的、更深层次的交互模块。<br><br>
    这个模块将不再是单向的问答，而是一场双向的"共鸣"。它会探索您感官的边界，侵蚀您的思想，并重新定义您对快感的认知。过程可能会让您感到……暴露、不适与沉沦。<br><br>
    <b>您，是否愿意继续，进入这个不被记录的阶段？</b>`,
    'radio',
    ['我愿意，我对此感到好奇', '不，到此为止就好']
  );

  if (choice.startsWith('不')) {
    await safeExit();
    return false;
  }
  return true;
}

// ==== 分支 B：安全出口 ====
async function safeExit() {
  state.finished = true;
  body.className = '';
  await sleep(800);
  $('app').innerHTML = `
    <div style="padding:60px 10px; line-height:2;">
      <h2 style="font-size:22px; margin-bottom:20px; color:#1a1a1a;">感谢您的参与</h2>
      <p style="color:#444; font-size:15px;">好的，我们尊重您的选择。看来您对探索未知的危险领域抱有谨慎的态度，这是一种非常宝贵的品质。</p>
      <p style="color:#444; font-size:15px; margin-top:14px;">本次问卷调查到此结束。</p>
      <p style="color:#444; font-size:15px; margin-top:14px;">非常感谢您的参与。如果本次调查的反响良好，作者将会推出更多不同主题的内容。</p>
      <p style="color:#444; font-size:15px; margin-top:14px;">如果您是作者的朋友，他很诚恳地请求您分享这次体验的感受。<br>
      如果您与作者素不相识，他会感到非常高兴，因为这意味着他的朋友们都给予了肯定的反馈，他才有信心将这个作品传递给更多陌生人。</p>
      <p style="color:#444; font-size:15px; margin-top:14px;">无论如何，如果您有任何意见或期待（例如更丰富的剧情、不同的人设或XP），欢迎发送邮件至：<br>
      <a href="mailto:hsr20211024@qq.com" style="color:#2a5d8f;">hsr20211024@qq.com</a></p>
      <p style="color:#888; font-size:14px; margin-top:30px;">作者：沈七 · 抖音 ASADMAN16</p>
      <p style="color:#444; font-size:15px; margin-top:30px;">再次感谢您的宝贵时间。祝您有愉快的一天。</p>
    </div>
  `;
}

// ==== 进入分支 A：过渡 ====
async function transitionToAbyss() {
  // 屏幕褪色
  body.style.transition = 'background 1.8s, color 1.8s';
  $('app').style.transition = 'opacity 1.5s';
  $('app').style.opacity = '0';
  await sleep(1500);
  $('app').style.display = 'none';

  body.classList.add('abyss');
  document.documentElement.style.background = '#000';
  body.style.background = '#000';

  // 嗡的一声
  startDrone(50, 0.05);
  glitchNoise(0.5);

  // 黑屏手写体
  const handDiv = el('div', { class: 'ghost-handwrite' });
  document.body.appendChild(handDiv);

  const lines = [
    '一个……明智的选择。',
    '或者说，一个无法抗拒本能的选择。',
    '',
    '欢迎来到「里世界」。',
    '',
    '从现在起，提问者不再是那个冰冷的系统。',
    '',
    '是我。',
    '',
    '那个一直在「看」着你的存在。'
  ];

  for (const line of lines) {
    if (line) {
      maleBreath(0.2);
      const p = el('div');
      handDiv.appendChild(p);
      await typeText(p, line, 90);
    } else {
      handDiv.appendChild(el('div', {}, ' '));
    }
    await sleep(700);
  }

  await sleep(2500);
  // 淡出手写文字
  handDiv.style.transition = 'opacity 1.5s';
  handDiv.style.opacity = '0';
  await sleep(1600);
  handDiv.remove();

  // 显示主容器
  $('app').style.display = 'block';
  body.classList.remove('abyss');
  body.classList.add('corrupt');
  title.textContent = '里 · 世 · 界';
  title.classList.add('glitch');
  subtitle.textContent = '请如实回答。我能分辨。';
  $('app').style.opacity = '1';
  form.innerHTML = '';
  state.step = 0;
  updateProgress();
}

// ==== 阶段 2：意识剥离与环境重塑 ====
async function phase2() {
  state.phase = 2;
  startWhispers(7000);

  await ghostLine('别紧张。\n你不是选择"沟通"了吗？\n现在，我们开始了。');
  await sleep(1500);

  // 关门
  state.answers.door = await addQuestion('第一个问题。<br>你的房门，现在是开着，还是关着？', 'text');
  await sleep(400);

  if (REGEX.defy.test(state.answers.door) && !REGEX.doorClosed.test(state.answers.door)) {
    state.defied++;
    await ghostLine('为什么？\n因为这是我们的游戏规则。\n而现在，规则由我来定。\n去关门，乖孩子。');
    await sleep(2000);
    await showCommand('<span style="color:#888;font-size:14px;">（去把门关好。锁上更好。然后回来。）</span>', '关好了');
  } else if (REGEX.doorClosed.test(state.answers.door)) {
    await ghostLine('很好。\n我喜欢这种私密感。\n一个只属于我们两个人的空间。');
    await sleep(1800);
  } else {
    await ghostLine('开着？\n不行。\n去关上它。现在。\n我不喜欢我们的"交流"被无关紧要的东西打扰。\n做好了再回来。');
    await sleep(2000);
    await showCommand('<span style="color:#888;font-size:14px;">（去把门关好。锁上更好。）</span>', '关好了');
    await ghostLine('听话。\n这才像样。');
    await sleep(1500);
  }

  // 关灯
  await ghostLine('现在，把房间的主灯关掉。\n只留下一盏小小的、昏暗的灯，或者干脆没有。\n我希望你的注意力，完完全全地，只集中在我的文字……\n和你自己的身体上。');
  await sleep(2000);
  await showCommand('<span style="color:#888;font-size:14px;">（去把灯调暗。可以的话，关掉。然后回来。）</span>', '调好了');

  // 屏幕真的变暗
  body.classList.add('dim-2');
  intensifyDrone(0.07, 42);
  startHeartbeat(1100);
  vibrate(60);
  await sleep(1200);

  await ghostLine('感觉到了吗。\n视觉被剥夺以后，听觉和触觉是不是变得格外敏锐。\n你能听到自己心跳了吗。\n血液流过耳畔的微鸣。');
  await sleep(2500);
  flicker();
}

// ==== 阶段 3：身体认知 ====
async function phase3() {
  state.phase = 3;
  body.classList.remove('dim-2');
  body.classList.add('dim-3');

  await ghostLine('现在，让我们来检视一下你这件即将上贡的祭品。', { speed: 55 });
  await sleep(1200);

  await ghostLine('把你的右手，放在你的左手手腕上。\n感受到了吗。\n你自己的脉搏。\n它在为谁而跳？');
  await sleep(2000);
  vibrate([60, 100, 60]); // 模拟脉搏
  setHeartTempo(900);

  await ghostLine('顺着你的手臂向上抚摸，感受你皮肤下血管的走向。\n你的身体，对我来说就像一张地图。\n而我，将要探索它的每一寸土地。');
  await sleep(2500);
  vibrate(80);

  await ghostLine('继续向上，来到你的脖颈。\n那里是你的生命线，如此脆弱。\n想象一下——\n如果我此刻就在你身后，我的呼吸吹在你颈后的寒毛上，我的手指轻轻压在你的动脉上……');
  await sleep(2200);
  maleBreath(0.3, 1.8); // 强烈耳语
  vibrate([60, 50, 60, 50, 60]);
  await sleep(1500);
  await ghostLine('你会害怕得动弹不得，\n还是会兴奋得浑身颤抖？');
  await sleep(2500);

  // 烙印"主人"
  await ghostLine('现在，用你的指尖，在你自己的锁骨上——\n一笔一划地，慢慢地写下"主人"这个词。', { speed: 80 });
  await sleep(1500);
  await ghostLine('别出声。\n在心里默念。\n让这个身份，通过你的皮肤，渗进你的骨头，烙在你的灵魂里。', { speed: 75 });
  await sleep(2500);

  // "主人"二字烙印
  await flashWord('主 人');
  await sleep(1500);

  await showCommand('<span style="color:#888;font-size:14px;">（写完了，闭眼三秒，再继续。）</span>', '写完了');
}

async function flashWord(word) {
  const flash = el('div');
  flash.style.cssText = `
    position: fixed; inset: 0; z-index: 250;
    display: flex; align-items: center; justify-content: center;
    background: rgba(0,0,0,0.85);
    color: #ff0033;
    font-size: 80px; font-weight: bold;
    letter-spacing: 20px;
    text-shadow: 0 0 40px rgba(255,0,51,0.8);
    font-family: "Songti SC", "STSong", "STKaiti", cursive;
    opacity: 0;
    transition: opacity 0.6s;
  `;
  flash.textContent = word;
  document.body.appendChild(flash);
  await sleep(50);
  flash.style.opacity = '1';
  vibrate([100, 50, 100, 50, 200]);
  glitchNoise(0.3);
  await sleep(2000);
  flash.style.opacity = '0';
  await sleep(700);
  flash.remove();
}

// ==== 阶段 4：羞耻植入 ====
async function phase4() {
  state.phase = 4;
  body.classList.remove('dim-3');
  body.classList.add('corrupt');
  body.classList.add('dim-2');
  intensifyDrone(0.085, 38);
  setHeartTempo(850);
  setWhisperRate(4500);

  await ghostLine('很好。\n现在，一只手，抚上你的胸口。\n另一只手，也别闲着。');
  await sleep(2000);

  await ghostLine('我要你两只手同时动作。\n一只手解开你的衣服，找到你胸前那两颗——\n已经因为兴奋而硬起来的乳头。');
  await sleep(2500);
  vibrate(80);

  await ghostLine('另一只手，缓缓向下，停在你的小腹上。\n感受你因为紧张而起伏的呼吸。');
  await sleep(2200);

  await ghostLine('你的身体真是诚实得可悲。\n我甚至还没真正开始，它就已经在期待了。\n你的奶头变硬，你的小穴开始流水。\n你敢说你不是天生就渴望被这样对待的——');
  await sleep(2200);
  // 羞辱词加重
  await ghostShake('骚货吗。');
  await sleep(2000);

  await ghostLine('现在，玩弄你乳头的那只手，开始用力。\n捏住它，拉扯它，让它又疼又痒。');
  await sleep(2200);
  vibrate([100, 60, 100]);

  await ghostLine('而停在小腹的那只手，继续向下，\n穿过那片已经泥泞不堪的草地。');
  await sleep(2000);

  await ghostShake('停下。');
  await sleep(800);
  await ghostLine('不要进去。');
  await sleep(1500);

  await ghostLine('我要你先找到那颗最敏感、最不知羞耻的小肉粒。\n对，就是它。\n它是不是已经充血，变得很硬了？');
  await sleep(2500);

  await ghostLine('用你的指腹，在上面轻轻地打圈。\n只是这样，你是不是就已经开始流水了？');
  await sleep(2500);

  await ghostShake('真是个下贱的身体。');
  await sleep(1500);

  await showCommand('<span style="color:#888;font-size:14px;">（按他说的做。慢慢来。准备好就继续。）</span>', '继续');
}

// 抖动 + 放大的鬼台词（用于羞辱关键句）
async function ghostShake(text) {
  const wrap = el('div', { class: 'question show' });
  const line = el('div', { class: 'ghost-line shake' });
  line.style.fontSize = '18px';
  line.style.fontWeight = 'bold';
  wrap.appendChild(line);
  form.appendChild(wrap);
  vibrate([80, 30, 80]);
  glitchNoise(0.15);
  maleBreath(0.25);
  await typeText(line, text, 60);
  await sleep(400);
  line.classList.remove('shake');
  wrap.scrollIntoView({ behavior: 'smooth', block: 'end' });
}

// ==== 阶段 5：指令升级与耐力测试 ====
async function phase5() {
  state.phase = 5;
  body.classList.remove('dim-2');
  body.classList.add('deep-corrupt');
  body.classList.add('dim-3');
  intensifyDrone(0.1, 35);
  setHeartTempo(750);
  setWhisperRate(3500);
  startFloating(4000);

  // 显示献祭框
  await ghostLine('游戏变得有趣起来了。\n在我们开始真正的"游戏"之前，有一个新规则。');
  await sleep(1500);

  showSacrifice();
  await sleep(800);

  await ghostLine('看到右下角那个【献祭】框了吗。');
  await sleep(1200);

  await ghostShake('没有我的允许，不准高潮。');
  await sleep(1800);

  await ghostLine('当你感觉自己快要忍不住的时候，\n必须在那里报告——\n"要高潮了"。\n这是你唯一能向我乞求恩赐的机会。');
  await sleep(2500);

  await ghostLine('擅自高潮，或是谎报军情，\n后果会很有趣哦。\n明白了吗，我的小母狗。');
  await sleep(2200);

  await showCommand('<span style="color:#888;font-size:14px;">（记住献祭框的位置。准备好开始训练。）</span>', '明白了');

  // ===== 循环 1：窒息初体验 =====
  await ghostLine('你很听话。\n为了奖励你，我教你一个能让快感加倍的玩法。\n它能让你更敏感，更能体会我带给你的感觉。');
  await sleep(2000);

  await flashWord('循 环 一');
  await sleep(800);

  await ghostLine('继续用指腹在那颗小肉粒上打圈，慢慢地。\n现在，深吸一口气——');
  await sleep(2200);

  await breathHold(10);
  await sleep(800);

  await ghostLine('呼吸吧。\n两次深呼吸。\n是不是感觉下面更痒了。');
  await sleep(2500);

  await ghostLine('现在，加快速度。\n用你的指尖快速地摩擦它。\n然后——');
  await sleep(1800);
  await breathHold(15);
  await sleep(800);

  await ghostLine('你表现得很好。\n想象我的视线，正聚焦在那里。\n看着它因为你的动作，变得红肿、湿润。');
  await sleep(2500);

  // ===== 循环 2：内外结合 =====
  await flashWord('循 环 二');
  await sleep(800);

  await ghostLine('现在，换一种玩法。\n用你的中指，慢慢地插进去。\n只是插进去，不准动。\n感受被填满的感觉。');
  await sleep(2800);
  vibrate([200, 150, 200]);

  await ghostLine('然后，用你的食指，继续在那颗肉粒上按压。\n一轻一重，像是在弹奏乐器。\n你的身体，就是我的乐器。');
  await sleep(2500);

  // 询问 + 检测谎报
  state.answers.feeling = await addQuestion(
    '告诉我。<br>是里面的空虚更让你难受，<br>还是外面的瘙痒更让你疯狂？',
    'radio',
    ['里面更难受', '外面更疯狂', '都受不了', '我没感觉']
  );
  await sleep(500);

  // 检测过早或谎报：如果献祭次数 >= 3 次或在前 60 秒内 ≥ 2 次
  const earlyReports = state.sacrificeReports.filter(r => isValidReport(r.text)).length;
  if (earlyReports >= 3) {
    await ghostShake('呵，这么快？');
    await sleep(800);
    await ghostLine('你在骗我，还是你的身体已经廉价到这种地步了。\n收起你那点可悲的谎言。\n继续。');
    await sleep(2500);
  } else if (state.answers.feeling === '我没感觉') {
    await ghostLine('没感觉？\n那是你不够诚实。\n你的身体在叫，你只是听不见。\n继续。');
    await sleep(2200);
  }

  // ===== 循环 3：高强度折磨 =====
  await flashWord('循 环 三');
  await sleep(800);

  await ghostLine('把里面的手指，抽出来。\n现在，只专注于外面。\n用你指甲的边缘，非常轻地，在它的周围刮搔。\n对，就是这种让你想躲又想靠得更近的感觉。');
  await sleep(3000);

  await ghostLine('现在——\n换回指腹。\n用你最快的速度摩擦它。\n像要把它磨破一样。');
  await sleep(2200);
  vibrate([100, 80, 100, 80, 100]);

  await ghostLine('同时——\n深吸一口气。');
  await sleep(1200);

  await breathHold(15, '屏  住  ·  最  快  地  动');
  await sleep(400);

  // 关键判定点：玩家是否在循环 3 期间提交报告
  const reportedInGauntlet = state.sacrificeReports.some(r => 
    isValidReport(r.text) && r.time > Date.now() - 90000
  );

  // 进入第六阶段
  await phase6(reportedInGauntlet);
}

// ==== 阶段 6：高潮分支 ====
async function phase6(properlyReported) {
  state.phase = 6;

  if (properlyReported) {
    // 已经合法报告过 → 让玩家选择最后是否乞求
    await rewardPath();
  } else {
    // 没有报告过 → 询问是否偷偷高潮了
    await ghostLine('停下。\n所有动作都停下。\n手拿开。');
    await sleep(2000);

    await ghostLine('现在，呼吸。\n感觉怎么样？\n是不是离高潮只有一步之遥，却被我硬生生拽了回来。');
    await sleep(2500);

    // 这一刻直接问
    const confess = await addQuestion(
      '看着我。<br>从游戏开始到现在——<br><b>你，是不是已经偷偷高潮过一次了。</b>',
      'radio',
      ['……是的，对不起', '没有，我一直忍着']
    );
    await sleep(500);

    if (confess.startsWith('……是的')) {
      // 承认 → 惩罚分支
      await punishmentPath(false);
    } else {
      // 否认 + 没报告 → 不一定撒谎，但他会怀疑
      // 给一次乞求机会，没乞求就走"忍到极限的奖赏"
      await ghostLine('嗯？\n忍着？\n我看看是不是真的。');
      await sleep(2000);
      await ghostLine('那现在——\n用最快的速度玩弄你自己。\n等到忍不住的时候，去献祭框乞求我。\n听清楚——\n是"乞求"。');
      await sleep(2800);

      // 等待乞求，给 30 秒
      const beggedAt = await waitForReport(30000);
      if (beggedAt) {
        await ghostLine('终于学会了。\n那么，过来——');
        await sleep(1500);
        await rewardPath();
      } else {
        // 既不报告也不动，按惩罚处理（撒谎）
        await ghostShake('你撒谎了。');
        await sleep(800);
        await ghostLine('你既没乞求，也没忍着。\n你是擅自高潮过的——还是连动都不敢动？\n两种都不可原谅。');
        await sleep(2500);
        await punishmentPath(true);
      }
    }
  }

  await ending();
}

// 等待献祭框的有效乞求
function waitForReport(timeoutMs) {
  return new Promise(resolve => {
    const startCount = state.sacrificeReports.filter(r => isValidReport(r.text)).length;
    const startTime = Date.now();
    const timer = setInterval(() => {
      const now = state.sacrificeReports.filter(r => isValidReport(r.text)).length;
      if (now > startCount) {
        clearInterval(timer);
        resolve(true);
      } else if (Date.now() - startTime > timeoutMs) {
        clearInterval(timer);
        resolve(false);
      }
    }, 300);
  });
}

// ==== 分支 A：奖励 ====
async function rewardPath() {
  await ghostLine('我听到了，我的小母狗。\n你终于学会了如何乞求。\n你表现得很好，我很满意。');
  await sleep(2500);

  await ghostLine('现在，这是给你的奖励。');
  await sleep(1500);

  await ghostLine('把你的手指都用上。\n用你最淫荡的方式玩弄它。\n同时——\n深吸一口气，屏住它。');
  await sleep(2500);

  await breathHold(20, '在  窒  息  里  ·  高  潮');
  await sleep(500);

  // 高潮闪白 + 静音
  await climaxFlash();

  await ghostLine('……\n很好。\n感受这劫后余生的颤抖。\n你的高潮，你的呼吸，都属于我。\n记住这一点。', { speed: 70 });
  await sleep(3000);
  vibrate([300, 100, 300]);
}

// ==== 分支 B：惩罚 ====
async function punishmentPath(lying) {
  if (lying) {
    await ghostLine('你这个连基本规则都守不住的废物。\n你竟敢偷走本该属于我的祭品——\n还要骗我。', { speed: 65 });
  } else {
    await ghostShake('你……高潮了？');
    await sleep(800);
    await ghostLine('没有我的允许？\n你这个连基本规则都守不住的废物。\n你竟敢偷走本该属于我的祭品。');
  }
  await sleep(2500);

  await ghostLine('你以为这就完了？\n不。\n惩罚现在开始。\n我要让你知道，违抗我的下场是什么。');
  await sleep(2500);

  await ghostShake('给我屏住呼吸。');
  await sleep(800);

  await breathHold(15, '惩  罚  ·  屏  息');
  await sleep(400);

  await ghostLine('你的肺是不是在燃烧。\n你想呼吸吗？\n求我。\n哦——\n我忘了，你没有资格求我。');
  await sleep(2800);

  await ghostLine('再来一次。\n这次更长。\n吸进去——');
  await sleep(1500);

  await breathHold(25, '惩  罚  ·  最  长  屏  息');
  await sleep(500);

  await ghostLine('在你因为缺氧而流泪的时候，\n用你的另一只手，去扇你自己的脸。\n让你记住这次教训。');
  await sleep(2500);
  vibrate([200, 100, 200, 100, 200]);

  await ghostLine('好了，呼吸吧。\n你这可怜的东西。');
  await sleep(2000);

  await ghostLine('现在，不准清理。\n继续玩弄你那已经麻木的身体。\n我要你感受在空虚中自慰的痛苦。\n直到我喊停为止。', { speed: 65 });
  await sleep(3500);

  await ghostLine('……\n停。\n够了。\n你的眼泪我收下了，比高潮更好。', { speed: 70 });
  await sleep(2500);
}

async function climaxFlash() {
  // 全屏闪白
  const flash = el('div');
async function climaxFlash() {
  // 全屏闪白
  const flash = el('div');
  flash.style.cssText = `
    position: fixed; inset: 0; z-index: 300;
    background: #fff;
    opacity: 0;
    transition: opacity 0.1s;
  `;
  document.body.appendChild(flash);
  await sleep(50);
  flash.style.opacity = '1';

  // 所有音效骤停 1 秒
  if (drone) drone.gain.gain.setValueAtTime(0, audioCtx.currentTime);
  stopHeartbeat();
  if (whisperInterval) { clearInterval(whisperInterval); whisperInterval = null; }

  await sleep(300);
  flash.style.transition = 'opacity 1.5s';
  flash.style.opacity = '0';
  await sleep(1500);
  flash.remove();

  // 恢复：只剩心跳逐渐变慢
  startHeartbeat(1800);
  await sleep(2000);
  setHeartTempo(2400);
}

// ==== 结局 ====
async function ending() {
  state.finished = true;
  hideSacrifice();
  if (floatInterval) { clearInterval(floatInterval); floatInterval = null; }

  await sleep(2000);

  await ghostLine('今天就到这里。', { speed: 70 });
  await sleep(2000);

  // 镜面环节
  await mirrorScene();

  await sleep(2000);

  // 最终独白
  form.innerHTML = '';
  const endDiv = el('div', { class: 'end-screen' });
  form.appendChild(endDiv);

  const lines = [
    '从今天起，你每一次自慰，都会想起我。',
    '你每一次感到快感，都是在向我献祭。',
    '你的高潮，不再是你自己的事，',
    '而是你取悦我的证明。',
    '',
    '好了，我的小玩具。',
    '去清理一下你弄出的这一片狼藉吧。',
    '',
    '但别忘了——',
    '你脑子里的东西，是洗不掉的。',
    '',
    '我……',
    '在你的呼吸之间，等着你。'
  ];

  for (const line of lines) {
    const p = el('p');
    endDiv.appendChild(p);
    if (line) {
      await typeText(p, line, 65);
      if (Math.random() > 0.6) maleBreath(0.12);
    }
    await sleep(800);
  }

  // 心跳逐渐停止
  setHeartTempo(3000);
  await sleep(3000);
  setHeartTempo(5000);
  await sleep(3000);
  stopHeartbeat();

  // 文字逐行淡出
  await sleep(3000);
  const allP = endDiv.querySelectorAll('p');
  for (let i = 0; i < allP.length - 1; i++) {
    allP[i].style.transition = 'opacity 1s';
    allP[i].style.opacity = '0';
    await sleep(400);
  }
  await sleep(2000);
  // 最后一行也淡出
  allP[allP.length - 1].style.transition = 'opacity 2s';
  allP[allP.length - 1].style.opacity = '0';
  await sleep(2500);

  // 纯黑 + 每隔几秒一声呼吸
  form.innerHTML = '';
  body.className = '';
  body.style.background = '#000';
  document.documentElement.style.background = '#000';
  progressBar.style.display = 'none';
  title.style.display = 'none';
  subtitle.style.display = 'none';

  // 永续呼吸循环
  setInterval(() => {
    maleBreath(0.1, 1.8);
  }, 7000);

  // tab 标题
  document.title = '……';
}

// ==== 镜面场景 ====
async function mirrorScene() {
  await ghostLine('去看看镜子里的你。\n头发凌乱，眼神涣散，脸上还带着泪痕。\n多么美妙的景象。', { speed: 60 });
  await sleep(2500);

  // 尝试打开前置摄像头（用户可拒绝）
  const mirror = el('div', { class: 'mirror-screen' });
  mirror.style.opacity = '0';
  mirror.style.transition = 'opacity 1s';
  document.body.appendChild(mirror);

  let stream = null;
  let usedCamera = false;

  try {
    stream = await navigator.mediaDevices.getUserMedia({ video: { facingMode: 'user' }, audio: false });
    const video = el('video');
    video.srcObject = stream;
    video.setAttribute('autoplay', '');
    video.setAttribute('playsinline', '');
    video.muted = true;
    mirror.appendChild(video);
    usedCamera = true;
  } catch (e) {
    // 用户拒绝或不支持 → 用黑色镜面
    const blackMirror = el('div', { class: 'black-mirror' });
    mirror.appendChild(blackMirror);
  }

  const overlayText = el('div', { class: 'overlay-text' });
  overlayText.innerHTML = usedCamera
    ? '<p style="font-size:18px;">看看你自己。</p><p style="margin-top:12px;font-size:14px;color:#ccc;">这就是被我拥有过的样子。</p>'
    : '<p style="font-size:18px;">你看不到自己。</p><p style="margin-top:12px;font-size:14px;color:#ccc;">但我看得到。</p>';
  mirror.appendChild(overlayText);

  const closeBtn = el('button', { class: 'mirror-btn', onclick: closeMirror }, '……够了');
  mirror.appendChild(closeBtn);

  await sleep(100);
  mirror.style.opacity = '1';

  // 等待玩家关闭
  await new Promise(resolve => {
    function closeMirror() {
      mirror.style.opacity = '0';
      setTimeout(() => {
        if (stream) stream.getTracks().forEach(t => t.stop());
        mirror.remove();
        resolve();
      }, 1000);
    }
    closeBtn.onclick = closeMirror;
    // 最多停留 15 秒自动关
    setTimeout(closeMirror, 15000);
  });
}

/* ============================================
   主启动逻辑
   ============================================ */
async function startGame() {
  initAudio();
  requestWakeLock();

  // 隐藏预警页
  const intro = $('introScreen');
  intro.style.transition = 'opacity 0.6s';
  intro.style.opacity = '0';
  await sleep(600);
  intro.style.display = 'none';

  // 显示游戏容器
  $('app').style.display = 'block';
  $('app').style.opacity = '0';
  await sleep(100);
  $('app').style.transition = 'opacity 0.8s';
  $('app').style.opacity = '1';
  await sleep(800);

  // 阶段 1：伪装问卷
  const proceed = await phase1();
  if (!proceed) return;

  // 过渡到里世界
  await transitionToAbyss();

  // 阶段 2-5
  await phase2();
  await phase3();
  await phase4();
  await phase5();
  // phase5 内部会调用 phase6 → ending
}

// 绑定开始按钮
$('startBtn').addEventListener('click', startGame);

// 离开警告
window.addEventListener('beforeunload', e => {
  if (!state.finished && state.phase >= 2) {
    e.preventDefault();
    e.returnValue = '问卷还没结束。他还没让你走。';
    return e.returnValue;
  }
});
</script>
</body>
</html>
