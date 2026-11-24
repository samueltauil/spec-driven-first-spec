# Member eligibility capability

## Purpose
Return a member's coverage status for a requested service date.

## Requirements

### Requirement: Authenticated eligibility lookup
The service MUST require an authenticated caller before returning member eligibility information.

#### Scenario: Authenticated request
- GIVEN an authenticated caller
- WHEN eligibility is requested for a service date
- THEN the service returns the coverage status applicable to that date

### Requirement: Sensitive-data protection
The service MUST NOT include protected member data in application logs or error responses.

#### Scenario: Sensitive data is not exposed
- GIVEN a request containing protected member data
- WHEN application logs or an error response is produced
- THEN protected member data is not included
