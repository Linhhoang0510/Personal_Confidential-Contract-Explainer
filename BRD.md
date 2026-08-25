# Business Requirements Document (BRD)
- Project: Confidential Contract Explainer (Internal AI Assistant)
- Document Version: 1.0
- Prepared For: Internal Use
- Prepared By: Lilly Nguyen, Project Owner / BA
- Last Updated: 25 Aug 2026

## 1. Executive Summary
This document defines the business rationale, objectives, and scope for an internally hosted AI assistant that allows employees to upload contracts, agreements, and other legal or business documents and ask natural-language questions about their contents.

The tool is intended to:
1. Reduce the time employees spend manually searching dense legal documents for specific clauses
2. Eliminating the confidentiality risk created when employees use public AI tools for the same purpose.

## 2. Business Context and Problem Statement
Employees across procurement, legal-adjacent, and operational teams regularly need to reference specific terms buried inside long contracts, such as liability caps, termination conditions, renewal triggers, or indemnification language. Locating this information manually is time-consuming, and using public AI tools such as ChatGPT or Gemini to accelerate this work introduces a real risk of confidential contract terms being transmitted to external, third-party servers, which may violate company data-handling policy or vendor confidentiality agreements. There is currently no internally sanctioned tool that lets employees get fast, accurate answers about their own documents without this exposure.

This project addresses that gap by providing a private, internally controlled equivalent that never sends document data outside your (company-controlled) systems. 

## 3. Business Objectives
| ID | Objective | Description |
| ---------------- | ---------------- | ---------------- |
| BO-01 | Reduce manual document review time | Enable employees to get answers to contract-specific questions rather than manually reading through the lengthy documents |
| BO-02 | Eliminate confidentiality risk from public AI usage | Provide an internal alternative to prevent employees from pasting confidential contracts into public AI tools | 
| BO-03 | Increase answer tracability and trust | Ensure every AI-generated answer is grounded in and cites the specific clause or section it was derived from, and allow users to instantly verify any citation by viewing the original document content it came from, rather than relying on unverifiable general knowledge or a citation label alone. |
| BO-04 | Operating at little licensing cost | Build the entire systems using free, open-source tools to allow free use | 
| BO-05 | Validate feasibility for broader adoption | Introduce pilot to validate business impact and value using data that could justify larger-scale rollout | 

## 4. Stakeholders
| ID | Requirement | Rationale |
| ---------------- | ---------------- | ---------------- |
| Project Owner  | Lilly | Builds and maintains the tool; owns the pilot rollout |
| End Users  | Internal employees | Primary users asking questions about their own documents |
| IT / Security (informal reviewer) | Whoever oversees internal infrastructure and data policy | Needs assurance that no confidential data leaves internal systems |


## 5. Scope
### 5.1 In Scope
The initial release will cover: 
1. Document upload and processing feature for common file types (PDF)
2. Parse the documents and show a side-by-side view showing the original document content alongside the chat conversation
3. The ability to jump directly from a cited answer to the exact highlighted location in the document it references
4. Conversational question-and-answer functionality about uploaded documents
5. The answers must references specific section or clause they were derived from
6. Basic user access control so users can only view their own document
7. A pilot-level deployment to a limited group of people for feedback and evaluation

### 5.2 Out-of-Scope

## 6. Business Requirements
| ID | Requirement | Rationale |
| ---------------- | ---------------- | ---------------- |
| BR-01 | The system must not transmit any uploaded document content to any external / third-party server or services | This is the core confidentiality objective and the entire business value vs using public AI tools |
| BR-02 | The system must provide answers referencing the specific clause or section used to generate them | Build user trust and instant user verification, critical at work |
| BR-03 | The system must clearly claim that it is only used for asking and extracting content from the  confidential uploaded documents, without providing legal or professional advices | Protect users from over-relying on AI for binding decisions |
| BR-04 | The system must support multiple concurrent users uploading and querying separate documents without cross-contamination of data between users' documents | Required for realistic multi-user pilot usage |
| BR-05 | The system must not produce false knowledge when the information is not present in the uploaded documents | Prevent users from using false information to make critical decisions |
| BR-06 | The system must be built and operated using only free or open-source components | Zero-cost objective; avoids procurement/budget approval delays. |
| BR-07 | The system must allow users to view the original document content alongside the chat interface, and navigate directly to the highlighted source location referenced by any citation in an AI-generated answer | Converts citations from a passive trust signal into an actively verifiable one, directly reinforcing BO-03 and reducing the risk of users acting on an unverified or misattributed answer |
| BR-08 | The system must automatically retain uploaded documents and associated chat history for a maximum of 2 weeks of inactivity, after which they are automatically and permanently deleted, unless the user or an administrator extends or removes the document earlier | Balances usability (allowing multi-day, multi-session conversations about a document) against data minimization principles for confidential content, and provides a clear, defensible answer to IT/Legal questions about how long sensitive documents are stored |

## 7. Assumptions and Constraints
### 7.1 Assumptions
- Pilot users will treat AI-generated answers as a starting point for review rather than a final determination, supported by the disclaimer requirement above
- It is assumed that a 2-week retention window is sufficient for typical use cases (reviewing a single contract over the course of a negotiation or approval cycle), and that users needing longer access will manually extend retention rather than relying on indefinite default storage.

### 7.2 Constraints
A constraint worth flagging is that the answer quality may not match that of large commercial AI service, a tradeoff accepted in exchange for confidentiality and zero cost.

## 8. Success Metrics
