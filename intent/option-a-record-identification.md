# Intent brief: Record identification for Northwind Traders requests

**Product owner**: Product owner, Operations Intake  |  **Engineering lead**: Engineering lead, Records Platform  |  **Date**: 2026-11-24

> Option A. Product owner leads. This brief explains the problem, not the solution. Nobody has written a rule
> for it yet: your proposal and spec decide what the system does, and your open questions say what is still
> unknown.

## 1. Problem and outcome

- **Problem**: Contoso's intake team finds the claim-like record for each Northwind Traders request with a matching rule that combines the submitted record number and service date. The team assumed those two values identify exactly one record. A synthetic test now returns two candidates with the same values from different source systems, and another input returns no match at all.
- **Outcome**: Staff know when they may select a record, when they must stop, and who resolves an ambiguous match, without seeing more details than they need.
- **Not decided yet**: the exact matching fields, how values are normalized, what staff see for each result, and who resolves ambiguity.

## 2. Constraints

- Do not assume a searchable index or a unique key exists.
- Never guess which record a request belongs to.
- Show staff only the details they need to decide.
- Synthetic data only. Never use a real request, record or person.

## 3. Synthetic examples

| Request | Submitted values | What the lookup returns today |
| --- | --- | --- |
| NWT-REQ-20261124-0007 | Record number R-100245, service date 2026-10-03 | One record, from the claims system |
| NWT-REQ-20261124-0008 | Record number R-100311, service date 2026-10-07 | Two records with the same values: one from the claims system, one from the legacy billing system |
| NWT-REQ-20261124-0009 | Record number R-109999, service date 2026-10-12 | No record |
| NWT-REQ-20261124-0010 | Record number ` r-100245 ` (lowercase, extra spaces), service date 03/10/2026 | Not tested yet |

## 4. Open questions

1. Which fields make up the matching rule, and how is each one normalized (case, spaces, leading zeros, date formats)?
2. What may staff see and do when there are zero, one or several candidates?
3. Who resolves an ambiguous match, and how quickly?
4. Who can confirm what the lookup actually searches, and how?
