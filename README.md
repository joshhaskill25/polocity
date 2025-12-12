<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<title>Polocity</title>
<meta name="viewport" content="width=device-width, initial-scale=1" />

<style>
:root {
  --bg:#ffffff;
  --text:#0f172a;
  --muted:#64748b;
  --border:#e5e7eb;
  --primary:#6366f1;
  --primary-soft:#eef2ff;

  --badge-upcoming:#fef3c7;
  --badge-passed:#dcfce7;
  --badge-failed:#fee2e2;
  --badge-committee:#e0e7ff;
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
  background:#fff;
  border-bottom:1px solid var(--border);
  padding:12px 16px;
  font-weight:700;
  z-index:10;
}

/* NOTIFICATIONS */
.notification {
  background:#f0f9ff;
  border-bottom:1px solid var(--border);
  padding:10px 16px;
  font-size:.8rem;
}

/* FEED */
main {
  max-width:620px;
  margin:auto;
}

/* ITEM */
.item {
  padding:14px 16px;
  border-bottom:1px solid var(--border);
}

.item:hover {
  background:#f8fafc;
}

.item-header {
  display:flex;
  justify-content:space-between;
  align-items:flex-start;
  gap:10px;
}

.item-title {
  font-weight:600;
  font-size:.95rem;
}

.item-meta {
  font-size:.75rem;
  color:var(--muted);
}

/* BADGES */
.badge {
  font-size:.7rem;
  padding:4px 8px;
  border-radius:999px;
  font-weight:600;
}

.upcoming { background:var(--badge-upcoming); }
.passed { background:var(--badge-passed); }
.failed { background:var(--badge-failed); }
.committee { background:var(--badge-committee); }

/* TAGS */
.tags {
  display:flex;
  gap:6px;
  flex-wrap:wrap;
  margin:6px 0;
}

.tag {
  font-size:.7rem;
  padding:2px 8px;
  border-radius:999px;
  background:var(--primary-soft);
  color:var(--primary);
  font-weight:600;
}

/* SUMMARY */
.item-summary {
  font-size:.9rem;
  margin:6px 0;
}

/* SENTIMENT */
.sentiment {
  font-size:.75rem;
  color:var(--muted);
  margin-bottom:6px;
}

/* DETAILS */
.details {
  display:none;
  margin-top:10px;
  padding:12px 14px;
  background:var(--primary-soft);
  border-radius:14px;
}

.details-title {
  font-size:.7rem;
  font-weight:700;
  text-transform:uppercase;
  color:var(--primary);
  margin-bottom:6px;
}

.details ul {
  padding-left:18px;
  margin:0 0 8px;
  font-size:.85rem;
}

.you {
  font-size:.85rem;
  border-left:3px solid var(--primary);
  padding-left:10px;
  margin-bottom:8px;
}

/* ANALYST */
.analyst {
  font-size:.8rem;
  color:var(--muted);
  border-top:1px solid var(--border);
  padding-top:6px;
}

/* ACTIONS */
.actions {
  display:flex;
  justify-content:space-between;
  margin-top:8px;
}

button {
  background:none;
  border:none;
  cursor:pointer;
  font-size:.8rem;
  color:var(--muted);
}

button.primary {
  color:var(--primary);
  font-weight:600;
}

/* STANCE */
.stance {
  display:flex;
  gap:8px;
  margin-top:8px;
}

.stance button {
  padding:6px 12px;
  border-radius:999px;
  border:1px solid var(--border);
  background:#fff;
}

.stance button.active {
  background:var(--primary-soft);
  color:var(--primary);
  font-weight:600;
}

.source {
  font-size:.75rem;
  color:var(--primary);
  text-decoration:none;
}
</style>
</head>

<body>

<header>Polocity</header>

<div id="notifications"></div>

<main id="feed"></main>

<script>
const items = [
  {
    title:"Zoning near light rail stations",
    badge:"upcoming",
    meta:"Jan 14 · City Council",
    tags:["Housing","Capitol Hill","Downtown"],
    summary:"Allows more housing near light rail stations.",
    sentiment:"Capitol Hill: Mixed · Downtown: Leaning for",
    why:["Increases housing supply","Reduces parking requirements"],
    you:"If you rent or live near transit, availability and pricing may change.",
    analyst:"Applies only within ¼ mile of stations.",
    reacted:true
  },
  {
    title:"Bus lane expansion downtown",
    badge:"committee",
    meta:"Jan 18 · Transportation",
    tags:["Transit","Downtown"],
    summary:"Adds dedicated bus lanes to improve reliability.",
    sentiment:"Downtown: Leaning for",
    why:["Improves bus reliability","Reduces congestion"],
    you:"Your commute time may decrease.",
    analyst:"Limited to identified corridors.",
    reacted:true
  },
  {
    title:"Neighborhood traffic calming",
    badge:"passed",
    meta:"Jan 23 · City Council",
    tags:["Safety","Ballard"],
    summary:"Adds speed humps and crosswalks.",
    sentiment:"Ballard: Mostly supportive",
    why:["Improves pedestrian safety","Slows traffic"],
    you:"Walking and biking may feel safer.",
    analyst:"Targets streets with speeding complaints.",
    reacted:true
  },
  {
    title:"Mid-year budget adjustment",
    badge:"failed",
    meta:"Jan 21 · Finance",
    tags:["Budget","Citywide"],
    summary:"Reallocates funding across departments.",
    sentiment:"Citywide: Mixed",
    why:["Shifts service funding","Changes priorities"],
    you:"Services you use could be affected.",
    analyst:"No net increase to the budget.",
    reacted:false
  },
  {
    title:"Urban tree canopy expansion",
    badge:"passed",
    meta:"Jan 25 · Environment",
    tags:["Environment","Fremont"],
    summary:"Funds new tree planting.",
    sentiment:"Fremont: Strong support",
    why:["Reduces heat","Improves air quality"],
    you:"More shade and cleaner air.",
    analyst:"Focuses on low-canopy areas.",
    reacted:true
  }
];

function badgeClass(b){
  return b;
}

function render(){
  const feed = document.getElementById('feed');
  const notifications = document.getElementById('notifications');
  feed.innerHTML = notifications.innerHTML = '';

  items.forEach(i=>{
    if(i.reacted && (i.badge === 'passed' || i.badge === 'failed')){
      notifications.innerHTML += `
        <div class="notification">
          🔔 An item you reacted to has an outcome: <strong>${i.title}</strong>
        </div>`;
    }
  });

  items.forEach(i=>{
    feed.innerHTML += `
      <div class="item">
        <div class="item-header">
          <div class="item-title">${i.title}</div>
          <div class="badge ${badgeClass(i.badge)}">${i.badge}</div>
        </div>

        <div class="item-meta">${i.meta}</div>

        <div class="tags">${i.tags.map(t=>`<span class="tag">${t}</span>`).join('')}</div>

        <div class="item-summary">${i.summary}</div>

        <div class="sentiment">
          Neighborhood reactions: <strong>${i.sentiment}</strong>
        </div>

        <div class="details">
          <div class="details-title">Why this matters</div>
          <ul>${i.why.map(w=>`<li>${w}</li>`).join('')}</ul>

          <div class="details-title">Why this matters to you</div>
          <div class="you">${i.you}</div>

          <div class="analyst">
            Civic analyst note · ✓ Verified<br>${i.analyst}
          </div>

          <div class="stance">
            <button onclick="setActive(this)">👍 For</button>
            <button onclick="setActive(this)">👎 Against</button>
            <button onclick="setActive(this)">🤔 Not sure</button>
          </div>
        </div>

        <div class="actions">
          <button class="primary" onclick="toggleDetails(this)">ℹ️ Details</button>
          <a class="source" href="https://seattle.legistar.com/" target="_blank">Source</a>
        </div>
      </div>`;
  });
}

function toggleDetails(btn){
  const d = btn.closest('.item').querySelector('.details');
  d.style.display = d.style.display === 'block' ? 'none' : 'block';
}

function setActive(btn){
  btn.parentElement.querySelectorAll('button').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
}

render();
</script>

</body>
</html>
