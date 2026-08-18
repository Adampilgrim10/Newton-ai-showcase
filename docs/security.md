# Security Engineering

Security is treated as a launch gate for Newton.ai.

This document intentionally provides a defensive, portfolio-level overview rather than production-sensitive implementation detail.

## Authentication and authorisation

Protected application routes require an authenticated user.

Customer-specific resources are checked for object-level access rather than assuming that possession of an object identifier grants access.

Database policies provide an additional isolation layer through Supabase Row Level Security.

## Data protection

Security controls include:

- Row Level Security on application tables
- server-side handling of privileged credentials
- no-store/private caching behaviour for sensitive responses
- safe client-facing error messages
- validation of identifiers and request payloads

## Request validation

API routes are hardened against malformed or abusive input using controls such as:

- JSON content-type enforcement
- request-body size limits
- type and shape validation
- supported-value allowlists
- malformed JSON handling
- bounded AI input lengths

## AI security

AI-facing routes are designed around the assumption that all user-supplied text is untrusted.

Controls include:

- prompt instructions that separate user content from system instructions
- prompt-injection resistance
- response-shape and integrity checks
- deterministic checks where appropriate
- generic upstream-error handling
- model-request timeouts and bounded retries

## Abuse controls

A shared AI guard provides central enforcement for:

- short-window per-user/per-route rate limits
- a global daily AI request quota
- per-user concurrent-request limits
- expiring active-request leases
- usage accounting

Rejected rate-limited or concurrency-limited requests are blocked before model execution.

## Security testing

The security review includes tests for:

- unauthenticated access
- cross-account access
- copied object URLs
- draft/private resource access
- malformed request bodies
- oversized payloads
- unsupported content types
- prompt injection
- AI response-format failures
- rate-limit enforcement
- concurrency enforcement
- upstream AI failure cleanup

## Deliberately excluded from this public repository

The following are not published:

- credentials or environment files
- production source code
- service-role keys
- database connection secrets
- private deployment configuration
- real user data
- security-sensitive operational detail
