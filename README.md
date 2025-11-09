# AI Automation Assignment: Multi-Agent Content Pipeline in n8n

## Overview
This repository presents a complete implementation and documentation for the **AI Automation Assignment: Multi-Agent Content Pipeline in n8n**.  
It automates the process of discovering trending topics in the AI Automation niche, generating content prompts, creating blog posts and videos, and submitting them for human review.

---

## Objectives
1. Automate topic discovery using Google Trends and YouTube Data API.  
2. Generate creative prompts automatically using OpenAI or Gemini.  
3. Produce blog and video content through automated API workflows.  
4. Submit the generated results to Google Sheets for manual review.  
5. Add error handling and notification systems.

---

## Workflow Architecture

### 1️⃣ ContentResearch Agent
**Goal:** Discover trending topics in AI Automation.  
**Nodes Used:**  
- HTTP Request (Google Trends)  
- HTTP Request (YouTube API)  
- Function node (deduplicate topics)  

**Output:** List of trending topics passed to Prompt Agent.

### 2️⃣ Prompt Agent
**Goal:** Generate prompts for blogs and videos.  
**Tools:** OpenAI / Gemini node  
**Output:** Structured list of prompts containing `title`, `type`, and `description`.

### 3️⃣ Content Creator Agent
**Goal:** Generate blog posts and videos.  
**Tools:** OpenAI (blog), Google VEO 3 API (video)  
**Output:** Blog content + video link.

### 4️⃣ Content Submission & Review Agent
**Goal:** Submit generated content to Google Sheets.  
**Tools:** Google Sheets node, Slack/Email Notification  
**Output:** New row appended to Google Sheet.

---

## Node Summary

| Agent | Node | Function |
|-------|------|-----------|
| ContentResearch | HTTP Request | Google Trends API |
| ContentResearch | HTTP Request | YouTube Data API |
| Prompt Agent | OpenAI | Prompt Generation |
| Content Creator | OpenAI | Blog Generation |
| Content Creator | HTTP Request | Google VEO 3 Video Generation |
| Submission | Google Sheets | Append results |
| Submission | HTTP Request | Slack Notification |

---

## Example Output
```json
{
  "topic": "automate ai workflows",
  "prompt": "3 Ways to Automate Model Retraining",
  "blog_excerpt": "In this article we describe three practical ways to automate model retraining...",
  "video_link": "https://storage.googleapis.com/veo-output/abcd.mp4",
  "status": "Pending Review"
}
```

---

## Error Handling
- **Catch Node:** Captures workflow errors.  
- **Retry Logic:** Retries each API call 3 times.  
- **Error Sheet:** Logs failures in a separate tab.  
- **Slack Notification:** Alerts reviewer of new content or errors.

---

## Repository Contents
| File | Description |
|------|--------------|
| `Assignment_Documentation.md` | Full markdown documentation |
| `workflow-ai-automation.json` | n8n workflow export |
| `sample-outputs.json` | Example Google Sheet entry |
| `screenshots/` | Node configuration images |

---

## Setup Instructions
1. Open **n8n** → *Workflows → Import from File* → select `workflow-ai-automation.json`.  
2. Create credentials for Google, YouTube, OpenAI, and Slack.  
3. Replace placeholders (`YOUR_YOUTUBE_API_KEY`, `GOOGLE_SHEET_ID`, etc.).  
4. Test run the workflow to generate and log new content automatically.

---

## Author Details
**Name:** Anomitro Sarker
**Date:** November 8, 2025  
