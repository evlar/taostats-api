# Taostats API Documentation

This repository contains the official documentation for the Taostats API, which provides comprehensive access to data from the Bittensor ecosystem - the same data that powers [taostats.io](https://taostats.io).

## Overview

The Taostats API offers a wide range of endpoints that allow developers to:
- Track real-time and historical price data for TAO
- Monitor coldkey/wallet balances and transactions
- Access network and chain statistics
- View delegation and staking information
- Analyze metagraph data
- Get validator and subnet metrics
- Access EVM-related functionality
- Utilize Trading View compatible endpoints
- Track accounting and financial metrics
- Access live streaming data
- Connect to hosted RPC nodes

## API Categories

### Core Features
- **Price API**: Real-time and historical price data for TAO
- **Coldkeys/Wallets API**: Account information, balances, and transaction history
- **Network/Chain API**: Blockchain and network statistics
- **Delegation/Staking API**: Validator and delegator information
- **Metagraph API**: Network topology and metrics
- **Submit API**: Transaction submission endpoints
- **Validation API**: Validator performance and metrics
- **EVM API**: Ethereum Virtual Machine integration
- **Trading View API**: Chart and widget compatible data
- **Accounting API**: Financial metrics and analysis
- **Live API**: Real-time data streaming
- **Hosted RPC**: Direct blockchain connectivity

### Beta Features
- **dTAO TESTNET**: Testnet-specific endpoints
- **dTao BETA**: Experimental features
- **Validator Emission**: Emission tracking by submission
- **Stake Balance**: Current and historical stake tracking

## Getting Started

1. **API Key**: Obtain your API key to access the endpoints
2. **Authentication**: Include your API key in the `Authorization` header
3. **Rate Limits**: Review the rate limiting documentation
4. **Examples**: Check out the [example repository](https://github.com/taostats/examples)

## Documentation Structure

Each API category has its own documentation section covering:
- Available endpoints
- Query parameters
- Response formats
- Example requests
- Field descriptions
- Usage notes

## Authentication

All endpoints require an API key for authentication. Include it in your requests:

```python
headers = {
    "accept": "application/json",
    "Authorization": "YOUR-API-KEY"
}
```

## Common Features

All endpoints share some common characteristics:
- JSON response format
- Pagination support where applicable
- Timestamp fields in ISO 8601 format
- Numerical values as strings to preserve precision
- Consistent error handling

## Response Format

Standard response structure:
```json
{
  "pagination": {
    "current_page": integer,
    "per_page": integer,
    "total_items": integer,
    "total_pages": integer,
    "next_page": integer|null,
    "prev_page": integer|null
  },
  "data": [
    // Endpoint-specific data
  ]
}
```

## Contributing

This documentation is maintained by the Taostats team. For issues, suggestions, or corrections:
1. Open an issue describing the problem or suggestion
2. Submit a pull request with proposed changes
3. Follow the documentation style guide

## Support

- [Taostats Website](https://taostats.io)
- [Example Repository](https://github.com/taostats/examples)
- [API Status](https://api.taostats.io/status)

## License

[License information to be added] 