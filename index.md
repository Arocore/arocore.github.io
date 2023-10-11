---
layout: default
title: Home
---

Welcome to the Sinkabirum API documentation. 

Sinkabirum offers a powerful API designed to provide quick and efficient location-based
access to Swedish crime data. Whether you're developing an application, conducting research,
or just curious about crime trends in Sweden, our API is here to assist.

Dive into the documentation to learn how to get started, understand the endpoints
and integrate the Sinkabirum API into your projects.

---

**Key Features**:
- **Location-based Queries**: Retrieve crime data specific to a location or region.
- **Time-specific Queries**: Retrieve crime data for a specific time span
- **Fast Responses**: Designed for efficiency, ensuring you get your data when you need it.
- **Comprehensive Data**: Access a rich dataset covering various types of crimes.

Happy coding!

## Authentication

All API endpoints require authentication using an API key. This ensures that only authorized users can access the data and helps prevent abuse.

### How to Authenticate:

1. Obtain an API key. Contact the Sinkabirum team to request access.
2. Include the API key in the header of every request to the API using the `x-api-key` header field.

### Example:

When making a request to the API, set the header as:

```bash
curl -H "x-api-key: YOUR_API_KEY_HERE" https://api.sinkabirum.com/location/stats?lat=59.3293&lng=18.0686&radius=1000
```

Replace `YOUR_API_KEY_HERE` with your actual API key.

### Error Responses:

- **401 Unauthorized**: If the API key is missing, invalid, or not provided in the `x-api-key` header, the API will return a `401` status code.
  
- **429 Too Many Requests**: If the rate limit for the API key is exceeded, the API will return a `429` status code.

Ensure you manage your API key securely and do not exceed the allowed request rate to ensure uninterrupted access.

---

## Endpoint: `/location/stats`

Retrieve crime statistics based on a specific location and radius in Sweden.

### Method:

`GET`

### Parameters:

- **lat** (required): Latitude of the center point.
- **lng** (required): Longitude of the center point.
- **radius** (required): The radius (in meters) around the center point to fetch the crime statistics.
- **from** (optional): Start date for the statistics in ISO format (`YYYY-MM-DD`). Defaults to the beginning of recorded data.
- **to** (optional): End date for the statistics in ISO format (`YYYY-MM-DD`). Defaults to the current date.

### Response:

Returns a JSON object containing crime statistics for the specified location and time range.

### Example Request:

```bash
curl -H 'x-api-key: <your-api-key>' https://api.sinkabirum.se/location/stats\?lat\=59.325102\&lng\=18.071411\&radius\=1000\&from\=2020-12-01T00:00:00\&to\=2020-12-31T23:59:00
```

```json
[
  {
    "type": "Bråk & Stök",
    "count": 4,
    "risk": 0.04107224337855364
  },
  {
    "type": "Våld & Hot",
    "count": 2,
    "risk": 0.02053612168927682
  },
  {
    "type": "Inbrott & Stöld",
    "count": 1,
    "risk": 0.01026806084463841
  },
  {
    "type": "Trafikbrott",
    "count": 1,
    "risk": 0.01026806084463841
  }
]
```

### Error Handling:

- If `lat`, `lng`, or `radius` parameters are missing or not numbers, the API will return a `400` status code.
- If there's an internal server error, the API will return a `500` status code.

---

e

Continue exploring the documentation to learn more about other endpoints and functionalities as they become available.

