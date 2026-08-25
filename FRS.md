# Functional Requirements Specification (FRS)
- Project: Confidential Contract Explainer (Internal AI Assistant)
- Document Version: 1.0
- Prepared For: Internal Use
- Prepared By: Lilly Nguyen, Project Owner / BA
- Last Updated: 24 Aug 2026

## 1. Purpose
This document translates the business requirements as well as commercial language defined in the Business Requirement Document (BRD) into specific functional and non-funcitonal requirements that describe how the system must behave from a user and system-interaction perspective. 

*Note that this does not describe the underlying architecture or technology choices, focusing only on observable system behaviour.*

## 2. Functional Requirements
### 2.1 Document Upload & Ingestion
| ID | Requirement |
| ---------------- | ---------------- |
| FR-01 | The system shall allow users to upload documents through the chat interface |
| FR-02 | The system shall extract text content from the uploaded documents, preserving page/section/clause numbering where identifiable |
| FR-03 | The system shall organize extracted text into logical segments aligned to clause or section boundaries rather than arbitrary length cuts |
| FR-04 | The system shall associate each uploaded document with the user who uploaded it |
| FR-05 | The system shall reject unsupported files with clear, user-facing error message |
| FR-06 | The system shall confirm to user once the document has been successfully uploaded and processed and ready for questions |
### 2.2 Chat Interface
| ID | Requirement |
| ---------------- | ---------------- |
| FR-07 | The system shall provide a conversational chat interface allowing a dialogue regarding uploaded documents |
| FR-30 | The system shall display the latest chat history upon user log in |
| FR-08 | The system shall retain and display the chat history for the duration of a session, allowing user to ask follow-up questions with context |
| FR-18 | The system  shall display a brand new chat session when switching to a new document |
| FR-10 | The system  shall display the AI assistant's response progressively rather than only after full completion, to improve the dynamic responsiveness |
| FR-16 | The system shall display a persistent disclaimer indicating the tool provides informational assistance only, not legal advice |
### 2.3 Question & Answer / Retrieval
| ID | Requirement |
| ---------------- | ---------------- |
| FR-11 | The system shall allow users to ask natual-language questions and receive answers about uploaded documents via a chat box interface |
| FR-12 | The system shall identify the most relevant sections of the selected documents needed to answer user's questions |
| FR-13 | The system shall generate the answer only based on the content of the selected documents |
| FR-14 | The system shall clearly state when a questions cannot be answered from the uploaded documents |
| FR-15 | The system shall display, alongside each answer, the specific section or clause references used to generate the answer |
### 2.4 Document Viewing and Citation Navigation
| ID | Requirement |
| ---------------- | ---------------- |
| FR-17 | The system shall display the full content of the currently selected document in a panel alongside the chat interface when clicking on a document |
| FR-19 | The system shall allow users to go back and select another uploaded document |
| FR-09 | The system  shall allow the users to switch between multiple uploaded documents within the interface |
| FR-20 | The system shall render each citation in each AI-generated answer as a clickable/selectable element rather than plain text |
| FR-21 | When a user selects a citation, the system shall automatically scroll the document panel to the exact section or clause referenced |
| FR-22 | When a user selects a citation, the system shall visually highlight the referenced section or clause within the document panel |
| FR-23 | The system shall maintain the highlighted state until user selects a different citation or dismiss it |
| FR-24 | If a citation references a section that cannot be precisely located in the rendered documents or do not exist, the system shall inform user rather than silently failing or highlighting the wrong content |
### 2.5 User & Access Management
| ID | Requirement |
| ---------------- | ---------------- |
| FR-25 | The system shall require users to log in before uploading or querying any documents |
| FR-26 | The system shall ensure a user can only query documents they themselves uploaded, unless explicitly shared |

### 2.6 Data Retention & Expiry
| ID | Requirement |
| ---------------- | ---------------- |
| FR-28 | The system shall record basic usage activity (timestamp, user, document name) for adoption tracking, without logging full question/answer content unless explicitly enabled |
| FR-29 | The system shall allow a user or administrator to manually delete a document and its associated data at any time, independent of the automatic expiry schedule |
| FR-30 | The system shall automatically delete a document, its parsed content, its embeddings, and its associated chat history after 14 days of inactivity |
| FR-31 | The system shall reset the 14-day inactivity countdown each time a user queries or views the associated document |
| FR-32 | The system shall notify the user (e.g., on login or within the interface) when a document is within 48 hours of automatic deletion |
| FR-33 | The system shall permanently and irreversibly remove all data associated with a document upon deletion, whether triggered automatically or manually. |

## 3. Non-Functional Requirements
| ID | Category | Requirement |
| ---------------- | ---------------- | ---------------- |
| NFR-01 | Security/Privacy | No document content shall be transmitted outside the internal network at any point |
| NFR-02 | Data Retention | Uploaded documents and associated data must be deletable by the uploading user or an administrator on request |
| NFR-03 | Availability | The system should be available during standard business hours with no formal SLA required for the pilot phase |
| NFR-04 | Scalability | The system must support at least 10 concurrent users without significant performance degradation |
| NFR-05 | Cost | Ongoing operating cost of the system must remain at under 5GBP / month in software licensing |
| NFR-06 | Usability | The chat interface must be usable by non-technical employees without training documentation |
| NFR-07 | Performance | A typical query against a document under 50 pages should return an answer within 15-20 seconds under normal operating conditions |
| NFR-08 | Performance | Navigating from a citation click to its highlighted location in the document panel should occur within 1–2 seconds to preserve a responsive, native feel |

## 4. Traceability to Business Requirements
| BRD Reference | Related FRS Requirements |
| ---------------- | ---------------- |
| BR-01 (No external data transmission) | NFR-01 |
| BR-02 (Citation-backed answers)| FR-15 |
| BR-03 (Disclaimer) | FR-16 |
| BR-04 (Multi-user, no cross-contamination) | FR-04, NFR-04, FR-26 |
| BR-05 (No AI hallucinations) | FR-14, FR-24 |
| BR-06 (Standard infrastructure, zero/little cost) | FR-04, NFR-04, FR-26 |
| BR-07 (Document view + citation navigation)| FR-17, FR-20, FR-21, FR-22, FR-23  |
| BR-08 (2-week hybrid retention policy) | NFR-02, FR-30, FR-31, FR-32, FR-33 |