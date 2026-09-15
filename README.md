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
graph TD
    A[📩 Trigger: Shared Mailbox Email] --> B[🌐 Convert Timestamp to EST]
    B --> C{❓ Is it business hours?<br/>Mon-Fri, 8:00 AM - 5:00 PM EST}
    
    C -- YES --> D[🔔 Teams Bot: Immediate Notification]
    
    C -- NO --> E[🧮 Logic Expression: Evaluate day & calculate delay]
    E --> F[⏳ Delay Until: Wait until 08:00 AM next business day]
    F --> G[🔔 Teams Bot: Scheduled Notification]

    style A fill:#0078D4,color:#fff
    style C fill:#f3f2f1,stroke:#333
    style D fill:#107C41,color:#fff
    style G fill:#107C41,color:#fff


