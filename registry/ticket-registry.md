# Ticket registry (canonical index)

**Single source of truth** for tickets in this repo.  
Do not maintain a second ticket list elsewhere.

| ticket-id | title | requester | status | priority | handover-count | ticket-file |
| --- | --- | --- | --- | --- | --- | --- |
| TKT-001 | CPI cost — Golden Tax app | Chakriya | new | B | 0 | tickets/20260417-142958-TKT-001-cpi-cost-chakriya.md |

## Allowed values

- `status`: `new`, `in progress`, `blocked`, `closed`
- `priority`: `A`, `B`, `C`
  - `A`: asap
  - `B`: do after A
  - `C`: parking

## Default values for new ticket rows

- `status = new`
- `priority = B`

## Ticket ID assignment (agent rule)

When creating a new ticket:

1. Read this registry.
2. Find the highest existing `TKT-###`.
3. Assign the next number (zero-padded to 3 digits), e.g. `TKT-001`, `TKT-002`, `TKT-003`.
4. If no ticket row exists yet, start at `TKT-001`.
5. IDs are global in this repo and never reused.

## Ticket file naming pattern

Create ticket files under `tickets/` with:

`YYYYMMDD-HHMMSS-<ticket-id>-<ticket-title>-<requester>.md`

- Time uses UTC+8 and `HHMMSS` (no colons).
- `<ticket-title>` uses kebab-case.
- `<requester>` is requester full name normalized to kebab-case for filename safety.

## Handover linkage

- Keep related handover links in the ticket file itself (one ticket can link to many handover files).
- Keep `handover-count` in this registry aligned with the number of linked handover files in that ticket file.
