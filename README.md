<!doctype html>
<html lang="ja">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>繝悶Ο繝�け繝代ぜ繝ｫ</title>
<style>
:root{--bg:#f2eefc;--board:#d9d2f3;--cell:#e9e4f9;--ink:#2a2352;--sub:#7a72a8;--c0:#ff5d73;--c1:#ffb23e;--c2:#2fcf8e;--c3:#4aa8ff;--c4:#a46bff;--c5:#ff7ad9;--sh:inset 0 -4px 0 rgba(0,0,0,.22),inset 0 2px 0 rgba(255,255,255,.45),inset 0 0 0 1.5px rgba(255,255,255,.22);--gl:radial-gradient(circle at 28% 22%,rgba(255,255,255,.7) 0,rgba(255,255,255,0) 34%),linear-gradient(145deg,rgba(255,255,255,.3),rgba(255,255,255,0) 50%,rgba(0,0,0,.22));box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#14122b;--board:#231f4a;--cell:#302b63;--ink:#f1eeff;--sub:#9a93d1;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#14122b;--board:#231f4a;--cell:#302b63;--ink:#f1eeff;--sub:#9a93d1;color-scheme:dark}
html,body{height:100%}
body{margin:0;background:var(--bg);color:var(--ink);font-family:"M PLUS Rounded 1c","Hiragino Maru Gothic ProN","Yu Gothic",system-ui,sans-serif;display:flex;justify-content:center;touch-action:none;user-select:none;-webkit-user-select:none;-webkit-font-smoothing:antialiased;overscroll-behavior:none;overflow:hidden}
.app{width:min(94vw,420px);display:flex;flex-direction:column;justify-content:center;gap:18px}
.top{display:flex;justify-content:space-between;align-items:flex-end}
.lbl{font-size:12px;color:var(--sub);font-weight:700}
#score{font-size:46px;font-weight:800;line-height:1;font-variant-numeric:tabular-nums}
.best{text-align:right}
#best{font-size:22px;font-weight:800;font-variant-numeric:tabular-nums}
#board{contain:layout style paint;display:grid;grid-template-columns:repeat(8,minmax(0,1fr));grid-template-rows:repeat(8,minmax(0,1fr));gap:3px;padding:6px;background:var(--board);border-radius:16px;aspect-ratio:1}
.cell{background:var(--cell);border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:calc(var(--cs,40px)*.55);line-height:1}
.cell.f{box-shadow:var(--sh)}
.cell.bm{animation:tick 1.6s ease-in-out 4}@keyframes tick{50%{transform:scale(1.07)}}
.cell.gh{opacity:.55}
.cell.hl{opacity:1;box-shadow:inset 0 0 0 40px rgba(255,255,255,.22),0 0 10px 2px rgba(255,255,255,.75)}
.cell.drop{animation:drop .46s cubic-bezier(.2,.9,.3,1)}
html[data-fx="2"] .cell.drop{animation:drop2 .5s cubic-bezier(.2,.9,.3,1)}
@keyframes drop2{0%{transform:scale(.7)}45%{transform:scale(1.22)}70%{transform:scale(.94)}100%{transform:scale(1)}}
@keyframes drop{0%{transform:scale(.85)}55%{transform:scale(1.1)}100%{transform:scale(1)}}
#tray{display:grid;grid-template-columns:repeat(3,1fr);gap:8px}
.slot{display:flex;justify-content:center;align-items:center;min-height:92px;touch-action:none;cursor:grab}
.blk{box-shadow:var(--sh)}
#drag{position:fixed;left:0;top:0;pointer-events:none;z-index:5}
#drag .blk{box-shadow:var(--sh),0 6px 4px rgba(0,0,0,.22)}
#over{position:fixed;inset:0;background:rgba(20,18,43,.78);display:none;flex-direction:column;align-items:center;justify-content:center;gap:12px;color:#fff;z-index:9}
#over.on{display:flex;animation:fade .4s}@keyframes fade{from{opacity:0}}
#over h2{margin:0;font-size:30px}
#over .big{font-size:56px;font-weight:800}
button{font:inherit;font-weight:800;font-size:18px;border:0;border-radius:14px;padding:12px 30px;background:var(--c4);color:#fff;cursor:pointer}
#snd{position:fixed;top:calc(env(safe-area-inset-top,0px) + 6px);right:8px;z-index:8;background:none;padding:6px 8px;font-size:20px;border-radius:10px}
html[data-tex="1"]{--gl:linear-gradient(rgba(255,255,255,.1),rgba(255,255,255,.1));--sh:0 0 0 0 transparent}
html[data-tex="1"] .cell{border-radius:4px}
html[data-tex="2"]{--gl:radial-gradient(circle at 30% 25%,#fff 0,rgba(255,255,255,.55) 14%,rgba(255,255,255,0) 40%),radial-gradient(circle at 50% 115%,rgba(0,0,0,.32),rgba(0,0,0,0) 60%);--sh:0 0 0 0 transparent}
html[data-tex="2"] .cell,html[data-tex="2"] .blk{border-radius:50%!important}
html[data-tex="3"]{--gl:linear-gradient(rgba(10,8,30,.55),rgba(10,8,30,.55));--sh:inset 0 0 0 2px rgba(255,255,255,.7),0 0 6px rgba(255,255,255,.35)}
html[data-tex="4"]{--gl:linear-gradient(135deg,rgba(255,255,255,.22),rgba(255,255,255,0) 45%,rgba(0,0,0,.12));--sh:inset 0 0 0 2px rgba(255,255,255,.38),inset 0 -3px 0 rgba(0,0,0,.25)}
html[data-tex="4"] .cell{border-radius:6px}
html[data-tex="5"]{--c0:#e2573a;--c1:#e8693e;--c2:#d94a30;--c3:#ee7747;--c4:#e05d3b;--c5:#ea6f45;--sh:inset 0 -3px 0 rgba(0,0,0,.2),inset 0 0 0 1.5px rgba(255,255,255,.18);--gl:linear-gradient(rgba(255,236,214,.6),rgba(255,236,214,.6)),linear-gradient(rgba(255,236,214,.6),rgba(255,236,214,.6)),linear-gradient(rgba(255,236,214,.6),rgba(255,236,214,.6)),linear-gradient(160deg,rgba(255,255,255,.2),rgba(0,0,0,.15))}
html[data-tex="5"] .cell.f,html[data-tex="5"] .blk{background-size:100% 7%,7% 50%,7% 50%,100% 100%!important;background-position:0 50%,35% 0,65% 100%,0 0!important;background-repeat:no-repeat!important}
html[data-tex="5"] .cell{border-radius:6px;background:#22345a}
html[data-tex="5"] .blk{border-radius:6px!important}
html[data-tex="5"] #board{background:#2d4272;border-radius:12px}
html[data-tex="5"] body{background:linear-gradient(#7fb6e6,#b7d7f1);color:#1d3557}
html[data-tex="5"] #menu{background:#9cc9ee}
html[data-tex="5"] .top{flex-direction:column;align-items:stretch;gap:2px}
html[data-tex="5"] .best{order:-1;text-align:left;color:#f2b21d}
html[data-tex="5"] .best::before{content:"荘 "}
html[data-tex="5"] .lbl{display:none}
html[data-tex="5"] .top>div:first-child{text-align:center}
html[data-tex="5"] #score{font-size:56px;color:#fff;text-shadow:0 3px 0 rgba(30,60,110,.25)}
#score{position:relative;z-index:1}
html[data-tex="6"]{--gl:linear-gradient(rgba(10,8,34,.8),rgba(10,8,34,.8));--sh:0 0 4px currentColor,inset 0 0 5px currentColor}
html[data-tex="6"] .cell.f,html[data-tex="6"] .blk{border:3px solid transparent!important;background-origin:border-box!important;background-clip:padding-box,border-box!important}
html[data-tex="6"] .cell{border-radius:7px;background:#232150}
html[data-tex="6"] .blk{border-radius:7px!important}
html[data-tex="6"] #board{background:#171540}
html[data-tex="6"] body{background:#0f0d2e;color:#e8e6ff}
html[data-tex="6"] #menu{background:#0f0d2e}
html[data-tex="6"] #score{color:#fff}
html[data-tex="7"]{--gl:linear-gradient(rgba(255,255,255,.88),rgba(255,255,255,.88));--sh:0 0 4px currentColor,inset 0 0 5px currentColor}
html[data-tex="7"] .cell.f,html[data-tex="7"] .blk{border:3px solid transparent!important;background-origin:border-box!important;background-clip:padding-box,border-box!important}
html[data-tex="7"] .cell{border-radius:7px;background:#e3e7fb}
html[data-tex="7"] .blk{border-radius:7px!important}
html[data-tex="7"] #board{background:#f4f6ff}
html[data-tex="7"] body{background:#eef1ff;color:#1c2040}
html[data-tex="7"] #menu{background:#eef1ff}
html[data-tex="7"] .lbl{color:#6b73a8}
html[data-fx="1"] .cell.bm{animation-iteration-count:3}
html[data-fx="0"] .cell.bm{animation:none}
#menu{position:fixed;inset:0;z-index:10;display:none;flex-direction:column;align-items:center;justify-content:center;gap:12px;background:var(--bg);padding:20px;overflow:auto}
#menu.on{display:flex}
#menu h1{margin:0;font-size:32px}
#menu button.m{width:min(260px,80vw)}
#menu button.sub,.seg button{background:var(--board);color:var(--ink)}
#sets{display:none;width:min(360px,92vw);flex-direction:column;gap:10px}
#sets.on{display:flex}
.row{display:flex;justify-content:space-between;align-items:center;gap:8px;font-weight:800;font-size:14px}
.seg{display:flex;gap:4px;flex-wrap:wrap;justify-content:flex-end}
.seg button{font-size:13px;padding:7px 10px;border-radius:10px}
.seg button.on{background:var(--c4);color:#fff}
#prev{display:flex;gap:6px;justify-content:center}
#board.cb{box-shadow:0 0 0 3px var(--cc),0 0 16px var(--cc)}
.cell.nb{animation:nudge .4s ease-out backwards}@keyframes nudge{40%{transform:scale(.9)}100%{transform:scale(1)}}
html[data-rq="2"] .cell.f:not(.hl),html[data-rq="2"] .blk{box-shadow:var(--sh),0 2px 3px rgba(0,0,0,.28)}
html[data-rq="2"] #board:not(.cb){box-shadow:inset 0 2px 6px rgba(0,0,0,.25),0 6px 18px rgba(0,0,0,.2)}
html[data-rq="0"] .cell.f:not(.hl),html[data-rq="0"] .blk,html[data-rq="0"] #drag .blk{box-shadow:none!important}
html[data-rq="0"] .cell{transition:none}
html[data-rq="0"][data-tex="0"]{--gl:linear-gradient(rgba(255,255,255,.18),rgba(255,255,255,0) 60%)}
@media (prefers-reduced-motion:reduce){.cell.drop,.cell.bm{animation:none}}
</style>
</head>
<body>
<div class="app">
  <div class="top">
    <div><div class="lbl">繧ｹ繧ｳ繧｢</div><div id="score">0</div></div>
    <div class="best"><div class="lbl">繝吶せ繝�</div><div id="best">0</div></div>
  </div>
  <div id="board"></div>
  <div id="tray"><div class="slot"></div><div class="slot"></div><div class="slot"></div></div>
</div>
<button id="snd" aria-label="繝｡繝九Η繝ｼ">笘ｰ</button>
<div id="menu"><h1>ｧｩ 繝悶Ο繝�け繝代ぜ繝ｫ</h1><div class="lbl">繝吶せ繝� <b id="mb">0</b></div><div id="prev"></div><div id="sets"></div><button class="m" id="play">縺ゅ◎縺ｶ</button><button class="m sub" id="setb">縺帙▲縺ｦ縺�</button><button class="m sub" id="rst">縺ｯ縺倥ａ縺九ｉ</button></div>
<div id="over"><h2>繧ｲ繝ｼ繝�繧ｪ繝ｼ繝舌�</h2><div class="big" id="fin">0</div><div id="nb"></div><button id="again">繧ゅ≧荳蠎ｦ</button></div>
<script>
const N=8,OFF=80;
const SH=[[[0,0]],[[0,0],[0,1]],[[0,0],[1,0]],[[0,0],[0,1],[0,2]],[[0,0],[1,0],[2,0]],[[0,0],[0,1],[0,2],[0,3]],[[0,0],[1,0],[2,0],[3,0]],[[0,0],[0,1],[1,0],[1,1]],[[0,0],[0,1],[0,2],[1,0],[1,1],[1,2],[2,0],[2,1],[2,2]],[[0,0],[0,1],[0,2],[1,0],[1,1],[1,2]],[[0,0],[1,0],[1,1]],[[0,0],[0,1],[1,0]],[[0,1],[1,0],[1,1]],[[0,0],[0,1],[1,1]],[[0,0],[1,0],[2,0],[2,1]],[[0,1],[1,1],[2,1],[2,0]],[[0,0],[0,1],[0,2],[1,0]],[[0,0],[0,1],[0,2],[1,2]],[[0,0],[0,1],[0,2],[1,1]],[[0,0],[1,0],[2,0],[0,1],[0,2]],[[0,0],[0,1],[0,2],[0,3],[0,4]],[[0,0],[1,0],[2,0],[3,0],[4,0]],[[0,0],[0,1],[1,0],[1,1],[2,0],[2,1]],[[0,0],[1,0],[2,0],[2,1],[2,2]],[[0,2],[1,2],[2,0],[2,1],[2,2]],[[0,0],[0,1],[0,2],[1,2],[2,2]],[[0,0],[1,0],[2,0],[1,1]],[[0,1],[1,1],[2,1],[1,0]],[[0,0],[0,1],[1,1],[1,2]],[[0,1],[0,2],[1,0],[1,1]],[[0,0],[1,0],[1,1],[2,1]],[[0,1],[1,0],[1,1],[2,0]],[[0,0],[1,0],[2,0],[0,1]],[[0,0],[0,1],[1,1],[2,1]],[[0,0],[1,0],[1,1],[1,2]],[[0,2],[1,0],[1,1],[1,2]],[[0,1],[1,0],[1,1],[1,2],[2,1]],[[0,0],[1,1]],[[0,1],[1,0]]];
const $=s=>document.querySelector(s);
const board=$('#board'),slots=[...document.querySelectorAll('.slot')];
const cells=[];for(let i=0;i<64;i++){const d=document.createElement('div');d.className='cell';board.appendChild(d);cells.push(d)}
let miss=0,g,gb,pieces,score,best=0,combo,drag=null,shown,fresh,AC,snd=true,gkey='',gcells=[],hcells=[];
const RMq=matchMedia('(prefers-reduced-motion:reduce)').matches;let RM=RMq,AT,live=0,BG,BM,bgN=0,bgS=0;
try{best=+localStorage.getItem('bp-best')||0}catch(e){}
let S={snd:1,sf:5,bgm:0,dr:2,rq:1,fp:1,fc:1,vib:1,tex:5,fx:2,th:0};try{Object.assign(S,JSON.parse(localStorage.getItem('bp-set2')||'{}'))}catch(e){}if(S.fl===undefined)S.fl=S.fx+1;snd=!!S.snd;
/* audio / haptics */
function ac(){if(!AC){try{AC=new(window.AudioContext||window.webkitAudioContext)()}catch(e){}}if(AC&&AC.state==='suspended')AC.resume();clearTimeout(AT);if(!BG)AT=setTimeout(()=>{if(AC)AC.suspend()},5000);return AC}
function tone(f,d,type,v,t0,f2){if(!snd||(S.fx<2&&v<.06))return;const a=ac();if(!a)return;const t=a.currentTime+(t0||0),o=a.createOscillator(),gn=a.createGain();const q=S.sf|0,m=q===3?2:1;d=q===3?d*1.6:d;o.type=q===6?type||'sine':q===1&&type!=='sine'?'square':q>1?'sine':type||'sine';o.frequency.setValueAtTime(f*m,t);if(f2)o.frequency.exponentialRampToValueAtTime(f2*m,t+d);gn.gain.setValueAtTime((v||.15)*(q===1?.6:1),t);gn.gain.exponentialRampToValueAtTime(.001,t+d);o.connect(gn);gn.connect(a.destination);o.start(t);o.stop(t+d)}
function buzz(p){if(S.vib&&navigator.vibrate){try{navigator.vibrate(p)}catch(e){}}}
let NB;function noise(d,v,t0){if(!snd)return;const a=ac();if(!a)return;if(!NB){NB=a.createBuffer(1,a.sampleRate,a.sampleRate);const x=NB.getChannelData(0);for(let i=0;i<x.length;i++)x[i]=Math.random()*2-1}const t=a.currentTime+(t0||0),s=a.createBufferSource(),gn=a.createGain();s.buffer=NB;gn.gain.setValueAtTime(v,t);gn.gain.linearRampToValueAtTime(0,t+d);s.connect(gn);gn.connect(a.destination);s.start(t);s.stop(t+d)}
function bn(f,ty,t,d,v,f2){const a=AC;if(!BM){BM=a.createGain();BM.gain.value=.55;BM.connect(a.destination)}const o=a.createOscillator(),g=a.createGain();o.type=ty;o.frequency.setValueAtTime(f,t);if(f2)o.frequency.exponentialRampToValueAtTime(f2,t+d);g.gain.setValueAtTime(v,t);g.gain.exponentialRampToValueAtTime(.001,t+d);o.connect(g);g.connect(BM);o.start(t);o.stop(t+d+.02)}
function bgm(on){clearInterval(BG);BG=null;if(!on)return;if(!ac())return;bgN=AC.currentTime+.1;bgS=0;BG=setInterval(bgTick,250);bgTick()}
function bgTick(){const a=AC;if(!a||!S.bgm||!snd)return;if(a.state==='suspended')a.resume();while(bgN<a.currentTime+.7){bgStep(bgN,bgS++);bgN+=60/118/4}}
function bgStep(t,k){const s=k%16,r=[55,43.65,49,55][(k>>4)%4],d=Math.max(0,t-AC.currentTime);
 if(s%4===0)bn(150,'sine',t,.14,.4,45);
 if(s===4||s===12)noise(.1,.1,d);
 if(s%2===1)noise(.03,.04,d);
 if([0,3,6,10,12,14].includes(s))bn(r*(s===6||s===14?2:1),'sawtooth',t,.2,.09);
 if(s%2===0)bn(r*8*Math.pow(2,[0,7,12,7,3,10,15,10][(s>>1)%8]/12),'square',t,.12,.03)}
const SFX={
 pick(){tone(520,.07,'triangle',.1);buzz(8)},
 drop(){if(S.sf===6){tone(900,.08,'square',.12,0,150);tone(110,.12,'sawtooth',.2,0,55);noise(.03,.1);buzz(15);return}if(S.sf===5){tone(357,.06,'triangle',.35,0,230);tone(570,.03,'sine',.12,0,400);noise(.04,.18);buzz(15);return}if(S.sf===4){tone(330,.09,'sine',.3,0,200);tone(660,.05,'sine',.08,0,500);buzz(15);return}tone(220,.16,'sine',.34,0,60);tone(1200,.05,'square',.05,0,1800);tone(1760,.12,'triangle',.07,.03);noise(.06,.08);buzz(15)},
 boom(){noise(.6,.4);tone(120,.4,'sawtooth',.25,0,30);tone(60,.5,'sine',.3,0,25);buzz([60,30,120])},
 zap(){for(let k=0;k<6;k++)tone(1800-k*200,.07,'sawtooth',.08,k*.04,300);buzz([30,20,30,20,60])},
 bad(){tone(160,.14,'sawtooth',.07,0,100);buzz([20,40,20])},
 clear(n,cb){if(S.sf===6){const sc=[440,523,659,784,880,1047,1319],o=Math.pow(1.06,Math.min(cb-1,6));tone(200,.35,'sawtooth',.1,0,1600);noise(.25,.1);for(let k=0;k<Math.min(n*2+3,8);k++)tone(sc[k%7]*o,.12,'square',.09,.04+k*.05);buzz([25,30,25+n*15]);return}if(S.sf===5){const sc=[1047,1319,1568],o=Math.pow(1.06,Math.min(cb-1,6));noise(.3,.16);tone(161,.3,'sine',.3,0,90);for(let k=0;k<Math.min(n*2+4,10);k++){tone(sc[k%3]*o,.28,'sine',.13,.02+k*.07);tone(sc[k%3]*o*2,.12,'sine',.03,.02+k*.07)}buzz([25,30,25+n*15]);return}if(S.sf===4){const sc=[523,587,659,784,880,1047,1175,1319,1568],o=Math.min(cb-1,3);tone(250,.1,'sine',.3,0,110);for(let k=0;k<Math.min(n+2,6);k++){tone(sc[o+k],.2,'sine',.16,.03+k*.055);tone(sc[o+k]*3,.08,'sine',.04,.03+k*.055)}buzz([25,30,25+n*15]);return}const b=[523,659,784,1047,1319,1568,2093,2637],m=Math.pow(1.122,Math.min(cb-1,8)),c=Math.min(n+4,8);tone(110,.35,'sine',.4,0,40);noise(.35,.14);for(let k=0;k<c;k++){tone(b[k]*m,.25,'triangle',.16,.04+k*.045);tone(b[k]*m*2,.15,'square',.04,.05+k*.045)}if(n>1)for(let k=0;k<5;k++)tone(2093*m+k*300,.1,'sine',.07,.2+k*.04);if(cb>2){tone(b[2]*m,.5,'sawtooth',.06,.1);tone(b[4]*m,.5,'sawtooth',.05,.1)}buzz([25,30,25+n*15])},
 over(){[392,330,262,196].forEach((f,k)=>tone(f,.3,'triangle',.16,k*.16));buzz([80,50,160])}
};
/* effects */
const _cc={};const col=c=>_cc[c]||(_cc[c]=getComputedStyle(document.documentElement).getPropertyValue('--c'+c).trim());
const step=()=>cells[1].getBoundingClientRect().left-cells[0].getBoundingClientRect().left;
const rect=i=>cells[i].getBoundingClientRect();
function fx(css,fr,opt){if(S.ul)return document.createElement('i');const e=document.createElement('i');e.style.cssText='position:fixed;pointer-events:none;z-index:6;'+css;document.body.appendChild(e);e.animate(fr,opt).onfinish=()=>e.remove();return e}
function sparks(x,y,c,n,pw,dl){if(RM||live>36)return;live+=n;setTimeout(()=>live-=n,900);requestAnimationFrame(()=>{for(let k=0;k<(S.fx>1?n:n>>1);k++){const a=Math.random()*6.28,d=(.5+Math.random())*pw,s=4+Math.random()*5;fx(`left:${x-s/2}px;top:${y-s/2}px;width:${s}px;height:${s}px;border-radius:${S.tex===5?'2px':'50%'};background:${c}`,[{transform:'translate(0,0) scale(1)',opacity:1},{transform:`translate(${Math.cos(a)*d}px,${Math.sin(a)*d+18}px) scale(.1)`,opacity:0}],{duration:600+Math.random()*400,easing:'cubic-bezier(.1,.7,.3,1)',delay:dl||0,fill:'backwards'})}})}
function ring(x,y,c,s,dl){if(RM)return;fx(`left:${x-s/2}px;top:${y-s/2}px;width:${s}px;height:${s}px;border-radius:50%;border:3px solid ${c}`,[{transform:'scale(.2)',opacity:.9},{transform:'scale(1.6)',opacity:0}],{duration:600,easing:'cubic-bezier(.15,.7,.25,1)',delay:dl||0,fill:'backwards'})}
function shake(n){if(RM)return;const a=Math.min(3+n*2,10);board.animate([{transform:'translate(0)'},{transform:`translate(${-a}px,${a/2}px)`},{transform:`translate(${a}px,${-a/2}px)`},{transform:`translate(${-a/2}px,0)`},{transform:'translate(0)'}],{duration:400,easing:'ease-out'})}
function popup(t,big){if(S.ul)return;const b=board.getBoundingClientRect();const e=fx(`left:${b.left}px;top:${b.top+b.height/2-30}px;width:${b.width}px;text-align:center;font-style:normal;font-weight:800;font-size:${big?44:32}px;color:#fff;text-shadow:0 3px 0 var(--c4),0 0 18px var(--c4);z-index:7`,[{transform:'scale(.4)',opacity:0},{transform:'scale(1.2)',opacity:1,offset:.25},{transform:'scale(1) translateY(-10px)',opacity:1,offset:.7},{transform:'scale(1) translateY(-50px)',opacity:0}],{duration:1200,easing:'cubic-bezier(.2,.8,.3,1)'});e.textContent=t}
function wave(x,y,c,s){if(RM)return;const o={easing:'cubic-bezier(.15,.7,.25,1)',fill:'backwards'},b=`left:${x-s/2}px;top:${y-s/2}px;width:${s}px;height:${s}px;border-radius:50%;`;fx(b+`border:4px solid ${c};background:radial-gradient(circle,rgba(255,255,255,.3),rgba(255,255,255,0) 65%)`,[{transform:'scale(.2)',opacity:1},{opacity:.7,offset:.4},{transform:'scale(1.9)',opacity:0}],{...o,duration:800});if(S.fx>1)fx(b+'border:2px solid #fff',[{transform:'scale(.1)',opacity:.9},{opacity:.5,offset:.45},{transform:'scale(1.4)',opacity:0}],{...o,duration:680,delay:110})}
function confetti(){if(RM||S.fx<2)return;const cs=['#ff5d73','#ffb23e','#2fcf8e','#4aa8ff','#a46bff','#ff7ad9'];for(let k=0;k<24;k++){const x=Math.random()*innerWidth,w=6+Math.random()*6;fx(`left:${x}px;top:-20px;width:${w}px;height:${w*1.6}px;background:${cs[k%6]};border-radius:2px`,[{transform:'translateY(0) rotate(0deg)',opacity:1},{transform:`translate(${(Math.random()-.5)*160}px,${innerHeight*.9}px) rotate(${360+Math.random()*540}deg)`,opacity:.9}],{duration:1400+Math.random()*900,delay:Math.random()*300,easing:'cubic-bezier(.3,.2,.6,1)',fill:'backwards'})}}
function placeFx(idx,c){if(!S.fp)return;const cc=col(c);let sx=0,sy=0;idx.forEach(k=>{const r=rect(k),x=r.left+r.width/2,y=r.top+r.height/2;sx+=x;sy+=y;sparks(x,y,cc,1,45)});wave(sx/idx.length,sy/idx.length,cc,70+idx.length*18);if(S.fx>1&&!RM)impact(idx,cc)}
function impact(idx,cc){
  const rs=idx.map(rect),L=Math.min(...rs.map(r=>r.left)),T=Math.min(...rs.map(r=>r.top)),R=Math.max(...rs.map(r=>r.right)),B=Math.max(...rs.map(r=>r.bottom));
  rs.forEach(r=>fx(`left:${r.left}px;top:${r.top}px;width:${r.width}px;height:${r.height}px;border-radius:6px;background:#fff`,[{opacity:.75},{opacity:0}],{duration:220,easing:'ease-out'}));
  [[L,B],[R,B]].forEach(([x,y],i)=>fx(`left:${x-30}px;top:${y-30}px;width:60px;height:60px;border-radius:50%;background:radial-gradient(circle,rgba(255,255,255,.6),rgba(255,255,255,0) 70%)`,[{transform:'translate(0,0) scale(.3)',opacity:.9},{transform:`translate(${i?18:-18}px,4px) scale(1.5)`,opacity:0}],{duration:480,easing:'cubic-bezier(.2,.7,.3,1)'}));
  for(let k=0;k<3;k++){const x=L+Math.random()*(R-L),y=T+Math.random()*(B-T),e=fx(`left:${x-10}px;top:${y-10}px;font-style:normal;font-size:20px;line-height:20px;color:#fff;text-shadow:0 0 6px ${cc}`,[{transform:'scale(0) rotate(0deg)',opacity:0},{transform:'scale(1.3) rotate(45deg)',opacity:1,offset:.4},{transform:'scale(0) rotate(90deg)',opacity:0}],{duration:520,delay:k*60,easing:'ease-out',fill:'backwards'});e.textContent='笨ｦ'}
  const s=new Set(idx),dm={};
  for(const k of idx){const y=k/N|0,x=k%N;for(let a=-2;a<=2;a++)for(let b=-2;b<=2;b++){const yy=y+a,xx=x+b,j=yy*N+xx;if(yy<0||yy>=N||xx<0||xx>=N||s.has(j))continue;const d=Math.abs(a)+Math.abs(b);if(d<=2&&(dm[j]===undefined||d<dm[j]))dm[j]=d}}
  const js=Object.keys(dm);js.forEach(j=>{cells[j].style.animationDelay=dm[j]*45+'ms';cells[j].classList.add('nb')});
  setTimeout(()=>js.forEach(j=>{cells[j].classList.remove('nb');cells[j].style.animationDelay=''}),650);
}
function clearFx(cl,idx,n,gain){if(!S.fc)return;
  const o=rect(idx[0]),ox=o.left,oy=o.top,st=step();
  cl.forEach(q=>{const dl=Math.hypot(q.r.left-ox,q.r.top-oy)/st*38,cc=col(q.c);
    if(!RM){const o=fx(`left:${q.r.left}px;top:${q.r.top}px;width:${q.r.width}px;height:${q.r.height}px;border-radius:6px;background:${cc}`,[{transform:'scale(1)'},{transform:'scale(1.15)',offset:.35},{transform:'scale(.1) rotate(90deg)',opacity:0}],{duration:520,delay:dl,easing:'cubic-bezier(.4,0,.6,1)',fill:'backwards'}),w=document.createElement('b');w.style.cssText='position:absolute;inset:0;border-radius:inherit;background:#fff';if(cl.length<=20){o.appendChild(w);w.animate([{opacity:0},{opacity:.75,offset:.35},{opacity:.55}],{duration:520,delay:dl,easing:'cubic-bezier(.4,0,.6,1)',fill:'backwards'})}}
    sparks(q.r.left+q.r.width/2,q.r.top+q.r.height/2,cc,cl.length>16?1:2,70,dl)});
  const cc=col(cl[0].c);ring(ox,oy,cc,200);ring(ox,oy,'#fff',120,80);
  if(!RM){const bb=board.getBoundingClientRect();fx(`left:${bb.left}px;top:${bb.top}px;width:${bb.width}px;height:${bb.height}px;border-radius:16px;box-shadow:0 0 24px 5px ${cc}`,[{opacity:0},{opacity:1,offset:.3},{opacity:0}],{duration:600});
    if(n>1||combo>1)fx('inset:0;background:#fff',[{opacity:.35},{opacity:0}],{duration:260})}
  if(combo>1&&!RM){const s=$('#score').getBoundingClientRect(),h=fx(`left:${s.left+s.width/2-45}px;top:${s.top+s.height/2-45}px;font-style:normal;font-size:90px;line-height:90px;z-index:0`,[{transform:'scale(.3)',opacity:0},{transform:'scale(1.15)',opacity:.9,offset:.3},{transform:'scale(1)',opacity:.9,offset:.8},{transform:'scale(1)',opacity:0}],{duration:1200});h.textContent=combo>3?'苧':'貯'}
  const ks=new Set(cl.map(q=>q.k)),GG=geo(),sw=[];
  for(let r=0;r<N;r++)if([...Array(N)].every((_,x)=>ks.has(r*N+x)))sw.push([GG.c.left,GG.c.top+r*GG.st,GG.st*N-3,GG.st-3,0]);
  for(let c=0;c<N;c++)if([...Array(N)].every((_,y)=>ks.has(y*N+c)))sw.push([GG.c.left+c*GG.st,GG.c.top,GG.st-3,GG.st*N-3,1]);
  if(S.fx>1&&!RM)sw.slice(0,4).forEach(([x,y,w,h,v],i)=>fx(`left:${x}px;top:${y}px;width:${v?w:w*.35}px;height:${v?h*.35:h}px;border-radius:6px;background:linear-gradient(${v?'180deg':'90deg'},rgba(255,255,255,0),rgba(255,255,255,.85),rgba(255,255,255,0))`,[{transform:v?'translateY(-100%)':'translateX(-100%)'},{transform:v?'translateY(300%)':'translateX(300%)'}],{duration:480,delay:i*60,easing:'cubic-bezier(.4,0,.2,1)',fill:'backwards'}));
  shake(n);
  popup((combo>1?combo+'繧ｳ繝ｳ繝� ':'')+['','繝翫う繧ｹ��','繧ｰ繝ｬ繝ｼ繝茨ｼ�','縺吶＃縺�ｼ�','繝代�繝輔ぉ繧ｯ繝茨ｼ�'][Math.min(n,4)]+' +'+gain,n>2||combo>2);
}
/* game */
function shapeEl(s,cp,gap,c,bi,ti){
  const mr=Math.max(...s.map(x=>x[0]))+1,mc=Math.max(...s.map(x=>x[1]))+1;
  const el=document.createElement('div');
  el.style.cssText=`display:grid;gap:${gap}px;grid-template-columns:repeat(${mc},${cp}px);grid-template-rows:repeat(${mr},${cp}px)`;
  s.forEach(([r,k],n)=>{const d=document.createElement('div');d.className='blk';if(n===bi)d.textContent=['','張','笞｡'][ti]||'張';d.style.cssText=`font-size:${cp*.65}px;display:flex;align-items:center;justify-content:center;line-height:1;color:var(--c${c});grid-row:${r+1};grid-column:${k+1};background:var(--gl),var(--c${c});border-radius:${cp*.2}px`;el.appendChild(d)});
  return{el,w:mc*cp+(mc-1)*gap,h:mr*cp+(mr-1)*gap};
}
function fits(s,r,c){return s.every(([a,b])=>{const y=r+a,x=c+b;return y>=0&&y<N&&x>=0&&x<N&&g[y*N+x]<0})}
function canAny(s){for(let r=0;r<N;r++)for(let c=0;c<N;c++)if(fits(s,r,c))return true;return false}
function lines(t){const s=new Set();let n=0;for(let k=0;k<N;k++){let r=1,c=1;for(let x=0;x<N;x++){if(t[k*N+x]<0)r=0;if(t[x*N+k]<0)c=0}if(r){n++;for(let x=0;x<N;x++)s.add(k*N+x)}if(c){n++;for(let y=0;y<N;y++)s.add(y*N+k)}}s.n=n;return s}
function draw(){
  cells.forEach((d,i)=>{const v=g[i],sg=v+'|'+gb[i];if(d._s===sg)return;d._s=sg;d.className=v>=0?(gb[i]?'cell f bm':'cell f'):'cell';d.textContent=['','張','笞｡'][gb[i]]||'';d.style.color=v>=0?`var(--c${v})`:'';d.style.background=v>=0?`var(--gl),var(--c${v})`:''});
  gkey='';gcells=[];hcells=[];hud();
}
let tw=0;
function hud(){
  board.classList.toggle('cb',combo>1&&S.fx>0);board.style.setProperty('--cc',combo>3?'#ff7ad9':'#4aa8ff');
  $('#best').textContent=best;
  if(score===shown)return;
  const a=shown||0,b=score,t0=performance.now(),el=$('#score'),id=++tw;shown=score;
  if(RM){el.textContent=b;return}
  el.animate([{transform:`scale(${S.fx>1?1.4:1.25})`},{transform:'scale(1)'}],{duration:S.fx>1?300:220});
  (function f(t){if(id!==tw)return;const p=Math.min((t-t0)/350,1);el.textContent=Math.round(a+(b-a)*(1-Math.pow(1-p,3)));if(p<1)requestAnimationFrame(f)})(t0);
}
function drawTray(){
  const cp=Math.floor(step()*.5);
  slots.forEach((sl,i)=>{
    sl.innerHTML='';sl.style.minHeight=Math.floor(step()*2.4)+'px';
    const p=pieces[i];
    if(p){const e=shapeEl(p.s,cp,2,p.c,p.b,p.t).el;sl.appendChild(e);if(fresh&&!RM)e.animate([{transform:'translateY(30px) scale(.6)',opacity:0},{transform:'none',opacity:1}],{duration:340,delay:i*70,easing:'cubic-bezier(.2,1.4,.4,1)',fill:'backwards'})}
  });
  fresh=false;
}
function canClear(s){for(let r=0;r<N;r++)for(let c=0;c<N;c++){if(!fits(s,r,c))continue;const t=g.slice();s.forEach(([a,b])=>t[(r+a)*N+c+b]=0);if(lines(t).n)return true}return false}
function mk(){let s;do{s=SH[Math.random()*SH.length|0]}while(Math.random()<(s.length>5?.85:s.length>4?.5:0));return{s,c:Math.random()*6|0,b:s.length>1&&Math.random()<.65?Math.random()*s.length|0:-1,t:Math.random()<.5?2:1}}
function newSet(){fresh=true;let n=0;do{pieces=[0,1,2].map(mk);n++}while(n<60&&!(pieces.every(p=>canAny(p.s))&&(pieces.some(p=>canClear(p.s))||n>8)))}
function fit(){const cs=Math.floor((Math.min(innerWidth*.94,420)-33)/8);document.documentElement.style.setProperty('--cs',cs+'px');board.style.cssText=`width:${cs*8+21}px;align-self:center;aspect-ratio:auto;grid-template-columns:repeat(8,${cs}px);grid-template-rows:repeat(8,${cs}px)`}
function start(){fit();g=Array(64).fill(-1);gb=Array(64).fill(0);score=0;combo=0;newSet();draw();drawTray();$('#over').classList.remove('on')}
let _geo,lp,placing;function geo(){return _geo||(_geo={c:cells[0].getBoundingClientRect(),st:step()})}
function pos(p,left,top){
  const G=geo(),c0=G.c,st=G.st,fr=(top-c0.top)/st,fc=(left-c0.left)/st;
  let res=null,bd=1.01;
  for(const r of[Math.floor(fr),Math.ceil(fr)])for(const c of[Math.floor(fc),Math.ceil(fc)]){if(!fits(p.s,r,c))continue;const d=Math.hypot(r-fr,c-fc);if(d<bd){bd=d;res={r,c}}}
  if(lp&&fits(p.s,lp.r,lp.c)){const d0=Math.hypot(lp.r-fr,lp.c-fc);if(res&&d0<bd+.18&&d0<1.01)res=lp}lp=res;return res;
}
function ghost(p,q){
  const key=q?q.r+','+q.c:'';if(key===gkey)return;gkey=key;
  gcells.forEach(i=>{if(g[i]<0){cells[i].className='cell';cells[i].style.background=''}});
  hcells.forEach(i=>cells[i].classList.remove('hl'));gcells=[];hcells=[];
  if(!q)return;
  gcells=p.s.map(([a,b])=>(q.r+a)*N+q.c+b);
  gcells.forEach(i=>{cells[i].className='cell gh f';cells[i].style.color=`var(--c${p.c})`;cells[i].style.background=`var(--gl),var(--c${p.c})`});
  const t=g.slice();gcells.forEach(i=>t[i]=p.c);
  lines(t).forEach(i=>{cells[i].classList.add('hl');hcells.push(i)});
}
function ptr(e){if(!drag)return;let x=e.clientX,y=e.clientY;const pe=e.getPredictedEvents&&e.getPredictedEvents();if(pe&&pe.length){const q=pe[pe.length-1];x+=(q.clientX-x)*.6;y+=(q.clientY-y)*.6}drag.tx=x;drag.ty=y-OFF;drag.mv=1}
function loop(t){
  if(!drag)return;const d=drag,dt=Math.min(t-(d.t||t),25)||16.7;d.t=t;
  if(d.mv||d.q===undefined){d.mv=0;d.q=pos(d.p,d.tx-d.w/2,d.ty-d.h/2);ghost(d.p,d.q)}const q=d.q,G=geo();let gx=d.tx,gy=d.ty;if(q){gx+=(G.c.left+q.c*G.st+d.w/2-gx)*.35;gy+=(G.c.top+q.r*G.st+d.h/2-gy)*.35}
  const s=dt/1000,ks=1-Math.pow(.7,dt/16.7);const[K,C]=[[3600,110],[2500,90],[1500,70]][S.dr|0];d.vx=((d.vx||0)+(gx-d.cx)*K*s)*Math.exp(-C*s);d.vy=((d.vy||0)+(gy-d.cy)*K*s)*Math.exp(-C*s);d.cx+=d.vx*s;d.cy+=d.vy*s;d.sc+=(1-d.sc)*ks;const tr=S.ul?0:Math.min(18,Math.min(9,Math.abs(d.vx)*.015)+Math.max(0,Math.abs(d.vx)-600)*.0075)*Math.sign(d.vx);d.rot=(d.rot||0)+(tr-(d.rot||0))*(1-Math.pow(.75,dt/16.7));if(!d.wc&&Math.abs(1-d.sc)<.01){d.sc=1;d.wc=1;d.el.style.willChange='transform'}
  if(d.sc===1&&Math.abs(d.vx)+Math.abs(d.vy)<.3&&Math.abs(gx-d.cx)+Math.abs(gy-d.cy)<.2&&Math.abs(d.rot)<.01){requestAnimationFrame(loop);return}
  d.el.style.transform=`translate(${d.cx-d.w/2}px,${d.cy-d.h/2}px) rotate(${d.rot}deg) scale(${d.sc})`;
  requestAnimationFrame(loop);
}
slots.forEach((sl,i)=>sl.addEventListener('pointerdown',e=>{
  if(drag||placing||!pieces[i])return;
  const p=pieces[i],cp=step()-3,s=shapeEl(p.s,cp,3,p.c,p.b,p.t),m=sl.firstChild.getBoundingClientRect();
  s.el.id='drag';document.body.appendChild(s.el);
  const cx=m.left+m.width/2,cy=m.top+m.height/2;
  lp=null;drag={i,p,el:s.el,w:s.w,h:s.h,cx,cy,sc:m.width/s.w,sc0:m.width/s.w,tx:e.clientX,ty:e.clientY-OFF};
  sl.style.opacity=0;SFX.pick();ptr(e);requestAnimationFrame(loop);
}));
function up(){
  if(!drag)return;const d=drag;drag=null;
  const q=pos(d.p,d.tx-d.w/2,d.ty-d.h/2);ghost(d.p,null);
  const sl=slots[d.i];
  if(q){const G=geo(),fin=()=>{place(d.i,q.r,q.c);d.el.remove();sl.style.opacity=1;placing=0};placing=1;if(RM)fin();else d.el.animate([{transform:`translate(${d.cx-d.w/2}px,${d.cy-d.h/2}px) rotate(${d.rot||0}deg) scale(${d.sc})`},{transform:`translate(${G.c.left+q.c*G.st}px,${G.c.top+q.r*G.st}px) rotate(0deg) scale(1)`}],{duration:70,easing:'cubic-bezier(.2,.8,.3,1)',fill:'forwards'}).onfinish=fin}
  else{
    SFX.bad();const m=sl.getBoundingClientRect();
    d.el.animate([{transform:`translate(${d.cx-d.w/2}px,${d.cy-d.h/2}px) rotate(${d.rot||0}deg) scale(${d.sc})`},{transform:`translate(${m.left+m.width/2-d.w/2}px,${m.top+m.height/2-d.h/2}px) rotate(0deg) scale(${d.sc0})`}],{duration:240,easing:'cubic-bezier(.2,.9,.3,1.15)',fill:'forwards'}).onfinish=()=>{d.el.remove();sl.style.opacity=1};
  }
}
function place(i,r,c){
  const p=pieces[i],idx=p.s.map(([a,b])=>(r+a)*N+c+b);
  idx.forEach(k=>g[k]=p.c);if(p.b>=0)gb[idx[p.b]]=p.t||1;score+=idx.length*3;pieces[i]=null;
  const L=lines(g),X=new Set(L),bombs=[],ths=new Set();
  const q=[...L].filter(k=>gb[k]);
  while(q.length){const k=q.pop();bombs.push(k);const y=k/N|0,x=k%N,th=gb[k]===2;if(th)ths.add(k);for(let yy=0;yy<N;yy++)for(let xx=0;xx<N;xx++){const hit=th?(yy===y||xx===x):(Math.abs(yy-y)<=1&&Math.abs(xx-x)<=1);if(!hit)continue;const j=yy*N+xx;if(g[j]>=0&&!X.has(j)){X.add(j);if(gb[j])q.push(j)}}}
  const extra=X.size-L.size,cl=[...X].map(k=>({k,c:g[k],r:rect(k)}));
  X.forEach(k=>{g[k]=-1;gb[k]=0});
  draw();
  if(!RM&&S.fp)idx.forEach(k=>{if(!L.has(k))cells[k].classList.add('drop')});
  SFX.drop();placeFx(idx,p.c);
  if(L.n){combo++;miss=0;const gain=(L.n*L.n*30+X.size*5)*combo;score+=gain;SFX.clear(L.n,combo);clearFx(cl,idx,L.n,gain);if(bombs.length){score+=extra*20;SFX.boom();if(ths.size)SFX.zap();shake(6);const bb=board.getBoundingClientRect(),rs=bombs.map(rect);bombs.forEach((k,j)=>{const r=rs[j],x=r.left+r.width/2,y=r.top+r.height/2;const T=ths.has(k),bc=T?'#ffe14a':'#ff9d2e';ring(x,y,bc,240);ring(x,y,'#fff',150,60);sparks(x,y,bc,10,120);if(T){fx(`left:${bb.left}px;top:${y-14}px;width:${bb.width}px;height:28px;background:linear-gradient(transparent,#ffe14a 30%,#fff7a8 50%,#ffe14a 70%,transparent)`,[{opacity:1,transform:'scaleX(.2)'},{opacity:0,transform:'scaleX(1)'}],{duration:450});fx(`left:${x-14}px;top:${bb.top}px;width:28px;height:${bb.height}px;background:linear-gradient(90deg,transparent,#ffe14a 30%,#fff7a8 50%,#ffe14a 70%,transparent)`,[{opacity:1,transform:'scaleY(.2)'},{opacity:0,transform:'scaleY(1)'}],{duration:450})}});setTimeout(()=>popup((ths.size?'繧ｵ繝ｳ繝繝ｼ�� +':'繝懊Β�� +')+extra*20,true),350)}
    if(g.every(v=>v<0)){score+=500;confetti();setTimeout(()=>popup('繧ｪ繝ｼ繝ｫ繧ｯ繝ｪ繧｢�� +500',true),500)}}
  else{miss++;if(miss>2)combo=0}
  after();
}
function after(){
  if(score>best){best=score;try{localStorage.setItem('bp-best',best)}catch(e){}}
  if(pieces.every(p=>!p))newSet();
  hud();drawTray();
  if(!pieces.some(p=>p&&canAny(p.s))){
    $('#fin').textContent=score;
    $('#nb').textContent=score>=best&&score>0?'繝吶せ繝域峩譁ｰ��':'繝吶せ繝� '+best;
    SFX.over();shake(3);setTimeout(()=>$('#over').classList.add('on'),450);
  }
}
addEventListener('pointermove',ptr);
addEventListener('pointerup',up);
addEventListener('pointercancel',up);
addEventListener('resize',()=>{_geo=null;fit();drawTray()});document.addEventListener('visibilitychange',()=>{if(AC){document.hidden?AC.suspend():(BG&&AC.resume())}});
$('#again').onclick=start;
const sb=$('#snd'),menu=$('#menu'),sp=$('#sets');
const OPT=[['ld','雋�闕ｷ',['菴�','荳ｭ','鬮�']],['snd','蜉ｹ譫憺浹',['OFF','ON']],['sf','髻ｳ濶ｲ',['繝弱�繝槭Ν','繝ｬ繝医Ο','繝昴ャ繝�','繧ｯ繝ｪ繧ｹ繧ｿ繝ｫ','繝悶Λ繧ｹ繝磯｢ｨ','繧後ｓ縺�','繧ｵ繧､繝舌�']],['bgm','BGM',['OFF','繧ｵ繧､繝舌�']],['dr','繝峨Λ繝�げ',['繧ｭ繝薙く繝�','縺ｪ繧√ｉ縺�','縺ｨ繧阪→繧�']],['vib','謖ｯ蜍�',['OFF','ON']],['tex','繝悶Ο繝�け',['繧ｸ繝･繧ｨ繝ｫ','繝輔Λ繝�ヨ','繧ｭ繝｣繝ｳ繝�ぅ','繝阪が繝ｳ','繝悶Λ繧ｹ繝磯｢ｨ','繧後ｓ縺�','繧ｵ繧､繝舌�鮟�','繧ｵ繧､繝舌�逋ｽ']],['rq','謠冗判',['霆ｽ驥�','讓呎ｺ�','鬮倡判雉ｪ']],['fl','貍泌�',['雜�ｻｽ驥�','霆ｽ驥�','讓呎ｺ�','雎ｪ闖ｯ']],['fp','鄂ｮ縺上お繝輔ぉ繧ｯ繝�',['OFF','ON']],['fc','豸亥悉繧ｨ繝輔ぉ繧ｯ繝�',['OFF','ON']],['th','繝��繝�',['閾ｪ蜍�','繝ｩ繧､繝�','繝繝ｼ繧ｯ']]];
function applySet(){const h=document.documentElement;S.fx=Math.max(0,S.fl-1);S.ul=S.fl===0?1:0;h.dataset.tex=S.tex;h.dataset.fx=S.fx;h.dataset.rq=S.rq;if(S.th)h.dataset.theme=S.th===1?'light':'dark';else delete h.dataset.theme;snd=!!S.snd;RM=RMq||S.fx===0;for(const k in _cc)delete _cc[k];bgm(!!(S.bgm&&S.snd));try{localStorage.setItem('bp-set2',JSON.stringify(S))}catch(e){}}
function mark(){sp.querySelectorAll('.row').forEach((r,i)=>r.querySelectorAll('button').forEach((b,j)=>b.classList.toggle('on',S[OPT[i][0]]===j)))}
function openMenu(){$('#mb').textContent=best;menu.classList.add('on')}
for(let i=0;i<6;i++){const d=document.createElement('div');d.className='blk';d.style.cssText=`width:34px;height:34px;border-radius:7px;background:var(--gl),var(--c${i})`;$('#prev').appendChild(d)}
OPT.forEach(([k,l,v])=>{const r=document.createElement('div'),sg=document.createElement('div');r.className='row';r.innerHTML=`<span>${l}</span>`;sg.className='seg';v.forEach((t,j)=>{const b=document.createElement('button');b.textContent=t;b.onclick=()=>{S[k]=j;if(k==='ld')Object.assign(S,[{rq:0,fl:0,bgm:0},{rq:1,fl:2},{rq:2,fl:3}][j]);applySet();mark();if((k==='snd'&&j)||k==='sf')SFX.clear(1,1);if(k==='vib')buzz(30)};sg.appendChild(b)});r.appendChild(sg);sp.appendChild(r)});
sb.textContent='笘ｰ';sb.onclick=openMenu;
$('#play').onclick=()=>{ac();menu.classList.remove('on');sp.classList.remove('on')};
$('#setb').onclick=()=>sp.classList.toggle('on');
$('#rst').onclick=()=>{start();menu.classList.remove('on');sp.classList.remove('on')};
applySet();mark();openMenu();
start();
</script>
</body>
</html>
