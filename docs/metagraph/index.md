# Metagraph API

The Metagraph API provides detailed information about the network topology, neuron relationships, and subnet structures within the Bittensor network.

## Available Endpoints

### Core Metagraph Data
- [Get Metagraph](get-metagraph.md) - Get current metagraph state
- [Get Metagraph History](get-metagraph-history.md) - Retrieve historical metagraph data
- [Get Root Subnet Metagraph](get-root-subnet-metagraph.md) - View root subnet topology
- [Get Root Subnet History](get-root-subnet-history.md) - Access historical root subnet data

### Neuron Management
- [Get Neuron Registrations](get-neuron-registrations.md) - Query neuron registration events
- [Get Neuron Deregistrations](get-neuron-deregistrations.md) - View neuron deregistration events
- [Get Miner Weights](get-miner-weights.md) - Retrieve miner weight distributions

### Subnet Analysis
- [Get Subnet Coldkey Distribution](get-subnet-coldkey-distribution.md) - View coldkey distribution across subnets
- [Get Subnet Axon IP](get-subnet-axon-ip.md) - Query subnet axon IP addresses
- [Get Subnet Miner Incentive](get-subnet-miner-incentive.md) - Access miner incentive data

## Common Parameters

All Metagraph API endpoints support these common parameters:

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
- Network weights are normalized to [0,1] range
- IP addresses follow standard IPv4/IPv6 format
- Historical data queries support pagination
- Block numbers are provided as integers
- Incentive values are provided in both rao and tao units 