# ArcVault Intake Triage Pipeline

An AI-powered intake and triage workflow built with **n8n** and **Claude (Sonnet 4)** for the Valsoft AI Engineer assessment.

## What It Does

Processes unstructured customer requests (bug reports, feature requests, billing issues, etc.) and automatically classifies, enriches, routes, and escalates them — producing structured JSON records ready for downstream teams.
### Development Conversation (Claude)

The prompt engineering and workflow design process can be viewed here:

[https://claude.ai/share/your-link-here](https://claude.ai/share/ad6f629f-640f-43a6-9bbb-cc33f95ccc69)

This conversation shows the iterative reasoning behind the workflow architecture, prompt structure, and routing logic.

## Workflow Overview

| Node | Purpose |
|------|---------|
| Manual Trigger | Starts the workflow |
| Sample Inputs | Emits 5 synthetic test messages |
| Claude Classification | Sends each message to Claude API for classification and enrichment |
| Parse Response | Maps Claude's output to a structured JSON schema |
| Routing Logic | Assigns each request to a destination queue (Engineering, Billing, Product, IT/Security) |
| Escalation Check | Flags records for human review based on confidence score, outage keywords, or billing discrepancies |
| Write Output | Combines all records into a final JSON output |

## Files

- **arcvault_workflow.json** — Exported n8n workflow (import into any n8n instance)
- **arcvault_triage_output.json** — Final structured output for all 5 sample inputs
- **arcvault_triage_report.docx** — Architecture write-up, prompt documentation, and screenshots

## Tools Used

- **n8n Cloud** — Workflow orchestration
- **Claude Sonnet 4 (Anthropic API)** — Classification, enrichment, and summarization
- **JSON** — Structured output format

## How to Run

1. Import `arcvault_workflow.json` into an n8n instance
2. Add your Anthropic API key as a Header Auth credential (name: `x-api-key`)
3. Click "Execute Workflow"
