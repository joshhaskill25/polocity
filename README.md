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

/* FEED */
main {
  max-width:620px;
  margin:auto;
}

/* FEED ITEM */
.item {
  padding:14px 16px;
  border-bottom:1px solid var(--border);
}

.item:hover {
  background:#f8fafc;
}

/* HEADER ROW */
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
  white-space:nowrap;
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
  margin:6px 0 8px;
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
  margin:0 0 10px;
  font-size:.85rem;
}

.you {
  font-size:.85rem;
  border-left:3px solid var(--primary);
  padding-left:10px;
  margin-bottom:10px;
}

/* ANALYST */
.analyst {
  font-size:.8rem;
  color:var(--muted);
  border-top:1px solid var(--border);
  padding-top:8px;
}

/* ACTIONS */
.actions {
  display:flex;
  justify-content:space-between;
  align-items:center;
  margin-top:10px;
}

.actions-left {
  display:flex;
  gap:10px;
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

/* STANCE BUTTONS */
.stance {
  display:flex;
  gap:10px;
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

/* SOURCE */
.source {
  font-size:.75rem;
  color:var(--primary);
  text-decoration:none;
}

/* MOBILE */
@media (max-width:480px){
  .item-summary { font-size:.95rem; }
}
</style>
</head>

<body>
<header>Polocity</header>

<main>

<!-- ITEM -->
<div class="item">
  <div class="item-header">
    <div class="item-title">Zoning near light rail stations</div>
    <div class="badge upcoming">Upcoming vote</div>
  </div>

  <div class="item-meta">Jan 14 · City Council</div>

  <div class="tags">
    <span class="tag">Housing</span>
    <span class="tag">Capitol Hill</span>
    <span class="tag">Downtown</span>
  </div>

  <div class="item-summary">
    Allows more housing near light rail stations by reducing parking requirements.
  </div>

  <div class="sentiment">
    Community reactions so far: <strong>Mixed</strong>
  </div>

  <div class="details">
    <div class="details-title">Why this matters</div>
    <ul>
      <li>Increases housing supply near transit</li>
      <li>Reduces parking minimums</li>
    </ul>

    <div class="details-title">Why this matters to you</div>
    <div class="you">
      If you rent or live near transit, availability and pricing could change.
    </div>

    <div class="analyst">
      Civic analyst note · ✓ Verified  
      <br>
      Applies only within ¼ mile of stations and does not change height limits.
    </div>

    <div class="stance">
      <button onclick="setStance(this)">👍 For</button>
      <button onclick="setStance(this)">👎 Against</button>
      <button onclick="setStance(this)">🤔 Not sure</button>
    </div>
  </div>

  <div class="actions">
    <div class="actions-left">
      <button class="primary" onclick="toggleDetails(this)">ℹ️ Details</button>
    </div>
    <a class="source" href="https://seattle.legistar.com/" target="_blank">Source</a>
  </div>
</div>

<!-- ITEM -->
<div class="item">
  <div class="item-header">
    <div class="item-title">Bus lane expansion downtown</div>
    <div class="badge committee">In committee</div>
  </div>

  <div class="item-meta">Jan 18 · Transportation</div>

  <div class="tags">
    <span class="tag">Transit</span>
    <span class="tag">Downtown</span>
  </div>

  <div class="item-summary">
    Adds dedicated bus lanes downtown to improve reliability.
  </div>

  <div class="sentiment">
    Community reactions so far: <strong>Leaning for</strong>
  </div>

  <div class="details">
    <div class="details-title">Why this matters</div>
    <ul>
      <li>Improves bus reliability</li>
      <li>Reduces congestion</li>
    </ul>

    <div class="details-title">Why this matters to you</div>
    <div class="you">
      Your commute time may decrease during peak hours.
    </div>

    <div class="analyst">
      Civic analyst note · ✓ Verified  
      <br>
      Limited to corridors identified in the transit plan.
    </div>

    <div class="stance">
      <button onclick="setStance(this)">👍 For</button>
      <button onclick="setStance(this)">👎 Against</button>
      <button onclick="setStance(this)">🤔 Not sure</button>
    </div>
  </div>

  <div class="actions">
    <div class="actions-left">
      <button class="primary" onclick="toggleDetails(this)">ℹ️ Details</button>
    </div>
    <a class="source" href="https://seattle.legistar.com/" target="_blank">Source</a>
  </div>
</div>

</main>

<script>
function toggleDetails(btn){
  const item = btn.closest('.item');
  const details = item.querySelector('.details');
  details.style.display = details.style.display === 'block' ? 'none' : 'block';
}

function setStance(btn){
  const group = btn.parentElement.querySelectorAll('button');
  group.forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
}
</script>

</body>
</html>
