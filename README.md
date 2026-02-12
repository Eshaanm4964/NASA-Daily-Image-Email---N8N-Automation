**🚀 Daily NASA APOD Mailer**

An automated email system that sends NASA's Astronomy Picture of the Day (APOD) to subscribed users at their chosen time.

Built using n8n, Google Sheets, and Gmail automation.

**🌌 Project Overview**

This project allows users to:

📩 Subscribe using a form

⏰ Choose a preferred delivery time

🛰 Receive NASA's APOD image daily via email

The system uses two automation workflows:

Form Workflow → Collects user data

Schedule Workflow → Sends daily emails

**🏗 Architecture**
User Form Submission
        ↓
Google Sheets (Database)
        ↓
Scheduled Workflow (runs daily)
        ↓
NASA APOD API
        ↓
Email Sent via Gmail

**🛠 Tech Stack**

**n8n **– Workflow automation

**Google Sheets** – Subscriber database

**NASA APOD API** – Daily image source

**Gmail Node **– Email delivery

**Form Trigger (n8n)** – Subscription form

📋** Workflow Breakdown**
🟢 **Workflow 1:** Subscription Collector

Trigger:

Form Trigger

**Flow:**

Form Submission → Append Row in Google Sheets


**Stores:**

email

activation_time

active (TRUE/FALSE)

**🔵 Workflow 2: Daily Email Sender**

**Trigger:**

Schedule Trigger (runs periodically)

**Flow:**

Schedule → NASA API Request → Get Rows from Sheet
        → Check Time + Active Status
        → Send Email


**Logic:**

Sends email only if:

activation_time matches current time

active = TRUE

**📊 Google Sheet Structure**
email	activation_time	active
test@gmail.com
	08:00	TRUE

Both workflows use the same sheet.

**🔑 NASA API Used**
https://api.nasa.gov/planetary/apod?api_key=YOUR_API_KEY


**You will need a free API key from:**
https://api.nasa.gov

**⚙️ Setup Instructions**

Clone this repository

Import the workflows into n8n

Connect:

Google Sheets credentials

Gmail credentials

Add your NASA API key

Activate both workflows

**🔐 Production Notes**

Workflows are separated for clean architecture

Google Sheets acts as the shared database

Form and Schedule triggers operate independently

Easy to scale or migrate to a real database later

**🚀 Possible Improvements**

Add unsubscribe feature

Store timezone per user

Add duplicate email protection

Move from Sheets → PostgreSQL

Add email formatting (HTML template)

**📌 Future Expansion**

This project can be extended into:

A general newsletter automation platform

Multi-topic subscription system

SaaS automation product

**👨‍💻 Author**

Built as a learning + automation project using n8n.
