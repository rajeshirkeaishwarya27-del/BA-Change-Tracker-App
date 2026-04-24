# Changelog

All notable changes to **BA Change Tracker** are documented in this file.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).  
Versioning follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [3.1.0] — 2025-04-24

### Added
- Full authentication system with **Sign In** and **Create Account** tabs on a single card
- `Create Account` form — First Name, Last Name, Work Email, Password, Confirm Password
- Live **password strength indicator** (4-bar meter: Weak / Fair / Good / Strong) with colour coding
- Registered users persisted to `localStorage` under key `ba_tracker_users`
- Session persisted under key `ba_tracker_session` — survives page refresh
- **Sign Out confirmation modal** — polished in-app dialog (replaces browser `confirm()`)
- **Topbar logout button** — red arrow icon always visible in the top-right corner, regardless of active page
- Profile → Settings → Sign Out now fully functional, triggers the same confirmation modal
- `doLogin()` distinguishes between "wrong password" and "email not found" with specific error messages
- `doRegister()` validates duplicate emails, password length ≥ 8 chars, and password match
- `showForgot()` — Forgot Password flow triggered from Sign In panel; validates email field first
- `togglePwVis()` — show/hide password toggle on both Sign In and Create Account password fields
- `authTab()` — smooth tab switcher between Sign In and Create Account panels
- Card shake animation on validation errors
- Welcome toast on successful sign-in: *"Welcome back, [First Name]! 👋"*
- Account creation toast: *"Account created! Welcome, [First Name]! 🎉"*

### Changed
- Login screen redesigned from single panel to **two-tab card** (Sign In / Create Account)
- Removed unprofessional "DEMO CREDENTIALS" autofill tile from login screen
- `confirmSignOut()` now shows a styled modal instead of a raw browser `confirm()` dialog
- Login screen fade-out animation on successful auth (opacity + scale transition)
- HTML file size updated: ~113 KB → ~140 KB

### Fixed
- Sign Out previously only showed a toast with no actual session termination — now clears session and returns to login screen
- `togglePwVis()` refactored to accept `inputId` and `iconId` parameters — supports multiple password fields simultaneously

---

## [3.0.0] — 2025-04-24

### Added
- 100 real IT/business change requests seeded (replacing 8 placeholder records)
- SVG Pie Chart for status distribution on Analytics page and Dashboard sidebar
- Changes by Owner bar chart covering all 9 team members ranked by CR volume
- Monthly Trend bar chart showing Jan–Jun 2025 CR creation volume
- Full Workflow page with 5-stage visual pipeline (Request → Approval → Development → Testing → Closure)
- Stage Detail Cards with 5 activity bullets per stage including BA responsibilities
- SLA Targets section: 2d / 5d / 14d / 5d / 2d per stage
- Live CR Distribution cards showing real-time count per workflow stage
- Escalation Rules and Exception Handling documentation in Workflow page
- Per-member stat cards in Teams page: total CRs, done count, completion rate %, animated progress bar
- `renderWorkflow()` function wired to nav and `switchPage()`

### Fixed
- **Critical:** Broken template literal in `renderNotifications()` — a `]` character instead of `}` caused a JavaScript syntax error that prevented the entire application from loading
- `localStorage` key updated from `ba_changes_v2` to `ba_v3` to avoid conflicts with previous versions

### Changed
- Dashboard sidebar now shows Status Pie Chart and Top 5 Owners bar chart (replacing plain activity feed)
- Analytics page expanded from 4 to 6 charts
- Teams page upgraded from list cards to grid cards with workload statistics
- Completion ring radius adjusted (r=44) for better proportions at 110px size

---

## [2.0.0] — 2025-03-15

### Added
- Full desktop layout with fixed sidebar navigation replacing mobile bottom tabs
- Edit Profile modal with fields: First Name, Last Name, Email, Job Title, Department, Location, Photo upload
- Change Password modal with current/new/confirm fields and validation (min 8 chars, match check)
- Invite Member modal for Teams page
- 6 report types on Reports page (Executive Summary, Detailed Log, Owner Performance, Risk, Monthly, CSV)
- Settings panel on Profile page — all 6 items now clickable with real actions
- Manage Teams page navigable from Profile settings
- Export Reports navigates to Reports page from Profile settings
- Sign Out confirmation dialog

### Changed
- User name updated from Alex Kumar → **Aishwarya Rajeshirke**
- Role updated from Senior Business Analyst → **Business Analyst**
- Default owner in Add modal updated to Aishwarya Rajeshirke
- CSV export filename updated to `BA_Changes_Aishwarya_Rajeshirke.csv`
- Topbar user pill shows full name and role

### Fixed
- Profile settings items (Edit Profile, Notifications, Manage Teams, Export Reports) were previously non-functional — all now open correct modals or navigate to correct pages

---

## [1.0.0] — 2025-02-01

### Added
- Initial release as a mobile-first web application
- 4-tab navigation: Dashboard, Changes, Analytics, Profile
- 8 sample change requests with realistic IT scenarios
- Add / Edit / Delete change requests via bottom sheet modal
- Status filtering: All, Open, In Progress, In Review, Done, Critical
- Global search across title, description, ID and owner
- `localStorage` persistence under key `ba_changes_v2`
- CSV export of all change requests
- Completion rate donut ring on Analytics page
- Bar charts for Priority, Type, Owner breakdown
- Real-time clock in mobile status bar
- Ripple tap effect on interactive cards
- Toast notification system
- Mobile-optimised layout (max-width 430px)

---

[3.1.0]: https://github.com/aishwarya-rajeshirke/ba-change-tracker/compare/v3.0.0...v3.1.0
[3.0.0]: https://github.com/aishwarya-rajeshirke/ba-change-tracker/compare/v2.0.0...v3.0.0
[2.0.0]: https://github.com/aishwarya-rajeshirke/ba-change-tracker/compare/v1.0.0...v2.0.0
[1.0.0]: https://github.com/aishwarya-rajeshirke/ba-change-tracker/releases/tag/v1.0.0
