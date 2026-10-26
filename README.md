# Spendwise – expense tracker

React + Vite, Chart.js, Firebase (Auth + Firestore).

## Features
- Email/password login; each user's data is private (see firestore.rules)
- Import a bank-statement CSV (Date, Description, Debit/Amount columns) or add expenses by hand
- Auto-categorises by merchant keywords (src/categorize.js) – change any category from the table
- Charts: spend by category, daily spend vs limit, weekdays vs weekends
- Monthly report with category breakdown (print / save as PDF)
- Daily limit: notification the moment you go over, and an evening notification if you stayed under

- Smart insights, subscription detector, no-spend streak, delete/re-categorise, dark mode

## Included
- `src/` the React app, `firestore.rules`, `.env.example`
- `sample-statement.csv` realistic Aug-Oct 2026 statement to import
- `standalone/spendwise.html` single-file version that runs without Firebase (data kept in the browser)

## Setup
1. Create a Firebase project; enable Authentication (Email/Password) and Firestore.
2. Copy `.env.example` to `.env` and fill in your web-app config.
3. Paste `firestore.rules` into Firestore > Rules.
4. `npm install` then `npm run dev`

## Notes
- Notifications use the browser Notification API, so the tab must be open. For alerts while the app is closed,
  add Firebase Cloud Messaging + a scheduled Cloud Function that runs the same over/under check.
- Statement formats differ per bank; adjust the column regexes in `src/utils.js` if yours isn't detected.
- Sample CSV: sample-statement.csv
