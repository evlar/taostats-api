# Taostats API Documentation

This repository contains the complete documentation for the Taostats API, formatted for optimal use with AI tools. The API provides comprehensive data from the Bittensor network, which powers [taostats.io](https://taostats.io).

## Documentation Coverage

This documentation covers all available API endpoints across these categories:

- [Price data](docs/price/index.md) - Latest prices, historical data, and OHLC
- [Coldkeys and wallets](docs/coldkeys-wallets/index.md) - Account information, balances, and history
- [Network and chain stats](docs/network-chain/index.md) - Blockchain metrics and network status
- [Delegation and staking](docs/delegation-staking/index.md) - Stake management and delegation events
- [Metagraph](docs/metagraph/index.md) - Network topology and relationships
- [Validation](docs/validation/index.md) - Validator metrics and performance
- [EVM](docs/evm/index.md) - Ethereum Virtual Machine integration
- [Trading View](docs/trading-view/index.md) - Trading data and charts
- [Accounting](docs/accounting/index.md) - Financial reporting and analysis
- [Live data](docs/live/index.md) - Real-time network information
- [Hosted RPC](docs/hosted-rpc/index.md) - Remote procedure call access
- [dTAO Beta](docs/dtao/index.md) - Beta features for dTAO functionality

See the [API Overview](docs/index.md) for a complete endpoint listing.

## Documentation Structure

Each API endpoint is documented in its own markdown file with:
1. Clear endpoint description
2. Complete parameter specifications
3. Response structure details
4. Working code examples
5. Comprehensive field descriptions
6. Additional notes and usage guidelines

## File Organization

```
docs/
├── index.md          # Complete API overview
├── api-key.md        # Authentication guide
├── category/         # Each API category has its own directory
│   ├── index.md     # Category overview
│   └── endpoint.md  # Individual endpoint documentation
```

## Response Standards

All API responses follow these conventions:
- Pagination for multi-item responses
- Consistent error formatting
- ISO 8601 timestamps
- String-formatted numbers for precision
- Standardized JSON structure

## Beta Features

The dTAO API section includes beta endpoints that:
- Are currently running on testnet
- May be subject to changes
- Use standard API authentication
- Should be used with awareness of their beta status

## Contributing

While this documentation is complete, we welcome contributions to:
- Fix any inaccuracies
- Update outdated information
- Add missing details
- Improve clarity and examples

To contribute, simply:
1. Fork the repository
2. Make your changes
3. Submit a pull request with a clear description

## Useful Links

- [Taostats Website](https://taostats.io)
- [Example Code](https://github.com/taostats/examples)
- [API Status](https://api.taostats.io/status)
- [Authentication Guide](docs/api-key.md) 