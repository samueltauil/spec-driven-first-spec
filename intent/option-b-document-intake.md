# Intent brief: Inbound document intake from Fabrikam

**Product owner**: Product owner, Operations Intake  |  **Engineering lead**: Engineering lead, Operations Platform  |  **Date**: 2026-11-24

> Option B. Product owner leads. This brief explains the problem, not the solution. It builds on the inbound
> document triage you traced in exercise 1, but this time nobody has written the rules: your proposal and spec
> decide what people and systems do, and your open questions say what is still unknown.

## 1. Problem and outcome

- **Problem**: Contoso receives faxed and scanned documents from Fabrikam in different layouts, page orders and levels of legibility. The initial request says only "put each document in the correct queue". The synthetic intake set shows that many documents are not that simple.
- **Outcome**: People and systems know what to do beyond the happy path: what stays unattached, who acts next, and how receipt time and every page stay accounted for across handoffs.
- **Not decided yet**: which document types are in scope, what the system may do on its own, and what happens when a receiving queue is unavailable.

## 2. Constraints

- Do not assume OCR, matching lookups or a receiving team's queue is available.
- Classification, routing and attachment are system suggestions. Business decisions stay with people.
- Receipt time and every page must stay accounted for across handoffs.
- Synthetic data only. Never use a real document, member or person.

## 3. Synthetic intake set

| Document | What it is |
| --- | --- |
| FAX-20261124-0101 | A readable Fabrikam claim form, 3 pages, with member ID CHP-0007731 and claim CLM-2026-000512 |
| FAX-20261124-0102 | An unreadable scan: 2 pages too dark to read |
| FAX-20261124-0103 | A prior-authorization form with no member ID and no claim number |
| FAX-20261124-0104 | An appeal letter that was sent to the claims queue instead of the appeals queue |
| FAX-20261124-0105 | A second copy of FAX-20261124-0101, received 40 minutes later |
| FAX-20261124-0106 | A Proseware marketing flyer, not a member document at all |

## 4. Open questions

1. Which document types are in scope for this change, and which are not?
2. What happens to an unreadable, incomplete, misrouted or duplicate document, and who acts next?
3. When does the receipt clock start, and does it survive a re-route?
4. What happens if a receiving queue is unavailable?
