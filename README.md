[Uploading index.htm.html…]()
<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sylvia Core · Finance Hub</title>
<script>
(function(){
  function load(src,ok,err){var s=document.createElement('script');s.src=src;s.onload=ok;s.onerror=err;document.head.appendChild(s);}
  var xu=['https://cdn.jsdelivr.net/npm/xlsx@0.18.5/dist/xlsx.full.min.js','https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js','https://unpkg.com/xlsx@0.18.5/dist/xlsx.full.min.js'];
  var cu=['https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js','https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js','https://unpkg.com/chart.js@4.4.1/dist/chart.umd.min.js'];
  function tryX(i){if(i>=xu.length)return;load(xu[i],function(){tryC(0);},function(){tryX(i+1);});}
  function tryC(i){if(i>=cu.length)return;load(cu[i],function(){},function(){tryC(i+1);});}
  tryX(0);
})();
</script>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@400;500;600;700;800&family=Noto+Sans+TC:wght@300;400;500;700&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
:root{
  /* ── 時尚配色系統 ── */
  --navy:   #1E2D5A;  /* 深靛藍：權威 header */
  --navy2:  #2A3F7E;  /* 次深藍 */
  --coral:  #FFA07A;  /* 蜜桃橘：主強調 */
  --coral2: #FFB89A;  /* 淺蜜桃 */
  --emerald:#00C48C;  /* 翡翠：正增長 */
  --rose:   #FF4D6D;  /* 玫瑰：負增長 */
  --gold:   #FFB627;  /* 金黃：第三色 */
  --violet: #7C5CFC;  /* 紫羅蘭：第四色 */
  --sky:    #38BDF8;  /* 天藍：第五色 */

  /* ── 中性色 ── */
  --bg:      #F6F7FB;
  --surface: #FFFFFF;
  --surf2:   #F0F2F8;
  --border:  #E4E8F0;
  --border2: #D0D6E8;

  /* ── 文字 ── */
  --ink:   #0F172A;
  --ink2:  #475569;
  --ink3:  #94A3B8;

  --radius: 14px;
  --mono:  'DM Mono', monospace;
  --sans:  'Noto Sans TC', sans-serif;
  --title: 'Outfit', 'Noto Sans TC', sans-serif;
  --shadow-sm: 0 1px 3px rgba(0,0,0,.06), 0 2px 8px rgba(0,0,0,.04);
  --shadow:    0 2px 8px rgba(0,0,0,.07), 0 8px 24px rgba(0,0,0,.05);
}
*{box-sizing:border-box;margin:0;padding:0}
body{background:var(--bg);color:var(--ink);font-family:var(--sans);font-size:14px;min-height:100vh}

/* ═══════════════════════════════
   HEADER — 深靛藍滿版
══════════════════════════════ */
header{
  background:var(--navy);
  padding:0 32px;
  height:60px;
  display:flex;align-items:center;justify-content:space-between;
  position:sticky;top:0;z-index:200;
  box-shadow:0 2px 16px rgba(30,45,90,.3);
}
.logo{display:flex;align-items:center;gap:12px}
.logo-mark{
  width:36px;height:36px;border-radius:10px;
  background:linear-gradient(135deg,#FFA07A,#FFB627);
  display:flex;align-items:center;justify-content:center;
  font-family:var(--title);font-weight:800;font-size:15px;color:#fff;
  box-shadow:0 2px 10px rgba(255,160,122,.35);
}
.logo-text{font-family:var(--title);font-size:16px;font-weight:700;color:#fff;letter-spacing:.01em}
.logo-sub{font-size:11px;color:rgba(255,255,255,.45);margin-top:1px;font-family:var(--sans)}
.hdr-right{display:flex;align-items:center;gap:10px}
#fileInfo{font-size:11px;color:rgba(255,255,255,.45);font-family:var(--mono)}
.btn-hdr{
  padding:7px 16px;border-radius:8px;
  background:rgba(255,160,122,.18);border:1px solid rgba(255,160,122,.4);
  color:#FFB89A;font-size:12px;cursor:pointer;
  font-family:var(--sans);font-weight:500;transition:all .15s;
}
.btn-hdr:hover{background:#FFA07A;color:#fff;border-color:#FFA07A}

/* ═══════════════════════════════
   TOAST
══════════════════════════════ */
#toast{
  display:none;position:fixed;top:72px;left:50%;transform:translateX(-50%);
  background:var(--navy);color:#fff;
  padding:10px 24px;border-radius:10px;font-size:13px;font-weight:500;
  z-index:999;box-shadow:0 8px 24px rgba(30,45,90,.3);
  border-left:3px solid var(--coral);
}

/* ═══════════════════════════════
   SAVED BAR
══════════════════════════════ */
#savedBar{
  display:none;padding:8px 32px;
  background:#fff;border-bottom:1px solid var(--border);
  font-size:12px;color:var(--ink2);
  align-items:center;gap:8px;flex-wrap:wrap;
}
.m-tag{
  display:inline-flex;align-items:center;gap:4px;
  background:var(--surf2);border:1px solid var(--border);
  border-radius:6px;padding:3px 9px;font-size:11px;
  font-family:var(--mono);color:var(--navy2);
}
.m-del{cursor:pointer;color:var(--ink3);margin-left:2px;font-size:13px}
.m-del:hover{color:var(--rose)}
.btn-clear{
  margin-left:auto;padding:4px 10px;border-radius:6px;
  border:1px solid #ffc9d0;background:transparent;color:var(--rose);
  font-size:11px;cursor:pointer;font-family:var(--sans);
}

/* ═══════════════════════════════
   UPLOAD SCREEN
══════════════════════════════ */
#uploadSection{
  display:flex;flex-direction:column;align-items:center;
  justify-content:center;min-height:calc(100vh - 60px);padding:40px;
}
.drop-zone{
  width:100%;max-width:520px;
  border:2px dashed var(--border2);border-radius:20px;
  padding:60px 44px;text-align:center;cursor:pointer;
  transition:all .2s;background:var(--surface);
  box-shadow:var(--shadow);
}
.drop-zone:hover,.drop-zone.over{
  border-color:var(--coral);background:linear-gradient(135deg,#fff8f6,#fff);
  transform:translateY(-3px);box-shadow:0 8px 32px rgba(255,160,122,.12);
}
.drop-icon{font-size:44px;margin-bottom:18px}
.drop-title{font-family:var(--title);font-size:20px;font-weight:700;margin-bottom:8px;color:var(--ink)}
.drop-sub{font-size:13px;color:var(--ink2);line-height:1.65}
.drop-btn{
  display:inline-block;margin-top:24px;
  padding:11px 30px;background:linear-gradient(135deg,#FFA07A,#FFB89A);
  color:#fff;border-radius:10px;font-size:13px;font-weight:600;
  cursor:pointer;box-shadow:0 4px 14px rgba(255,160,122,.35);
  transition:transform .15s,box-shadow .15s;
  font-family:var(--title);letter-spacing:.02em;
}
.drop-btn:hover{transform:translateY(-1px);box-shadow:0 6px 20px rgba(255,160,122,.45)}
.drop-hint{margin-top:14px;font-size:11px;color:var(--ink3);font-family:var(--mono)}
.data-status{
  margin-top:22px;padding:16px 22px;
  background:#F0FDF8;border:1px solid #A7F3D0;
  border-radius:12px;font-size:12px;color:#065F46;
  max-width:520px;width:100%;line-height:1.9;
}

/* ═══════════════════════════════
   DASHBOARD
══════════════════════════════ */
#dashboard{display:none;padding:24px 32px 48px}

/* ── View bar ── */
.view-bar{display:flex;align-items:center;gap:10px;margin-bottom:20px;flex-wrap:wrap}
.view-title{
  font-family:var(--title);font-size:17px;font-weight:700;
  margin-right:auto;color:var(--navy);letter-spacing:-.01em;
}
.view-title em{color:var(--coral);font-style:normal}
.toggle-grp{
  display:flex;background:var(--surface);border:1.5px solid var(--border);
  border-radius:10px;overflow:hidden;box-shadow:var(--shadow-sm);
}
.t-btn{
  padding:7px 18px;font-size:12px;font-weight:600;
  cursor:pointer;border:none;background:transparent;
  color:var(--ink2);font-family:var(--title);transition:all .15s;
}
.t-btn.on{background:var(--navy);color:#fff}
.t-btn:hover:not(.on){background:var(--surf2);color:var(--navy)}

/* ── KPI Row ── */
.kpi-row{display:grid;grid-template-columns:repeat(5,1fr);gap:14px;margin-bottom:22px}
.kpi{
  background:var(--surface);border:1.5px solid var(--border);
  border-radius:var(--radius);padding:18px 20px;
  position:relative;overflow:hidden;box-shadow:var(--shadow-sm);
  transition:transform .15s,box-shadow .15s;
}
.kpi:hover{transform:translateY(-2px);box-shadow:var(--shadow)}
.kpi::before{
  content:'';position:absolute;top:0;left:0;right:0;height:3.5px;
  background:linear-gradient(90deg,var(--c1),var(--c2));
}
.kpi-lbl{
  font-size:10px;color:var(--ink3);letter-spacing:.1em;
  text-transform:uppercase;margin-bottom:8px;
  font-family:var(--title);font-weight:600;
}
.kpi-val{
  font-size:21px;font-weight:700;font-family:var(--mono);
  letter-spacing:-.03em;color:var(--ink);line-height:1.2;
}
.kpi-sub{font-size:11px;color:var(--ink2);margin-top:6px;line-height:1.4}
.kpi-badge{
  display:inline-flex;align-items:center;gap:3px;
  font-size:11px;font-family:var(--mono);font-weight:700;
  padding:3px 8px;border-radius:6px;margin-top:6px;
}
.b-up{background:#D1FAE5;color:#065F46}
.b-dn{background:#FFE4E6;color:#9F1239}

/* ── Chart Grid ── */
.chart-row{display:grid;grid-template-columns:1.5fr 1fr;gap:16px;margin-bottom:16px}
.chart-row2{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:16px}
.card{
  background:var(--surface);border:1.5px solid var(--border);
  border-radius:var(--radius);padding:20px;box-shadow:var(--shadow-sm);
}
.card-hdr{display:flex;align-items:flex-start;justify-content:space-between;margin-bottom:16px;gap:8px}
.card-title{font-family:var(--title);font-size:13.5px;font-weight:700;color:var(--ink)}
.card-sub{font-size:11px;color:var(--ink3);margin-top:2px}
.leg-row{display:flex;gap:12px;flex-wrap:wrap;align-items:center}
.leg{display:flex;align-items:center;gap:5px;font-size:11px;color:var(--ink2);font-family:var(--title);font-weight:500}
.leg-dot{width:8px;height:8px;border-radius:3px}
.chart-wrap{position:relative}

/* ── Table ── */
.tbl-card{
  background:var(--surface);border:1.5px solid var(--border);
  border-radius:var(--radius);overflow:hidden;box-shadow:var(--shadow-sm);
}
.tbl-bar{
  padding:14px 20px;border-bottom:1.5px solid var(--border);
  display:flex;align-items:center;gap:10px;flex-wrap:wrap;
  background:linear-gradient(135deg,#F8F9FF,#F4F6FD);
}
.tbl-title{font-family:var(--title);font-size:14px;font-weight:700;margin-right:auto;color:var(--navy)}
.srch{
  background:#fff;border:1.5px solid var(--border);border-radius:8px;
  padding:7px 12px;color:var(--ink);font-size:12px;
  font-family:var(--sans);outline:none;width:180px;transition:border-color .2s;
}
.srch:focus{border-color:var(--coral);box-shadow:0 0 0 3px rgba(255,107,71,.12)}
.srch::placeholder{color:var(--ink3)}
select.ctrl{
  background:#fff;border:1.5px solid var(--border);border-radius:8px;
  padding:7px 10px;color:var(--ink);font-size:12px;
  font-family:var(--sans);outline:none;cursor:pointer;
}
select.ctrl:focus{border-color:var(--navy)}
.tbl-wrap{overflow-x:auto}
table{width:100%;border-collapse:collapse;font-size:12.5px}
thead th{
  padding:11px 14px;text-align:left;font-size:10px;font-weight:700;
  color:var(--ink3);letter-spacing:.08em;text-transform:uppercase;
  border-bottom:1.5px solid var(--border);white-space:nowrap;
  background:#FAFBFF;font-family:var(--title);
}
thead th.r{text-align:right}
tbody td{padding:10px 14px;border-bottom:1px solid #F1F3F9;white-space:nowrap;color:var(--ink)}
tbody td.r{text-align:right;font-family:var(--mono);font-size:12px}
tbody td.dim{color:var(--ink3);font-family:var(--mono);font-size:11px}
tbody tr:hover td{background:#F8F9FF}
tbody tr:last-child td{border-bottom:none}
.pill{
  display:inline-block;padding:2px 8px;border-radius:5px;
  font-size:10px;font-weight:700;font-family:var(--mono);
}
.p-up{background:#D1FAE5;color:#065F46}
.p-dn{background:#FFE4E6;color:#9F1239}
.p-new{background:#FEF3C7;color:#92400E}
.p-na{background:#F1F5F9;color:#64748B}
.tbl-foot{
  padding:10px 20px;font-size:11px;color:var(--ink3);text-align:right;
  border-top:1px solid var(--border);font-family:var(--mono);
  background:#FAFBFF;
}

@media(max-width:900px){
  .kpi-row{grid-template-columns:repeat(2,1fr)}
  .chart-row,.chart-row2{grid-template-columns:1fr}
  #dashboard{padding:14px 16px 40px}
  header{padding:0 16px}
  #savedBar{padding:8px 16px}
}
</style>
</head>
<body>
<div id="toast"></div>

<header>
  <div class="logo">
    <div class="logo-mark">SF</div>
    <div>
      <div class="logo-text">Sylvia Finance</div>
      <div class="logo-sub">Finance Hub · 應收帳款儀表板</div>
    </div>
  </div>
  <div class="hdr-right">
    <span id="fileInfo">2026年：尚未載入</span>
    <button class="btn-hdr" onclick="document.getElementById('fi2').click()">＋ 新增月份</button>
    <input type="file" id="fi2" accept=".xlsx,.xls" style="display:none" onchange="handleFile(this.files[0])">
  </div>
</header>

<div id="savedBar">
  <span style="font-weight:600;color:var(--navy)">2026 已儲存：</span>
  <div id="mTags"></div>
  <button class="btn-clear" onclick="clearAll()">🗑 清除 2026</button>
</div>

<div id="uploadSection">
  <div class="drop-zone" id="dz">
    <div class="drop-icon">📊</div>
    <div class="drop-title">拖曳 2026 年 Excel 到這裡</div>
    <div class="drop-sub">每月上傳自動疊加，不覆蓋舊資料<br>2024、2025 全年資料已內建</div>
    <label class="drop-btn" for="fi">選擇檔案</label>
    <input type="file" id="fi" accept=".xlsx,.xls" style="display:none" onchange="handleFile(this.files[0])">
    <div class="drop-hint">支援格式：.xlsx / .xls</div>
  </div>
  <div class="data-status">
    ✅ 2024 全年內建（1–12月）<br>
    ✅ 2025 全年內建（1–12月）<br>
    ⬆ 請上傳 2026 年 Excel，系統自動計算 YoY & MoM
  </div>
</div>

<div id="dashboard">
  <div class="view-bar">
    <div class="view-title" id="vTitle">應收帳款分析 <em>·</em></div>
    <div class="toggle-grp">
      <button class="t-btn on" id="btn26" onclick="setView('2026')">2026年</button>
      <button class="t-btn" id="btn25" onclick="setView('2025')">2025年</button>
      <button class="t-btn" id="btn24" onclick="setView('2024')">2024年</button>
      <button class="t-btn" id="btnYoY" onclick="setView('yoy')">YoY 同期</button>
      <button class="t-btn" id="btnMoM" onclick="setView('mom')">MoM 月增</button>
    </div>
  </div>
  <div class="kpi-row" id="kpiRow"></div>
  <div class="chart-row">
    <div class="card">
      <div class="card-hdr">
        <div><div class="card-title" id="barTitle">前 10 大客戶</div><div class="card-sub" id="barSub"></div></div>
        <div class="leg-row" id="barLeg"></div>
      </div>
      <div class="chart-wrap" style="height:300px"><canvas id="barC"></canvas></div>
    </div>
    <div class="card">
      <div class="card-hdr">
        <div><div class="card-title">月趨勢</div><div class="card-sub" id="lineSub"></div></div>
        <div class="leg-row" id="lineLeg"></div>
      </div>
      <div class="chart-wrap" style="height:300px"><canvas id="lineC"></canvas></div>
    </div>
  </div>
  <div class="chart-row2">
    <div class="card">
      <div class="card-hdr">
        <div><div class="card-title" id="yoyBarTitle">YoY 年增率</div><div class="card-sub" id="yoyBarSub"></div></div>
      </div>
      <div class="chart-wrap" style="height:230px"><canvas id="yoyBarC"></canvas></div>
    </div>
    <div class="card">
      <div class="card-hdr">
        <div><div class="card-title" id="momBarTitle">MoM 月增率</div><div class="card-sub" id="momBarSub"></div></div>
      </div>
      <div class="chart-wrap" style="height:230px"><canvas id="momBarC"></canvas></div>
    </div>
  </div>
  <div class="tbl-card">
    <div class="tbl-bar">
      <span class="tbl-title">客戶明細</span>
      <input class="srch" id="srch" placeholder="搜尋客戶名稱 / 編號…" oninput="renderTable()">
      <select class="ctrl" id="tSort" onchange="renderTable()">
        <option value="latest">最新月 ↓</option>
        <option value="total">累計 ↓</option>
        <option value="yoy">YoY ↓</option>
        <option value="name">名稱</option>
      </select>
      <select class="ctrl" id="tFilter" onchange="renderTable()">
        <option value="all">全部客戶</option>
        <option value="active">最新月有資料</option>
        <option value="new">最新月新增</option>
        <option value="miss">最新月無資料</option>
      </select>
    </div>
    <div class="tbl-wrap"><table><thead id="tHead"></thead><tbody id="tBody"></tbody></table></div>
    <div class="tbl-foot" id="tFoot"></div>
  </div>
</div>

<script>
// ── 時尚暖色系圖表配色 ──
const PAL = ['#1E3A8A','#FFA07A','#FFB627','#00C48C','#E8F500'];
const PAL2 = ['#FFB89A','#FFC84D','#33D9A7','#60CDFF','#F0FF70','#FF7A91','#FBBF24','#34D399','#818CF8','#F472B6'];

const DATA = {
  2024: [{"id":"A15003","name":"三元第","1月":837696,"1月_tax":41885,"2月":464784,"2月_tax":23239,"3月":73680,"3月_tax":3684,"4月":614160,"4月_tax":30708,"5月":211320,"5月_tax":10566,"6月":318360,"6月_tax":15918,"7月":60720,"7月_tax":3036,"8月":762060,"8月_tax":38103,"9月":54000,"9月_tax":2700,"10月":523680,"10月_tax":26184,"11月":670560,"11月_tax":33528,"12月":45120,"12月_tax":2256},{"id":"A15007","name":"文正","1月":733603,"1月_tax":12000,"2月":355383,"2月_tax":6000,"3月":160247,"3月_tax":2640,"4月":189366,"4月_tax":3156,"5月":340722,"5月_tax":0,"6月":193224,"6月_tax":3200,"7月":218584,"7月_tax":3645,"8月":240830,"8月_tax":3948,"9月":307154,"9月_tax":5104,"10月":283418,"10月_tax":4033,"11月":346716,"11月_tax":5781,"12月":602560,"12月_tax":0},{"id":"A15011","name":"長億","1月":140400,"1月_tax":7020,"2月":120720,"2月_tax":6036,"3月":0,"3月_tax":0,"4月":25920,"4月_tax":1296,"5月":91360,"5月_tax":4568,"6月":33120,"6月_tax":1656,"7月":38640,"7月_tax":1932,"8月":55640,"8月_tax":2782,"9月":85872,"9月_tax":4294,"10月":50640,"10月_tax":2105,"11月":5796,"11月_tax":290,"12月":29024,"12月_tax":1451},{"id":"A15017","name":"統富","1月":330,"1月_tax":17,"2月":42240,"2月_tax":2112,"3月":26400,"3月_tax":1104,"4月":206880,"4月_tax":10344,"5月":52800,"5月_tax":2640,"6月":15840,"6月_tax":787,"7月":26400,"7月_tax":1320,"8月":63360,"8月_tax":3168,"9月":68640,"9月_tax":3432,"10月":29952,"10月_tax":1498,"11月":101070,"11月_tax":5054,"12月":50400,"12月_tax":2520},{"id":"A15039","name":"名信","1月":87696,"1月_tax":0,"2月":37584,"2月_tax":0,"3月":35676,"3月_tax":0,"4月":70068,"4月_tax":0,"5月":59280,"5月_tax":0,"6月":52632,"6月_tax":0,"7月":89952,"7月_tax":0,"8月":70848,"8月_tax":0,"9月":25356,"9月_tax":0,"10月":34344,"10月_tax":0,"11月":43644,"11月_tax":0,"12月":70332,"12月_tax":0},{"id":"A15041","name":"名翔","1月":285744,"1月_tax":0,"2月":297534,"2月_tax":0,"3月":30450,"3月_tax":0,"4月":72246,"4月_tax":0,"5月":147648,"5月_tax":0,"6月":138534,"6月_tax":0,"7月":41634,"7月_tax":0,"8月":140724,"8月_tax":0,"9月":15762,"9月_tax":0,"10月":94250,"10月_tax":0,"11月":58494,"11月_tax":0,"12月":176022,"12月_tax":0},{"id":"A15049","name":"佳崚","1月":141424,"1月_tax":0,"2月":70446,"2月_tax":3522,"3月":43044,"3月_tax":2152,"4月":18198,"4月_tax":910,"5月":50802,"5月_tax":2540,"6月":22416,"6月_tax":1121,"7月":37554,"7月_tax":1878,"8月":52166,"8月_tax":2608,"9月":41412,"9月_tax":2071,"10月":50058,"10月_tax":2503,"11月":74218,"11月_tax":3711,"12月":129306,"12月_tax":6465},{"id":"A15061","name":"威麗士","1月":108424,"1月_tax":5421,"2月":0,"2月_tax":0,"3月":17400,"3月_tax":870,"4月":5760,"4月_tax":288,"5月":5800,"5月_tax":290,"6月":19800,"6月_tax":990,"7月":11600,"7月_tax":580,"8月":28700,"8月_tax":1435,"9月":5800,"9月_tax":290,"10月":15700,"10月_tax":785,"11月":22350,"11月_tax":0,"12月":48568,"12月_tax":1529},{"id":"A15066","name":"益鋒","1月":144000,"1月_tax":0,"2月":135000,"2月_tax":0,"3月":0,"3月_tax":0,"4月":19200,"4月_tax":0,"5月":54000,"5月_tax":0,"6月":12000,"6月_tax":0,"7月":0,"7月_tax":0,"8月":87000,"8月_tax":0,"9月":0,"9月_tax":0,"10月":21000,"10月_tax":0,"11月":17700,"11月_tax":0,"12月":46200,"12月_tax":0},{"id":"A15087","name":"震輝","1月":87660,"1月_tax":2343,"2月":12000,"2月_tax":594,"3月":18090,"3月_tax":905,"4月":58788,"4月_tax":2939,"5月":53892,"5月_tax":2695,"6月":39720,"6月_tax":1986,"7月":18000,"7月_tax":900,"8月":44070,"8月_tax":2204,"9月":7890,"9月_tax":395,"10月":50274,"10月_tax":2514,"11月":122184,"11月_tax":6109,"12月":58536,"12月_tax":2927},{"id":"A15088","name":"繁星","1月":108216,"1月_tax":5411,"2月":45072,"2月_tax":1638,"3月":13200,"3月_tax":660,"4月":24000,"4月_tax":1200,"5月":111600,"5月_tax":5580,"6月":0,"6月_tax":0,"7月":58650,"7月_tax":2933,"8月":41700,"8月_tax":2085,"9月":27900,"9月_tax":1395,"10月":39600,"10月_tax":1980,"11月":56568,"11月_tax":2828,"12月":117744,"12月_tax":5887},{"id":"A15090","name":"九龍","1月":26400,"1月_tax":1320,"2月":0,"2月_tax":0,"3月":69400,"3月_tax":3470,"4月":26400,"4月_tax":1320,"5月":15840,"5月_tax":792,"6月":26070,"6月_tax":1304,"7月":52140,"7月_tax":2607,"8月":38520,"8月_tax":1926,"9月":21120,"9月_tax":1056,"10月":46530,"10月_tax":2273,"11月":32720,"11月_tax":1636,"12月":37480,"12月_tax":1874},{"id":"A15113","name":"方盛育","1月":266760,"1月_tax":0,"2月":300048,"2月_tax":0,"3月":0,"3月_tax":0,"4月":0,"4月_tax":0,"5月":0,"5月_tax":0,"6月":0,"6月_tax":0,"7月":0,"7月_tax":0,"8月":0,"8月_tax":0,"9月":0,"9月_tax":0,"10月":0,"10月_tax":0,"11月":0,"11月_tax":0,"12月":443448,"12月_tax":0},{"id":"A15133","name":"匯勤","1月":0,"1月_tax":0,"2月":0,"2月_tax":0,"3月":0,"3月_tax":0,"4月":0,"4月_tax":0,"5月":0,"5月_tax":0,"6月":0,"6月_tax":0,"7月":0,"7月_tax":0,"8月":0,"8月_tax":0,"9月":765787,"9月_tax":38290,"10月":3519857,"10月_tax":175993,"11月":964603,"11月_tax":48230,"12月":0,"12月_tax":0},{"id":"A15134","name":"聯端","1月":0,"1月_tax":0,"2月":45120,"2月_tax":2256,"3月":107160,"3月_tax":5358,"4月":163560,"4月_tax":8178,"5月":0,"5月_tax":0,"6月":0,"6月_tax":0,"7月":0,"7月_tax":0,"8月":0,"8月_tax":0,"9月":0,"9月_tax":0,"10月":104400,"10月_tax":5220,"11月":117900,"11月_tax":5895,"12月":36000,"12月_tax":1778},{"id":"A15149","name":"恭赫","1月":33810,"1月_tax":1691,"2月":33760,"2月_tax":1688,"3月":11760,"3月_tax":588,"4月":23520,"4月_tax":1176,"5月":27880,"5月_tax":1394,"6月":51400,"6月_tax":2570,"7月":35280,"7月_tax":1764,"8月":22000,"8月_tax":1100,"9月":11000,"9月_tax":550,"10月":63160,"10月_tax":3158,"11月":21240,"11月_tax":1062,"12月":53480,"12月_tax":2674},{"id":"A15170","name":"上友","1月":61776,"1月_tax":0,"2月":12000,"2月_tax":0,"3月":0,"3月_tax":0,"4月":9150,"4月_tax":0,"5月":13416,"5月_tax":0,"6月":13458,"6月_tax":0,"7月":16134,"7月_tax":0,"8月":8400,"8月_tax":0,"9月":5670,"9月_tax":0,"10月":7470,"10月_tax":0,"11月":34140,"11月_tax":0,"12月":55056,"12月_tax":0},{"id":"A15220","name":"東蒙","1月":44460,"1月_tax":2223,"2月":0,"2月_tax":0,"3月":20490,"3月_tax":1025,"4月":84270,"4月_tax":4214,"5月":40680,"5月_tax":2035,"6月":70158,"6月_tax":3508,"7月":88790,"7月_tax":4440,"8月":42360,"8月_tax":2118,"9月":41550,"9月_tax":2078,"10月":61120,"10月_tax":3057,"11月":31160,"11月_tax":1558,"12月":43402,"12月_tax":2170},{"id":"A15224","name":"宥展","1月":28200,"1月_tax":1410,"2月":40440,"2月_tax":2022,"3月":52680,"3月_tax":2634,"4月":35760,"4月_tax":1788,"5月":0,"5月_tax":0,"6月":82800,"6月_tax":4140,"7月":0,"7月_tax":0,"8月":47040,"8月_tax":2352,"9月":0,"9月_tax":0,"10月":52680,"10月_tax":2634,"11月":31080,"11月_tax":1554,"12月":40440,"12月_tax":2022},{"id":"A15231","name":"麗佩沛","1月":1183468,"1月_tax":59322,"2月":0,"2月_tax":0,"3月":0,"3月_tax":0,"4月":0,"4月_tax":0,"5月":0,"5月_tax":0,"6月":0,"6月_tax":0,"7月":0,"7月_tax":0,"8月":0,"8月_tax":0,"9月":1020351,"9月_tax":0,"10月":356186,"10月_tax":68827,"11月":0,"11月_tax":0,"12月":413064,"12月_tax":20653}],
  2025: [{"id":"A15003","name":"三元第","1月":421800,"1月_tax":21090,"2月":99120,"2月_tax":4956,"3月":59400,"3月_tax":2970,"4月":366600,"4月_tax":18330,"5月":274540,"5月_tax":13727,"6月":506860,"6月_tax":25343,"7月":228800,"7月_tax":11440,"8月":17160,"8月_tax":858,"9月":147600,"9月_tax":7380,"10月":59400,"10月_tax":2970,"11月":523800,"11月_tax":26190,"12月":226680,"12月_tax":11334},{"id":"A15006","name":"天堂鳥","1月":0,"1月_tax":0,"2月":0,"2月_tax":0,"3月":0,"3月_tax":0,"4月":0,"4月_tax":0,"5月":0,"5月_tax":0,"6月":0,"6月_tax":0,"7月":0,"7月_tax":0,"8月":0,"8月_tax":0,"9月":0,"9月_tax":0,"10月":540,"10月_tax":0,"11月":0,"11月_tax":0,"12月":0,"12月_tax":0},{"id":"A15007","name":"文正","1月":899794,"1月_tax":15005,"2月":302387,"2月_tax":5040,"3月":136006,"3月_tax":2246,"4月":123686,"4月_tax":2074,"5月":153518,"5月_tax":2554,"6月":175380,"6月_tax":2700,"7月":214390,"7月_tax":3564,"8月":323618,"8月_tax":5400,"9月":247280,"9月_tax":0,"10月":208704,"10月_tax":3472,"11月":662746,"11月_tax":11052,"12月":732810,"12月_tax":12160},{"id":"A15011","name":"長億","1月":114384,"1月_tax":5719,"2月":98640,"2月_tax":4932,"3月":16560,"3月_tax":828,"4月":0,"4月_tax":0,"5月":499588,"5月_tax":24979,"6月":121050,"6月_tax":6053,"7月":43680,"7月_tax":2184,"8月":33040,"8月_tax":998,"9月":3200,"9月_tax":160,"10月":27600,"10月_tax":1380,"11月":127872,"11月_tax":6394,"12月":67200,"12月_tax":3360},{"id":"A15017","name":"統富","1月":129530,"1月_tax":6477,"2月":15840,"2月_tax":792,"3月":55200,"3月_tax":1980,"4月":0,"4月_tax":0,"5月":21120,"5月_tax":1056,"6月":42240,"6月_tax":2112,"7月":26400,"7月_tax":1320,"8月":15840,"8月_tax":492,"9月":52800,"9月_tax":2640,"10月":45840,"10月_tax":2292,"11月":46020,"11月_tax":2301,"12月":49900,"12月_tax":2495},{"id":"A15041","name":"名翔","1月":411312,"1月_tax":0,"2月":54270,"2月_tax":0,"3月":79752,"3月_tax":0,"4月":15690,"4月_tax":0,"5月":138522,"5月_tax":0,"6月":132720,"6月_tax":0,"7月":64962,"7月_tax":0,"8月":68622,"8月_tax":0,"9月":113208,"9月_tax":0,"10月":60756,"10月_tax":0,"11月":200790,"11月_tax":0,"12月":260790,"12月_tax":0},{"id":"A15049","name":"佳崚","1月":151572,"1月_tax":7579,"2月":68634,"2月_tax":0,"3月":22068,"3月_tax":1103,"4月":24937,"4月_tax":0,"5月":38630,"5月_tax":1932,"6月":50890,"6月_tax":2545,"7月":26928,"7月_tax":1346,"8月":29816,"8月_tax":1491,"9月":44317,"9月_tax":2216,"10月":45744,"10月_tax":0,"11月":61874,"11月_tax":3094,"12月":96752,"12月_tax":4838},{"id":"A15066","name":"益鋒","1月":217200,"1月_tax":0,"2月":0,"2月_tax":0,"3月":0,"3月_tax":0,"4月":6720,"4月_tax":0,"5月":0,"5月_tax":0,"6月":28800,"6月_tax":0,"7月":54840,"7月_tax":0,"8月":24840,"8月_tax":0,"9月":39600,"9月_tax":0,"10月":21060,"10月_tax":0,"11月":12000,"11月_tax":0,"12月":33900,"12月_tax":0},{"id":"A15087","name":"震輝","1月":133656,"1月_tax":6683,"2月":29346,"2月_tax":1467,"3月":12600,"3月_tax":630,"4月":0,"4月_tax":0,"5月":50262,"5月_tax":1456,"6月":36480,"6月_tax":1824,"7月":24810,"7月_tax":1241,"8月":62784,"8月_tax":3139,"9月":30624,"9月_tax":1531,"10月":13050,"10月_tax":653,"11月":26520,"11月_tax":1326,"12月":99126,"12月_tax":4956},{"id":"A15088","name":"繁星","1月":165024,"1月_tax":8251,"2月":58800,"2月_tax":2940,"3月":13950,"3月_tax":698,"4月":11280,"4月_tax":552,"5月":39450,"5月_tax":1973,"6月":42000,"6月_tax":2100,"7月":48120,"7月_tax":2371,"8月":31200,"8月_tax":1560,"9月":38280,"9月_tax":1914,"10月":19200,"10月_tax":960,"11月":127062,"11月_tax":6353,"12月":118950,"12月_tax":5948},{"id":"A15090","name":"九龍","1月":21120,"1月_tax":1056,"2月":36300,"2月_tax":1815,"3月":44320,"3月_tax":2216,"4月":20790,"4月_tax":1040,"5月":31680,"5月_tax":1584,"6月":59640,"6月_tax":2982,"7月":63410,"7月_tax":3171,"8月":42430,"8月_tax":2122,"9月":58790,"9月_tax":2940,"10月":48560,"10月_tax":2428,"11月":49080,"11月_tax":2454,"12月":41480,"12月_tax":2074},{"id":"A15113","name":"方盛育","1月":335112,"1月_tax":0,"2月":201528,"2月_tax":0,"3月":0,"3月_tax":0,"4月":0,"4月_tax":0,"5月":0,"5月_tax":0,"6月":0,"6月_tax":0,"7月":0,"7月_tax":0,"8月":0,"8月_tax":0,"9月":0,"9月_tax":0,"10月":0,"10月_tax":0,"11月":167832,"11月_tax":0,"12月":166728,"12月_tax":0},{"id":"A15133","name":"匯勤","1月":0,"1月_tax":0,"2月":0,"2月_tax":0,"3月":0,"3月_tax":0,"4月":0,"4月_tax":0,"5月":0,"5月_tax":0,"6月":0,"6月_tax":0,"7月":0,"7月_tax":0,"8月":465429,"8月_tax":23272,"9月":0,"9月_tax":0,"10月":7274064,"10月_tax":363703,"11月":668629,"11月_tax":33432,"12月":0,"12月_tax":0},{"id":"A15134","name":"聯端","1月":0,"1月_tax":0,"2月":144000,"2月_tax":5220,"3月":49800,"3月_tax":2490,"4月":65190,"4月_tax":3260,"5月":121200,"5月_tax":6060,"6月":76800,"6月_tax":3840,"7月":114600,"7月_tax":5730,"8月":54000,"8月_tax":2700,"9月":83400,"9月_tax":4168,"10月":86400,"10月_tax":4316,"11月":28200,"11月_tax":1410,"12月":5400,"12月_tax":270},{"id":"A15149","name":"恭赫","1月":99412,"1月_tax":4971,"2月":22000,"2月_tax":1100,"3月":113128,"3月_tax":5656,"4月":94320,"4月_tax":4716,"5月":51120,"5月_tax":2556,"6月":38740,"6月_tax":1937,"7月":58940,"7月_tax":2947,"8月":65240,"8月_tax":3262,"9月":48360,"9月_tax":2418,"10月":83648,"10月_tax":2178,"11月":71360,"11月_tax":2368,"12月":38880,"12月_tax":1944},{"id":"A15152","name":"益祥","1月":0,"1月_tax":0,"2月":6600,"2月_tax":0,"3月":14400,"3月_tax":0,"4月":7525,"4月_tax":0,"5月":48744,"5月_tax":0,"6月":6600,"6月_tax":0,"7月":24744,"7月_tax":0,"8月":16362,"8月_tax":0,"9月":6690,"9月_tax":0,"10月":50752,"10月_tax":0,"11月":0,"11月_tax":0,"12月":0,"12月_tax":0},{"id":"A15170","name":"上友","1月":27708,"1月_tax":0,"2月":6600,"2月_tax":0,"3月":5280,"3月_tax":0,"4月":12240,"4月_tax":0,"5月":12708,"5月_tax":0,"6月":6696,"6月_tax":0,"7月":3828,"7月_tax":0,"8月":18360,"8月_tax":0,"9月":13560,"9月_tax":0,"10月":2400,"10月_tax":0,"11月":78204,"11月_tax":0,"12月":28308,"12月_tax":0},{"id":"A15220","name":"東蒙","1月":17790,"1月_tax":890,"2月":18080,"2月_tax":904,"3月":67350,"3月_tax":3368,"4月":56630,"4月_tax":2832,"5月":67970,"5月_tax":3399,"6月":90110,"6月_tax":4506,"7月":152050,"7月_tax":7603,"8月":192718,"8月_tax":9636,"9月":104210,"9月_tax":5211,"10月":137750,"10月_tax":6888,"11月":97630,"11月_tax":4882,"12月":81626,"12月_tax":4081},{"id":"A15224","name":"宥展","1月":35760,"1月_tax":1788,"2月":0,"2月_tax":0,"3月":30120,"3月_tax":1506,"4月":18840,"4月_tax":942,"5月":60240,"5月_tax":3012,"6月":0,"6月_tax":0,"7月":11280,"7月_tax":564,"8月":0,"8月_tax":0,"9月":48960,"9月_tax":2448,"10月":65880,"10月_tax":3294,"11月":0,"11月_tax":0,"12月":0,"12月_tax":0},{"id":"A15231","name":"麗佩沛","1月":0,"1月_tax":0,"2月":0,"2月_tax":0,"3月":0,"3月_tax":0,"4月":1406294,"4月_tax":70206,"5月":558748,"5月_tax":27938,"6月":1083863,"6月_tax":54111,"7月":5727326,"7月_tax":241574,"8月":209476,"8月_tax":10536,"9月":0,"9月_tax":0,"10月":2949682,"10月_tax":147483,"11月":3440703,"11月_tax":168047,"12月":1340001,"12月_tax":0},{"id":"A15233","name":"薆米克","1月":52416,"1月_tax":2621,"2月":0,"2月_tax":0,"3月":0,"3月_tax":0,"4月":0,"4月_tax":0,"5月":0,"5月_tax":0,"6月":0,"6月_tax":0,"7月":0,"7月_tax":0,"8月":0,"8月_tax":0,"9月":0,"9月_tax":0,"10月":0,"10月_tax":0,"11月":14352,"11月_tax":718,"12月":29860,"12月_tax":1493}]
};

const MONTHS=['1月','2月','3月','4月','5月','6月','7月','8月','9月','10月','11月','12月'];
const TAX=['稅金','稅金.1','稅金.2','稅金.3','稅金.4','稅金.5','稅金.6','稅金.7','稅金.8','稅金.9','稅金.10','稅金.11'];
const KEY26='sylvia_ar_2026_v2';
let STATE26={customers:[],months:[]};
let VIEW='2026',CHARTS={};

function saveStorage(){try{localStorage.setItem(KEY26,JSON.stringify(STATE26));}catch(e){}}
function loadStorage(){try{const r=localStorage.getItem(KEY26);if(!r)return false;const d=JSON.parse(r);if(d&&d.customers&&d.months&&d.months.length){STATE26=d;return true;}}catch(e){}return false;}
function toast(msg){const t=document.getElementById('toast');t.textContent=msg;t.style.display='block';setTimeout(()=>t.style.display='none',3000);}

const dz=document.getElementById('dz');
dz.addEventListener('dragover',e=>{e.preventDefault();dz.classList.add('over');});
dz.addEventListener('dragleave',()=>dz.classList.remove('over'));
dz.addEventListener('drop',e=>{e.preventDefault();dz.classList.remove('over');handleFile(e.dataTransfer.files[0]);});

function handleFile(file){
  if(!file)return;
  if(typeof XLSX==='undefined'){alert('讀取模組載入中，請稍後再試');return;}
  const reader=new FileReader();
  reader.onload=e=>{try{const wb=XLSX.read(new Uint8Array(e.target.result),{type:'array'});const ws=wb.Sheets[wb.SheetNames[0]];const raw=XLSX.utils.sheet_to_json(ws,{defval:null});merge2026(raw,file.name);}catch(err){alert('讀取失敗：'+err.message);}};
  reader.readAsArrayBuffer(file);
}

function merge2026(rows,fileName){
  if(!rows.length)return;
  const keys=Object.keys(rows[0]);
  const newMons=MONTHS.filter(m=>keys.includes(m));
  const dRows=rows.filter(r=>r['客戶編號']&&r['客戶編號']!=='合計'&&r['客戶']);
  const activeMons=newMons.filter(m=>dRows.some(r=>parseFloat(r[m])>0));
  if(!activeMons.length){alert('此 Excel 無有效月份資料');return;}
  const map=new Map();
  STATE26.customers.forEach(c=>map.set(c.id,{...c}));
  dRows.forEach(r=>{
    const id=String(r['客戶編號']||''),name=String(r['客戶']||'');
    if(!id)return;
    if(!map.has(id))map.set(id,{id,name});
    const obj=map.get(id);
    newMons.forEach((m,i)=>{const v=parseFloat(r[m])||0,t=parseFloat(r[TAX[MONTHS.indexOf(m)]])||0;if(v>0){obj[m]=v;obj[m+'_tax']=t;}});
  });
  const allMons=[...new Set([...STATE26.months,...activeMons])];
  allMons.sort((a,b)=>MONTHS.indexOf(a)-MONTHS.indexOf(b));
  const allC=Array.from(map.values()).filter(c=>allMons.some(m=>c[m]>0));
  const added=activeMons.filter(m=>!STATE26.months.includes(m));
  const updated=activeMons.filter(m=>STATE26.months.includes(m));
  STATE26={customers:allC,months:allMons};
  saveStorage();updateSavedBar();
  document.getElementById('fileInfo').textContent='2026年：'+allMons.join('、');
  let msg='';if(added.length)msg+='✅ 新增 '+added.join('、')+' ';if(updated.length)msg+='🔄 更新 '+updated.join('、');if(msg)toast(msg.trim());
  renderAll();
  document.getElementById('uploadSection').style.display='none';
  document.getElementById('dashboard').style.display='block';
}

function updateSavedBar(){
  const bar=document.getElementById('savedBar');
  if(!STATE26.months.length){bar.style.display='none';return;}
  bar.style.display='flex';
  document.getElementById('mTags').innerHTML=STATE26.months.map(m=>`<span class="m-tag">${m}<span class="m-del" onclick="delMonth('${m}')">×</span></span>`).join('');
}
function delMonth(m){
  if(!confirm('確定刪除 2026年 '+m+' 的資料？'))return;
  STATE26.months=STATE26.months.filter(x=>x!==m);
  STATE26.customers=STATE26.customers.map(c=>{const nc={...c};delete nc[m];delete nc[m+'_tax'];return nc;}).filter(c=>STATE26.months.some(mo=>c[mo]>0));
  if(!STATE26.months.length){clearAll();return;}
  saveStorage();updateSavedBar();renderAll();toast('🗑 已刪除 2026/'+m);
}
function clearAll(){
  if(!confirm('確定清除所有 2026 年資料？'))return;
  localStorage.removeItem(KEY26);STATE26={customers:[],months:[]};
  document.getElementById('dashboard').style.display='none';
  document.getElementById('savedBar').style.display='none';
  document.getElementById('uploadSection').style.display='flex';
  document.getElementById('fileInfo').textContent='2026年：尚未載入';
  toast('✅ 已清除');
}
function setView(v){
  VIEW=v;
  ['26','25','24','YoY','MoM'].forEach(x=>{const b=document.getElementById('btn'+x);if(b)b.classList.toggle('on',(x==='26'&&v==='2026')||(x==='25'&&v==='2025')||(x==='24'&&v==='2024')||(x==='YoY'&&v==='yoy')||(x==='MoM'&&v==='mom'));});
  renderAll();
}

const C26=()=>STATE26.customers,M26=()=>STATE26.months,C25=()=>DATA[2025],C24=()=>DATA[2024];
function mT(cs,m){return cs.reduce((s,c)=>s+(c[m]||0),0);}
function find(cs,id){return cs.find(c=>c.id===id);}
function fmt(v){return v>0?'$'+Math.round(v).toLocaleString('zh-TW'):'—';}
function fmtK(v){return v>=1e6?'$'+(v/1e6).toFixed(1)+'M':v>=1000?'$'+Math.round(v/1000)+'K':'$'+Math.round(v);}
function fmtPct(a,b){if(!b||b===0)return null;return((a-b)/b*100).toFixed(1);}
function pctTag(pct){
  if(pct===null)return '<span style="color:#94A3B8;font-size:11px">N/A</span>';
  const up=parseFloat(pct)>=0;
  return `<span class="pill ${up?'p-up':'p-dn'}">${up?'▲':'▼'}${Math.abs(pct)}%</span>`;
}
function dc(k){if(CHARTS[k]){CHARTS[k].destroy();delete CHARTS[k];}}

const TC='#475569', GC='rgba(0,0,0,0.06)';

function renderAll(){renderKPIs();renderBarChart();renderLineChart();renderYoYBar();renderMoMBar();renderTableHead();renderTable();}

function renderKPIs(){
  const m26=M26(),c26=C26(),c25=C25(),c24=C24();let kpis=[];
  if(VIEW==='2026'){
    if(!m26.length)return;
    const L=m26[m26.length-1],P=m26.length>1?m26[m26.length-2]:null;
    const lT=mT(c26,L),pT=P?mT(c26,P):null,lTax=c26.reduce((s,c)=>s+(c[L+'_tax']||0),0),lCnt=c26.filter(c=>c[L]>0).length;
    const totAll=m26.reduce((s,m)=>s+mT(c26,m),0),y25=mT(c25,L),yoy=fmtPct(lT,y25),mom=pT!==null?fmtPct(lT,pT):null;
    kpis=[
      {lbl:`${L} 應收合計`,val:'$'+lT.toLocaleString('zh-TW'),sub:`稅金 ${lTax.toLocaleString('zh-TW')} · ${lCnt}家客戶`,c1:'#FFA07A',c2:'#FFB627',badge:yoy!==null?{v:yoy,l:'YoY'}:null},
      {lbl:'MoM 月增率',val:mom!==null?(parseFloat(mom)>=0?'+':'')+mom+'%':'—',sub:P?`${P} → ${L}`:'無上月資料',c1:parseFloat(mom)>=0?'#00C48C':'#FF4D6D',c2:'#FFA07A',badge:null},
      {lbl:'YoY 年增率',val:yoy!==null?(parseFloat(yoy)>=0?'+':'')+yoy+'%':'—',sub:`vs 2025/${L} ${fmt(y25)}`,c1:parseFloat(yoy)>=0?'#00C48C':'#FF4D6D',c2:'#7C5CFC',badge:null},
      {lbl:`${m26[0]}～${L} 累計`,val:'$'+totAll.toLocaleString('zh-TW'),sub:m26.length+'個月合計',c1:'#FFB627',c2:'#7C5CFC',badge:null},
      {lbl:'有資料客戶數',val:String(lCnt),sub:'共 '+c26.length+' 家',c1:'#7C5CFC',c2:'#38BDF8',badge:null}
    ];
  }else if(VIEW==='2025'){
    const t25=MONTHS.reduce((s,m)=>s+mT(c25,m),0),t24=MONTHS.reduce((s,m)=>s+mT(c24,m),0);
    const yoy=fmtPct(t25,t24),maxM=MONTHS.reduce((b,m)=>mT(c25,m)>mT(c25,b)?m:b,'1月');
    kpis=[
      {lbl:'2025全年合計',val:'$'+t25.toLocaleString('zh-TW'),sub:'vs 2024: '+(parseFloat(yoy)>=0?'+':'')+yoy+'%',c1:'#FFA07A',c2:'#FFB627',badge:{v:yoy,l:'YoY'}},
      {lbl:'2024全年合計',val:'$'+t24.toLocaleString('zh-TW'),sub:'比較基準年',c1:'#94A3B8',c2:'#CBD5E1',badge:null},
      {lbl:'最高月份',val:maxM,sub:'$'+mT(c25,maxM).toLocaleString('zh-TW'),c1:'#FFB627',c2:'#7C5CFC',badge:null},
      {lbl:'月平均',val:'$'+Math.round(t25/12).toLocaleString('zh-TW'),sub:'全年平均',c1:'#7C5CFC',c2:'#38BDF8',badge:null},
      {lbl:'有資料客戶',val:String(c25.filter(c=>MONTHS.some(m=>c[m]>0)).length),sub:'2025全年',c1:'#00C48C',c2:'#38BDF8',badge:null}
    ];
  }else if(VIEW==='2024'){
    const t24=MONTHS.reduce((s,m)=>s+mT(c24,m),0),maxM=MONTHS.reduce((b,m)=>mT(c24,m)>mT(c24,b)?m:b,'1月');
    kpis=[
      {lbl:'2024全年合計',val:'$'+t24.toLocaleString('zh-TW'),sub:'全年12個月',c1:'#94A3B8',c2:'#CBD5E1',badge:null},
      {lbl:'最高月份',val:maxM,sub:'$'+mT(c24,maxM).toLocaleString('zh-TW'),c1:'#FFB627',c2:'#7C5CFC',badge:null},
      {lbl:'月平均',val:'$'+Math.round(t24/12).toLocaleString('zh-TW'),sub:'全年平均',c1:'#7C5CFC',c2:'#38BDF8',badge:null},
      {lbl:'最低月份',val:MONTHS.reduce((b,m)=>mT(c24,m)<mT(c24,b)?m:b,'1月'),sub:'',c1:'#FFA07A',c2:'#00C48C',badge:null},
      {lbl:'有資料客戶',val:String(c24.filter(c=>MONTHS.some(m=>c[m]>0)).length),sub:'2024全年',c1:'#00C48C',c2:'#FFA07A',badge:null}
    ];
  }else if(VIEW==='yoy'){
    if(!m26.length)return;
    const sm=m26.filter(m=>MONTHS.includes(m));
    const t26=sm.reduce((s,m)=>s+mT(c26,m),0),t25=sm.reduce((s,m)=>s+mT(c25,m),0),t24=sm.reduce((s,m)=>s+mT(c24,m),0);
    const y2625=fmtPct(t26,t25),y2524=fmtPct(t25,t24);
    kpis=[
      {lbl:'2026 同期合計',val:'$'+t26.toLocaleString('zh-TW'),sub:sm.join('、'),c1:'#FFA07A',c2:'#FFB627',badge:{v:y2625,l:'vs 2025'}},
      {lbl:'2025 同期合計',val:'$'+t25.toLocaleString('zh-TW'),sub:sm.join('、'),c1:'#94A3B8',c2:'#CBD5E1',badge:{v:y2524,l:'vs 2024'}},
      {lbl:'2024 同期合計',val:'$'+t24.toLocaleString('zh-TW'),sub:sm.join('、'),c1:'#CBD5E1',c2:'#94A3B8',badge:null},
      {lbl:'YoY 2026 vs 2025',val:(parseFloat(y2625)>=0?'+':'')+y2625+'%',sub:sm.length+'個月同期比',c1:parseFloat(y2625)>=0?'#00C48C':'#FF4D6D',c2:'#FFA07A',badge:null},
      {lbl:'YoY 2025 vs 2024',val:(parseFloat(y2524)>=0?'+':'')+y2524+'%',sub:sm.length+'個月同期比',c1:parseFloat(y2524)>=0?'#00C48C':'#FF4D6D',c2:'#FFB627',badge:null}
    ];
  }else{
    if(!m26.length)return;
    const L=m26[m26.length-1],P=m26.length>1?m26[m26.length-2]:null;
    const lT=mT(c26,L),pT=P?mT(c26,P):null,mom=pT!==null?fmtPct(lT,pT):null;
    const y25L=mT(c25,L),y25P=P?mT(c25,P):null,momY25=y25P!==null?fmtPct(y25L,y25P):null;
    kpis=[
      {lbl:`${L} 本月`,val:'$'+lT.toLocaleString('zh-TW'),sub:'2026年當月',c1:'#FFA07A',c2:'#FFB627',badge:mom!==null?{v:mom,l:'MoM'}:null},
      {lbl:'MoM 月增率',val:mom!==null?(parseFloat(mom)>=0?'+':'')+mom+'%':'—',sub:P?`vs ${P}`:'無上月',c1:parseFloat(mom)>=0?'#00C48C':'#FF4D6D',c2:'#FFA07A',badge:null},
      {lbl:`${P||'—'} 上月`,val:pT!==null?'$'+pT.toLocaleString('zh-TW'):'—',sub:'2026年上月',c1:'#94A3B8',c2:'#CBD5E1',badge:null},
      {lbl:`2025/${L} 同月`,val:'$'+y25L.toLocaleString('zh-TW'),sub:`YoY: ${fmtPct(lT,y25L)!==null?(parseFloat(fmtPct(lT,y25L))>=0?'+':'')+fmtPct(lT,y25L)+'%':'N/A'}`,c1:'#FFB627',c2:'#7C5CFC',badge:null},
      {lbl:'MoM 2025 參考',val:momY25!==null?(parseFloat(momY25)>=0?'+':'')+momY25+'%':'—',sub:'2025同期月增率',c1:'#7C5CFC',c2:'#38BDF8',badge:null}
    ];
  }
  document.getElementById('kpiRow').innerHTML=kpis.map(k=>`
    <div class="kpi" style="--c1:${k.c1};--c2:${k.c2}">
      <div class="kpi-lbl">${k.lbl}</div>
      <div class="kpi-val">${k.val}</div>
      <div class="kpi-sub">${k.sub}</div>
      ${k.badge?`<div class="kpi-badge ${parseFloat(k.badge.v)>=0?'b-up':'b-dn'}">${k.badge.l} ${parseFloat(k.badge.v)>=0?'▲':'▼'}${Math.abs(k.badge.v)}%</div>`:''}
    </div>`).join('');
}

function renderBarChart(){
  if(typeof Chart==='undefined')return;
  const m26=M26(),c26=C26(),c25=C25(),c24=C24();let labels,datasets;
  if(VIEW==='2026'){
    if(!m26.length)return;
    const L=m26[m26.length-1],show=m26.slice(-3),top10=[...c26].sort((a,b)=>(b[L]||0)-(a[L]||0)).slice(0,10);
    labels=top10.map(c=>c.name);
    datasets=show.map((m,i)=>({label:m,data:top10.map(c=>c[m]||0),backgroundColor:PAL[i],borderRadius:6,borderSkipped:false}));
    document.getElementById('barTitle').textContent='前 10 大客戶（2026）';
    document.getElementById('barSub').textContent='依 '+L+' 排序';
    document.getElementById('barLeg').innerHTML=show.map((m,i)=>`<div class="leg"><div class="leg-dot" style="background:${PAL[i]}"></div>${m}</div>`).join('');
  }else if(VIEW==='2025'){
    const tot=c=>MONTHS.reduce((s,m)=>s+(c[m]||0),0),top10=[...c25].filter(c=>tot(c)>0).sort((a,b)=>tot(b)-tot(a)).slice(0,10);
    labels=top10.map(c=>c.name);datasets=[{label:'2025全年',data:top10.map(c=>tot(c)),backgroundColor:PAL[2],borderRadius:6,borderSkipped:false}];
    document.getElementById('barTitle').textContent='前 10 大客戶（2025全年）';document.getElementById('barSub').textContent='依全年合計排序';document.getElementById('barLeg').innerHTML='';
  }else if(VIEW==='2024'){
    const tot=c=>MONTHS.reduce((s,m)=>s+(c[m]||0),0),top10=[...c24].filter(c=>tot(c)>0).sort((a,b)=>tot(b)-tot(a)).slice(0,10);
    labels=top10.map(c=>c.name);datasets=[{label:'2024全年',data:top10.map(c=>tot(c)),backgroundColor:'#94A3B8',borderRadius:6,borderSkipped:false}];
    document.getElementById('barTitle').textContent='前 10 大客戶（2024全年）';document.getElementById('barSub').textContent='依全年合計排序';document.getElementById('barLeg').innerHTML='';
  }else if(VIEW==='yoy'){
    if(!m26.length)return;
    const sm=m26.filter(m=>MONTHS.includes(m));
    const g26=c=>sm.reduce((s,m)=>s+(c[m]||0),0),g25=id=>{const c=find(c25,id);return c?sm.reduce((s,m)=>s+(c[m]||0),0):0;},g24=id=>{const c=find(c24,id);return c?sm.reduce((s,m)=>s+(c[m]||0),0):0;};
    const top10=[...c26].sort((a,b)=>g26(b)-g26(a)).slice(0,10);
    labels=top10.map(c=>c.name);
    datasets=[{label:'2026',data:top10.map(c=>g26(c)),backgroundColor:PAL[0],borderRadius:6,borderSkipped:false},{label:'2025',data:top10.map(c=>g25(c.id)),backgroundColor:PAL[1],borderRadius:6,borderSkipped:false},{label:'2024',data:top10.map(c=>g24(c.id)),backgroundColor:'#CBD5E1',borderRadius:6,borderSkipped:false}];
    document.getElementById('barTitle').textContent='前 10 大客戶 YoY 同期比';document.getElementById('barSub').textContent=sm.join('、');
    document.getElementById('barLeg').innerHTML=`<div class="leg"><div class="leg-dot" style="background:${PAL[0]}"></div>2026</div><div class="leg"><div class="leg-dot" style="background:${PAL[1]}"></div>2025</div><div class="leg"><div class="leg-dot" style="background:#CBD5E1"></div>2024</div>`;
  }else{
    if(!m26.length)return;
    const L=m26[m26.length-1],P=m26.length>1?m26[m26.length-2]:null,top10=[...c26].sort((a,b)=>(b[L]||0)-(a[L]||0)).slice(0,10);
    labels=top10.map(c=>c.name);
    datasets=[{label:L,data:top10.map(c=>c[L]||0),backgroundColor:PAL[0],borderRadius:6,borderSkipped:false},...(P?[{label:P,data:top10.map(c=>c[P]||0),backgroundColor:PAL[1],borderRadius:6,borderSkipped:false}]:[])];
    document.getElementById('barTitle').textContent='前 10 大客戶 MoM';document.getElementById('barSub').textContent=(P?P+' vs ':'')+L;
    document.getElementById('barLeg').innerHTML=datasets.map((d,i)=>`<div class="leg"><div class="leg-dot" style="background:${PAL[i]}"></div>${d.label}</div>`).join('');
  }
  dc('bar');
  CHARTS.bar=new Chart(document.getElementById('barC'),{type:'bar',data:{labels,datasets},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false}},scales:{x:{ticks:{color:TC,font:{size:11},maxRotation:30},grid:{display:false},border:{display:false}},y:{ticks:{color:TC,font:{size:11,family:'DM Mono'},callback:v=>fmtK(v)},grid:{color:GC},border:{display:false}}}}});
}

function renderLineChart(){
  if(typeof Chart==='undefined')return;
  const m26=M26(),c26=C26(),c25=C25(),c24=C24();let lL,lD;
  const lo=(color,fill=false)=>({borderColor:color,backgroundColor:color+'18',fill,tension:0.4,pointRadius:5,pointBackgroundColor:color,pointBorderColor:'#fff',pointBorderWidth:2.5,borderWidth:2.5});
  if(VIEW==='2026'){if(!m26.length)return;lL=m26;lD=[{label:'2026',...lo(PAL[0],true),data:m26.map(m=>mT(c26,m))}];document.getElementById('lineSub').textContent='2026各月應收合計';document.getElementById('lineLeg').innerHTML='';}
  else if(VIEW==='2025'){lL=MONTHS;lD=[{label:'2025',...lo(PAL[2],true),data:MONTHS.map(m=>mT(c25,m))}];document.getElementById('lineSub').textContent='2025全年各月趨勢';document.getElementById('lineLeg').innerHTML='';}
  else if(VIEW==='2024'){lL=MONTHS;lD=[{label:'2024',...lo('#94A3B8',true),data:MONTHS.map(m=>mT(c24,m))}];document.getElementById('lineSub').textContent='2024全年各月趨勢';document.getElementById('lineLeg').innerHTML='';}
  else if(VIEW==='yoy'){
    if(!m26.length)return;
    const sm=m26.filter(m=>MONTHS.includes(m));lL=sm;
    lD=[{label:'2026',...lo(PAL[0]),data:sm.map(m=>mT(c26,m))},{label:'2025',...lo(PAL[1]),data:sm.map(m=>mT(c25,m))},{label:'2024',...lo('#94A3B8'),data:sm.map(m=>mT(c24,m))}];
    document.getElementById('lineSub').textContent='三年同期趨勢比較';
    document.getElementById('lineLeg').innerHTML=`<div class="leg"><div class="leg-dot" style="background:${PAL[0]}"></div>2026</div><div class="leg"><div class="leg-dot" style="background:${PAL[1]}"></div>2025</div><div class="leg"><div class="leg-dot" style="background:#94A3B8"></div>2024</div>`;
  }else{
    if(!m26.length)return;lL=m26;
    lD=[{label:'2026',...lo(PAL[0]),data:m26.map(m=>mT(c26,m))},{label:'2025同期',...lo(PAL[1]),data:m26.map(m=>mT(c25,m))}];
    document.getElementById('lineSub').textContent='MoM 月度走勢';
    document.getElementById('lineLeg').innerHTML=`<div class="leg"><div class="leg-dot" style="background:${PAL[0]}"></div>2026</div><div class="leg"><div class="leg-dot" style="background:${PAL[1]}"></div>2025</div>`;
  }
  dc('line');
  CHARTS.line=new Chart(document.getElementById('lineC'),{type:'line',data:{labels:lL,datasets:lD},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:lD.length>1,labels:{color:TC,font:{size:11},boxWidth:10}},tooltip:{callbacks:{label:ctx=>' $'+ctx.raw.toLocaleString('zh-TW')}}},scales:{x:{ticks:{color:TC,font:{size:12}},grid:{display:false},border:{display:false}},y:{ticks:{color:TC,font:{size:11,family:'DM Mono'},callback:v=>fmtK(v)},grid:{color:GC},border:{display:false}}}}});
}

function renderYoYBar(){
  if(typeof Chart==='undefined')return;
  const m26=M26(),c26=C26(),c25=C25();if(!m26.length){dc('yoyBar');return;}
  const sm=m26.filter(m=>MONTHS.includes(m));
  const yd=c26.map(c=>{const v26=sm.reduce((s,m)=>s+(c[m]||0),0),c25c=find(c25,c.id),v25=c25c?sm.reduce((s,m)=>s+(c25c[m]||0),0):0,pct=v25>0?((v26-v25)/v25*100):null;return{name:c.name,pct,v26};}).filter(d=>d.pct!==null).sort((a,b)=>b.v26-a.v26).slice(0,10);
  document.getElementById('yoyBarTitle').textContent='YoY 年增率（2026 vs 2025）';
  document.getElementById('yoyBarSub').textContent=sm.join('、')+' 同期';
  dc('yoyBar');
  CHARTS.yoyBar=new Chart(document.getElementById('yoyBarC'),{type:'bar',data:{labels:yd.map(d=>d.name),datasets:[{label:'YoY%',data:yd.map(d=>parseFloat(d.pct.toFixed(1))),backgroundColor:yd.map(d=>d.pct>=0?'#00C48C':'#FF4D6D'),borderRadius:6,borderSkipped:false}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false},tooltip:{callbacks:{label:ctx=>` ${ctx.raw>=0?'+':''}${ctx.raw}%`}}},scales:{x:{ticks:{color:TC,font:{size:10},maxRotation:30},grid:{display:false},border:{display:false}},y:{ticks:{color:TC,font:{size:10,family:'DM Mono'},callback:v=>v+'%'},grid:{color:GC},border:{display:false}}}}});
}

function renderMoMBar(){
  if(typeof Chart==='undefined')return;
  const m26=M26(),c26=C26();if(m26.length<2){dc('momBar');return;}
  const L=m26[m26.length-1],P=m26[m26.length-2];
  const md=c26.map(c=>{const vL=c[L]||0,vP=c[P]||0,pct=vP>0?((vL-vP)/vP*100):null;return{name:c.name,pct,vL};}).filter(d=>d.pct!==null).sort((a,b)=>b.vL-a.vL).slice(0,10);
  document.getElementById('momBarTitle').textContent=`MoM 月增率（${P} → ${L}）`;
  document.getElementById('momBarSub').textContent='2026年';
  dc('momBar');
  CHARTS.momBar=new Chart(document.getElementById('momBarC'),{type:'bar',data:{labels:md.map(d=>d.name),datasets:[{label:'MoM%',data:md.map(d=>parseFloat(d.pct.toFixed(1))),backgroundColor:md.map(d=>d.pct>=0?PAL[0]:'#FF4D6D'),borderRadius:6,borderSkipped:false}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false},tooltip:{callbacks:{label:ctx=>` ${ctx.raw>=0?'+':''}${ctx.raw}%`}}},scales:{x:{ticks:{color:TC,font:{size:10},maxRotation:30},grid:{display:false},border:{display:false}},y:{ticks:{color:TC,font:{size:10,family:'DM Mono'},callback:v=>v+'%'},grid:{color:GC},border:{display:false}}}}});
}

function renderTableHead(){
  const m26=M26();if(!m26.length)return;
  const L=m26[m26.length-1],P=m26.length>1?m26[m26.length-2]:null;
  document.getElementById('tHead').innerHTML=`<tr><th>編號</th><th>客戶</th>${P?`<th class="r">${P}</th>`:''}<th class="r">${L}</th><th class="r">稅金(${L})</th><th class="r">MoM</th><th class="r">YoY vs 2025</th><th class="r">YoY vs 2024</th><th class="r">累計</th><th>趨勢</th></tr>`;
}

function renderTable(){
  const m26=M26(),c26=C26(),c25=C25(),c24=C24();if(!m26.length)return;
  const L=m26[m26.length-1],P=m26.length>1?m26[m26.length-2]:null;
  const q=document.getElementById('srch').value.trim().toLowerCase(),sort=document.getElementById('tSort').value,filt=document.getElementById('tFilter').value;
  let data=c26.filter(c=>{if(q&&!c.name.toLowerCase().includes(q)&&!c.id.toLowerCase().includes(q))return false;if(filt==='active')return c[L]>0;if(filt==='new')return c[L]>0&&(!P||!c[P]);if(filt==='miss')return!c[L]&&m26.some(m=>m!==L&&c[m]>0);return true;});
  const total=c=>m26.reduce((s,m)=>s+(c[m]||0),0);
  const y25=c=>{const x=find(c25,c.id);return x?fmtPct(c[L]||0,x[L]||0):null;};
  const y24=c=>{const x=find(c24,c.id);return x?fmtPct(c[L]||0,x[L]||0):null;};
  const mom=c=>P?fmtPct(c[L]||0,c[P]||0):null;
  if(sort==='latest')data.sort((a,b)=>(b[L]||0)-(a[L]||0));
  else if(sort==='total')data.sort((a,b)=>total(b)-total(a));
  else if(sort==='yoy')data.sort((a,b)=>{const ya=parseFloat(y25(a))||0,yb=parseFloat(y25(b))||0;return yb-ya;});
  else data.sort((a,b)=>a.name.localeCompare(b.name,'zh-TW'));
  function badge(c){if(!P)return '';if(c[L]>0&&!c[P])return '<span class="pill p-new">新增</span>';if(!c[L]&&c[P]>0)return '<span class="pill p-na">本月無</span>';if(c[L]>0&&c[P]>0){const p=((c[L]-c[P])/c[P]*100).toFixed(0);return c[L]>=c[P]?`<span class="pill p-up">▲${p}%</span>`:`<span class="pill p-dn">▼${Math.abs(p)}%</span>`;}return '';}
  document.getElementById('tBody').innerHTML=data.map(c=>{const yy25=y25(c),yy24=y24(c),mo=mom(c);return`<tr><td class="dim">${c.id}</td><td style="font-weight:600">${c.name}</td>${P?`<td class="r" style="color:#94A3B8">${fmt(c[P]||0)}</td>`:''}<td class="r">${fmt(c[L]||0)}</td><td class="r dim">${fmt(c[L+'_tax']||0)}</td><td class="r">${pctTag(mo)}</td><td class="r">${pctTag(yy25)}</td><td class="r">${pctTag(yy24)}</td><td class="r" style="font-weight:700">${fmt(total(c))}</td><td>${badge(c)}</td></tr>`;}).join('');
  document.getElementById('tFoot').textContent=`顯示 ${data.length} 筆 · 共 ${c26.length} 筆`;
}

window.addEventListener('load',()=>{
  const ok=loadStorage();
  if(ok){document.getElementById('fileInfo').textContent='2026年：'+STATE26.months.join('、');updateSavedBar();renderAll();document.getElementById('uploadSection').style.display='none';document.getElementById('dashboard').style.display='block';}
});
</script>
</body>
</html>
