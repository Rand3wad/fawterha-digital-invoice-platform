# Fawterha — Digital Invoice Management Platform

> **Portfolio case study** — this repository documents the project at a safe, high level. It is not a copy of the original team repository and does not contain production credentials, private data, or proprietary source code.

## Overview

**Fawterha** is an Android application designed to reduce reliance on paper receipts by turning invoices and receipts into a centralized, searchable digital archive.

The platform supports both uploaded receipts and automated invoice ingestion through POS integration. It combines backend services, structured invoice data, AI-assisted extraction, categorization, reporting, and reminder workflows to make personal receipt management easier.

## Problem

Paper receipts are easy to lose, difficult to search, and inconvenient for tracking spending or managing return and exchange dates.

The project explored how a digital platform could:

- Centralize receipts and invoices
- Reduce dependence on physical paper
- Extract structured data from uploaded receipts
- Receive invoices electronically from POS systems
- Organize purchases by category
- Provide spending insights
- Support reminders related to returns and exchanges

## Solution

Fawterha provides two main invoice-ingestion paths:

### 1. Uploaded receipts

```text
Upload Receipt
      ↓
Store Attachment
      ↓
AI Extraction
      ↓
Validate Structured Data
      ↓
Create Digital Invoice
      ↓
Categorize & Display
```

### 2. POS-integrated invoices

```text
POS / External System
      ↓
Authenticated API Request
      ↓
Validate User & Invoice Data
      ↓
Duplicate / Idempotency Check
      ↓
Persist Invoice
      ↓
Make Available in User Archive
```

## Key Capabilities

- User registration and authentication
- Email verification and password-reset workflows
- JWT-protected application endpoints
- Receipt image/PDF upload
- AI-assisted receipt data extraction
- Digital invoice creation
- User-specific invoice retrieval
- Invoice categorization
- Weekly, monthly, and yearly spending reports
- POS invoice ingestion through an external API
- Duplicate-handling for repeated external invoice requests
- Notifications and reminder-related workflows

## Architecture

```text
Android Application
       │
       │ REST API
       ▼
Node.js + Express.js Backend
       │
       ├── Authentication & User Services
       ├── Receipt / Invoice Services
       ├── Reporting Services
       ├── Notification Services
       ├── AI Extraction Integration
       └── External POS Integration
       │
       ▼
PostgreSQL / Supabase
```

External integrations include:

- **Google Gemini API** — structured data extraction from uploaded receipts
- **Odoo POS** — electronic invoice ingestion
- **Email services** — verification and account-related flows

## Backend API Areas

The backend was organized around functional routes such as:

```text
/auth
/receipts
/notifications
/expense-limits
/reports
/external
```

Examples of supported backend behavior include:

- Uploading receipt attachments
- Processing attachments with AI
- Creating an invoice from extracted data
- Updating invoice categories
- Retrieving user invoices
- Soft-deleting invoices
- Generating weekly/monthly/yearly reports
- Receiving invoices from an external POS source

## External Integration Design

The external invoice endpoint was designed to handle repeated delivery safely.

At a high level:

```text
External invoice arrives
        ↓
Authenticate request
        ↓
Validate payload
        ↓
Resolve application user
        ↓
Check whether invoice already exists
        ↓
Existing → return existing record
New      → persist and return created record
```

This avoids creating duplicate invoices when an external system retries the same request.

## Security Considerations

The project included several security-related mechanisms:

- Password hashing
- JWT-based authentication
- Protected routes
- User ownership validation
- Email/OTP verification flows
- API-key protection for external integration
- Environment variables for secrets and service credentials

No real secrets or production configuration are included in this portfolio repository.

## Testing & Validation

Testing included:

- REST API testing with Postman
- Valid and invalid request scenarios
- Authentication and authorization checks
- Database state and constraint validation
- Integration testing
- Duplicate-invoice behavior
- User-specific data access
- Functional testing
- End-user validation with the application frontend

## My Role

I focused primarily on **backend and data development**.

My contributions included:

- Backend service and REST API development
- Database-related design and implementation work
- Authentication and account workflows
- Invoice-processing logic
- Google Gemini API integration for receipt extraction
- Contribution to Odoo POS integration
- API and database testing
- Requirements analysis
- User stories and acceptance criteria
- Workflow definition and backlog work
- Technical documentation

Because this was a team graduation project, this case study distinguishes my own contribution from the overall product scope.

## Technology Stack

| Area | Technology |
| --- | --- |
| Backend | Node.js, Express.js |
| Database / Platform | PostgreSQL, Supabase |
| API Style | REST |
| AI Integration | Google Gemini API |
| POS Integration | Odoo |
| Authentication | JWT, password hashing, verification flows |
| Testing | Postman, database validation, functional testing |
| Collaboration | Git, GitHub |

## What This Project Demonstrates

This project demonstrates experience across more than implementation alone:

- Translating a product problem into technical workflows
- Designing and integrating REST APIs
- Working with relational data
- Integrating external systems
- Applying authentication and data-ownership controls
- Handling duplicate external requests
- Testing API and database behavior
- Connecting requirements, implementation, and validation



## Verified Technical Evidence

The original graduation project was developed collaboratively in the shared `fawterha-project/backend` repository.

One of my merged pull requests is publicly available and provides direct evidence of my backend contribution:

- **PR #9 — Auth, receipts, categories, and initial backend structure**  
  https://github.com/fawterha-project/backend/pull/9

That contribution includes backend work around JWT authentication middleware, receipt attachment handling, invoice retrieval and ownership checks, receipt-processing flows, and AI-assisted extraction integration.

For a recruiter-friendly summary of what this PR demonstrates, see [TECHNICAL-EVIDENCE.md](TECHNICAL-EVIDENCE.md).

## Repository Note

The original implementation was developed in a shared team repository.

This repository is intentionally a **sanitized portfolio representation**. It does not duplicate the original repository, claim sole ownership of team work, or expose source code and information that should remain with the original project.
