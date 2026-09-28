# AGENTS.md — Base44 dev environment

## Project
LoanDocSeparator is a **single static HTML file** (`index.html`) — a client-side PDF processing tool ("by SigningLedger"). No backend, no database, no build step. All libraries (Tailwind, PDF.js, PDF-Lib, jsPDF, JSZip, FileSaver) load from CDNs. PDF processing happens entirely in the browser.

## Running
Served by `nginx:alpine` via `docker-compose.base44.yml` on host port 3000.
- A custom `nginx.base44.conf` is mounted because the bind-mounted repo dir has `700` permissions; nginx must run as `user root;` to read it.
- Edits to `index.html` are served live on browser refresh (no build/reload step needed). Use `reload_preview` only after compose/config changes.

## Secrets
None required — fully client-side app.

## Verify
`curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/` → `200`.
