# Get Price OHLC

Returns Open, High, Low, Close price data for the specified asset with pagination support.

```
GET https://api.taostats.io/api/price/ohlc/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| asset | string | Yes | The asset to get OHLC data for | tao |
| period | string | Yes | Time period for OHLC data (e.g., '1d' for daily) | 1d |
| page | integer | No | Page number for pagination | 1 |
| limit | integer | No | Number of records per page | 50 |
| timestamp_start | integer | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| timestamp_end | integer | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |

## Response

A successful response returns HTTP 200 status code with the following JSON structure:

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
    {
      "period": string,
      "timestamp": string (ISO 8601),
      "asset": string,
      "volume_24h": string,
      "open": string,
      "high": string,
      "low": string,
      "close": string
    }
  ]
}
```

## Example Request

```python
import requests

url = "https://api.taostats.io/api/price/ohlc/v1?asset=tao&period=1d&page=1&limit=50"
headers = {
    "accept": "application/json",
    "Authorization": "YOUR-API-KEY"
}

response = requests.get(url, headers=headers)
print(response.text)
```

## Example Response

```json
{
  "pagination": {
    "current_page": 1,
    "per_page": 50,
    "total_items": 851,
    "total_pages": 18,
    "next_page": 2,
    "prev_page": null
  },
  "data": [
    {
      "period": "1d",
      "timestamp": "2024-10-23T00:00:00Z",
      "asset": "TAO",
      "volume_24h": "109342484.1156",
      "open": "542.8411",
      "high": "547.0797",
      "low": "524.2589",
      "close": "525.2484"
    }
  ]
}
```

## Response Fields

| Field | Description |
|-------|-------------|
| period | The time period for the OHLC data (e.g., "1d" for daily) |
| timestamp | The start time of the period in ISO 8601 format |
| asset | The asset symbol |
| volume_24h | 24-hour trading volume |
| open | Opening price for the period |
| high | Highest price during the period |
| low | Lowest price during the period |
| close | Closing price for the period |

*Documentation for this endpoint is under development. Please check back later for complete documentation.* 