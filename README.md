
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Weekly Routine</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;600;700&family=IBM+Plex+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --paper:#EEF2F5; --grid-line:#C7D4E0; --ink:#16233F; --ink-soft:#4A5872; --card:#FFFFFF;
    --workout:#B5502D; --workout-bg:#F7E7DF;
    --python:#2F5D8A; --python-bg:#E4EDF5;
    --mandarin:#7A4B6E; --mandarin-bg:#F0E6ED;
    --tlevel:#1F7A6C; --tlevel-bg:#E1EFEC;
    --electronics:#C98A02; --electronics-bg:#FBF1DC;
    --school:#5C6B80; --school-bg:#E7EAEE;
    --homework:#3E7E82; --homework-bg:#E4F0F1;
    --flashcards:#4C7A3A; --flashcards-bg:#E9F0E4;
    --free:#8B93A0; --free-bg:#EAEBEE;
    --sleep:#16233F; --sleep-bg:#E7E9EE;
  }
  *{box-sizing:border-box;}
  body{
    margin:0;
    background:
      linear-gradient(var(--grid-line) 1px, transparent 1px) 0 0/100% 34px,
      linear-gradient(90deg, var(--grid-line) 1px, transparent 1px) 0 0/34px 100%,
      var(--paper);
    font-family:'IBM Plex Sans', sans-serif;
    color:var(--ink);
    padding:36px 28px 60px;
  }
  .wrap{max-width:900px;margin:0 auto;}
  h1{font-family:'Space Grotesk',sans-serif;font-weight:700;font-size:clamp(26px,4vw,38px);margin:0 0 4px;letter-spacing:-0.01em;}
  .sub{font-family:'IBM Plex Mono',monospace;font-size:13px;color:var(--ink-soft);margin-bottom:20px;}

  .panel{background:var(--card);border:1px solid var(--grid-line);border-radius:6px;padding:20px 22px;margin-bottom:26px;}

  .status-row{display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:14px;margin-bottom:18px;}
  .clock{font-family:'IBM Plex Mono',monospace;font-size:28px;font-weight:500;letter-spacing:0.02em;}
  .clock .date{display:block;font-size:12px;color:var(--ink-soft);font-weight:400;margin-top:2px;letter-spacing:0;}

  .notify-btn{
    font-family:'IBM Plex Mono',monospace; font-size:12px; border:1px solid var(--ink); background:var(--ink); color:#fff;
    padding:9px 14px; border-radius:4px; cursor:pointer;
  }
  .notify-btn.on{background:var(--tlevel); border-color:var(--tlevel);}
  .notify-btn.denied{background:var(--workout); border-color:var(--workout);}

  .next-banner{
    display:flex; align-items:center; justify-content:space-between; gap:14px;
    background:var(--school-bg); border:1px dashed var(--school); border-radius:4px;
    padding:12px 16px; margin-bottom:18px; font-size:13px;
  }
  .next-banner .label{font-family:'Space Grotesk',sans-serif; font-weight:600;}
  .next-banner .countdown{font-family:'IBM Plex Mono',monospace; color:var(--ink-soft); font-size:12px;}

  .block-list{display:flex;flex-direction:column;gap:8px;}
  .block{
    display:flex; align-items:center; gap:12px;
    border-radius:4px; padding:11px 14px;
    border:1px solid transparent;
  }
  .block.current{border-color:var(--ink); box-shadow:0 0 0 1px var(--ink) inset;}
  .block.done{opacity:0.55;}
  .block.done .activity{text-decoration:line-through;}

  .block input[type=checkbox]{
    width:18px;height:18px; accent-color:var(--ink); flex:none; cursor:pointer;
  }
  .block .time{font-family:'IBM Plex Mono',monospace; font-size:11px; color:var(--ink-soft); width:56px; flex:none;}
  .block .body{flex:1; min-width:0;}
  .block .activity{font-size:13.5px; font-weight:500;}
  .block .tag{font-family:'IBM Plex Mono',monospace; font-size:9.5px; margin-top:2px; opacity:0.8;}

  .workout{background:var(--workout-bg);} .workout .tag{color:var(--workout);}
  .python{background:var(--python-bg);} .python .tag{color:var(--python);}
  .mandarin{background:var(--mandarin-bg);} .mandarin .tag{color:var(--mandarin);}
  .tlevel{background:var(--tlevel-bg);} .tlevel .tag{color:var(--tlevel);}
  .electronics{background:var(--electronics-bg);} .electronics .tag{color:var(--electronics);}
  .school{background:var(--school-bg);} .school .tag{color:var(--school);}
  .homework{background:var(--homework-bg);} .homework .tag{color:var(--homework);}
  .flashcards{background:var(--flashcards-bg);} .flashcards .tag{color:var(--flashcards);}
  .free{background:var(--free-bg);} .free .tag{color:var(--free);}
  .sleep{background:var(--sleep-bg);} .sleep .tag{color:var(--sleep);}

  .reset-row{display:flex; justify-content:flex-end; margin-top:14px;}
  .reset-btn{
    font-family:'IBM Plex Mono',monospace; font-size:11px; color:var(--ink-soft);
    background:none; border:1px solid var(--grid-line); border-radius:4px; padding:6px 10px; cursor:pointer;
  }
  .reset-btn:hover{border-color:var(--ink-soft);}

  .legend{display:flex;flex-wrap:wrap;gap:10px;margin:0 0 22px;padding:14px 16px;background:var(--card);border:1px solid var(--grid-line);border-radius:4px;}
  .chip{display:flex;align-items:center;gap:7px;font-family:'IBM Plex Mono',monospace;font-size:12px;color:var(--ink-soft);}
  .dot{width:9px;height:9px;border-radius:2px;flex:none;}

  .section-title{font-family:'Space Grotesk',sans-serif;font-weight:600;font-size:16px;margin:0 0 12px;}

  footer{margin-top:8px;font-family:'IBM Plex Mono',monospace;font-size:11.5px;color:var(--ink-soft);line-height:1.7;border-top:1px solid var(--grid-line);padding-top:14px;}
</style>
</head>
<body>
<div class="wrap">

  <h1>Weekly Routine</h1>
  <div class="sub">Tick off each block · get notified when the next one starts</div>

  <div class="legend" id="legend"></div>

  <div class="panel">
    <div class="status-row">
      <div class="clock" id="clock">--:--<span class="date" id="dateLabel">Loading…</span></div>
      <button class="notify-btn" id="notifyBtn">Enable notifications</button>
    </div>

    <div class="next-banner" id="nextBanner" style="display:none;">
      <div><span class="label" id="nextLabel"></span></div>
      <div class="countdown" id="nextCountdown"></div>
    </div>

    <div class="section-title">Today</div>
    <div class="block-list" id="blockList"></div>

    <div class="reset-row">
      <button class="reset-btn" id="resetBtn">Reset today's ticks</button>
    </div>
  </div>

  <footer>
    Notifications fire only while this page stays open in a browser tab — a web page can't send OS-level alerts once it's closed, so keep this open in the background (or a phone browser tab) if you want the pings.
    Checkbox progress is saved automatically per day.
  </footer>

</div>

<script>
const LEGEND = [
  ['workout','Workout'],['python','Python (Coddy)'],['mandarin','Mandarin'],
  ['tlevel','T Level Prep'],['electronics','Electronics'],['school','School'],
  ['homework','Homework'],['flashcards','Flashcards / Review'],['free','Free'],['sleep','Sleep']
];
document.getElementById('legend').innerHTML = LEGEND.map(([cat,label]) =>
  `<div class="chip"><span class="dot" style="background:var(--${cat})"></span>${label}</div>`
).join('');

// SCHEDULE keyed by JS getDay(): 0=Sun ... 6=Sat
const SCHEDULE = {
  1: [ // Monday
    {id:'workout', time:'04:30', label:'Workout', cat:'workout'},
    {id:'py1', time:'05:30', label:'Python (Coddy)', cat:'python'},
    {id:'tlevel1', time:'06:30', label:'T Level Prep', cat:'tlevel'},
    {id:'school', time:'08:25', label:'School', tag:'until 15:15', cat:'school'},
    {id:'afternoon', time:'15:15', label:'Homework', cat:'homework'},
    {id:'flash', time:'19:00', label:'Flashcards / Review', cat:'flashcards'},
    {id:'sleep', time:'22:30', label:'Sleep', cat:'sleep'},
  ],
  2: [ // Tuesday
    {id:'workout', time:'04:30', label:'Workout', cat:'workout'},
    {id:'mand1', time:'05:30', label:'Mandarin', cat:'mandarin'},
    {id:'elec1', time:'06:30', label:'Electronics', cat:'electronics'},
    {id:'school', time:'08:25', label:'School', tag:'until 11:30', cat:'school'},
    {id:'afternoon', time:'11:30', label:'T Level / Projects', cat:'tlevel'},
    {id:'flash', time:'19:00', label:'Flashcards / Review', cat:'flashcards'},
    {id:'sleep', time:'22:30', label:'Sleep', cat:'sleep'},
  ],
  3: [ // Wednesday
    {id:'workout', time:'04:30', label:'Workout', cat:'workout'},
    {id:'py1', time:'05:30', label:'Python (Coddy)', cat:'python'},
    {id:'tlevel1', time:'06:30', label:'T Level Prep', cat:'tlevel'},
    {id:'school', time:'08:25', label:'School', tag:'until 14:00', cat:'school'},
    {id:'afternoon', time:'14:00', label:'Homework', cat:'homework'},
    {id:'flash', time:'19:00', label:'Flashcards / Review', cat:'flashcards'},
    {id:'sleep', time:'22:30', label:'Sleep', cat:'sleep'},
  ],
  4: [ // Thursday
    {id:'workout', time:'04:30', label:'Workout', cat:'workout'},
    {id:'mand1', time:'05:30', label:'Mandarin', cat:'mandarin'},
    {id:'elec1', time:'06:30', label:'Electronics', cat:'electronics'},
    {id:'school', time:'08:25', label:'School', tag:'until 15:15', cat:'school'},
    {id:'afternoon', time:'15:15', label:'Homework', cat:'homework'},
    {id:'flash', time:'19:00', label:'Flashcards / Review', cat:'flashcards'},
    {id:'sleep', time:'22:30', label:'Sleep', cat:'sleep'},
  ],
  5: [ // Friday
    {id:'workout', time:'04:30', label:'Workout', cat:'workout'},
    {id:'py1', time:'05:30', label:'Python (Coddy)', cat:'python'},
    {id:'tlevel1', time:'06:30', label:'T Level Prep', cat:'tlevel'},
    {id:'school', time:'08:25', label:'School', tag:'off from 11:30', cat:'school'},
    {id:'afternoon', time:'11:30', label:'Electronics / Mandarin', cat:'electronics'},
    {id:'flash', time:'19:00', label:'Free', cat:'free'},
    {id:'sleep', time:'22:30', label:'Sleep', cat:'sleep'},
  ],
  0: [ // Sunday
    {id:'workout', time:'04:30', label:'Workout / Rest', cat:'workout'},
    {id:'flex1', time:'05:30', label:'Free / Flex', cat:'free'},
    {id:'flex2', time:'06:30', label:'Free / Flex', cat:'free'},
    {id:'personal', time:'12:00', label:'Personal Time', cat:'free'},
    {id:'flash', time:'19:00', label:'Free', cat:'free'},
    {id:'sleep', time:'22:30', label:'Sleep', cat:'sleep'},
  ],
  6: [ // Saturday — same shape as Sunday
    {id:'workout', time:'04:30', label:'Workout / Rest', cat:'workout'},
    {id:'flex1', time:'05:30', label:'Free / Flex', cat:'free'},
    {id:'flex2', time:'06:30', label:'Free / Flex', cat:'free'},
    {id:'personal', time:'12:00', label:'Personal Time', cat:'free'},
    {id:'flash', time:'19:00', label:'Free', cat:'free'},
    {id:'sleep', time:'22:30', label:'Sleep', cat:'sleep'},
  ],
};

function pad(n){ return n.toString().padStart(2,'0'); }
function dateKey(d){ return d.getFullYear()+'-'+pad(d.getMonth()+1)+'-'+pad(d.getDate()); }
function timeToMinutes(t){ const parts = t.split(':').map(Number); return parts[0]*60+parts[1]; }
function nowMinutes(d){ return d.getHours()*60 + d.getMinutes(); }

let today = new Date();
let todayKey = dateKey(today);
let blocks = SCHEDULE[today.getDay()];
let doneState = {};
let notifiedIds = new Set();
let notifPermission = (typeof Notification !== 'undefined') ? Notification.permission : 'unsupported';
let pageLoadedM = null;

async function loadDoneState(){
  try{
    const res = await window.storage.get('done:'+todayKey);
    doneState = res ? JSON.parse(res.value) : {};
  }catch(e){
    doneState = {};
  }
  renderBlocks();
}

async function saveDoneState(){
  try{
    await window.storage.set('done:'+todayKey, JSON.stringify(doneState));
  }catch(e){
    console.error('Could not save progress', e);
  }
}

function renderBlocks(){
  const nowM = nowMinutes(new Date());
  let currentIdx = -1;
  for(let i=0;i<blocks.length;i++){
    if(timeToMinutes(blocks[i].time) <= nowM) currentIdx = i;
  }
  const nextBlock = blocks.find(b => timeToMinutes(b.time) > nowM);

  document.getElementById('blockList').innerHTML = blocks.map((b,i) => {
    const isDone = !!doneState[b.id];
    const isCurrent = i === currentIdx;
    return `
      <label class="block ${b.cat} ${isDone ? 'done' : ''} ${isCurrent ? 'current' : ''}">
        <input type="checkbox" data-id="${b.id}" ${isDone ? 'checked' : ''}>
        <div class="time">${b.time}</div>
        <div class="body">
          <div class="activity">${b.label}</div>
          ${b.tag ? `<div class="tag">${b.tag}</div>` : ''}
        </div>
      </label>`;
  }).join('');

  document.querySelectorAll('.block-list input[type=checkbox]').forEach(cb => {
    cb.addEventListener('change', e => {
      doneState[e.target.dataset.id] = e.target.checked;
      saveDoneState();
      renderBlocks();
    });
  });

  const banner = document.getElementById('nextBanner');
  if(nextBlock){
    banner.style.display = 'flex';
    const mins = timeToMinutes(nextBlock.time) - nowM;
    document.getElementById('nextLabel').textContent = `Next: ${nextBlock.label} at ${nextBlock.time}`;
    document.getElementById('nextCountdown').textContent = mins <= 1 ? 'starting now' : `in ${mins} min`;
  } else {
    banner.style.display = 'none';
  }
}

function checkForDueBlocks(){
  const now = new Date();
  if(dateKey(now) !== todayKey){
    todayKey = dateKey(now);
    today = now;
    blocks = SCHEDULE[now.getDay()];
    notifiedIds = new Set();
    pageLoadedM = nowMinutes(now);
    loadDoneState();
    return;
  }
  const nowM = nowMinutes(now);
  blocks.forEach(b => {
    if(timeToMinutes(b.time) <= nowM && !notifiedIds.has(b.id)){
      notifiedIds.add(b.id);
      if(pageLoadedM !== null && timeToMinutes(b.time) >= pageLoadedM){
        fireNotification(b);
      }
    }
  });
}

function fireNotification(block){
  if(notifPermission === 'granted' && typeof Notification !== 'undefined'){
    new Notification('Time for: ' + block.label, {
      body: block.time + (block.tag ? ' · ' + block.tag : ''),
    });
  }
}

function updateClock(){
  const now = new Date();
  document.getElementById('clock').innerHTML =
    pad(now.getHours())+':'+pad(now.getMinutes())+
    `<span class="date">${now.toLocaleDateString(undefined,{weekday:'long', month:'short', day:'numeric'})}</span>`;
  renderBlocks();
  checkForDueBlocks();
}

const notifyBtn = document.getElementById('notifyBtn');
function updateNotifyBtn(){
  if(typeof Notification === 'undefined'){
    notifyBtn.textContent = 'Notifications not supported';
    notifyBtn.disabled = true;
    return;
  }
  if(notifPermission === 'granted'){
    notifyBtn.textContent = 'Notifications on';
    notifyBtn.classList.add('on');
  } else if(notifPermission === 'denied'){
    notifyBtn.textContent = 'Notifications blocked';
    notifyBtn.classList.add('denied');
  } else {
    notifyBtn.textContent = 'Enable notifications';
  }
}
notifyBtn.addEventListener('click', async () => {
  if(typeof Notification === 'undefined') return;
  const perm = await Notification.requestPermission();
  notifPermission = perm;
  updateNotifyBtn();
  if(perm === 'granted'){
    new Notification('Notifications enabled', {body:"You'll get a ping when it's time for the next thing."});
  }
});

document.getElementById('resetBtn').addEventListener('click', () => {
  doneState = {};
  saveDoneState();
  renderBlocks();
});

(async function init(){
  pageLoadedM = nowMinutes(new Date());
  updateNotifyBtn();
  await loadDoneState();
  updateClock();
  setInterval(updateClock, 15000);
})();
</script>
</body>
</html>
