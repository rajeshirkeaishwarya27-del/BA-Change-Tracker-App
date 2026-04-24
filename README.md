# 📋 BA Change Tracker

> A production-grade, single-file desktop web application for Business Analysts to track, manage and analyse IT change requests — built with vanilla HTML, CSS and JavaScript. No frameworks, no dependencies, no build step.

**Maintained by:** Aishwarya Rajeshirke — Business Analyst, IT Division  
**Version:** 3.1.0  
**Last Updated:** April 2025

---

## 📌 Table of Contents

- [Overview](#overview)
- [Live Demo](#live-demo)
- [Features](#features)
- [Authentication](#authentication)
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

Built as a **single HTML file** (~140 KB), it requires no server, no database, no npm install and no internet connection after the first load. Data is persisted in the browser's `localStorage`.

```
┌─────────────────────────────────────────────────────────────────┐
│  Technology Stack                                               │
│  ─────────────────────────────────────────────────────────────  │
│  Frontend    →  HTML5, CSS3, Vanilla JavaScript (ES6+)         │
│  Charts      →  SVG (hand-crafted, zero library)               │
│  Storage     →  Browser localStorage (JSON)                    │
│  Auth        →  localStorage-based user registry + sessions    │
│  Fonts       →  Sora + JetBrains Mono (Google Fonts)          │
│  Icons       →  Inline SVG                                     │
│  Framework   →  None                                           │
│  Build tool  →  None                                           │
└─────────────────────────────────────────────────────────────────┘
```

---

## Live Demo

Simply download `index.html` and open it in any modern browser:

```bash
# Clone the repository
git clone https://github.com/aishwarya-rajeshirke/ba-change-tracker.git

# Open in browser (macOS)
open ba-change-tracker/index.html

# Open in browser (Linux)
xdg-open ba-change-tracker/index.html

# Open in browser (Windows)
start ba-change-tracker/index.html
```

> **No npm install. No localhost. No configuration.** Just open and use.

---

## Features

### Authentication
| Feature | Description |
|---|---|
| 🔐 **Sign In** | Email + password login with session persistence |
| 📝 **Create Account** | Register with name, work email and password |
| 💪 **Password Strength** | Live 4-bar strength meter (Weak / Fair / Good / Strong) |
| 👁️ **Show/Hide Password** | Toggle visibility on all password fields |
| 🔑 **Forgot Password** | In-app reset flow with email validation |
| 🚪 **Sign Out** | Confirmation modal accessible from topbar and Profile page |
| 💾 **Session Persistence** | Stay logged in across page refreshes |

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

## Authentication

The app includes a full client-side authentication system built on `localStorage`.

### Sign In

1. Open `index.html` — the login screen appears automatically
2. Enter your registered **email** and **password**
3. Click **Sign In**

If you enter an email that doesn't exist, the error message will direct you to create an account instead of a generic "incorrect credentials" message.

### Create Account

1. Click the **Create Account** tab on the login screen
2. Fill in: First Name, Last Name, Work Email, Password, Confirm Password
3. Password requirements: minimum 8 characters
4. The live strength meter shows **Weak / Fair / Good / Strong** as you type
5. Click **Create Account** — you're logged in immediately

Registered accounts are stored in `localStorage` under key `ba_tracker_users` and persist indefinitely in the browser.

### Sign Out

Sign out from either location:
- **Topbar** — click the red logout arrow icon (top-right, always visible)
- **Profile page** → Settings → Sign Out

Both trigger a confirmation modal. On confirm, your session is cleared and you're returned to the login screen.

### Forgot Password

1. Enter your email address in the Sign In panel
2. Click **Forgot password?**
3. A confirmation message appears (in a real deployment, this would send an email)

### localStorage Keys Used by Auth

| Key | Contents |
|---|---|
| `ba_tracker_users` | Array of all registered user objects |
| `ba_tracker_session` | Currently logged-in user object |
| `ba_v3` | Change request data (app data, separate from auth) |

### Resetting Auth Data

```javascript
// In browser DevTools console (F12):

// Remove all registered accounts
localStorage.removeItem('ba_tracker_users');

// Clear current session (forces login screen on reload)
localStorage.removeItem('ba_tracker_session');

// Reset everything
localStorage.clear();
location.reload();
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
curl -O https://raw.githubusercontent.com/aishwarya-rajeshirke/ba-change-tracker/main/index.html

# Option 3: GitHub Releases
# Go to Releases → download index.html
```

### First Run

1. Open `index.html` in your browser — the **login screen** appears
2. Click **Create Account** and register with your details
3. You're logged in and the app loads with **100 pre-seeded change requests**
4. All data is stored in your browser's `localStorage`
5. Any changes you make (add, edit, delete) persist across sessions

### Reset to Default Data

To reset change requests to the original 100 records:

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
├── index.html       ← Entire application (single file, ~140 KB)
├── README.md        ← This documentation
├── CHANGELOG.md     ← Version history
└── LICENSE          ← MIT License
```

### Internal File Structure (within the HTML)

```
index.html
│
├── <head>
│   ├── Google Fonts (Sora, JetBrains Mono)
│   └── <style> — 650+ lines of CSS
│       ├── Layout (topbar, sidebar, content)
│       ├── Components (cards, badges, table, modal, toast)
│       ├── Charts (pie, bar, donut, progress ring)
│       └── Pages (dashboard, analytics, workflow, profile...)
│
├── <body>
│   ├── #loginScreen — Auth overlay (Sign In / Create Account)
│   ├── .topbar — Global header with search, notifications, logout
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
│   ├── Modals (add/edit, detail, profile, password, invite)
│   └── #signOutModal — Sign out confirmation dialog
│
└── <script> — 800+ lines of JavaScript
    ├── AUTH — Sign in, register, sign out, session management
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

---

### 4. Workflow

**Route:** `nav-workflow`

Visual 5-stage change lifecycle pipeline with SLA targets, escalation rules, and live CR counts per stage.

#### Pipeline Stages

```
📝 Request → ✅ Approval → ⚙️ Development → 🧪 Testing → 🏁 Closure
  Stage 1       Stage 2        Stage 3          Stage 4      Stage 5
```

#### SLA Targets

| Stage | Target |
|---|---|
| Request Submission | 2 days |
| Approval Decision | 5 days |
| Development Sprint | 14 days |
| UAT Testing | 5 days |
| Closure & Sign-off | 2 days |
| **Total End-to-End** | **~28 days** |

---

### 5. Notifications

**Route:** `nav-notifications`

In-app notification centre with read/unread state and toggle settings.

---

### 6. Teams

**Route:** `nav-teams`

Team member management with real workload statistics and per-member completion rates.

---

### 7. Reports

**Route:** `nav-reports`

Six report generation options: Executive Summary, Detailed Log, Owner Performance, Risk Assessment, Monthly Summary, CSV Export.

---

### 8. Profile & Settings

**Route:** `nav-profile`

User account management. Settings panel includes Edit Profile, Change Password, Notifications, Manage Teams, Export Reports, and Sign Out.

---

## Data Model

Each change request follows this schema:

```javascript
{
  id:       "CR-001",
  title:    "Migrate legacy CRM to Salesforce",
  desc:     "Full migration of on-premise CRM...",
  priority: "critical",   // critical | high | medium | low
  status:   "progress",   // open | progress | review | done | rejected
  type:     "Business",
  owner:    "Aishwarya Rajeshirke",
  impact:   "CRM, Sales Team",
  created:  "2025-01-08",
  updated:  "2025-01-08",
  log: [
    { text: "Change request created and logged", time: "2025-01-08" }
  ]
}
```

---

## Storage & Persistence

| Key | Purpose |
|---|---|
| `ba_v3` | All change request records (JSON array) |
| `ba_tracker_users` | Registered user accounts (JSON array) |
| `ba_tracker_session` | Active session / logged-in user (JSON object) |

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

---

## Deployment

### Option 1: Static File (Simplest)

Share the `index.html` file directly. Recipients open it locally — no installation needed.

### Option 2: GitHub Pages

```bash
git init
git add index.html README.md CHANGELOG.md LICENSE
git commit -m "feat: BA Change Tracker v3.1.0 with auth"
git remote add origin https://github.com/aishwarya-rajeshirke/ba-change-tracker.git
git push -u origin main
# Enable GitHub Pages → Settings → Pages → Source: main → / (root)
```

### Option 3: SharePoint / Intranet

Upload `index.html` to SharePoint and embed via the **Embed web part**, or serve from an internal Nginx/Apache server.

---

## Changelog

### v3.1.0 — April 2025
- 🔐 Added full authentication: Sign In, Create Account, Sign Out
- 📝 Create Account with name, email, password + confirm
- 💪 Live password strength meter (Weak / Fair / Good / Strong)
- 🚪 Sign Out confirmation modal — topbar button + Profile settings
- 🔑 Forgot Password flow with email validation
- 💾 Session persists across page refreshes via `localStorage`
- 🐛 Fixed Sign Out (previously toast-only, now clears session and returns to login)

### v3.0.0 — April 2025
- ✨ 100 real IT/business change requests
- ✨ SVG Pie Chart, Owner bar chart, Monthly Trend chart
- ✨ Full Workflow page with 5-stage pipeline
- ✨ SLA targets, escalation rules, live CR distribution
- ✨ Team cards with per-member completion stats
- 🐛 Fixed critical syntax error in `renderNotifications()`

### v2.0.0 — March 2025
- ✨ Desktop layout with sidebar navigation
- ✨ All profile settings made functional
- ✨ Edit Profile, Change Password, Invite Member modals
- ✨ Updated to Aishwarya Rajeshirke / Business Analyst

### v1.0.0 — February 2025
- 🚀 Initial mobile-first release
- ✨ Add/Edit/Delete CRs, filtering, search, CSV export

---

## License

MIT License — Copyright (c) 2025 Aishwarya Rajeshirke

---

## Contact

**Aishwarya Rajeshirke**  
Business Analyst — IT Division  
📧 aishwarya.rajeshirke@company.com  
📍 Pune, Maharashtra, India  

---

<div align="center">

**BA Change Tracker** — Built with ❤️ for Business Analysts

*No frameworks. No dependencies. Just clean HTML, CSS and JavaScript.*

</div>
