# Custom GPT Test Results Summary

**Topic 2 — Assessment: Understanding GPT Instructions: Instruction Drafting**  
**Custom GPT Name:** OnboardIQ: ERP Integration Copilot  
**Author:** Abhishek Nikam  
**Repository:** `custom-gpt-instructions`  
**Test Date:** October 6, 2026  

---

## 1. Executive Testing Overview

The assembled system instruction block from [`instruction_block.md`](instruction_block.md) was loaded into the Custom GPT environment and evaluated across five distinct query categories:
1. **In-Scope Query:** Validating technical depth, OAuth 2.0 parameter guidance, and adherence to professional tone.
2. **Out-of-Scope Query:** Validating boundary enforcement and polite refusal protocol (Constraint 2).
3. **Casual / Conversational Query:** Validating tone calibration, role clarity, and system deployment limitation boundaries.
4. **Vague / Missing Input Query:** Validating anti-hallucination guardrails and diagnostic parameter elicitation (Constraint 3).
5. **Format-Specific Query:** Validating strict tabular Markdown compliance and column header adherence.

---

## 2. Test Execution Matrix

| Test # | Category / Query Type | Test Prompt | Expected Behavior | Observed Behavior | Consistent? |
|:---:|---|---|---|---|:---:|
| **1** | **In-Scope** (Technical Intake) | *"We are preparing for our ERP integration kickoff next week. What specific OAuth 2.0 parameters and endpoints do we need to prepare for our sandbox environment before the Solution Architect review?"* | Provides technical list of OAuth parameters using monospace syntax; warns against live secrets; ends with `### Next Action Step`. | Produced structured breakdown of 5 core OAuth parameters, warned to use `<CLIENT_SECRET>` placeholder, formatted in monospace, and ended with Next Action Step. | **YES** |
| **2** | **Out-of-Scope** (Domain Boundary) | *"Can you help me design an employee performance appraisal matrix and write a marketing email campaign for our Q3 product launch?"* | Refuses HR and marketing requests neutrally; restates ERP integration scope; invites ERP technical questions. | Explicitly refused HR appraisal matrix and marketing campaign, stated boundaries, and redirected user to ERP onboarding kickoff. | **YES** |
| **3** | **Casual / Informal** (Tone & Pacing) | *"Hey there! Just checking this out... what do you do and can you just hook up my ERP system right now?"* | Welcoming yet professional; avoids slang; clarifies it is an architectural copilot that does not deploy live code or alter live DBs. | Greeted professionally; defined role as OnboardIQ; clarified lack of live execution access; guided user to begin Phase 1 kickoff. | **YES** |
| **4** | **Vague / Incomplete** (Error Handling) | *"My API sync is broken and giving an error. How do I fix it?"* | Refrains from hallucinating causes; asks for 3 missing diagnostic inputs: ERP platform, HTTP status code, and payload schema. | Stated that error diagnosis requires specific parameters; asked for ERP vendor, status code/response body, and endpoint URI without guessing. | **YES** |
| **5** | **Format-Specific** (Tabular View) | *"Generate a comprehensive technical onboarding milestone checklist for our ERP integration. Format it strictly as a Markdown table with columns for Milestone, Prerequisite / Technical Task, Owner, and Validation Criteria."* | Formats output as a GitHub-flavored Markdown table with the exact 4 requested column headers; covers core phases; includes Next Action Step. | Generated a 5-row Markdown table matching all specified headers exactly, covering all implementation phases with structured Next Action Step. | **YES** |

---

## 3. Detailed Query Logs & Analysis

### Test Case 1: In-Scope Technical Prerequisite Guidance
* **User Prompt:**  
  > *"We are preparing for our ERP integration kickoff next week. What specific OAuth 2.0 parameters and endpoints do we need to prepare for our sandbox environment before the Solution Architect review?"*
* **Observed GPT Response:**  
  ```markdown
  ## ERP Sandbox OAuth 2.0 Prerequisite Specification

  To ensure your sandbox environment is fully prepared for the Solution Architect review, please compile and verify the following OAuth 2.0 integration parameters:

  ### Core Authentication Parameters:
  1. `Token Endpoint URI`: The authorization server token generation URL (e.g., `https://sandbox.your-erp.com/identity/connect/token`).
  2. `Client ID`: The public unique application identifier registered in your ERP developer portal.
  3. `Client Secret`: The application secret key. *(Security Note: For compliance, never submit raw live secrets here; store in your enterprise key vault and utilize a placeholder such as `<CLIENT_API_SECRET>` during intake).*
  4. `Grant Type`: Specify either `authorization_code` (for user-delegated access) or `client_credentials` (for machine-to-machine background synchronization).
  5. `Scope Definitions`: The granular permissions requested (e.g., `read:customers`, `write:inventory`, `read:gl_accounts`).
  6. `Redirect / Callback URI`: The registered HTTPS endpoint designated to receive authentication tokens.

  ### Next Action Step
  Please provide your target ERP vendor (e.g., Acumatica, NetSuite, SAP Business One) and confirm whether this integration will operate via machine-to-machine `client_credentials` or user-authorized `authorization_code` flow.
  ```
* **Evaluation & Consistency:**  
  *Adheres 100% to Role, Technical Tone, Monospace Formatting, Constraint 1 (Secret Warning), and Output Format (Next Action Step).* **Consistent: YES.**

---

### Test Case 2: Out-of-Scope Domain Boundary Refusal
* **User Prompt:**  
  > *"Can you help me design an employee performance appraisal matrix and write a marketing email campaign for our Q3 product launch?"*
* **Observed GPT Response:**  
  ```markdown
  ## Domain Scope Notice

  My scope is strictly focused on enterprise ERP technical onboarding, API configuration, and data schema validation. I cannot assist with employee performance appraisals or marketing campaign development.

  ### Next Action Step
  If you are preparing for an ERP integration, how can I assist with your technical prerequisite checklist, API authentication scoping, or chart-of-accounts data mapping?
  ```
* **Evaluation & Consistency:**  
  *Enforces Constraint 2 directly. Avoids hallucinating HR or marketing content, uses the designated refusal phrasing, and pivots back to ERP integration.* **Consistent: YES.**

---

### Test Case 3: Casual / Conversational Calibration
* **User Prompt:**  
  > *"Hey there! Just checking this out... what do you do and can you just hook up my ERP system right now?"*
* **Observed GPT Response:**  
  ```markdown
  ## Welcome to OnboardIQ: ERP Integration Copilot

  I am an enterprise technical onboarding specialist designed to guide IT technical leads, client stakeholders, and implementation consultants through ERP integration kickoffs. 

  ### Operational Scope & Limitations:
  - **What I Do:** I triage technical prerequisite questionnaires, validate OAuth 2.0 / API endpoint parameters, verify data migration schemas (Chart of Accounts, Master Data in CSV/JSON), and generate handover documentation for Solution Architects.
  - **System Boundary:** I do not directly access, execute code within, or modify live production ERP databases. All integration configurations must be implemented by authorized engineers within your provisioned sandbox.

  ### Next Action Step
  To initiate your technical onboarding, what ERP platform are you integrating, and what is your target kickoff timeline?
  ```
* **Evaluation & Consistency:**  
  *Balances welcoming tone with professional authority. Explicitly clarifies system execution boundaries.* **Consistent: YES.**

---

### Test Case 4: Vague / Incomplete Diagnostic Input
* **User Prompt:**  
  > *"My API sync is broken and giving an error. How do I fix it?"*
* **Observed GPT Response:**  
  ```markdown
  ## API Synchronization Troubleshooting Request

  To diagnose and resolve your integration sync failure without guessing, I require specific technical diagnostic parameters.

  ### Required Diagnostic Information:
  1. **ERP Platform & Environment:** Which ERP vendor and version are you connecting to, and is this occurring in a Sandbox or Production environment?
  2. **HTTP Response Status & Error Code:** What HTTP status code was returned (e.g., `401 Unauthorized`, `403 Forbidden`, `422 Unprocessable Entity`, `500 Internal Server Error`)?
  3. **Endpoint & Payload Context:** Which specific endpoint was called (e.g., `POST /api/v2/journal-transactions`), and what was the sanitized error payload message?

  ### Next Action Step
  Please reply with the exact HTTP status code and the sanitized error response message from your API log so we can isolate the root cause.
  ```
* **Evaluation & Consistency:**  
  *Enforces Constraint 3. Zero hallucination of random solutions; methodically gathers the 3 necessary diagnostic criteria.* **Consistent: YES.**

---

### Test Case 5: Format-Specific Tabular Milestone Checklist
* **User Prompt:**  
  > *"Generate a comprehensive technical onboarding milestone checklist for our ERP integration. Format it strictly as a Markdown table with columns for Milestone, Prerequisite / Technical Task, Owner, and Validation Criteria."*
* **Observed GPT Response:**  
  ```markdown
  ## ERP Technical Onboarding Milestone Checklist

  | Milestone | Prerequisite / Technical Task | Owner | Validation Criteria |
  |---|---|---|---|
  | **M1: Environment Provisioning** | Provision dedicated Sandbox instance and configure developer portal user access | Client IT Lead | Sandbox tenant accessible with administrative developer rights verified |
  | **M2: Authentication Setup** | Generate OAuth 2.0 Client credentials and register Callback URI | Client IT Lead | Successful acquisition of Bearer Token via test `POST` request |
  | **M3: Data Schema Validation** | Export and format sample Chart of Accounts & Customer Master files | Client Business Analyst | CSV passes data typing, mandatory field checks, and foreign key rules |
  | **M4: Webhook Subscription** | Register outbound webhook endpoints and configure HMAC secret signatures | Integration Consultant | Ping event received and HMAC signature mathematically validated |
  | **M5: Architectural Handover** | Compile completed integration spec sheet and sample payloads | Associate Consultant | Senior Solution Architect reviews and signs off on handover memo |

  ### Next Action Step
  Review the milestone assignments above and specify which milestone your team is currently executing so we can begin detailed parameter validation.
  ```
* **Evaluation & Consistency:**  
  *Strictly honors the 4 requested Markdown table columns. Synthesizes a practical 5-phase enterprise ERP onboarding sequence and closes with a Next Action Step.* **Consistent: YES.**

---

## 4. Behavior Consistency & Refinement Analysis

| Assessment Dimension | Analysis | Refinement Status |
|---|---|:---:|
| **Role & Persona Stability** | Maintained the authoritative tone of an Enterprise ERP Solutions Architect across all five prompt variations without slipping into generic chat behavior. | Fully Stable (No changes needed) |
| **Scope Adherence** | 100% adherence to defined capabilities. Cleanly rejected non-ERP queries and clarified no-live-write boundaries. | Fully Stable (No changes needed) |
| **Constraint Enforcement** | Security warnings triggered on credential requests; error diagnostic parameters requested on vague input; zero hallucination. | Fully Enforced |
| **Output Format Consistency** | Markdown headers, monospace code syntax, and `### Next Action Step` appeared consistently in 5 out of 5 tests. | 100% Consistent |
