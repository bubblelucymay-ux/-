<!DOCTYPE html>

<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<title>CASH CREW</title>
<link href="https://fonts.googleapis.com/css2?family=Bangers&family=Nunito:wght@400;700;800;900&display=swap" rel="stylesheet">
<style>
:root {
  --orange:#FF6B35; --red:#E8341C; --yellow:#FFD166;
  --cream:#FFF5E0;  --brown:#3D1C02; --teal:#2EC4B6;
  --purple:#9B6DFF; --dark:#120800; --card:rgba(255,245,224,0.97);
  --safe-top:env(safe-area-inset-top,0px);
  --safe-bottom:env(safe-area-inset-bottom,0px);
}
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent;}
html,body{height:100%;}
body{background:var(--dark);font-family:'Nunito',sans-serif;overflow:hidden;
  background-image:radial-gradient(ellipse 100% 45% at 50% 0%,#5c1f00 0%,transparent 50%),
    radial-gradient(ellipse 70% 40% at 90% 100%,#2a0e00 0%,transparent 55%);
  -webkit-font-smoothing:antialiased;}

/* ── SHELL ── */
#app{display:flex;flex-direction:column;height:100dvh;max-width:430px;margin:0 auto;overflow:hidden;}

.app-header{flex-shrink:0;position:relative;text-align:center;
padding-top:calc(var(–safe-top) + 16px);padding-bottom:10px;overflow:hidden;}
.sunrays{position:absolute;top:0;left:50%;transform:translateX(-50%);width:220%;height:100%;
background:conic-gradient(from -90deg at 50% 0%,#6a2208 0deg,#e05a28 7deg,#6a2208 14deg,#e05a28 21deg,
#6a2208 28deg,#e05a28 35deg,#6a2208 42deg,#e05a28 49deg,#6a2208 56deg,#e05a28 63deg,
#6a2208 70deg,#e05a28 77deg,#6a2208 84deg,#e05a28 91deg,#6a2208 98deg,#e05a28 105deg,
#6a2208 112deg,#e05a28 119deg,#6a2208 126deg,#e05a28 133deg,#6a2208 140deg,#e05a28 147deg,
#6a2208 154deg,#e05a28 161deg,#6a2208 168deg,#e05a28 175deg,#6a2208 182deg);
opacity:.2;pointer-events:none;}
.logo{font-family:‘Bangers’,cursive;font-size:50px;letter-spacing:5px;color:var(–yellow);
text-shadow:3px 3px 0 var(–red),6px 6px 0 rgba(0,0,0,.35);line-height:1;position:relative;}
.logo-sub{font-family:‘Bangers’,cursive;font-size:13px;letter-spacing:7px;color:var(–orange);position:relative;}
.hs-row{display:flex;justify-content:center;gap:12px;margin-top:4px;position:relative;}
.hs{font-size:20px;display:inline-block;animation:wb 2.5s ease-in-out infinite;}
.hs:nth-child(2){animation-delay:.5s;}.hs:nth-child(3){animation-delay:1s;}
@keyframes wb{0%,100%{transform:rotate(-8deg) scale(1)}50%{transform:rotate(8deg) scale(1.12)}}

.app-body{flex:1;overflow-y:auto;overflow-x:hidden;-webkit-overflow-scrolling:touch;
overscroll-behavior:contain;padding:0 13px;padding-bottom:calc(var(–safe-bottom) + 82px);}
.app-body::-webkit-scrollbar{display:none;}

.view{display:none;animation:fadeUp .22s ease both;}
.view.active{display:block;}
@keyframes fadeUp{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:translateY(0)}}

/* ── BOTTOM NAV ── */
.bottom-nav{flex-shrink:0;display:flex;background:rgba(18,8,0,.93);
backdrop-filter:blur(20px);-webkit-backdrop-filter:blur(20px);
border-top:2px solid rgba(255,209,102,.13);padding-bottom:var(–safe-bottom);}
.nav-btn{flex:1;display:flex;flex-direction:column;align-items:center;justify-content:center;
gap:2px;padding:9px 0;border:none;background:transparent;cursor:pointer;position:relative;transition:transform .15s;}
.nav-btn:active{transform:scale(.9);}
.nav-icon{font-size:22px;line-height:1;transition:transform .2s cubic-bezier(.34,1.56,.64,1),filter .2s;}
.nav-label{font-family:‘Bangers’,cursive;font-size:11px;letter-spacing:1px;color:rgba(255,245,224,.3);transition:color .2s;}
.nav-ind{position:absolute;top:5px;width:24px;height:3px;background:var(–yellow);border-radius:2px;opacity:0;transition:opacity .2s;}
.nav-btn.active .nav-icon{transform:scale(1.18) translateY(-2px);filter:drop-shadow(0 0 5px rgba(255,209,102,.6));}
.nav-btn.active .nav-label{color:var(–yellow);}
.nav-btn.active .nav-ind{opacity:1;}

/* ── COMMON ── */
.top-pad{height:6px;}
.section-title{font-family:‘Bangers’,cursive;font-size:19px;letter-spacing:2px;color:var(–yellow);
text-shadow:2px 2px 0 var(–brown);margin:14px 0 8px;display:flex;align-items:center;gap:7px;}
.sec-count{font-family:‘Nunito’,sans-serif;font-size:12px;color:rgba(255,245,224,.28);}

.dark-card{background:linear-gradient(145deg,#200e00,#381500);border:2.5px solid var(–orange);
border-radius:18px;padding:14px 15px;margin-bottom:10px;box-shadow:0 4px 0 rgba(255,107,53,.35);}
.dark-card.yb{border-color:var(–yellow);box-shadow:0 4px 0 rgba(255,209,102,.3);}
.dark-card.pb{border-color:var(–purple);box-shadow:0 4px 0 rgba(155,109,255,.3);}
.dark-card.rb{border-color:var(–red);box-shadow:0 4px 0 rgba(232,52,28,.3);}
.dark-card.tb{border-color:var(–teal);box-shadow:0 4px 0 rgba(46,196,182,.3);}

.light-card{background:var(–card);border:2.5px solid var(–brown);border-radius:20px;
padding:15px;margin-bottom:10px;box-shadow:0 4px 0 var(–brown);}

.card-title{font-family:‘Bangers’,cursive;font-size:19px;letter-spacing:2px;margin-bottom:10px;}
.card-title.dk{color:var(–yellow);}
.card-title.lt{color:var(–brown);}

.dinput{background:rgba(255,245,224,.08);border:2px solid rgba(255,107,53,.55);border-radius:12px;
padding:11px 13px;color:var(–cream);font-family:‘Nunito’,sans-serif;font-size:15px;font-weight:700;
outline:none;-webkit-appearance:none;transition:border-color .2s,background .2s;width:100%;}
.dinput::placeholder{color:rgba(255,245,224,.25);}
.dinput:focus{border-color:var(–yellow);background:rgba(255,245,224,.12);}

.linput{background:white;border:2.5px solid var(–brown);border-radius:12px;padding:11px 13px;
color:var(–brown);font-family:‘Nunito’,sans-serif;font-size:15px;font-weight:700;
outline:none;-webkit-appearance:none;transition:border-color .2s;width:100%;}
.linput:focus{border-color:var(–orange);}

.hint{margin-top:7px;color:rgba(255,245,224,.4);font-size:11px;font-weight:800;}

.btn{background:var(–yellow);border:2.5px solid var(–brown);border-radius:12px;
padding:10px 16px;font-family:‘Bangers’,cursive;font-size:18px;letter-spacing:1px;color:var(–brown);
cursor:pointer;box-shadow:0 3px 0 var(–brown);transition:transform .1s,box-shadow .1s;
white-space:nowrap;line-height:1;min-height:44px;display:flex;align-items:center;justify-content:center;}
.btn:active{transform:translateY(2px);box-shadow:0 1px 0 var(–brown);}
.btn.red{background:var(–red);color:#fff;border-color:#8a1a0a;box-shadow:0 3px 0 #8a1a0a;}
.btn.teal{background:var(–teal);color:#fff;border-color:#1a8a85;box-shadow:0 3px 0 #1a8a85;}
.btn.purple{background:var(–purple);color:#fff;border-color:#5a3db0;box-shadow:0 3px 0 #5a3db0;}
.btn.full{width:100%;font-size:20px;padding:14px;min-height:52px;}
.setup-row{display:flex;gap:8px;align-items:center;}

/* ── HOME ── */
.month-bar{display:flex;justify-content:space-between;align-items:center;padding:12px 0 8px;}
.month-label{font-family:‘Bangers’,cursive;font-size:22px;color:var(–cream);letter-spacing:3px;opacity:.7;}
.month-nav{background:rgba(255,245,224,.08);border:2px solid rgba(255,245,224,.12);border-radius:10px;
color:var(–yellow);font-size:18px;cursor:pointer;padding:6px 14px;
transition:background .15s,transform .15s;min-width:44px;min-height:44px;
display:flex;align-items:center;justify-content:center;}
.month-nav:active{background:rgba(255,209,102,.15);transform:scale(.9);}

.balance-card{background:var(–yellow);border:3px solid var(–brown);border-radius:22px;
padding:16px 18px 13px;margin-bottom:10px;position:relative;box-shadow:0 6px 0 var(–brown);overflow:hidden;}
.balance-card::before{content:’’;position:absolute;top:-30px;right:-30px;width:150px;height:150px;
border-radius:50%;background:rgba(255,255,255,.11);}
.balance-card::after{content:‘💰’;position:absolute;right:16px;bottom:12px;font-size:46px;opacity:.1;transform:rotate(15deg);}
.balance-label{font-size:10px;font-weight:900;letter-spacing:3px;color:var(–brown);text-transform:uppercase;opacity:.55;}
.balance-amount{font-family:‘Bangers’,cursive;font-size:54px;color:var(–brown);letter-spacing:2px;line-height:1;margin:2px 0 5px;}
.balance-amount .cur{font-size:23px;vertical-align:super;margin-right:1px;}
.balance-meta{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:9px;}
.tag{border-radius:20px;padding:4px 11px;font-size:11px;font-weight:900;letter-spacing:.5px;}
.tag.income{background:var(–teal);color:#fff;}.tag.expense{background:var(–red);color:#fff;}
.tag.sub{background:var(–purple);color:#fff;}
.progress-wrap{display:flex;align-items:center;gap:8px;}
.progress-bar{flex:1;background:rgba(61,28,2,.18);border-radius:10px;height:6px;overflow:hidden;}
.progress-fill{height:100%;background:linear-gradient(90deg,var(–teal),var(–orange));border-radius:10px;transition:width 1s cubic-bezier(.34,1.56,.64,1);}
.progress-pct{font-size:11px;font-weight:900;color:var(–brown);opacity:.6;min-width:32px;text-align:right;}

.stats-row{display:grid;grid-template-columns:1fr 1fr 1fr;gap:7px;margin-bottom:10px;}
.stat-card{background:var(–card);border:2.5px solid var(–brown);border-radius:16px;padding:11px 9px;
box-shadow:0 3px 0 var(–brown);position:relative;overflow:hidden;}
.stat-card::after{content:attr(data-e);position:absolute;bottom:-6px;right:3px;font-size:30px;opacity:.1;transform:rotate(12deg);pointer-events:none;}
.stat-icon{font-size:16px;margin-bottom:1px;}.stat-label{font-size:9px;font-weight:900;letter-spacing:1.5px;color:#8B5A3A;text-transform:uppercase;}
.stat-value{font-family:‘Bangers’,cursive;font-size:19px;letter-spacing:1px;line-height:1.1;}
.stat-value.iv{color:#0a8c84;}.stat-value.ev{color:var(–red);}.stat-value.sv{color:var(–purple);}

/* ── TX LIST ── */
.tx-list{display:flex;flex-direction:column;gap:7px;}
.tx-item{background:var(–card);border:2.5px solid var(–brown);border-radius:15px;
padding:11px 13px;display:flex;align-items:center;gap:11px;box-shadow:0 3px 0 var(–brown);
animation:popIn .25s cubic-bezier(.34,1.56,.64,1) both;}
.tx-item.salary{background:linear-gradient(135deg,#1e9990,#167a74);border-color:#0d6b66;}
.tx-item.salary .tx-desc{color:#fff;}.tx-item.salary .tx-date{color:rgba(255,255,255,.6);}
.tx-item.salary .tx-amount{color:#fff;}
.tx-item.is-sub{background:linear-gradient(135deg,#2a1a4a,#1e1235);border-color:rgba(155,109,255,.5);}
.tx-item.is-sub .tx-desc{color:var(–cream);}.tx-item.is-sub .tx-date{color:rgba(255,245,224,.45);}
@keyframes popIn{from{opacity:0;transform:translateY(12px) scale(.95)}to{opacity:1;transform:translateY(0) scale(1)}}
.tx-emoji{font-size:21px;width:42px;height:42px;flex-shrink:0;background:var(–yellow);border:2.5px solid var(–brown);
border-radius:11px;display:flex;align-items:center;justify-content:center;}
.tx-item.salary .tx-emoji{background:rgba(255,255,255,.18);border-color:rgba(255,255,255,.3);}
.tx-item.is-sub .tx-emoji{background:rgba(155,109,255,.2);border-color:rgba(155,109,255,.4);}
.tx-info{flex:1;min-width:0;}
.tx-desc{font-size:14px;font-weight:900;color:var(–brown);white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}
.tx-date{font-size:11px;color:#8B5A3A;font-weight:700;margin-top:1px;}
.tx-amount{font-family:‘Bangers’,cursive;font-size:19px;letter-spacing:1px;flex-shrink:0;}
.tx-amount.income{color:#0a8c84;}.tx-amount.expense{color:var(–red);}.tx-amount.sub-amt{color:var(–purple);}
.tx-del{background:none;border:none;cursor:pointer;font-size:14px;color:var(–brown);opacity:.22;
padding:6px;margin:-6px;min-width:36px;min-height:36px;display:flex;align-items:center;justify-content:center;transition:opacity .15s;}
.tx-del:active{opacity:1;}

/* ── ADD ── */
.type-toggle{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:12px;}
.type-btn{padding:12px 8px;border-radius:14px;border:2.5px solid var(–brown);font-family:‘Bangers’,cursive;
font-size:18px;letter-spacing:1px;cursor:pointer;background:rgba(61,28,2,.05);color:var(–brown);transition:all .15s;min-height:48px;}
.type-btn.active.ib{background:var(–teal);color:#fff;border-color:#1a9990;box-shadow:0 3px 0 #1a9990;}
.type-btn.active.eb{background:var(–red);color:#fff;border-color:#a02010;box-shadow:0 3px 0 #a02010;}

.cat-grid{display:grid;grid-template-columns:repeat(5,1fr);gap:6px;margin-bottom:12px;}
.cat-btn{aspect-ratio:1;border-radius:12px;border:2.5px solid var(–brown);font-size:21px;cursor:pointer;
background:white;transition:all .15s;display:flex;align-items:center;justify-content:center;min-height:50px;}
.cat-btn.active{background:var(–yellow);border-color:var(–orange);box-shadow:0 3px 0 var(–orange);transform:scale(1.08);}

.form-row{display:flex;gap:8px;margin-bottom:10px;}
.form-row .linput{flex:1;}

/* ── CHARTS ── */
.chart-container{position:relative;width:100%;margin-bottom:10px;}

/* Donut */
.donut-wrap{display:flex;align-items:center;gap:16px;background:var(–card);border:2.5px solid var(–brown);
border-radius:20px;padding:16px;box-shadow:0 4px 0 var(–brown);}
.donut-svg{flex-shrink:0;width:120px;height:120px;}
.donut-legend{flex:1;display:flex;flex-direction:column;gap:7px;}
.legend-item{display:flex;align-items:center;gap:8px;}
.legend-dot{width:12px;height:12px;border-radius:50%;flex-shrink:0;}
.legend-label{font-size:12px;font-weight:800;color:var(–brown);flex:1;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}
.legend-pct{font-family:‘Bangers’,cursive;font-size:16px;color:var(–brown);}

/* Bar chart */
.bar-chart{background:var(–card);border:2.5px solid var(–brown);border-radius:20px;
padding:14px 15px;box-shadow:0 4px 0 var(–brown);margin-bottom:10px;}
.bar-chart-title{font-family:‘Bangers’,cursive;font-size:16px;letter-spacing:1.5px;color:var(–brown);margin-bottom:12px;}
.bars{display:flex;align-items:flex-end;gap:6px;height:80px;}
.bar-col{flex:1;display:flex;flex-direction:column;align-items:center;gap:3px;}
.bar-fill{width:100%;border-radius:6px 6px 0 0;transition:height .6s cubic-bezier(.34,1.56,.64,1);min-height:2px;}
.bar-fill.income-bar{background:var(–teal);}
.bar-fill.expense-bar{background:var(–red);}
.bar-month{font-size:9px;font-weight:900;color:#8B5A3A;letter-spacing:.5px;}
.bar-val{font-family:‘Bangers’,cursive;font-size:11px;color:var(–brown);}

/* ── BUDGET ── */
.budget-item{background:var(–card);border:2.5px solid var(–brown);border-radius:16px;
padding:13px 14px;margin-bottom:8px;box-shadow:0 3px 0 var(–brown);}
.budget-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:8px;}
.budget-cat{font-size:20px;margin-right:7px;}
.budget-name{font-size:13px;font-weight:900;color:var(–brown);flex:1;}
.budget-nums{font-family:‘Bangers’,cursive;font-size:16px;letter-spacing:1px;}
.budget-bar-bg{background:rgba(61,28,2,.15);border-radius:8px;height:8px;overflow:hidden;}
.budget-bar-fill{height:100%;border-radius:8px;transition:width .8s cubic-bezier(.34,1.56,.64,1);}
.budget-bar-fill.ok{background:linear-gradient(90deg,var(–teal),#5dd6d0);}
.budget-bar-fill.warn{background:linear-gradient(90deg,var(–orange),#ffaa55);}
.budget-bar-fill.over{background:linear-gradient(90deg,var(–red),#ff6655);}
.budget-del{background:none;border:none;cursor:pointer;opacity:.25;font-size:14px;padding:4px;color:var(–brown);}
.budget-del:active{opacity:1;}

.add-budget-row{display:grid;grid-template-columns:44px 1fr 90px auto;gap:7px;align-items:center;margin-top:4px;}

/* ── SAVINGS GOALS ── */
.goal-item{background:var(–card);border:2.5px solid var(–brown);border-radius:16px;
padding:13px 14px;margin-bottom:8px;box-shadow:0 3px 0 var(–brown);}
.goal-header{display:flex;align-items:center;gap:10px;margin-bottom:8px;}
.goal-icon{font-size:26px;width:44px;height:44px;background:rgba(255,209,102,.25);border:2px solid var(–brown);
border-radius:12px;display:flex;align-items:center;justify-content:center;flex-shrink:0;}
.goal-info{flex:1;min-width:0;}
.goal-name{font-size:14px;font-weight:900;color:var(–brown);}
.goal-nums{font-size:12px;font-weight:700;color:#8B5A3A;margin-top:1px;}
.goal-pct{font-family:‘Bangers’,cursive;font-size:18px;color:var(–yellow);
text-shadow:1px 1px 0 var(–brown);flex-shrink:0;}
.goal-bar-bg{background:rgba(61,28,2,.15);border-radius:8px;height:10px;overflow:hidden;margin-bottom:8px;}
.goal-bar-fill{height:100%;border-radius:8px;background:linear-gradient(90deg,var(–yellow),var(–orange));
transition:width .8s cubic-bezier(.34,1.56,.64,1);}
.goal-bar-fill.done{background:linear-gradient(90deg,var(–teal),#5dd6d0);}
.goal-add-btn{background:var(–yellow);border:2px solid var(–brown);border-radius:8px;
padding:5px 12px;font-family:‘Bangers’,cursive;font-size:15px;letter-spacing:1px;color:var(–brown);cursor:pointer;
box-shadow:0 2px 0 var(–brown);transition:transform .1s;}
.goal-add-btn:active{transform:translateY(1px);}
.goal-done-badge{background:var(–teal);color:#fff;border-radius:8px;padding:4px 10px;
font-size:11px;font-weight:900;letter-spacing:1px;}
.goal-del{background:none;border:none;cursor:pointer;opacity:.22;font-size:14px;padding:4px;color:var(–brown);}
.goal-del:active{opacity:1;}

.add-goal-grid{display:grid;grid-template-columns:44px 1fr 90px;gap:7px;align-items:center;margin-bottom:7px;}
.goal-emoji-pick{width:44px;height:44px;background:rgba(255,209,102,.15);border:2px solid rgba(255,209,102,.5);
border-radius:12px;font-size:22px;cursor:pointer;display:flex;align-items:center;justify-content:center;}

/* ── SUB ── */
.sub-add-row{display:grid;grid-template-columns:44px 1fr 70px 48px 44px;gap:7px;align-items:center;}
.emoji-pick{width:44px;height:44px;flex-shrink:0;background:rgba(155,109,255,.15);
border:2px solid rgba(155,109,255,.5);border-radius:12px;font-size:22px;cursor:pointer;
display:flex;align-items:center;justify-content:center;transition:all .15s;}
.emoji-pick:active{background:rgba(155,109,255,.3);transform:scale(.92);}
.emoji-panel{display:none;flex-wrap:wrap;gap:4px;background:linear-gradient(145deg,#2a1a4a,#1e1235);
border:2px solid var(–purple);border-radius:14px;padding:10px;margin-top:8px;box-shadow:0 4px 0 rgba(155,109,255,.4);}
.emoji-panel.open{display:flex;animation:fadeUp .2s ease both;}
.ep-opt{font-size:25px;cursor:pointer;padding:5px;border-radius:8px;transition:background .1s;}
.ep-opt:active{background:rgba(155,109,255,.3);}
.sub-total-row{display:flex;align-items:center;justify-content:space-between;background:rgba(155,109,255,.1);
border:2px solid rgba(155,109,255,.2);border-radius:14px;padding:11px 14px;margin-bottom:10px;}
.sub-total-label{font-size:11px;font-weight:900;color:rgba(155,109,255,.75);letter-spacing:2px;text-transform:uppercase;}
.sub-total-val{font-family:‘Bangers’,cursive;font-size:22px;color:var(–purple);letter-spacing:1px;}
.sub-list{display:flex;flex-direction:column;gap:8px;}
.sub-item{display:flex;align-items:center;gap:11px;background:rgba(155,109,255,.07);
border:2px solid rgba(155,109,255,.25);border-radius:16px;padding:12px 13px;animation:popIn .25s cubic-bezier(.34,1.56,.64,1) both;}
.sub-icon{font-size:21px;width:42px;height:42px;flex-shrink:0;background:rgba(155,109,255,.15);
border:2px solid rgba(155,109,255,.35);border-radius:11px;display:flex;align-items:center;justify-content:center;}
.sub-info{flex:1;min-width:0;}
.sub-name{font-size:14px;font-weight:900;color:var(–cream);}
.sub-detail{font-size:11px;color:rgba(255,245,224,.4);font-weight:700;margin-top:1px;}
.sub-amount{font-family:‘Bangers’,cursive;font-size:19px;color:var(–purple);flex-shrink:0;}
.sub-del{background:none;border:none;cursor:pointer;color:rgba(255,245,224,.28);font-size:14px;
padding:6px;margin:-6px;min-width:36px;min-height:36px;display:flex;align-items:center;justify-content:center;}
.sub-del:active{color:var(–red);}

/* ── MODAL (edit tx / add deposit) ── */
.modal-bg{position:fixed;inset:0;background:rgba(0,0,0,.65);backdrop-filter:blur(6px);
z-index:100;display:flex;align-items:flex-end;justify-content:center;
opacity:0;pointer-events:none;transition:opacity .25s;}
.modal-bg.open{opacity:1;pointer-events:all;}
.modal{background:linear-gradient(160deg,#2a1200,#1a0800);border:2.5px solid var(–orange);
border-radius:24px 24px 0 0;padding:20px 16px;padding-bottom:calc(var(–safe-bottom) + 20px);
width:100%;max-width:430px;transform:translateY(100%);transition:transform .3s cubic-bezier(.34,1.56,.64,1);}
.modal-bg.open .modal{transform:translateY(0);}
.modal-title{font-family:‘Bangers’,cursive;font-size:22px;letter-spacing:2px;color:var(–yellow);margin-bottom:14px;}
.modal-row{display:flex;gap:8px;margin-bottom:10px;}
.modal-close{background:none;border:none;color:rgba(255,245,224,.4);font-size:22px;cursor:pointer;
position:absolute;top:18px;right:16px;min-width:36px;min-height:36px;}

/* ── EMPTY ── */
.empty-state{text-align:center;padding:32px 16px;color:rgba(255,245,224,.28);}
.empty-state .e{font-size:52px;margin-bottom:10px;display:block;}
.empty-state p{font-weight:800;font-size:13px;letter-spacing:1px;line-height:1.7;}

/* ── TOAST ── */
.toast{position:fixed;bottom:calc(var(–safe-bottom) + 78px);left:50%;
transform:translateX(-50%) translateY(14px);background:rgba(61,28,2,.95);
backdrop-filter:blur(10px);color:var(–yellow);font-family:‘Bangers’,cursive;
font-size:16px;letter-spacing:2px;padding:9px 18px;border-radius:14px;
border:2px solid rgba(255,209,102,.35);box-shadow:0 4px 18px rgba(0,0,0,.4);
opacity:0;transition:all .28s cubic-bezier(.34,1.56,.64,1);z-index:200;white-space:nowrap;pointer-events:none;}
.toast.show{opacity:1;transform:translateX(-50%) translateY(0);}

/* ── CUSTOM CATS ── */
.custom-cats-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:6px;margin-bottom:10px;}
.ccat-chip{display:flex;flex-direction:column;align-items:center;gap:2px;
background:var(–card);border:2.5px solid var(–brown);border-radius:12px;
padding:8px 4px;cursor:pointer;position:relative;transition:all .15s;}
.ccat-chip:active{transform:scale(.95);}
.ccat-emoji{font-size:22px;}.ccat-label{font-size:9px;font-weight:900;color:var(–brown);letter-spacing:.5px;text-align:center;max-width:60px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap;}
.ccat-del{position:absolute;top:-4px;right:-4px;background:var(–red);color:#fff;border:none;border-radius:50%;
width:16px;height:16px;font-size:9px;cursor:pointer;display:flex;align-items:center;justify-content:center;}
</style>

</head>
<body>
<div id="app">

<!-- HEADER -->

<div class="app-header">
  <div class="sunrays"></div>
  <div class="logo">CASH CREW</div>
  <div class="logo-sub">記帳小隊出發！</div>
  <div class="hs-row"><span class="hs">🤙</span><span class="hs">💸</span><span class="hs">🎵</span></div>
</div>

<!-- BODY -->

<div class="app-body" id="appBody">

<!-- ══ HOME ══ -->

<div class="view active" id="view-home">
  <div class="top-pad"></div>
  <div class="month-bar">
    <button class="month-nav" onclick="changeMonth(-1)">◀</button>
    <span class="month-label" id="monthLabel"></span>
    <button class="month-nav" onclick="changeMonth(1)">▶</button>
  </div>
  <div class="balance-card">
    <div class="balance-label">💵 當前餘額</div>
    <div class="balance-amount"><span class="cur">NT$</span><span id="balanceDisplay">0</span></div>
    <div class="balance-meta">
      <span class="tag income" id="incomeTag">＋ $0</span>
      <span class="tag expense" id="expenseTag">－ $0</span>
      <span class="tag sub" id="subTag">📡 $0</span>
    </div>
    <div class="progress-wrap">
      <div class="progress-bar"><div class="progress-fill" id="progressFill" style="width:0%"></div></div>
      <div class="progress-pct" id="progressPct">0%</div>
    </div>
  </div>
  <div class="stats-row">
    <div class="stat-card" data-e="📈"><div class="stat-icon">📈</div><div class="stat-label">本月收入</div><div class="stat-value iv" id="statIncome">$0</div></div>
    <div class="stat-card" data-e="🛍️"><div class="stat-icon">📉</div><div class="stat-label">本月支出</div><div class="stat-value ev" id="statExpense">$0</div></div>
    <div class="stat-card" data-e="📡"><div class="stat-icon">📡</div><div class="stat-label">月訂閱</div><div class="stat-value sv" id="statSub">$0</div></div>
  </div>
  <div class="section-title">🧾 交易紀錄 <span class="sec-count" id="txCount"></span></div>
  <div class="tx-list" id="txList"></div>
</div>

<!-- ══ ADD ══ -->

<div class="view" id="view-add">
  <div class="top-pad"></div>
  <div class="light-card">
    <div class="card-title lt">✏️ 新增紀錄</div>
    <div class="type-toggle">
      <button class="type-btn ib active" id="incomeBtn" onclick="setType('income')">＋ 收入</button>
      <button class="type-btn eb" id="expenseBtn" onclick="setType('expense')">－ 支出</button>
    </div>
    <div class="cat-grid" id="catGrid"></div>
    <div class="form-row">
      <input type="number" inputmode="decimal" class="linput" id="amountInput" placeholder="金額 NT$" style="flex:0 0 130px;">
      <input type="text" class="linput" id="descInput" placeholder="備註說明">
    </div>
    <!-- Date picker row -->
    <div class="form-row" style="margin-bottom:12px;">
      <input type="date" class="linput" id="txDateInput">
    </div>
    <button class="btn red full" onclick="addTransaction()">BOOM! 新增 💥</button>
  </div>
</div>

<!-- ══ CHARTS ══ -->

<div class="view" id="view-charts">
  <div class="top-pad"></div>
  <div class="section-title">📊 支出分類</div>
  <div class="donut-wrap" id="donutWrap">
    <svg class="donut-svg" viewBox="0 0 120 120" id="donutSvg"></svg>
    <div class="donut-legend" id="donutLegend"></div>
  </div>
  <div class="section-title">📈 收支趨勢（近6月）</div>
  <div class="bar-chart">
    <div class="bar-chart-title">每月收入 vs 支出</div>
    <div class="bars" id="barChartBars"></div>
    <div style="display:flex;gap:12px;margin-top:8px;">
      <span style="display:flex;align-items:center;gap:4px;font-size:11px;font-weight:800;color:#8B5A3A;">
        <span style="width:10px;height:10px;border-radius:3px;background:var(--teal);display:inline-block;"></span>收入
      </span>
      <span style="display:flex;align-items:center;gap:4px;font-size:11px;font-weight:800;color:#8B5A3A;">
        <span style="width:10px;height:10px;border-radius:3px;background:var(--red);display:inline-block;"></span>支出
      </span>
    </div>
  </div>
</div>

<!-- ══ BUDGET & GOALS ══ -->

<div class="view" id="view-budget">
  <div class="top-pad"></div>

  <!-- BUDGET -->

  <div class="section-title">🎯 預算設定</div>
  <div class="dark-card tb">
    <div class="card-title dk">➕ 新增預算</div>
    <div class="add-budget-row">
      <div class="goal-emoji-pick" id="budgetEmojiPick" onclick="toggleBudgetEmoji()" style="border-color:rgba(46,196,182,.5);background:rgba(46,196,182,.15);">🍔</div>
      <input type="text" class="dinput" id="budgetName" placeholder="預算名稱" style="border-color:rgba(46,196,182,.5);">
      <input type="number" inputmode="decimal" class="dinput" id="budgetAmount" placeholder="上限金額" style="border-color:rgba(46,196,182,.5);">
      <button class="btn teal" onclick="addBudget()" style="padding:0;font-size:22px;min-width:44px;">＋</button>
    </div>
    <div class="emoji-panel" id="budgetEmojiPanel">
      <span class="ep-opt" onclick="pickBudgetEmoji('🍔')">🍔</span><span class="ep-opt" onclick="pickBudgetEmoji('☕')">☕</span>
      <span class="ep-opt" onclick="pickBudgetEmoji('🛍️')">🛍️</span><span class="ep-opt" onclick="pickBudgetEmoji('🚇')">🚇</span>
      <span class="ep-opt" onclick="pickBudgetEmoji('🎮')">🎮</span><span class="ep-opt" onclick="pickBudgetEmoji('💊')">💊</span>
      <span class="ep-opt" onclick="pickBudgetEmoji('✈️')">✈️</span><span class="ep-opt" onclick="pickBudgetEmoji('🎵')">🎵</span>
      <span class="ep-opt" onclick="pickBudgetEmoji('📚')">📚</span><span class="ep-opt" onclick="pickBudgetEmoji('💡')">💡</span>
      <span class="ep-opt" onclick="pickBudgetEmoji('🏠')">🏠</span><span class="ep-opt" onclick="pickBudgetEmoji('🐾')">🐾</span>
    </div>
  </div>
  <div id="budgetList"></div>

  <!-- SAVINGS GOALS -->

  <div class="section-title">🏆 存錢目標</div>
  <div class="dark-card yb">
    <div class="card-title dk">➕ 新增目標</div>
    <div class="add-goal-grid">
      <div class="goal-emoji-pick" id="goalEmojiPick" onclick="toggleGoalEmoji()">🏖️</div>
      <input type="text" class="dinput" id="goalName" placeholder="目標名稱" style="border-color:rgba(255,209,102,.5);">
      <input type="number" inputmode="decimal" class="dinput" id="goalTarget" placeholder="目標金額" style="border-color:rgba(255,209,102,.5);">
    </div>
    <div class="emoji-panel" id="goalEmojiPanel" style="border-color:var(--yellow);box-shadow:0 4px 0 rgba(255,209,102,.35);">
      <span class="ep-opt" onclick="pickGoalEmoji('🏖️')">🏖️</span><span class="ep-opt" onclick="pickGoalEmoji('🚗')">🚗</span>
      <span class="ep-opt" onclick="pickGoalEmoji('🏠')">🏠</span><span class="ep-opt" onclick="pickGoalEmoji('💍')">💍</span>
      <span class="ep-opt" onclick="pickGoalEmoji('💻')">💻</span><span class="ep-opt" onclick="pickGoalEmoji('📷')">📷</span>
      <span class="ep-opt" onclick="pickGoalEmoji('🎓')">🎓</span><span class="ep-opt" onclick="pickGoalEmoji('✈️')">✈️</span>
      <span class="ep-opt" onclick="pickGoalEmoji('🐶')">🐶</span><span class="ep-opt" onclick="pickGoalEmoji('🎸')">🎸</span>
      <span class="ep-opt" onclick="pickGoalEmoji('⭐')">⭐</span><span class="ep-opt" onclick="pickGoalEmoji('🏆')">🏆</span>
    </div>
    <button class="btn full" onclick="addGoal()" style="margin-top:10px;">建立目標</button>
  </div>
  <div id="goalList"></div>
</div>

<!-- ══ SUB ══ -->

<div class="view" id="view-sub">
  <div class="top-pad"></div>
  <div class="dark-card pb">
    <div class="card-title dk">📡 新增訂閱</div>
    <div class="sub-add-row">
      <div class="emoji-pick" id="subEmojiPick" onclick="toggleSubEmoji()">🎵</div>
      <input type="text" class="dinput" id="subName" placeholder="服務名稱">
      <input type="number" inputmode="decimal" class="dinput" id="subAmount" placeholder="金額">
      <input type="number" inputmode="numeric" class="dinput" id="subDay" placeholder="日" min="1" max="31">
      <button class="btn purple" onclick="addSub()" style="padding:0;font-size:22px;min-width:44px;">＋</button>
    </div>
    <div class="emoji-panel" id="subEmojiPanel">
      <span class="ep-opt" onclick="pickSubEmoji('🎵')">🎵</span><span class="ep-opt" onclick="pickSubEmoji('🎬')">🎬</span>
      <span class="ep-opt" onclick="pickSubEmoji('📺')">📺</span><span class="ep-opt" onclick="pickSubEmoji('🎮')">🎮</span>
      <span class="ep-opt" onclick="pickSubEmoji('☁️')">☁️</span><span class="ep-opt" onclick="pickSubEmoji('📰')">📰</span>
      <span class="ep-opt" onclick="pickSubEmoji('🏋️')">🏋️</span><span class="ep-opt" onclick="pickSubEmoji('🧘')">🧘</span>
      <span class="ep-opt" onclick="pickSubEmoji('💼')">💼</span><span class="ep-opt" onclick="pickSubEmoji('🎨')">🎨</span>
      <span class="ep-opt" onclick="pickSubEmoji('🛡️')">🛡️</span><span class="ep-opt" onclick="pickSubEmoji('🤖')">🤖</span>
    </div>
    <div class="hint" style="margin-top:8px;">名稱 · 金額 · 每月扣款日 → 到期自動記入</div>
  </div>
  <div class="sub-total-row">
    <span class="sub-total-label">📡 每月訂閱總計</span>
    <span class="sub-total-val" id="subTotalDisplay">NT$ 0</span>
  </div>
  <div class="sub-list" id="subList"></div>
</div>

<!-- ══ SETTINGS ══ -->

<div class="view" id="view-settings">
  <div class="top-pad"></div>
  <div class="dark-card">
    <div class="card-title dk">💼 月薪設定</div>
    <div class="setup-row"><input type="number" inputmode="decimal" class="dinput" id="salaryInput" placeholder="輸入每月薪水..."><button class="btn" onclick="saveSalary()">SET IT</button></div>
    <div class="hint" id="salaryInfo">每月 1 日自動匯入月薪 💸</div>
  </div>
  <div class="dark-card yb">
    <div class="card-title dk">🏦 初始餘額</div>
    <div class="setup-row"><input type="number" inputmode="decimal" class="dinput" id="initInput" placeholder="設定起始金額..."><button class="btn" onclick="saveInit()">SET IT</button></div>
    <div class="hint" id="initInfo">設定帳戶現有金額作為起點 💰</div>
  </div>
  <!-- Custom categories -->
  <div class="section-title">🏷️ 自訂分類</div>
  <div class="dark-card">
    <div class="card-title dk" style="font-size:17px;">➕ 新增分類</div>
    <div style="display:grid;grid-template-columns:44px 1fr auto;gap:7px;align-items:center;">
      <div class="goal-emoji-pick" id="ccatEmojiPick" onclick="toggleCcatEmoji()" style="border-color:rgba(255,107,53,.5);background:rgba(255,107,53,.12);">🌟</div>
      <input type="text" class="dinput" id="ccatName" placeholder="分類名稱（最多6字）" maxlength="6">
      <button class="btn" onclick="addCustomCat()" style="padding:0;font-size:22px;min-width:44px;">＋</button>
    </div>
    <div class="emoji-panel" id="ccatEmojiPanel">
      <span class="ep-opt" onclick="pickCcatEmoji('🌟')">🌟</span><span class="ep-opt" onclick="pickCcatEmoji('🍕')">🍕</span>
      <span class="ep-opt" onclick="pickCcatEmoji('🎁')">🎁</span><span class="ep-opt" onclick="pickCcatEmoji('🌿')">🌿</span>
      <span class="ep-opt" onclick="pickCcatEmoji('🐱')">🐱</span><span class="ep-opt" onclick="pickCcatEmoji('🐶')">🐶</span>
      <span class="ep-opt" onclick="pickCcatEmoji('🧴')">🧴</span><span class="ep-opt" onclick="pickCcatEmoji('💅')">💅</span>
      <span class="ep-opt" onclick="pickCcatEmoji('🍷')">🍷</span><span class="ep-opt" onclick="pickCcatEmoji('🎂')">🎂</span>
      <span class="ep-opt" onclick="pickCcatEmoji('🏃')">🏃</span><span class="ep-opt" onclick="pickCcatEmoji('🧩')">🧩</span>
    </div>
  </div>
  <div class="custom-cats-grid" id="customCatsGrid"></div>

  <div class="dark-card rb" style="margin-top:6px;">
    <div class="card-title" style="color:var(--red);font-family:'Bangers',cursive;font-size:18px;letter-spacing:2px;margin-bottom:10px;">⚠️ 危險區域</div>
    <button class="btn red full" onclick="confirmClear()">清除所有資料</button>
  </div>
</div>

</div><!-- /body -->

<!-- BOTTOM NAV -->

<nav class="bottom-nav">
  <button class="nav-btn active" id="nav-home" onclick="switchTab('home')"><div class="nav-ind"></div><span class="nav-icon">🏠</span><span class="nav-label">總覽</span></button>
  <button class="nav-btn" id="nav-add" onclick="switchTab('add')"><div class="nav-ind"></div><span class="nav-icon">➕</span><span class="nav-label">記帳</span></button>
  <button class="nav-btn" id="nav-charts" onclick="switchTab('charts')"><div class="nav-ind"></div><span class="nav-icon">📊</span><span class="nav-label">圖表</span></button>
  <button class="nav-btn" id="nav-budget" onclick="switchTab('budget')"><div class="nav-ind"></div><span class="nav-icon">🎯</span><span class="nav-label">目標</span></button>
  <button class="nav-btn" id="nav-sub" onclick="switchTab('sub')"><div class="nav-ind"></div><span class="nav-icon">📡</span><span class="nav-label">訂閱</span></button>
  <button class="nav-btn" id="nav-settings" onclick="switchTab('settings')"><div class="nav-ind"></div><span class="nav-icon">⚙️</span><span class="nav-label">設定</span></button>
</nav>

</div><!-- /app -->

<!-- DEPOSIT MODAL for savings goals -->

<div class="modal-bg" id="depositModal">
  <div class="modal" style="position:relative;">
    <button class="modal-close" onclick="closeDeposit()">✕</button>
    <div class="modal-title">💰 存入金額</div>
    <div class="modal-row">
      <input type="number" inputmode="decimal" class="dinput" id="depositAmount" placeholder="要存入多少？">
    </div>
    <button class="btn full" onclick="confirmDeposit()">存入！</button>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
// ── DEFAULT CATS ──
const DEFAULT_EXPENSE_CATS = ['🍔','🚇','🛍️','🎮','💊','☕','✈️','🎵','📚','💡'];
const DEFAULT_INCOME_CATS  = ['💼','💰','🎁','📈','🏆','🎵','📸','🛒','🎓','⭐'];
const CAT_COLORS = ['#FF6B35','#2EC4B6','#9B6DFF','#FFD166','#E8341C','#5DD6D0',
  '#FF9F1C','#CBFF8C','#FF6FA8','#44BBA4','#F72585','#4CC9F0'];

// ── STATE ──
let S = {
  salary:0, initialBalance:0,
  transactions:[], subscriptions:[], budgets:[], goals:[],
  customCats:[], // [{emoji, name}]
  currentYear:new Date().getFullYear(), currentMonth:new Date().getMonth()+1,
  selType:'income', selCat:'🍔',
  subEmoji:'🎵', budgetEmoji:'🍔', goalEmoji:'🏖️', ccatEmoji:'🌟',
  activeGoalId:null
};

// ── PERSIST ──
function load(){
  const r=localStorage.getItem('cashcrew_v5');
  if(r){const p=JSON.parse(r);Object.assign(S,{salary:p.salary||0,initialBalance:p.initialBalance||0,
    transactions:p.transactions||[],subscriptions:p.subscriptions||[],
    budgets:p.budgets||[],goals:p.goals||[],customCats:p.customCats||[]});}
  checkSalary(); checkSubCharges();
}
function save(){
  localStorage.setItem('cashcrew_v5',JSON.stringify({salary:S.salary,initialBalance:S.initialBalance,
    transactions:S.transactions,subscriptions:S.subscriptions,
    budgets:S.budgets,goals:S.goals,customCats:S.customCats}));
}
function fmt(y,m,d){return y+'/'+String(m).padStart(2,'0')+'/'+String(d).padStart(2,'0');}

// ── SALARY ──
function checkSalary(){
  if(!S.salary) return;
  const now=new Date(), key=`sal_${now.getFullYear()}_${now.getMonth()+1}`;
  if(!S.transactions.find(t=>t.id===key)){
    S.transactions.unshift({id:key,type:'income',amount:S.salary,desc:'💼 月薪入帳',cat:'💼',
      date:fmt(now.getFullYear(),now.getMonth()+1,1),year:now.getFullYear(),month:now.getMonth()+1,isSalary:true,ts:Date.now()});
    save();
  }
}
function saveSalary(){
  const v=parseInt(document.getElementById('salaryInput').value);
  if(!v||v<=0){toast('請輸入有效金額！');return;}
  S.salary=v;
  const now=new Date(),key=`sal_${now.getFullYear()}_${now.getMonth()+1}`;
  S.transactions=S.transactions.filter(t=>t.id!==key);
  checkSalary(); document.getElementById('salaryInput').value='';
  document.getElementById('salaryInfo').textContent=`月薪 NT$ ${v.toLocaleString()} ✅`;
  save(); render(); toast('月薪設定完成！🎉');
}
function saveInit(){
  const v=parseFloat(document.getElementById('initInput').value);
  if(isNaN(v)){toast('請輸入有效金額！');return;}
  S.initialBalance=v; save(); render();
  document.getElementById('initInput').value='';
  document.getElementById('initInfo').textContent=`起始餘額 NT$ ${v.toLocaleString()} ✅`;
  toast('初始餘額設定完成！🏦');
}
function confirmClear(){
  if(confirm('確定清除全部資料？')){
    localStorage.removeItem('cashcrew_v5');
    location.reload();
  }
}

// ── SUBSCRIPTIONS ──
function checkSubCharges(){
  const now=new Date();
  S.subscriptions.forEach(sub=>{
    const key=`sub_${sub.id}_${now.getFullYear()}_${now.getMonth()+1}`;
    if(!S.transactions.find(t=>t.id===key)&&now.getDate()>=sub.day)
      S.transactions.unshift({id:key,type:'expense',amount:sub.amount,
        desc:sub.emoji+' '+sub.name,cat:sub.emoji,
        date:fmt(now.getFullYear(),now.getMonth()+1,sub.day),
        year:now.getFullYear(),month:now.getMonth()+1,isSub:true,ts:Date.now()});
  });
  save();
}
function toggleSubEmoji(){document.getElementById('subEmojiPanel').classList.toggle('open');}
function pickSubEmoji(e){S.subEmoji=e;document.getElementById('subEmojiPick').textContent=e;document.getElementById('subEmojiPanel').classList.remove('open');}
function addSub(){
  const name=document.getElementById('subName').value.trim();
  const amount=parseFloat(document.getElementById('subAmount').value);
  const day=parseInt(document.getElementById('subDay').value)||1;
  if(!name||!amount||amount<=0){toast('請填寫名稱和金額！');return;}
  S.subscriptions.push({id:Date.now().toString(),name,amount,day,emoji:S.subEmoji});
  save(); checkSubCharges();
  document.getElementById('subName').value=''; document.getElementById('subAmount').value=''; document.getElementById('subDay').value='';
  render(); renderSubs(); toast(S.subEmoji+' '+name+' 已加入！');
}
function deleteSub(id){
  S.subscriptions=S.subscriptions.filter(s=>s.id!==id);
  S.transactions=S.transactions.filter(t=>!t.id.startsWith(`sub_${id}_`));
  save(); render(); renderSubs(); toast('訂閱已刪除 👋');
}
function renderSubs(){
  const total=S.subscriptions.reduce((s,x)=>s+x.amount,0);
  document.getElementById('subTotalDisplay').textContent='NT$ '+total.toLocaleString();
  const list=document.getElementById('subList');
  if(!S.subscriptions.length){list.innerHTML=`<div class="empty-state"><span class="e">📡</span><p>還沒有訂閱<br>加入 Netflix、YouTube…</p></div>`;return;}
  list.innerHTML=S.subscriptions.map(s=>`
    <div class="sub-item"><div class="sub-icon">${s.emoji}</div>
    <div class="sub-info"><div class="sub-name">${s.name}</div><div class="sub-detail">每月 ${s.day} 日 · NT$ ${s.amount.toLocaleString()}</div></div>
    <div class="sub-amount">-$${s.amount.toLocaleString()}</div>
    <button class="sub-del" onclick="deleteSub('${s.id}')">✕</button></div>`).join('');
}

// ── BUDGET ──
function toggleBudgetEmoji(){document.getElementById('budgetEmojiPanel').classList.toggle('open');}
function pickBudgetEmoji(e){S.budgetEmoji=e;document.getElementById('budgetEmojiPick').textContent=e;document.getElementById('budgetEmojiPanel').classList.remove('open');}
function addBudget(){
  const name=document.getElementById('budgetName').value.trim();
  const amount=parseFloat(document.getElementById('budgetAmount').value);
  if(!name||!amount||amount<=0){toast('請填寫名稱和金額！');return;}
  S.budgets.push({id:Date.now().toString(),name,amount,emoji:S.budgetEmoji});
  save(); document.getElementById('budgetName').value=''; document.getElementById('budgetAmount').value='';
  renderBudgets(); toast(S.budgetEmoji+' '+name+' 預算已設定！');
}
function deleteBudget(id){S.budgets=S.budgets.filter(b=>b.id!==id);save();renderBudgets();toast('預算已刪除 👋');}
function renderBudgets(){
  const {currentYear:Y,currentMonth:M}=S;
  const mTxs=S.transactions.filter(t=>t.year===Y&&t.month===M&&t.type==='expense');
  const list=document.getElementById('budgetList');
  if(!S.budgets.length){list.innerHTML=`<div class="empty-state" style="padding:20px"><span class="e">🎯</span><p>還沒有預算設定</p></div>`;return;}
  list.innerHTML=S.budgets.map(b=>{
    const spent=mTxs.filter(t=>t.desc.includes(b.name)||t.cat===b.emoji).reduce((s,t)=>s+t.amount,0);
    const pct=Math.min(100,Math.round((spent/b.amount)*100));
    const cls=pct>=100?'over':pct>=80?'warn':'ok';
    const color=pct>=100?'var(--red)':pct>=80?'var(--orange)':'var(--teal)';
    return `<div class="budget-item">
      <div class="budget-header">
        <span class="budget-cat">${b.emoji}</span>
        <span class="budget-name">${b.name}</span>
        <span class="budget-nums" style="color:${color}">$${spent.toLocaleString()} / $${b.amount.toLocaleString()}</span>
        <button class="budget-del" onclick="deleteBudget('${b.id}')">✕</button>
      </div>
      <div class="budget-bar-bg"><div class="budget-bar-fill ${cls}" style="width:${pct}%"></div></div>
      <div style="display:flex;justify-content:space-between;margin-top:4px;">
        <span style="font-size:10px;font-weight:800;color:#8B5A3A;">${pct>=100?'⚠️ 超支！':pct>=80?'⚡ 快到上限':''}</span>
        <span style="font-size:10px;font-weight:900;color:${color};">${pct}%</span>
      </div>
    </div>`;
  }).join('');
}

// ── SAVINGS GOALS ──
function toggleGoalEmoji(){document.getElementById('goalEmojiPanel').classList.toggle('open');}
function pickGoalEmoji(e){S.goalEmoji=e;document.getElementById('goalEmojiPick').textContent=e;document.getElementById('goalEmojiPanel').classList.remove('open');}
function addGoal(){
  const name=document.getElementById('goalName').value.trim();
  const target=parseFloat(document.getElementById('goalTarget').value);
  if(!name||!target||target<=0){toast('請填寫目標名稱和金額！');return;}
  S.goals.push({id:Date.now().toString(),name,target,saved:0,emoji:S.goalEmoji});
  save(); document.getElementById('goalName').value=''; document.getElementById('goalTarget').value='';
  renderGoals(); toast(S.goalEmoji+' '+name+' 目標建立！');
}
function openDeposit(id){S.activeGoalId=id;document.getElementById('depositAmount').value='';document.getElementById('depositModal').classList.add('open');}
function closeDeposit(){document.getElementById('depositModal').classList.remove('open');S.activeGoalId=null;}
function confirmDeposit(){
  const v=parseFloat(document.getElementById('depositAmount').value);
  if(!v||v<=0){toast('請輸入金額！');return;}
  const g=S.goals.find(g=>g.id===S.activeGoalId);
  if(!g) return;
  g.saved=Math.min(g.target,g.saved+v);
  save(); renderGoals(); closeDeposit();
  toast(g.emoji+' 已存入 $'+v.toLocaleString()+'！');
}
function deleteGoal(id){S.goals=S.goals.filter(g=>g.id!==id);save();renderGoals();toast('目標已刪除 👋');}
function renderGoals(){
  const list=document.getElementById('goalList');
  if(!S.goals.length){list.innerHTML=`<div class="empty-state" style="padding:20px"><span class="e">🏆</span><p>還沒有存錢目標</p></div>`;return;}
  list.innerHTML=S.goals.map(g=>{
    const pct=Math.round((g.saved/g.target)*100);
    const done=pct>=100;
    return `<div class="goal-item">
      <div class="goal-header">
        <div class="goal-icon">${g.emoji}</div>
        <div class="goal-info">
          <div class="goal-name">${g.name}</div>
          <div class="goal-nums">NT$ ${g.saved.toLocaleString()} / ${g.target.toLocaleString()}</div>
        </div>
        <div class="goal-pct">${pct}%</div>
        <button class="goal-del" onclick="deleteGoal('${g.id}')">✕</button>
      </div>
      <div class="goal-bar-bg"><div class="goal-bar-fill${done?' done':''}" style="width:${pct}%"></div></div>
      <div style="display:flex;justify-content:space-between;align-items:center;">
        ${done?'<span class="goal-done-badge">🎉 達成！</span>':'<button class="goal-add-btn" onclick="openDeposit(\''+g.id+'\')">＋ 存入</button>'}
        <span style="font-size:11px;font-weight:800;color:#8B5A3A;">還差 NT$ ${Math.max(0,g.target-g.saved).toLocaleString()}</span>
      </div>
    </div>`;
  }).join('');
}

// ── CUSTOM CATEGORIES ──
function toggleCcatEmoji(){document.getElementById('ccatEmojiPanel').classList.toggle('open');}
function pickCcatEmoji(e){S.ccatEmoji=e;document.getElementById('ccatEmojiPick').textContent=e;document.getElementById('ccatEmojiPanel').classList.remove('open');}
function addCustomCat(){
  const name=document.getElementById('ccatName').value.trim();
  if(!name){toast('請輸入分類名稱！');return;}
  if(S.customCats.length>=8){toast('最多 8 個自訂分類');return;}
  S.customCats.push({emoji:S.ccatEmoji,name});
  save(); document.getElementById('ccatName').value='';
  renderCustomCats(); rebuildCatGrid(); toast(S.ccatEmoji+' '+name+' 分類已加入！');
}
function deleteCustomCat(idx){S.customCats.splice(idx,1);save();renderCustomCats();rebuildCatGrid();}
function renderCustomCats(){
  const g=document.getElementById('customCatsGrid');
  if(!S.customCats.length){g.innerHTML='<div style="grid-column:1/-1;text-align:center;color:rgba(255,245,224,.3);font-size:12px;font-weight:800;padding:12px;">還沒有自訂分類</div>';return;}
  g.innerHTML=S.customCats.map((c,i)=>`
    <div class="ccat-chip">
      <button class="ccat-del" onclick="deleteCustomCat(${i})">✕</button>
      <span class="ccat-emoji">${c.emoji}</span>
      <span class="ccat-label">${c.name}</span>
    </div>`).join('');
}
function rebuildCatGrid(){
  const allExpense=[...DEFAULT_EXPENSE_CATS,...S.customCats.map(c=>c.emoji)];
  const allIncome=[...DEFAULT_INCOME_CATS,...S.customCats.map(c=>c.emoji)];
  const cats=S.selType==='income'?allIncome:allExpense;
  const grid=document.getElementById('catGrid');
  grid.innerHTML=cats.map((c,i)=>`
    <button class="cat-btn${i===0?' active':''}" data-cat="${c}" onclick="selectCat(this)">${c}</button>`).join('');
  S.selCat=cats[0];
}

// ── TRANSACTIONS ──
function setType(type){
  S.selType=type;
  document.getElementById('incomeBtn').className='type-btn ib'+(type==='income'?' active':'');
  document.getElementById('expenseBtn').className='type-btn eb'+(type==='expense'?' active':'');
  rebuildCatGrid();
}
function selectCat(btn){document.querySelectorAll('.cat-btn').forEach(b=>b.classList.remove('active'));btn.classList.add('active');S.selCat=btn.dataset.cat;}
function addTransaction(){
  const amount=parseFloat(document.getElementById('amountInput').value);
  const desc=document.getElementById('descInput').value.trim()||'未命名';
  if(!amount||amount<=0){toast('請輸入金額！');return;}
  const dateVal=document.getElementById('txDateInput').value;
  let year,month,day,dateStr;
  if(dateVal){
    const d=new Date(dateVal+'T12:00:00');
    year=d.getFullYear(); month=d.getMonth()+1; day=d.getDate();
    dateStr=fmt(year,month,day);
  } else {
    const now=new Date();
    year=now.getFullYear(); month=now.getMonth()+1; day=now.getDate();
    dateStr=fmt(year,month,day);
  }
  S.transactions.unshift({id:Date.now().toString(),type:S.selType,amount,desc,cat:S.selCat,
    date:dateStr,year,month,ts:Date.now()});
  save(); document.getElementById('amountInput').value=''; document.getElementById('descInput').value='';
  render(); toast(S.selType==='income'?'收入入帳！💰':'支出記錄！🧾'); switchTab('home');
}
function deleteTx(id){S.transactions=S.transactions.filter(t=>t.id!==id);save();render();toast('已刪除 👋');}

// ── CHARTS ──
function renderCharts(){
  const {currentYear:Y,currentMonth:M}=S;
  const mTxs=S.transactions.filter(t=>t.year===Y&&t.month===M&&t.type==='expense'&&!t.isSub);
  // Donut
  const catMap={};
  mTxs.forEach(t=>{catMap[t.cat]=(catMap[t.cat]||0)+t.amount;});
  const subTotalMonth=S.transactions.filter(t=>t.year===Y&&t.month===M&&t.isSub).reduce((s,t)=>s+t.amount,0);
  if(subTotalMonth>0) catMap['📡訂閱']=(catMap['📡訂閱']||0)+subTotalMonth;
  const entries=Object.entries(catMap).sort((a,b)=>b[1]-a[1]);
  const total=entries.reduce((s,[,v])=>s+v,0);
  const svg=document.getElementById('donutSvg');
  const legend=document.getElementById('donutLegend');
  if(!total){
    svg.innerHTML='<text x="60" y="65" text-anchor="middle" font-size="11" fill="rgba(61,28,2,.4)" font-family="Nunito" font-weight="800">本月無支出</text>';
    legend.innerHTML='';
  } else {
    let angle=-90,paths='';
    const top=entries.slice(0,6);
    top.forEach(([cat,val],i)=>{
      const pct=val/total;
      const a=pct*360;
      const r=45,cx=60,cy=60;
      const start=angle,end=angle+a;
      const x1=cx+r*Math.cos(start*Math.PI/180), y1=cy+r*Math.sin(start*Math.PI/180);
      const x2=cx+r*Math.cos(end*Math.PI/180),   y2=cy+r*Math.sin(end*Math.PI/180);
      const large=a>180?1:0;
      paths+=`<path d="M${cx},${cy} L${x1},${y1} A${r},${r} 0 ${large},1 ${x2},${y2} Z" fill="${CAT_COLORS[i]}" stroke="#FFF5E0" stroke-width="1.5"/>`;
      angle+=a;
    });
    // donut hole
    paths+=`<circle cx="60" cy="60" r="24" fill="rgba(255,245,224,.95)"/>`;
    paths+=`<text x="60" y="55" text-anchor="middle" font-size="9" fill="rgba(61,28,2,.55)" font-family="Nunito" font-weight="800">支出</text>`;
    paths+=`<text x="60" y="67" text-anchor="middle" font-size="11" fill="#3D1C02" font-family="Bangers" letter-spacing="1">$${(total/1000).toFixed(1)}K</text>`;
    svg.innerHTML=paths;
    legend.innerHTML=top.map(([cat,val],i)=>`
      <div class="legend-item">
        <div class="legend-dot" style="background:${CAT_COLORS[i]}"></div>
        <div class="legend-label">${cat}</div>
        <div class="legend-pct">${Math.round(val/total*100)}%</div>
      </div>`).join('');
  }
  // Bar chart – last 6 months
  const bars=document.getElementById('barChartBars');
  const months=[];
  for(let i=5;i>=0;i--){let m=M-i,y=Y;if(m<=0){m+=12;y--;}months.push({y,m});}
  const maxVal=Math.max(1,...months.flatMap(({y,m})=>{
    const inc=S.transactions.filter(t=>t.year===y&&t.month===m&&t.type==='income').reduce((s,t)=>s+t.amount,0);
    const exp=S.transactions.filter(t=>t.year===y&&t.month===m&&t.type==='expense').reduce((s,t)=>s+t.amount,0);
    return[inc,exp];
  }));
  const MNAMES=['1月','2月','3月','4月','5月','6月','7月','8月','9月','10月','11月','12月'];
  bars.innerHTML=months.map(({y,m})=>{
    const inc=S.transactions.filter(t=>t.year===y&&t.month===m&&t.type==='income').reduce((s,t)=>s+t.amount,0);
    const exp=S.transactions.filter(t=>t.year===y&&t.month===m&&t.type==='expense').reduce((s,t)=>s+t.amount,0);
    const ih=Math.round((inc/maxVal)*72), eh=Math.round((exp/maxVal)*72);
    const isMth=y===Y&&m===M;
    return `<div class="bar-col" style="${isMth?'opacity:1':'opacity:.6'}">
      <div style="display:flex;align-items:flex-end;gap:2px;height:72px;">
        <div class="bar-fill income-bar" style="width:14px;height:${ih}px;"></div>
        <div class="bar-fill expense-bar" style="width:14px;height:${eh}px;"></div>
      </div>
      <div class="bar-month">${MNAMES[m-1]}</div>
    </div>`;
  }).join('');
}

// ── MAIN RENDER ──
function render(){
  const {currentYear:Y,currentMonth:M}=S;
  const mTxs   =S.transactions.filter(t=>t.year===Y&&t.month===M);
  const allInc =S.transactions.filter(t=>t.type==='income').reduce((s,t)=>s+t.amount,0);
  const allExp =S.transactions.filter(t=>t.type==='expense').reduce((s,t)=>s+t.amount,0);
  const mInc   =mTxs.filter(t=>t.type==='income').reduce((s,t)=>s+t.amount,0);
  const mExp   =mTxs.filter(t=>t.type==='expense').reduce((s,t)=>s+t.amount,0);
  const mSub   =mTxs.filter(t=>t.isSub).reduce((s,t)=>s+t.amount,0);
  const balance=S.initialBalance+allInc-allExp;

  document.getElementById('monthLabel').textContent=Y+' / '+String(M).padStart(2,'0');
  document.getElementById('balanceDisplay').textContent=balance.toLocaleString();
  document.getElementById('incomeTag').textContent='＋ $'+mInc.toLocaleString();
  document.getElementById('expenseTag').textContent='－ $'+mExp.toLocaleString();
  document.getElementById('subTag').textContent='📡 $'+mSub.toLocaleString();
  document.getElementById('statIncome').textContent='$'+mInc.toLocaleString();
  document.getElementById('statExpense').textContent='$'+mExp.toLocaleString();
  document.getElementById('statSub').textContent='$'+mSub.toLocaleString();

  const pct=S.salary?Math.round(Math.min(100,(mExp/S.salary)*100)):0;
  document.getElementById('progressFill').style.width=pct+'%';
  document.getElementById('progressPct').textContent=pct+'%';

  if(S.salary) document.getElementById('salaryInfo').textContent=`月薪 NT$ ${S.salary.toLocaleString()} ✅`;
  if(S.initialBalance!==0) document.getElementById('initInfo').textContent=`起始餘額 NT$ ${S.initialBalance.toLocaleString()} ✅`;

  document.getElementById('txCount').textContent=mTxs.length?`(${mTxs.length} 筆)`:'';
  const list=document.getElementById('txList');
  if(!mTxs.length){list.innerHTML=`<div class="empty-state"><span class="e">💀</span><p>這個月還沒有紀錄<br>點 ➕ 記帳新增吧！</p></div>`;return;}
  list.innerHTML=mTxs.map((tx,i)=>`
    <div class="tx-item ${tx.isSalary?'salary':''} ${tx.isSub?'is-sub':''}" style="animation-delay:${i*0.025}s">
      <div class="tx-emoji">${tx.cat}</div>
      <div class="tx-info"><div class="tx-desc">${tx.desc}</div><div class="tx-date">${tx.date}</div></div>
      <div class="tx-amount ${tx.isSub?'sub-amt':tx.type}">${tx.type==='income'?'+':'-'} $${tx.amount.toLocaleString()}</div>
      ${(!tx.isSalary&&!tx.isSub)?`<button class="tx-del" onclick="deleteTx('${tx.id}')">✕</button>`:''}
    </div>`).join('');
}

function changeMonth(dir){
  S.currentMonth+=dir;
  if(S.currentMonth>12){S.currentMonth=1;S.currentYear++;}
  if(S.currentMonth<1){S.currentMonth=12;S.currentYear--;}
  render();
}

// ── TAB ──
function switchTab(tab){
  document.querySelectorAll('.view').forEach(v=>v.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(b=>b.classList.remove('active'));
  document.getElementById('view-'+tab).classList.add('active');
  document.getElementById('nav-'+tab).classList.add('active');
  document.getElementById('appBody').scrollTop=0;
  if(tab==='sub') renderSubs();
  if(tab==='charts') renderCharts();
  if(tab==='budget'){renderBudgets();renderGoals();}
  if(tab==='settings') renderCustomCats();
}

// ── TOAST ──
function toast(msg){
  const t=document.getElementById('toast');
  t.textContent=msg; t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'),2100);
}

// ── INIT DATE INPUT ──
function initDateInput(){
  const now=new Date();
  document.getElementById('txDateInput').value=now.getFullYear()+'-'+String(now.getMonth()+1).padStart(2,'0')+'-'+String(now.getDate()).padStart(2,'0');
}

// ── CLOSE MODAL ON BG TAP ──
document.getElementById('depositModal').addEventListener('click',function(e){if(e.target===this) closeDeposit();});

load(); render(); renderSubs(); renderCustomCats(); rebuildCatGrid(); initDateInput();
</script>

</body>
</html>
