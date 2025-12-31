<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<title>Polocity</title>
<meta name="viewport" content="width=device-width, initial-scale=1" />

<style> 
/* =====================
   DESIGN TOKENS
===================== */
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

  /* stance colors */
  --for-bg:#ecfdf3;
  --for-border:#22c55e;

  --against-bg:#fff1f2;
  --against-border:#ef4444;

  --unsure-bg:#f8fafc;
  --unsure-border:#94a3b8;

  /* lively gradients */
  --grad-a: linear-gradient(135deg, rgba(99,102,241,.18), rgba(59,130,246,.10));
  --grad-b: linear-gradient(135deg, rgba(34,197,94,.12), rgba(99,102,241,.12));
  --grad-c: linear-gradient(135deg, rgba(251,191,36,.18), rgba(99,102,241,.10));

  --pulse: rgba(99,102,241,.22);
}

body.dark {
  --bg-body:#020617;
  --bg-card:#020617;
  --text-main:#e5e7eb;
  --text-muted:#94a3b8;
  --border:#1e293b;
  --shadow:none;

  --against-bg:#2a0f12;
  --unsure-bg:#0b1220;

  --grad-a: linear-gradient(135deg, rgba(99,102,241,.22), rgba(59,130,246,.14));
  --grad-b: linear-gradient(135deg, rgba(34,197,94,.18), rgba(99,102,241,.18));
  --grad-c: linear-gradient(135deg, rgba(251,191,36,.22), rgba(99,102,241,.16));

  --pulse: rgba(99,102,241,.35);
}

/* =====================
   GLOBAL
===================== */
* { box-sizing:border-box; }
html { scroll-behavior:smooth; }

body {
  margin:0;
  font-family:system-ui,-apple-system,BlinkMacSystemFont,sans-serif;
  background:var(--bg-body);
  color:var(--text-main);
}

/* =====================
   HEADER
===================== */
header {
  position:sticky;
  top:0;
  background:var(--bg-card);
  border-bottom:1px solid var(--border);
  padding:14px 16px;
  display:flex;
  justify-content:space-between;
  align-items:center;
  z-index:10;
  backdrop-filter: saturate(140%) blur(8px);
}

.logo {
  font-weight:800;
  font-size:1.2rem;
  letter-spacing:-0.02em;
}

.logo span { color: var(--primary); }

.toggle { cursor:pointer; }

/* =====================
   TABS
===================== */
.tabs {
  display:flex;
  gap:8px;
  margin:12px 0 16px;
}

.tab {
  padding:9px 14px;
  border-radius:999px;
  border:1px solid var(--border);
  background:var(--bg-card);
  font-size:0.82rem;
  cursor:pointer;
  display:flex;
  align-items:center;
  gap:8px;
  transition:transform .08s ease, box-shadow .12s ease, background .12s ease;
}

.tab:hover { transform: translateY(-1px); }

.tab.active {
  background:var(--primary-soft);
  color:var(--primary);
  border-color:transparent;
  box-shadow:0 10px 24px rgba(99,102,241,.18);
}

.view { display:none; }
.view.active { display:block; }

/* =====================
   LAYOUT
===================== */
main {
  max-width:680px;
  margin:auto;
  padding:14px 14px 88px;
}

.section-title {
  font-size:.74rem;
  text-transform:uppercase;
  letter-spacing:.10em;
  color:var(--text-muted);
  margin:18px 4px 6px;
}

.feed-subtitle {
  font-size:.86rem;
  color:var(--text-muted);
  margin:0 4px 12px;
  line-height:1.35;
}

.feed-divider {
  margin:28px 0 20px;
  border-top:2px solid var(--border);
}

/* =====================
   NOTIFICATIONS
===================== */
.notification {
  background:#fef3c7;
  border:1px solid #fde68a;
  color:#92400e;
  border-radius:14px;
  padding:10px 12px;
  font-size:.86rem;
  margin-bottom:10px;
}

body.dark .notification {
  background:#2b1f05;
  border-color:#7c4a03;
  color:#fde68a;
}

/* =====================
   TOPIC BUCKETS
===================== */
.topic-buckets {
  display:flex;
  gap:8px;
  flex-wrap:wrap;
  margin-bottom:12px;
}

.topic-bubble {
  padding:7px 12px;
  border-radius:999px;
  font-size:.78rem;
  background:var(--primary-soft);
  color:var(--primary);
  border:1px solid rgba(99,102,241,.20);
}

/* =====================
   CARDS
===================== */
.card {
  position:relative;
  background:var(--bg-card);
  border-radius:22px;
  box-shadow:var(--shadow);
  padding:18px;
  margin-bottom:16px;
  border:1px solid transparent;
  overflow:hidden;
  transform: translateZ(0);
  transition:transform .12s ease, border-color .12s ease;
}

.card::before{
  content:"";
  position:absolute;
  inset:-2px;
  background: var(--grad-a);
  opacity:.95;
  filter: blur(18px);
  z-index:0;
}

.card > * { position:relative; z-index:1; }

.card:hover {
  transform: translateY(-2px);
  border-color: rgba(99,102,241,.25);
}

.card-top {
  display:flex;
  justify-content:space-between;
  align-items:flex-start;
  gap:12px;
}

.card h3 {
  margin:0;
  font-size:1.06rem;
  line-height:1.25;
  letter-spacing:-0.01em;
}

.meta {
  font-size:.78rem;
  color:var(--text-muted);
  margin-top:8px;
  display:flex;
  align-items:center;
  gap:8px;
  flex-wrap:wrap;
}

.badge {
  display:inline-flex;
  align-items:center;
  gap:6px;
  padding:5px 10px;
  border-radius:999px;
  font-size:.74rem;
  border:1px solid var(--border);
  background: rgba(255,255,255,.72);
}

body.dark .badge { background: rgba(2,6,23,.55); }

.badge.ok { border-color:#86efac; background:#ecfdf3; color:#166534; }
.badge.warn { border-color:#fde68a; background:#fef3c7; color:#92400e; }
.badge.info { border-color:#c7d2fe; background:#eef2ff; color:#3730a3; }

body.dark .badge.ok { background:#052e16; color:#bbf7d0; border-color:#14532d; }
body.dark .badge.warn { background:#3a2502; color:#fde68a; border-color:#7c4a03; }
body.dark .badge.info { background:#0b1b44; color:#c7d2fe; border-color:#1e3a8a; }

.tag-row {
  display:flex;
  gap:8px;
  flex-wrap:wrap;
  margin-top:12px;
}

.tag {
  display:inline-flex;
  align-items:center;
  gap:6px;
  padding:6px 10px;
  border-radius:999px;
  font-size:.76rem;
  border:1px solid rgba(15,23,42,.10);
  background: rgba(255,255,255,.70);
}

body.dark .tag { background: rgba(2,6,23,.55); border-color: rgba(148,163,184,.15); }

.summary {
  font-size:.95rem;
  margin:12px 0 0;
  line-height:1.45;
}

/* =====================
   WHY BLOCKS
===================== */
.why-block {
  margin-top:12px;
  background: rgba(255,255,255,.70);
  border-radius:16px;
  padding:12px 14px;
  border: 1px solid rgba(99,102,241,.18);
}

body.dark .why-block { background: rgba(2,6,23,.55); }

.why-title {
  font-size:.72rem;
  font-weight:900;
  text-transform:uppercase;
  letter-spacing:.10em;
  color:var(--primary);
}

.why-points {
  padding-left:18px;
  font-size:.88rem;
  margin:8px 0 0;
  line-height:1.35;
}

.emphasis {
  font-weight:800;
  color:var(--primary);
}

.you-block {
  margin-top:12px;
  border-left:4px solid var(--primary);
  padding-left:12px;
  font-size:.92rem;
  line-height:1.4;
  background: rgba(255,255,255,.60);
  border-radius:12px;
  padding:12px;
  border:1px solid rgba(99,102,241,.14);
}

body.dark .you-block { background: rgba(2,6,23,.55); }

/* =====================
   DETAILS EXPANSION (ENGAGING)
===================== */
.details {
  margin-top:14px;
  border:1px solid rgba(99,102,241,.22);
  border-radius:18px;
  overflow:hidden;
  background: rgba(99,102,241,.05);
}

.details > summary {
  list-style:none;
  cursor:pointer;
  padding:12px 14px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:12px;
  font-weight:900;
  font-size:.88rem;
}

.details > summary::-webkit-details-marker { display:none; }

.chev {
  width:34px;
  height:34px;
  border-radius:999px;
  display:flex;
  align-items:center;
  justify-content:center;
  border:1px solid rgba(99,102,241,.25);
  background: rgba(255,255,255,.75);
  transition: transform .16s ease;
}

body.dark .chev { background: rgba(2,6,23,.55); }

.details[open] .chev { transform: rotate(180deg); }

.details-body {
  padding:12px 14px 14px;
  border-top:1px solid rgba(99,102,241,.14);
  background: rgba(255,255,255,.66);
}

body.dark .details-body { background: rgba(2,6,23,.55); }

.details-headline {
  display:flex;
  flex-wrap:wrap;
  align-items:center;
  gap:10px;
  margin-bottom:10px;
}

.progress {
  display:flex;
  gap:6px;
  flex-wrap:wrap;
}

.step {
  padding:6px 10px;
  border-radius:999px;
  font-size:.78rem;
  border:1px solid rgba(148,163,184,.30);
  background: rgba(255,255,255,.72);
}

body.dark .step { background: rgba(2,6,23,.55); }

.step.active {
  border-color: rgba(99,102,241,.35);
  background: rgba(99,102,241,.12);
  box-shadow: 0 0 0 4px rgba(99,102,241,.10);
}

.detail-grid {
  display:grid;
  grid-template-columns: 1fr;
  gap:12px;
}

.detail-card {
  border:1px solid rgba(148,163,184,.25);
  border-radius:16px;
  padding:12px;
  background: rgba(255,255,255,.72);
}

body.dark .detail-card { background: rgba(2,6,23,.55); border-color: rgba(148,163,184,.18); }

.detail-title {
  font-size:.72rem;
  font-weight:900;
  text-transform:uppercase;
  letter-spacing:.10em;
  color:var(--text-muted);
  margin-bottom:8px;
  display:flex;
  align-items:center;
  gap:8px;
}

.detail-list {
  margin:0;
  padding-left:18px;
  font-size:.9rem;
  line-height:1.35;
}

.quick-actions {
  display:flex;
  gap:10px;
  flex-wrap:wrap;
  margin-top:12px;
}

.pill {
  border:1px solid rgba(99,102,241,.24);
  background: rgba(99,102,241,.10);
  color: var(--primary);
  font-weight:800;
  font-size:.82rem;
  border-radius:999px;
  padding:8px 12px;
  cursor:pointer;
  transition: transform .06s ease;
}

.pill:active { transform: scale(.98); }

.pill.secondary {
  background: rgba(148,163,184,.10);
  border-color: rgba(148,163,184,.30);
  color: var(--text-main);
}

.pill.on {
  background: rgba(34,197,94,.12);
  border-color: rgba(34,197,94,.35);
  color: #166534;
}

/* =====================
   ANALYST NOTE + SOURCES
===================== */
.analyst-note {
  margin-top: 12px;
  padding: 12px 14px;
  border-radius: 16px;
  background: rgba(255,255,255,.72);
  border: 1px solid rgba(148,163,184,.25);
  font-size: 0.9rem;
}

body.dark .analyst-note { background: rgba(2,6,23,.55); }

.analyst-header {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 0.72rem;
  font-weight: 900;
  text-transform: uppercase;
  color: var(--text-muted);
  margin-bottom: 6px;
  justify-content: space-between;
}

.verified {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  color: #16a34a;
  font-weight: 900;
}

.check {
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: #16a34a;
  color: #fff;
  font-size: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.sources {
  margin-top:10px;
  display:flex;
  flex-direction:column;
  gap:6px;
}

.sources a {
  font-size:.86rem;
  color: var(--primary);
  text-decoration:none;
}

.sources a:hover { text-decoration: underline; }

/* =====================
   STANCE BUTTONS (inside details)
===================== */
.stance {
  display:flex;
  gap:8px;
  margin-top:12px;
}

.stance button {
  flex:1;
  padding:10px;
  border-radius:999px;
  border:1px solid rgba(148,163,184,.30);
  background: rgba(255,255,255,.78);
  font-size:.82rem;
  font-weight:800;
  cursor:pointer;
  transition: transform .06s ease, box-shadow .12s ease;
}

body.dark .stance button { background: rgba(2,6,23,.55); }

.stance button:active { transform: scale(.98); }

.for.active { background:var(--for-bg); border-color:var(--for-border); box-shadow: 0 0 0 4px rgba(34,197,94,.10); }
.against.active { background:var(--against-bg); border-color:var(--against-border); box-shadow: 0 0 0 4px rgba(239,68,68,.10); }
.unsure.active { background:var(--unsure-bg); border-color:var(--unsure-border); box-shadow: 0 0 0 4px rgba(148,163,184,.12); }

/* =====================
   MOBILE POLISH
===================== */
@media (max-width: 420px) {
  .card { padding:16px; }
  .tag { font-size:.74rem; }
  .summary { font-size:.95rem; }
  .stance { flex-direction:column; }
  .stance button { width:100%; }
}
</style>
</head>

<body>
<header>
  <div class="logo"><span>P</span>olocity</div>
  <div class="toggle" onclick="toggleDark()" title="Toggle dark mode">🌙</div>
</header>

<main>
  <div class="tabs">
    <div class="tab active" onclick="switchView('feed', this)">📰 Your feed</div>
    <div class="tab" onclick="switchView('stances', this)">💬 My stances</div>
  </div>

  <!-- FEED VIEW -->
  <div id="feedView" class="view active">
    <div id="notifications"></div>
    <div id="topicBuckets" class="topic-buckets"></div>

    <div class="section-title">Your feed</div>
    <div class="feed-subtitle">Personalized based on what you engage with</div>
    <div id="homeFeed"></div>

    <div class="feed-divider"></div>

    <div class="section-title">All items</div>
    <div class="feed-subtitle">A demo timeline showing how one major decision unfolded</div>
    <div id="allFeed"></div>
  </div>

  <!-- STANCES VIEW -->
  <div id="stancesView" class="view">
    <div class="section-title">Your stances</div>
    <div class="feed-subtitle">A summary of topics you’ve reacted to</div>
    <div id="stanceBuckets" class="topic-buckets"></div>

    <div class="section-title">Items you reacted to</div>
    <div class="feed-subtitle">Grouped by topic</div>
    <div id="stanceCards"></div>
  </div>
</main>

<script>
const items = [
  {
    id: 101,
    topic: "housing",
    neighborhood: ["Downtown", "South Lake Union"],
    title: "Big housing rules proposed for Downtown & South Lake Union",
    when: "March 2017 · Review begins",
    summary:
      "Seattle started reviewing new rules that require future buildings to include affordable homes or contribute to a city fund.",
    why: [
      "<span class='emphasis'>Creates</span> more support for affordable housing",
      "<span class='emphasis'>Influences</span> what gets built in fast-growing areas"
    ],
    you:
      "If you live or work nearby, this shapes future construction and how the neighborhood changes over time.",
    outcome: { label: "In review", tone: "info" },
    stage: 1,
    tags: ["🏠 Housing", "🧭 City planning", "📍 Downtown/SLU"],
    details: {
      headline: "What this means in plain English",
      overview:
        "Seattle is deciding new rules for future buildings in Downtown and South Lake Union. The goal is to make sure growth helps fund or create affordable housing.",
      keyPoints: [
        "Applies to future building projects (not existing buildings)",
        "Affordable housing becomes a standard part of new development",
        "Details are split across the bill, maps, and amendments"
      ],
      whatChanged: [
        "This is an early version — the final details can still change quickly"
      ],
      timeline: [
        "Introduced → reviewed by staff",
        "Referred for discussion → later goes to a full council vote"
      ]
    },
    analystNote:
      "Even though this is public, it isn’t written for residents. Polocity turns it into a simple timeline with the few details people actually need.",
    sources: [
      {
        label: "Legistar record – CB 118940",
        url: "https://seattle.legistar.com/LegislationDetail.aspx?ID=3011262&GUID=E6D86622-97D3-41AF-BCCD-A7794C171A2C"
      }
    ]
  },

  {
    id: 102,
    topic: "housing",
    neighborhood: ["Downtown", "South Lake Union"],
    title: "Map released: here’s which blocks are affected",
    when: "Early April 2017 · New info added",
    summary:
      "A map was published showing the exact parts of Downtown and South Lake Union covered by the new rules.",
    why: [
      "<span class='emphasis'>Your block might be included</span> even if the next one isn’t",
      "The map is the easiest way to tell if you’re impacted"
    ],
    you:
      "If you’re trying to understand what changes near you, this is the most important attachment.",
    outcome: { label: "New details", tone: "warn" },
    stage: 2,
    tags: ["🗺️ Map", "🏠 Housing", "📍 Neighborhood impact"],
    details: {
      headline: "Why the map matters",
      overview:
        "The policy applies to specific blocks. Without the map, most people can’t tell whether their street is included.",
      keyPoints: [
        "Coverage depends on map boundaries",
        "Maps often live as attachments, not explained on the main page",
        "This is where “does this affect me?” gets answered"
      ],
      whatChanged: [
        "The city clarified which areas are included once the map exhibit was published"
      ],
      timeline: [
        "Map added → coverage becomes clear → council moves toward a vote"
      ]
    },
    analystNote:
      "Polocity would summarize the map as a simple ‘covered / not covered’ signal with neighborhood labels.",
    sources: [
      {
        label: "See Exhibits / attachments on the record",
        url: "https://seattle.legistar.com/LegislationDetail.aspx?ID=3011262&GUID=E6D86622-97D3-41AF-BCCD-A7794C171A2C"
      }
    ]
  },

  {
    id: 103,
    topic: "housing",
    neighborhood: ["Downtown", "South Lake Union"],
    title: "Late changes added right before the vote",
    when: "April 2017 · Amendments added",
    summary:
      "Right before the final vote, the Council added changes that adjusted how the policy would work.",
    why: [
      "<span class='emphasis'>Last-minute changes</span> can reshape the final outcome",
      "These changes are easy to miss because they’re separate documents"
    ],
    you:
      "If you followed earlier drafts, you could be working off outdated info unless you catch these updates.",
    outcome: { label: "Changed before vote", tone: "warn" },
    stage: 3,
    tags: ["🧩 Changes", "⚠️ Late update", "🏛️ Council"],
    details: {
      headline: "What changed (and why you’d miss it)",
      overview:
        "The city often posts amendments as separate files. That means the final version can differ from what people read earlier.",
      keyPoints: [
        "Amendments were posted as supporting documents",
        "Some were added after earlier versions circulated",
        "Tracking changes requires comparing files"
      ],
      whatChanged: [
        "The final version incorporated changes added close to decision time"
      ],
      timeline: [
        "Amendments posted → final language updated → vote happens"
      ]
    },
    analystNote:
      "Polocity would highlight the exact difference in plain language (what changed, who it affects, and why it matters).",
    sources: [
      {
        label: "Supporting documents (proposed amendments)",
        url: "https://seattle.legistar.com/LegislationDetail.aspx?ID=3011262&GUID=E6D86622-97D3-41AF-BCCD-A7794C171A2C"
      }
    ]
  },

  {
    id: 104,
    topic: "housing",
    neighborhood: ["Downtown", "South Lake Union"],
    title: "Approved: new rules for future development",
    when: "April 10, 2017 · Council vote",
    summary:
      "City Council approved the updated rules, including the affordable housing requirement, for Downtown and South Lake Union.",
    why: [
      "Sets long-term direction for <span class='emphasis'>growth</span> in major neighborhoods",
      "Makes affordable housing support part of future projects"
    ],
    you:
      "This doesn’t change today’s buildings — it shapes what gets built next and where.",
    outcome: { label: "Passed", tone: "ok" },
    stage: 4,
    tags: ["✅ Outcome", "🏠 Housing", "📍 Downtown/SLU"],
    details: {
      headline: "What happens after a “Pass”",
      overview:
        "Once council approves it, the policy moves to the Mayor. After it’s signed, it becomes the rule for future building permits.",
      keyPoints: [
        "Council approved the final package (including amendments)",
        "The map + rules together define what changes where",
        "Impacts show up through future permits and construction"
      ],
      whatChanged: [
        "The approved version includes late updates that may differ from earlier drafts"
      ],
      timeline: [
        "Council vote → sent to Mayor → signed → takes effect"
      ]
    },
    analystNote:
      "Polocity would show: what passed, what changed since last update, and what residents should expect next.",
    sources: [
      {
        label: "Ordinance listed on the record (125291)",
        url: "https://seattle.legistar.com/LegislationDetail.aspx?ID=3011262&GUID=E6D86622-97D3-41AF-BCCD-A7794C171A2C"
      }
    ]
  },

  {
    id: 105,
    topic: "housing",
    neighborhood: ["Downtown", "South Lake Union"],
    title: "Signed: policy becomes official",
    when: "April 14, 2017 · Signed by Mayor",
    summary:
      "The Mayor signed the ordinance, which made the new rules official going forward.",
    why: [
      "This is when the decision becomes <span class='emphasis'>real</span> for future projects",
      "People often notice impacts later—when construction starts"
    ],
    you:
      "If you’ve ever wondered ‘why is this happening?’ after construction begins, this is usually the moment behind it.",
    outcome: { label: "In effect", tone: "ok" },
    stage: 5,
    tags: ["🖊️ Signed", "🏗️ Construction", "🧭 What’s next"],
    details: {
      headline: "Why this step matters",
      overview:
        "A signature turns a decision into the city’s actual rulebook. After this, new projects must follow the updated rules.",
      keyPoints: [
        "Signed ordinance = official city policy",
        "Impacts show up over time (permits, new projects, construction patterns)",
        "Polocity ties later impacts back to this decision"
      ],
      whatChanged: [
        "The policy moved from decision to enforcement for future projects"
      ],
      timeline: [
        "Signed → becomes the rule for future building permits"
      ]
    },
    analystNote:
      "Polocity would send an optional ‘outcome notification’ here so people aren’t surprised later.",
    sources: [
      {
        label: "Signed ordinance listed on the record",
        url: "https://seattle.legistar.com/LegislationDetail.aspx?ID=3011262&GUID=E6D86622-97D3-41AF-BCCD-A7794C171A2C"
      }
    ]
  }
];

let stances = JSON.parse(localStorage.getItem("polocity_stances") || "{}");
let follows = JSON.parse(localStorage.getItem("polocity_follows") || "{}");

function toggleDark() {
  document.body.classList.toggle("dark");
  localStorage.setItem("polocity_dark", document.body.classList.contains("dark"));
}
if (localStorage.getItem("polocity_dark") === "true") {
  document.body.classList.add("dark");
}

function switchView(view, el) {
  document.getElementById("feedView").classList.toggle("active", view === "feed");
  document.getElementById("stancesView").classList.toggle("active", view === "stances");
  document.querySelectorAll(".tab").forEach(t => t.classList.remove("active"));
  el.classList.add("active");
}

function setStance(id, stance, btn) {
  stances[id] = stance;
  localStorage.setItem("polocity_stances", JSON.stringify(stances));
  [...btn.parentElement.children].forEach(b => b.classList.remove("active"));
  btn.classList.add("active");
  pulse(btn);
  render();
}

function toggleFollow(id, btn) {
  follows[id] = !follows[id];
  localStorage.setItem("polocity_follows", JSON.stringify(follows));
  btn.classList.toggle("on", !!follows[id]);
  btn.textContent = follows[id] ? "🔔 Following" : "🔔 Follow updates";
  pulse(btn);
  renderTopicBuckets();
}

function pulse(el){
  el.style.boxShadow = `0 0 0 6px var(--pulse)`;
  setTimeout(()=>{ el.style.boxShadow = ""; }, 220);
}

function renderNotifications() {
  const n = document.getElementById("notifications");
  const followed = items.filter(i => follows[i.id]);

  if (!followed.length) {
    n.innerHTML = `
      <div class="notification">
        Tip: open any card → <strong>Follow updates</strong> to get a clean “what changed” style alert.
      </div>
    `;
    return;
  }

  n.innerHTML = followed.map(i =>
    `<div class="notification">🔔 Following: <strong>${i.title}</strong> · You’ll get updates when outcomes change.</div>`
  ).join("");
}

function renderTopicBuckets() {
  const c = document.getElementById("topicBuckets");
  const counts = {};
  Object.keys(stances).forEach(id => {
    const i = items.find(x => x.id == id);
    if (i) counts[i.topic] = (counts[i.topic] || 0) + 1;
  });

  // also show how many are followed
  const followedCount = Object.values(follows).filter(Boolean).length;

  const bubbles = [];
  Object.entries(counts).forEach(([t,n]) => bubbles.push(`<div class="topic-bubble">🎯 ${t} · ${n}</div>`));
  if (followedCount) bubbles.push(`<div class="topic-bubble">🔔 following · ${followedCount}</div>`);

  c.innerHTML = bubbles.join("");
}

function renderStanceBuckets() {
  const c = document.getElementById("stanceBuckets");
  const counts = {};
  Object.entries(stances).forEach(([id, stance]) => {
    const i = items.find(x => x.id == id);
    if (!i) return;
    const key = `${i.topic} · ${stance}`;
    counts[key] = (counts[key] || 0) + 1;
  });

  c.innerHTML = Object.keys(counts).length
    ? Object.entries(counts).map(([k,v]) => `<div class="topic-bubble">${k} · ${v}</div>`).join("")
    : '<div class="feed-subtitle">Open any card → “View details” → react.</div>';
}

function renderStanceCards() {
  const container = document.getElementById("stanceCards");
  container.innerHTML = "";

  const grouped = {};
  Object.entries(stances).forEach(([id]) => {
    const item = items.find(i => i.id == id);
    if (!item) return;
    if (!grouped[item.topic]) grouped[item.topic] = [];
    grouped[item.topic].push(item);
  });

  if (!Object.keys(grouped).length) {
    container.innerHTML = '<div class="feed-subtitle">No items yet. Open any card → “View details” → react.</div>';
    return;
  }

  Object.entries(grouped).forEach(([topic, topicItems]) => {
    const section = document.createElement("div");
    section.innerHTML = `<div class="section-title">${topic}</div>`;
    topicItems.forEach(i => section.appendChild(card(i)));
    container.appendChild(section);
  });
}

function badgeHTML(i) {
  if (!i.outcome?.label) return "";
  const tone = i.outcome.tone || "info";
  const emoji = tone === "ok" ? "✅" : tone === "warn" ? "⚠️" : "ℹ️";
  return `<span class="badge ${tone}">${emoji} ${i.outcome.label}</span>`;
}

function tagsHTML(i) {
  if (!i.tags || !i.tags.length) return "";
  return `<div class="tag-row">${i.tags.map(t => `<span class="tag">${t}</span>`).join("")}</div>`;
}

function sourcesHTML(i) {
  if (!i.sources || !i.sources.length) return "";
  return `
    <div class="sources">
      ${i.sources.map(s => `<a href="${s.url}" target="_blank" rel="noopener noreferrer">↗ ${s.label}</a>`).join("")}
    </div>
  `;
}

function analystHTML(i) {
  if (!i.analystNote) return "";
  return `
    <div class="analyst-note">
      <div class="analyst-header">
        <span>Analyst note</span>
        <span class="verified"><span class="check">✓</span> Verified</span>
      </div>
      ${i.analystNote}
      ${sourcesHTML(i)}
    </div>
  `;
}

function stagePills(stage){
  const labels = ["1) Introduced","2) Map / scope","3) Changes","4) Vote","5) Signed"];
  return labels.map((lbl, idx)=>{
    const s = idx+1;
    return `<span class="step ${s===stage?'active':''}">${lbl}</span>`;
  }).join("");
}

function detailsHTML(i) {
  if (!i.details) return "";

  const d = i.details;
  const kp = (d.keyPoints || []).map(x => `<li>${x}</li>`).join("");
  const wc = (d.whatChanged || []).map(x => `<li>${x}</li>`).join("");
  const tl = (d.timeline || []).map(x => `<li>${x}</li>`).join("");

  const isFollowed = !!follows[i.id];

  return `
    <details class="details">
      <summary>
        <div style="display:flex;flex-direction:column;gap:2px;">
          <span>✨ Dig deeper</span>
          <span style="font-weight:700;font-size:.78rem;color:var(--text-muted);">
            See what changed • quick timeline • follow updates • react
          </span>
        </div>
        <div class="chev">⌄</div>
      </summary>

      <div class="details-body">
        <div class="details-headline">
          <span class="badge info">🧠 ${d.headline || "Details"}</span>
          <div class="progress">${stagePills(i.stage || 1)}</div>
        </div>

        <div class="detail-grid">
          <div class="detail-card">
            <div class="detail-title">🧾 The quick story</div>
            <div style="font-size:.92rem;line-height:1.45;">${d.overview || ""}</div>
          </div>

          <div class="detail-card">
            <div class="detail-title">✅ Key takeaways</div>
            <ul class="detail-list">${kp}</ul>
          </div>

          <div class="detail-card">
            <div class="detail-title">🔁 What changed</div>
            <ul class="detail-list">${wc}</ul>
          </div>

          <div class="detail-card">
            <div class="detail-title">🗓️ What happens next</div>
            <ul class="detail-list">${tl}</ul>
          </div>
        </div>

        <div class="quick-actions">
          <button class="pill ${isFollowed ? 'on' : ''}" onclick="toggleFollow(${i.id}, this)">
            ${isFollowed ? "🔔 Following" : "🔔 Follow updates"}
          </button>
          <a class="pill secondary" href="${(i.sources && i.sources[0] && i.sources[0].url) ? i.sources[0].url : '#'}"
             target="_blank" rel="noopener noreferrer">↗ Open source</a>
        </div>

        ${analystHTML(i)}

        <div class="stance">
          <button class="for ${stances[i.id]==='for'?'active':''}" onclick="setStance(${i.id},'for',this)">👍 For</button>
          <button class="against ${stances[i.id]==='against'?'active':''}" onclick="setStance(${i.id},'against',this)">👎 Against</button>
          <button class="unsure ${stances[i.id]==='unsure'?'active':''}" onclick="setStance(${i.id},'unsure',this)">🤔 Not sure</button>
        </div>
      </div>
    </details>
  `;
}

function card(i) {
  const d = document.createElement("div");
  d.className = "card";

  // vary gradient subtly
  const grad = (i.stage === 2) ? "var(--grad-c)" : (i.stage === 5) ? "var(--grad-b)" : "var(--grad-a)";
  d.style.setProperty("--card-grad", grad);

  // override background tint via ::before by swapping var (hack: set inline style used in CSS? not needed; kept lively)
  // Keep tags visible
  d.innerHTML = `
    <div class="card-top">
      <div>
        <h3>${i.title}</h3>
        <div class="meta">
          <span>⏱ ${i.when}</span>
          ${badgeHTML(i)}
        </div>
      </div>
    </div>

    ${tagsHTML(i)}

    <p class="summary">${i.summary}</p>

    <div class="why-block">
      <div class="why-title">Why this matters</div>
      <ul class="why-points">${(i.why || []).map(p => `<li>${p}</li>`).join("")}</ul>
    </div>

    <div class="you-block"><strong>Why this matters to you:</strong> ${i.you || ""}</div>

    ${detailsHTML(i)}
  `;
  return d;
}

function render() {
  renderNotifications();
  renderTopicBuckets();
  renderStanceBuckets();

  const home = document.getElementById("homeFeed");
  const all = document.getElementById("allFeed");
  home.innerHTML = "";
  all.innerHTML = "";

  // weight topics based on stances
  const weights = {};
  Object.keys(stances).forEach(id => {
    const it = items.find(x => x.id == id);
    if (it) weights[it.topic] = (weights[it.topic] || 0) + 1;
  });

  const ranked = [...items].sort((a,b) => (weights[b.topic] || 0) - (weights[a.topic] || 0));

  // Home feed: show 2 most relevant + prioritize followed
  const followedFirst = ranked.sort((a,b)=> (follows[b.id]===true) - (follows[a.id]===true));
  followedFirst.slice(0,2).forEach(i => home.appendChild(card(i)));

  items.forEach(i => all.appendChild(card(i)));

  renderStanceCards();
}

render();
</script>
</body>
</html>
