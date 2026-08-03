# WinIt deploy notes

Based on upstream **parse-dashboard 9.2.0**, plus WinIt fork options:

- `deleteOptions` — `{ class, columns, selectedRows, allData }` (default all `true`)
- `exportOptions` — `{ schema, selectedRows, allData }` (default all `true`)
- `securityOptions` — boolean (default `true`); set `false` to hide Security dialog in data browser

Upstream `preventDataExport` still works and disables all export UI when `true`.

Also keep using Parse Server `readOnlyMasterKey` + dashboard user `readOnly` for fully read-only accounts.

## Host (planned)

ECS Fargate image built from this repo's `Dockerfile`, private via NetBird / internal ALB.
See WinIt-backend #4576 / #4607.
