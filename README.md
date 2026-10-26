# Telegram AI CRM Automation

Automatically receives customers from Telegram, provides initial AI-powered consultation, saves the
information to a Notion CRM, and hands off to Sales only when the customer genuinely needs direct support.

## Highlights
- Prevents duplicate leads using the Chat ID
- Batches a customer's consecutive messages so the bot doesn't reply to every short line
- Doesn't hand off to Sales when a customer has only stated a general need; hands off only with a valid phone number and a clear need
- Automatically writes customer notes for Sales and pauses the bot after handoff
- Detects spam and repeated messages, and handles cases where Sales can't reach the customer

## Workflow
1. Receive a message from Telegram
2. Check for an existing customer in the Notion CRM
3. Prevent creating a duplicate lead
4. Batch messages and take the final one
5. Check whether the lead has already been handed off to Sales
6. Check for spam and repeated messages
7. AI consults the customer and normalizes the data into JSON
8. Update the CRM and reply to the customer
9. Hand off the lead to Sales via a Telegram group

## Tech Stack
n8n, Telegram Bot, Notion API, Google Gemini (AI Agent + Basic LLM Chain), JavaScript

## Setup
1. In n8n, choose Import from file and load `workflows/automation-telegram.example.json`.
2. Create credentials: Telegram, Notion, Google Gemini.
3. Replace the `YOUR_...` placeholders with your own values (Notion database ID, Sales group Chat ID).
4. Create a Notion database with the columns the workflow uses (Chat ID, Tin nhắn chờ [pending messages], Bot tạm dừng? [bot paused?], Giai đoạn Sale [sales stage], ...).
