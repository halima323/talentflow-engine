# TalentFlow Engine: Recruitment Automation Demo

An n8n workflow that triages inbound job candidates. It is a demonstration project that uses **synthetic data only** (17 fictional candidates). No real people are involved.

## What it does
- **Cleans the data:** normalises names, emails, phone numbers (E.164) and job titles.
- **Removes duplicates:** matches on email, phone, or name plus location, and checks against a simulated CRM (existing records, do-not-contact, recently contacted).
- **Screens fairly:** protected-characteristic terms and contact details are redacted before scoring and before any AI call.
- **Scores transparently:** a 0 to 100 match score against four open roles, with a must-have gate.
- **Uses AI with guardrails:** the rule-based baseline always runs first. The AI can only make a recommendation more cautious, cannot invent skills, and its output is filtered. If the AI fails, the workflow falls back to the baseline and flags the record for review.
- **Keeps a human in charge:** drafts are recommendations only. A recruiter decides everything and no message is sent automatically.
- **Outputs:** an HTML recruitment operations dashboard plus draft payloads for Salesforce (Contact and match record), Airtable and Clay. Pushing to these tools is **off by default**.

## Files
- `talentflow-engine-recruitment-automation.json`: the n8n workflow (26 working nodes plus 5 note nodes).

## How to run it
1. In n8n, choose **Import from file** and select the JSON file.
2. Click **Execute workflow** on the manual trigger, or open the dashboard webhook URL.
3. All settings (jobs, skills list, scoring weights, recruiters, AI prompt, endpoints) are in the node named **2. Load CONFIG**.

## Tools
n8n, JavaScript (Code nodes), Salesforce, Airtable and Clay (draft integrations), an OpenAI-compatible LLM API (optional).

Built by Halima Khatoon.
