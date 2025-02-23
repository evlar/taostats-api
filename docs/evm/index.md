# EVM API

The EVM API provides access to Ethereum Virtual Machine data and interactions within the Bittensor network.

## Available Endpoints

- [Get EVM Transaction](get-evm-transaction.md) - Retrieve transaction details
- [Get EVM Block](get-evm-block.md) - Get block information
- [Get EVM Contract](get-evm-contract.md) - Query contract data
- [Get EVM Log](get-evm-log.md) - Access event logs
- [Get EVM Address](get-evm-address.md) - Get address information

## Common Parameters

All EVM API endpoints support these common parameters:

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| network | string | No | Network to query (e.g., "finney") | "finney" |
| format | string | No | Response format ("json" or "raw") | "json" |

## Response Format

All responses follow the standard format:

```json
{
    "success": true,
    "data": {
        // Endpoint-specific data
    },
    "timestamp": "2025-02-23T19:12:00.001Z"
}
```

## Notes

- All addresses are provided in standard EVM hex format
- Transaction hashes follow EVM conventions
- Block numbers are provided as integers
- Gas prices and values are provided as strings for precision
- Timestamps are in ISO 8601 format
- Contract ABIs are provided in standard JSON format
- Event logs include indexed and non-indexed parameters 