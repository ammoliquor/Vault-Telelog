---
date: 2026-07-22
type: project
status: active
tags: [project, telegram-bot]
ai-first: true
---

## For future Gemini
Project documentation for the Quick Capture Telegram bot deployment.

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
* *(WhatsApp via Twilio has strict time limits and trial balance requirements, making Telegram the clear choice for a permanent free setup).*

### 2. Deployment Options (24/7 Active, Free)
We have two main deployment routes for a 24/7 Python Telegram bot:

* **Option A: Serverless Webhook on Vercel (Recommended)**
  * **How it works:** Telegram sends an HTTP POST request to a Vercel Serverless Function (written in Python) every time you send a message. Vercel runs the function, processes the message, and shuts down.
  * **Pros:** 100% free, zero maintenance, scales automatically, 24/7 active with no idle timeouts.
  * **Cons:** Stateless (no persistent in-memory variables, must write to external APIs like Notion or Obsidian sync APIs).
* **Option B: Long-Polling Worker on Koyeb or Render**
  * **How it works:** A standard Python process runs 24/7, constantly checking Telegram for new messages.
  * **Pros:** Simple setup, stateful (can keep session state in memory).
  * **Cons:** Render's free tier spins down if it doesn't receive HTTP traffic (requiring a "ping" service), and Koyeb has resource limit caps.

---

## 4. Antigravity's Role
* **System Architecture:** Designing the webhook receiver/polling listener and the dispatch logic that handles `/notion`, `/antigravity`, or default Obsidian logging.
* **API Integrations:** Writing Python wrappers for the Notion API and integration with Antigravity commands.
* **Deployment Setup:** Providing configuration files (e.g., `vercel.json` or Dockerfiles) to deploy the bot 24/7 seamlessly.
* **Troubleshooting:** Pinpointing environment and path routing issues during local run and deployment.
