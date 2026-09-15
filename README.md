# ⚙️ Automated Email Notifications

## 📌 Project Overview
An automated workflow developed in **Power Automate** to monitor a shared mailbox and trigger real-time notifications via **Microsoft Teams**.

The flow evaluates the arrival timestamp and day of the week in real time to prevent sending alerts during weekends or after hours, dynamically rescheduling the notification for the next business day at the start of the shift.

---

## 🛠️ Technologies & Connectors
- **Power Automate** (Cloud Flows)
- **Office 365 Shared Mailbox API**
- **Microsoft Teams Connector**
- **WQL / JSON Expressions (Date/Time manipulation and conditional logic)**

---

## 📐 Workflow Architecture
[📩 Trigger: Shared Mailbox Email]
       │
       ▼
[🌐 Timezone Conversion] ─────► Convert UTC to EST (Eastern Standard Time)
       │
       ▼
[❓ Business Hours Check] ────► Is it Mon-Fri AND between 8:00 AM - 5:00 PM?
       │
       ├──────► [YES] ──► 🔔 [Immediate Action]
       │                  Send instant Teams notification to assigned analyst
       │
       └──────► [NO]  ──► 🧮 [Delayed Action]
                          1. Calculate days to add (handles weekend logic)
                          2. Pause execution until 08:00 AM next business day
                          3. 🔔 Send scheduled Teams notification

