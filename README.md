# 🎓 Grounded Q&A Assistant for Higher Education (Salesforce + Heroku + LLM)

## Overview

This project is a proof-of-concept AI assistant that enables Salesforce users (e.g. university staff) to ask natural-language questions about student policies and receive accurate, grounded answers.

The assistant:
- Accepts questions via Salesforce UI
- Sends the input and context to a Flask app hosted on Heroku
- Grounds the prompt using relevant student data and reference docs
- Calls a large language model (e.g. OpenAI GPT-4, Claude)
- Returns the answer and stores it back in the Salesforce record

---

## 🔗 Architecture

**User (Salesforce)**  
→ Lightning Web Component (input form)  
→ **Heroku (Flask API)**  
→ **LLM API (OpenAI or Claude)**  
→ **Response saved back to Salesforce** (e.g. Case or Contact)

---

## 🎯 Example Use Case

**Question:**  
> "What documents does a military veteran need to apply for Spring 2026?"

**Grounded Context:**  
- Student type: Veteran  
- Campus: Online  
- Term: Spring 2026

**LLM Response:**  
> "Veteran applicants must submit a DD-214, proof of residency, and official transcripts."

**Saved To:**  
Case record → `LLM_Response__c` field

---

## 🔐 Trust & Compliance Notes
- All data is routed through a **Heroku-hosted intermediary**, keeping the LLM call isolated
- LLM output is stored in Salesforce for **transparency and auditability**
- BYO LLM possible via Claude, Hugging Face, etc. for public sector or GovCloud use cases

---

## 📌 Status

✅ Flask API scaffolded  
✅ LLM integration functional  
✅ Grounding using mock CSV data  
⬜ Salesforce UI input + record update  
⬜ Reusable demo script + architecture diagram

---

## 👥 Next Steps

- Finalize UI integration in Salesforce (input + display)
- Expand grounding dataset to support additional use cases (e.g. financial aid, disability services)
- Package and enable for AEs to demo across EDU/Gov accounts

---

## 🧠 Why This Matters

This assistant closes the loop between Salesforce, Heroku, and trusted AI output. It enables customer-specific demos even when Copilot and Prompt Builder are unavailable in GovCloud — helping us win technical validation faster.
