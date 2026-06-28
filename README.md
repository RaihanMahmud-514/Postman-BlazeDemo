# API Test Automation Suite — BlazeDemo

A Postman-based API test collection for [BlazeDemo](https://blazedemo.com), integrated with Newman CLI for CI/CD pipeline execution.

## What this covers

| Endpoint | Test scenarios |
|---|---|
| Flight search | Valid routes, invalid city pairs, boundary inputs |
| Flight selection | Seat availability, pricing validation |
| Booking | Form field validation, required field checks |
| Confirmation | Response schema, booking ID format, status codes |

## Test design

- **Authentication**: session handling across requests
- **Schema validation**: response structure verified on every endpoint
- **Boundary analysis**: min/max passenger counts, date edge cases
- **Error responses**: 4xx handling, invalid input rejection
- **Chained requests**: booking ID from search passed into confirmation

## Running locally

```bash
# Install Newman
npm install -g newman newman-reporter-htmlextra

# Run the collection
newman run "Postman Collections/BlazeDemo.postman_collection.json" \
  -r htmlextra \
  --reporter-htmlextra-export results/report.html
```

## CI/CD integration

Newman is configured to run on every code push, generating an HTML report automatically. This removes the need for manual API regression before each release.

## Tech stack

- **Postman** — collection authoring and local execution
- **Newman CLI** — command-line runner for pipeline integration
- **newman-reporter-htmlextra** — HTML test reports
