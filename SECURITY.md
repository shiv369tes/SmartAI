# Security model

- Verify file extension, MIME type, size, workbook dimensions, and storage ownership before parsing.
- Do not execute macros, formulas, or user-provided JavaScript. Formula cells are read as data only.
- Encrypt OAuth tokens with an authenticated encryption key; never return them to the client or logs.
- Scope every query by organization membership; record sensitive actions in `AuditLog`.
- Apply rate limiting to auth, upload, AI, and sync start endpoints. Use HTTP-only secure cookies and CSRF protection for cookie-authenticated mutations.
- Require explicit confirmation for replace/overwrite behavior and preserve row-level failures for retry.
