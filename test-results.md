# Test Results - Restful Booker API

Execution date: 29 September 2026 | Tester: Nikhil Partap Singh
Base URL: https://restful-booker.herokuapp.com

Raw evidence from the actual run (responses shortened where noted).

## TC-API-01 - Create token (valid)
```
POST /auth  {"username":"admin","password":"password123"}
-> {"token":"1e4055ced27641b"}
```

## TC-API-02 - Create token (wrong password)
```
POST /auth  {"username":"admin","password":"wrong"}
-> {"reason":"Bad credentials"}
```

## TC-API-03 - Create booking
```
POST /booking
{"firstname":"Nikhil","lastname":"Singh","totalprice":1500,"depositpaid":true,
 "bookingdates":{"checkin":"2026-10-01","checkout":"2026-10-05"},"additionalneeds":"Breakfast"}
-> {"bookingid":1318, "booking":{ ...data echoed exactly as sent... }}
```

## TC-API-04 - Get booking
```
GET /booking/1318
-> {"firstname":"Nikhil","lastname":"Singh","totalprice":1500,"depositpaid":true,
    "bookingdates":{"checkin":"2026-10-01","checkout":"2026-10-05"},"additionalneeds":"Breakfast"}
```

## TC-API-05 - Full update (PUT) with token
```
PUT /booking/1318  Cookie: token=...
{"firstname":"Nikhil","lastname":"Partap Singh","totalprice":2000,"depositpaid":false,
 "bookingdates":{"checkin":"2026-10-02","checkout":"2026-10-06"},"additionalneeds":"Late checkout"}
-> 200, updated fields returned
```

## TC-API-06 - Update without token
```
PUT /booking/1318 (no Cookie) -> HTTP 403 Forbidden
```

## TC-API-07 - Partial update (PATCH)
```
PATCH /booking/1318  Cookie: token=...  {"totalprice":2500}
-> 200, totalprice=2500, all other fields unchanged
```

## TC-API-08 - Search by name
```
GET /booking?firstname=Nikhil&lastname=Partap%20Singh
-> [{"bookingid":1318}]
```

## TC-API-09 - Delete booking
```
DELETE /booking/1318  Cookie: token=... -> HTTP 201
```

## TC-API-10 - Get deleted booking
```
GET /booking/1318 -> HTTP 404
```

## TC-API-11 - Get non-existent booking
```
GET /booking/999999999 -> HTTP 404
```

## TC-API-12 - Health check
```
GET /ping -> HTTP 201
```

## Summary

| Metric | Value |
|---|---|
| Test cases executed | 12 |
| Passed | 12 |
| Failed | 0 |
| Pass rate | 100% |
| Defects found | 0 |

The API behaved as documented across the full CRUD lifecycle, authorization checks, search and negative paths.
