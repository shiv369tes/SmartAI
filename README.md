# SheetSync AI

An Excel-to-Smartsheet workflow platform with a usable demo experience and server-side boundaries for real integrations.

## Run locally

1. Copy `.env.example` to `.env` and set values. `AI_PROVIDER=demo` enables the credential-free UI.
2. Run `npm install`.
3. Run `npm run dev`, then open `http://localhost:3000`.

## Database

Install Prisma (`npm i -D prisma && npm i @prisma/client`), then run `npx prisma migrate dev --name init` and `npx prisma generate`. Use PostgreSQL in development and production.

## Smartsheet OAuth

Create an OAuth app in Smartsheet, set the callback to `SMARTSHEET_REDIRECT_URI`, and store the client credentials only in server environment variables. Exchange the callback code server-side, encrypt the tokens, and create a `SmartsheetConnection` scoped to the active organization.

## Production deployment

Deploy the Next.js app to Vercel and attach PostgreSQL plus object storage. Run an independent worker/queue for analysis and sync chunks; do not run large imports in API request lifetimes. Configure an AI adapter selected by `AI_PROVIDER` and monitoring that redacts tokens and file content.
