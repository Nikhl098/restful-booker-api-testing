# Restful Booker - API Testing Project

API testing of Restful Booker (https://restful-booker.herokuapp.com), a public practice API for learning API testing. Tests executed with Postman-style HTTP requests covering authentication and full booking CRUD.

**Author:** Nikhil Partap Singh - Manual QA Tester (Fresher)
**Date executed:** 29 September 2026

## Scope

- Authentication: token creation with valid and invalid credentials
- Booking CRUD: create, read, full update (PUT), partial update (PATCH), delete
- Authorization: update without a token is rejected
- Search: filter bookings by firstname and lastname
- Negative tests: deleted and non-existent booking IDs return 404
- Health check: /ping

## Artifacts

| File | Contents |
|---|---|
| `test-plan.md` | API test plan: objectives, scope, approach, entry/exit criteria |
| `api-test-cases.md` | 12 API test cases with request, expected and actual results |
| `test-results.md` | Execution report with real request/response evidence |
| `Restful-Booker.postman_collection.json` | Importable Postman collection of the same requests |

## Result

12 of 12 test cases passed. Auth token flow, full CRUD cycle and negative paths all behaved as expected. Full evidence with actual API responses is in `test-results.md`.
