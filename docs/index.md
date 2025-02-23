# Welcome to the Taostats API Documentation

> **Important Note**: This documentation is a community-created resource designed to help developers use AI tools to better understand and work with the Taostats API. It is not officially affiliated with or endorsed by Taostats or taostats.io.

This documentation provides comprehensive coverage of the Taostats API - the same API that powers [taostats.io](https://taostats.io). The documentation is structured to be easily parsed and understood by AI tools while remaining human-readable.

## Documentation Structure

Each API endpoint is documented with:
1. Clear endpoint description
2. Complete parameter specifications
3. Response structure details
4. Working code examples
5. Comprehensive field descriptions
6. Additional notes and usage guidelines

## API Categories

### Core Features
- [Price](price/index.md) - Latest prices, historical data, and OHLC
- [Coldkeys/Wallets](coldkeys-wallets/index.md) - Account information, balances, and history
- [Network/Chain](network-chain/index.md) - Blockchain metrics and network status
- [Get API Status](get-api-status.md) - Service health and status
- [Delegation/Staking](delegation-staking/index.md) - Stake management and delegation events
- [Metagraph](metagraph/index.md) - Network topology and relationships
- [Submit](submit/index.md) - Data submission endpoints
- [Validation](validation/index.md) - Validator metrics and performance
- [EVM](evm/index.md) - Ethereum Virtual Machine integration
- [Trading View](trading-view/index.md) - Trading data and charts
- [Accounting](accounting/index.md) - Financial reporting and analysis
- [Live](live/index.md) - Real-time network information
- [Hosted RPC Connectivity](hosted-rpc/index.md) - Remote procedure call access

### Beta Features
- [dTAO API](dtao/index.md)
  - [Get Stake Balance](dtao/get-stake-balance.md)
  - [Get Historical Stake Balance](dtao/get-historical-stake-balance.md)
  - [Get Validator Emission by Subnet](dtao/get-validator-emission.md)

## Response Standards

All API responses follow these conventions:
- Pagination for multi-item responses
- Consistent error formatting
- ISO 8601 timestamps
- String-formatted numbers for precision
- Standardized JSON structure

## File Organization
```
docs/
├── index.md          # Complete API overview
├── api-key.md        # Authentication guide
├── category/         # Each API category has its own directory
│   ├── index.md     # Category overview
│   └── endpoint.md  # Individual endpoint documentation
```

## Version
Current Version: v2.0

## Useful Links
- [Taostats Website](https://taostats.io)
- [API Status](https://api.taostats.io/status)
- [Authentication Guide](api-key.md)

*Last updated: February 23, 2025* 