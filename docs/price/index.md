# Price API

The Price API provides real-time and historical price data for Bittensor (TAO). The following endpoints are available:

## Available Endpoints

### [Get Latest Price](price.md)
Get the current price and market data for TAO.
```
GET https://api.taostats.io/api/price/latest/v1
```

### [Get Price History](history.md)
Get historical price data with support for pagination and time ranges.
```
GET https://api.taostats.io/api/price/history/v1
```

### [Get Price OHLC](ohlc.md)
Get Open, High, Low, Close price data.
```
GET https://api.taostats.io/api/price/ohlc/v1
```

## Authentication

All endpoints require authentication using an API key. Include your API key in the `Authorization` header of your requests.

```
Authorization: YOUR-API-KEY
```

## Rate Limits

Please refer to your API key documentation for specific rate limit information.

## Response Codes

- 200: Successful request
- 401: Unauthorized - Invalid or missing API key
- 403: Forbidden - API key doesn't have access to this endpoint
- 429: Too Many Requests - Rate limit exceeded
- 500: Internal Server Error

## Notes

- All numerical values are returned as strings to preserve precision
- Timestamps are in ISO 8601 format
- Price data is updated approximately every minute
- Historical data availability may vary 