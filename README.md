Conversational Sales Agent App
A complete consent-first conversational sales agent built in Python with a Google ADK-compatible `SalesAgent` class, FastAPI web UI, CSV lead storage, multi-session handling, simulation testing, and manual terminal testing.
Features
External trigger simulation: the agent starts when a new lead sends the first message.
Consent-first flow: no lead data is collected until the lead agrees.
Step-by-step qualification:
Age
Country
Interested product or service
Multi-lead sessions using independent `lead_id` values.
Auto follow-up after 10 seconds of inactivity.
CSV lead saving in `leads.csv`.
Browser-based chat app.
Manual terminal test.
Concurrent lead simulation.
Project Structure
```text
sales-agent-app/
├── app.py
├── agent.py
├── utils.py
├── simulate_leads.py
├── interactive_test.py
├── leads.csv
├── requirements.txt
├── README.md
└── static/
    └── index.html
```
Setup
1. Create virtual environment
Windows:
```bash
python -m venv adk-env
adk-env\Scripts\activate
```
macOS/Linux:
```bash
python3 -m venv adk-env
source adk-env/bin/activate
```
2. Install dependencies
```bash
pip install -r requirements.txt
```
Run the Web App
```bash
uvicorn app:app --reload
```
Open:
```text
http://127.0.0.1:8000
```
Manual Test
```bash
python interactive_test.py
```
Example conversation:
```text
You: Hi
Agent: Hey! Thank you for your interest...
You: yes
Agent: What is your age?
You: 25
Agent: Which country are you from?
You: India
Agent: What product or service are you interested in?
You: Premium Travel Package
Agent: Thank you! Your information has been recorded...
```
Automatic Multi-Lead Simulation
```bash
python simulate_leads.py
```
This simulates multiple leads concurrently and writes output to `leads.csv`.
Lead CSV Format
```csv
lead_id,age,country,interest,status
lead_india_001,25,India,Premium Travel Package,secured
```
Notes on Google ADK
The `SalesAgent` class attempts to import:
```python
from google.adk.agents import Agent as ADKAgent
```
If `google-adk` is installed, the class inherits from the ADK `Agent`. If the package is not installed, the project still runs locally through a safe fallback class, which makes testing easier.
Production Upgrade Ideas
Connect to WhatsApp Business API, website forms, or CRM webhook.
Replace CSV with PostgreSQL or Firebase.
Add OTP-based phone verification.
Add dashboard authentication.
Add email/SMS follow-up instead of browser-only follow-up.
Add lead scoring and product recommendations.
Deploy to Google Cloud Run.
