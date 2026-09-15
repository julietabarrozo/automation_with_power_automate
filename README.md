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

```mermaid
graph TD;
    A[📩 New Email in Shared Mailbox] --> B{Is it a business day & working hours?<br/>Mon-Fri, 8:00 AM - 5:00 PM EST};
    B -- Yes (True) --> C[🔔 Immediate Teams Notification];
    B -- No (False) --> D[🧮 Calculate Days to Add];
    D --> E[⏳ Delay Until: Wait until 08:00 AM next business day];
    E --> F[🔔 Scheduled Teams Notification];
