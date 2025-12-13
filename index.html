<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<title>Polocity</title>
<meta name="viewport" content="width=device-width, initial-scale=1" />

<style>
:root {
  --bg:#F9FAFB;
  --card:#FFFFFF;
  --text:#111827;
  --muted:#6B7280;
  --border:#E5E7EB;

  /* Brand */
  --primary:#6366F1;
  --primary-soft:#EEF2FF;

  /* Stance colors */
  --for:#22C55E;        /* green (unchanged) */
  --against:#F87171;   /* warm coral red */
  --unsure:#D1BFA7;    /* warm neutral sand */

  /* Outcome badges */
  --badge-upcoming:#FEF3C7;
  --badge-passed:#DCFCE7;
  --badge-failed:#FEE2E2;
  --badge-committee:#E0E7FF;
}

* { box-sizing:border-box; }

body {
  margin:0;
  font-family:system-ui,-apple-system,BlinkMacSystemFont,sans-serif;
  background:var(--bg);
  color:var(--text);
}

/* HEADER */
header {
  position:sticky;
  top:0;
  background:var(--card);
  border-bottom:1px solid var(--border);
  padding:14px 16px;
  font-weight:800;
  z-index:10;
}

/* FEED */
main {
  max-width:620px;
  margin:auto;
}

/* ITEM */
.item {
  padding:16px;
  border-bottom:1px solid var(--border);
  background:var(--card);
  transition:transform .15s ease, box-shadow .15s ease;
}

@media (hover:hover) {
  .item:hover {
    transform:translateY(-2px);
    box-shadow:0 6px 18px rgba(0,0,0,.05);
  }
}

.item-header {
  display:flex;
  justify-content:space-between;
}

.item-title {
  font-weight:700;
  font-size:.95rem;
}

/* BADGES */
.badge {
  font-size:.7rem;
  padding:4px 10px;
  border-radius:999px;
  font-weight:700;
}

.upcoming { background:var(--badge-upcoming); }
.passed { background:var(--badge-passed); }
.failed { background:var(--badge-failed); }
.committee { background:var(--badge-committee); }

.item-meta {
  font-size:.75rem;
  color:var(--muted);
}

/* TAGS */
.tags {
  display:flex;
  gap:6px;
  flex-wrap:wrap;
  margin:6px 0;
}

.tag {
  font-size:.7rem;
  padding:3px 10px;
  border-radius:999px;
  background:var(--primary-soft);
  color:var(--primary);
  font-weight:700;
}

/* SUMMARY */
.summary {
  font-size:.92rem;
  margin:6px 0;
}

/* SENTIMENT */
.sentiment {
  display:inline-block;
  font-size:.75rem;
  background:rgba(34,197,94,0.12);
  color:#065F46;
  padding:6px 10px;
  border-radius:12px;
  margin-bottom:8px;
}

/* DETAILS */
.details {
  overflow:hidden;
  max-height:0;
  opacity:0;
  transition:max-height .35s ease, opacity .25s ease;
  margin-top:8px;
  background:var(--primary-soft);
  border-radius:16px;
}

.details.open {
  max-height:600px;
  opacity:1;
  padding:14px;
}

.details h4 {
  font-size:.7rem;
  text-transform:uppercase;
  color:var(--primary);
  margin:8px 0 4px;
}

.details ul {
  padding-left:18px;
  margin:0 0 8px;
  font-size:.85rem;
}

.you {
  border-left:4px solid var(--primary);
  padding-left:10px;
  font-size:.85rem;
  margin-bottom:8px;
}

/* ANALYST */
.analyst {
  font-size:.8rem;
  color:var(--muted);
  border-top:1px dashed var(--border);
  padding-top:6px;
}

/* ACTIONS */
.actions {
  display:flex;
  justify-content:space-between;
  align-items:center;
  margin-top:10px;
}

button {
  border:none;
  background:none;
  cursor:pointer;
  font-size:.8rem;
  font-weight:700;
}

.details-btn {
  color:var(--primary);
  background:rgba(99,102,241,0.12);
  padding:6px 14px;
  border-radius:999px;
}

/* STANCE */
.stance {
  display:flex;
  gap:8px;
  margin-top:10px;
}

.stance button {
  padding:6px 14px;
  border-radius:999px;
  border:1px solid var(--border);
  background:var(--card);
  transition:transform .1s ease;
}

.stance button:active {
  transform:scale(.92);
}

/* Active states */
.stance button.for.active {
  background:var(--for);
  color:white;
  border-color:transparent;
}

.stance button.against.active {
  background:var(--against);
  color:white;
  border-color:transparent;
}

.stance button.unsure.active {
  background:var(--unsure);
  color:white;
  border-color:transparent;
}

/* SOURCE */
.source {
  font-size:.75rem;
  color:var(--primary);
  text-decoration:none;
}

/* TOAST */
.toast {
  position:fixed;
  bottom:24px;
  left:50%;
  transform:translateX(-50%);
  background:#111827;
  color:white;
  padding:8px 14px;
  border-radius:999px;
  font-size:.75rem;
  opacity:0;
  pointer-events:none;
  transition:opacity .2s ease;
}

.toast.show {
  opacity:1;
}
</style>
</head>

<body>

<header>Polocity</header>

<main id="feed"></main>

<div id="toast" class="toast">Saved</div>

<script>
const items = [
  {
    title:"Zoning near light rail stations",
    badge:"upcoming",
    meta:"Jan 14 · City Council",
    tags:["Housing","Capitol Hill","Downtown"],
    summary:"Allows more housing near light rail stations by reducing parking requirements.",
    sentiment:"Capitol Hill mixed · Downtown leaning for",
    why:["Increases housing supply","Reduces parking minimums"],
    you:"If you rent or live near transit, availability and pricing could change.",
    analyst:"Applies only within ¼ mile of stations."
  },
  {
    title:"Bus lane expansion downtown",
    badge:"committee",
    meta:"Jan 18 · Transportation",
    tags:["Transit","Downtown"],
    summary:"Adds dedicated bus lanes to improve reliability.",
    sentiment:"Downtown leaning for",
    why:["Improves bus reliability","Reduces congestion"],
    you:"Commute times may decrease.",
    analyst:"Limited to identified corridors."
  },
  {
    title:"Neighborhood traffic calming",
    badge:"passed",
    meta:"Jan 23 · City Council",
    tags:["Safety","Ballard"],
    summary:"Adds speed humps and crosswalks.",
    sentiment:"Ballard mostly supportive",
    why:["Improves pedestrian safety","Slows traffic"],
    you:"Walking and biking may feel safer.",
    analyst:"Targets streets with repeated speeding complaints."
  },
  {
    title:"Mid-year budget adjustment",
    badge:"failed",
    meta:"Jan 21 · Finance",
    tags:["Budget","Citywide"],
    summary:"Reallocates funding across departments.",
    sentiment:"Citywide mixed",
    why:["Shifts funding priorities","Impacts services"],
    you:"Some services you rely on could change.",
    analyst:"No net increase to total budget."
  },
  {
    title:"Urban tree canopy expansion",
    badge:"passed",
    meta:"Jan 25 · Environment",
    tags:["Environment","Fremont"],
    summary:"Funds new tree planting in dense areas.",
    sentiment:"Fremont strong support",
    why:["Reduces urban heat","Improves air quality"],
    you:"More shade and cleaner air locally.",
    analyst:"Focuses on low-canopy neighborhoods."
  }
];

const feed = document.getElementById('feed');
const toast = document.getElementById('toast');

items.forEach(i=>{
  feed.innerHTML += `
  <div class="item">
    <div class="item-header">
      <div class="item-title">${i.title}</div>
      <div class="badge ${i.badge}">${i.badge}</div>
    </div>
    <div class="item-meta">${i.meta}</div>
    <div class="tags">${i.tags.map(t=>`<span class="tag">${t}</span>`).join('')}</div>
    <div class="summary">${i.summary}</div>
    <div class="sentiment">Neighborhood reactions: ${i.sentiment}</div>

    <div class="details">
      <h4>Why this matters</h4>
      <ul>${i.why.map(w=>`<li>${w}</li>`).join('')}</ul>

      <h4>Why this matters to you</h4>
      <div class="you">${i.you}</div>

      <div class="analyst">Civic analyst note · ✓ Verified<br>${i.analyst}</div>

      <div class="stance">
        <button class="for" onclick="setStance(this)">👍 For</button>
        <button class="against" onclick="setStance(this)">👎 Against</button>
        <button class="unsure" onclick="setStance(this)">🤔 Not sure</button>
      </div>
    </div>

    <div class="actions">
      <button class="details-btn" onclick="toggleDetails(this)">ℹ️ Details</button>
      <a class="source" href="https://seattle.legistar.com/" target="_blank">Source</a>
    </div>
  </div>`;
});

function toggleDetails(btn){
  const d = btn.closest('.item').querySelector('.details');
  d.classList.toggle('open');
}

function setStance(btn){
  btn.parentElement.querySelectorAll('button').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  toast.classList.add('show');
  setTimeout(()=>toast.classList.remove('show'),900);
}
</script>

</body>
</html>
