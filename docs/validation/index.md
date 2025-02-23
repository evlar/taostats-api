# Validation API

The Validation API provides comprehensive information about validators in the Bittensor network, including their performance metrics, relationships, and historical data.

## Available Endpoints

### Core Validator Information
- [Get Validator](get-validator.md) - Get current validator information
- [Get Validator History](get-validator-history.md) - Retrieve historical validator data
- [Get Validator Metrics](get-validator-metrics.md) - Get current validator performance metrics
- [Get Validator Metrics History](get-validator-metrics-history.md) - View historical performance metrics

### Relationships and Identity
- [Get Parent/Child Hotkey](get-parent-child-hotkey.md) - Query parent/child hotkey relationships
- [Get Parent/Child Hotkey History](get-parent-child-hotkey-history.md) - View historical relationship data
- [Get Validator Identity](get-validator-identity.md) - Retrieve validator identity information
- [Get Validator Performance](get-validator-performance.md) - Get detailed performance metrics

### Weights and Shares
- [Get Current Validator Weights](get-current-validator-weights.md) - View current validator weight distributions
- [Get Validator Weights History](get-validator-weights-history.md) - Retrieve historical weight data
- [Get Validator Alpha Shares](get-validator-alpha-shares.md) - Query current alpha share distribution
- [Get Validator Alpha Shares (Historical)](get-validator-alpha-shares-historical.md) - View historical alpha shares
- [Get Weight Copiers](get-weight-copiers.md) - Identify validators copying weights
- [Get Validator Emission by Subnet](get-validator-emission-by-subnet.md) - View emissions across subnets

## Common Parameters

All Validation API endpoints support these common parameters:

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
- Numerical values use string format for precision
- Historical data queries support pagination
- Block numbers are provided as integers
- Performance metrics are normalized to [0,1] range 