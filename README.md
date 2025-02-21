# Taostats API Documentation

This repository contains documentation for the Taostats API in a format that's easy for AI tools to understand and use. The API provides data from the Bittensor network, which powers [taostats.io](https://taostats.io).

## What's Here

Documentation for these main API categories:

- Price data (latest, historical, OHLC)
- Coldkeys and wallets (accounts, balances, history)
- Network and chain stats
- Delegation and staking info
- Metagraph data
- Validator info
- EVM functionality
- Trading View data
- Accounting metrics
- Live data streams
- RPC connections

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