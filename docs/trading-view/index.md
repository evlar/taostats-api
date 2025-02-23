# Trading View API

The Trading View API provides data compatible with TradingView charts and widgets, allowing integration of Bittensor price and trading data into TradingView-based applications.

## Available Endpoints

- [Get Trading View History](history.md) - Retrieve historical price and trading data in TradingView format

## Common Parameters

All Trading View API endpoints support these common parameters:

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| symbol | string | No | Trading pair symbol (e.g., "TAO/USD") | "TAO/USD" |
| interval | string | No | Time interval for data points | "1d" |
| from | int64 | No | Start timestamp (Unix) | None |
| to | int64 | No | End timestamp (Unix) | None |

## Response Format

All responses follow the TradingView UDF (Universal Data Feed) format:

```json
{
    "s": "ok",
    "t": [1708732800],  // Timestamps
    "o": [10.5],        // Open prices
    "h": [11.2],        // High prices
    "l": [10.1],        // Low prices
    "c": [10.8],        // Close prices
    "v": [1500000]      // Volumes
}
```

## Notes

- Timestamps are provided in Unix format (seconds since epoch)
- Price values use 8 decimal precision
- Volume values are provided in base currency units
- Supported intervals: 1m, 5m, 15m, 30m, 1h, 2h, 4h, 1d
- Historical data is available from network genesis
- Data is compatible with TradingView Technical Analysis 