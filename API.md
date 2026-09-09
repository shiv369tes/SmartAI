# API contracts

| Endpoint | Purpose |
|---|---|
| `POST /api/imports` | Create an authenticated import record and signed upload URL. |
| `POST /api/imports/:id/analyze` | Queue server-side analysis. |
| `POST /api/imports/analyze` | Development analyzer for a multipart workbook. |
| `GET /api/imports/:id/preview` | Return a paginated, sanitized preview. |
| `POST /api/mappings/analyze` | Request structured AI mapping recommendations. |
| `PUT /api/mappings/:id` | Approve or correct one mapping. |
| `POST /api/sync` | Confirm and queue a chunked sync. |
| `GET /api/sync/:id` | Return persisted progress and errors. |

All non-public endpoints require authentication, organization membership, and Zod input validation. The live API needs persistence and auth wiring before deployment.
