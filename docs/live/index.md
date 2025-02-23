# Live API

The Live API provides real-time data and streaming information from the Bittensor network.

## Available Endpoints

- [Get Free Tao Balance](get-free-tao-balance.md) - Query available free tao balance
- [Get Extrinsics for Block Range](get-extrinsics-block-range.md) - Retrieve extrinsics within a specified block range
- [Get Latest Block Extrinsics](get-latest-block-extrinsics.md) - Get extrinsics from the most recent block
- [Get Extrinsics for Specific Block](get-extrinsics-specific-block.md) - Query extrinsics for a particular block
- [Get Raw Extrinsics for Specific Block](get-raw-extrinsics-specific-block.md) - Retrieve raw extrinsic data for a block
- [Get Node Transaction Pool](get-node-transaction-pool.md) - View current transaction pool status
- [Get Node Version](get-node-version.md) - Check node software version
- [Get Pallet Consts](get-pallet-consts.md) - Retrieve pallet constants
- [Get Pallet Consts by Id](get-pallet-consts-by-id.md) - Get constants for a specific pallet
- [Get Pallet Events by Id](get-pallet-events-by-id.md) - Query events from a specific pallet

## Common Parameters

All Live API endpoints support these common parameters:

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| network | string | No | Network to query (e.g., "finney") | "finney" |
| format | string | No | Response format ("json" or "raw") | "json" |

## Response Format

All Live API responses follow the standard format:

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
- Addresses are provided in both SS58 and hex formats where applicable
- Raw responses maintain original blockchain format
- JSON responses are normalized for consistency 