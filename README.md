# 📋 BA Change Tracker

> A production-grade, single-file desktop web application for Business Analysts to track, manage and analyse IT change requests — built with vanilla HTML, CSS and JavaScript. No frameworks, no dependencies, no build step.

**Maintained by:** Aishwarya Rajeshirke — Business Analyst, IT Division  
**Version:** 3.0.0  
**Last Updated:** April 2025

---

## 📌 Table of Contents

- [Overview](#overview)
- [Live Demo](#live-demo)
- [Features](#features)
- [Screenshots](#screenshots)
- [Getting Started](#getting-started)
- [App Structure](#app-structure)
- [Pages & Modules](#pages--modules)
  - [Dashboard](#1-dashboard)
  - [Change Requests](#2-change-requests)
  - [Analytics](#3-analytics)
  - [Workflow](#4-workflow)
  - [Notifications](#5-notifications)
  - [Teams](#6-teams)
  - [Reports](#7-reports)
  - [Profile & Settings](#8-profile--settings)
- [Data Model](#data-model)
- [Change Request Lifecycle](#change-request-lifecycle)
- [Charts & Visualisations](#charts--visualisations)
- [Storage & Persistence](#storage--persistence)
- [Team Members](#team-members)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [Browser Support](#browser-support)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [Changelog](#changelog)
- [License](#license)

---

## Overview

The **BA Change Tracker** is a fully functional, offline-capable change management application designed for Business Analysts working in IT divisions. It provides a centralised dashboard to log, track, filter, analyse and report on change requests across the full ITIL-aligned change lifecycle.

Built as a **single HTML file** (~113 KB), it requires no server, no database, no npm install and no internet connection after the first load. Data is persisted in the browser's `localStorage`.

```
┌─────────────────────────────────────────────────────────────────┐
│  Technology Stack                                               │
│  ─────────────────────────────────────────────────────────────  │
│  Frontend    →  HTML5, CSS3, Vanilla JavaScript (ES6+)         │
│  Charts      →  SVG (hand-crafted, zero library)               │
│  Storage     →  Browser localStorage (JSON)                    │
│  Fonts       →  Sora + JetBrains Mono (Google Fonts)          │
│  Icons       →  Inline SVG                                     │
│  Framework   →  None                                           │
│  Build tool  →  None                                           │
└─────────────────────────────────────────────────────────────────┘
```

---

## Live Demo

Simply download `BA_Change_Tracker_Desktop.html` and open it in any modern browser:

```bash
# Clone the repository
git clone https://github.com/aishwarya-rajeshirke/ba-change-tracker.git

# Open in browser (macOS)
open ba-change-tracker/BA_Change_Tracker_Desktop.html

# Open in browser (Linux)
xdg-open ba-change-tracker/BA_Change_Tracker_Desktop.html

# Open in browser (Windows)
start ba-change-tracker/BA_Change_Tracker_Desktop.html
```

> **No npm install. No localhost. No configuration.** Just open and use.

---

## Features

### Core Functionality
| Feature | Description |
|---|---|
| 📋 **100 Pre-loaded CRs** | Real IT/business change requests across 8 types and 10 owners |
| ➕ **Create / Edit / Delete** | Full CRUD operations on any change request |
| 🔍 **Global Search** | Instant search across title, description, ID, owner and impact area |
| 🏷️ **Multi-filter** | Filter by status (Open, In Progress, In Review, Done, Rejected) or priority |
| 📤 **CSV Export** | One-click export of all 100 CRs to downloadable CSV |
| 💾 **Persistent Storage** | All data saved to `localStorage` — survives page refresh |

### Analytics & Reporting
| Feature | Description |
|---|---|
| 🥧 **Pie Chart** | SVG status distribution (Open / In Progress / Review / Done / Rejected) |
| 📊 **Bar Charts** | Changes by Priority, Type, Owner and Monthly Trend |
| 💫 **Completion Ring** | Animated SVG donut showing overall completion percentage |
| 📈 **Monthly Trend** | Jan–Jun 2025 CR creation volume per month |
| 📋 **6 Report Types** | Executive Summary, Detailed Log, Owner Performance, Risk Assessment, Monthly Summary, CSV |

### Workflow & Process
| Feature | Description |
|---|---|
| 🔄 **5-Stage Workflow** | Visual pipeline: Request → Approval → Development → Testing → Closure |
| 📐 **SLA Targets** | Per-stage time targets (2d / 5d / 14d / 5d / 2d) |
| 🚨 **Escalation Rules** | Defined triggers and exception handling procedures |
| 📍 **Live CR Distribution** | Real-time count of CRs at each workflow stage |

### Team & Profile
| Feature | Description |
|---|---|
| 👥 **Team Cards** | Per-member stats: total CRs, done count, completion rate % |
| ✉️ **Invite Member** | Add new team members with role and department |
| ✏️ **Edit Profile** | Update name, email, role, department, location |
| 🔒 **Change Password** | Password update with validation (8+ chars, match check) |
| 🔔 **Notifications** | 7 real notifications with read/unread state and toggle settings |

---

## Screenshots

```
┌────────────────────────────────────────────────────────────┐
│  DASHBOARD                                                  │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐     │
│  │ Total    │ │ Active   │ │ Completed│ │ Critical │     │
│  │   100   │ │    58    │ │    29    │ │    8     │     │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘     │
│  ┌──────────────────────────┐  ┌──────────────────────┐   │
│  │  Recent Change Requests  │  │   Status Pie Chart   │   │
│  │  CR-100 | ESG pipeline   │  │   🔵 Open     28%    │   │
│  │  CR-099 | Fraud detect.. │  │   🟡 Progress 24%    │   │
│  │  CR-098 | Compliance LMS │  │   🟣 Review   11%    │   │
│  │  ...                     │  │   🟢 Done     29%    │   │
│  └──────────────────────────┘  │   🔴 Rejected  8%    │   │
│                                └──────────────────────┘   │
└────────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────────┐
│  WORKFLOW PIPELINE                                          │
│  ┌─────────┐▶┌─────────┐▶┌─────────┐▶┌─────────┐▶┌──────┐│
│  │📝 Request│ │✅Approve│ │⚙️  Dev  │ │🧪 Test  │ │🏁 End││
│  │ Stage 1 │ │ Stage 2 │ │ Stage 3 │ │ Stage 4 │ │Stg 5 ││
│  │  Open   │ │ Review  │ │Progress │ │ Review  │ │ Done ││
│  │   28    │ │    6    │ │   24    │ │    5    │ │  29  ││
│  └─────────┘ └─────────┘ └─────────┘ └─────────┘ └──────┘│
└────────────────────────────────────────────────────────────┘
```

---

## Getting Started

### Prerequisites

- Any modern web browser (Chrome 90+, Firefox 88+, Edge 90+, Safari 14+)
- No Node.js, Python, or any server required

### Installation

```bash
# Option 1: Clone the full repo
git clone https://github.com/aishwarya-rajeshirke/ba-change-tracker.git
cd ba-change-tracker

# Option 2: Download just the HTML file
curl -O https://raw.githubusercontent.com/aishwarya-rajeshirke/ba-change-tracker/main/BA_Change_Tracker_Desktop.html

# Option 3: GitHub Releases
# Go to Releases → download BA_Change_Tracker_Desktop.html
```

### First Run

1. Open `BA_Change_Tracker_Desktop.html` in your browser
2. The app auto-loads with **100 pre-seeded change requests**
3. All data is stored in your browser's `localStorage` under key `ba_v3`
4. Any changes you make (add, edit, delete) persist across sessions

### Reset to Default Data

To reset to the original 100 change requests:

```javascript
// Open browser DevTools console (F12) and run:
localStorage.removeItem('ba_v3');
location.reload();
```

---

## App Structure

```
ba-change-tracker/
│
├── BA_Change_Tracker_Desktop.html   ← Entire application (single file)
├── README.md                        ← This documentation
├── CHANGELOG.md                     ← Version history
└── LICENSE                          ← MIT License
```

### Internal File Structure (within the HTML)

```
BA_Change_Tracker_Desktop.html
│
├── <head>
│   ├── Google Fonts (Sora, JetBrains Mono)
│   └── <style> — 600+ lines of CSS
│       ├── Layout (topbar, sidebar, content)
│       ├── Components (cards, badges, table, modal, toast)
│       ├── Charts (pie, bar, donut, progress ring)
│       └── Pages (dashboard, analytics, workflow, profile...)
│
├── <body>
│   ├── .topbar — Global header with search and user info
│   ├── .sidebar — Left navigation (8 pages)
│   ├── .content — Page container
│   │   ├── #page-dashboard
│   │   ├── #page-changes
│   │   ├── #page-analytics
│   │   ├── #page-workflow
│   │   ├── #page-notifications
│   │   ├── #page-teams
│   │   ├── #page-reports
│   │   └── #page-profile
│   └── Modals (add/edit, detail, profile, password, invite)
│
└── <script> — 700+ lines of JavaScript
    ├── DATA — 100 change request records
    ├── Storage (load/save to localStorage)
    ├── Navigation (switchPage)
    ├── Render functions (one per page)
    ├── Chart builders (makeBars, buildSVGPie)
    ├── CRUD operations (saveChange, deleteChange)
    ├── Modal controllers
    └── Utility (showToast, exportData)
```

---

## Pages & Modules

### 1. Dashboard

**Route:** Default / Home page

Provides an at-a-glance view of the entire change portfolio.

| Element | Description |
|---|---|
| Stat Cards (×4) | Total CRs, Active (Open + In Progress), Completed, Critical |
| Recent CRs Table | Last 8 updated change requests with ID, title, priority, status, owner |
| Status Pie Chart | SVG pie showing distribution across all 5 statuses |
| Owner Bar Chart | Top 5 owners ranked by number of assigned CRs |

**Key functions:**
```javascript
renderDashboard()   // Recalculates all stats and re-renders
```

---

### 2. Change Requests

**Route:** `nav-changes`

Full paginated table of all change requests with filtering, search and inline actions.

#### Filters Available
| Filter | Description |
|---|---|
| All | Show all 100 CRs |
| Open | Status = open |
| In Progress | Status = progress |
| In Review | Status = review |
| Done | Status = done |
| Rejected | Status = rejected |
| 🚨 Critical | Priority = critical (any status) |
| 🔴 High | Priority = high (any status) |

#### Table Columns
`ID` · `Title / Description` · `Type` · `Priority` · `Status` · `Owner` · `Impact Area` · `Updated` · `Actions`

#### Actions per Row
- **Edit** → Opens pre-filled Add/Edit modal
- **Del** → Confirms then permanently deletes
- **Click row** → Opens full detail modal with activity log

**Key functions:**
```javascript
renderChanges()       // Re-renders table with current filter + search
setFilter(f, el)      // Sets active filter chip and re-renders
globalSearchFn()      // Triggered on search input; switches to Changes page
```

---

### 3. Analytics

**Route:** `nav-analytics`

Six visual charts providing data-driven insights across all 100 CRs.

| Chart | Type | Data |
|---|---|---|
| Completion Rate | Animated SVG Donut | % of CRs with status = done |
| Status Distribution | SVG Pie Chart | Count per status with % labels |
| Changes by Priority | Horizontal Bar | Critical / High / Medium / Low counts |
| Changes by Type | Horizontal Bar | 8 types: Technical, Business, Regulatory... |
| Changes by Owner | Horizontal Bar | All 9 team members ranked by CR count |
| Monthly Trend | Horizontal Bar | CR creation count: Jan–Jun 2025 |

All bars animate in on page load using CSS transitions with `data-w` percentage attributes.

**Key functions:**
```javascript
renderAnalytics()     // Renders all 6 charts
makeBars(id, entries) // Generic bar chart renderer: [[label, count, color], ...]
buildSVGPie(id, dataMap, colors) // SVG pie chart with legend
```

---

### 4. Workflow

**Route:** `nav-workflow`

The core BA value-add page. Documents and visualises the full change lifecycle.

#### Pipeline Stages

```
📝 Request → ✅ Approval → ⚙️ Development → 🧪 Testing → 🏁 Closure
  Stage 1       Stage 2        Stage 3          Stage 4      Stage 5
  (Open)        (CRB Review)   (In Progress)    (UAT)        (Done)
```

#### Stage Detail Cards

Each stage card includes 5 bullet points covering:
- Who initiates / owns the stage
- What activities happen
- BA's specific responsibilities
- Tools / systems involved
- Output / exit criteria

#### SLA Targets

| Stage | Target |
|---|---|
| Request Submission | 2 days |
| Approval Decision | 5 days |
| Development Sprint | 14 days |
| UAT Testing | 5 days |
| Closure & Sign-off | 2 days |
| **Total End-to-End** | **~28 days** |

#### Live CR Distribution

Real-time cards showing how many CRs are currently sitting at each stage, calculated from live data.

#### Escalation Rules

- Critical CRs not approved within 24h → auto-escalate to IT Director
- Any CR in Development >21 days → flag to Project Manager
- UAT defects unresolved after 3 days → escalate to Dev Lead
- No stakeholder sign-off after 5 days → reschedule closure review

#### Exception Handling

- **Emergency (P0):** Bypass CRB, get verbal approval, document post-facto
- **Scope Creep:** Raise new CR; do not expand existing
- **Rejected CRs:** May be resubmitted after addressing CRB feedback
- **Regulatory CRs:** Require compliance officer signature before closure

---

### 5. Notifications

**Route:** `nav-notifications`

In-app notification centre with read/unread state.

**7 pre-loaded notifications** covering:
- CR escalations
- Status changes
- CRB approvals
- SLA breach warnings
- Weekly digest summaries

**Notification Settings (toggles):**
| Setting | Default |
|---|---|
| Email Alerts (Critical only) | ON |
| Browser Push (All status changes) | ON |
| Weekly Digest (Monday 9AM) | OFF |
| Slack Integration (#changes) | OFF |

**Key functions:**
```javascript
renderNotifications()  // Renders notification list with read/unread styling
markRead(id)           // Marks single notification as read
markAllRead()          // Marks all notifications as read
toggleSetting(el)      // Toggles on/off for notification preferences
```

---

### 6. Teams

**Route:** `nav-teams`

Team member management with real workload statistics.

#### Team Members (9 default)

| Name | Role | Department |
|---|---|---|
| Aishwarya Rajeshirke | Business Analyst | IT Division |
| Dev Patel | Senior Developer | Engineering |
| Priya Mehta | Project Manager | PMO |
| Sara Lim | UX Designer | Design |
| Rohit Sharma | Financial Analyst | Finance |
| Ananya Iyer | Data Analyst | Data & Analytics |
| Karan Joshi | IT Service Manager | IT Operations |
| Neha Roy | QA Engineer | Quality |
| Vikram Singh | Infrastructure Lead | IT Infrastructure |

#### Per-Member Stats Card Shows:
- Total CRs assigned
- CRs completed (Done)
- Completion rate %
- Animated progress bar

#### Actions:
- **Edit** → Toast confirmation (extensible to modal)
- **Remove** → Confirm dialog → removes from team list
- **Invite Member** → Modal with Name, Email, Role, Department

---

### 7. Reports

**Route:** `nav-reports`

Six report generation options:

| Report | Format | Description |
|---|---|---|
| Executive Summary | PDF | KPIs, completion rates for leadership |
| Detailed Change Log | PDF | All CRs with full descriptions and audit trail |
| Owner Performance | PDF | Per-owner breakdown with completion rates |
| Export to CSV | CSV | All 100 CRs downloadable for Excel/Power BI |
| Risk Assessment | PDF | Critical and high-priority open CRs |
| Monthly Summary | PDF | This month's CRs by type, status, priority |

> **Note:** PDF generation shows a toast confirmation. To implement actual PDF export, integrate with a library such as `jsPDF` or `html2pdf.js`.

---

### 8. Profile & Settings

**Route:** `nav-profile`

User account management and app settings.

#### Profile Card
- Name, role, department, email
- Stats: Total CRs, Done, On-Time %
- Account details: Employee ID, Location, Join Date, Last Login

#### Settings Panel (all clickable)

| Setting | Action |
|---|---|
| Edit Profile | Opens modal with Name, Email, Role, Department, Location fields |
| Notifications | Navigates to Notifications page |
| Manage Teams | Navigates to Teams page |
| Export Reports | Navigates to Reports page |
| Change Password | Opens modal with current/new/confirm fields + validation |
| Sign Out | Confirmation dialog |

---

## Data Model

Each change request follows this schema:

```javascript
{
  id:       "CR-001",           // Auto-incremented, zero-padded string
  title:    "Migrate legacy CRM to Salesforce",
  desc:     "Full migration of on-premise CRM...",
  priority: "critical",         // critical | high | medium | low
  status:   "progress",         // open | progress | review | done | rejected
  type:     "Business",         // Technical | Business | Regulatory | Process |
                                // UI/UX | Data | Infrastructure | Security
  owner:    "Aishwarya Rajeshirke",
  impact:   "CRM, Sales Team",  // Affected systems / areas
  created:  "2025-01-08",       // ISO date string (YYYY-MM-DD)
  updated:  "2025-01-08",       // ISO date string (YYYY-MM-DD)
  log: [                        // Activity log array
    { text: "Change request created and logged", time: "2025-01-08" },
    { text: "Priority set to critical, assigned to ...", time: "2025-01-08" }
  ]
}
```

### Status Flow

```
open ──────→ progress ──→ review ──→ done
  │                                    ↑
  └──────────────────────────→ rejected
```

### Priority Levels

| Priority | Usage | Colour |
|---|---|---|
| `critical` | System down, compliance deadline, data breach risk | 🔴 Red |
| `high` | Significant business impact, approaching deadline | 🟡 Yellow |
| `medium` | Normal business change, planned improvement | 🔵 Blue |
| `low` | Minor change, housekeeping, cosmetic update | 🟢 Green |

### Change Types

| Type | Examples |
|---|---|
| Technical | API changes, upgrades, migrations, architecture |
| Business | Process changes, new capabilities, cost savings |
| Regulatory | GDPR, PCI-DSS, ISO 27001, tax compliance |
| Process | Workflow redesign, automation, SOP updates |
| UI/UX | Interface redesign, accessibility, mobile |
| Data | Pipelines, dashboards, data quality, ML models |
| Infrastructure | Cloud, servers, network, DevOps |
| Security | IAM, EDR, vulnerability management, MFA |

---

## Change Request Lifecycle

```
┌─────────────────────────────────────────────────────────────────────┐
│                    FULL CR LIFECYCLE                                │
│                                                                     │
│  1. STAKEHOLDER identifies business need                           │
│          ↓                                                          │
│  2. BA captures requirements and creates CR (Status: OPEN)         │
│          ↓                                                          │
│  3. CR submitted to Change Review Board (CRB)                      │
│          ↓                    ↓                                     │
│     [APPROVED]           [REJECTED] ──→ CR closed / resubmitted   │
│          ↓                                                          │
│  4. Development team picks up CR (Status: IN PROGRESS)             │
│          ↓                                                          │
│  5. Build complete → QA + BA testing in UAT (Status: IN REVIEW)    │
│          ↓                    ↓                                     │
│    [TEST PASS]          [DEFECTS FOUND] ──→ Back to Development    │
│          ↓                                                          │
│  6. Stakeholder sign-off obtained                                   │
│          ↓                                                          │
│  7. Production deployment executed                                  │
│          ↓                                                          │
│  8. Post-implementation review + documentation (Status: DONE)      │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Charts & Visualisations

All charts are built with **pure SVG and CSS** — no Chart.js, D3 or any external library.

### SVG Pie Chart

```javascript
buildSVGPie(containerId, dataMap, colors)
// dataMap: { "open": 28, "progress": 24, "review": 11, "done": 29, "rejected": 8 }
// Renders: SVG with arc paths + legend with percentages
```

**How it works:**
1. Calculates each segment's arc angle: `(value / total) * 2π`
2. Uses `M cx,cy L x1,y1 A r,r 0 largeArcFlag,1 x2,y2 Z` SVG path
3. Renders legend with `legend-dot` + label + count (%)

### Horizontal Bar Chart

```javascript
makeBars(containerId, entries)
// entries: [["Label", count, "var(--accent)"], ...]
// Renders: animated bars using CSS width transition from 0% to data-w%
```

### SVG Donut / Progress Ring

```javascript
// Completion ring uses SVG stroke-dashoffset animation
// stroke-dasharray = 2πr = 2 * π * 44 ≈ 276
// stroke-dashoffset = 276 * (1 - percentage/100)
```

---

## Storage & Persistence

The app uses `localStorage` with key `ba_v3`.

```javascript
// Data is stored as a JSON array of change request objects
localStorage.setItem('ba_v3', JSON.stringify(changes));

// On load, existing data is restored; if absent, 100 seed records are used
const raw = localStorage.getItem('ba_v3');
if (raw) changes = JSON.parse(raw);
else { changes = seedData(); save(); }
```

### Storage Limits

| Browser | localStorage Limit |
|---|---|
| Chrome / Edge | ~5 MB |
| Firefox | ~10 MB |
| Safari | ~5 MB |

The full 100-CR dataset is approximately **80 KB** serialised — well within all browser limits.

### Data Reset

```javascript
// In browser DevTools console:
localStorage.removeItem('ba_v3');
location.reload();
```

---

## Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl/Cmd + F` | Focus global search bar |
| `Escape` | Close any open modal |
| `Enter` (in form) | Submit form (where applicable) |

> Extended keyboard shortcuts can be added via `document.addEventListener('keydown', ...)` in the script section.

---

## Browser Support

| Browser | Version | Support |
|---|---|---|
| Chrome | 90+ | ✅ Full |
| Edge | 90+ | ✅ Full |
| Firefox | 88+ | ✅ Full |
| Safari | 14+ | ✅ Full |
| Opera | 76+ | ✅ Full |
| IE 11 | — | ❌ Not supported |

**Required browser features:**
- CSS Custom Properties (variables)
- CSS Grid and Flexbox
- ES6+ (arrow functions, template literals, destructuring, spread)
- `localStorage` API
- SVG rendering
- `Blob` + `URL.createObjectURL` (for CSV export)

---

## Deployment

### Option 1: Static File (Simplest)

Just share the `.html` file directly. Recipients open it locally in their browser.

```bash
# Share via email, Teams, Slack, SharePoint, OneDrive, etc.
# Recipient opens the file — no installation needed.
```

### Option 2: GitHub Pages

```bash
# 1. Push to GitHub
git init
git add BA_Change_Tracker_Desktop.html README.md
git commit -m "Initial commit: BA Change Tracker v3.0"
git remote add origin https://github.com/YOUR_USERNAME/ba-change-tracker.git
git push -u origin main

# 2. Enable GitHub Pages
# Repository → Settings → Pages → Source: main branch → / (root)
# App available at: https://YOUR_USERNAME.github.io/ba-change-tracker/BA_Change_Tracker_Desktop.html
```

### Option 3: Nginx / Apache (Team Intranet)

```nginx
# nginx.conf
server {
    listen 80;
    server_name ba-tracker.internal.company.com;
    root /var/www/ba-change-tracker;
    index BA_Change_Tracker_Desktop.html;
    location / {
        try_files $uri $uri/ =404;
    }
}
```

### Option 4: SharePoint / Confluence Embed

Upload the HTML file to SharePoint and embed in a page using the **Embed web part** or use Confluence's HTML macro.

> ⚠️ Note: Some SharePoint configurations restrict inline JavaScript. Test before deployment.

---

## Contributing

### Branching Strategy

```
main          ← Production-ready, stable
develop       ← Integration branch
feature/*     ← New features (e.g. feature/add-gantt-chart)
fix/*         ← Bug fixes (e.g. fix/notification-render)
docs/*        ← Documentation updates
```

### Commit Convention

```
feat: add Gantt chart view for active CRs
fix: resolve notification template literal syntax error
docs: update README with deployment options
style: improve mobile responsiveness for analytics page
refactor: extract chart rendering into separate module
```

### Pull Request Process

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Make changes to `BA_Change_Tracker_Desktop.html`
4. Test in Chrome, Firefox and Edge
5. Validate JS syntax: copy `<script>` block into browser DevTools console
6. Update `README.md` if adding new features
7. Submit PR with a clear description of changes

### Adding New Change Requests

To add more seed data, extend the `RAW_CHANGES` array:

```javascript
// Format: [title, description, priority, status, type, owner, impact, date]
['Your change title', 
 'Detailed description of the business change', 
 'high',           // critical | high | medium | low
 'open',           // open | progress | review | done | rejected
 'Technical',      // type
 'Dev Patel',      // owner (must match OWNERS array)
 'API Gateway',    // impact area
 '2025-05-01']     // created date YYYY-MM-DD
```

### Adding a New Page

1. Add nav item to sidebar HTML:
```html
<div class="nav-item" onclick="switchPage('mypage')" id="nav-mypage">
  <svg>...</svg>
  <span class="nav-label">My Page</span>
</div>
```

2. Add page container:
```html
<div class="page" id="page-mypage">
  <!-- page content -->
</div>
```

3. Add render function:
```javascript
function renderMypage() {
  // populate page content
}
```

4. Register in `switchPage()`:
```javascript
const renders = {
  // ... existing
  mypage: renderMypage,
};
```

---

## Changelog

### v3.0.0 — April 2025
- ✨ Added 100 real IT/business change requests (replacing 8 sample records)
- ✨ Added SVG Pie Chart for status distribution (Analytics + Dashboard)
- ✨ Added Changes by Owner bar chart (all 9 team members)
- ✨ Added Monthly Trend chart (Jan–Jun 2025)
- ✨ Added full Workflow page with 5-stage pipeline diagram
- ✨ Added SLA targets, escalation rules and exception handling
- ✨ Added live CR distribution across workflow stages
- ✨ Added team cards with per-member completion stats
- 🐛 Fixed broken template literal in `renderNotifications()` (syntax error causing blank app)
- 🐛 Fixed `localStorage` key collision — updated to `ba_v3`

### v2.0.0 — March 2025
- ✨ Desktop layout with sidebar navigation
- ✨ All profile settings made clickable with real modals
- ✨ Edit Profile, Change Password, Invite Member modals
- ✨ Changed user to Aishwarya Rajeshirke / Business Analyst
- ✨ Teams page with workload distribution
- ✨ 6 report types in Reports page

### v1.0.0 — February 2025
- 🚀 Initial release as mobile web app
- ✨ 4-tab mobile interface (Dashboard, Changes, Analytics, Profile)
- ✨ Add/Edit/Delete change requests
- ✨ Basic status and priority filtering
- ✨ localStorage persistence
- ✨ CSV export

---



---


</div>
