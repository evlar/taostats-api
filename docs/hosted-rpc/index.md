# Hosted RPC API

The Hosted RPC API provides direct access to Bittensor network nodes through a reliable, high-performance RPC endpoint.

## Connection Details

### Mainnet (Finney)
```
wss://api.taostats.io/ws/finney
https://api.taostats.io/rpc/finney
```

### Testnet
```
wss://api.taostats.io/ws/test
https://api.taostats.io/rpc/test
```

## Authentication

All RPC connections require authentication using your Taostats API key:

```
Authorization: YOUR-API-KEY
```

## Usage Limits

| Plan | Connections | Requests/min | WebSocket Messages/min |
|------|-------------|--------------|----------------------|
| Free | 2 | 1000 | 2000 |
| Pro | 5 | 5000 | 10000 |
| Enterprise | Custom | Custom | Custom |

## Supported Methods

The RPC endpoint supports all standard Substrate RPC methods, including:

- Chain state queries
- Block retrieval
- Transaction submission
- Event subscription
- Runtime calls
- Network state queries

## WebSocket Subscriptions

Example subscription:
```javascript
{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "chain_subscribeNewHeads",
    "params": []
}
```

## Notes

- Both HTTP and WebSocket connections are supported
- All responses follow standard Substrate RPC format
- Connection pooling is recommended for high-volume usage
- Automatic failover is provided for high availability
- SSL/TLS is required for all connections
- Rate limits are applied per API key
- Enterprise support is available for custom requirements 