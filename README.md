<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<title>Polocity</title>
<meta name="viewport" content="width=device-width, initial-scale=1" />

<style>
:root {
  --bg-body:#f8fafc;
  --bg-card:#ffffff;
  --primary:#6366f1;
  --primary-soft:#eef2ff;
  --text-main:#0f172a;
  --text-muted:#64748b;
  --border:#e5e7eb;
  --radius:18px;
  --shadow:0 6px 20px rgba(15,23,42,.08);

  --for-bg:#ecfdf3;
  --for-border:#22c55e;
  --against-bg:#fef2f2;
  --against-border:#ef4444;
  --unsure-bg:#f1f5f9;
  --unsure-border:#94a3b8;
}

* { box-sizing:border-box; }

body {
  margin:0;
  font-family:system-ui,-apple-system,BlinkMacSystemFont,sans-serif;
  background:var(--bg-body);
  color:var(--text-main);
}

header {
  position:sticky;
  top:0;
  background:var(--bg-card);
  border-bottom:1px solid var(--border);
  padding:14px 16px;
  font-weight:700;
  z-index:10;
}

.tabs {
  display:flex;
  gap:10px;
  margin:12px 0 16px;
  position:sticky;
  top:56px;
  background:var(--bg-body);
  padding:8px 0;
  z-index:9;
}

.tab {
  padding:8px 16px;
  border-radius:999px;
  border:1px solid var(--border);
  background:var(--bg-card);
  font-size:.8rem;
  cursor:pointer;
  min-height:44px;
}

.tab.active {
  background:var(--primary-soft);
  color:var(--primary);
  border-color:transparent;
}

.view { display:none; }
.view.active { display:block; }

.filters {
  margin:12px 0 16px;
}

.filter-title {
  font-size:.7rem;
  text-transform:uppercase;
  color:var(--text-muted);
  margin-bottom:6px;
}

.filter-row {
  display:flex;
  gap:8px;
  flex-wrap:wrap;
}

.filter {
  padding:6px 12px;
  border-radius:999px;
  border:1px solid var(--border);
  font-size:.75rem;
  cursor:pointer;
  background:var(--bg-card);
  min-height:44px;
}

.filter.active {
  background:var(--primary-soft);
  color:var(--primary);
  border-color:transparent;
  box-shadow:0 0 0 2px rgba(99,102,241,.15);
}

main {
  max-width:640px;
  margin:auto;
  padding:14px 14px calc(80px + env(safe-area-inset-bottom));
}

.card {
  background:var(--bg-card);
  border-radius:var(--radius);
  box-shadow:var(--shadow);
  padding:18px;
  margin-bottom:16px;
}

.card h3 {
  margin:0;
  font-size:1.05rem;
}

.tags {
  display:flex;
  gap:6px;
  margin:6px 0 4px;
  flex-wrap:wrap;
}

.tag {
  font-size:.7rem;
  padding:4px 10px;
  border-radius:999px;
  background:var(--primary-soft);
  color:var(--primary);
  font-weight:600;
}

.meta {
  font-size:.75rem;
  color:var(--text-muted);
}

.summary {
  font-size:.92rem;
  margin:10px 0;
}

.why-block {
  background:var(--primary-soft);
  border-radius:14px;
  padding:12px 14px;
}

.why-title {
  font-size:.72rem;
  font-weight:600;
  text-transform:uppercase;
  color:var(--primary);
}

.why-points {
  padding-left:18px;
  font-size:.85rem;
}

.emphasis {
  font-weight:600;
  color:var(--primary);
}

.you-block {
  border-left:3px solid var(--primary);
  padding-left:12px;
  margin:12px 0;
  font-size:.88rem;
}

.analyst-note {
  margin-top:12px;
  padding:12px 14px;
  border-radius:14px;
  background:#f8fafc;
  border:1px solid var(--border);
  font-size:.85rem;
}

.analyst-header {
  font-size:.72rem;
  font-weight:600;
  text-transform:uppercase;
  color:var(--text-muted);
  margin-bottom:6px;
}

.verified {
  color:#16a34a;
  font-weight:600;
}

.card-links {
  display:flex;
  justify-content:space-between;
  font-size:.75rem;
  margin-top:10px;
}

.card-links a {
  color:var(--primary);
  text-decoration:none;
  font-weight:600;
}

.stance {
  display:flex;
  gap:10px;
  margin-top:12px;
}

.stance button {
  flex:1;
  padding:9px;
  border-radius:999px;
  border:1px solid var(--border);
  background:var(--bg-card);
  font-size:.75rem;
  cursor:pointer;
  min-height:44px;
  transition:transform .08s ease;
}

.stance button:active {
  transform:scale(0.97);
}

.for.active { background:var(--for-bg); border-color:var(--for-border); }
.against.active { background:var(--against-bg); border-color:var(--against-border); }
.unsure.active { background:var(--unsure-bg); border-color:var(--unsure-border); }

.topic-bubble {
  padding:6px 12px;
  border-radius:999px;
  background:var(--primary-soft);
  color:var(--primary);
  font-size:.75rem;
  display:inline-block;
  margin:4px 6px 10px 0;
}

@media (max-width:480px){
  .card { padding:16px; }
  .summary { font-size:.95rem; }
  .why-points { font-size:.9rem; }
  .you-block { font-size:.9rem; }
}
</style>
</head>

<body>
<header>Polocity</header>

<main>

<div class="tabs">
  <div class="tab active" onclick="switchView('feed',this)">📰 Your feed</div>
  <div class="tab" onclick="switchView('stances',this)">📌 My stances</div>
</div>

<div class="filters">
  <div class="filter-title">Neighborhoods</div>
  <div class="filter-row" id="neighborhoodFilters"></div>
</div>

<div id="feedView" class="view active"></div>

<div id="stancesView" class="view">
  <div id="stanceSummary"></div>
  <div id="stanceCards"></div>
</div>

</main>

<script>
const neighborhoods = ['All','Capitol Hill','Ballard','Fremont','Downtown','Rainier Valley'];
let activeNeighborhood = 'All';

const items = [
  {
    id:1,
    topic:'housing',
    neighborhoods:['Capitol Hill','Downtown'],
    title:'Zoning near light rail stations',
    when:'Vote Jan 14',
    summary:'Allows more housing near transit.',
    why:[
      '<span class="emphasis">Increases</span> housing supply',
      '<span class="emphasis">Reduces</span> parking requirements'
    ],
    you:'If you rent or live near transit, this may affect availability.',
    analyst:'Applies only within 1/4 mile of stations and does not change height limits.'
  },
  {
    id:2,
    topic:'transit',
    neighborhoods:['Downtown','Fremont'],
    title:'Bus lane expansion downtown',
    when:'Committee Jan 18',
    summary:'Adds dedicated bus lanes.',
    why:[
      '<span class="emphasis">Improves</span> bus reliability',
      '<span class="emphasis">Reduces</span> congestion'
    ],
    you:'This may shorten your commute.',
    analyst:'Limited to corridors identified in the transit plan.'
  },
  {
    id:3,
    topic:'budget',
    neighborhoods:['All'],
    title:'Mid-year budget adjustment',
    when:'Finance Committee Jan 21',
    summary:'Reallocates funding across departments.',
    why:[
      '<span class="emphasis">Shifts</span> funding priorities',
      '<span class="emphasis">Affects</span> department resources'
    ],
    you:'Services you rely on may see changes.',
    analyst:'No net increase to the city budget; funds are reallocated internally.'
  },
  {
    id:4,
    topic:'safety',
    neighborhoods:['Ballard','Rainier Valley'],
    title:'Neighborhood traffic calming',
    when:'Vote Jan 23',
    summary:'Adds speed humps and crosswalks.',
    why:[
      '<span class="emphasis">Improves</span> pedestrian safety',
      '<span class="emphasis">Slows</span> vehicle speeds'
    ],
    you:'Walking or biking in these areas may feel safer.',
    analyst:'Measures target streets with repeated speeding complaints.'
  },
  {
    id:5,
    topic:'environment',
    neighborhoods:['Fremont','Capitol Hill'],
    title:'Urban tree canopy expansion',
    when:'Committee Jan 25',
    summary:'Funds new tree planting in dense neighborhoods.',
    why:[
      '<span class="emphasis">Reduces</span> urban heat',
      '<span class="emphasis">Improves</span> air quality'
    ],
    you:'More shade and cleaner air in your neighborhood.',
    analyst:'Focuses on areas with below-average tree coverage.'
  }
];

let stances = JSON.parse(localStorage.getItem('polocity_stances') || '{}');

function switchView(view, el){
  document.getElementById('feedView').classList.toggle('active', view==='feed');
  document.getElementById('stancesView').classList.toggle('active', view==='stances');
  document.querySelectorAll('.tab').forEach(t=>t.classList.remove('active'));
  el.classList.add('active');
}

function setStance(id, stance){
  stances[id] = stance;
  localStorage.setItem('polocity_stances', JSON.stringify(stances));

  const toast = document.createElement('div');
  toast.innerText = 'Saved';
  toast.style.position='fixed';
  toast.style.bottom='20px';
  toast.style.left='50%';
  toast.style.transform='translateX(-50%)';
  toast.style.background='#0f172a';
  toast.style.color='#fff';
  toast.style.padding='6px 12px';
  toast.style.borderRadius='999px';
  toast.style.fontSize='.75rem';
  toast.style.zIndex='999';
  document.body.appendChild(toast);
  setTimeout(()=>toast.remove(),800);

  render();
}

function card(i){
  return `
  <div class="card">
    <h3>${i.title}</h3>
    <div class="tags">
      <span class="tag">${i.topic}</span>
      ${i.neighborhoods.map(n=>`<span class="tag">${n}</span>`).join('')}
    </div>
    <div class="meta">${i.when}</div>
    <p class="summary">${i.summary}</p>

    <div class="why-block">
      <div class="why-title">Why this matters</div>
      <ul class="why-points">${i.why.map(p=>`<li>${p}</li>`).join('')}</ul>
    </div>

    <div class="you-block"><strong>Why this matters to you:</strong> ${i.you}</div>

    <div class="analyst-note">
      <div class="analyst-header">Civic analyst note <span class="verified">✓ Verified</span></div>
      ${i.analyst}
    </div>

    <div class="card-links">
      <a href="https://seattle.legistar.com/" target="_blank">🔗 Source</a>
      <a href="#">📄 Full analysis</a>
    </div>

    <div class="stance">
      <button class="for ${stances[i.id]==='for'?'active':''}" onclick="setStance(${i.id},'for')">👍 For</button>
      <button class="against ${stances[i.id]==='against'?'active':''}" onclick="setStance(${i.id},'against')">👎 Against</button>
      <button class="unsure ${stances[i.id]==='unsure'?'active':''}" onclick="setStance(${i.id},'unsure')">🤔 Not sure</button>
    </div>
  </div>`;
}

function render(){
  const feed=document.getElementById('feedView');
  const stanceCards=document.getElementById('stanceCards');
  const summary=document.getElementById('stanceSummary');
  const filters=document.getElementById('neighborhoodFilters');

  feed.innerHTML=stanceCards.innerHTML=summary.innerHTML=filters.innerHTML='';

  neighborhoods.forEach(n=>{
    const b=document.createElement('div');
    b.className='filter'+(n===activeNeighborhood?' active':'');
    b.innerText=n;
    b.onclick=()=>{activeNeighborhood=n;render();};
    filters.appendChild(b);
  });

  const counts={};
  Object.entries(stances).forEach(([id,stance])=>{
    const item=items.find(i=>i.id==id);
    if(!item) return;
    counts[`${item.topic} · ${stance}`]=(counts[`${item.topic} · ${stance}`]||0)+1;
    stanceCards.innerHTML+=card(item);
  });

  Object.entries(counts).forEach(([k,v])=>{
    summary.innerHTML+=`<span class="topic-bubble">${k} · ${v}</span>`;
  });

  items
    .filter(i=>activeNeighborhood==='All'||i.neighborhoods.includes(activeNeighborhood))
    .forEach(i=>feed.innerHTML+=card(i));
}

render();
</script>
</body>
</html>
