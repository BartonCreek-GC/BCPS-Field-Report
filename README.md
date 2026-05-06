<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>BCPS Field Log</title>
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@400;600;700;800;900&family=Barlow:wght@400;500;600&display=swap" rel="stylesheet">
<style>
:root {
  --ink:#111820; --ink-mid:#1a2535; --ink-card:rgba(26,37,53,0.95);
  --gold:#e8a020; --gold-dark:#c4861a; --gold-glow:rgba(232,160,32,0.12); --gold-border:rgba(232,160,32,0.3);
  --slate:#8fa5c0; --border:rgba(143,165,192,0.18); --white:#f0f4f8;
  --green:#2ecc71; --red:#e74c3c; --blue:#3b82f6;
  --r:8px; --input-bg:rgba(17,24,32,0.7);
}
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent;}
html,body{height:auto;min-height:100%;}
body{font-family:'Barlow',sans-serif;background:var(--ink);color:var(--white);
  background-image:radial-gradient(ellipse 80% 40% at 50% -10%,rgba(232,160,32,0.07) 0%,transparent 60%);}

/* HEADER */
.app-header{background:linear-gradient(135deg,var(--ink-mid),var(--ink));border-bottom:3px solid var(--gold);
  padding:12px 16px 0;position:sticky;top:0;z-index:50;box-shadow:0 4px 24px rgba(0,0,0,0.5);}
.header-row{display:flex;align-items:center;justify-content:space-between;margin-bottom:10px;}
.brand{display:flex;align-items:center;gap:10px;}
.brand-badge{background:var(--gold);color:var(--ink);font-family:'Barlow Condensed',sans-serif;
  font-weight:900;font-size:13px;letter-spacing:1px;padding:5px 9px;border-radius:5px;line-height:1.2;}
.brand-text h1{font-family:'Barlow Condensed',sans-serif;font-size:20px;font-weight:800;line-height:1;}
.brand-text p{font-size:10px;color:var(--slate);letter-spacing:2px;text-transform:uppercase;margin-top:1px;}
.admin-btn{background:none;border:1px solid var(--border);color:var(--slate);font-size:11px;font-weight:600;
  letter-spacing:1px;text-transform:uppercase;padding:6px 10px;border-radius:var(--r);cursor:pointer;
  font-family:'Barlow Condensed',sans-serif;transition:all 0.2s;}
.admin-btn:hover{border-color:var(--gold);color:var(--gold);}
.tab-bar{display:flex;}
.tab-btn{flex:1;padding:9px 4px;background:none;border:none;font-family:'Barlow Condensed',sans-serif;
  font-size:11px;font-weight:700;letter-spacing:1px;color:var(--slate);cursor:pointer;
  border-bottom:3px solid transparent;text-transform:uppercase;position:relative;bottom:-3px;transition:all 0.2s;}
.tab-btn.active{color:var(--gold);border-bottom-color:var(--gold);}

/* PAGES */
.tab-page{display:none;padding:14px;max-width:700px;margin:0 auto;padding-bottom:50px;}
.tab-page.active{display:block;}

/* CARDS */
.card{background:var(--ink-card);border:1px solid var(--border);border-radius:var(--r);padding:14px;margin-bottom:12px;}
.card-hd{display:flex;align-items:center;gap:8px;margin-bottom:12px;padding-bottom:10px;border-bottom:1px solid var(--border);}
.card-ico{width:26px;height:26px;background:var(--gold-glow);border:1px solid var(--gold-border);border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:13px;}
.card-ttl{font-family:'Barlow Condensed',sans-serif;font-size:14px;font-weight:700;letter-spacing:1.5px;text-transform:uppercase;color:var(--gold);flex:1;}
.card-badge{font-size:10px;font-weight:700;letter-spacing:1px;padding:3px 8px;border-radius:20px;border:1px solid var(--gold-border);color:var(--gold);background:var(--gold-glow);font-family:'Barlow Condensed',sans-serif;}

/* FORM */
label{display:block;font-size:10px;font-weight:600;letter-spacing:1.5px;text-transform:uppercase;color:var(--slate);margin-bottom:4px;}
input[type=text],input[type=date],input[type=number],input[type=password],textarea,select{
  width:100%;background:var(--input-bg);border:1px solid var(--border);border-radius:var(--r);color:var(--white);
  font-family:'Barlow',sans-serif;font-size:14px;padding:9px 11px;outline:none;transition:border-color 0.2s,box-shadow 0.2s;-webkit-appearance:none;}
input:focus,textarea:focus,select:focus{border-color:var(--gold);box-shadow:0 0 0 3px var(--gold-glow);}
input[type=date]::-webkit-calendar-picker-indicator{filter:invert(0.6);}
select option{background:var(--ink-mid);}
textarea{resize:vertical;min-height:72px;}
.frow{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:10px;}
.ff{margin-bottom:10px;}

/* TAG MULTISELECT */
.tag-box{display:flex;flex-wrap:wrap;gap:6px;padding:8px;background:var(--input-bg);border:1px solid var(--border);border-radius:var(--r);min-height:42px;}
.tag-pill{padding:4px 11px;border-radius:20px;font-size:11px;font-weight:700;font-family:'Barlow Condensed',sans-serif;cursor:pointer;border:1px solid;transition:all 0.15s;user-select:none;letter-spacing:0.5px;}
.tag-pill.off{color:var(--slate);border-color:var(--border);background:none;}
.tag-pill.on{color:var(--ink);border-color:var(--gold);background:var(--gold);}
.tag-placeholder{font-size:12px;color:var(--slate);align-self:center;}

/* TABLES */
.mp-wrap{overflow-x:auto;margin-bottom:10px;}
.mp-table{width:100%;border-collapse:collapse;font-size:12px;min-width:400px;}
.mp-table thead tr{background:rgba(232,160,32,0.08);border-bottom:1px solid var(--gold-border);}
.mp-table th{padding:7px 6px;text-align:left;font-family:'Barlow Condensed',sans-serif;font-size:10px;font-weight:700;letter-spacing:1px;text-transform:uppercase;color:var(--gold);}
.mp-table td{padding:3px 4px;border-bottom:1px solid var(--border);}
.mp-table td input,.mp-table td select{padding:7px;font-size:12px;background:rgba(17,24,32,0.6);}
.mp-table .tot-row td{border-top:2px solid var(--gold-border);padding-top:8px;font-family:'Barlow Condensed',sans-serif;font-size:13px;font-weight:700;color:var(--gold);}
.rm-btn{background:none;border:none;cursor:pointer;color:var(--red);font-size:15px;padding:4px;}
.add-row-btn{width:100%;padding:8px;background:none;border:1px dashed var(--border);border-radius:var(--r);color:var(--slate);font-size:12px;font-weight:600;letter-spacing:1px;text-transform:uppercase;cursor:pointer;font-family:'Barlow Condensed',sans-serif;transition:all 0.2s;}
.add-row-btn:hover{border-color:var(--gold);color:var(--gold);}

/* WORK ROWS */
.work-row{background:var(--input-bg);border:1px solid var(--border);border-radius:var(--r);padding:10px;margin-bottom:8px;}
.work-row-top{display:flex;gap:8px;align-items:center;margin-bottom:8px;}
.work-row-top select{flex:1;}

/* PHOTOS */
.drop-zone{border:2px dashed var(--gold-border);border-radius:var(--r);padding:20px 14px;text-align:center;cursor:pointer;transition:all 0.2s;margin-bottom:10px;background:var(--gold-glow);}
.drop-zone:hover,.drop-zone.on{border-color:var(--gold);background:rgba(232,160,32,0.18);}
.drop-zone .di{font-size:28px;margin-bottom:6px;}
.drop-zone p{font-size:12px;color:var(--slate);}
.drop-zone strong{color:var(--gold);}
#photoInput{display:none;}
.photo-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:8px;}
.photo-card{background:var(--input-bg);border:1px solid var(--border);border-radius:var(--r);overflow:hidden;}
.photo-card img{width:100%;aspect-ratio:4/3;object-fit:cover;display:block;}
.photo-card .pc-cap{padding:6px 8px;}
.photo-card .pc-cap input{font-size:11px;padding:5px 7px;border-color:transparent;}
.photo-card .pc-rm{text-align:right;padding:2px 6px 4px;}

/* PUNCH FIELD */
.pf-item{background:var(--input-bg);border:1px solid var(--border);border-radius:var(--r);padding:12px;margin-bottom:8px;}
.pf-row{display:flex;align-items:flex-start;gap:10px;}
.pf-chk{width:22px;height:22px;flex-shrink:0;appearance:none;-webkit-appearance:none;background:var(--input-bg);border:2px solid var(--border);border-radius:4px;cursor:pointer;position:relative;transition:all 0.15s;margin-top:2px;}
.pf-chk:checked{background:var(--green);border-color:var(--green);}
.pf-chk:checked::after{content:'✓';position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);color:#fff;font-size:13px;font-weight:700;}
.pf-body{flex:1;}
.pf-desc{font-size:14px;font-weight:600;margin-bottom:5px;}
.pf-meta{display:flex;gap:7px;flex-wrap:wrap;align-items:center;}
.pf-tag{font-size:10px;font-weight:700;padding:2px 8px;border-radius:20px;background:var(--gold-glow);border:1px solid var(--gold-border);color:var(--gold);font-family:'Barlow Condensed',sans-serif;text-transform:uppercase;}
.pf-loc,.pf-due{font-size:11px;color:var(--slate);}
.pf-notes{font-size:12px;color:var(--slate);margin-top:5px;font-style:italic;}
.pf-done-date{font-size:10px;color:var(--green);margin-top:4px;}
.pri-badge{font-size:9px;font-weight:700;padding:2px 6px;border-radius:20px;font-family:'Barlow Condensed',sans-serif;text-transform:uppercase;border:1px solid;}
.pri-lo{color:var(--green);border-color:var(--green);}
.pri-me{color:var(--gold);border-color:var(--gold);}
.pri-hi{color:var(--red);border-color:var(--red);}
.pf-empty{text-align:center;color:var(--slate);font-size:13px;padding:24px;line-height:1.7;}

/* STATUS */
.stat-row{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:12px;}
.chip{padding:3px 10px;border-radius:20px;font-size:10px;font-weight:700;border:1px solid;font-family:'Barlow Condensed',sans-serif;letter-spacing:0.5px;}
.chip-o{color:var(--gold);border-color:var(--gold-border);background:var(--gold-glow);}
.chip-d{color:var(--green);border-color:rgba(46,204,113,0.3);background:rgba(46,204,113,0.08);}

/* SIGNATURES */
.sig-wrap{margin-bottom:14px;}
.sig-lbl{font-size:10px;font-weight:600;letter-spacing:1.5px;text-transform:uppercase;color:var(--slate);margin-bottom:5px;}
.sig-name-row{display:flex;gap:8px;margin-bottom:7px;}
.sig-name-row input{flex:1;}
canvas.sig-cv{width:100%;height:140px;background:rgba(17,24,32,0.9);border:1px solid var(--border);border-radius:var(--r);cursor:crosshair;display:block;touch-action:none;}
canvas.sig-cv.inking{border-color:var(--gold);}
.sig-acts{display:flex;justify-content:flex-end;margin-top:4px;}
.sig-hint{font-size:10px;color:var(--slate);margin-top:3px;}
.divider{display:flex;align-items:center;gap:8px;margin:14px 0 10px;}
.divider span{font-family:'Barlow Condensed',sans-serif;font-size:10px;font-weight:700;letter-spacing:2px;text-transform:uppercase;color:var(--slate);white-space:nowrap;}
.divider::before,.divider::after{content:'';flex:1;height:1px;background:var(--border);}

/* TASKS */
.task-filters{display:flex;gap:8px;margin-bottom:10px;flex-wrap:wrap;}
.task-filters select{flex:1;min-width:110px;}
.task-add-form{background:var(--input-bg);border:1px solid var(--gold-border);border-radius:var(--r);padding:12px;margin-bottom:12px;}
.task-add-form label{color:var(--gold);}
.task-item{display:flex;align-items:flex-start;gap:8px;padding:10px;background:var(--input-bg);border:1px solid var(--border);border-radius:var(--r);margin-bottom:6px;}
.t-chk{width:20px;height:20px;flex-shrink:0;appearance:none;-webkit-appearance:none;background:var(--input-bg);border:2px solid var(--border);border-radius:3px;cursor:pointer;position:relative;transition:all 0.15s;margin-top:2px;}
.t-chk:checked{background:var(--blue);border-color:var(--blue);}
.t-chk:checked::after{content:'✓';position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);color:#fff;font-size:10px;font-weight:700;}
.t-body{flex:1;}
.t-txt{font-size:13px;font-weight:600;}
.t-txt.done{text-decoration:line-through;color:var(--slate);}
.t-meta{display:flex;gap:5px;flex-wrap:wrap;margin-top:4px;align-items:center;}
.t-tag{font-size:9px;font-weight:700;padding:2px 6px;border-radius:20px;font-family:'Barlow Condensed',sans-serif;text-transform:uppercase;}
.t-job-tag{background:var(--gold-glow);border:1px solid var(--gold-border);color:var(--gold);}
.t-code-tag{background:rgba(59,130,246,0.1);border:1px solid rgba(59,130,246,0.3);color:#93c5fd;}
.t-user{font-size:10px;color:var(--slate);}
.t-due{font-size:10px;color:var(--slate);}
.t-rm{background:none;border:none;cursor:pointer;color:var(--red);font-size:14px;padding:2px;flex-shrink:0;}

/* BUTTONS */
.btn{padding:9px 16px;border:none;border-radius:var(--r);font-family:'Barlow Condensed',sans-serif;font-size:13px;font-weight:700;letter-spacing:1px;text-transform:uppercase;cursor:pointer;transition:all 0.2s;}
.btn-gold{background:var(--gold);color:var(--ink);}
.btn-gold:hover{background:var(--gold-dark);}
.btn-ghost{background:none;color:var(--slate);border:1px solid var(--border);}
.btn-ghost:hover{border-color:var(--slate);color:var(--white);}
.btn-green{background:var(--green);color:var(--ink);}
.btn-blue{background:var(--blue);color:#fff;}
.btn-full{width:100%;padding:13px;font-size:15px;letter-spacing:2px;margin-top:6px;display:flex;align-items:center;justify-content:center;gap:8px;}
.btn-sm{padding:5px 10px;font-size:11px;}

/* WEATHER */
.wx-row{display:flex;gap:5px;flex-wrap:wrap;}
.wx-btn{padding:5px 10px;border-radius:20px;border:1px solid var(--border);background:none;color:var(--slate);cursor:pointer;font-size:12px;transition:all 0.15s;}
.wx-btn.active{background:var(--gold-glow);border-color:var(--gold);color:var(--gold);}

/* ADMIN */
.admin-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,0.88);z-index:200;overflow-y:auto;}
.admin-overlay.open{display:block;}
.admin-panel{background:var(--ink-mid);max-width:640px;margin:0 auto;min-height:100%;padding:20px 16px 60px;}
.admin-hd{display:flex;align-items:center;justify-content:space-between;margin-bottom:20px;padding-bottom:14px;border-bottom:2px solid var(--gold);}
.admin-hd h2{font-family:'Barlow Condensed',sans-serif;font-size:22px;font-weight:900;color:var(--gold);letter-spacing:1px;}
.a-sec{margin-bottom:24px;}
.a-sec h3{font-family:'Barlow Condensed',sans-serif;font-size:13px;font-weight:700;letter-spacing:2px;text-transform:uppercase;color:var(--slate);margin-bottom:10px;padding-bottom:6px;border-bottom:1px solid var(--border);}
.a-item{display:flex;align-items:center;gap:8px;padding:9px 10px;background:var(--input-bg);border:1px solid var(--border);border-radius:var(--r);margin-bottom:6px;}
.a-item-info{flex:1;}
.a-item-name{font-size:13px;font-weight:600;}
.a-item-sub{font-size:10px;color:var(--slate);margin-top:2px;}
.a-status{font-size:9px;font-weight:700;letter-spacing:1px;padding:2px 7px;border-radius:20px;font-family:'Barlow Condensed',sans-serif;text-transform:uppercase;}
.s-active{background:rgba(46,204,113,0.15);border:1px solid rgba(46,204,113,0.4);color:var(--green);}
.s-inactive{background:rgba(143,165,192,0.1);border:1px solid var(--border);color:var(--slate);}
.jbtn{background:none;border:1px solid var(--border);color:var(--slate);padding:4px 8px;border-radius:4px;font-size:10px;cursor:pointer;font-family:'Barlow Condensed',sans-serif;font-weight:700;text-transform:uppercase;letter-spacing:1px;}
.jbtn:hover{border-color:var(--gold);color:var(--gold);}
.a-form{background:var(--input-bg);border:1px solid var(--gold-border);border-radius:var(--r);padding:14px;margin-top:10px;}
.a-form h4{font-family:'Barlow Condensed',sans-serif;font-size:13px;font-weight:700;color:var(--gold);letter-spacing:1px;text-transform:uppercase;margin-bottom:10px;}
.chips{display:flex;flex-wrap:wrap;gap:6px;margin-top:6px;margin-bottom:8px;}
.bc-chip{display:flex;align-items:center;gap:4px;padding:3px 8px;background:var(--gold-glow);border:1px solid var(--gold-border);border-radius:20px;font-size:11px;color:var(--gold);}
.bc-chip button{background:none;border:none;cursor:pointer;color:var(--gold);font-size:13px;padding:0;line-height:1;}
.bc-add-row{display:flex;gap:6px;}
.bc-add-row input{flex:1;}
.pri-btns{display:flex;gap:4px;margin-top:6px;}
.pri-btn{font-size:9px;font-weight:700;padding:3px 9px;border-radius:20px;border:1px solid;cursor:pointer;background:none;font-family:'Barlow Condensed',sans-serif;text-transform:uppercase;transition:all 0.15s;}
.pri-btn.lo{color:var(--green);border-color:var(--green);}
.pri-btn.me{color:var(--gold);border-color:var(--gold);}
.pri-btn.hi{color:var(--red);border-color:var(--red);}
.pri-btn.active.lo{background:var(--green);color:var(--ink);}
.pri-btn.active.me{background:var(--gold);color:var(--ink);}
.pri-btn.active.hi{background:var(--red);color:#fff;}
.pw-gate{display:flex;align-items:center;justify-content:center;min-height:220px;flex-direction:column;gap:12px;padding:20px;}
.pw-gate h3{font-family:'Barlow Condensed',sans-serif;font-size:18px;font-weight:800;color:var(--gold);}
.pw-gate p{font-size:12px;color:var(--slate);text-align:center;}
.pw-gate input{max-width:260px;}
.pw-err{color:var(--red);font-size:12px;}

/* MODALS */
.modal-ov{display:none;position:fixed;inset:0;background:rgba(0,0,0,0.8);z-index:300;align-items:center;justify-content:center;padding:16px;}
.modal-ov.open{display:flex;}
.modal-box{background:var(--ink-mid);border:1px solid var(--border);border-radius:12px;padding:22px;max-width:380px;width:100%;animation:su 0.2s ease;}
@keyframes su{from{transform:translateY(16px);opacity:0;}to{transform:translateY(0);opacity:1;}}
.modal-box h2{font-family:'Barlow Condensed',sans-serif;font-size:20px;font-weight:800;color:var(--gold);margin-bottom:6px;}
.modal-box p{font-size:13px;color:var(--slate);margin-bottom:16px;line-height:1.5;}
.modal-acts{display:flex;gap:8px;flex-wrap:wrap;}

@media(max-width:420px){.frow{grid-template-columns:1fr;}.photo-grid{grid-template-columns:1fr;}.brand-text h1{font-size:15px;}.task-filters{flex-direction:column;}}
@media print{.app-header,.btn,.drop-zone,.rm-btn,.add-row-btn,.admin-btn,.t-rm{display:none!important;}.tab-page{display:block!important;}.card{border:1px solid #ccc;break-inside:avoid;}body{background:white;color:black;}}
</style>
</head>
<body>

<div class="app-header">
  <div class="header-row">
    <div class="brand">
      <div class="brand-badge">BCPS</div>
      <div class="brand-text">
        <h1>Barton Creek Property Solutions</h1>
        <p>Field Daily Log System</p>
      </div>
    </div>
    <button class="admin-btn" onclick="openAdmin()">⚙ Admin</button>
  </div>
  <div class="tab-bar">
    <button class="tab-btn active" onclick="switchTab('daily',this)">📋 Daily</button>
    <button class="tab-btn" onclick="switchTab('punch',this)">✅ Punch</button>
    <button class="tab-btn" onclick="switchTab('tasks',this)">📌 Tasks</button>
  </div>
</div>

<!-- ════════════════ DAILY ════════════════ -->
<div id="tab-daily" class="tab-page active">

  <div class="card">
    <div class="card-hd"><div class="card-ico">🏗️</div><span class="card-ttl">Project Info</span></div>
    <div class="frow">
      <div class="ff"><label>Date</label><input type="date" id="d_date"></div>
      <div class="ff"><label>Weather</label>
        <div class="wx-row">
          <button class="wx-btn" onclick="this.classList.toggle('active')">☀️ Clear</button>
          <button class="wx-btn" onclick="this.classList.toggle('active')">⛅ Cloud</button>
          <button class="wx-btn" onclick="this.classList.toggle('active')">🌧️ Rain</button>
          <button class="wx-btn" onclick="this.classList.toggle('active')">🌩️ Storm</button>
          <button class="wx-btn" onclick="this.classList.toggle('active')">❄️ Cold</button>
        </div>
      </div>
    </div>
    <div class="ff"><label>Project Name</label>
      <select id="d_job" onchange="onDailyJobChange()"><option value="">— Select Project —</option></select></div>
    <div class="ff"><label>PM / Super</label>
      <input type="text" id="d_super" placeholder="Name of PM or Superintendent on site"></div>
    <div class="ff" id="d_tags_section" style="display:none;">
      <label>Job Tags — Select All That Apply</label>
      <div class="tag-box" id="d_tags"><span class="tag-placeholder">Select a project first</span></div>
    </div>
  </div>

  <div class="card">
    <div class="card-hd"><div class="card-ico">👷</div><span class="card-ttl">Manpower On Site</span></div>
    <div class="mp-wrap">
      <table class="mp-table">
        <thead><tr>
          <th>Billable Job Tag</th><th>Subcontractor Name</th><th style="width:90px">Hrs on Site</th><th style="width:28px"></th>
        </tr></thead>
        <tbody id="mpBody"></tbody>
        <tfoot><tr class="tot-row"><td colspan="2">TOTAL HOURS</td><td id="mpTotal">0.0</td><td></td></tr></tfoot>
      </table>
    </div>
    <button class="add-row-btn" onclick="addMpRow()">+ Add Row</button>
  </div>

  <div class="card">
    <div class="card-hd"><div class="card-ico">🔨</div><span class="card-ttl">Work Performed</span></div>
    <div id="workBody"></div>
    <button class="add-row-btn" onclick="addWorkRow()">+ Add Tag / Work Entry</button>
  </div>

  <div class="card">
    <div class="card-hd"><div class="card-ico">📦</div><span class="card-ttl">Materials</span></div>
    <div class="ff"><label>Materials Delivered Today</label>
      <textarea id="d_matdel" rows="3" placeholder="Materials received on site today — supplier, item, quantity..."></textarea></div>
    <div class="ff"><label>Materials Needed / Ordered</label>
      <textarea id="d_matneed" rows="3" placeholder="Materials needed — vendor, item, qty, urgency level..."></textarea></div>
  </div>

  <div class="card">
    <div class="card-hd"><div class="card-ico">📸</div><span class="card-ttl">Photos – Site &amp; Receipts</span></div>
    <div class="drop-zone" onclick="document.getElementById('photoInput').click()"
      ondragover="ev=>{ev.preventDefault();ev.currentTarget.classList.add('on')}"
      ondragleave="ev=>ev.currentTarget.classList.remove('on')"
      ondrop="handleDrop(event)">
      <div class="di">📷</div>
      <p><strong>Tap to add photos</strong> or drag &amp; drop</p>
    </div>
    <input type="file" id="photoInput" accept="image/*" multiple capture="environment" onchange="handlePhotos(event)">
    <div class="photo-grid" id="photoGrid"></div>
  </div>

  <div class="card">
    <div class="card-hd"><div class="card-ico">⚠️</div><span class="card-ttl">Incidents &amp; Notes</span></div>
    <div class="ff"><label>Incidents / Observations</label>
      <textarea id="d_incidents" rows="3" placeholder="Safety incidents, near-misses, hazards, observations..."></textarea></div>
    <div class="ff"><label>Delays / Problems</label>
      <textarea id="d_delays" rows="3" placeholder="Describe delay, root cause, time lost (e.g. 2.5 hrs), impact on schedule..."></textarea></div>
  </div>

  <button class="btn btn-gold btn-full" onclick="submitDaily()">📤 Submit Daily Report</button>
</div>

<!-- ════════════════ PUNCH ════════════════ -->
<div id="tab-punch" class="tab-page">
  <div class="card">
    <div class="card-hd"><div class="card-ico">📋</div><span class="card-ttl">Punch List</span></div>
    <div class="frow">
      <div class="ff"><label>Project</label>
        <select id="p_job" onchange="renderPunchField()"><option value="">— Select Project —</option></select></div>
      <div class="ff"><label>Filter by Tag</label>
        <select id="p_tagFilter" onchange="renderPunchField()"><option value="all">All Tags</option></select></div>
    </div>
  </div>

  <div class="stat-row">
    <span class="chip chip-o" id="pOpen">0 Open</span>
    <span class="chip chip-d" id="pDone">0 Complete</span>
  </div>

  <div id="punchFieldList"></div>

  <div class="card" id="punchSignCard" style="display:none;">
    <div class="card-hd"><div class="card-ico">✍️</div><span class="card-ttl">Sign Off</span></div>
    <div class="frow">
      <div class="ff"><label>Project</label><input type="text" id="ps_proj" readonly style="color:var(--slate);"></div>
      <div class="ff"><label>Date</label><input type="date" id="ps_date"></div>
    </div>
    <div class="sig-wrap">
      <div class="sig-lbl">Superintendent Sign-Off</div>
      <div class="sig-name-row"><input type="text" id="ss_name" placeholder="Print name"><input type="date" id="ss_date" style="width:140px"></div>
      <canvas class="sig-cv" id="sigS" width="600" height="140"></canvas>
      <div class="sig-hint">Sign with finger or stylus</div>
      <div class="sig-acts"><button class="btn btn-ghost btn-sm" onclick="clrSig('sigS')">Clear</button></div>
    </div>
    <div class="divider"><span>Project Manager</span></div>
    <div class="sig-wrap">
      <div class="sig-lbl">Project Manager Sign-Off</div>
      <div class="sig-name-row"><input type="text" id="sp_name" placeholder="Print name"><input type="date" id="sp_date" style="width:140px"></div>
      <canvas class="sig-cv" id="sigP" width="600" height="140"></canvas>
      <div class="sig-hint">Sign with finger or stylus</div>
      <div class="sig-acts"><button class="btn btn-ghost btn-sm" onclick="clrSig('sigP')">Clear</button></div>
    </div>
    <button class="btn btn-green btn-full" onclick="submitPunch()">📤 Submit &amp; Sign Punch List</button>
  </div>
</div>

<!-- ════════════════ TASKS ════════════════ -->
<div id="tab-tasks" class="tab-page">
  <div class="card">
    <div class="card-hd"><div class="card-ico">📌</div><span class="card-ttl">Task List</span><span class="card-badge" id="taskBadge">0 open</span></div>

    <div class="task-filters">
      <select id="t_jobFilter" onchange="onTaskJobFilterChange()"><option value="all">All Projects</option></select>
      <select id="t_tagFilter" onchange="renderTasks()"><option value="all">All Tags</option></select>
      <select id="t_userFilter" onchange="renderTasks()"><option value="all">All Users</option></select>
    </div>

    <div class="task-add-form">
      <div class="ff"><label>Task Description</label>
        <input type="text" id="t_text" placeholder="What needs to be done..." onkeydown="if(event.key==='Enter')addTask()"></div>
      <div class="frow">
        <div class="ff"><label>Project</label>
          <select id="t_jobSel" onchange="onNewTaskJobChange()"><option value="">— Select Project —</option></select></div>
        <div class="ff"><label>Job Tag</label>
          <select id="t_tagSel"><option value="">— Select Tag —</option></select></div>
      </div>
      <div class="frow">
        <div class="ff"><label>Assign To</label>
          <select id="t_userSel"><option value="">— Assign User —</option></select></div>
        <div class="ff"><label>Due Date</label><input type="date" id="t_due"></div>
      </div>
      <button class="btn btn-gold" style="width:100%;" onclick="addTask()">+ Add Task</button>
    </div>

    <div id="taskList"></div>
  </div>
</div>

<!-- ════════════════ ADMIN ════════════════ -->
<div class="admin-overlay" id="adminOverlay">
  <div class="admin-panel">
    <div class="admin-hd"><h2>⚙ Admin Panel</h2><button class="btn btn-ghost btn-sm" onclick="closeAdmin()">✕ Close</button></div>

    <div id="adminGate" class="pw-gate">
      <h3>🔐 Admin Access</h3>
      <p>Enter your admin password to manage projects, punch lists, users and settings.</p>
      <input type="password" id="adminPW" placeholder="Password" onkeydown="if(event.key==='Enter')checkPW()">
      <button class="btn btn-gold" onclick="checkPW()">Unlock</button>
      <span class="pw-err" id="pwErr"></span>
    </div>

    <div id="adminContent" style="display:none;">

      <!-- PROJECTS -->
      <div class="a-sec">
        <h3>Projects</h3>
        <div id="jobsList"></div>
        <div class="a-form">
          <h4 id="jobFormTitle">+ New Project</h4>
          <div class="frow">
            <div class="ff"><label>Project Name</label><input type="text" id="aj_name" placeholder="e.g. High Winds Hotel"></div>
            <div class="ff"><label>Job Number</label><input type="text" id="aj_num" placeholder="e.g. 2025-014"></div>
          </div>
          <div class="ff"><label>Client / Owner</label><input type="text" id="aj_client" placeholder="Owner name"></div>
          <div class="ff">
            <label>Job Tags</label>
            <div class="chips" id="bcList"></div>
            <div class="bc-add-row">
              <input type="text" id="bc_new" placeholder="e.g. Warehouse, Hotel, Oelke T&M" onkeydown="if(event.key==='Enter')addTag()">
              <button class="btn btn-ghost btn-sm" onclick="addTag()">+ Add</button>
            </div>
          </div>
          <div class="ff"><label>Status</label>
            <select id="aj_status"><option value="active">Active</option><option value="inactive">Inactive</option></select></div>
          <div style="display:flex;gap:8px;margin-top:10px;">
            <button class="btn btn-gold" onclick="saveJob()">Save Project</button>
            <button class="btn btn-ghost" onclick="resetJobForm()">Reset</button>
          </div>
        </div>
      </div>

      <!-- USERS -->
      <div class="a-sec">
        <h3>Users</h3>
        <div id="userList"></div>
        <div class="a-form">
          <h4>+ Add User</h4>
          <div class="frow">
            <div class="ff"><label>Full Name</label><input type="text" id="au_name" placeholder="e.g. John Smith"></div>
            <div class="ff"><label>Role</label>
              <select id="au_role">
                <option value="Super">Superintendent</option>
                <option value="PM">Project Manager</option>
                <option value="Foreman">Foreman</option>
                <option value="Sub">Subcontractor</option>
              </select>
            </div>
          </div>
          <button class="btn btn-gold" onclick="saveUser()">Add User</button>
        </div>
      </div>

      <!-- PUNCH BUILDER -->
      <div class="a-sec">
        <h3>Punch List Builder</h3>
        <div class="ff"><label>Project</label>
          <select id="ap_job" onchange="onAdminPunchJobChange()"><option value="">— Select Project —</option></select></div>
        <div id="adminPunchItems"></div>
        <div class="a-form" id="punchAddForm" style="display:none;">
          <h4 id="punchFormTitle">+ New Punch Item</h4>
          <div class="ff"><label>Description</label><input type="text" id="ap_desc" placeholder="What needs to be done..."></div>
          <div class="frow">
            <div class="ff"><label>Job Tag</label><select id="ap_tag"><option value="">— Tag —</option></select></div>
            <div class="ff"><label>Location on Site</label><input type="text" id="ap_loc" placeholder="e.g. 2nd Floor East"></div>
          </div>
          <div class="frow">
            <div class="ff"><label>Due Date</label><input type="date" id="ap_due"></div>
            <div class="ff"><label>Priority</label>
              <div class="pri-btns" id="ap_pri_btns">
                <button class="pri-btn lo" onclick="setPunchPri(this,'lo')">Low</button>
                <button class="pri-btn me active" onclick="setPunchPri(this,'me')">Med</button>
                <button class="pri-btn hi" onclick="setPunchPri(this,'hi')">High</button>
              </div>
            </div>
          </div>
          <div class="ff"><label>Notes</label><textarea id="ap_notes" rows="2" placeholder="Specs, reference drawings, additional instructions..."></textarea></div>
          <div style="display:flex;gap:8px;margin-top:8px;">
            <button class="btn btn-gold" onclick="savePunchItem()">Save Item</button>
            <button class="btn btn-ghost" onclick="resetPunchForm()">Reset</button>
          </div>
        </div>
      </div>

      <!-- DROPBOX -->
      <div class="a-sec">
        <h3>Dropbox Backup</h3>
        <p style="font-size:12px;color:var(--slate);margin-bottom:10px;line-height:1.5;">Auto-save submitted reports to <strong>BCPS Field Logs/[Project]/</strong> in your Dropbox.</p>
        <div id="adminDropboxStatus" style="font-size:12px;margin-bottom:10px;"></div>
        <div style="display:flex;gap:8px;flex-wrap:wrap;margin-bottom:12px;">
          <button class="btn btn-blue" id="dropboxConnectBtn" onclick="connectDropbox()">🔗 Connect Dropbox</button>
          <button class="btn btn-ghost" id="dropboxDisconnectBtn" style="display:none;" onclick="disconnectDropbox()">Disconnect</button>
        </div>
        <div class="ff"><label>Dropbox App Key</label>
          <input type="text" id="dropboxAppKey" placeholder="From dropbox.com/developers">
          <p style="font-size:10px;color:var(--slate);margin-top:4px;">dropbox.com/developers → Create App → Scoped → Full Dropbox → copy App Key</p>
        </div>
        <button class="btn btn-gold" onclick="saveDropboxKey()">Save App Key</button>
      </div>

      <!-- SECURITY -->
      <div class="a-sec">
        <h3>Security</h3>
        <div class="ff"><label>Change Admin Password</label><input type="password" id="newPW" placeholder="New password"></div>
        <button class="btn btn-gold" onclick="changePW()">Update Password</button>
      </div>

      <!-- DATA -->
      <div class="a-sec">
        <h3>Data</h3>
        <div style="display:flex;gap:8px;flex-wrap:wrap;">
          <button class="btn btn-ghost" onclick="exportData()">💾 Export JSON</button>
          <button class="btn btn-ghost" onclick="importData()">📂 Import</button>
          <input type="file" id="importFile" accept=".json" style="display:none" onchange="doImport(event)">
        </div>
      </div>

    </div>
  </div>
</div>

<!-- CONFIRM MODAL -->
<div class="modal-ov" id="confirmModal">
  <div class="modal-box">
    <h2 id="cm_title">Submitted</h2>
    <p id="cm_msg"></p>
    <div class="modal-acts">
      <button class="btn btn-gold" onclick="window.print()">🖨️ Print / PDF</button>
      <button class="btn btn-ghost" onclick="closeModal('confirmModal')">Done</button>
    </div>
  </div>
</div>

<!-- DROPBOX MODAL -->
<div class="modal-ov" id="dropboxModal">
  <div class="modal-box">
    <h2>📦 Connect Dropbox</h2>
    <p>Before clicking Authorize, make sure this exact URI is added in your Dropbox app settings:</p>
    <div style="background:var(--ink);border:1px solid var(--gold-border);border-radius:6px;padding:10px;margin-bottom:12px;font-size:11px;color:var(--gold);word-break:break-all;font-family:monospace;" id="dropboxRedirectUri"></div>
    <p style="font-size:11px;margin-bottom:16px;">Dropbox Console → your app → <strong>Settings</strong> → <strong>OAuth 2</strong> → <strong>Redirect URIs</strong> → Add → Save</p>
    <div class="modal-acts">
      <button class="btn btn-blue" onclick="launchDropboxOAuth()">🔗 Authorize Dropbox</button>
      <button class="btn btn-ghost" onclick="closeModal('dropboxModal')">Cancel</button>
    </div>
  </div>
</div>

<script>
// ═══════════════════════════════════════════
//  STATE
// ═══════════════════════════════════════════
const DEFAULT_PW = 'bcps2025';
let state = loadState();

function defaultState() {
  return {
    pw: DEFAULT_PW,
    jobs: [
      { id:uid(), name:'High Winds Hotel', num:'2025-001', client:'High Winds LLC', status:'active', codes:['Warehouse','Oelke T&M','Rework T&M','Hotel'] },
      { id:uid(), name:'Oelke Site Work', num:'2025-003', client:'Oelke Construction', status:'active', codes:['Site Work','Utilities','T&M'] },
      { id:uid(), name:'BCPS General', num:'2025-000', client:'Internal', status:'active', codes:['General','Admin'] },
    ],
    users: [
      { id:uid(), name:'Brandy Barton', role:'PM' },
      { id:uid(), name:'Field Super 1', role:'Super' },
    ],
    punchItems: [],
    tasks: [],
    dropboxConnected: false, dropboxToken: '', dropboxAppKey: ''
  };
}

function loadState() {
  try { const s = localStorage.getItem('bcps_v3'); if(s) return JSON.parse(s); } catch(e){}
  return defaultState();
}
function saveState() { localStorage.setItem('bcps_v3', JSON.stringify(state)); }
function uid() { return Math.random().toString(36).substr(2,9); }
function esc(s) { return String(s||'').replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;'); }

// ═══════════════════════════════════════════
//  INIT
// ═══════════════════════════════════════════
document.addEventListener('DOMContentLoaded', () => {
  const d = new Date().toISOString().slice(0,10);
  ['d_date','ps_date','ss_date','sp_date'].forEach(id => { const el=document.getElementById(id); if(el) el.value=d; });
  refreshAllDropdowns();
  addMpRow();
  addWorkRow();
  initSig('sigS'); initSig('sigP');
  renderTasks();
  renderPunchField();
  checkDropboxCallback();
});

// ═══════════════════════════════════════════
//  TABS
// ═══════════════════════════════════════════
function switchTab(tab, btn) {
  document.querySelectorAll('.tab-page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
  document.getElementById('tab-'+tab).classList.add('active');
  btn.classList.add('active');
  window.scrollTo(0,0);
  if(tab==='punch') renderPunchField();
  if(tab==='tasks') renderTasks();
}

// ═══════════════════════════════════════════
//  DROPDOWNS
// ═══════════════════════════════════════════
function refreshAllDropdowns() {
  const active = state.jobs.filter(j=>j.status==='active');
  const jobSelects = ['d_job','p_job','t_jobFilter','t_jobSel','ap_job'];
  jobSelects.forEach(id => {
    const sel = document.getElementById(id); if(!sel) return;
    const isFilter = (id==='t_jobFilter');
    const prev = sel.value;
    sel.innerHTML = isFilter ? '<option value="all">All Projects</option>' : '<option value="">— Select Project —</option>';
    active.forEach(j => { const o=document.createElement('option'); o.value=j.id; o.textContent=j.name+(j.num?' ('+j.num+')':''); sel.appendChild(o); });
    if(prev) sel.value = prev;
  });

  const userSelects = ['t_userSel','t_userFilter'];
  userSelects.forEach(id => {
    const sel = document.getElementById(id); if(!sel) return;
    const isFilter = (id==='t_userFilter');
    const prev = sel.value;
    sel.innerHTML = isFilter ? '<option value="all">All Users</option>' : '<option value="">— Assign User —</option>';
    state.users.forEach(u => { const o=document.createElement('option'); o.value=u.id; o.textContent=u.name+' ('+u.role+')'; sel.appendChild(o); });
    if(prev) sel.value = prev;
  });
}

function getJob(id) { return state.jobs.find(j=>j.id===id); }

function populateTagSelect(selEl, job) {
  const prev = selEl.value;
  selEl.innerHTML = '<option value="">— Tag —</option>';
  if(job) job.codes.forEach(c => { const o=document.createElement('option'); o.value=c; o.textContent=c; selEl.appendChild(o); });
  selEl.value = prev;
}

// ═══════════════════════════════════════════
//  DAILY — JOB TAG MULTISELECT
// ═══════════════════════════════════════════
function onDailyJobChange() {
  const job = getJob(document.getElementById('d_job').value);
  const section = document.getElementById('d_tags_section');
  const tagBox = document.getElementById('d_tags');

  if(!job) { section.style.display='none'; tagBox.innerHTML='<span class="tag-placeholder">Select a project first</span>'; refreshTagSelects(null); return; }
  section.style.display='';
  tagBox.innerHTML = job.codes.map(c => `<span class="tag-pill off" onclick="this.classList.toggle('off');this.classList.toggle('on')" data-tag="${esc(c)}">${esc(c)}</span>`).join('');
  refreshTagSelects(job);
}

function refreshTagSelects(job) {
  document.querySelectorAll('.bc-sel').forEach(sel => populateTagSelect(sel, job));
  document.querySelectorAll('.wk-tag-sel').forEach(sel => populateTagSelect(sel, job));
}

function getSelectedDailyTags() {
  return [...document.querySelectorAll('#d_tags .tag-pill.on')].map(p=>p.dataset.tag);
}

// ═══════════════════════════════════════════
//  MANPOWER
// ═══════════════════════════════════════════
function addMpRow() {
  const tbody = document.getElementById('mpBody');
  const job = getJob(document.getElementById('d_job').value);
  const opts = job ? job.codes.map(c=>`<option value="${esc(c)}">${esc(c)}</option>`).join('') : '';
  const tr = document.createElement('tr');
  tr.innerHTML = `
    <td><select class="bc-sel" oninput="calcMpTotal()"><option value="">— Tag —</option>${opts}</select></td>
    <td><input type="text" placeholder="Subcontractor name"></td>
    <td><input type="number" min="0" step="0.5" placeholder="0" oninput="calcMpTotal()"></td>
    <td><button class="rm-btn" onclick="this.closest('tr').remove();calcMpTotal()">✕</button></td>`;
  tbody.appendChild(tr);
}

function calcMpTotal() {
  let t=0;
  document.querySelectorAll('#mpBody tr').forEach(tr => { t+=parseFloat(tr.querySelectorAll('input[type=number]')[0]?.value)||0; });
  document.getElementById('mpTotal').textContent = t.toFixed(1);
}

// ═══════════════════════════════════════════
//  WORK PERFORMED
// ═══════════════════════════════════════════
let wkId=0;
function addWorkRow() {
  wkId++;
  const id='wk_'+wkId;
  const job = getJob(document.getElementById('d_job').value);
  const opts = job ? job.codes.map(c=>`<option value="${esc(c)}">${esc(c)}</option>`).join('') : '';
  const div = document.createElement('div');
  div.id=id; div.className='work-row';
  div.innerHTML=`
    <div class="work-row-top">
      <select class="wk-tag-sel" style="background:var(--input-bg);border:1px solid var(--border);border-radius:var(--r);color:var(--white);font-family:'Barlow',sans-serif;font-size:13px;padding:8px;">
        <option value="">— Job Tag —</option>${opts}
      </select>
      <button class="rm-btn" onclick="document.getElementById('${id}').remove()">✕</button>
    </div>
    <textarea placeholder="Describe work performed under this tag..." rows="3"
      style="width:100%;background:var(--input-bg);border:1px solid var(--border);border-radius:var(--r);color:var(--white);font-family:'Barlow',sans-serif;font-size:13px;padding:8px;resize:vertical;outline:none;"></textarea>`;
  document.getElementById('workBody').appendChild(div);
}

// ═══════════════════════════════════════════
//  PHOTOS
// ═══════════════════════════════════════════
function handleDrop(e) { e.preventDefault(); e.currentTarget.classList.remove('on'); processFiles(e.dataTransfer.files); }
function handlePhotos(e) { processFiles(e.target.files); e.target.value=''; }
function processFiles(files) {
  Array.from(files).forEach(f => { if(!f.type.startsWith('image/')) return;
    const r=new FileReader(); r.onload=ev=>addPhotoCard(ev.target.result); r.readAsDataURL(f); });
}
function addPhotoCard(src) {
  const d=document.createElement('div'); d.className='photo-card';
  d.innerHTML=`<img src="${src}" alt="">
    <div class="pc-cap"><input type="text" placeholder="Description / receipt note..."></div>
    <div class="pc-rm"><button class="rm-btn" onclick="this.closest('.photo-card').remove()">✕ Remove</button></div>`;
  document.getElementById('photoGrid').appendChild(d);
}

// ═══════════════════════════════════════════
//  PUNCH FIELD VIEW
// ═══════════════════════════════════════════
function renderPunchField() {
  const jobId = document.getElementById('p_job').value;
  const job = getJob(jobId);
  const tagFilter = document.getElementById('p_tagFilter').value;
  const listEl = document.getElementById('punchFieldList');
  const signCard = document.getElementById('punchSignCard');

  // sync tag filter dropdown
  const pTF = document.getElementById('p_tagFilter');
  const prevTF = pTF.value;
  pTF.innerHTML = '<option value="all">All Tags</option>';
  if(job) job.codes.forEach(c=>{ const o=document.createElement('option'); o.value=c; o.textContent=c; pTF.appendChild(o); });
  pTF.value = prevTF||'all';

  if(!jobId) {
    listEl.innerHTML=`<div class="card"><p class="pf-empty">Select a project to view punch items.</p></div>`;
    signCard.style.display='none'; return;
  }

  if(job) document.getElementById('ps_proj').value = job.name;

  let items = state.punchItems.filter(p=>p.jobId===jobId);
  if(tagFilter && tagFilter!=='all') items = items.filter(p=>p.tag===tagFilter);

  const openCount = items.filter(p=>!p.done).length;
  const doneCount = items.filter(p=>p.done).length;
  document.getElementById('pOpen').textContent = openCount+' Open';
  document.getElementById('pDone').textContent = doneCount+' Complete';

  if(!items.length) {
    listEl.innerHTML=`<div class="card"><p class="pf-empty">No punch items for this project yet.<br><span style="font-size:11px;">Admin creates items in the Admin panel → Punch List Builder.</span></p></div>`;
    signCard.style.display='none'; return;
  }

  // open items first, completed below
  const sorted = [...items.filter(p=>!p.done), ...items.filter(p=>p.done)];

  listEl.innerHTML = sorted.map(p => {
    const priLabel = p.priority==='lo'?'Low':p.priority==='hi'?'High':'Med';
    const priClass = 'pri-'+(p.priority||'me');
    return `
    <div class="card pf-item" id="pfi_${p.id}" style="border-left:4px solid ${p.done?'var(--green)':p.priority==='hi'?'var(--red)':p.priority==='lo'?'var(--green)':'var(--gold)'};">
      <div style="display:flex;align-items:flex-start;gap:12px;">
        <button onclick="togglePunchDone('${p.id}')"
          style="flex-shrink:0;width:32px;height:32px;border-radius:50%;border:2px solid ${p.done?'var(--green)':'var(--border)'};
          background:${p.done?'var(--green)':'transparent'};cursor:pointer;font-size:16px;
          display:flex;align-items:center;justify-content:center;transition:all 0.2s;margin-top:2px;"
          title="${p.done?'Mark Incomplete':'Mark Complete'}">
          ${p.done?'✓':''}
        </button>
        <div style="flex:1;">
          <div style="font-size:14px;font-weight:600;${p.done?'text-decoration:line-through;color:var(--slate);':''}">${esc(p.desc)}</div>
          <div style="display:flex;gap:7px;flex-wrap:wrap;align-items:center;margin-top:5px;">
            ${p.tag?`<span class="pf-tag">${esc(p.tag)}</span>`:''}
            ${p.loc?`<span class="pf-loc">📍 ${esc(p.loc)}</span>`:''}
            ${p.due?`<span class="pf-due">📅 Due: ${p.due}</span>`:''}
            <span class="pri-badge ${priClass}">${priLabel}</span>
          </div>
          ${p.notes?`<div class="pf-notes" style="margin-top:6px;">${esc(p.notes)}</div>`:''}
          ${p.done&&p.doneDate?`<div style="font-size:10px;color:var(--green);margin-top:4px;font-weight:600;">✓ Marked complete ${p.doneDate}</div>`:''}
        </div>
        <div style="font-size:11px;color:${p.done?'var(--green)':'var(--slate)'};font-weight:700;font-family:'Barlow Condensed',sans-serif;letter-spacing:1px;text-transform:uppercase;flex-shrink:0;">
          ${p.done?'DONE':'OPEN'}
        </div>
      </div>
    </div>`;
  }).join('');

  signCard.style.display = '';
}

function togglePunchDone(id) {
  const item = state.punchItems.find(p=>p.id===id);
  if(!item) return;
  item.done = !item.done;
  item.doneDate = item.done ? new Date().toISOString().slice(0,10) : '';
  saveState();
  renderPunchField(); // full re-render so visual state is always correct
}

// ═══════════════════════════════════════════
//  PUNCH ADMIN BUILDER
// ═══════════════════════════════════════════
let editingPunchId=null, curPri='me';

function onAdminPunchJobChange() {
  const job=getJob(document.getElementById('ap_job').value);
  populateTagSelect(document.getElementById('ap_tag'), job);
  document.getElementById('punchAddForm').style.display=job?'':'none';
  renderAdminPunchList();
}

function renderAdminPunchList() {
  const jobId=document.getElementById('ap_job').value;
  const el=document.getElementById('adminPunchItems');
  if(!jobId){el.innerHTML='';return;}
  const items=state.punchItems.filter(p=>p.jobId===jobId);
  if(!items.length){el.innerHTML=`<p style="font-size:12px;color:var(--slate);margin-bottom:8px;">No items yet — add below.</p>`;return;}
  el.innerHTML=items.map(p=>`
    <div class="a-item" style="align-items:flex-start;flex-wrap:wrap;">
      <div class="a-item-info">
        <div class="a-item-name">${esc(p.desc)}</div>
        <div class="a-item-sub" style="display:flex;gap:6px;margin-top:3px;flex-wrap:wrap;">
          ${p.tag?`<span class="pf-tag" style="font-size:9px;">${esc(p.tag)}</span>`:''}
          <span class="pri-badge pri-${p.priority||'me'}">${p.priority==='lo'?'Low':p.priority==='hi'?'High':'Med'}</span>
          ${p.done?'<span style="font-size:9px;color:var(--green);">✓ Done</span>':''}
          ${p.loc?`<span style="font-size:10px;color:var(--slate);">📍 ${esc(p.loc)}</span>`:''}
        </div>
      </div>
      <button class="jbtn" onclick="editPunchItem('${p.id}')">Edit</button>
      <button class="jbtn" style="color:var(--red);border-color:var(--red);" onclick="deletePunchItem('${p.id}')">Del</button>
    </div>`).join('');
}

function setPunchPri(btn,pri) {
  document.querySelectorAll('#ap_pri_btns .pri-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active'); curPri=pri;
}

function savePunchItem() {
  const jobId=document.getElementById('ap_job').value; if(!jobId) return alert('Select a project first.');
  const desc=document.getElementById('ap_desc').value.trim(); if(!desc) return alert('Description required.');
  const existing=editingPunchId?state.punchItems.find(p=>p.id===editingPunchId):null;
  const item={
    id:editingPunchId||uid(), jobId,
    tag:document.getElementById('ap_tag').value,
    desc, loc:document.getElementById('ap_loc').value.trim(),
    due:document.getElementById('ap_due').value,
    priority:curPri,
    notes:document.getElementById('ap_notes').value.trim(),
    done:existing?existing.done:false,
    doneDate:existing?existing.doneDate:''
  };
  if(editingPunchId){const i=state.punchItems.findIndex(p=>p.id===editingPunchId);if(i>-1)state.punchItems[i]=item;}
  else state.punchItems.push(item);
  saveState(); resetPunchForm(); renderAdminPunchList();
}

function editPunchItem(id) {
  const p=state.punchItems.find(p=>p.id===id); if(!p) return;
  editingPunchId=id;
  document.getElementById('ap_desc').value=p.desc;
  document.getElementById('ap_tag').value=p.tag||'';
  document.getElementById('ap_loc').value=p.loc||'';
  document.getElementById('ap_due').value=p.due||'';
  document.getElementById('ap_notes').value=p.notes||'';
  curPri=p.priority||'me';
  document.querySelectorAll('#ap_pri_btns .pri-btn').forEach(b=>{b.classList.remove('active');if(b.classList.contains(curPri))b.classList.add('active');});
  document.getElementById('punchFormTitle').textContent='✏ Edit Punch Item';
  document.getElementById('punchAddForm').scrollIntoView({behavior:'smooth'});
}

function deletePunchItem(id) {
  if(!confirm('Delete this punch item?')) return;
  state.punchItems=state.punchItems.filter(p=>p.id!==id);
  saveState(); renderAdminPunchList();
}

function resetPunchForm() {
  editingPunchId=null; curPri='me';
  ['ap_desc','ap_loc','ap_due','ap_notes'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('ap_tag').value='';
  document.querySelectorAll('#ap_pri_btns .pri-btn').forEach(b=>{b.classList.remove('active');if(b.classList.contains('me'))b.classList.add('active');});
  document.getElementById('punchFormTitle').textContent='+ New Punch Item';
}

// ═══════════════════════════════════════════
//  SIGNATURES
// ═══════════════════════════════════════════
function initSig(id) {
  const cv=document.getElementById(id),ctx=cv.getContext('2d');
  let ink=false,lx=0,ly=0;
  const pos=e=>{const r=cv.getBoundingClientRect(),sx=cv.width/r.width,sy=cv.height/r.height;
    return e.touches?[(e.touches[0].clientX-r.left)*sx,(e.touches[0].clientY-r.top)*sy]:[(e.clientX-r.left)*sx,(e.clientY-r.top)*sy];};
  const start=e=>{e.preventDefault();ink=true;cv.classList.add('inking');[lx,ly]=pos(e);};
  const draw=e=>{if(!ink)return;e.preventDefault();const[x,y]=pos(e);ctx.beginPath();ctx.moveTo(lx,ly);ctx.lineTo(x,y);ctx.strokeStyle='#e8a020';ctx.lineWidth=2.5;ctx.lineCap='round';ctx.lineJoin='round';ctx.stroke();[lx,ly]=[x,y];};
  const stop=()=>{ink=false;cv.classList.remove('inking');};
  cv.addEventListener('mousedown',start);cv.addEventListener('mousemove',draw);cv.addEventListener('mouseup',stop);cv.addEventListener('mouseleave',stop);
  cv.addEventListener('touchstart',start,{passive:false});cv.addEventListener('touchmove',draw,{passive:false});cv.addEventListener('touchend',stop);
}
function clrSig(id){document.getElementById(id).getContext('2d').clearRect(0,0,600,140);}
function sigEmpty(id){return !document.getElementById(id).getContext('2d').getImageData(0,0,600,140).data.some(v=>v!==0);}

// ═══════════════════════════════════════════
//  TASKS
// ═══════════════════════════════════════════
function onTaskJobFilterChange() {
  const job=getJob(document.getElementById('t_jobFilter').value);
  const tagSel=document.getElementById('t_tagFilter');
  const prev=tagSel.value;
  tagSel.innerHTML='<option value="all">All Tags</option>';
  if(job) job.codes.forEach(c=>{const o=document.createElement('option');o.value=c;o.textContent=c;tagSel.appendChild(o);});
  tagSel.value=prev;
  renderTasks();
}

function onNewTaskJobChange() {
  const job=getJob(document.getElementById('t_jobSel').value);
  populateTagSelect(document.getElementById('t_tagSel'),job);
}

function addTask() {
  const text=document.getElementById('t_text').value.trim();
  if(!text){document.getElementById('t_text').focus();return;}
  state.tasks.push({
    id:uid(), text,
    jobId:document.getElementById('t_jobSel').value,
    tag:document.getElementById('t_tagSel').value,
    assigneeId:document.getElementById('t_userSel').value,
    due:document.getElementById('t_due').value,
    done:false, created:new Date().toISOString()
  });
  document.getElementById('t_text').value='';
  saveState(); renderTasks();
}

function toggleTask(id){const t=state.tasks.find(t=>t.id===id);if(t){t.done=!t.done;saveState();renderTasks();}}
function removeTask(id){state.tasks=state.tasks.filter(t=>t.id!==id);saveState();renderTasks();}

function renderTasks() {
  const jf=document.getElementById('t_jobFilter')?.value||'all';
  const tf=document.getElementById('t_tagFilter')?.value||'all';
  const uf=document.getElementById('t_userFilter')?.value||'all';
  let tasks=state.tasks;
  if(jf!=='all') tasks=tasks.filter(t=>t.jobId===jf);
  if(tf!=='all') tasks=tasks.filter(t=>t.tag===tf);
  if(uf!=='all') tasks=tasks.filter(t=>t.assigneeId===uf);
  const open=tasks.filter(t=>!t.done).length;
  const badge=document.getElementById('taskBadge');
  if(badge) badge.textContent=open+' open';
  const listEl=document.getElementById('taskList'); if(!listEl) return;
  if(!tasks.length){listEl.innerHTML=`<div style="text-align:center;color:var(--slate);font-size:13px;padding:20px;">No tasks match this filter.</div>`;return;}
  const sorted=[...tasks.filter(t=>!t.done),...tasks.filter(t=>t.done)];
  listEl.innerHTML=sorted.map(t=>{
    const job=getJob(t.jobId);
    const user=state.users.find(u=>u.id===t.assigneeId);
    return `<div class="task-item">
      <input type="checkbox" class="t-chk" ${t.done?'checked':''} onchange="toggleTask('${t.id}')">
      <div class="t-body">
        <div class="t-txt ${t.done?'done':''}">${esc(t.text)}</div>
        <div class="t-meta">
          ${job?`<span class="t-tag t-job-tag">${esc(job.name.length>20?job.name.slice(0,18)+'…':job.name)}</span>`:''}
          ${t.tag?`<span class="t-tag t-code-tag">${esc(t.tag)}</span>`:''}
          ${user?`<span class="t-user">👤 ${esc(user.name)}</span>`:''}
          ${t.due?`<span class="t-due">📅 ${t.due}</span>`:''}
        </div>
      </div>
      <button class="t-rm" onclick="removeTask('${t.id}')">✕</button>
    </div>`;
  }).join('');
}

// ═══════════════════════════════════════════
//  ADMIN
// ═══════════════════════════════════════════
let adminUnlocked=false,editingJobId=null,pendingCodes=[];

function openAdmin(){document.getElementById('adminOverlay').classList.add('open');if(!adminUnlocked){document.getElementById('adminGate').style.display='';document.getElementById('adminContent').style.display='none';}}
function closeAdmin(){document.getElementById('adminOverlay').classList.remove('open');}

function checkPW(){
  if(document.getElementById('adminPW').value===state.pw){
    adminUnlocked=true;
    document.getElementById('adminGate').style.display='none';
    document.getElementById('adminContent').style.display='';
    refreshAllDropdowns();renderJobsList();renderUserList();updateDropboxUI();
  } else {document.getElementById('pwErr').textContent='Incorrect password.';document.getElementById('adminPW').value='';}
}
function changePW(){const np=document.getElementById('newPW').value.trim();if(!np)return alert('Enter new password.');state.pw=np;saveState();document.getElementById('newPW').value='';alert('Password updated.');}

function renderJobsList(){
  document.getElementById('jobsList').innerHTML=state.jobs.map(j=>`
    <div class="a-item">
      <div class="a-item-info">
        <div class="a-item-name">${esc(j.name)} <span style="color:var(--slate);font-size:10px;">${j.num}</span></div>
        <div class="a-item-sub">${j.codes.join(' · ')||'No tags'}</div>
      </div>
      <span class="a-status ${j.status==='active'?'s-active':'s-inactive'}">${j.status}</span>
      <button class="jbtn" onclick="editJob('${j.id}')">Edit</button>
      <button class="jbtn" style="color:var(--red);border-color:var(--red);" onclick="deleteJob('${j.id}')">Del</button>
    </div>`).join('');
}

function editJob(id){
  const j=getJob(id);if(!j)return;
  editingJobId=id;pendingCodes=[...j.codes];
  document.getElementById('aj_name').value=j.name;
  document.getElementById('aj_num').value=j.num;
  document.getElementById('aj_client').value=j.client||'';
  document.getElementById('aj_status').value=j.status;
  document.getElementById('jobFormTitle').textContent='✏ Edit Project';
  renderBCChips();
  document.getElementById('aj_name').scrollIntoView({behavior:'smooth'});
}
function deleteJob(id){if(!confirm('Delete this project?'))return;state.jobs=state.jobs.filter(j=>j.id!==id);saveState();renderJobsList();refreshAllDropdowns();}
function addTag(){const v=document.getElementById('bc_new').value.trim();if(!v)return;if(!pendingCodes.includes(v))pendingCodes.push(v);document.getElementById('bc_new').value='';renderBCChips();}
function removeTag(c){pendingCodes=pendingCodes.filter(x=>x!==c);renderBCChips();}
function renderBCChips(){document.getElementById('bcList').innerHTML=pendingCodes.map(c=>`<span class="bc-chip">${esc(c)}<button onclick="removeTag(${JSON.stringify(c)})">×</button></span>`).join('');}
function saveJob(){
  const name=document.getElementById('aj_name').value.trim();if(!name)return alert('Project name required.');
  const job={id:editingJobId||uid(),name,num:document.getElementById('aj_num').value.trim(),client:document.getElementById('aj_client').value.trim(),status:document.getElementById('aj_status').value,codes:[...pendingCodes]};
  if(editingJobId){const i=state.jobs.findIndex(j=>j.id===editingJobId);if(i>-1)state.jobs[i]=job;}else state.jobs.push(job);
  saveState();resetJobForm();renderJobsList();refreshAllDropdowns();
}
function resetJobForm(){editingJobId=null;pendingCodes=[];['aj_name','aj_num','aj_client','bc_new'].forEach(id=>document.getElementById(id).value='');document.getElementById('aj_status').value='active';document.getElementById('jobFormTitle').textContent='+ New Project';document.getElementById('bcList').innerHTML='';}

function renderUserList(){
  const el=document.getElementById('userList');
  if(!state.users.length){el.innerHTML=`<p style="font-size:12px;color:var(--slate);margin-bottom:8px;">No users yet.</p>`;return;}
  el.innerHTML=state.users.map(u=>`
    <div class="a-item">
      <div class="a-item-info"><div class="a-item-name">${esc(u.name)}</div><div class="a-item-sub">${u.role}</div></div>
      <button class="jbtn" style="color:var(--red);border-color:var(--red);" onclick="deleteUser('${u.id}')">Remove</button>
    </div>`).join('');
}
function saveUser(){const name=document.getElementById('au_name').value.trim();if(!name)return alert('Name required.');state.users.push({id:uid(),name,role:document.getElementById('au_role').value});document.getElementById('au_name').value='';saveState();renderUserList();refreshAllDropdowns();}
function deleteUser(id){if(!confirm('Remove this user?'))return;state.users=state.users.filter(u=>u.id!==id);saveState();renderUserList();refreshAllDropdowns();}

// ═══════════════════════════════════════════
//  DROPBOX
// ═══════════════════════════════════════════
function updateDropboxUI(){
  const s=document.getElementById('adminDropboxStatus');
  const c=document.getElementById('dropboxConnectBtn');
  const d=document.getElementById('dropboxDisconnectBtn');
  const k=document.getElementById('dropboxAppKey');
  if(k&&state.dropboxAppKey) k.value=state.dropboxAppKey;
  if(!s) return;
  if(state.dropboxConnected){s.innerHTML='✅ <span style="color:var(--green)">Connected</span>';if(c)c.style.display='none';if(d)d.style.display='';}
  else{s.innerHTML='⚠️ <span style="color:var(--slate)">Not connected</span>';if(c)c.style.display='';if(d)d.style.display='none';}
}
function getExactRedirectUri(){
  // Strip hash and query — must exactly match what's in Dropbox developer console
  return window.location.origin + window.location.pathname;
}
function saveDropboxKey(){
  const k=document.getElementById('dropboxAppKey').value.trim();
  if(!k)return alert('Paste App Key first.');
  state.dropboxAppKey=k;saveState();
  alert('App Key saved!\n\nIMPORTANT: Make sure this exact URI is added in your Dropbox app settings:\n\n' + getExactRedirectUri() + '\n\nDropbox Developer Console → your app → Settings → OAuth 2 → Redirect URIs → Add');
}
function connectDropbox(){
  if(!state.dropboxAppKey)return alert('Save your App Key first.');
  // Show the exact URI they need before launching
  document.getElementById('dropboxRedirectUri').textContent = getExactRedirectUri();
  document.getElementById('dropboxModal').classList.add('open');
}
function launchDropboxOAuth(){
  const k=state.dropboxAppKey;if(!k)return;
  const r=encodeURIComponent(getExactRedirectUri());
  window.location.href=`https://www.dropbox.com/oauth2/authorize?client_id=${k}&response_type=token&redirect_uri=${r}`;
  closeModal('dropboxModal');
}
function disconnectDropbox(){if(!confirm('Disconnect Dropbox?'))return;state.dropboxConnected=false;state.dropboxToken='';saveState();updateDropboxUI();}
function checkDropboxCallback(){
  const h=window.location.hash;
  if(h&&h.includes('access_token')){
    const p=new URLSearchParams(h.slice(1));const t=p.get('access_token');
    if(t){state.dropboxToken=t;state.dropboxConnected=true;saveState();history.replaceState(null,'',window.location.pathname);updateDropboxUI();alert('✅ Dropbox connected! Reports will now auto-backup.');}
  }
}
async function backupToDropbox(data,jobName){
  if(!state.dropboxConnected||!state.dropboxToken) return;
  try{
    const date=new Date().toISOString().slice(0,10);
    const safe=jobName.replace(/[^a-z0-9]/gi,'_');
    await fetch('https://content.dropboxapi.com/2/files/upload',{method:'POST',
      headers:{'Authorization':'Bearer '+state.dropboxToken,'Dropbox-API-Arg':JSON.stringify({path:`/BCPS Field Logs/${safe}/${date}_${data.type}.json`,mode:'overwrite',autorename:true}),'Content-Type':'application/octet-stream'},
      body:JSON.stringify(data,null,2)});
  }catch(e){console.warn('Dropbox:',e);}
}

// ═══════════════════════════════════════════
//  SUBMIT
// ═══════════════════════════════════════════
function submitDaily(){
  const jSel=document.getElementById('d_job');if(!jSel.value){alert('Please select a Project.');return;}
  const jobName=jSel.options[jSel.selectedIndex].text;
  const report={type:'daily',job:jobName,date:document.getElementById('d_date').value,pm_super:document.getElementById('d_super').value,tags:getSelectedDailyTags(),submitted:new Date().toISOString()};
  backupToDropbox(report,jobName);
  showConfirm('✅ Daily Report Submitted',`Daily log for "${jobName}" recorded.${state.dropboxConnected?'\n\nSaving to Dropbox…':'\n\nConnect Dropbox in Admin to auto-backup.'}`);
}

function submitPunch(){
  const jSel=document.getElementById('p_job');if(!jSel.value){alert('Select a Project.');return;}
  if(sigEmpty('sigS')){alert('Superintendent signature required.');return;}
  if(sigEmpty('sigP')){alert('Project Manager signature required.');return;}
  const jobName=jSel.options[jSel.selectedIndex].text;
  const items=state.punchItems.filter(p=>p.jobId===jSel.value);
  const done=items.filter(p=>p.done).length;
  const report={type:'punch',job:jobName,date:document.getElementById('ps_date').value,super:document.getElementById('ss_name').value,pm:document.getElementById('sp_name').value,items_complete:done,items_total:items.length,submitted:new Date().toISOString()};
  backupToDropbox(report,jobName);
  showConfirm('✅ Punch List Signed',`"${jobName}" punch list signed.\n${done} of ${items.length} items complete.${state.dropboxConnected?'\n\nSaving to Dropbox…':''}`);
}

function showConfirm(t,m){document.getElementById('cm_title').textContent=t;document.getElementById('cm_msg').textContent=m;document.getElementById('confirmModal').classList.add('open');}
function closeModal(id){document.getElementById(id).classList.remove('open');}

function exportData(){const b=new Blob([JSON.stringify(state,null,2)],{type:'application/json'});const a=document.createElement('a');a.href=URL.createObjectURL(b);a.download='bcps_data_'+new Date().toISOString().slice(0,10)+'.json';a.click();}
function importData(){document.getElementById('importFile').click();}
function doImport(e){const f=e.target.files[0];if(!f)return;const r=new FileReader();r.onload=ev=>{try{const d=JSON.parse(ev.target.result);if(confirm('Replace all current data?')){state=d;saveState();refreshAllDropdowns();renderJobsList();renderUserList();renderTasks();updateDropboxUI();alert('Imported.');}}catch(err){alert('Invalid file.');}};r.readAsText(f);e.target.value='';}
</script>
</body>
</html>
