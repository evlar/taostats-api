# Taostats API Documentation

This repository contains documentation for the Taostats API in a format that's easy for AI tools to understand and use. The API provides data from the Bittensor network, which powers [taostats.io](https://taostats.io).

## What's Here

Documentation for these main API categories:

- [Price data](docs/price/index.md) (latest, historical, OHLC)
- [Coldkeys and wallets](docs/coldkeys-wallets/index.md) (accounts, balances, history)
- [Network and chain stats](docs/network-chain/index.md)
- [Delegation and staking](docs/delegation-staking/index.md)
- [Metagraph](docs/metagraph/index.md)
- [Validation](docs/validation/index.md)
- [EVM](docs/evm/index.md)
- [Trading View](docs/trading-view/index.md)
- [Accounting](docs/accounting/index.md)
- [Live data](docs/live/index.md)
- [Hosted RPC](docs/hosted-rpc/index.md)

See the complete [API Overview](docs/index.md) for more details.

## How It's Organized

Each API endpoint has its own markdown file with:
1. What the endpoint does
2. How to call it
3. What parameters you can use
4. What the response looks like
5. Real examples

## File Structure

```
docs/
├── index.md          # Overview
├── api-key.md        # How to authenticate
├── price/            # Price endpoints
├── coldkeys-wallets/ # Wallet endpoints
├── network-chain/    # Network endpoints
[etc...]
```

## Common Patterns

All responses include:
- Pagination (if there are multiple items)
- Consistent error formats
- Timestamps in ISO 8601
- Numbers as strings (for precision)
- Standard JSON structure

## Links

- [Taostats Website](https://taostats.io)
- [Example Code](https://github.com/taostats/examples)
- [API Status](https://api.taostats.io/status)
- [Authentication Guide](docs/api-key.md) 