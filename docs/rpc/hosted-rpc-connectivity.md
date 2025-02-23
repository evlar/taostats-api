# Hosted RPC Connectivity

Taostats provides hosted RPC nodes for connecting to the Bittensor network. These endpoints allow direct blockchain interaction through RPC calls.

## Available Endpoints

### RPC Light Node

```
wss://api.taostats.io/api/v1/rpc/ws/finney_lite?authorization=API_KEY
```

The light node endpoint provides a WebSocket connection optimized for basic blockchain interactions and queries.

### RPC Archive

```
wss://api.taostats.io/api/v1/rpc/ws/finney_archive?authorization=API_KEY
```

The archive node endpoint provides a WebSocket connection with full historical data access.

## Authentication

Both endpoints require authentication using your Taostats API key as a query parameter:
- Add `?authorization=YOUR-API-KEY` to the WebSocket URL
- Replace `YOUR-API-KEY` with your actual Taostats API key

## Notes

- Both endpoints use secure WebSocket connections (wss://)
- The light node is optimized for:
  - Current state queries
  - Recent block data
  - Transaction submission
  - Event monitoring
- The archive node provides:
  - Full historical data access
  - Historical state queries
  - Complete block history
  - Historical event data
- Choose the appropriate endpoint based on your needs:
  - Use light node for general purpose applications
  - Use archive node when historical data is required
- Connection limits and rate limiting may apply
- WebSocket connections should be maintained and reconnected as needed 