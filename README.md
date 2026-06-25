# PA Analytics Dashboard

A standalone, single-file prior authorization analytics dashboard. No server, no install, no build step required — just open in a browser.

## How to use

1. **Export your SharePoint PA tracking list to Excel**
   - In SharePoint → your PA list → **Export → Export to Excel**
   - Save the `.xlsx` file to your computer

2. **Open the dashboard**
   - Download `pa-analytics.html` (or `index.html` if in the `pa-analytics/` folder)
   - Open it directly in Chrome, Edge, or Safari
   - No internet connection required after the page loads

3. **Load your data**
   - Click **Load Excel / CSV** in the sidebar (or drag and drop your file onto the Overview page)
   - Data is processed entirely in your browser — nothing is uploaded anywhere

4. **AI insights (optional)**
   - Go to the **AI insights** tab
   - Enter your DeepSeek API key (get one free at [platform.deepseek.com/api-keys](https://platform.deepseek.com/api-keys))
   - Your key is saved in your browser's local storage so you only need to enter it once
   - Ask questions in plain English about your PA data

---

## Supported SharePoint columns

The dashboard automatically maps these SharePoint column names:

| SharePoint Column | Dashboard field |
|---|---|
| Title | Patient name |
| Insurance | Payer / Insurance |
| PA Status | Status |
| Urgency | Priority |
| Medication | Medications (numeric codes after `;` are stripped) |
| Order Provider | Provider |
| Due | Due date |
| Decision Date | Decision date |
| Note | Notes |
| Created | Submission timeline |
| DOB | Date of birth |
| Assigned To | Assigned to |
| Item Type, Path | Ignored |

---

## Dashboard pages

- **Overview** — 4 metric cards (total, approved, denied, pending) + 4 charts (status breakdown, submissions over time, by urgency, top payers)
- **Case log** — filterable table with all cases; filter by status, payer, urgency, provider, or search by patient name
- **AI insights** — plain English Q&A about your PA data powered by DeepSeek
- **By payer** — volume and approved vs denied breakdown per insurance
- **By medication** — top requested medications (numeric codes automatically stripped)
- **By provider** — case volume per ordering provider

---

## Deploying to Netlify

To host this as a subpage (e.g. `yoursite.netlify.app/pa-analytics/`):

1. Place the file at `pa-analytics/index.html` in your project alongside your existing `index.html`
2. Deploy via Netlify drag-and-drop or Git push
3. Your original site at `/` is unaffected

---

## Tech stack

- Vanilla HTML / CSS / JavaScript — no framework, no build step
- [Chart.js 4.4.1](https://www.chartjs.org/) — charts
- [SheetJS (xlsx 0.18.5)](https://sheetjs.com/) — Excel/CSV parsing
- [DeepSeek API](https://platform.deepseek.com/) — AI insights (optional)

---

## Privacy

All data stays in your browser. The Excel file is read locally using the browser's File API — no data is sent to any server unless you use the AI insights feature, which sends an anonymized summary (counts and breakdowns, not individual patient records) to the DeepSeek API.
