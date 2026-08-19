# HisabKitab

A personal expense tracker, built around a real household budget spreadsheet. Runs entirely in the browser — no backend, no account. All data stays on your device via `localStorage`. Installable as a home-screen app on iPhone (and any modern browser) via "Add to Home Screen."

## Modules

**1. Monthly Budget**
- Income calculated from a configurable formula (e.g. `Considered Salary - (Abba + Abba Home Rent)`), with any number of named configuration values you can add yourself
- Needs, Wants, and Savings sections with per-category budget vs. spend, editable percentage targets, and progress bars
- Amount fields accept arithmetic — type `1383+1092` and it sums automatically on Enter/blur
- "Copy last month's budget" carries forward category budgets (skipping anything with no budget assigned) at zero spend
- Rich-text Notes with bold/italic/underline/bullets
- Collapsible Configurations panel for one-time settings

**2. Special Monthly Expenses**
- Four funds — Eid Expenses, Qurbani, Travel, and Medical (Special Occasion & Medical Funds, HDFC Bank) — shown as widget cards in a 2×2 grid, each with its own opening balance, this month's contribution, and an itemized expense table; balances roll forward month to month
- Zakat (Canara Bank) — opening balance, monthly contribution, and itemized disbursements (recipient/cause + amount)
- "Pull opening balances" carries each fund's closing balance into the new month

**3. Monthly Balance after Expenses**
- Opening balance, amount transferred to the bank (HDFC) this month, and an itemized, dated log of larger one-off purchases
- Running closing balance carries forward month to month via "Pull opening balance"

**4. Credit Cards**
- Two tables — Axis Bank and ICICI Bank — tracking transaction details, amount, and a Cleared toggle
- Cleared transactions highlight green and drop out of the "outstanding" total shown at the top of each card

All four modules include a month switcher and autosave as you type.

## Importing your spreadsheet

Every module has a **"Load from spreadsheet"** button that opens a file picker — select your `.xlsx` file and it parses it directly in the browser (no server, nothing uploaded anywhere). It recognizes any sheet named like a month ("Aug 26", "Sept 24", "June 23", etc., including inconsistent abbreviations) and imports all of them at once, across all four modules' worth of data, from a single upload. You only need to do this once, from any module.

## Using it

Just open `index.html` in a browser — React, Tailwind, and the app itself all load from the same files, no build step, no `npm install`.

## Installing it like an app (iPhone)

1. Open your deployed URL (e.g. GitHub Pages) in **Safari**
2. Tap the **Share** icon
3. Tap **Add to Home Screen**

This uses the included `manifest.json` and app icons to launch full-screen with no browser bar, like a normal installed app.

## Deploying it yourself

**GitHub Pages**: push all files to a repo — `index.html`, `app.js`, `styles.css`, `manifest.json`, `icon-180.png`, `icon-192.png`, `icon-512.png` — then Settings → Pages → deploy from the `main` branch, root folder. GitHub will give you a URL like `https://<username>.github.io/hisabkitab/`.

## Data & privacy

All data is stored locally in your browser (`localStorage`, under keys prefixed `hisabkitab:`). Nothing is sent to a server, including when importing a spreadsheet — parsing happens entirely on-device. Clearing your browser's site data for this page will erase it — there's no cloud backup, so export or note down anything important if you plan to clear browser data or switch devices.

## Notes

- August 2026 comes pre-seeded with real figures from the original spreadsheet this app was built from.
- Built with React, Tailwind CSS, and a small set of custom icons, all bundled directly into `app.js`/`styles.css` — no CDN dependency at runtime, no `npm install` required.
