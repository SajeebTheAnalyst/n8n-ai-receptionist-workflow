# 🤖 Multi-Channel & Voice AI Receptionist Automation Workflow

[![n8n](https://img.shields.io/badge/Orchestration-n8n-FF6D5A?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io)
[![Gemini AI](https://img.shields.io/badge/AI_Engine-Gemini_Pro-8E75B2?style=for-the-badge&logo=googlegemini&logoColor=white)](https://ai.google.dev/)
[![GreenAPI](https://img.shields.io/badge/WhatsApp-GreenAPI-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://green-api.com)
[![Meta](https://img.shields.io/badge/Social-Facebook_%26_Instagram-0081FB?style=for-the-badge&logo=meta&logoColor=white)](https://developers.facebook.com)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)

An end-to-end **Multi-Channel & Voice AI Receptionist Workflow** engineered with **n8n**, **Gemini AI**, and **Voice Speech-to-Text Pipeline**. Built for hospitality and service industries (specifically customized for **Mollywood Resort**), this system operates 24/7 across **WhatsApp, Facebook Messenger, Instagram DM, Telegram, and Voice Notes/Calls** to handle room bookings, dining orders, customer inquiries, and real-time database synchronization without human intervention.

---

## 📸 Workflow Architecture

![n8n Workflow Diagram](./Workflow.png)

---

## 🔥 Key Features

### 🎙️ 1. Multilingual Voice & Speech Processing
* **Voice Note & Call Automation:** Converts incoming voice messages (Bangla, English, Banglish) into text via Speech-to-Text (STT) models.
* **Contextual Voice Response:** Synthesizes natural audio replies for voice inquiries alongside text responses.

### 💬 2. Unified Multi-Channel Messaging
* **Cross-Platform Integration:** Single n8n routing engine handles WhatsApp (GreenAPI), Facebook Messenger, Instagram DM, and Telegram API.
* **Smart Intent Recognition:** Dynamically categorizes customer intents into `booking`, `order`, or `general_faq`.

### 🗓️ 3. Dynamic Date & Timestamp Standardizer
* **Relative Expression Resolution:** Resolves conversational time expressions (e.g., *"পরশু রাত ৮টায়"*, *"tomorrow afternoon"*) into standardized database ISO formats (`YYYY-MM-DD HH:mm AM/PM`).
* **Scheduling Accuracy:** Prevents scheduling overlaps and timezone mismatch errors in backend records.

### 📊 4. Database Persistence & Admin Alert System
* **Google Sheets Sync:** Automatically logs validated customer info (Name, Phone, Email, Requested Items/Rooms, Date) into Google Sheets.
* **Real-time Telegram Notifications:** Triggers instant, unbranded alert cards directly to the resort manager's Telegram bot upon order or reservation placement.

### 🛡️ 5. Robust Fallback & Guardrails
* **Clarification Engine:** Asks clarifying questions if required parameters (e.g., Phone number or Check-in date) are missing instead of writing incomplete `N/A` records.

---

## 🛠️ Tech Stack

* **Workflow Orchestration:** [n8n](https://n8n.io)
* **LLM & Reasoning Engine:** Google Gemini AI / OpenAI API
* **Speech-to-Text / Voice AI:** Whisper API / Gemini Multimodal Voice Processing
* **Messaging APIs:** GreenAPI (WhatsApp), Meta Graph API (Messenger/Instagram), Telegram Bot API
* **Data Storage:** Google Sheets API
* **Scripting Language:** JavaScript (Node.js syntax inside n8n Code Nodes)

---

## 📐 System Pipeline Flow

1. **Customer Input:** Receives incoming messages via Text, Voice Note, or Audio Call across WhatsApp, Messenger, Instagram, or Telegram.
2. **n8n Webhook Listener:** Triggers the workflow and captures payload metadata.
3. **Voice-to-Text Processing:** Automatically converts audio messages to text if the input is voice-based.
4. **AI Reasoning Agent:** Gemini AI processes context and identifies customer intent (`booking`, `order`, or `inquiry`).
5. **Dynamic Routing:**
   * **Inquiries:** Generates instant contextual AI response directly to user.
   * **Bookings/Orders:** Extracts structured details (Customer Name, Phone, Serving Date, Items/Cottage).
6. **Database Persistence:** Automatically appends structured JSON data to Google Sheets DB.
7. **Instant Admin Notification:** Fires clean Telegram alert card to resort owner's dashboard in real-time.

---

## 🚀 Setup & Installation

### Prerequisites
* Self-hosted or Cloud **n8n** instance (v1.x+)
* **GreenAPI Account** with active WhatsApp Instance
* **Meta Developer Account** for Messenger/Instagram Webhooks
* **Google Cloud Console** credentials for Google Sheets API
* **Telegram Bot Token** & Chat ID

### Quick Start Guide

#### Step 1: Clone the Repository
```bash
git clone https://github.com/SajeebTheAnalyst/n8n-ai-receptionist-workflow.git
cd n8n-ai-receptionist-workflow
```

#### Step 2: Import Workflow to n8n
* Open your n8n dashboard.
* Click **Workflows** ➔ **Import from File**.
* Select `Mollywood Resort - Multi Channel Messaging.json`.

#### Step 3: Configure Credentials
* **Google Sheets:** Authenticate via OAuth2 or Service Account.
* **Telegram API:** Enter your Telegram Bot Access Token.
* **GreenAPI:** Add your `instanceId` and `apiTokenInstance`.
* **Gemini / OpenAI API:** Insert your API Key under AI Credentials.

#### Step 4: Activate Webhooks
* Set your Webhook HTTP method to `POST` for production.
* Toggle workflow state to **Active / Published**.

---

## 📝 Environment & Webhook Configuration

| Service | Webhook Path / Parameter | Key Settings |
| :--- | :--- | :--- |
| **WhatsApp (GreenAPI)** | `/webhook` | `incomingWebhook` = **Enabled**, `outgoingWebhook` = **Disabled** |
| **Meta Graph API** | `/webhook` | Verify Token validation required on setup via `GET` |
| **Telegram** | Bot API Endpoint | Direct chat_id routing for instant alerts |

---

## 👨‍💻 Author

**Md Mosaddek Hosen Sajeeb**  
*Data Analyst & AI Automation Specialist*  
* **LinkedIn:** [Mosaddek Hosen Sajeeb]([https://linkedin.com](https://www.linkedin.com/in/sajeeb-the-analyst/))  
* **GitHub:** [@SajeebTheAnalyst](https://github.com/SajeebTheAnalyst)  
* **Portfolio:** [https://sajeeb-the-analyst.vercel.app/]

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
