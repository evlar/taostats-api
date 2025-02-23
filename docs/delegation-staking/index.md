# Delegation/Staking API

The Delegation/Staking API provides comprehensive information about staking positions, delegation relationships, and related events in the Bittensor network.

## Available Endpoints

### Stake Management
- [Get Stake](get-stake.md) - Get current stake information (v2)
- [Get Historical Stake](get-historical-stake.md) - Retrieve historical stake data
- [Get Stake Balance](get-stake-balance.md) - Query current stake balances
- [Get Stake Balance Sum in Tao](get-stake-balance-sum.md) - Calculate total stake in Tao
- [Get Slippage](get-slippage.md) - View stake slippage metrics

### Delegation Events
- [Get Delegation Events](get-delegation-events.md) - Query staking/delegation events
- [Get dTao Delegation Events](get-dtao-delegation-events.md) - View dTao-specific delegation events
- [Get dTAO Delegation Events](dtao-delegation-events.md) - Retrieve detailed dTAO delegation information

## Common Parameters

All Delegation/Staking API endpoints support these common parameters:

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| block_number | int32 | No | Specific block to query | Latest |
| netuid | int32 | No | Network/subnet ID filter | None |
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

- All timestamps are in ISO 8601 format
- Addresses are provided in both SS58 and hex formats
- Balance values are provided in both rao and tao units
- Historical data queries support pagination
- Block numbers are provided as integers
- Slippage values are provided as percentages
- Event data includes transaction hashes for reference 