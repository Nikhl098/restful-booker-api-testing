# Test Plan - Restful Booker API

## 1. Objective

Verify the authentication and booking management endpoints of the Restful Booker practice API behave correctly for valid, invalid and unauthorized requests.

## 2. System under test

- Base URL: https://restful-booker.herokuapp.com
- Type: public REST API built for API testing practice (JSON over HTTP)

## 3. Scope

**In scope**
- POST /auth - token generation, valid and invalid credentials
- POST /booking - create booking
- GET /booking/{id} - retrieve booking
- GET /booking?firstname=&lastname= - search filter
- PUT /booking/{id} - full update with token
- PATCH /booking/{id} - partial update with token
- DELETE /booking/{id} - delete with token
- Negative: update without token, get deleted/non-existent booking
- GET /ping - health check

**Out of scope**
- Performance and load testing
- Security penetration testing
- UI testing (no UI exists)

## 4. Approach

- Black-box API testing: send real HTTP requests, validate status codes and response bodies against API documentation
- Full CRUD lifecycle executed on one booking created during the run
- Results and raw responses recorded in `test-results.md`

## 5. Environment and tools

- HTTP client: curl / Postman (same requests provided as a Postman collection)
- Date: 29 September 2026

## 6. Entry criteria

- API health check (/ping) returns 201

## 7. Exit criteria

- All 12 planned test cases executed with recorded responses
- Execution report prepared

## 8. Deliverables

- API test cases with actual results (`api-test-cases.md`)
- Execution report with request/response evidence (`test-results.md`)
- Postman collection (`Restful-Booker.postman_collection.json`)
