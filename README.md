[index.html.html](https://github.com/user-attachments/files/30190835/index.html.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>ClientHunter AI – US Lead Research Agent</title>
<link href="https://fonts.googleapis.com/css2?family=Sora:wght@400;600;700;800&family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet"/>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg:#090E1A;--surface:#0D1525;--card:#111C30;--raised:#162038;--border:#1A2840;
  --amber:#F0A500;--amber-dim:#B87D00;--amber-glow:rgba(240,165,0,0.12);
  --green:#22C55E;--red:#EF4444;--blue:#3B82F6;
  --text:#E8EFF8;--sub:#8899B4;--muted:#3D5270;--white:#fff;
}
html{scroll-behavior:smooth}
body{font-family:'Inter',sans-serif;background:var(--bg);color:var(--text);min-height:100vh;overflow-x:hidden}

/* LAYOUT */
.app{display:grid;grid-template-columns:280px 1fr;min-height:100vh}

/* HEADER */
header{grid-column:1/-1;padding:0 24px;height:52px;display:flex;align-items:center;justify-content:space-between;background:var(--surface);border-bottom:1px solid var(--border);position:sticky;top:0;z-index:100}
.h-logo{font-family:'Sora',sans-serif;font-size:17px;font-weight:800;color:var(--white)}
.h-logo span{color:var(--amber)}
.h-status{display:flex;align-items:center;gap:6px;font-size:11px;font-weight:600;color:var(--amber)}
.h-dot{width:6px;height:6px;border-radius:50%;background:var(--amber);animation:glow 2s infinite}
@keyframes glow{0%,100%{opacity:1}50%{opacity:.4}}

/* SIDEBAR */
.sidebar{background:var(--surface);border-right:1px solid var(--border);display:flex;flex-direction:column;overflow-y:auto;padding:16px}

/* API KEY BOX */
.api-box{background:rgba(240,165,0,0.06);border:1px solid rgba(240,165,0,0.25);border-radius:12px;padding:16px;margin-bottom:16px}
.api-box.connected{background:rgba(34,197,94,0.06);border-color:rgba(34,197,94,0.25)}
.api-box-title{font-size:11px;font-weight:700;letter-spacing:1px;text-transform:uppercase;margin-bottom:4px}
.api-box-title.amber{color:var(--amber)}
.api-box-title.green{color:var(--green)}
.api-box-sub{font-size:11px;color:var(--muted);margin-bottom:10px;line-height:1.5}
.api-box-sub a{color:var(--amber);text-decoration:none}
.api-input-wrap{position:relative;margin-bottom:8px}
.api-inp{width:100%;padding:9px 36px 9px 10px;background:var(--card);border:1px solid var(--border);border-radius:7px;color:var(--text);font-size:11px;font-family:'JetBrains Mono',monospace;outline:none;transition:border-color .2s}
.api-inp:focus{border-color:var(--amber)}
.api-inp::placeholder{color:var(--muted);font-family:'Inter',sans-serif;font-size:11px}
.api-eye{position:absolute;right:8px;top:50%;transform:translateY(-50%);background:none;border:none;color:var(--muted);cursor:pointer;font-size:13px;padding:0}
.api-btn{width:100%;padding:8px;background:var(--amber);color:#000;border:none;border-radius:7px;font-size:12px;font-weight:700;cursor:pointer;font-family:'Inter',sans-serif;transition:opacity .2s}
.api-btn:hover{opacity:.85}
.api-btn:disabled{opacity:.5;cursor:not-allowed}
.api-status{font-size:11px;margin-top:6px;text-align:center;min-height:16px;line-height:1.4}
.api-change{font-size:11px;color:var(--muted);text-align:center;margin-top:6px;cursor:pointer;text-decoration:underline}
.api-change:hover{color:var(--amber)}

/* SEARCH */
.search-section{margin-bottom:16px}
.lp-label{font-size:10px;font-weight:700;letter-spacing:1px;text-transform:uppercase;color:var(--muted);margin-bottom:8px;display:block}
.lp-input{width:100%;padding:9px 12px;background:var(--card);border:1px solid var(--border);border-radius:7px;color:var(--text);font-size:13px;outline:none;transition:border-color .2s;font-family:'Inter',sans-serif;margin-bottom:6px}
.lp-input:focus{border-color:var(--amber)}
.lp-input::placeholder{color:var(--muted)}
.lp-select{width:100%;padding:9px 12px;background:var(--card);border:1px solid var(--border);border-radius:7px;color:var(--text);font-size:13px;outline:none;font-family:'Inter',sans-serif;margin-bottom:6px;cursor:pointer}
.btn-find{width:100%;padding:11px;background:var(--amber);color:#000;border:none;border-radius:8px;font-size:13px;font-weight:700;cursor:pointer;transition:all .2s;font-family:'Inter',sans-serif}
.btn-find:hover{opacity:.88;transform:translateY(-1px)}
.btn-find:disabled{opacity:.5;cursor:not-allowed;transform:none}

/* MY DETAILS */
.my-details{margin-bottom:16px}

/* LEAD LIST */
.lead-list-wrap{flex:1;overflow-y:auto}
.ll-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:8px}
.lead-item{padding:11px 12px;border-radius:9px;cursor:pointer;transition:all .15s;border:1px solid transparent;margin-bottom:4px}
.lead-item:hover{background:var(--card);border-color:var(--border)}
.lead-item.active{background:var(--amber-glow);border-color:rgba(240,165,0,.3)}
.li-top{display:flex;align-items:flex-start;justify-content:space-between;gap:6px}
.li-name{font-size:12px;font-weight:600;color:var(--white);line-height:1.3}
.li-score{font-family:'Sora',sans-serif;font-size:13px;font-weight:800;color:var(--amber);flex-shrink:0}
.li-meta{font-size:11px;color:var(--muted);margin-top:2px}
.li-badge{display:inline-block;margin-top:5px;font-size:10px;font-weight:700;padding:2px 7px;border-radius:100px}
.b-new{background:rgba(59,130,246,.15);color:#60A5FA}
.b-analyzed{background:rgba(240,165,0,.15);color:var(--amber)}
.b-sent{background:rgba(34,197,94,.15);color:var(--green)}
.b-booked{background:rgba(139,92,246,.15);color:#A78BFA}
.b-rejected{background:rgba(239,68,68,.15);color:var(--red)}

/* MAIN PANEL */
.main-panel{overflow-y:auto;padding:24px}

/* WELCOME */
.welcome{display:flex;flex-direction:column;align-items:center;justify-content:center;min-height:70vh;text-align:center;gap:14px}
.w-icon{font-size:56px}
.w-title{font-family:'Sora',sans-serif;font-size:22px;font-weight:700;color:var(--white)}
.w-sub{font-size:14px;color:var(--sub);max-width:380px;line-height:1.7}
.w-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-top:20px;max-width:520px}
.w-card{background:var(--card);border:1px solid var(--border);border-radius:10px;padding:16px 14px;text-align:center}
.wc-icon{font-size:22px;margin-bottom:8px}
.wc-title{font-size:12px;font-weight:700;color:var(--white);margin-bottom:3px}
.wc-sub{font-size:11px;color:var(--muted);line-height:1.5}

/* LOADING */
.loading{display:flex;flex-direction:column;align-items:center;justify-content:center;min-height:60vh;gap:16px;text-align:center}
.loader{width:44px;height:44px;border:3px solid var(--border);border-top-color:var(--amber);border-radius:50%;animation:spin 1s linear infinite}
@keyframes spin{to{transform:rotate(360deg)}}
.loading-text{font-size:14px;color:var(--sub)}
.loading-step{font-size:13px;color:var(--amber);font-weight:600}

/* DOSSIER */
.dossier{display:flex;flex-direction:column;gap:16px}
.dossier-top{display:flex;align-items:flex-start;justify-content:space-between;gap:12px;flex-wrap:wrap}
.biz-name{font-family:'Sora',sans-serif;font-size:24px;font-weight:800;color:var(--white);letter-spacing:-.5px}
.biz-meta{display:flex;gap:10px;flex-wrap:wrap;margin-top:6px}
.meta{font-size:12px;color:var(--sub)}
.score-box{text-align:center;background:var(--amber-glow);border:1px solid rgba(240,165,0,.25);border-radius:12px;padding:14px 20px;flex-shrink:0}
.score-num{font-family:'Sora',sans-serif;font-size:44px;font-weight:800;color:var(--amber);line-height:1}
.score-lbl{font-size:10px;color:var(--amber);font-weight:600;margin-top:3px;letter-spacing:.5px;text-transform:uppercase}

/* STATUS ROW */
.status-row{display:flex;gap:6px;flex-wrap:wrap;margin-top:10px}
.st-btn{padding:4px 12px;border-radius:100px;font-size:11px;font-weight:700;cursor:pointer;border:1px solid var(--border);background:var(--surface);color:var(--sub);font-family:'Inter',sans-serif;transition:all .15s}
.st-btn.active{background:var(--amber);color:#000;border-color:var(--amber)}

/* SECTION CARDS */
.d-card{background:var(--card);border:1px solid var(--border);border-radius:12px;overflow:hidden}
.d-card-head{padding:12px 16px;border-bottom:1px solid var(--border);display:flex;align-items:center;gap:8px;background:rgba(255,255,255,.02)}
.d-card-icon{font-size:15px}
.d-card-title{font-size:13px;font-weight:700;color:var(--white)}
.d-card-badge{margin-left:auto;font-size:10px;font-weight:700;padding:3px 9px;border-radius:100px;background:var(--amber-glow);color:var(--amber)}
.d-card-body{padding:16px}

/* GRID */
.two-col{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.info-card{background:var(--surface);border-radius:8px;padding:12px}
.ic-label{font-size:10px;font-weight:700;letter-spacing:.5px;text-transform:uppercase;color:var(--muted);margin-bottom:5px}
.ic-val{font-size:13px;color:var(--text);line-height:1.5}
.ic-val.warn{color:var(--amber)}
.ic-val.bad{color:var(--red)}
.ic-val.good{color:var(--green)}
.ic-val.mono{font-family:'JetBrains Mono',monospace;font-size:12px}

/* LISTS */
.pain-list,.opp-list,.missing-list{display:flex;flex-direction:column;gap:6px}
.pain-item{background:rgba(239,68,68,.06);border:1px solid rgba(239,68,68,.15);border-radius:7px;padding:9px 11px;font-size:12px;color:var(--text);line-height:1.5;display:flex;gap:8px}
.opp-item{background:rgba(34,197,94,.06);border:1px solid rgba(34,197,94,.15);border-radius:7px;padding:9px 11px;font-size:12px;color:var(--text);line-height:1.5;display:flex;gap:8px}
.missing-item{display:flex;gap:6px;align-items:center;font-size:12px;color:var(--red);padding:3px 0}

/* PITCH */
.pitch-box{background:var(--surface);border-left:3px solid var(--amber);border-radius:8px;padding:14px;font-size:13px;color:var(--text);line-height:1.8;white-space:pre-wrap}

/* OBJECTIONS */
.obj-list{display:flex;flex-direction:column;gap:10px}
.obj-item{background:var(--surface);border-radius:8px;overflow:hidden}
.obj-q{padding:9px 12px;background:rgba(239,68,68,.07);border-bottom:1px solid rgba(239,68,68,.1);font-size:12px;font-weight:600;color:#FCA5A5}
.obj-a{padding:9px 12px;font-size:12px;color:var(--text);line-height:1.6}

/* MESSAGES */
.msg-tabs{display:flex;gap:4px;margin-bottom:10px}
.msg-tab{padding:5px 14px;border-radius:5px;font-size:12px;font-weight:600;cursor:pointer;border:1px solid var(--border);background:transparent;color:var(--sub);transition:all .15s;font-family:'Inter',sans-serif}
.msg-tab.active{background:var(--amber);color:#000;border-color:var(--amber)}
.msg-content{background:var(--surface);border-radius:8px;padding:14px;font-size:13px;color:var(--text);line-height:1.8;white-space:pre-wrap;min-height:100px;border:1px solid var(--border)}
.msg-subject{background:var(--surface);border-radius:7px;padding:9px 12px;margin-bottom:8px;border:1px solid var(--border);font-size:12px}
.msg-subject span{color:var(--amber);font-weight:700}

/* DEMO SECTION */
.demo-gen-area{margin-top:2px}
.demo-modal{position:fixed;inset:0;background:rgba(0,0,0,.92);backdrop-filter:blur(10px);z-index:500;display:flex;flex-direction:column;opacity:0;pointer-events:none;transition:opacity .25s}
.demo-modal.open{opacity:1;pointer-events:all}
.demo-bar{padding:11px 18px;background:var(--surface);border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between}
.demo-bar-title{font-family:'Sora',sans-serif;font-size:13px;font-weight:700;color:var(--white);display:flex;align-items:center;gap:8px}
.demo-badge{font-size:10px;font-weight:700;padding:3px 9px;border-radius:100px;background:rgba(240,165,0,.15);color:var(--amber)}
.demo-close{background:rgba(239,68,68,.15);border:1px solid rgba(239,68,68,.2);color:var(--red);padding:5px 12px;border-radius:5px;font-size:12px;font-weight:700;cursor:pointer;font-family:'Inter',sans-serif}
.demo-frame{flex:1;border:none;width:100%}

/* BEFORE/AFTER */
.ba-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.ba-col{border-radius:10px;overflow:hidden;border:2px solid var(--border)}
.ba-col.before{border-color:rgba(239,68,68,.3)}
.ba-col.after{border-color:rgba(34,197,94,.3)}
.ba-head{padding:9px 14px;display:flex;align-items:center;justify-content:space-between;font-size:12px;font-weight:700}
.ba-head.before{background:rgba(239,68,68,.08);color:var(--red)}
.ba-head.after{background:rgba(34,197,94,.08);color:var(--green)}
.ba-body{padding:12px;background:var(--surface)}
.ba-item{font-size:12px;padding:6px 8px;border-radius:6px;margin-bottom:4px;display:flex;gap:6px;line-height:1.4}
.ba-item.bad{background:rgba(239,68,68,.07);color:#FCA5A5}
.ba-item.good{background:rgba(34,197,94,.07);color:#86EFAC}

/* ACTIONS ROW */
.actions-row{display:flex;gap:8px;flex-wrap:wrap;margin-top:10px}

/* BUTTONS */
.btn{padding:8px 16px;border-radius:7px;font-size:12px;font-weight:700;border:none;cursor:pointer;transition:all .2s;font-family:'Inter',sans-serif;display:inline-flex;align-items:center;gap:5px;white-space:nowrap}
.btn-amber{background:var(--amber);color:#000}
.btn-amber:hover{opacity:.85}
.btn-outline{background:transparent;border:1px solid var(--border);color:var(--sub)}
.btn-outline:hover{border-color:var(--amber);color:var(--amber)}
.btn-green{background:var(--green);color:#000}
.btn-green:hover{opacity:.85}
.btn:disabled{opacity:.5;cursor:not-allowed}

/* TOAST */
.toast{position:fixed;bottom:18px;right:18px;background:var(--card);border:1px solid var(--amber);border-radius:8px;padding:10px 16px;font-size:12px;font-weight:600;color:var(--amber);z-index:999;transform:translateY(60px);opacity:0;transition:all .3s}
.toast.show{transform:translateY(0);opacity:1}

@media(max-width:800px){
  .app{grid-template-columns:1fr}
  .sidebar{border-right:none;border-bottom:1px solid var(--border)}
  .two-col,.ba-grid,.w-grid{grid-template-columns:1fr}
}
</style>
</head>
<body>

<div class="app" style="grid-template-rows:52px 1fr">

<!-- HEADER -->
<header style="grid-column:1/-1">
  <div class="h-logo">Client<span>Hunter</span> AI</div>
  <div class="h-status"><div class="h-dot"></div><span id="headerStatus">AI Agent Ready</span></div>
  <div style="display:flex;gap:8px;align-items:center">
    <div style="font-size:11px;font-weight:600;padding:4px 10px;border-radius:5px;border:1px solid var(--border);color:var(--sub)">US Market</div>
    <div style="font-size:11px;font-weight:600;padding:4px 10px;border-radius:5px;border:1px solid var(--border);color:var(--sub)">Web Design</div>
  </div>
</header>

<!-- SIDEBAR -->
<aside class="sidebar">

  <!-- API KEY BOX -->
  <div class="api-box" id="apiBox">
    <div class="api-box-title amber">🔑 Gemini API Key</div>
    <div class="api-box-sub">Required for AI features.<br/>Get free key at <a href="https://aistudio.google.com" target="_blank">aistudio.google.com</a></div>
    <div class="api-input-wrap">
      <input class="api-inp" id="apiKeyInput" type="password" placeholder="Paste your API key here..."
        onkeydown="if(event.key==='Enter') connectApiKey()"/>
      <button class="api-eye" onclick="toggleApiVis()">👁</button>
    </div>
    <button class="api-btn" id="apiConnectBtn" onclick="connectApiKey()">🔑 Connect API Key</button>
    <div class="api-status" id="apiStatus"></div>
  </div>

  <!-- SEARCH -->
  <div class="search-section">
    <span class="lp-label">Find US Businesses</span>
    <input class="lp-input" id="bizType" placeholder="Business type (dental clinic, gym...)" value="dental clinic"/>
    <input class="lp-input" id="bizCity" placeholder="US City (Austin TX, Miami FL...)" value="Austin, TX"/>
    <select class="lp-select" id="bizCount">
      <option value="5">5 leads</option>
      <option value="10" selected>10 leads</option>
      <option value="15">15 leads</option>
    </select>
    <button class="btn-find" id="findBtn" onclick="findLeads()">🔍 Find & Research Leads</button>
  </div>

  <!-- MY DETAILS -->
  <div class="my-details">
    <span class="lp-label">My Details</span>
    <input class="lp-input" id="myName" placeholder="Your name (e.g. Shaik)"/>
    <input class="lp-input" id="myPrice" placeholder="Starting price (e.g. $299)" value="$299"/>
  </div>

  <!-- LEAD LIST -->
  <div class="lead-list-wrap">
    <div class="ll-header">
      <span class="lp-label" style="margin-bottom:0">Leads <span id="leadCount" style="color:var(--amber)">0</span></span>
    </div>
    <div id="leadList">
      <div style="text-align:center;padding:24px 12px;color:var(--muted);font-size:12px">No leads yet.<br/>Search above to start.</div>
    </div>
  </div>

</aside>

<!-- MAIN -->
<main class="main-panel" id="mainPanel">
  <div class="welcome">
    <div class="w-icon">🎯</div>
    <div class="w-title">Your US Client Hunter</div>
    <div class="w-sub">Add your Gemini API key → Find US businesses → AI analyzes them → Get personalized pitch + outreach emails automatically.</div>
    <div class="w-grid">
      <div class="w-card"><div class="wc-icon">🔑</div><div class="wc-title">Step 1</div><div class="wc-sub">Add your Gemini API key in the left panel</div></div>
      <div class="w-card"><div class="wc-icon">🔍</div><div class="wc-title">Step 2</div><div class="wc-sub">Search any US business type + city</div></div>
      <div class="w-card"><div class="wc-icon">✉️</div><div class="wc-title">Step 3</div><div class="wc-sub">Click any lead → Get full pitch + emails</div></div>
    </div>
  </div>
</main>

</div>

<!-- DEMO MODAL -->
<div class="demo-modal" id="demoModal">
  <div class="demo-bar">
    <div class="demo-bar-title">🌐 <span id="demoTitle">Demo Website</span><span class="demo-badge">AI Generated</span></div>
    <div style="display:flex;gap:8px">
      <button onclick="copyDemoHTML()" style="background:rgba(240,165,0,.15);border:1px solid rgba(240,165,0,.2);color:var(--amber);padding:5px 12px;border-radius:5px;font-size:12px;font-weight:700;cursor:pointer;font-family:'Inter',sans-serif">📋 Copy HTML</button>
      <button class="demo-close" onclick="closeDemoModal()">✕ Close</button>
    </div>
  </div>
  <iframe class="demo-frame" id="demoFrame" srcdoc=""></iframe>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<script>
// ── API KEY MANAGEMENT ──
// Using localStorage to persist key between sessions
function getKey(){ return localStorage.getItem('ch_claudekey') || ''; }
function storeKey(k){ localStorage.setItem('ch_claudekey', k.trim()); }
function removeKey(){ localStorage.removeItem('ch_claudekey'); }

// Build Gemini API URL
function geminiUrl(key){
  const k = key || getKey();
  // Support both old AIzaSy format and new format keys
  return 'https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=' + k;
}
// Convert Claude-style messages to Gemini format and call API
async function callGemini(prompt, key){
  const url = geminiUrl(key);
  const res = await fetch(url, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      contents: [{ parts: [{ text: prompt }] }],
      generationConfig: { temperature: 0.7, maxOutputTokens: 8192 }
    })
  });
  const data = await res.json();
  if(data.error){
    const msg = data.error.message || data.error.status || JSON.stringify(data.error);
    throw new Error('Gemini Error: ' + msg);
  }
  if(!data.candidates || !data.candidates[0]){
    throw new Error('No response from Gemini. Try again.');
  }
  const text = data.candidates[0].content.parts[0].text;
  return text;
}

function toggleApiVis(){
  const i = document.getElementById('apiKeyInput');
  i.type = i.type === 'password' ? 'text' : 'password';
}

async function connectApiKey(){
  const inp = document.getElementById('apiKeyInput');
  const statusEl = document.getElementById('apiStatus');
  const btn = document.getElementById('apiConnectBtn');
  const key = inp.value.trim();

  statusEl.style.color = 'var(--muted)';
  statusEl.textContent = '';

  if(!key){
    statusEl.style.color = 'var(--red)';
    statusEl.textContent = 'Please enter your API key.';
    return;
  }
  // No format check - accept any key and let Gemini verify it
  if(!key){
    statusEl.style.color = 'var(--red)';
    statusEl.textContent = 'Please paste your API key first.';
    return;
  }

  btn.textContent = 'Verifying...';
  btn.disabled = true;
  statusEl.style.color = 'var(--amber)';
  statusEl.textContent = 'Checking key...';

  try {
    // Test key by making a real Gemini call
    const testUrl = 'https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=' + key;
    const res = await fetch(testUrl, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        contents: [{ parts: [{ text: 'Say OK' }] }],
        generationConfig: { maxOutputTokens: 5 }
      })
    });

    const data = await res.json();

    if(data.error){
      statusEl.style.color = 'var(--red)';
      const errMsg = data.error.message || data.error.status || 'Key not accepted by Google.';
      statusEl.textContent = '❌ ' + errMsg;
      btn.textContent = '🔑 Connect API Key';
      btn.disabled = false;
      return;
    }

    if(!data.candidates || !data.candidates[0]){
      statusEl.style.color = 'var(--red)';
      statusEl.textContent = '❌ No response from Google. Try again.';
      btn.textContent = '🔑 Connect API Key';
      btn.disabled = false;
      return;
    }

    // Success
    storeKey(key);
    setConnectedState();

  } catch(err) {
    statusEl.style.color = 'var(--red)';
    statusEl.textContent = '❌ Network error: ' + err.message;
    btn.textContent = '🔑 Connect API Key';
    btn.disabled = false;
  }
}

function setConnectedState(){
  const box = document.getElementById('apiBox');
  const statusEl = document.getElementById('apiStatus');
  const btn = document.getElementById('apiConnectBtn');
  const headerStatus = document.getElementById('headerStatus');

  box.classList.add('connected');
  statusEl.style.color = 'var(--green)';
  statusEl.textContent = '✅ Connected — Ready to find leads!';
  btn.textContent = '✅ Connected';
  btn.disabled = true;

  // Add change key link
  if(!document.getElementById('changeKeyLink')){
    const link = document.createElement('div');
    link.className = 'api-change';
    link.id = 'changeKeyLink';
    link.textContent = 'Change API key';
    link.onclick = resetApiKey;
    box.appendChild(link);
  }

  if(headerStatus) headerStatus.textContent = 'Claude AI Connected';
  showToast('✅ Gemini API connected! Start finding leads.');
}

function resetApiKey(){
  removeKey();
  const box = document.getElementById('apiBox');
  const btn = document.getElementById('apiConnectBtn');
  const inp = document.getElementById('apiKeyInput');
  const statusEl = document.getElementById('apiStatus');
  const headerStatus = document.getElementById('headerStatus');
  const changeLink = document.getElementById('changeKeyLink');

  box.classList.remove('connected');
  btn.textContent = '🔑 Connect API Key';
  btn.disabled = false;
  inp.value = '';
  statusEl.textContent = '';
  if(headerStatus) headerStatus.textContent = 'AI Agent Ready';
  if(changeLink) changeLink.remove();
}

// ── STATE ──
let leads = [];
let activeLead = null;
let activeTab = 'email';
let currentDemoHTML = '';

// ── INIT ──
window.addEventListener('load', () => {
  const saved = getKey();
  if(saved){
    document.getElementById('apiKeyInput').value = saved;
    setConnectedState();
  }
});

// ── FIND LEADS ──
async function findLeads(){
  if(!getKey()){
    showToast('⚠️ Add your Gemini API key first');
    document.getElementById('apiKeyInput').focus();
    return;
  }

  const biz = document.getElementById('bizType').value.trim() || 'dental clinic';
  const city = document.getElementById('bizCity').value.trim() || 'Austin, TX';
  const count = parseInt(document.getElementById('bizCount').value);
  const btn = document.getElementById('findBtn');

  btn.disabled = true;
  btn.textContent = '🔄 AI Researching...';
  showLoading(`Finding ${biz}s in ${city}...`, 'Searching · Scoring leads · Analyzing web presence');

  try {
    const prompt = `You are a lead researcher for a web designer targeting US small businesses.

Generate ${count} realistic ${biz} leads in ${city} that need a website or better web presence.

Return ONLY a JSON array, no markdown, no backticks, no explanation. Each object:
{
  "name": "Business name",
  "owner": "Owner first name only",
  "type": "${biz}",
  "city": "${city}",
  "phone": "US format: (555) 555-0100",
  "email": "business@gmail.com",
  "website_status": "no_website OR outdated OR poor_design",
  "google_rating": "3.8 to 4.9",
  "review_count": 20 to 400,
  "years_in_business": 1 to 20,
  "opportunity_score": 55 to 98,
  "pain_point": "Their single biggest problem a website solves"
}`;

    const raw = await callGemini(prompt);
    const clean = raw.trim().replace(/```json|```/g,'').trim();
    leads = JSON.parse(clean).map((l,i) => ({
      ...l,
      id: Date.now()+i,
      status: 'new',
      analysis: null,
      demoHTML: '',
      beforeAfter: null
    }));

  } catch(e) {
    leads = fallbackLeads(biz, city, count);
    showToast('⚠️ Using sample leads — check API key if unexpected');
  }

  renderLeadList();
  document.getElementById('leadCount').textContent = leads.length;
  btn.disabled = false;
  btn.textContent = '🔍 Find & Research Leads';
  if(leads.length > 0) openLead(leads[0].id);
  showToast(`✅ Found ${leads.length} leads in ${city}`);
}

// ── OPEN LEAD ──
async function openLead(id){
  const lead = leads.find(l => l.id === id);
  if(!lead) return;
  activeLead = lead;

  document.querySelectorAll('.lead-item').forEach(el => el.classList.remove('active'));
  const el = document.getElementById('li-'+id);
  if(el) el.classList.add('active');

  if(lead.analysis){ renderDossier(lead); return; }

  showLoading(`Analyzing ${lead.name}...`, 'Checking website · Writing pitch · Preparing outreach messages...');

  const myName = document.getElementById('myName').value || 'Alex';
  const myPrice = document.getElementById('myPrice').value || '$299';

  try {
    // Using Gemini API
    const analysisPrompt = `You are a web design sales consultant analyzing a US business for outreach.

Business: ${lead.name} | Type: ${lead.type} | City: ${lead.city}
Owner: ${lead.owner} | Website: ${lead.website_status}
Rating: ${lead.google_rating}★ (${lead.review_count} reviews) | Years: ${lead.years_in_business}
Pain: ${lead.pain_point}

Freelancer: Name=${myName}, Price=${myPrice}, Service=Professional website design

Return ONLY valid JSON, no markdown, no backticks:
{
  "website_verdict": "one sentence verdict",
  "website_score": 1-100,
  "missing_features": ["feature1","feature2","feature3","feature4"],
  "revenue_impact": "how weak web presence costs them money (1-2 sentences)",
  "pain_points": ["pain1","pain2","pain3"],
  "opportunities": ["opp1","opp2","opp3"],
  "pitch": "4-5 sentence personalized pitch. Start with their name. Mention rating + years + specific problems. End with question. Sound human.",
  "objections": [
    {"q":"We already have a website","a":"specific response"},
    {"q":"We can't afford it","a":"ROI focused response"},
    {"q":"How do I know it will work","a":"credibility response"},
    {"q":"I need to think about it","a":"urgency + next step response"}
  ],
  "email_subject": "curiosity-based subject line",
  "email_message": "complete cold email under 150 words. Hi [Owner], personalized, mention specific problem, your service, value, price ${myPrice}, soft CTA",
  "dm_message": "Instagram/Facebook DM under 80 words, casual but professional",
  "followup_message": "3-day follow-up under 60 words"
}`;

    const rawAnalysis = await callGemini(analysisPrompt);
    const cleanAnalysis = rawAnalysis.trim().replace(/```json|```/g,'').trim();
    lead.analysis = JSON.parse(cleanAnalysis);
    lead.status = 'analyzed';
    updateLeadBadge(id, 'analyzed');

  } catch(e) {
    lead.analysis = fallbackAnalysis(lead, myName, myPrice);
    lead.status = 'analyzed';
    updateLeadBadge(id, 'analyzed');
  }

  renderDossier(lead);
}

// ── RENDER DOSSIER ──
function renderDossier(lead){
  const a = lead.analysis;
  const isNoWeb = lead.website_status === 'no_website';

  document.getElementById('mainPanel').innerHTML = `
  <div class="dossier">

    <div class="dossier-top">
      <div>
        <div class="biz-name">${lead.name}</div>
        <div class="biz-meta">
          <span class="meta">📍 ${lead.city}</span>
          <span class="meta">⭐ ${lead.google_rating} (${lead.review_count} reviews)</span>
          <span class="meta">🏢 ${lead.years_in_business} yrs</span>
          <span class="meta">📞 ${lead.phone}</span>
          <span class="meta">✉ ${lead.email}</span>
        </div>
        <div class="status-row">
          ${['new','analyzed','sent','replied','booked','rejected'].map(s=>`
            <button class="st-btn ${lead.status===s?'active':''}" onclick="setStatus(${lead.id},'${s}')">${sEmoji(s)} ${s}</button>
          `).join('')}
        </div>
      </div>
      <div class="score-box">
        <div class="score-num">${lead.opportunity_score}</div>
        <div class="score-lbl">Opportunity</div>
      </div>
    </div>

    <!-- WEBSITE ANALYSIS -->
    <div class="d-card">
      <div class="d-card-head">
        <span class="d-card-icon">🌐</span>
        <span class="d-card-title">Website Analysis</span>
        <span class="d-card-badge">${wsLabel(lead.website_status)}</span>
      </div>
      <div class="d-card-body">
        <div style="background:var(--surface);border-left:3px solid ${a.website_score<40?'var(--red)':a.website_score<70?'var(--amber)':'var(--green)'};border-radius:7px;padding:12px;margin-bottom:12px">
          <div style="font-size:13px;font-weight:600;color:var(--white);margin-bottom:3px">${a.website_verdict}</div>
          <div style="font-size:11px;color:var(--muted)">Health score: <span style="font-weight:700;color:${a.website_score<40?'var(--red)':a.website_score<70?'var(--amber)':'var(--green)'}">${a.website_score}/100</span></div>
        </div>
        <div class="two-col">
          <div class="info-card">
            <div class="ic-label">Revenue Impact</div>
            <div class="ic-val warn">${a.revenue_impact}</div>
          </div>
          <div class="info-card">
            <div class="ic-label">Missing Features</div>
            <div class="missing-list">${(a.missing_features||[]).map(f=>`<div class="missing-item"><span>✗</span><span>${f}</span></div>`).join('')}</div>
          </div>
        </div>
      </div>
    </div>

    <!-- DEMO / BEFORE-AFTER -->
    <div class="d-card">
      <div class="d-card-head">
        <span class="d-card-icon">${isNoWeb?'🏗️':'🔄'}</span>
        <span class="d-card-title">${isNoWeb?'Generate Demo Website':'Before / After Analysis'}</span>
        <span class="d-card-badge" style="background:rgba(34,197,94,.1);color:var(--green);border:1px solid rgba(34,197,94,.15)">${isNoWeb?'Show them what they\'re missing':'Show the transformation'}</span>
      </div>
      <div class="d-card-body">
        ${isNoWeb
          ? `<div style="background:rgba(34,197,94,.06);border:1px solid rgba(34,197,94,.15);border-radius:8px;padding:12px;margin-bottom:12px;font-size:12px;color:var(--sub);line-height:1.6"><strong style="color:var(--green)">Strategy:</strong> Build a live demo website with their real business name. Send the link in your pitch email. Seeing their own name on a professional site closes deals instantly.</div>
            <div id="demoArea">${lead.demoHTML
              ? `<div style="display:flex;gap:8px"><button class="btn btn-green" onclick="openDemoModal(${lead.id})">👁 View Demo Website</button><button class="btn btn-outline" onclick="generateDemo(${lead.id})">🔄 Regenerate</button></div>`
              : `<button class="btn btn-green" onclick="generateDemo(${lead.id})">🏗️ Generate Demo Website for ${lead.name}</button><div style="font-size:11px;color:var(--muted);margin-top:6px">Takes ~10 seconds · Real working website using their details</div>`
            }</div>`
          : `<div style="background:rgba(240,165,0,.06);border:1px solid rgba(240,165,0,.15);border-radius:8px;padding:12px;margin-bottom:12px;font-size:12px;color:var(--sub);line-height:1.6"><strong style="color:var(--amber)">Strategy:</strong> Show them exact problems with their current site and what the redesign will look like. Visual proof is the most powerful sales tool.</div>
            <div id="demoArea">${lead.beforeAfter
              ? renderBAHTML(lead.beforeAfter, lead.id)
              : `<button class="btn btn-amber" onclick="generateBA(${lead.id})">🔄 Generate Before / After Analysis</button><div style="font-size:11px;color:var(--muted);margin-top:6px">AI shows exact problems + improvements with expected ROI</div>`
            }</div>`
        }
      </div>
    </div>

    <!-- PAIN & OPPORTUNITY -->
    <div class="two-col">
      <div class="d-card">
        <div class="d-card-head"><span class="d-card-icon">🔴</span><span class="d-card-title">Their Pain Points</span></div>
        <div class="d-card-body">
          <div class="pain-list">${(a.pain_points||[]).map(p=>`<div class="pain-item"><span>⚠️</span><span>${p}</span></div>`).join('')}</div>
        </div>
      </div>
      <div class="d-card">
        <div class="d-card-head"><span class="d-card-icon">🟢</span><span class="d-card-title">Your Opportunities</span></div>
        <div class="d-card-body">
          <div class="opp-list">${(a.opportunities||[]).map(o=>`<div class="opp-item"><span>✅</span><span>${o}</span></div>`).join('')}</div>
        </div>
      </div>
    </div>

    <!-- PITCH -->
    <div class="d-card">
      <div class="d-card-head"><span class="d-card-icon">🎯</span><span class="d-card-title">Personalized Pitch</span><span class="d-card-badge">AI Generated for ${lead.name}</span></div>
      <div class="d-card-body">
        <div class="pitch-box">${a.pitch}</div>
        <div class="actions-row"><button class="btn btn-outline" onclick="copyTxt(\`${esc(a.pitch)}\`)">📋 Copy Pitch</button></div>
      </div>
    </div>

    <!-- OBJECTIONS -->
    <div class="d-card">
      <div class="d-card-head"><span class="d-card-icon">🛡️</span><span class="d-card-title">Objection Handling</span><span class="d-card-badge">4 Responses Ready</span></div>
      <div class="d-card-body">
        <div class="obj-list">${(a.objections||[]).map(o=>`
          <div class="obj-item">
            <div class="obj-q">❓ "${o.q}"</div>
            <div class="obj-a">💬 ${o.a}</div>
          </div>`).join('')}
        </div>
      </div>
    </div>

    <!-- MESSAGES -->
    <div class="d-card">
      <div class="d-card-head"><span class="d-card-icon">✉️</span><span class="d-card-title">Outreach Messages</span><span class="d-card-badge">Ready to Send</span></div>
      <div class="d-card-body">
        <div class="msg-tabs">
          <button class="msg-tab ${activeTab==='email'?'active':''}" onclick="switchTab('email',${lead.id})">📧 Email</button>
          <button class="msg-tab ${activeTab==='dm'?'active':''}" onclick="switchTab('dm',${lead.id})">💬 DM</button>
          <button class="msg-tab ${activeTab==='followup'?'active':''}" onclick="switchTab('followup',${lead.id})">🔄 Follow-up</button>
        </div>
        ${activeTab==='email'?`
          <div class="msg-subject"><span>Subject:</span> ${a.email_subject||''}</div>
          <div class="msg-content" id="msgContent">${a.email_message||''}</div>
        `:`<div class="msg-content" id="msgContent">${activeTab==='dm'?a.dm_message||'':a.followup_message||''}</div>`}
        <div class="actions-row">
          <button class="btn btn-amber" onclick="copyActiveMsg()">📋 Copy Message</button>
          <button class="btn btn-green" onclick="setStatus(${lead.id},'sent');showToast('✅ Marked sent!')">✅ Mark Sent</button>
          <button class="btn btn-outline" onclick="openGmail('${lead.email}','${esc(a.email_subject||'')}','${esc(a.email_message||'')}')">📧 Open Gmail</button>
        </div>
      </div>
    </div>

    <!-- CONTACT -->
    <div class="d-card">
      <div class="d-card-head"><span class="d-card-icon">📋</span><span class="d-card-title">Contact Details</span></div>
      <div class="d-card-body">
        <div class="two-col">
          <div class="info-card"><div class="ic-label">Owner</div><div class="ic-val">${lead.owner}</div></div>
          <div class="info-card"><div class="ic-label">Phone</div><div class="ic-val mono">${lead.phone}</div></div>
          <div class="info-card"><div class="ic-label">Email</div><div class="ic-val mono" style="font-size:11px;word-break:break-all">${lead.email}</div></div>
          <div class="info-card"><div class="ic-label">Business</div><div class="ic-val">${lead.type} · ${lead.city}</div></div>
        </div>
        <div class="actions-row" style="margin-top:12px">
          <button class="btn btn-outline" onclick="copyTxt('${lead.email}')">📋 Copy Email</button>
          <button class="btn btn-outline" onclick="copyTxt('${lead.phone}')">📋 Copy Phone</button>
          <button class="btn btn-amber" onclick="openGmail('${lead.email}','${esc(a.email_subject||'')}','${esc(a.email_message||'')}')">📧 Open in Gmail</button>
        </div>
      </div>
    </div>

  </div>`;
}

// ── DEMO WEBSITE GENERATOR ──
async function generateDemo(id){
  const lead = leads.find(l => l.id === id);
  if(!lead) return;
  const area = document.getElementById('demoArea');
  if(area) area.innerHTML = `<div style="display:flex;align-items:center;gap:10px;color:var(--green);font-size:13px"><div class="loader" style="width:20px;height:20px;border-width:2px"></div>Building demo website for ${lead.name}...</div>`;

  try {
    const demoPrompt = `Build a complete professional single-page HTML website for this US business.

Business: \${lead.name} | Type: \${lead.type} | City: \${lead.city}
Phone: \${lead.phone} | Email: \${lead.email}
Rating: \${lead.google_rating}★ | Reviews: \${lead.review_count} | Years: \${lead.years_in_business}

Requirements:
- Complete self-contained HTML with all CSS in style tags
- Professional modern design appropriate for a \${lead.type}
- Sections: Hero, Services, About/Stats, Testimonials (3), Contact with phone+email
- Mobile responsive with good color scheme
- Google Fonts from fonts.googleapis.com
- Clear Book Now or Contact Us CTA button
- Use emojis instead of images
- Look like a 500 dollar professional website
- Return ONLY the complete HTML starting with DOCTYPE html`;

    const html = await callGemini(demoPrompt);
    lead.demoHTML = html;
    currentDemoHTML = html;
    openDemoModal(id);
    if(area) area.innerHTML = `<div style="display:flex;gap:8px;flex-wrap:wrap"><button class="btn btn-green" onclick="openDemoModal(${id})">👁 View Demo Website</button><button class="btn btn-outline" onclick="copyDemoHTML()">📋 Copy HTML</button><button class="btn btn-outline" onclick="generateDemo(${id})">🔄 Regenerate</button></div><div style="font-size:11px;color:var(--muted);margin-top:8px">📧 Tell clients: "I already built a demo for ${lead.name} — here's the link" (after hosting on Netlify/GitHub)</div>`;

  } catch(e) {
    lead.demoHTML = fallbackDemoSite(lead);
    currentDemoHTML = lead.demoHTML;
    openDemoModal(id);
    if(area) area.innerHTML = `<div style="display:flex;gap:8px"><button class="btn btn-green" onclick="openDemoModal(${id})">👁 View Demo</button><button class="btn btn-outline" onclick="generateDemo(${id})">🔄 Retry with AI</button></div>`;
  }
}

// ── BEFORE/AFTER GENERATOR ──
async function generateBA(id){
  const lead = leads.find(l => l.id === id);
  if(!lead) return;
  const area = document.getElementById('demoArea');
  if(area) area.innerHTML = `<div style="display:flex;align-items:center;gap:10px;color:var(--amber);font-size:13px"><div class="loader" style="width:20px;height:20px;border-width:2px;border-top-color:var(--amber)"></div>Analyzing ${lead.name}'s website...</div>`;

  try {
    const baPrompt = `Create a before/after website analysis for sales pitch purposes.

Business: \${lead.name} | Type: \${lead.type} | City: \${lead.city}
Current website: \${lead.website_status} | Known problems: \${(lead.analysis?.missing_features||[]).join(', ')}

Return ONLY valid JSON, no markdown, no backticks:
{
  "before_score": 15-45,
  "before_issues": [
    {"label":"issue","detail":"business impact"},
    {"label":"issue","detail":"business impact"},
    {"label":"issue","detail":"business impact"},
    {"label":"issue","detail":"business impact"}
  ],
  "after_score": 88-97,
  "after_improvements": [
    {"label":"improvement","detail":"business benefit"},
    {"label":"improvement","detail":"business benefit"},
    {"label":"improvement","detail":"business benefit"},
    {"label":"improvement","detail":"business benefit"}
  ],
  "expected_results": ["result with number","result with number","result with number"],
  "summary": "2 sentence transformation summary for pitch email"
}`;

    const rawBA = await callGemini(baPrompt);
    const cleanBA = rawBA.trim().replace(/```json|```/g,'').trim();
    lead.beforeAfter = JSON.parse(cleanBA);
    if(area) area.innerHTML = renderBAHTML(lead.beforeAfter, id);

  } catch(e) {
    lead.beforeAfter = fallbackBA(lead);
    if(area) area.innerHTML = renderBAHTML(lead.beforeAfter, id);
  }
}

function renderBAHTML(ba, id){
  return `
    <div class="ba-grid">
      <div class="ba-col before">
        <div class="ba-head before">❌ Current State <span>${ba.before_score}/100</span></div>
        <div class="ba-body">
          ${(ba.before_issues||[]).map(i=>`<div class="ba-item bad"><span>✗</span><div><strong>${i.label}</strong><br/><span style="opacity:.8">${i.detail}</span></div></div>`).join('')}
        </div>
      </div>
      <div class="ba-col after">
        <div class="ba-head after">✅ After Redesign <span>${ba.after_score}/100</span></div>
        <div class="ba-body">
          ${(ba.after_improvements||[]).map(i=>`<div class="ba-item good"><span>✓</span><div><strong>${i.label}</strong><br/><span style="opacity:.8">${i.detail}</span></div></div>`).join('')}
        </div>
      </div>
    </div>
    <div style="background:rgba(240,165,0,.07);border:1px solid rgba(240,165,0,.15);border-radius:8px;padding:12px;margin-top:10px">
      <div style="font-size:11px;font-weight:700;color:var(--amber);margin-bottom:6px">Expected Results</div>
      <div style="display:flex;gap:6px;flex-wrap:wrap;margin-bottom:8px">${(ba.expected_results||[]).map(r=>`<span style="background:rgba(240,165,0,.1);border:1px solid rgba(240,165,0,.2);color:var(--amber);font-size:11px;font-weight:600;padding:3px 10px;border-radius:100px">${r}</span>`).join('')}</div>
      <div style="font-size:12px;color:var(--sub);line-height:1.6">${ba.summary||''}</div>
    </div>
    <div class="actions-row" style="margin-top:10px">
      <button class="btn btn-amber" onclick="copyBAPitch(${id})">📋 Copy for Email</button>
      <button class="btn btn-outline" onclick="generateBA(${id})">🔄 Regenerate</button>
    </div>`;
}

function copyBAPitch(id){
  const lead = leads.find(l => l.id === id);
  if(!lead || !lead.beforeAfter) return;
  const ba = lead.beforeAfter;
  const text = `Hi ${lead.owner},\n\nI analyzed ${lead.name}'s online presence and here's what I found:\n\nCURRENT WEBSITE (Score: ${ba.before_score}/100)\n${(ba.before_issues||[]).map(i=>`✗ ${i.label}: ${i.detail}`).join('\n')}\n\nAFTER REDESIGN (Score: ${ba.after_score}/100)\n${(ba.after_improvements||[]).map(i=>`✓ ${i.label}: ${i.detail}`).join('\n')}\n\n${ba.summary}\n\nExpected: ${(ba.expected_results||[]).join(' · ')}\n\nWould a quick 10-min call work this week?`;
  navigator.clipboard.writeText(text);
  showToast('📋 Before/After pitch copied!');
}

// ── DEMO MODAL ──
function openDemoModal(id){
  const lead = leads.find(l => l.id === id);
  if(!lead || !lead.demoHTML) return;
  currentDemoHTML = lead.demoHTML;
  document.getElementById('demoTitle').textContent = lead.name + ' — Demo Website';
  document.getElementById('demoFrame').srcdoc = lead.demoHTML;
  document.getElementById('demoModal').classList.add('open');
}
function closeDemoModal(){
  document.getElementById('demoModal').classList.remove('open');
  document.getElementById('demoFrame').srcdoc = '';
}
function copyDemoHTML(){
  navigator.clipboard.writeText(currentDemoHTML);
  showToast('📋 HTML copied! Save as index.html and upload to GitHub Pages');
}

// ── TAB & STATUS ──
function switchTab(tab, id){
  activeTab = tab;
  const lead = leads.find(l => l.id === id);
  if(lead && lead.analysis) renderDossier(lead);
}
function setStatus(id, status){
  const lead = leads.find(l => l.id === id);
  if(!lead) return;
  lead.status = status;
  updateLeadBadge(id, status);
  if(activeLead && activeLead.id === id && lead.analysis) renderDossier(lead);
}
function updateLeadBadge(id, status){
  const el = document.getElementById('li-'+id);
  if(!el) return;
  const badge = el.querySelector('.li-badge');
  if(badge){ badge.className=`li-badge b-${status}`; badge.textContent=sEmoji(status)+' '+status; }
}
function sEmoji(s){ return {new:'🔵',analyzed:'🟡',sent:'📤',replied:'💬',booked:'🎯',rejected:'❌'}[s]||''; }
function wsLabel(s){ return {no_website:'No Website',outdated:'Outdated',poor_design:'Poor Design',decent:'Exists'}[s]||s; }

// ── RENDER LEAD LIST ──
function renderLeadList(){
  document.getElementById('leadList').innerHTML = leads.map(l=>`
    <div class="lead-item" id="li-${l.id}" onclick="openLead(${l.id})">
      <div class="li-top">
        <div class="li-name">${l.name}</div>
        <div class="li-score">${l.opportunity_score}</div>
      </div>
      <div class="li-meta">📍 ${l.city}</div>
      <span class="li-badge b-${l.status}">${sEmoji(l.status)} ${l.status}</span>
    </div>`).join('');
}

// ── LOADING STATE ──
function showLoading(title, sub){
  document.getElementById('mainPanel').innerHTML = `
    <div class="loading">
      <div class="loader"></div>
      <div class="loading-step">${title}</div>
      <div class="loading-text" style="max-width:320px">${sub}</div>
    </div>`;
}

// ── UTILS ──
function copyActiveMsg(){
  const el = document.getElementById('msgContent');
  if(!el) return;
  navigator.clipboard.writeText(el.textContent);
  showToast('📋 Message copied! Ready to send.');
}
function copyTxt(text){ navigator.clipboard.writeText(text); showToast('📋 Copied!'); }
function openGmail(email, subject, body){
  window.open(`https://mail.google.com/mail/?view=cm&to=${encodeURIComponent(email)}&su=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`, '_blank');
}
function esc(str){ return (str||'').replace(/`/g,'\\`').replace(/\\/g,'\\\\'); }
function showToast(msg){
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'), 3000);
}

// ── FALLBACK DATA ──
function fallbackLeads(biz, city, count){
  const names=['Sunrise','Premier','City','Elite','Quality','Pro','Best','Top','Metro','Central','Golden','Royal'];
  const owners=['Mike','Sarah','John','Lisa','David','Amy','Robert','Jennifer','Chris','Karen','James','Emily'];
  const statuses=['no_website','outdated','poor_design','no_website','outdated','poor_design'];
  return Array.from({length:count},(_,i)=>({
    id:Date.now()+i,
    name:`${names[i%names.length]} ${biz.split(' ').map(w=>w.charAt(0).toUpperCase()+w.slice(1)).join(' ')}`,
    owner:owners[i%owners.length],type:biz,city,
    phone:`(${Math.floor(200+Math.random()*700)}) ${Math.floor(200+Math.random()*700)}-${Math.floor(1000+Math.random()*9000)}`,
    email:`info@${names[i%names.length].toLowerCase()}${biz.replace(/\s+/g,'').toLowerCase()}.com`,
    website_status:statuses[i%statuses.length],
    google_rating:(3.8+Math.random()*1.1).toFixed(1),
    review_count:Math.floor(20+Math.random()*300),
    years_in_business:Math.floor(1+Math.random()*18),
    opportunity_score:Math.floor(60+Math.random()*38),
    pain_point:'Losing customers to competitors with better websites',
    status:'new',analysis:null,demoHTML:'',beforeAfter:null
  }));
}
function fallbackAnalysis(lead, myName, myPrice){
  return {
    website_verdict:lead.website_status==='no_website'?'No website found — completely invisible online':'Website exists but losing customers daily',
    website_score:lead.website_status==='no_website'?8:32,
    missing_features:['Mobile-friendly design','Online booking system','Fast loading speed','Clear contact info'],
    revenue_impact:`With ${lead.review_count} Google reviews and ${lead.google_rating}★ rating, ${lead.name} has strong reputation but loses online customers to competitors with professional websites.`,
    pain_points:['Invisible to people searching online','No way to book after hours','Missing 60% of mobile searches'],
    opportunities:['Build website that ranks on Google','Add online booking to capture leads 24/7','Mobile-first design for smartphone users'],
    pitch:`Hi ${lead.owner}, I came across ${lead.name} on Google and was impressed by your ${lead.google_rating}★ rating with ${lead.review_count} reviews — clearly you're doing great work in ${lead.city}. But I also noticed ${lead.website_status==='no_website'?"you don't have a website yet, which means you're invisible to the 80% of customers who search online before visiting":'your current website may be costing you customers who leave within seconds on mobile'}. I specialize in building professional websites for ${lead.type}s that actually bring in new customers, starting at ${myPrice}. Would it be worth a quick 10-minute call this week?`,
    objections:[
      {q:'We already have a website',a:`Great! Most ${lead.type} websites I see aren't built to convert visitors. I'd love to show you 3 specific improvements that could bring more inquiries — free, no obligation.`},
      {q:"We can't afford it",a:`I start at ${myPrice} — about the cost of one new customer. Most clients see that returned in the first 2 weeks from new bookings alone. Payment plans available too.`},
      {q:'How do I know it will work',a:`I can show you similar ${lead.type}s I've built and their results. I also offer unlimited revisions until you're completely happy with the design.`},
      {q:'I need to think about it',a:`Of course! Can I send you a quick audit showing exactly what your website is missing? Takes me 5 minutes and gives you something concrete to evaluate.`}
    ],
    email_subject:`Quick question about ${lead.name}'s online presence`,
    email_message:`Hi ${lead.owner},\n\nI came across ${lead.name} on Google and was impressed by your ${lead.google_rating}★ rating — clearly you're doing great work in ${lead.city}.\n\nI also noticed ${lead.website_status==='no_website'?"you don't have a website yet":'your website could use some improvements'} — which means you're likely missing customers who search online before visiting.\n\nI build professional websites for ${lead.type}s starting at ${myPrice} — mobile-friendly, fast, and designed to bring in real customers.\n\nWould you be open to a quick 10-minute call this week?\n\nBest,\n${myName}`,
    dm_message:`Hi ${lead.owner}! Found ${lead.name} on Google — love the ${lead.google_rating}★ reviews. I build websites for ${lead.type}s and noticed you could use a stronger online presence. Starting at ${myPrice}. Worth a quick chat?`,
    followup_message:`Hi ${lead.owner}, following up on my email about ${lead.name}'s website. I know things get busy — would a 10-minute call work this week? Happy to show examples first.`
  };
}
function fallbackDemoSite(lead){
  return `<!DOCTYPE html><html><head><meta charset="UTF-8"/><meta name="viewport" content="width=device-width,initial-scale=1"/><title>${lead.name}</title><link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Inter:wght@400;500;600&display=swap" rel="stylesheet"/><style>*{box-sizing:border-box;margin:0;padding:0}body{font-family:'Inter',sans-serif}nav{background:#1F4E79;padding:16px 40px;display:flex;justify-content:space-between;align-items:center}.nav-logo{font-family:'Playfair Display',serif;font-size:22px;color:#fff}.nav-btn{background:#fff;color:#1F4E79;padding:10px 22px;border-radius:6px;font-size:14px;font-weight:700;border:none;cursor:pointer}.hero{background:linear-gradient(135deg,#1F4E79,#2E75B6);padding:100px 40px;text-align:center;color:#fff}.hero h1{font-family:'Playfair Display',serif;font-size:52px;margin-bottom:20px}.hero p{font-size:18px;opacity:.85;max-width:560px;margin:0 auto 36px}.hero-btn{background:#fff;color:#1F4E79;padding:16px 36px;border-radius:8px;font-size:16px;font-weight:700;text-decoration:none;display:inline-block}.stats{display:flex;justify-content:center;background:#E8F0F8;padding:32px;flex-wrap:wrap;gap:0}.stat{text-align:center;padding:0 40px;border-right:1px solid #c0d4e8}.stat:last-child{border-right:none}.stat-n{font-family:'Playfair Display',serif;font-size:36px;color:#1F4E79;font-weight:700}.stat-l{font-size:13px;color:#666;margin-top:4px}.services{padding:80px 40px;max-width:1100px;margin:0 auto;text-align:center}.services h2{font-family:'Playfair Display',serif;font-size:40px;margin-bottom:48px}.svc-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:24px}.svc-card{background:#E8F0F8;border-radius:14px;padding:32px 24px}.svc-icon{font-size:36px;margin-bottom:16px}.svc-card h3{font-size:18px;font-weight:700;color:#1F4E79;margin-bottom:10px}.svc-card p{font-size:14px;color:#666;line-height:1.65}.cta{background:#1F4E79;padding:80px 40px;text-align:center;color:#fff}.cta h2{font-family:'Playfair Display',serif;font-size:44px;margin-bottom:16px}.cta p{font-size:18px;opacity:.8;margin-bottom:32px}.contact-grid{display:flex;justify-content:center;gap:20px;flex-wrap:wrap}.contact-item{background:rgba(255,255,255,.1);border-radius:10px;padding:14px 22px;font-size:14px}footer{background:#1a1a1a;color:rgba(255,255,255,.5);padding:24px;text-align:center;font-size:13px}@media(max-width:768px){.svc-grid{grid-template-columns:1fr}.hero h1{font-size:36px}}</style></head><body><nav><div class="nav-logo">${lead.name}</div><button class="nav-btn">Book Appointment</button></nav><div class="hero"><h1>Welcome to ${lead.name}</h1><p>Serving ${lead.city} with excellence for ${lead.years_in_business} years. Rated ${lead.google_rating}★ by ${lead.review_count}+ happy customers.</p><a href="#contact" class="hero-btn">Book Your Appointment →</a></div><div class="stats"><div class="stat"><div class="stat-n">${lead.google_rating}★</div><div class="stat-l">Google Rating</div></div><div class="stat"><div class="stat-n">${lead.review_count}+</div><div class="stat-l">Happy Customers</div></div><div class="stat"><div class="stat-n">${lead.years_in_business}</div><div class="stat-l">Years Experience</div></div><div class="stat"><div class="stat-n">24/7</div><div class="stat-l">Online Booking</div></div></div><div class="services"><h2>Our Services</h2><div class="svc-grid"><div class="svc-card"><div class="svc-icon">⭐</div><h3>Premium Service</h3><p>Top-quality ${lead.type} services tailored to your specific needs.</p></div><div class="svc-card"><div class="svc-icon">🏆</div><h3>Expert Team</h3><p>Experienced professionals dedicated to delivering the best results.</p></div><div class="svc-card"><div class="svc-icon">📅</div><h3>Easy Booking</h3><p>Book appointments online 24/7 at your convenience.</p></div></div></div><div class="cta" id="contact"><h2>Ready to Get Started?</h2><p>Contact us today and experience the ${lead.name} difference.</p><div class="contact-grid"><div class="contact-item">📞 ${lead.phone}</div><div class="contact-item">✉ ${lead.email}</div><div class="contact-item">📍 ${lead.city}</div></div></div><footer>© ${new Date().getFullYear()} ${lead.name} · ${lead.city} · All rights reserved</footer></body></html>`;
}
function fallbackBA(lead){
  return {
    before_score:22,
    before_issues:[
      {label:'Not Mobile Friendly',detail:'60% of customers search on phones — site breaks on every smartphone'},
      {label:'No Online Booking',detail:'Customers who can\'t book instantly go to a competitor'},
      {label:'Slow Loading',detail:'Google penalizes slow sites — invisible in search results'},
      {label:'No Clear CTA',detail:'Visitors don\'t know what to do next — they leave immediately'}
    ],
    after_score:94,
    after_improvements:[
      {label:'Mobile-First Design',detail:'Perfect on all devices — captures 60% of phone searchers'},
      {label:'Online Booking',detail:'Capture appointments 24/7, even when closed'},
      {label:'Fast Loading',detail:'Under 2 seconds — Google rewards with higher rankings'},
      {label:'Clear Book Now Button',detail:'Visitors convert to customers in one tap'}
    ],
    expected_results:['40-60% more online inquiries','First page Google in 60 days','24/7 appointment capture'],
    summary:`Redesigning ${lead.name}'s website from its current state to a modern, mobile-first design would directly convert their strong ${lead.google_rating}★ reputation into actual online bookings.`
  };
}
</script>
</body>
</html>
