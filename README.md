# ⚙️ Automated Email Notifications (EST Timezone)

## 📌 Project Overview
An automated workflow developed in **Power Automate** to monitor a shared mailbox and trigger real-time notifications via **Microsoft Teams**.

The flow evaluates the arrival timestamp and day of the week in real time using the **Eastern Standard Time (EST)** zone. This prevents sending alerts during weekends or after hours, dynamically rescheduling the notification for the next business day at the start of the shift.

---

## 🛠️ Technologies & Connectors
- **Power Automate** (Cloud Flows)
- **Office 365 Shared Mailbox API**
- **Microsoft Teams Connector**
- **WQL / JSON Expressions (Date/Time manipulation and conditional logic)**

---

## 📐 Workflow Logic
1. **📩 Trigger:** A new email arrives in the shared mailbox.
2. **🌐 Timezone Conversion:** The arrival timestamp is instantly converted to **EST**.
3. **❓ Condition Evaluation:** The system checks if the current time is within business hours (**Mon-Fri, 8:00 AM - 5:00 PM EST**).
   - **🟢 If YES:** The **Microsoft Teams Bot** sends an immediate notification.
   - **🔴 If NO:** A logical expression calculates the exact time gap until the next business day at **8:00 AM EST**, holds the execution using a **Delay Until** action, and then sends the notification.
