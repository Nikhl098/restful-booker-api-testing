# API Test Cases - Restful Booker

Executed: 29 September 2026 | Tester: Nikhil Partap Singh
Base URL: https://restful-booker.herokuapp.com

| ID | Title | Request | Expected result | Actual result | Status |
|----|-------|---------|-----------------|---------------|--------|
| TC-API-01 | Create token - valid credentials | POST /auth {"username":"admin","password":"password123"} | 200 with a token in the body | Token returned (e.g. "1e4055ced27641b") | PASS |
| TC-API-02 | Create token - wrong password | POST /auth {"username":"admin","password":"wrong"} | Error, no token | {"reason":"Bad credentials"} | PASS |
| TC-API-03 | Create booking | POST /booking with valid booking JSON | 200 with bookingid and echoed data | bookingid 1318 created, data echoed correctly | PASS |
| TC-API-04 | Get booking | GET /booking/1318 | 200 with the created booking's fields | All fields returned exactly as created | PASS |
| TC-API-05 | Full update with token | PUT /booking/1318 (Cookie: token) | 200 with updated fields | Updated lastname, price, dates returned correctly | PASS |
| TC-API-06 | Update without token | PUT /booking/1318, no auth cookie | 403 Forbidden | 403 returned | PASS |
| TC-API-07 | Partial update with token | PATCH /booking/1318 {"totalprice":2500} | 200, only totalprice changed | totalprice now 2500, other fields unchanged | PASS |
| TC-API-08 | Search by name | GET /booking?firstname=Nikhil&lastname=Partap Singh | List containing the booking | [{"bookingid":1318}] returned | PASS |
| TC-API-09 | Delete booking with token | DELETE /booking/1318 (Cookie: token) | 201 Created | 201 returned | PASS |
| TC-API-10 | Get deleted booking | GET /booking/1318 after delete | 404 Not Found | 404 returned | PASS |
| TC-API-11 | Get non-existent booking | GET /booking/999999999 | 404 Not Found | 404 returned | PASS |
| TC-API-12 | Health check | GET /ping | 201 Created | 201 returned | PASS |

**Result: 12 / 12 passed.**
