# Coldkeys and Wallets API

The Coldkeys and Wallets API provides comprehensive information about Bittensor coldkeys, their associated wallets, transaction history, and exchange interactions.

## Available Endpoints

### Account Information
- [Get Account](account.md) - Get current coldkey account information
- [Get Account History](account-history.md) - Retrieve historical account data

### Transactions
- [Get Transfers](transfers.md) - View transfer transactions
- [Get Exchanges](exchanges.md) - Access exchange-related information

## Common Parameters

All Coldkeys/Wallets API endpoints support these common parameters:

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| ss58_address | string | Yes | SS58 formatted coldkey address | None |
| block_number | int32 | No | Specific block to query | Latest |
| format | string | No | Response format ("json" or "raw") | "json" |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Items per page | 50 |

## Response Format

All responses follow the standard format:

```json
{
    "success": true,
    "data": {
        // Endpoint-specific data
    },
    "pagination": {
        "current_page": 1,
        "total_pages": 10,
        "total_items": 486,
        "items_per_page": 50
    },
    "timestamp": "2025-02-23T19:12:00.001Z"
}
```

## Notes

- All timestamps are in ISO 8601 format
- Addresses are provided in both SS58 and hex formats
- Balance values are provided in both rao and tao units
- Historical data queries support pagination
- Block numbers are provided as integers
- Transaction hashes follow standard blockchain format
- Exchange rates use 8 decimal precision

## Authentication

All endpoints require authentication using an API key. Include your API key in the `Authorization` header of your requests:

```
Authorization: YOUR-API-KEY
``` 