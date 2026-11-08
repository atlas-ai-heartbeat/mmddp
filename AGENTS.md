
# THEIN GYI MARKET - AI DEVELOPMENT RULES

## 1. Project identity
Project: Thein Gyi Market Digital Discovery Platform.
Initial market: Thein Gyi Market, Yangon, Myanmar.
Pilot target: 100 shops and 1,000 customers.

This is a market discovery and shop directory platform.
It is NOT an e-commerce checkout or delivery marketplace.

## 2. Application architecture
Build three separate applications:
1. Customer App: Flutter.
2. Owner App: Flutter.
3. Admin Portal: Next.js and TypeScript.

Shared backend:
- NestJS
- REST API
- PostgreSQL
- PostGIS
- Redis
- Docker

The applications may share backend services but must
enforce separate application permissions and user journeys.

## 3. Business restrictions
Do not introduce:
- Online checkout
- Customer wallet
- Delivery dispatch
- Delivery provider application
- Order management
- Transaction commission

These are outside the MVP scope.

## 4. Identity rules
Customer registration:
- Phone number
- OTP verification
- Customer profile

Owner registration:
- Phone number
- NRC or driving licence evidence
- Face verification where supported
- Shop/business evidence
- Admin verification

Customer registration must never require owner verification.

Never use NRC as a database primary key.
Never expose identity evidence through public APIs.
Do not store raw biometric data without explicit approval.

## 5. Shop rules
Owner verification and shop approval are separate statuses.
An owner may manage multiple shops.
Each shop has an independent approval status.

Pending shops must:
- Be clearly labelled pending/unverified.
- Not receive verified badges.
- Not receive sponsored placement.
- Not receive public reviews.

Do not assume pending shops can expose all public fields.
Follow the approved publication policy.

## 6. Development rules
- Read relevant documentation before implementation.
- Do not invent business requirements.
- Ask for clarification when a requirement is ambiguous.
- Use database migrations.
- Validate all API inputs.
- Enforce authorization on the server.
- Use UUID identifiers.
- Add tests for business rules.
- Update API documentation when endpoints change.
- Do not hardcode secrets.
- Never use real customer identity data in development.

## 7. Quality requirements
Every feature must include:
- Requirement reference ID
- Implementation
- Validation
- Automated tests
- Acceptance criteria
- Error handling
- Security review

## 8. AI agent behaviour
Before modifying files:
1. Inspect the existing project.
2. Read relevant requirements.
3. Explain the implementation plan.
4. List files to be created or modified.
5. Identify risks and assumptions.

Do not rewrite unrelated modules.
Do not delete existing functionality without approval.
Do not run destructive database commands without approval.

After implementation:
1. Run relevant tests.
2. Run lint and type checks.
3. Report changed files.
4. Report test results.
5. Report unresolved issues.
