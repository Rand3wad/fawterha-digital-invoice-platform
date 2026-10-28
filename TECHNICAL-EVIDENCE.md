# Technical Evidence

This file links the portfolio case study to verifiable work in the original shared graduation-project repository.

## Verified Pull Request

### PR #9 — Auth, Receipts, Categories & Initial Backend Structure

**Original pull request:**  
https://github.com/fawterha-project/backend/pull/9

**Author:** Rand3wad  
**Branch:** `rand-receipts-feature`  
**Status:** Merged

The pull request provides direct evidence of my contribution to the backend implementation.

## What the contribution demonstrates

### Authentication

The contribution includes JWT-based middleware that:

- Reads the Bearer token from the Authorization header
- Verifies the token
- Checks token state against stored authentication records
- Rejects invalid or revoked tokens
- Attaches authenticated user context to the request

### Receipt and attachment workflows

The contribution includes backend flows for:

- Uploading receipt images or PDF files
- Storing attachment metadata
- Associating data with the authenticated user
- Retrieving a user's receipts
- Retrieving invoice details
- Filtering user-owned records
- Deleting attachments and receipt-related data

### AI-assisted receipt processing

The contribution contains logic for:

- Sending uploaded receipt content to an AI extraction service
- Requesting structured invoice data
- Parsing structured output
- Validating whether uploaded content is a receipt
- Mapping extracted receipt data into application records
- Supporting automatic category assignment

### Data ownership and access control

Several flows scope data operations by the authenticated user's ID rather than relying only on a record identifier.

This is important for preventing one authenticated user from reading or modifying another user's records.

## Why the source code is not duplicated here

Fawterha was a team graduation project. The original repository remains the canonical source for collaborative code and commit history.

This portfolio repository therefore:

- Links to verifiable original contributions
- Explains my role and technical work
- Avoids copying the entire team codebase into a personal repository
- Avoids presenting collaborative work as solely mine
- Keeps the portfolio easy for recruiters to review

## Portfolio Context

The broader Fawterha solution includes work by multiple team members across mobile development, backend services, database design, integrations, reporting, notifications, and other product functionality.

The project-level README describes the complete solution, while this document specifically points to verifiable evidence of my own backend contribution.
