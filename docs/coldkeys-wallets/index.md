# Coldkeys and Wallets API

The Coldkeys and Wallets API provides information about Bittensor coldkeys and their associated wallets.

## Available Endpoints

### [Get Account](account.md)
Get information about a specific coldkey account.
```
GET https://api.taostats.io/api/coldkeys-wallets/account/v1
```

### [Get Account History](account-history.md)
Get historical data for a coldkey account.
```
GET https://api.taostats.io/api/coldkeys-wallets/history/v1
```

### [Get Exchanges](exchanges.md)
Get exchange-related information for coldkeys.
```
GET https://api.taostats.io/api/coldkeys-wallets/exchanges/v1
```

## Common Parameters

All endpoints in this section share some common parameters:

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| ss58_address | string | Yes | The SS58 formatted address of the coldkey |

## Authentication

All endpoints require authentication using an API key. Include your API key in the `Authorization` header of your requests:

```
Authorization: YOUR-API-KEY
```

## Response Format

All endpoints return data in JSON format with a standard structure including pagination where applicable. 