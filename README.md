# n8n AI Hospital Outreach Automation

AI-powered outreach automation built with n8n for UAE hospital Wi-Fi campaigns.  
This workflow drafts human-tone emails using GPT, applies intro variation logic, schedules controlled sending windows, and delivers through Outlook with safe delay intervals.

---

## 🚀 Overview

This project automates first-touch outreach emails for hospitals & clinics in the UAE using:

- n8n (workflow automation)
- OpenAI GPT (email drafting)
- Microsoft Outlook (email delivery)
- Google Sheets (lead tracking & status control)

The system focuses on:
- Human-sounding email tone
- Intro variation to prevent repetition
- Controlled daily sending limits
- Random delay intervals to avoid spam detection
- Morning/Afternoon scheduling windows

---

## 🧠 Features

### ✅ AI Email Drafting
- GPT-based generation
- Department-aware language level
- Non-sales, conversational tone
- Single-problem focused messaging
- One service mention per email

### ✅ Humanization Controls
- Randomized intro line rotation
- Natural sentence rhythm
- Soft closing question
- Strict signature formatting

### ✅ Sending Logic
- Sunday–Thursday only
- Two sending windows:
  - 08:30–10:30 (UAE)
  - 14:00–16:00 (UAE)
- 30 emails per mailbox per day
- Random delay (6–10 minutes) between emails
- No burst sending

### ✅ Lead Management
- Pulls only "Pending" rows from Google Sheets
- Updates row status after sending
- Prevents duplicate outreach

---

## 🏗 Workflow Architecture

Schedule Trigger  
↓  
Google Sheets (Get Rows – Pending)  
↓  
Limit (15 per window)  
↓  
Loop Over Items (Batch Size = 1)  
↓  
Generate Intro (Randomizer Code Node)  
↓  
GPT Draft Email  
↓  
Update Google Sheet (Status → Sent/Drafted)  
↓  
Outlook Send  
↓  
Random Delay Generator  
↓  
Wait Node  
↓  
Back to Loop

---

## ⚙️ Tech Stack

- n8n (Cloud)
- OpenAI GPT-5.2
- Microsoft Graph (Outlook)
- Google Sheets API
- JavaScript Code Nodes (intro + delay randomization)

---

## 🔐 Environment Requirements

Before running:

- OpenAI API Key
- Outlook OAuth credentials
- Google Sheets OAuth credentials
- n8n Cloud instance

---

## 🛠 Setup Instructions

1. Import the workflow JSON into n8n.
2. Configure credentials:
   - OpenAI
   - Microsoft Outlook
   - Google Sheets
3. Update sheet ID and column mappings.
4. Set your timezone (UAE GMT+4 recommended).
5. Publish the workflow.

---

## 📊 Sending Strategy

| Setting | Value |
|----------|--------|
| Days | Sunday–Thursday |
| Morning Window | 08:30–10:30 |
| Afternoon Window | 14:00–16:00 |
| Daily Emails | 30 per mailbox |
| Delay | Random 6–10 minutes |

---

## 🎯 Campaign Goal

To generate warm conversations with UAE hospitals by:

- Addressing real Wi-Fi issues
- Maintaining a human tone
- Avoiding spam-trigger language
- Using structured automation with natural variation

---

## ⚠️ Notes

- Signature images are not included by default (text-based signature recommended for deliverability).
- Always test with a low limit before full production rollout.
- Monitor Outlook sending limits and API usage.


