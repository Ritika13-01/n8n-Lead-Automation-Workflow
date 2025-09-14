📌 Workflow Overview

🔹 Trigger

Schedule Trigger runs daily at 9:00 AM IST (example in JSON shows 03:30 UTC).

🔹 Lead Collection

Uses HTTP Request node to fetch leads from a mock API:
👉 https://jsonplaceholder.typicode.com/users

🔹 Data Processing

A Code (JavaScript) node extracts and cleans required fields:

name

email (defaults to "not provided" if missing)

company

phone

Adds enrichment fields:

lead_source = "n8n-internship-assignment"

created_at = today's date (YYYY-MM-DD)

🔹 Storage

Google Sheets node appends processed leads into a Sheet.

Example columns:

name	email	company	phone	lead_source	created_at

🔹 Notifications

(Optional extension) Send a Slack / Telegram / Email notification:

"X new leads added today"

Include a link to the Google Sheet.

🔹 Error Handling

If the workflow fails, an Error Workflow sends an alert email to the admin.

⚙️ Setup Instructions

Clone / Import Workflow

Import the provided JSON file into your n8n instance.

Google Sheets Setup

Create a Google Sheet with headers:

name | email | company | phone | lead_source | created_at


Connect your Google account in n8n → Credentials → Google Sheets.

Test Run

Run the workflow manually first (click ▶ Run).

Verify rows are appended to your Sheet.

Enable Schedule

Activate the workflow so it runs daily at 9 AM IST.

🧪 How to Test

Run manually → check rows in Google Sheet.

Disable internet → confirm error email is triggered.

Remove email field from API data → confirm "not provided" appears in the sheet.
