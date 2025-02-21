# Taostats API Documentation

This repository contains a structured, machine-readable documentation for the Taostats API, specifically formatted to be easily parsed and understood by AI language models and development tools. The documentation provides comprehensive access to the Bittensor ecosystem data that powers [taostats.io](https://taostats.io).

## Purpose

This documentation is designed to:
- Provide consistent, structured information that AI tools can easily process
- Enable AI-powered development environments to offer accurate code completion
- Help AI assistants generate correct API calls and handle responses
- Maintain a standardized format across all endpoint documentation

## Documentation Structure

Each API endpoint is documented in a consistent format:

```markdown
# Endpoint Name

Brief description of the endpoint's purpose

```
GET/POST https://api.taostats.io/api/[endpoint-path]
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| param1 | string | Yes/No | Description | default |

## Response

JSON structure with types specified:

```json
{
  "field": type (format),
  "nested": {
    "field": type
  }
}
```

## Example Request/Response

Complete working examples with actual data
```

### Core API Categories

Each category follows the same documentation pattern:

1. **Price API** (`/docs/price/`)
   - Latest price
   - Historical data
   - OHLC data

2. **Coldkeys/Wallets API** (`/docs/coldkeys-wallets/`)
   - Account information
   - Transaction history
   - Balance tracking

[Additional categories listed in directory structure]

## Machine-Readable Features

The documentation emphasizes:
- Consistent JSON schemas
- Explicit type definitions
- Standardized parameter tables
- Clear response structures
- Real-world examples
- Structured error formats

## Directory Structure

```
docs/
├── index.md                 # API Overview
├── api-key.md              # Authentication
├── price/                  # Price endpoints
│   ├── index.md
│   ├── latest.md
│   ├── history.md
│   └── ohlc.md
├── coldkeys-wallets/       # Wallet endpoints
│   ├── index.md
│   ├── account.md
│   └── history.md
[etc...]
```

## Common Response Patterns

All endpoints follow consistent patterns:

1. **Pagination Structure**
```json
{
  "pagination": {
    "current_page": integer,
    "per_page": integer,
    "total_items": integer,
    "total_pages": integer,
    "next_page": integer|null,
    "prev_page": integer|null
  }
}
```

2. **Error Format**
```json
{
  "error": {
    "code": string,
    "message": string,
    "details": object|null
  }
}
```

## Type Conventions

- Timestamps: ISO 8601 format
- Numerical values: Strings for precision
- Addresses: SS58 and hex formats
- Network names: Lowercase strings
- Block numbers: Integers
- Balances: Strings (to preserve precision)

## Using with AI Tools

This documentation is optimized for:
- Code completion engines
- AI pair programming assistants
- Documentation generators
- API client generators
- Test case generators

## Contributing

When contributing documentation:
1. Follow the established format patterns
2. Include explicit type information
3. Provide real-world examples
4. Maintain consistent structure
5. Include machine-readable metadata

## Support

- [Taostats Website](https://taostats.io)
- [Example Repository](https://github.com/taostats/examples)
- [API Status](https://api.taostats.io/status)

## License

[License information to be added] 