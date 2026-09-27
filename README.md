# Telegram AI Agent (n8n)

An AI-powered Telegram assistant built with n8n. The agent answers customer
questions using a knowledge base (RAG), remembers conversation context per
user, and can take actions on its own — sending emails, logging leads to a
spreadsheet, and booking calendar meetings.

## How it works
1. **Telegram Trigger** receives an incoming message.
2. **Supabase Vector Store** retrieves relevant context from a knowledge base
   using embeddings (RAG).
3. An **AI Agent** (GPT-4.1) generates a grounded answer, using only the
   retrieved context — it's instructed never to answer from its own
   knowledge to avoid hallucinating prices, schedules, or policies.
4. **Conversation memory** is kept per Telegram user, so the agent
   remembers earlier messages in the same chat.
5. The agent can call three tools on its own when needed:
   - **Gmail** – send an email
   - **Google Sheets** – log a lead (name, email, requested service)
   - **Google Calendar** – book a meeting

## Stack
n8n · Telegram Bot API · OpenAI (GPT-4.1) · Supabase (vector store) ·
Google Sheets · Google Calendar · Gmail

## Setup notes
This export has credentials removed (n8n never exports secrets). To run it,
you'll need your own Telegram Bot token, OpenAI API key, Supabase project
with a vector table, and OAuth connections for Gmail, Sheets and Calendar.
