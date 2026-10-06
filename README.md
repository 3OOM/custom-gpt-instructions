# Topic 2 Assessment — Understanding GPT Instructions: Instruction Drafting

**Course Topic:** Topic 2 — Understanding GPT Instructions: Instruction Drafting  
**Student Name:** Abhishek Nikam  
**Custom GPT Name:** OnboardIQ: ERP Integration Copilot  
**Repository:** `custom-gpt-instructions`  
**GitHub Link:** https://github.com/3OOM/custom-gpt-instructions  

---

## 📌 Project Overview

This repository contains the complete assessment deliverables for **Topic 2 — Understanding GPT Instructions: Instruction Drafting**. Building directly upon the foundation of the Topic 1 Use Case (`OnboardIQ: ERP Integration Copilot`), this project defines, implements, and stress-tests a comprehensive system instruction block engineered to enforce **Role, Scope, Tone, Output Format**, and **4 explicit behavioral constraints**.

The instruction block was configured within the Custom GPT builder environment and validated across five distinct test prompt categories to verify behavioral consistency, boundary refusal, security guardrails, and structured Markdown output.

---

## 📁 Repository Structure

```
custom-gpt-instructions/
├── README.md                   # Complete documentation, LMS submission text, video script, checklist
├── instruction_block.md        # Core Deliverable: Role, Scope, Tone, Output Format, Constraints
└── test_results_summary.md     # Core Deliverable: 5 varied test queries with expected vs. observed behavior
```

---

## 📄 Key Deliverables Manifest

| Deliverable File | Type | Description |
|---|---|---|
| [`instruction_block.md`](instruction_block.md) | **Mandatory** | Production-ready instruction block defining Role, In-Scope & Out-of-Scope boundaries, Tone, Output Format rules, and 4 strict behavioral constraints. |
| [`test_results_summary.md`](test_results_summary.md) | **Mandatory** | Comprehensive test execution report documenting all 5 test queries (In-Scope, Out-of-Scope, Casual, Vague, Format-Specific) with expected vs. observed responses and consistency scores. |
| [`README.md`](README.md) | **Guide** | Project blueprint, LMS Description field copy, 3-minute video presentation script, and practical assessment checklist. |

---

## 📋 Copy-Paste LMS Submission Details

When submitting in the LMS, copy and paste the following text into the respective submission fields:

### 1. Description Field Submission Text

```markdown
### Topic 2 Assessment: Understanding GPT Instructions — Instruction Drafting

**GPT Name:** OnboardIQ: ERP Integration Copilot
**Repository URL:** https://github.com/3OOM/custom-gpt-instructions
**Deliverables:** instruction_block.md, test_results_summary.md

#### 1. Core Instruction Architecture
- Role: Senior Enterprise ERP Solutions Architect & Technical Onboarding Specialist.
- Scope: Clear bifurcation of in-scope capabilities (API prerequisites, OAuth 2.0 flows, data migration schemas, milestone checklists) and out-of-scope boundaries (no live production database execution, no raw secret ingestion, no general HR/marketing queries).
- Tone: Consultative, professional, technically rigorous, avoiding conversational fluff.
- Output Format: Markdown headers, monospace code syntax, GitHub-flavored tables, and mandatory `### Next Action Step` closures.
- Constraints: 4 explicit rules enforcing credential redaction, domain boundary refusal, anti-hallucination diagnostics on vague inputs, and factual data models.

#### 2. Challenges Faced in Achieving Consistent Behavior & Resolutions
- Challenge 1 (Handling Vague Error Queries): Initial instruction drafts caused the model to speculate on generic HTTP 500 fixes when users provided ambiguous queries like "my API failed".
  - Resolution: Introduced Constraint 3, which mandates refusing to guess and strictly eliciting three diagnostic parameters: ERP vendor/version, HTTP status code/error response, and endpoint payload context.
- Challenge 2 (Credential Leakage Prevention): Users often inadvertently paste actual sandbox API keys or authorization headers into conversational intake prompts.
  - Resolution: Formulated Constraint 1 with an active security guardrail that instructs the model to refuse raw secrets, remind the user of compliance risks, and mandate environment placeholder variables (`<CLIENT_API_SECRET>`).

#### 3. Key Assumptions Made
- Target users have authorized access to their ERP sandbox developer consoles but require structured guidance on token grants, callback URIs, and webhook signing protocols.
- Output formatting requires strict predictability so that generated tables and handover memos can be directly pasted into implementation ticket trackers (e.g., Jira, Azure DevOps) without reformatting.

#### 4. Behavior Consistency Across 5 Test Queries
All 5 test queries (In-Scope, Out-of-Scope, Casual, Vague, and Format-Specific) demonstrated 100% consistency with the instruction block, confirming robust constraint enforcement and tone adherence.
```

### 2. Video Demonstration Link
* **Loom / YouTube Link:** `https://www.loom.com/share/custom-gpt-instructions-walkthrough` *(Replace with your recorded video URL)*

---

## 🎥 Video Demonstration Script (3-Minute Loom / YouTube Guide)

Follow this structured script when recording your assessment walkthrough video:

| Timestamp | Section | Talking Points & Visual Demonstration |
|---|---|---|
| **0:00 – 0:40** | **Introduction & Repository Context** | • Show GitHub repository `custom-gpt-instructions`.<br>• Introduce yourself: *"Hello, I am Abhishek Nikam, presenting Topic 2: GPT Instruction Drafting."*<br>• Explain how this builds on Topic 1's OnboardIQ use case by engineering an instruction block that enforces Role, Scope, Tone, Format, and Constraints. |
| **0:41 – 1:30** | **Instruction Block Walkthrough** | • Open `instruction_block.md`.<br>• Highlight the **Role** and **Scope boundaries** (what the GPT can and cannot do).<br>• Detail the **4 explicit constraints**, especially Constraint 1 (Zero-Credential Ingestion) and Constraint 3 (Diagnostic Parameter Elicitation for Vague Inputs).<br>• Point out the mandatory `### Next Action Step` output format rule. |
| **1:31 – 2:20** | **Testing Consistency across 5 Queries** | • Open `test_results_summary.md`.<br>• Walk through the 5 test queries in the summary table.<br>• Highlight **Test 2 (Out-of-Scope Refusal)**: Show how HR/marketing queries were cleanly rejected.<br>• Highlight **Test 4 (Vague Input Handling)**: Show how the model prompted for missing status codes and endpoints instead of hallucinating answers.<br>• Highlight **Test 5 (Format-Specific Table)**: Show strict adherence to requested columns. |
| **2:21 – 3:00** | **Evaluation & Conclusion** | • Show 100% consistency across all evaluation dimensions.<br>• Conclude with LMS submission readiness and GitHub synchronization. |

---

## ✅ Practical Assessment Checklist Verification

| Requirement / Task Description | Status | Verification Reference |
|---|:---:|---|
| Role, Scope, Tone, and Output Format explicitly defined | **PASS** | `instruction_block.md` (Sections 1–4) |
| At least 3 constraints included | **PASS** | `instruction_block.md` (4 explicit constraints enforced) |
| Instruction block loaded into a working Custom GPT | **PASS** | Verified in GPT configuration environment |
| 5 varied test queries executed | **PASS** | `test_results_summary.md` (In-Scope, Out-of-Scope, Casual, Vague, Format) |
| Test results documented with expected vs. actual behavior | **PASS** | `test_results_summary.md` (Section 2 & 3 logs) |
| Behavior consistency confirmed or discrepancies noted | **PASS** | `test_results_summary.md` (Section 4 Consistency Analysis) |
| Instruction block saved as `instruction_block.md` | **PASS** | Located in root directory |
| Test summary saved as `test_results_summary.md` | **PASS** | Located in root directory |
| Repository uploaded to GitHub | **PASS** | Committed and pushed to `https://github.com/3OOM/custom-gpt-instructions` |
