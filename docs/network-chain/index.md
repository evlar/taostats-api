# Network/Chain API

The Network/Chain API provides comprehensive access to blockchain data, network statistics, and chain state information from the Bittensor network.

## Available Endpoints

### Block Information
- [Get Blocks](blocks.md) - Retrieve block data
- [Get Block Number over Interval](block-interval.md) - Calculate block numbers for time intervals

### Chain Activity
- [Get Extrinsics](extrinsics.md) - Query blockchain transactions
- [Get Events](events.md) - Access chain events
- [Get Chain Calls](chain-calls.md) - View chain call information
- [Get Proxy Calls](proxy-calls.md) - Access proxy call data

### Network Statistics
- [Get Stats Latest](stats-latest.md) - View current network statistics
- [Get Stats History](stats-history.md) - Access historical network stats

### Runtime Information
- [Get Runtime Version](runtime-version.md) - Check current runtime version
- [Get Historical Runtime Version](runtime-version-history.md) - View runtime version history

## Common Parameters

All Network/Chain API endpoints support these common parameters:

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| block_number | int32 | No | Specific block to query | Latest |
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

- All timestamps are in ISO 8601 format
- Block numbers are provided as integers
- Extrinsic hashes follow standard blockchain format
- Event data includes all indexed and non-indexed fields
- Chain calls include full parameter details
- Statistics are updated approximately every block
- Historical data is available from network genesis 