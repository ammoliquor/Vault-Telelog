# Project: Workflow WhatsApp/Telegram Bot (Quick Capture)

## 1. Project Overview & Objective
A quick-capture bot to instantly log thoughts, ideas, links, clips, or notes from your mobile device directly into your Obsidian second brain. It must:
* Be 100% free to run 24/7.
* Support custom commands (e.g., `/notion <text>` to log to Notion, `/antigravity <command>` to interact with Antigravity CLI, or general text to log directly to Obsidian).
* Be reliable, fast, and structured.

---

## 2. Project Folder Structure & Mapping
The project folders correspond to specific stages of your knowledge and content pipeline:

* **📁 `Inputs/`**: Logs raw incoming captures.
  * *Content:* Raw notes, web clips, research, ideas, and meeting transcripts.
* **📁 `Process/`**: The workspace for active thought and execution.
  * *Content:* Active drafts, working notes, and agent task logs.
* **📁 `Outputs/`**: Finished, polished artifacts.
  * *Content:* Work ready to publish, ship, or send.
* **📁 `Feedback/`**: Performance evaluation and iteration.
  * *Content:* Metrics, audience responses, reviews, and post-mortems.

---

## 3. Technology Stack & Deployment Plan
To meet the requirements of a **free** and **24/7 active** bot:

### Bot Platform: Telegram Bot API
* **Why:** 100% free with no rate limits for personal use, native support for rich command menus (like `/notion`, `/antigravity`), and easy to interface with Python using `python-telegram-bot` or webhook payloads.

### Deployment Options (24/7 Active, Free)
* **Vercel Serverless Functions (Python) [Webhook Route]**
  * **How it works:** Telegram sends an HTTP POST request to a Vercel Serverless Function (written in Python) every time you send a message. Vercel runs the function, processes the message, and shuts down, ensuring 24/7 responsiveness completely for free.
