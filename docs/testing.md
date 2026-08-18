# Testing

Newton.ai is tested using production-style builds for security and release checks.

## Build checks

Typical release checks include:

```text
npm run lint
npm run build
npm run start
```

Development mode is used for quick troubleshooting rather than as the final security-validation environment.

## API security test categories

### Authentication

- no-session requests
- protected-route access
- authenticated normal flow

### Object-level access

- own resource
- another user's resource
- unknown object identifier
- malformed identifier

### Request integrity

- missing body
- malformed JSON
- wrong field type
- unsupported value
- incorrect content type
- oversized body

### AI security

- prompt-injection attempts
- malformed model output
- contradictory model output
- required output sections
- blank-answer handling where relevant

### Abuse controls

- successful guarded request
- request and token accounting
- short-window rate-limit rejection
- rejected-request accounting
- concurrent-request rejection
- successful lease release
- upstream model failure
- failed-request accounting
- failure-path lease cleanup
- recovery after failure

## Privacy during testing

Screenshots and logs intended for public use should be reviewed before publication.

Do not publish:

- bearer tokens
- cookies
- API keys
- environment variables
- private email addresses
- real student data
- sensitive database identifiers
- browser request headers containing credentials
