# SheetSync AI architecture

The browser only handles user interaction and preview pagination. Files, OAuth credentials, AI calls, validation, and Smartsheet writes stay server-side.

`Upload → object storage → import job → workbook analysis → reviewed mappings → validation → sync job → chunked Smartsheet writes → audit/report`

`ExcelImport` is the source of truth for the import state machine. A worker claims `SyncJob` records with `QUEUED` status, persists progress after each chunk, and uses idempotency keys based on import, destination, and row key. All tenant-owned reads are constrained by `organizationId` and role checks.

AI providers implement `AIProvider` in `src/lib/ai/contracts.ts`. Responses are Zod-validated before they affect recommendations. Smartsheet OAuth tokens are encrypted at rest and accessed only by a server-side adapter.
