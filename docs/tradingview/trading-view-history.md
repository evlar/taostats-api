# Trading View History

Retrieves historical price and volume data in Trading View's Universal Data Feed (UDF) format, suitable for displaying interactive charts.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| symbol | string | Yes | SUB- followed by subnet:uid (e.g., "SUB-19") | None |
| resolution | string | Yes | Granularity of data (possible values: 1,5,15,60 for minutes; 1D, 2D, 3D for days) | None |
| from | int32 | Yes | Start time in Unix timestamp | None |
| to | int32 | Yes | End time in Unix timestamp | None |

## Response

The response follows Trading View's UDF protocol format, containing OHLCV (Open, High, Low, Close, Volume) data.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/dtao/tradingview/udf/history"
headers = {
    "accept": "application/json",
    "Authorization": "YOUR-API-KEY"
}

params = {
    "symbol": "SUB-19",
    "resolution": "60",
    "from": "1709251200",
    "to": "1709337600"
}

response = requests.get(url, headers=headers, params=params)
print(response.text)
```

## Response Fields

| Field | Description |
|-------|-------------|
| s | Status of the response ("ok" or "error") |
| t[] | Array of timestamps for each candle |
| o[] | Array of opening prices |
| h[] | Array of high prices |
| l[] | Array of low prices |
| c[] | Array of closing prices |
| v[] | Array of volume data |

## Notes

- The symbol format must be "SUB-" followed by the subnet:uid
- Resolution options:
  - Minutes: 1, 5, 15, 60
  - Days: 1D, 2D, 3D
- Timestamps should be provided in Unix format (seconds since epoch)
- This endpoint is specifically designed for Trading View chart integration
- Data is returned in chronological order
- All price values are in TAO units
- Empty periods will have null values for OHLCV data
- The response format follows Trading View's UDF (Universal Data Feed) specification 