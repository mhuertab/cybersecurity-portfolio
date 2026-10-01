# Identity & Access Management

## Objective

Show how identity security can be translated into operational controls that reduce excessive privilege while keeping business and technology teams productive.

## Core Principles

- Least privilege
- Role-based access
- Segregation of duties
- MFA for sensitive access
- Controlled privileged accounts
- Traceability of administrative activity
- Periodic access reviews
- Timely joiner / mover / leaver processes
- Temporary access where permanent privilege is unnecessary

## Access Lifecycle

**Request → Approval → Provisioning → Authentication → Use → Monitoring → Review → Revocation**

Each stage should produce sufficient evidence to answer:

- Who requested access?
- Who approved it?
- What privilege was granted?
- Why was it required?
- For how long?
- Was its use monitored?
- When was it reviewed or revoked?

## Privileged Access

Administrative access represents a different risk profile from standard user access. A mature model therefore separates normal identities from privileged identities and applies stronger controls such as PAM, MFA, session traceability and time-bound permissions.

## Example Control Pattern

For sensitive cloud or production access:

**User request → Manager/owner approval → Temporary role → Logged activity → Automatic expiration**

This reduces standing privilege and creates auditable evidence without making elevated access permanently available.

> The examples in this section are conceptual reference patterns and do not represent any specific company's access model.