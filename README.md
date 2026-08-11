# HisabKitab

A personal expense tracker, built around a real household budget spreadsheet. Runs entirely in the browser — no backend, no account, no build step. All data stays on your device via `localStorage`.

## Modules

**Monthly Budget**
- Income calculated from a configurable formula (e.g. `Considered Salary - (Abba + Abba Home Rent)`)
- Needs, Wants, and Savings sections with per-category budget vs. spend, editable percentage targets, and progress bars
- Amount fields accept arithmetic — type `1383+1092` and it sums automatically on Enter/blur
- "Copy last month's budget" carries forward category budgets (skipping anything with no budget assigned) at zero spend
- Rich-text Notes with bold/italic/underline/bullets
- Collapsible Configurations panel for one-time settings

**Special Monthly Expenses**
- Table 1: Eid Expenses, Qurbani, Travel, and Medical funds (HDFC Bank) — each tracks an opening balance, this month's contribution, and itemized expenses, with the balance rolling forward month to month
- Table 2: Zakat (Canara Bank) — opening balance, monthly contribution, and itemized disbursements (recipient/cause + amount)
- "Pull opening balances" carries each fund's closing balance into the new month

Both modules include a month switcher and autosave as you type.

## Using it

Just open `index.html` in a browser — everything (React, Tailwind, icons) loads from CDN, so an internet connection is needed the first time a page loads, but your data itself is stored locally on your device.

## Deploying it yourself

**GitHub Pages** (this repo): Settings → Pages → deploy from the `main` branch, root folder. GitHub will give you a URL like `https://<username>.github.io/hisabkitab/`.

**On iPhone**: open that URL in Safari → Share icon → **Add to Home Screen**, for a full-screen, app-like icon.

## Data & privacy

All data is stored locally in your browser (`localStorage`, under keys prefixed `hisabkitab:`). Nothing is sent to a server. Clearing your browser's site data for this page will erase it — there's no cloud backup, so export or note down anything important if you plan to clear browser data or switch devices.

## Notes

- August 2026 comes pre-seeded with real figures from the original spreadsheet this app was built from.
- Built with React, Tailwind CSS, and a small set of custom icons — all loaded via CDN, no `npm install` required.
