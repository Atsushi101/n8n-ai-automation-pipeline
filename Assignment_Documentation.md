# Assignment Documentation: Multi-Agent Content Pipeline in n8n

## Summary
This markdown provides detailed node configuration, integrations, and workflow logic used for the AI Automation multi-agent pipeline built in n8n.

### Agents Overview
1. **ContentResearch Agent** – Google Trends & YouTube scraping.
2. **Prompt Agent** – Prompt generation using OpenAI/Gemini.
3. **Content Creator Agent** – Blog & Video generation.
4. **Content Submission Agent** – Google Sheets submission & notifications.

### Tools Used
- Google Trends API / HTTP Request
- YouTube Data API
- OpenAI / Gemini
- Google Sheets API
- Slack / Email Notifications
- Error handling nodes and Function nodes

Each agent passes structured JSON data to the next, ensuring a smooth end-to-end automation pipeline.
