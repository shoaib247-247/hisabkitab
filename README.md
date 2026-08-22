# HisabKitab

A personal expense tracker, built around a household budget spreadsheet. Runs entirely in the browser — no backend, no account, no sign-up. All data stays on your device via `localStorage`. Installable as a home-screen app (iPhone, Android, or desktop) via "Add to Home Screen."

## Modules

**1. Monthly Budget**
- Income calculated from a configurable formula (e.g. `Salary - (Rent + Other Deductions)`) built from any number of named values you define yourself under Configurations
- Needs, Wants, and Savings sections with per-category budget vs. spend, editable percentage targets, and progress bars
- Amount fields accept arithmetic, and include a **+** button next to each one (since phone number keypads don't have a plus key) — tap it to insert `+` and keep typing, e.g. `500` → **+** → `300` sums to `800` automatically
- "Copy Last Month Budget" carries forward category budgets (skipping anything with no budget assigned) at zero spend
- Rich-text Notes with bold/italic/underline/bullet-list formatting
- Configurations panel (income formula, named values, Needs/Wants/Savings percentages) has explicit **Save** and **Cancel** buttons — nothing changes until you save, so a wrong edit can always be discarded
- **Export Data** downloads a real `.xlsx` file for the currently viewed month, named with that month and year (e.g. `HisabKitab-March-2026.xlsx`) — built directly in the browser, no server involved. It includes that month's data from **all four modules** in one file: Budget Summary, Budget Detail, Special Expenses, Monthly Balance, and Credit Cards
- An annual bar chart at the bottom shows that year's month-by-month total spend at a glance

**2. Special Monthly Expenses**
- Any number of sinking funds (e.g. seasonal or occasional expense categories) shown as widget cards in a grid, each with its own opening balance, this month's contribution, and an itemized expense table; balances roll forward month to month
- A dedicated fund card for tracking contributions and itemized disbursements toward a specific recurring obligation
- "Pull Opening Balances" carries each fund's closing balance into the new month automatically

**3. Monthly Balance after Expenses**
- Opening balance, amount transferred to savings/bank this month, and an itemized, dated log of larger one-off purchases
- Running closing balance carries forward month to month via "Pull Opening Balance"

**4. Credit Cards**
- One table per card you want to track, logging transaction details, amount, and a Cleared toggle
- Cleared transactions highlight green and drop out of the "outstanding" total shown at the top of each card

All four modules include a month switcher and autosave as you type — nothing is lost switching between months.

## Importing your spreadsheet

Every module has an **"Import Data"** / **"Load From Spreadsheet"** option that opens a file picker — select your `.xlsx` file and it's parsed directly in the browser (nothing is uploaded anywhere). It recognizes any sheet named like a month (e.g. "Jan 24", "September 25", handling inconsistent abbreviations), and imports all matching months at once, populating all four modules' worth of data from a single upload. You only need to do this once, from any module.

## Using it

Just open `index.html` in a browser. Everything the app needs — the interface, styling, and icons — is bundled directly into `app.js` and `styles.css`; there's no build step and no external service required to run it.

## Installing it like an app (iPhone)

1. Open your deployed URL (e.g. GitHub Pages) in **Safari**
2. Tap the **Share** icon
3. Tap **Add to Home Screen**

This uses the included `manifest.json` and app icons to launch full-screen with no browser address bar, like a normally installed app.

## Deploying it yourself

**GitHub Pages**: push all files to a repo — `index.html`, `app.js`, `styles.css`, `manifest.json`, `icon-180.png`, `icon-192.png`, `icon-512.png` — then Settings → Pages → deploy from the `main` branch, root folder. GitHub will give you a URL like `https://<username>.github.io/<repo-name>/`.

## Data, privacy & backups

All data is stored locally in your browser (`localStorage`), scoped to the exact URL you're using. Nothing is ever sent to a server, including when importing a spreadsheet — parsing happens entirely on-device.

A few things worth knowing:
- **Each device/browser has its own separate copy.** There's no automatic sync between your phone and laptop — installing the app on a second device starts with empty data there.
- **Clearing your browser's "site data" or "browsing data" (not just history) for this page will erase it.** There's no cloud backup.
- Use **Export Data** periodically as a safety net — it gives you an offline copy of everything, independent of the browser.
- Because the app's code (this repo's files) and your data (browser storage) are entirely separate, deploying an update to the app **never** erases or resets your existing data.

## Notes

- Built with React, Tailwind CSS, and a small custom icon set, all bundled directly into `app.js`/`styles.css` — no CDN dependency at runtime, no `npm install` required.
- The `.xlsx` export/import logic is hand-written (no third-party spreadsheet library), so it works fully offline with zero dependencies.
