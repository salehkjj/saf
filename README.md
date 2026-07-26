<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>صَفّ — رتّب يومك</title>
<link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Crect x='20' y='18' width='45' height='14' rx='7' fill='%23FF6B00'/%3E%3Crect x='20' y='43' width='62' height='14' rx='7' fill='%23FF6B00'/%3E%3Cpath d='M20 68 h45 a7 7 0 0 1 7 7 v0 a7 7 0 0 1 -7 7 H34 Z' fill='%23FF6B00'/%3E%3Ccircle cx='73' cy='25' r='7' fill='%23FF6B00'/%3E%3C/svg%3E">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;800;900&display=swap" rel="stylesheet">
<style>
/* ============ TOKENS ============ */
:root{
  --bg: #0a0a0a;
  --s1: #131313;
  --s2: #191919;
  --s3: #212121;
  --border-subtle: rgba(255,255,255,0.055);
  --border: rgba(255,255,255,0.10);
  --border-strong: rgba(255,255,255,0.18);
  --orange: #FF6B00;
  --orange-hover: #FF7E1F;
  --orange-soft: rgba(255,107,0,0.10);
  --orange-soft-2: rgba(255,107,0,0.20);
  --orange-line: rgba(255,107,0,0.34);
  --text-1: #F5F5F5;
  --text-2: #9d9d9d;
  --text-3: #626262;
  --danger: #FF5252;
  --danger-soft: rgba(255,82,82,0.12);
  --r-sm: 10px;
  --r-md: 16px;
  --r-lg: 24px;
  --r-pill: 999px;
  --ease: cubic-bezier(.22,1,.36,1);
  --shadow-pop: 0 20px 50px -12px rgba(0,0,0,.6), 0 4px 16px -4px rgba(0,0,0,.4);
}

*{ margin:0; padding:0; box-sizing:border-box; }
html,body{ height:100%; }
body{
  background: var(--bg);
  color: var(--text-1);
  font-family: 'Tajawal', sans-serif;
  font-weight: 400;
  -webkit-font-smoothing: antialiased;
  overflow: hidden;
  font-size: 14.5px;
}
::selection{ background: var(--orange); color:#0a0a0a; }
::-webkit-scrollbar{ width:7px; height:7px; }
::-webkit-scrollbar-track{ background: transparent; }
::-webkit-scrollbar-thumb{ background: #2a2a2a; border-radius: 10px; }
::-webkit-scrollbar-thumb:hover{ background: var(--orange); }
button, input, textarea, select{ font-family: inherit; color: inherit; font-size: inherit; }
button{ cursor:pointer; border:none; background:none; }
input, textarea{ background:none; border:none; }
:focus-visible{ outline: 2px solid var(--orange); outline-offset: 2px; border-radius: 6px; }
h1,h2,h3,h4{ font-weight:800; line-height:1.25; }
p{ line-height:1.6; }
.hidden{ display:none !important; }

/* ============ Logo mark (reused everywhere) ============ */
.logo-mark{ position:relative; flex-shrink:0; }
.logo-mark span{ position:absolute; display:block; border-radius:5px; background: var(--orange); }
.logo-mark .b1{ top:6%; right:6%; width:56%; height:19%; }
.logo-mark .b2{ top:33%; right:6%; width:82%; height:19%; }
.logo-mark .b3{ top:60%; right:6%; width:70%; height:19%; border-radius: 5px 5px 5px 2px; }
.logo-mark .dot{ position:absolute; top:0; left:0; width:19%; height:19%; border-radius:50%; background: var(--orange); }

/* ============ Onboarding ============ */
.onboarding{
  position:fixed; inset:0; z-index:100;
  background: var(--bg);
  display:flex; align-items:center; justify-content:center;
  animation: fadeIn .4s var(--ease);
}
.onboarding.leaving{ animation: fadeOut .35s var(--ease) forwards; }
@keyframes fadeIn{ from{opacity:0} to{opacity:1} }
@keyframes fadeOut{ from{opacity:1} to{opacity:0; visibility:hidden;} }
.onb-glow{
  position:absolute; top:50%; right:50%; transform:translate(50%,-50%);
  width:640px; height:640px; border-radius:50%;
  background: radial-gradient(circle, rgba(255,107,0,0.10), transparent 70%);
  pointer-events:none;
}
.onb-card{ position:relative; max-width:460px; width:92%; text-align:center; padding: 20px; }
.onb-logo{ width:64px; height:64px; margin:0 auto 22px; animation: onbPop .6s var(--ease); }
@keyframes onbPop{ from{ transform:scale(.6); opacity:0; } to{ transform:scale(1); opacity:1; } }
.onb-word{ font-size:34px; font-weight:900; letter-spacing:.5px; }
.onb-tagline{ color:var(--text-2); font-size:15px; margin-top:8px; }
.onb-features{ display:flex; flex-direction:column; gap:14px; margin: 32px 0 30px; text-align:right; }
.onb-feature{ display:flex; align-items:center; gap:14px; background:var(--s1); border:1px solid var(--border-subtle); border-radius: var(--r-md); padding:14px 16px; }
.onb-feature .fi{ width:36px; height:36px; border-radius:11px; background:var(--orange-soft); display:flex; align-items:center; justify-content:center; flex-shrink:0; }
.onb-feature .fi svg{ width:18px; height:18px; stroke:var(--orange); }
.onb-feature b{ display:block; font-size:14px; font-weight:700; }
.onb-feature span{ font-size:12.5px; color:var(--text-2); }
.onb-cta{
  background: var(--orange); color:#0a0a0a; font-weight:800; font-size:15px;
  padding:15px 0; width:100%; border-radius: var(--r-md);
  transition: filter .2s ease, transform .15s var(--ease);
}
.onb-cta:hover{ filter:brightness(1.08); }
.onb-cta:active{ transform:scale(.98); }
.onb-note{ margin-top:16px; font-size:11.5px; color:var(--text-3); }

/* ============ App shell ============ */
.app{ height:100vh; display:flex; }

.sidebar{
  width:240px; flex-shrink:0;
  background: var(--s1);
  border-inline-start: 1px solid var(--border-subtle);
  display:flex; flex-direction:column;
  padding: 26px 16px 16px;
}
.brand{ display:flex; align-items:center; gap:11px; padding: 4px 8px 28px; }
.brand .logo-mark{ width:32px; height:32px; }
.brand-word{ font-weight:800; font-size:19px; }
.brand-word small{ display:block; font-weight:500; font-size:11px; color:var(--text-3); }

.nav{ position:relative; display:flex; flex-direction:column; gap:3px; }
.nav-indicator{
  position:absolute; right:0; left:0; height:42px;
  background: var(--orange-soft); border:1px solid var(--orange-line);
  border-radius: var(--r-sm); transition: transform .35s var(--ease); z-index:0;
}
.nav-item{
  position:relative; z-index:1; display:flex; align-items:center; gap:11px;
  height:42px; padding:0 13px; border-radius: var(--r-sm);
  color:var(--text-2); font-size:14px; font-weight:600; text-align:right;
  transition: color .2s ease;
}
.nav-item svg{ width:18px; height:18px; opacity:.85; flex-shrink:0; }
.nav-item.active{ color:var(--orange); }
.nav-item.active svg{ opacity:1; }
.nav-item:not(.active):hover{ color:var(--text-1); }

.sidebar-bottom{ margin-top:auto; display:flex; flex-direction:column; gap:10px; }
.today-ring-row{
  display:flex; align-items:center; gap:12px;
  background:var(--s2); border:1px solid var(--border-subtle);
  border-radius: var(--r-md); padding:12px 14px;
}
.ring{
  --pct: 0;
  width:36px; height:36px; border-radius:50%; flex-shrink:0;
  background: conic-gradient(var(--orange) calc(var(--pct)*1%), var(--s3) 0);
  display:flex; align-items:center; justify-content:center;
  transition: background 1s var(--ease);
}
.ring::after{ content:""; width:26px; height:26px; border-radius:50%; background:var(--s2); }
.today-ring-row .rlabel b{ display:block; font-size:12.5px; font-weight:700; }
.today-ring-row .rlabel span{ font-size:11px; color:var(--text-3); }
.settings-btn{
  display:flex; align-items:center; gap:10px; width:100%;
  padding:10px 12px; border-radius: var(--r-sm); color:var(--text-2); font-size:13px; font-weight:600;
  transition: background .2s ease, color .2s ease;
}
.settings-btn:hover{ background:var(--s2); color:var(--text-1); }
.settings-btn svg{ width:16px; height:16px; }

/* ============ Main ============ */
.main{ flex:1; overflow-y:auto; padding: 34px 44px 60px; }
.view{ display:none; }
.view.active{ display:block; animation: viewIn .4s var(--ease); }
@keyframes viewIn{ from{ opacity:0; transform:translateY(8px);} to{ opacity:1; transform:none; } }

.page-header{ display:flex; align-items:flex-end; justify-content:space-between; margin-bottom:28px; gap:16px; }
.eyebrow{ font-size:12px; color:var(--text-3); font-weight:700; letter-spacing:.3px; margin-bottom:6px; }
.page-header h1{ font-size:25px; }

.btn-add-global{
  display:flex; align-items:center; gap:8px; flex-shrink:0;
  background: var(--orange); color:#0a0a0a; font-weight:700; font-size:13.5px;
  padding: 11px 18px; border-radius: var(--r-pill);
  transition: filter .2s ease, transform .15s var(--ease);
}
.btn-add-global:hover{ filter:brightness(1.08); }
.btn-add-global:active{ transform:scale(.95); }
.btn-add-global svg{ width:15px; height:15px; }

/* ============ Quick-add popover ============ */
.popover-anchor{ position:relative; }
.qa-popover{
  position:absolute; top: calc(100% + 10px); left:0; width:320px; z-index:40;
  background:var(--s2); border:1px solid var(--border); border-radius: var(--r-md);
  box-shadow: var(--shadow-pop); padding:16px;
  animation: popIn .18s var(--ease);
}
@keyframes popIn{ from{ opacity:0; transform: translateY(-6px) scale(.98); } to{ opacity:1; transform:none; } }
.qa-popover input[type=text]{
  width:100%; background:var(--s3); border:1px solid var(--border); border-radius: var(--r-sm);
  padding: 12px 13px; font-size:14px; margin-bottom:12px;
}
.qa-popover input[type=text]:focus{ border-color: var(--orange-line); }
.qa-context{ font-size:11.5px; color:var(--orange); margin-bottom:10px; }
.qa-row-label{ font-size:11px; color:var(--text-3); font-weight:700; margin-bottom:7px; }
.priority-mini{ display:flex; gap:6px; margin-bottom:14px; }
.priority-mini button{
  flex:1; display:flex; align-items:center; justify-content:center; gap:6px;
  padding:7px 4px; border-radius:8px; border:1px solid var(--border); font-size:11.5px; color:var(--text-2);
  transition: border-color .2s ease, color .2s ease, background .2s ease;
}
.priority-mini button .pdot{ width:7px; height:7px; border-radius:50%; }
.priority-mini button.sel{ border-color: var(--orange-line); background:var(--orange-soft); color:var(--text-1); }
.qa-actions{ display:flex; gap:8px; }
.qa-actions .btn-primary{ flex:1; }

/* ============ Buttons (shared) ============ */
.btn-primary{
  background: var(--orange); color:#0a0a0a; font-weight:700; font-size:13.5px;
  padding:11px 18px; border-radius: var(--r-sm); transition: filter .2s ease, transform .15s var(--ease);
}
.btn-primary:hover{ filter:brightness(1.08); }
.btn-primary:active{ transform:scale(.96); }
.btn-ghost{
  color:var(--text-2); font-size:13.5px; padding:11px 16px; border-radius: var(--r-sm);
  transition: color .2s ease, background .2s ease;
}
.btn-ghost:hover{ color:var(--text-1); background: rgba(255,255,255,0.05); }
.btn-danger-confirm{
  color: var(--danger); font-size:13px; font-weight:700; padding:10px 16px; border-radius: var(--r-sm);
  background: var(--danger-soft); transition: background .2s ease;
}

/* ============ Dashboard ============ */
.greet-row{ display:flex; align-items:baseline; justify-content:space-between; margin-bottom:26px; }
.greet-row h1{ font-size:26px; }
.greet-row .date{ font-size:12.5px; color:var(--text-3); }

.focus-card{
  position:relative; overflow:hidden;
  background: linear-gradient(155deg, var(--s1), var(--s2));
  border:1px solid var(--border); border-radius: var(--r-lg);
  padding: 28px 30px; max-width:680px; margin-bottom:26px;
}
.focus-card .fc-glow{
  position:absolute; top:-90px; left:-90px; width:260px; height:260px; border-radius:50%;
  background: radial-gradient(circle, rgba(255,107,0,0.14), transparent 70%);
  animation: breathe 8s ease-in-out infinite; pointer-events:none;
}
@keyframes breathe{ 0%,100%{ transform:scale(1); opacity:.85;} 50%{ transform:scale(1.14); opacity:1;} }
.fc-eyebrow{ position:relative; font-size:11.5px; font-weight:700; color:var(--orange); letter-spacing:.3px; margin-bottom:10px; }
.fc-text{ position:relative; font-size:21px; font-weight:800; line-height:1.4; margin-bottom:14px; }
.fc-meta{ position:relative; display:flex; gap:8px; align-items:center; margin-bottom:20px; }
.fc-actions{ position:relative; display:flex; gap:10px; }
.fc-actions .btn-primary{ padding:12px 26px; }
.fc-empty{ position:relative; text-align:center; padding: 18px 0 6px; }
.fc-empty .fe-icon{ font-size:30px; margin-bottom:10px; }
.fc-empty p{ color:var(--text-2); font-size:14px; margin-bottom:16px; }

.stats-row{ display:grid; grid-template-columns: repeat(3,1fr); gap:12px; max-width:680px; margin-bottom:34px; }
.stat-card{
  background: var(--s1); border:1px solid var(--border-subtle); border-radius: var(--r-md);
  padding:16px 18px; display:flex; align-items:center; gap:12px;
}
.stat-card .si{ width:36px; height:36px; border-radius:10px; display:flex; align-items:center; justify-content:center; flex-shrink:0; }
.stat-card .si svg{ width:17px; height:17px; }
.stat-card.today .si{ background: var(--orange-soft); }
.stat-card.today .si svg{ stroke: var(--orange); }
.stat-card.progress .si{ background: rgba(255,255,255,0.06); }
.stat-card.progress .si svg{ stroke: var(--text-1); }
.stat-card.done .si{ background: rgba(255,255,255,0.06); }
.stat-card.done .si svg{ stroke: var(--text-1); }
.stat-card b{ display:block; font-size:20px; font-weight:800; }
.stat-card span{ font-size:11.5px; color:var(--text-2); }

.quick-actions{ display:flex; gap:10px; margin-bottom:38px; }
.qa-pill{
  display:flex; align-items:center; gap:8px;
  background:var(--s1); border:1px solid var(--border-subtle); border-radius: var(--r-pill);
  padding:10px 18px; font-size:13px; font-weight:600; color:var(--text-2);
  transition: border-color .2s ease, color .2s ease, background .2s ease;
}
.qa-pill:hover{ border-color: var(--orange-line); color:var(--text-1); background: var(--orange-soft); }
.qa-pill svg{ width:14px; height:14px; }

.section-head{ display:flex; align-items:center; justify-content:space-between; margin-bottom:16px; }
.section-head h2{ font-size:16.5px; font-weight:700; }

/* ============ Segmented tabs ============ */
.tabs{ position:relative; display:inline-grid; grid-auto-flow:column; background:var(--s1); border:1px solid var(--border-subtle); border-radius: var(--r-pill); padding:4px; gap:2px; }
.tab-indicator{ position:absolute; top:4px; bottom:4px; background:var(--orange); border-radius: var(--r-pill); transition: left .32s var(--ease), width .32s var(--ease); z-index:0; }
.tab{ position:relative; z-index:1; padding:8px 18px; font-size:13px; font-weight:600; border-radius: var(--r-pill); color:var(--text-2); transition: color .25s ease; }
.tab.active{ color:#0a0a0a; }

/* ============ Filter chips ============ */
.chip-row{ display:flex; gap:8px; margin-bottom:18px; flex-wrap:wrap; }
.chip{
  padding:7px 15px; border-radius: var(--r-pill); font-size:12.5px; font-weight:600;
  background:var(--s1); border:1px solid var(--border-subtle); color:var(--text-2);
  transition: all .2s ease; display:flex; align-items:center; gap:6px;
}
.chip .cdot{ width:7px; height:7px; border-radius:50%; }
.chip.active{ background: var(--orange-soft); border-color: var(--orange-line); color:var(--text-1); }
.chip:hover:not(.active){ border-color: var(--border-strong); color:var(--text-1); }

/* ============ Task list & card ============ */
.tasklist{ display:flex; flex-direction:column; gap:8px; max-width:680px; }
.task{
  position:relative;
  background: var(--s1); border:1px solid var(--border-subtle); border-radius: var(--r-md);
  transition: border-color .2s ease, background .2s ease, opacity .25s ease, transform .25s ease;
  animation: taskIn .3s var(--ease);
}
@keyframes taskIn{ from{ opacity:0; transform:translateY(6px);} to{ opacity:1; transform:none;} }
.task.dragging{ opacity:.35; }
.task.completing{ opacity:0; transform: scale(.96) translateY(4px); }
.task-row{ display:flex; align-items:center; gap:11px; padding:13px 14px; }
.task:hover{ border-color: var(--border); }

.drag-handle{ width:14px; height:20px; flex-shrink:0; opacity:0; cursor:grab; transition:opacity .2s ease; display:flex; align-items:center; justify-content:center; }
.task:hover .drag-handle{ opacity:.4; }
.drag-handle:hover{ opacity:.9 !important; }
.drag-handle svg{ width:12px; height:16px; stroke:var(--text-2); }

.check{
  width:21px; height:21px; border-radius:50%; border:2px solid var(--text-3); flex-shrink:0;
  display:flex; align-items:center; justify-content:center;
  transition: border-color .2s ease, background .2s ease, transform .15s var(--ease);
}
.check svg{ width:11px; height:11px; opacity:0; transform:scale(.5); transition: all .2s var(--ease); }
.task.done .check{ background: var(--orange); border-color: var(--orange); }
.task.done .check svg{ opacity:1; transform:scale(1); }
.check:active{ transform:scale(.85); }

.task-body{ flex:1; min-width:0; }
.task-text{ font-size:14px; font-weight:500; transition: color .2s ease; word-break: break-word; }
.task.done .task-text{ color: var(--text-3); text-decoration: line-through; }
.task-meta{ display:flex; gap:10px; align-items:center; margin-top:4px; flex-wrap:wrap; }
.meta-priority{ display:flex; align-items:center; gap:5px; font-size:11px; color:var(--text-3); }
.meta-priority .pdot{ width:6px; height:6px; border-radius:50%; }
.meta-project{ font-size:11px; color:var(--text-2); background: rgba(255,255,255,0.05); padding:2px 8px; border-radius:6px; }

.task-menu-wrap{ position:relative; flex-shrink:0; }
.menu-btn{ width:28px; height:28px; border-radius:8px; display:flex; align-items:center; justify-content:center; color:var(--text-3); transition: background .2s ease, color .2s ease; }
.menu-btn:hover{ background: rgba(255,255,255,0.06); color:var(--text-1); }
.menu-btn svg{ width:16px; height:16px; }
.task-menu{
  position:absolute; top: calc(100% + 4px); left:0; width:168px; z-index:20;
  background:var(--s3); border:1px solid var(--border); border-radius: var(--r-sm);
  box-shadow: var(--shadow-pop); padding:6px; animation: popIn .15s var(--ease);
}
.task-menu button{ display:flex; align-items:center; gap:9px; width:100%; padding:9px 10px; border-radius:7px; font-size:12.5px; font-weight:500; color:var(--text-1); transition: background .15s ease; text-align:right; }
.task-menu button:hover{ background: rgba(255,255,255,0.06); }
.task-menu button.danger{ color: var(--danger); }
.task-menu button svg{ width:14px; height:14px; }
.task-menu hr{ border:none; border-top:1px solid var(--border-subtle); margin:4px 2px; }

.task-edit{ max-height:0; overflow:hidden; transition: max-height .3s var(--ease); }
.task-edit-inner{ padding: 4px 14px 16px; border-top:1px solid var(--border-subtle); margin-top:2px; padding-top:14px; }
.task-edit input[type=text]{
  width:100%; background:var(--s2); border:1px solid var(--border); border-radius: var(--r-sm);
  padding:10px 12px; font-size:13.5px; margin-bottom:12px;
}
.edit-label{ font-size:11px; color:var(--text-3); font-weight:700; margin-bottom:7px; }
.edit-chip-row{ display:flex; gap:6px; flex-wrap:wrap; margin-bottom:4px; }
.edit-chip{ padding:6px 13px; border-radius: var(--r-pill); font-size:12px; font-weight:600; background:var(--s2); border:1px solid var(--border); color:var(--text-2); transition:all .2s ease; }
.edit-chip.sel{ background: var(--orange-soft); border-color: var(--orange-line); color:var(--text-1); }

.task.priority-high .meta-priority .pdot{ background: var(--orange); }
.task.priority-medium .meta-priority .pdot{ background:transparent; border:1.5px solid var(--orange); }
.task.priority-low .meta-priority .pdot{ background:transparent; border:1.5px solid var(--text-3); }

/* ============ Empty states ============ */
.empty{ text-align:center; padding: 50px 20px 40px; max-width:680px; }
.empty-illo{ width:84px; height:84px; margin:0 auto 18px; position:relative; opacity:.9; }
.empty-illo .ring-dash{ position:absolute; inset:0; border-radius:50%; border:1.5px dashed var(--border-strong); }
.empty-illo .logo-mark{ width:34px; height:34px; position:absolute; top:50%; left:50%; transform:translate(-50%,-50%); opacity:.55; }
.empty h3{ font-size:15px; font-weight:700; margin-bottom:6px; }
.empty p{ font-size:13px; color:var(--text-2); margin-bottom:18px; }

/* ============ Projects ============ */
.projects-grid{ display:grid; grid-template-columns: repeat(auto-fill, minmax(240px,1fr)); gap:14px; }
.project-card{
  background: var(--s1); border:1px solid var(--border-subtle); border-radius: var(--r-lg);
  padding:20px; cursor:pointer; transition: border-color .2s ease, transform .2s var(--ease); animation: taskIn .3s var(--ease);
  text-align:right;
}
.project-card:hover{ border-color: var(--orange-line); transform: translateY(-2px); }
.project-card .pc-top{ display:flex; align-items:center; justify-content:space-between; margin-bottom:16px; }
.project-dot{ width:11px; height:11px; border-radius:50%; }
.pc-pct{ font-size:12px; color:var(--text-2); font-weight:700; }
.project-card h3{ font-size:15.5px; margin-bottom:12px; }
.progress-bar{ height:6px; border-radius:4px; background: var(--s3); overflow:hidden; margin-bottom:10px; }
.progress-bar-fill{ height:100%; border-radius:4px; background: var(--orange); transition: width .5s var(--ease); }
.project-card .pc-count{ font-size:12px; color:var(--text-2); }

.add-card{
  display:flex; align-items:center; justify-content:center; gap:8px;
  border:1.5px dashed var(--border); border-radius: var(--r-lg); color:var(--text-2);
  font-size:13.5px; font-weight:600; min-height:118px; transition: border-color .2s ease, color .2s ease;
}
.add-card:hover{ border-color: var(--orange-line); color:var(--orange); }

.inline-form{
  background: var(--s1); border:1px solid var(--orange-line); border-radius: var(--r-lg);
  padding:20px; max-width:400px; margin-top:16px; animation: taskIn .3s var(--ease);
}
.inline-form input[type=text]{ width:100%; background:var(--s2); border:1px solid var(--border); border-radius: var(--r-sm); padding:11px 13px; font-size:14px; margin-bottom:14px; }
.swatches{ display:flex; gap:10px; margin-bottom:16px; }
.swatch{ width:23px; height:23px; border-radius:50%; border:2px solid transparent; transition: transform .15s ease, border-color .15s ease; }
.swatch.selected{ border-color: var(--text-1); transform:scale(1.12); }
.form-actions{ display:flex; gap:8px; }

/* Project detail */
.back-link{ display:flex; align-items:center; gap:6px; color:var(--text-2); font-size:13px; font-weight:600; margin-bottom:20px; transition: color .2s ease; }
.back-link:hover{ color:var(--orange); }
.back-link svg{ width:14px; height:14px; }
.pd-header{ display:flex; align-items:center; gap:18px; margin-bottom:30px; }
.pd-ring{ width:62px; height:62px; flex-shrink:0; }
.pd-ring::after{ width:46px; height:46px; }
.pd-ring-num{ position:relative; }
.pd-title-wrap h1{ font-size:22px; margin-bottom:4px; }
.pd-title-wrap span{ font-size:12.5px; color:var(--text-2); }
.pd-delete{ margin-inline-start:auto; color:var(--text-3); }
.pd-delete:hover{ color:var(--danger); }

/* ============ Notes ============ */
.notes-toolbar{ display:flex; gap:10px; margin-bottom:18px; }
.search-box{ position:relative; flex:1; max-width:280px; }
.search-box svg{ position:absolute; right:13px; top:50%; transform:translateY(-50%); width:15px; height:15px; stroke:var(--text-3); pointer-events:none; }
.search-box input{ width:100%; background:var(--s1); border:1px solid var(--border-subtle); border-radius: var(--r-pill); padding:10px 40px 10px 16px; font-size:13.5px; }
.search-box input:focus{ border-color: var(--orange-line); }

.notes-wrap{ display:flex; gap:18px; align-items:flex-start; }
.notes-grid{ display:grid; grid-template-columns: repeat(auto-fill, minmax(180px,1fr)); gap:12px; flex:1; }
.note-card{
  background: var(--s1); border:1px solid var(--border-subtle); border-radius: var(--r-md);
  padding:15px; cursor:pointer; transition: border-color .2s ease, transform .2s var(--ease);
  animation: taskIn .3s var(--ease); min-height:106px; display:flex; flex-direction:column; text-align:right;
}
.note-card:hover{ border-color: var(--orange-line); transform: translateY(-2px); }
.note-card.active{ border-color: var(--orange); background: var(--s2); }
.note-card h4{ font-size:14px; margin-bottom:6px; }
.note-card p{ font-size:12px; color:var(--text-2); line-height:1.6; overflow:hidden; display:-webkit-box; -webkit-line-clamp:3; -webkit-box-orient:vertical; flex:1; }
.note-card time{ font-size:10.5px; color:var(--text-3); margin-top:10px; }

.note-editor{
  flex:1.3; background: var(--s1); border:1px solid var(--border-subtle); border-radius: var(--r-lg);
  padding:22px; display:flex; flex-direction:column; min-height:400px; position:sticky; top:0;
}
.note-editor-head{ display:flex; align-items:center; justify-content:space-between; margin-bottom:10px; }
.note-editor input[type=text]{ font-size:18px; font-weight:800; flex:1; }
.focus-btn, .close-focus-btn{ display:flex; align-items:center; gap:6px; color:var(--text-2); font-size:12px; font-weight:600; padding:7px 12px; border-radius: var(--r-pill); transition: all .2s ease; flex-shrink:0; }
.focus-btn:hover{ color:var(--orange); background: var(--orange-soft); }
.focus-btn svg{ width:13px; height:13px; }
.note-editor textarea{ flex:1; resize:none; font-size:14px; line-height:1.9; }
.note-foot{ display:flex; justify-content:space-between; align-items:center; margin-top:12px; padding-top:12px; border-top:1px solid var(--border-subtle); }
.note-foot span{ font-size:11.5px; color:var(--text-3); }

body.focus-mode .sidebar, body.focus-mode .notes-grid, body.focus-mode .notes-toolbar, body.focus-mode .page-header{ display:none !important; }
body.focus-mode .main{ padding: 0; display:flex; align-items:center; justify-content:center; }
body.focus-mode .notes-wrap{ width:100%; height:100vh; }
body.focus-mode .note-editor{ max-width:680px; margin:0 auto; width:100%; height:82vh; border:none; background:transparent; }
body.focus-mode .close-focus-btn{ display:flex; }
.close-focus-btn{ display:none; }

/* ============ Modal ============ */
.modal-overlay{
  position:fixed; inset:0; z-index:80; background:rgba(0,0,0,0.55);
  display:flex; align-items:center; justify-content:center; animation: fadeIn .2s ease;
}
.modal{
  background: var(--s2); border:1px solid var(--border); border-radius: var(--r-lg);
  width:380px; max-width:92vw; padding:24px; box-shadow: var(--shadow-pop);
  animation: popIn .2s var(--ease);
}
.modal h3{ font-size:17px; margin-bottom:4px; }
.modal .modal-sub{ font-size:12.5px; color:var(--text-2); margin-bottom:20px; }
.modal-stats{ display:grid; grid-template-columns: repeat(3,1fr); gap:10px; margin-bottom:20px; }
.modal-stat{ background:var(--s1); border-radius: var(--r-sm); padding:12px; text-align:center; }
.modal-stat b{ display:block; font-size:18px; font-weight:800; }
.modal-stat span{ font-size:10.5px; color:var(--text-3); }
.modal-footer-note{ font-size:11.5px; color:var(--text-3); margin-bottom:18px; line-height:1.7; }
.modal-actions{ display:flex; gap:8px; }
.modal-close{ position:absolute; top:16px; left:16px; color:var(--text-3); }
.modal-close:hover{ color:var(--text-1); }

/* ============ Responsive ============ */
@media (max-width: 860px){
  .app{ flex-direction:column; }
  .sidebar{
    width:100%; flex-direction:row; align-items:center; order:2; padding:8px 10px;
    border-inline-start:none; border-top:1px solid var(--border-subtle);
    position:fixed; bottom:0; right:0; left:0; z-index:10;
  }
  .brand, .sidebar-bottom{ display:none; }
  .nav{ flex-direction:row; flex:1; justify-content:space-around; }
  .nav-indicator{ display:none; }
  .nav-item{ flex-direction:column; gap:3px; font-size:10.5px; height:auto; padding:6px 8px; }
  .main{ order:1; padding: 22px 18px 90px; }
  .stats-row{ grid-template-columns: repeat(3,1fr); }
  .quick-actions{ flex-wrap:wrap; }
  .notes-wrap{ flex-direction:column; }
  .note-editor{ position:static; width:100%; }
  .drag-handle{ display:none; }
  body.focus-mode .main{ padding: 20px; }
}
@media (hover: none) and (pointer: coarse){
  .drag-handle{ display:none !important; }
}
@media (prefers-reduced-motion: reduce){
  *{ animation-duration:.001s !important; transition-duration:.001s !important; }
}
</style>
</head>
<body>

<!-- ============ Onboarding ============ -->
<div class="onboarding" id="onboarding">
  <div class="onb-glow"></div>
  <div class="onb-card">
    <div class="onb-logo logo-mark"><span class="b1"></span><span class="b2"></span><span class="b3"></span><span class="dot"></span></div>
    <div class="onb-word">صَفّ</div>
    <p class="onb-tagline">رتّب يومك، ووصل للي يهمك.</p>

    <div class="onb-features">
      <div class="onb-feature">
        <div class="fi"><svg viewBox="0 0 24 24" fill="none" stroke-width="1.8" stroke-linecap="round"><path d="M4 6h16M4 12h16M4 18h10"/></svg></div>
        <div><b>تنظيم ووضوح</b><span>كل مهامك في مكان واحد، بدون تعقيد</span></div>
      </div>
      <div class="onb-feature">
        <div class="fi"><svg viewBox="0 0 24 24" fill="none" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M5 13l4 4L19 7"/></svg></div>
        <div><b>إنجاز وتركيز</b><span>بطاقة واحدة توريك أهم شي تسويه الحين</span></div>
      </div>
      <div class="onb-feature">
        <div class="fi"><svg viewBox="0 0 24 24" fill="none" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="4"/><path d="M12 2v2M12 20v2M4.9 4.9l1.4 1.4M17.7 17.7l1.4 1.4M2 12h2M20 12h2M4.9 19.1l1.4-1.4M17.7 6.3l1.4-1.4"/></svg></div>
        <div><b>بداية كل يوم</b><span>تبدأ من فاضي، وترتب يومك بثواني</span></div>
      </div>
    </div>

    <button class="onb-cta" id="onbStart">ابدأ الآن</button>
    <p class="onb-note">بدون تسجيل دخول — بياناتك تُحفظ على جهازك فقط</p>
  </div>
</div>

<div class="app">

  <!-- ============ Sidebar ============ -->
  <aside class="sidebar">
    <div class="brand">
      <div class="logo-mark"><span class="b1"></span><span class="b2"></span><span class="b3"></span><span class="dot"></span></div>
      <div class="brand-word">صَفّ<small>رتّب يومك</small></div>
    </div>

    <nav class="nav" id="nav">
      <div class="nav-indicator" id="navIndicator"></div>
      <button class="nav-item active" data-view="dashboard">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"><path d="M3 12l2-2 5 5L20 5l1 1"/></svg>
        الرئيسية
      </button>
      <button class="nav-item" data-view="tasks">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"><path d="M4 6h16M4 12h16M4 18h10"/></svg>
        المهام
      </button>
      <button class="nav-item" data-view="projects">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><rect x="3.5" y="3.5" width="7" height="7" rx="1.5"/><rect x="13.5" y="3.5" width="7" height="7" rx="1.5"/><rect x="3.5" y="13.5" width="7" height="7" rx="1.5"/><rect x="13.5" y="13.5" width="7" height="7" rx="1.5"/></svg>
        المشاريع
      </button>
      <button class="nav-item" data-view="notes">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M5 4h11l3 3v13H5z"/><path d="M9 9h6M9 13h6M9 17h3"/></svg>
        الملاحظات
      </button>
    </nav>

    <div class="sidebar-bottom">
      <div class="today-ring-row">
        <div class="ring" id="todayRing"></div>
        <div class="rlabel"><b id="todayRingPct">٠٪</b><span>إنجاز اليوم</span></div>
      </div>
      <button class="settings-btn" id="openSettings">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 00.33 1.82l.06.06a2 2 0 11-2.83 2.83l-.06-.06a1.65 1.65 0 00-1.82-.33 1.65 1.65 0 00-1 1.51V21a2 2 0 01-4 0v-.09A1.65 1.65 0 009 19.4a1.65 1.65 0 00-1.82.33l-.06.06a2 2 0 11-2.83-2.83l.06-.06A1.65 1.65 0 004.6 15a1.65 1.65 0 00-1.51-1H3a2 2 0 010-4h.09A1.65 1.65 0 004.6 9a1.65 1.65 0 00-.33-1.82l-.06-.06a2 2 0 112.83-2.83l.06.06A1.65 1.65 0 009 4.6a1.65 1.65 0 001-1.51V3a2 2 0 014 0v.09a1.65 1.65 0 001 1.51 1.65 1.65 0 001.82-.33l.06-.06a2 2 0 112.83 2.83l-.06.06A1.65 1.65 0 0019.4 9c.36.51.9.85 1.51 1H21a2 2 0 010 4h-.09a1.65 1.65 0 00-1.51 1z"/></svg>
        الإعدادات
      </button>
    </div>
  </aside>

  <!-- ============ Main ============ -->
  <main class="main">

    <!-- Dashboard -->
    <section class="view active" id="view-dashboard">
      <div class="greet-row">
        <div><span class="eyebrow" id="dateTag"></span><h1 id="greeting">وش وراك اليوم؟</h1></div>
        <div class="popover-anchor" id="dashAddAnchor">
          <button class="btn-add-global" data-qa-trigger>
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><path d="M12 5v14M5 12h14"/></svg>
            مهمة جديدة
          </button>
        </div>
      </div>

      <div class="focus-card" id="focusCard"></div>

      <div class="stats-row">
        <div class="stat-card today">
          <div class="si"><svg viewBox="0 0 24 24" fill="none" stroke-width="1.8" stroke-linecap="round"><circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 3"/></svg></div>
          <div><b id="statToday">0</b><span>مهام اليوم</span></div>
        </div>
        <div class="stat-card progress">
          <div class="si"><svg viewBox="0 0 24 24" fill="none" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="9"/><path d="M10 8.5l6 3.5-6 3.5z"/></svg></div>
          <div><b id="statProgress">0</b><span>قيد التنفيذ</span></div>
        </div>
        <div class="stat-card done">
          <div class="si"><svg viewBox="0 0 24 24" fill="none" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M5 13l4 4L19 7"/></svg></div>
          <div><b id="statDone">0</b><span>مكتملة</span></div>
        </div>
      </div>

      <div class="quick-actions">
        <button class="qa-pill" data-qa-trigger><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><path d="M12 5v14M5 12h14"/></svg>مهمة</button>
        <button class="qa-pill" id="qaProject"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3.5" y="3.5" width="7" height="7" rx="1.5"/><rect x="13.5" y="13.5" width="7" height="7" rx="1.5"/></svg>مشروع</button>
        <button class="qa-pill" id="qaNote"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 4h11l3 3v13H5z"/></svg>ملاحظة</button>
      </div>

      <div class="section-head">
        <h2>أولوياتك اليوم</h2>
        <div class="tabs" id="dashTabs" data-group="dash">
          <div class="tab-indicator"></div>
          <button class="tab active" data-status="today">اليوم</button>
          <button class="tab" data-status="progress">جاري</button>
          <button class="tab" data-status="done">منتهي</button>
        </div>
      </div>
      <div class="tasklist" id="dashTaskList"></div>
    </section>

    <!-- Tasks -->
    <section class="view" id="view-tasks">
      <div class="page-header">
        <div><span class="eyebrow">إدارة كاملة</span><h1>المهام</h1></div>
        <div class="popover-anchor" id="tasksAddAnchor">
          <button class="btn-add-global" data-qa-trigger>
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><path d="M12 5v14M5 12h14"/></svg>
            مهمة جديدة
          </button>
        </div>
      </div>
      <div class="chip-row" id="projectFilterChips"></div>
      <div class="section-head">
        <div></div>
        <div class="tabs" id="tasksTabs" data-group="tasks">
          <div class="tab-indicator"></div>
          <button class="tab active" data-status="today">اليوم</button>
          <button class="tab" data-status="progress">جاري</button>
          <button class="tab" data-status="done">منتهي</button>
        </div>
      </div>
      <div class="tasklist" id="tasksTaskList"></div>
    </section>

    <!-- Projects -->
    <section class="view" id="view-projects">
      <div id="projectsListSubview">
        <div class="page-header"><div><span class="eyebrow">تجميع الأهداف</span><h1>المشاريع</h1></div></div>
        <div class="projects-grid" id="projectsGrid"></div>
      </div>
      <div id="projectDetailSubview" class="hidden"></div>
    </section>

    <!-- Notes -->
    <section class="view" id="view-notes">
      <div class="page-header">
        <div><span class="eyebrow">كتابة حرة</span><h1>الملاحظات</h1></div>
        <button class="btn-add-global" id="newNoteBtn">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><path d="M12 5v14M5 12h14"/></svg>
          ملاحظة جديدة
        </button>
      </div>
      <div class="notes-toolbar">
        <div class="search-box">
          <svg viewBox="0 0 24 24" fill="none" stroke-width="2" stroke-linecap="round"><circle cx="11" cy="11" r="7"/><path d="M21 21l-4-4"/></svg>
          <input type="text" id="noteSearch" placeholder="ابحث في ملاحظاتك...">
        </div>
      </div>
      <div class="notes-wrap">
        <div class="notes-grid" id="notesGrid"></div>
        <div class="note-editor hidden" id="noteEditor">
          <div class="note-editor-head">
            <input type="text" id="noteTitleInput" placeholder="عنوان الملاحظة">
            <button class="focus-btn" id="focusModeBtn">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M8 3H5a2 2 0 00-2 2v3M16 3h3a2 2 0 012 2v3M8 21H5a2 2 0 01-2-2v-3M16 21h3a2 2 0 002-2v-3"/></svg>
              وضع التركيز
            </button>
            <button class="close-focus-btn" id="closeFocusBtn">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><path d="M18 6L6 18M6 6l12 12"/></svg>
              إغلاق
            </button>
          </div>
          <textarea id="noteContentInput" placeholder="اكتب أي شي يخطر على بالك..."></textarea>
          <div class="note-foot">
            <span id="noteSavedTag">محفوظة تلقائياً</span>
            <button class="btn-ghost" id="deleteNoteBtn" style="color:var(--danger);">حذف الملاحظة</button>
          </div>
        </div>
      </div>
    </section>

  </main>
</div>

<script>
(function(){
"use strict";

/* ================= State ================= */
const LS_KEY = "saf_app_state_v2";
const LS_KEY_OLD = "saf_app_state_v1";
const LS_ONBOARDED = "saf_onboarded";
const PROJECT_COLORS = ["#FF6B00", "#F5F5F5", "#8f8f8f", "#FF9E4D"];
const PRIORITY_ORDER = { high:0, medium:1, low:2 };
const PRIORITY_LABEL = { high:"عالية", medium:"متوسطة", low:"منخفضة" };

function uid(){ return Date.now().toString(36) + Math.random().toString(36).slice(2,7); }

function seedState(){
  const p1 = uid(), p2 = uid();
  return {
    projects: [
      { id:p1, name:"الشغل", color: PROJECT_COLORS[0] },
      { id:p2, name:"شخصي", color: PROJECT_COLORS[1] }
    ],
    tasks: [
      { id:uid(), text:"تصميم شاشة المشاريع", status:"today", projectId:p1, priority:"high" },
      { id:uid(), text:"مراجعة الفواتير الشهرية", status:"today", projectId:p2, priority:"medium" },
      { id:uid(), text:"تنسيق اجتماع الفريق", status:"progress", projectId:p1, priority:"medium" },
      { id:uid(), text:"تجربة صَفّ لأول مرة", status:"done", projectId:null, priority:"low" }
    ],
    notes: [
      { id:uid(), title:"أفكار سريعة", content:"اكتب أي شي يخطر على بالك هنا... صَفّ يحفظ كل شي تلقائياً على جهازك.", updatedAt: Date.now() }
    ]
  };
}

function migrateFromV1(){
  try{
    const raw = localStorage.getItem(LS_KEY_OLD);
    if(!raw) return null;
    const old = JSON.parse(raw);
    if(!old.tasks) return null;
    return {
      projects: old.projects || [],
      tasks: (old.tasks||[]).map(t=>({ ...t, priority: t.priority || "medium" })),
      notes: old.notes || []
    };
  }catch(e){ return null; }
}

function loadState(){
  try{
    const raw = localStorage.getItem(LS_KEY);
    if(raw){
      const parsed = JSON.parse(raw);
      if(parsed.projects && parsed.tasks && parsed.notes) return parsed;
    }
    const migrated = migrateFromV1();
    if(migrated) return migrated;
    return seedState();
  }catch(e){ return seedState(); }
}

let state = loadState();
function save(){ localStorage.setItem(LS_KEY, JSON.stringify(state)); }

/* ================= Icons ================= */
const ICON_CHECK = '<svg viewBox="0 0 24 24" fill="none" stroke="#0a0a0a" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12l5 5 9-10"/></svg>';
const ICON_GRIP = '<svg viewBox="0 0 8 16" fill="currentColor"><circle cx="2" cy="2" r="1.3"/><circle cx="6" cy="2" r="1.3"/><circle cx="2" cy="8" r="1.3"/><circle cx="6" cy="8" r="1.3"/><circle cx="2" cy="14" r="1.3"/><circle cx="6" cy="14" r="1.3"/></svg>';
const ICON_MORE = '<svg viewBox="0 0 24 24" fill="currentColor"><circle cx="5" cy="12" r="1.8"/><circle cx="12" cy="12" r="1.8"/><circle cx="19" cy="12" r="1.8"/></svg>';
const ICON_PLAY = '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="9"/><path d="M10 8.5l6 3.5-6 3.5z" fill="currentColor" stroke="none"/></svg>';
const ICON_PAUSE = '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"><rect x="6" y="5" width="4" height="14" rx="1"/><rect x="14" y="5" width="4" height="14" rx="1"/></svg>';
const ICON_EDIT = '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M12 20h9"/><path d="M16.5 3.5a2.12 2.12 0 013 3L7 19l-4 1 1-4z"/></svg>';
const ICON_TRASH = '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M4 7h16M9 7V5a1 1 0 011-1h4a1 1 0 011 1v2m-9 0l1 12a1 1 0 001 1h6a1 1 0 001-1l1-12"/></svg>';
const ICON_BACK = '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 6l6 6-6 6"/></svg>';

const EMPTY_COPY = {
  today: { h:"يوم صافي", p:"ما عندك مهام اليوم. ابدأ بإضافة أول وحدة." },
  progress: { h:"ولا شي جاري", p:"المهام اللي تبدأها بتظهر هنا." },
  done: { h:"لسا ما خلصت شي", p:"أول ما تخلص مهمة بتنعرض هنا." }
};

function emptyIllo(){ return '<div class="empty-illo"><div class="ring-dash"></div><div class="logo-mark"><span class="b1"></span><span class="b2"></span><span class="b3"></span><span class="dot"></span></div></div>'; }

/* ================= Nav / views ================= */
const navEl = document.getElementById("nav");
const navIndicator = document.getElementById("navIndicator");
const navItems = [...navEl.querySelectorAll(".nav-item")];

function positionNavIndicator(btn){
  if(window.innerWidth <= 860) return;
  navIndicator.style.height = btn.offsetHeight + "px";
  navIndicator.style.transform = `translateY(${btn.offsetTop}px)`;
}
function switchView(viewName){
  navItems.forEach(b=>b.classList.toggle("active", b.dataset.view===viewName));
  const active = navItems.find(b=>b.classList.contains("active"));
  if(active) positionNavIndicator(active);
  document.querySelectorAll(".view").forEach(v=>v.classList.remove("active"));
  document.getElementById("view-"+viewName).classList.add("active");
  closeAllPopovers();
}
navItems.forEach(btn=> btn.addEventListener("click", ()=> switchView(btn.dataset.view)));
window.addEventListener("resize", ()=>{
  const active = navItems.find(b=>b.classList.contains("active"));
  if(active) positionNavIndicator(active);
});

/* ================= Segmented tabs (generic) ================= */
function setupTabs(container, onChange){
  const indicator = container.querySelector(".tab-indicator");
  const tabs = [...container.querySelectorAll(".tab")];
  function position(btn){
    indicator.style.width = btn.offsetWidth + "px";
    indicator.style.left = btn.offsetLeft + "px";
  }
  tabs.forEach(t=>{
    t.addEventListener("click", ()=>{
      tabs.forEach(x=>x.classList.remove("active"));
      t.classList.add("active");
      position(t);
      onChange(t.dataset.status);
    });
  });
  requestAnimationFrame(()=> position(tabs.find(t=>t.classList.contains("active"))));
  return { tabs, reposition:()=> position(tabs.find(t=>t.classList.contains("active"))) };
}
const dashTabsCtl = setupTabs(document.getElementById("dashTabs"), ()=> renderTasksFor("dash"));
const tasksTabsCtl = setupTabs(document.getElementById("tasksTabs"), ()=> renderTasksFor("tasks"));

let tasksProjectFilter = "all";

function currentActiveStatus(group){
  const container = document.getElementById(group==="dash" ? "dashTabs" : "tasksTabs");
  const active = container.querySelector(".tab.active");
  return active ? active.dataset.status : "today";
}

/* ================= Priority helpers ================= */
function priorityDot(p){ return `<span class="pdot"></span>`; }

/* ================= Task rendering ================= */
function projectById(id){ return state.projects.find(p=>p.id===id); }

function taskCard(t){
  const wrap = document.createElement("div");
  wrap.className = "task priority-"+t.priority + (t.status==="done"?" done":"") + (t.status==="progress"?" progress":"");
  wrap.dataset.id = t.id;
  wrap.draggable = true;
  const proj = projectById(t.projectId);

  wrap.innerHTML = `
    <div class="task-row">
      <div class="drag-handle" title="اسحب لإعادة الترتيب">${ICON_GRIP}</div>
      <button class="check" aria-label="تم">${ICON_CHECK}</button>
      <div class="task-body">
        <div class="task-text"></div>
        <div class="task-meta">
          <span class="meta-priority">${priorityDot(t.priority)}<span class="plabel"></span></span>
          ${proj ? `<span class="meta-project"></span>` : ``}
        </div>
      </div>
      <div class="task-menu-wrap">
        <button class="menu-btn">${ICON_MORE}</button>
      </div>
    </div>
    <div class="task-edit">
      <div class="task-edit-inner">
        <input type="text" class="edit-text" value="">
        <div class="edit-label">الأولوية</div>
        <div class="edit-chip-row edit-priority">
          <button class="edit-chip" data-p="high">عالية</button>
          <button class="edit-chip" data-p="medium">متوسطة</button>
          <button class="edit-chip" data-p="low">منخفضة</button>
        </div>
        <div class="edit-label" style="margin-top:12px;">المشروع</div>
        <div class="edit-chip-row edit-project">
          <button class="edit-chip" data-proj="">بدون</button>
        </div>
      </div>
    </div>
  `;
  wrap.querySelector(".task-text").textContent = t.text;
  wrap.querySelector(".plabel").textContent = PRIORITY_LABEL[t.priority];
  if(proj) wrap.querySelector(".meta-project").textContent = proj.name;
  wrap.querySelector(".edit-text").value = t.text;

  // checkbox
  wrap.querySelector(".check").addEventListener("click", ()=>{
    if(t.status === "done"){ t.status = "today"; save(); renderAll(); return; }
    wrap.classList.add("completing");
    setTimeout(()=>{ t.status = "done"; save(); renderAll(); }, 260);
  });

  // menu
  const menuWrap = wrap.querySelector(".task-menu-wrap");
  const menuBtn = wrap.querySelector(".menu-btn");
  menuBtn.addEventListener("click", (e)=>{
    e.stopPropagation();
    const isOpen = !!menuWrap.querySelector(".task-menu");
    closeAllTaskMenus();
    if(isOpen) return;
    const menu = document.createElement("div");
    menu.className = "task-menu";
    menu.innerHTML = `
      <button class="toggle-progress">${t.status==="progress" ? ICON_PAUSE : ICON_PLAY}<span>${t.status==="progress" ? "إيقاف التنفيذ" : "بدء التنفيذ"}</span></button>
      <button class="toggle-edit">${ICON_EDIT}<span>تعديل</span></button>
      <hr>
      <button class="danger do-delete">${ICON_TRASH}<span>حذف</span></button>
    `;
    menuWrap.appendChild(menu);
    menu.querySelector(".toggle-progress").addEventListener("click", ()=>{
      t.status = (t.status === "progress") ? "today" : "progress";
      save(); renderAll();
    });
    menu.querySelector(".toggle-edit").addEventListener("click", ()=>{
      closeAllTaskMenus();
      toggleEditPanel(wrap, t);
    });
    menu.querySelector(".do-delete").addEventListener("click", ()=>{
      state.tasks = state.tasks.filter(x=>x.id!==t.id);
      save(); renderAll();
    });
  });

  // edit panel wiring
  const editText = wrap.querySelector(".edit-text");
  let editSaveTimer;
  editText.addEventListener("input", ()=>{
    clearTimeout(editSaveTimer);
    editSaveTimer = setTimeout(()=>{
      t.text = editText.value.trim() || t.text;
      wrap.querySelector(".task-text").textContent = t.text;
      save();
    }, 350);
  });
  wrap.querySelectorAll(".edit-priority .edit-chip").forEach(chip=>{
    if(chip.dataset.p === t.priority) chip.classList.add("sel");
    chip.addEventListener("click", ()=>{
      t.priority = chip.dataset.p;
      wrap.querySelectorAll(".edit-priority .edit-chip").forEach(c=>c.classList.toggle("sel", c===chip));
      wrap.className = "task priority-"+t.priority + (t.status==="done"?" done":"") + (t.status==="progress"?" progress":"");
      wrap.querySelector(".plabel").textContent = PRIORITY_LABEL[t.priority];
      save();
    });
  });
  const projRow = wrap.querySelector(".edit-project");
  state.projects.forEach(p=>{
    const b = document.createElement("button");
    b.className = "edit-chip" + (t.projectId===p.id ? " sel":"");
    b.dataset.proj = p.id;
    b.textContent = p.name;
    projRow.appendChild(b);
  });
  if(!t.projectId) projRow.querySelector('[data-proj=""]').classList.add("sel");
  projRow.querySelectorAll(".edit-chip").forEach(chip=>{
    chip.addEventListener("click", ()=>{
      t.projectId = chip.dataset.proj || null;
      projRow.querySelectorAll(".edit-chip").forEach(c=>c.classList.toggle("sel", c===chip));
      save();
      renderAll();
    });
  });

  // drag events
  wrap.addEventListener("dragstart", ()=>{ wrap.classList.add("dragging"); });
  wrap.addEventListener("dragend", ()=>{
    wrap.classList.remove("dragging");
    const container = wrap.parentElement;
    if(!container || !container._currentItems) return;
    const ids = [...container.querySelectorAll(".task")].map(el=>el.dataset.id);
    reorderTasks(container._currentItems, ids);
    save();
  });

  return wrap;
}

function toggleEditPanel(wrap, t){
  const panel = wrap.querySelector(".task-edit");
  const isOpen = panel.style.maxHeight && panel.style.maxHeight !== "0px";
  if(isOpen){ panel.style.maxHeight = "0px"; }
  else{ panel.style.maxHeight = panel.scrollHeight + "px"; }
}

function closeAllTaskMenus(){ document.querySelectorAll(".task-menu").forEach(m=>m.remove()); }

function reorderTasks(renderedTasks, newOrderIds){
  const idsSet = new Set(renderedTasks.map(t=>t.id));
  const others = state.tasks.filter(t=>!idsSet.has(t.id));
  const map = new Map(renderedTasks.map(t=>[t.id,t]));
  const reordered = newOrderIds.map(id=>map.get(id)).filter(Boolean);
  state.tasks = [...others, ...reordered];
}

function attachDragoverOnce(container){
  if(container._dragoverAttached) return;
  container._dragoverAttached = true;
  container.addEventListener("dragover", e=>{
    e.preventDefault();
    const dragging = container.querySelector(".dragging");
    if(!dragging) return;
    const siblings = [...container.querySelectorAll(".task:not(.dragging)")];
    let after = null, closestOffset = -Infinity;
    for(const child of siblings){
      const box = child.getBoundingClientRect();
      const offset = e.clientY - box.top - box.height/2;
      if(offset < 0 && offset > closestOffset){ closestOffset = offset; after = child; }
    }
    if(after == null) container.appendChild(dragging);
    else container.insertBefore(dragging, after);
  });
}

function renderTasksFor(group){
  const status = currentActiveStatus(group);
  const listEl = document.getElementById(group==="dash" ? "dashTaskList" : "tasksTaskList");
  attachDragoverOnce(listEl);
  closeAllTaskMenus();
  let items = state.tasks.filter(t=>t.status===status);
  if(group==="tasks" && tasksProjectFilter !== "all"){
    items = items.filter(t => tasksProjectFilter==="none" ? !t.projectId : t.projectId===tasksProjectFilter);
  }
  listEl._currentItems = items;
  listEl.innerHTML = "";
  if(items.length===0){
    const info = EMPTY_COPY[status];
    const e = document.createElement("div");
    e.className = "empty";
    e.innerHTML = emptyIllo() + `<h3>${info.h}</h3><p>${info.p}</p>`;
    listEl.appendChild(e);
    return;
  }
  items.forEach(t=> listEl.appendChild(taskCard(t)));
}

function renderStats(){
  const today = state.tasks.filter(t=>t.status==="today").length;
  const progress = state.tasks.filter(t=>t.status==="progress").length;
  const done = state.tasks.filter(t=>t.status==="done").length;
  document.getElementById("statToday").textContent = today;
  document.getElementById("statProgress").textContent = progress;
  document.getElementById("statDone").textContent = done;

  const total = today + progress + done;
  const pct = total===0 ? 0 : Math.round((done/total)*100);
  document.getElementById("todayRing").style.setProperty("--pct", pct);
  document.getElementById("todayRingPct").textContent = toArabicDigits(pct) + "٪";
}

function toArabicDigits(n){
  const map = {0:"٠",1:"١",2:"٢",3:"٣",4:"٤",5:"٥",6:"٦",7:"٧",8:"٨",9:"٩"};
  return String(n).split("").map(ch=> map[ch] !== undefined ? map[ch] : ch).join("");
}

/* ================= Focus card ================= */
function renderFocusCard(){
  const el = document.getElementById("focusCard");
  const candidates = state.tasks
    .filter(t=>t.status==="today")
    .slice()
    .sort((a,b)=> PRIORITY_ORDER[a.priority]-PRIORITY_ORDER[b.priority]);
  el.innerHTML = '<div class="fc-glow"></div>';
  if(candidates.length===0){
    el.innerHTML += `
      <div class="fc-empty">
        <div class="fe-icon">✨</div>
        <p>خلصت كل مهامك اليوم. وقت ترتاح أو تضيف شي جديد.</p>
        <button class="btn-primary" id="fcAddBtn">أضف مهمة</button>
      </div>`;
    document.getElementById("fcAddBtn").addEventListener("click", ()=> openQuickAdd(document.getElementById("dashAddAnchor"), null));
    return;
  }
  const t = candidates[0];
  const proj = projectById(t.projectId);
  el.innerHTML += `
    <div class="fc-eyebrow">التركيز الآن</div>
    <div class="fc-text"></div>
    <div class="fc-meta">
      <span class="meta-priority">${priorityDot(t.priority)}<span class="plabel"></span></span>
      ${proj ? `<span class="meta-project"></span>` : ``}
    </div>
    <div class="fc-actions">
      <button class="btn-primary" id="fcComplete">تم ✓</button>
      <button class="btn-ghost" id="fcOpenAll">فتح كل المهام</button>
    </div>
  `;
  el.querySelector(".fc-text").textContent = t.text;
  el.querySelector(".plabel").textContent = PRIORITY_LABEL[t.priority];
  const wrap = el.querySelector(".priority-high, .meta-priority");
  el.querySelector(".meta-priority .pdot").className = "pdot";
  el.querySelector(".meta-priority .pdot").style.cssText =
    t.priority==="high" ? "background:var(--orange)" :
    t.priority==="medium" ? "background:transparent;border:1.5px solid var(--orange)" :
    "background:transparent;border:1.5px solid var(--text-3)";
  if(proj) el.querySelector(".meta-project").textContent = proj.name;

  el.querySelector("#fcComplete").addEventListener("click", ()=>{
    t.status = "done"; save(); renderAll();
  });
  el.querySelector("#fcOpenAll").addEventListener("click", ()=> switchView("tasks"));
}

/* ================= Quick add popover ================= */
let qaContext = { projectId: null };
function closeAllPopovers(){
  document.querySelectorAll(".qa-popover").forEach(p=>p.remove());
  closeAllTaskMenus();
}
document.addEventListener("click", (e)=>{
  if(!e.target.closest(".task-menu-wrap")) closeAllTaskMenus();
  if(!e.target.closest(".popover-anchor")) closeAllPopovers();
});

function openQuickAdd(anchorEl, projectId){
  const already = anchorEl.querySelector(".qa-popover");
  closeAllPopovers();
  if(already) return;
  qaContext.projectId = projectId;
  const proj = projectId ? projectById(projectId) : null;
  const pop = document.createElement("div");
  pop.className = "qa-popover";
  pop.innerHTML = `
    ${proj ? `<div class="qa-context">سيُضاف إلى: ${proj.name}</div>` : ``}
    <input type="text" class="qa-input" placeholder="أضف مهمة جديدة..." autocomplete="off">
    <div class="qa-row-label">الأولوية</div>
    <div class="priority-mini">
      <button data-p="high"><span class="pdot" style="background:var(--orange)"></span>عالية</button>
      <button data-p="medium" class="sel"><span class="pdot" style="border:1.5px solid var(--orange)"></span>متوسطة</button>
      <button data-p="low"><span class="pdot" style="border:1.5px solid var(--text-3)"></span>منخفضة</button>
    </div>
    <div class="qa-actions">
      <button class="btn-primary qa-submit">إضافة</button>
      <button class="btn-ghost qa-cancel">إلغاء</button>
    </div>
  `;
  anchorEl.appendChild(pop);
  const input = pop.querySelector(".qa-input");
  input.focus();
  let selPriority = "medium";
  pop.querySelectorAll(".priority-mini button").forEach(b=>{
    b.addEventListener("click", ()=>{
      selPriority = b.dataset.p;
      pop.querySelectorAll(".priority-mini button").forEach(x=>x.classList.toggle("sel", x===b));
    });
  });
  function submit(){
    const text = input.value.trim();
    if(!text) return;
    state.tasks.push({ id:uid(), text, status:"today", projectId: qaContext.projectId, priority: selPriority });
    save();
    closeAllPopovers();
    renderAll();
  }
  pop.querySelector(".qa-submit").addEventListener("click", submit);
  input.addEventListener("keydown", e=>{ if(e.key==="Enter") submit(); if(e.key==="Escape") closeAllPopovers(); });
  pop.querySelector(".qa-cancel").addEventListener("click", closeAllPopovers);
}

document.querySelectorAll("[data-qa-trigger]").forEach(btn=>{
  btn.addEventListener("click", (e)=>{
    e.stopPropagation();
    const anchor = btn.closest(".popover-anchor");
    openQuickAdd(anchor, null);
  });
});

/* ================= Projects ================= */
const projectsGrid = document.getElementById("projectsGrid");
const projectsListSubview = document.getElementById("projectsListSubview");
const projectDetailSubview = document.getElementById("projectDetailSubview");
let activeProjectId = null;

function projectStats(pid){
  const items = state.tasks.filter(t=>t.projectId===pid);
  const done = items.filter(t=>t.status==="done").length;
  const total = items.length;
  const pct = total===0 ? 0 : Math.round((done/total)*100);
  return { done, total, pct };
}

function renderProjects(){
  projectsGrid.innerHTML = "";
  if(state.projects.length===0){
    const e = document.createElement("div");
    e.className = "empty";
    e.innerHTML = emptyIllo() + `<h3>لا مشاريع بعد</h3><p>أنشئ أول مشروع لك عشان تجمع مهامك حول هدف واحد.</p>`;
    projectsGrid.appendChild(e);
  }
  state.projects.forEach(p=>{
    const s = projectStats(p.id);
    const card = document.createElement("div");
    card.className = "project-card";
    card.innerHTML = `
      <div class="pc-top"><div class="project-dot" style="background:${p.color}"></div><span class="pc-pct"></span></div>
      <h3></h3>
      <div class="progress-bar"><div class="progress-bar-fill"></div></div>
      <div class="pc-count"></div>
    `;
    card.querySelector("h3").textContent = p.name;
    card.querySelector(".pc-pct").textContent = toArabicDigits(s.pct) + "٪";
    card.querySelector(".progress-bar-fill").style.width = s.pct + "%";
    card.querySelector(".pc-count").textContent = s.total===0 ? "لا مهام بعد" : `${toArabicDigits(s.done)} من ${toArabicDigits(s.total)} مهمة مكتملة`;
    card.addEventListener("click", ()=> openProjectDetail(p.id));
    projectsGrid.appendChild(card);
  });

  const addCard = document.createElement("div");
  addCard.className = "add-card";
  addCard.innerHTML = `<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><path d="M12 5v14M5 12h14"/></svg>مشروع جديد`;
  addCard.addEventListener("click", showProjectForm);
  projectsGrid.appendChild(addCard);
}

function showProjectForm(){
  if(document.getElementById("projectInlineForm")) return;
  const form = document.createElement("div");
  form.className = "inline-form";
  form.id = "projectInlineForm";
  form.innerHTML = `
    <input type="text" id="projNameInput" placeholder="اسم المشروع">
    <div class="swatches">${PROJECT_COLORS.map((c,i)=>`<div class="swatch ${i===0?'selected':''}" data-color="${c}" style="background:${c}"></div>`).join("")}</div>
    <div class="form-actions"><button class="btn-primary" id="saveProjBtn">إنشاء</button><button class="btn-ghost" id="cancelProjBtn">إلغاء</button></div>
  `;
  projectsGrid.after(form);
  let selectedColor = PROJECT_COLORS[0];
  form.querySelectorAll(".swatch").forEach(sw=>{
    sw.addEventListener("click", ()=>{
      form.querySelectorAll(".swatch").forEach(s=>s.classList.remove("selected"));
      sw.classList.add("selected"); selectedColor = sw.dataset.color;
    });
  });
  const nameInput = form.querySelector("#projNameInput");
  nameInput.focus();
  nameInput.addEventListener("keydown", e=>{ if(e.key==="Enter") saveProj(); });
  function saveProj(){
    const name = nameInput.value.trim();
    if(!name) return;
    state.projects.push({ id:uid(), name, color:selectedColor });
    save(); form.remove(); renderProjects(); renderProjectFilterChips();
  }
  form.querySelector("#saveProjBtn").addEventListener("click", saveProj);
  form.querySelector("#cancelProjBtn").addEventListener("click", ()=> form.remove());
}

function openProjectDetail(pid){
  activeProjectId = pid;
  projectsListSubview.classList.add("hidden");
  projectDetailSubview.classList.remove("hidden");
  renderProjectDetail();
}

function renderProjectDetail(){
  const p = projectById(activeProjectId);
  if(!p){ projectsListSubview.classList.remove("hidden"); projectDetailSubview.classList.add("hidden"); return; }
  const s = projectStats(activeProjectId);
  projectDetailSubview.innerHTML = `
    <button class="back-link" id="pdBack">${ICON_BACK}رجوع للمشاريع</button>
    <div class="pd-header">
      <div class="ring pd-ring" style="--pct:${s.pct}"></div>
      <div class="pd-title-wrap"><h1></h1><span></span></div>
      <button class="pd-delete" title="حذف المشروع">${ICON_TRASH}</button>
    </div>
    <div class="chip-row"><div class="popover-anchor" id="pdAddAnchor"><button class="btn-add-global" style="padding:9px 16px;font-size:12.5px;"><svg viewBox="0 0 24 24" width="13" height="13" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><path d="M12 5v14M5 12h14"/></svg>مهمة لهذا المشروع</button></div></div>
    <div class="section-head">
      <div></div>
      <div class="tabs" id="pdTabs" data-group="pd">
        <div class="tab-indicator"></div>
        <button class="tab active" data-status="today">اليوم</button>
        <button class="tab" data-status="progress">جاري</button>
        <button class="tab" data-status="done">منتهي</button>
      </div>
    </div>
    <div class="tasklist" id="pdTaskList"></div>
  `;
  projectDetailSubview.querySelector("h1").textContent = p.name;
  projectDetailSubview.querySelector(".pd-title-wrap span").textContent =
    s.total===0 ? "لا مهام بعد" : `${toArabicDigits(s.done)} من ${toArabicDigits(s.total)} مهمة مكتملة`;

  projectDetailSubview.querySelector("#pdBack").addEventListener("click", ()=>{
    activeProjectId = null;
    projectsListSubview.classList.remove("hidden");
    projectDetailSubview.classList.add("hidden");
    renderProjects();
  });
  projectDetailSubview.querySelector(".pd-delete").addEventListener("click", ()=>{
    if(!confirm(`حذف مشروع "${p.name}"؟ المهام المرتبطة فيه بترجع بدون مشروع.`)) return;
    state.tasks.forEach(t=>{ if(t.projectId===p.id) t.projectId = null; });
    state.projects = state.projects.filter(x=>x.id!==p.id);
    save();
    activeProjectId = null;
    projectsListSubview.classList.remove("hidden");
    projectDetailSubview.classList.add("hidden");
    renderAll();
  });
  projectDetailSubview.querySelector("#pdAddAnchor button").addEventListener("click", (e)=>{
    e.stopPropagation();
    openQuickAdd(projectDetailSubview.querySelector("#pdAddAnchor"), p.id);
  });

  function renderPdList(){
    const status = document.querySelector("#pdTabs .tab.active").dataset.status;
    const listEl = document.getElementById("pdTaskList");
    attachDragoverOnce(listEl);
    const items = state.tasks.filter(t=>t.projectId===p.id && t.status===status);
    listEl._currentItems = items;
    listEl.innerHTML = "";
    if(items.length===0){
      const info = EMPTY_COPY[status];
      const e = document.createElement("div");
      e.className = "empty";
      e.innerHTML = emptyIllo() + `<h3>${info.h}</h3><p>${info.p}</p>`;
      listEl.appendChild(e);
      return;
    }
    items.forEach(t=> listEl.appendChild(taskCard(t)));
  }
  setupTabs(document.getElementById("pdTabs"), renderPdList);
  renderPdList();
  window._renderPdList = renderPdList;
}

function renderProjectFilterChips(){
  const row = document.getElementById("projectFilterChips");
  row.innerHTML = "";
  const allChip = document.createElement("button");
  allChip.className = "chip" + (tasksProjectFilter==="all" ? " active" : "");
  allChip.textContent = "الكل";
  allChip.addEventListener("click", ()=>{ tasksProjectFilter="all"; renderProjectFilterChips(); renderTasksFor("tasks"); });
  row.appendChild(allChip);
  state.projects.forEach(p=>{
    const chip = document.createElement("button");
    chip.className = "chip" + (tasksProjectFilter===p.id ? " active" : "");
    chip.innerHTML = `<span class="cdot" style="background:${p.color}"></span>`;
    chip.append(document.createTextNode(p.name));
    chip.addEventListener("click", ()=>{ tasksProjectFilter=p.id; renderProjectFilterChips(); renderTasksFor("tasks"); });
    row.appendChild(chip);
  });
  const noneChip = document.createElement("button");
  noneChip.className = "chip" + (tasksProjectFilter==="none" ? " active" : "");
  noneChip.textContent = "بدون مشروع";
  noneChip.addEventListener("click", ()=>{ tasksProjectFilter="none"; renderProjectFilterChips(); renderTasksFor("tasks"); });
  row.appendChild(noneChip);
}

document.getElementById("qaProject").addEventListener("click", ()=>{
  switchView("projects");
  setTimeout(showProjectForm, 50);
});

/* ================= Notes ================= */
const notesGrid = document.getElementById("notesGrid");
const noteEditor = document.getElementById("noteEditor");
const noteTitleInput = document.getElementById("noteTitleInput");
const noteContentInput = document.getElementById("noteContentInput");
const noteSavedTag = document.getElementById("noteSavedTag");
let activeNoteId = null;
let noteSearchQuery = "";

function fmtTime(ts){
  const d = new Date(ts);
  return d.toLocaleDateString("ar-SA-u-ca-gregory", { day:"numeric", month:"short" }) + " · " +
         d.toLocaleTimeString("ar-SA", { hour:"2-digit", minute:"2-digit" });
}

function renderNotes(){
  notesGrid.innerHTML = "";
  const q = noteSearchQuery.trim().toLowerCase();
  const filtered = state.notes
    .filter(n => !q || (n.title||"").toLowerCase().includes(q) || (n.content||"").toLowerCase().includes(q))
    .slice().sort((a,b)=>b.updatedAt-a.updatedAt);

  if(state.notes.length===0){
    const e = document.createElement("div");
    e.className = "empty";
    e.innerHTML = emptyIllo() + `<h3>صفحة بيضاء</h3><p>اكتب أول ملاحظة وخلها تصير عادة يومية.</p>`;
    notesGrid.appendChild(e);
    return;
  }
  if(filtered.length===0){
    const e = document.createElement("div");
    e.className = "empty";
    e.innerHTML = emptyIllo() + `<h3>ولا نتيجة</h3><p>جرّب كلمة بحث ثانية.</p>`;
    notesGrid.appendChild(e);
    return;
  }
  filtered.forEach(n=>{
    const card = document.createElement("div");
    card.className = "note-card" + (n.id===activeNoteId ? " active" : "");
    card.innerHTML = `<h4></h4><p></p><time></time>`;
    card.querySelector("h4").textContent = n.title || "بدون عنوان";
    card.querySelector("p").textContent = n.content || "لا يوجد محتوى بعد...";
    card.querySelector("time").textContent = fmtTime(n.updatedAt);
    card.addEventListener("click", ()=> openNote(n.id));
    notesGrid.appendChild(card);
  });
}

function openNote(id){
  activeNoteId = id;
  const n = state.notes.find(x=>x.id===id);
  if(!n) return;
  noteEditor.classList.remove("hidden");
  noteTitleInput.value = n.title;
  noteContentInput.value = n.content;
  renderNotes();
}

let noteSaveTimer;
function scheduleNoteSave(){
  noteSavedTag.textContent = "جارٍ الحفظ...";
  clearTimeout(noteSaveTimer);
  noteSaveTimer = setTimeout(()=>{
    const n = state.notes.find(x=>x.id===activeNoteId);
    if(!n) return;
    n.title = noteTitleInput.value;
    n.content = noteContentInput.value;
    n.updatedAt = Date.now();
    save();
    noteSavedTag.textContent = "محفوظة تلقائياً";
    renderNotes();
  }, 450);
}
noteTitleInput.addEventListener("input", scheduleNoteSave);
noteContentInput.addEventListener("input", scheduleNoteSave);
document.getElementById("noteSearch").addEventListener("input", (e)=>{ noteSearchQuery = e.target.value; renderNotes(); });

function createNewNote(){
  const n = { id:uid(), title:"", content:"", updatedAt: Date.now() };
  state.notes.unshift(n);
  save();
  openNote(n.id);
  noteTitleInput.focus();
}
document.getElementById("newNoteBtn").addEventListener("click", createNewNote);
document.getElementById("qaNote").addEventListener("click", ()=>{ switchView("notes"); createNewNote(); });

document.getElementById("deleteNoteBtn").addEventListener("click", ()=>{
  state.notes = state.notes.filter(n=>n.id!==activeNoteId);
  activeNoteId = null;
  noteEditor.classList.add("hidden");
  document.body.classList.remove("focus-mode");
  save();
  renderNotes();
});

document.getElementById("focusModeBtn").addEventListener("click", ()=> document.body.classList.add("focus-mode"));
document.getElementById("closeFocusBtn").addEventListener("click", ()=> document.body.classList.remove("focus-mode"));
document.addEventListener("keydown", e=>{
  if(e.key==="Escape" && document.body.classList.contains("focus-mode")) document.body.classList.remove("focus-mode");
});

/* ================= Settings modal ================= */
document.getElementById("openSettings").addEventListener("click", ()=>{
  const overlay = document.createElement("div");
  overlay.className = "modal-overlay";
  overlay.innerHTML = `
    <div class="modal" style="position:relative;">
      <button class="modal-close" id="closeModal">${'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><path d="M18 6L6 18M6 6l12 12"/></svg>'}</button>
      <h3>الإعدادات</h3>
      <p class="modal-sub">بياناتك محفوظة محلياً على هذا الجهاز فقط.</p>
      <div class="modal-stats">
        <div class="modal-stat"><b>${state.tasks.length}</b><span>مهمة</span></div>
        <div class="modal-stat"><b>${state.projects.length}</b><span>مشروع</span></div>
        <div class="modal-stat"><b>${state.notes.length}</b><span>ملاحظة</span></div>
      </div>
      <p class="modal-footer-note">إعادة التعيين تحذف كل المهام والمشاريع والملاحظات نهائياً من هذا الجهاز.</p>
      <div class="modal-actions">
        <button class="btn-danger-confirm" id="resetBtn" style="flex:1;">إعادة تعيين البيانات</button>
      </div>
    </div>
  `;
  document.body.appendChild(overlay);
  overlay.addEventListener("click", e=>{ if(e.target===overlay) overlay.remove(); });
  overlay.querySelector("#closeModal").addEventListener("click", ()=> overlay.remove());
  const resetBtn = overlay.querySelector("#resetBtn");
  let confirming = false, confirmTimer;
  resetBtn.addEventListener("click", ()=>{
    if(!confirming){
      confirming = true;
      resetBtn.textContent = "متأكد؟ اضغط مرة ثانية للتأكيد";
      confirmTimer = setTimeout(()=>{ confirming=false; resetBtn.textContent = "إعادة تعيين البيانات"; }, 4000);
      return;
    }
    clearTimeout(confirmTimer);
    localStorage.removeItem(LS_KEY);
    localStorage.removeItem(LS_KEY_OLD);
    state = seedState();
    save();
    activeProjectId = null; activeNoteId = null;
    projectsListSubview.classList.remove("hidden");
    projectDetailSubview.classList.add("hidden");
    document.body.classList.remove("focus-mode");
    overlay.remove();
    renderAll();
    switchView("dashboard");
  });
});

/* ================= Onboarding ================= */
const onboarding = document.getElementById("onboarding");
if(localStorage.getItem(LS_ONBOARDED)){
  onboarding.remove();
} else {
  document.getElementById("onbStart").addEventListener("click", dismissOnboarding);
  document.addEventListener("keydown", function escOnb(e){
    if(e.key==="Escape"){ dismissOnboarding(); document.removeEventListener("keydown", escOnb); }
  });
}
function dismissOnboarding(){
  localStorage.setItem(LS_ONBOARDED, "1");
  onboarding.classList.add("leaving");
  setTimeout(()=> onboarding.remove(), 400);
}

/* ================= Greeting / clock ================= */
function updateGreeting(){
  const h = new Date().getHours();
  let g = "وش وراك اليوم؟";
  if(h < 5) g = "سهرانين لين الحين؟";
  else if(h < 12) g = "صباح الخير، وش وراك اليوم؟";
  else if(h < 17) g = "وش وراك اليوم؟";
  else g = "مساء الخير، خلّص شي حلو اليوم؟";
  document.getElementById("greeting").textContent = g;
  document.getElementById("dateTag").textContent = new Date().toLocaleDateString("ar-SA-u-ca-gregory", { weekday:"long", day:"numeric", month:"long" });
}
updateGreeting();
setInterval(updateGreeting, 30000);

/* ================= Keyboard shortcut ================= */
document.addEventListener("keydown", e=>{
  const tag = (document.activeElement && document.activeElement.tagName) || "";
  if(tag === "INPUT" || tag === "TEXTAREA") return;
  if(e.key.toLowerCase()==="n" && !document.querySelector(".modal-overlay")){
    e.preventDefault();
    const view = document.querySelector(".view.active").id;
    if(view==="view-dashboard") openQuickAdd(document.getElementById("dashAddAnchor"), null);
    else if(view==="view-tasks") openQuickAdd(document.getElementById("tasksAddAnchor"), null);
  }
});

/* ================= Render orchestration ================= */
function renderAll(){
  renderFocusCard();
  renderStats();
  renderTasksFor("dash");
  renderTasksFor("tasks");
  renderProjectFilterChips();
  if(activeProjectId && window._renderPdList){ renderProjectDetail(); }
  else { renderProjects(); }
  renderNotes();
}
renderAll();
requestAnimationFrame(()=>{
  const active = navItems.find(b=>b.classList.contains("active"));
  if(active) positionNavIndicator(active);
});

})();
</script>
</body>
</html>
