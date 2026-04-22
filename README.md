# sdci-permit-dashboard
Active SDCI construction permits across our Seattle development portfolio, updated automatically each morning. Review cycles, reviewer assignments, and upcoming deadlines tracked in real time.

# Seattle Permit Tracker

**A free tool for Seattle real estate developers.**
*Shared by [Advantage Realty Advisors LLC](https://advantage-realty-advisors.com).*

---

## What it does

Automatically checks your SDCI construction permits every morning at 7 AM and gives you:

- **A branded dashboard** of your entire permit portfolio, opened in your browser
- **A daily Slack and/or email summary** with any overnight status changes
- **Instant visibility** when reviewers flip a discipline to *Corrections Required* or *Approved*

You never need to log into the Seattle Services Portal again.

### Example dashboard

Every permit gets a card showing review cycle, due date, active reviews, and reviewer assignments — with a "View on SDCI portal" button to jump to the underlying record. Mobile-friendly so you can check status from anywhere.

### Example Slack message

```
Permit Status - Wed Apr 22

• 1234 Main St (7100545-CN) — Cycle 2, due 05/01/2026, 8 active, 1 change
    ↳ Drainage: 'Pending Assignment' -> 'Assigned' (Jessica Batterman)
• 🔴 5678 Oak Ave (7100718-CN) — Corrections Required (action needed)
```

---

## Setup (5 minutes)

1. **Unzip** this folder somewhere permanent, like `C:\Users\YourName\Documents\PermitTracker\`
2. **Double-click `install.bat`** — it will:
   - Walk you through adding your permit URLs
   - Ask for a Slack webhook URL (optional)
   - Ask for email SMTP credentials (optional)
   - Register a Windows task to run every morning at 7 AM
   - Run your first permit check and open your dashboard in the browser
3. **Done.** Your dashboard lives at `dashboard\index.html` and updates daily.

No Python installation needed — everything runs from the bundled files.

---

## Optional: share your dashboard publicly

If you want a public URL to share your dashboard with investors, architects,
lenders, or partners, run **`enable_publishing.bat`**. A wizard walks you through
publishing to GitHub Pages (free, takes ~10 minutes). After that, every daily
update auto-publishes and anyone with the URL can view live permit status.

This step is entirely optional. The local dashboard works just fine without it.

---

## What you need before starting

- **Your permit URLs.** Go to [services.seattle.gov](https://services.seattle.gov), search for your permit, and copy the full URL from the browser.
- **A Slack webhook URL** (optional). The installer walks you through creating one.
- **Email SMTP credentials** (optional). Gmail users need an [App Password](https://support.google.com/accounts/answer/185833).

---

## Daily workflow

Once installed, the tracker runs by itself. You get your first status update at
7 AM the morning after install. To test manually, double-click `run_checker.bat`
at any time — it'll rescrape everything, update your dashboard, and post to
Slack/email if configured.

---

## Disclaimer

**This is provided free, as-is, with no support or guarantees.**

The Seattle Services Portal occasionally changes its HTML structure. When that
happens, this tool may stop working or return incomplete data until it's updated.
Since this is shared as a free goodwill tool, there's no maintenance commitment.

This tool doesn't collect any data, doesn't phone home, and runs entirely on your
local machine. Your config (including Slack webhook and email credentials) lives
only in `config.ini` on your computer.

---

## Troubleshooting

- **Task didn't run at 7 AM** → Open Task Scheduler, find "Seattle Permit Tracker", check the History tab. Machine must be on (or set to wake) with network access.
- **Slack post didn't appear** → Run `run_checker.bat` manually and watch for error messages.
- **Missing disciplines or empty statuses** → The portal HTML may have changed.
- **Dashboard shows old data** → The 7 AM run refreshes it; or run `run_checker.bat` manually.
- **Lost your setup** → Delete `config.ini` and re-run `install.bat`.

---

## Feedback

Found a bug or have a suggestion? Reach out to Alex Hiebert at
Advantage Realty Advisors. No promises on turnaround, but improvements will be
rolled back into the shared version when possible.
