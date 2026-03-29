# The Intelligent Business Suite: AI Data Analyst Agent 🚀

## Project Overview
This repository contains the architecture and workflow files for a local, autonomous AI Data Assistant. Designed to replace manual spreadsheet workflows (like VLOOKUPs and manual pivot tables), this ReAct (Reason-and-Act) agent translates natural language queries into instant quantitative insights. 

**Core Objective:** Automate data retrieval and aggregation from live business databases using a locally hosted orchestration engine.

## 🛠 Tech Stack
* **Workflow Engine:** n8n (Local Docker Deployment)
* **LLM / Brain:** Google Gemini 1.5 Flash (via API)
* **Database Target:** Google Sheets API
* **Authentication:** Google Cloud Console (OAuth 2.0)

## 🏗 System Architecture & Key Features
1. **Secure API Pipeline:** Engineered a strict OAuth 2.0 connection through the Google Cloud Console, navigating custom consent screens and managing developer token generation. 
2. **ReAct Agent Logic:** Configured a "Tools Agent" that receives a plain-English prompt, determines which tool to use, fetches raw JSON rows from the spreadsheet, and calculates the final answer in its 'head' before responding.
3. **Prompt Engineering & Tool Constraints:** Implemented strict system guardrails. To prevent LLM "parameter hallucination" and guarantee 100% data retrieval accuracy, the AI is explicitly forbidden from generating dynamic target variables, relying strictly on hardcoded Document IDs.

## 🔍 How to Explore This Project
* **`workflow.json`**: The raw n8n export. You can import this directly into your own local n8n instance to view the node configurations. 
* **`architecture_diagram.png`**: A high-resolution visual map of the data pipeline. 

## 💡 Key Learnings & Troubleshooting
Building this required rigorous systematic debugging, specifically around API authentication. Major hurdles overcome included resolving Google Cloud `403 Access Denied` errors by managing testing environments, and bypassing `PartialExecutionToolExecutor` failures by restricting the AI's ability to manipulate active tool parameters.
