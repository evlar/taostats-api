# Get Latest Price

Returns the latest price and market data for the specified asset.

```
GET https://api.taostats.io/api/price/latest/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| asset | string | Yes | The asset to get price for | tao |

## Response

A successful response returns HTTP 200 status code with the following JSON structure:

```json
{
  "pagination": {
    "current_page": integer,
    "per_page": integer,
    "total_items": integer,
    "total_pages": integer,
    "next_page": string|null,
    "prev_page": string|null
  },
  "data": [
    {
      "created_at": string (ISO 8601),
      "updated_at": string (ISO 8601),
      "name": string,
      "symbol": string,
      "slug": string,
      "circulating_supply": string,
      "max_supply": string,
      "total_supply": string,
      "last_updated": string (ISO 8601),
      "price": string,
      "volume_24h": string,
      "market_cap": string,
      "percent_change_1h": string,
      "percent_change_24h": string,
      "percent_change_7d": string,
      "percent_change_30d": string,
      "percent_change_60d": string,
      "percent_change_90d": string,
      "market_cap_dominance": string,
      "fully_diluted_market_cap": string
    }
  ]
}
```

## Example Request

```python
import requests

url = "https://api.taostats.io/api/price/latest/v1?asset=tao"
headers = {
    "accept": "application/json",
    "Authorization": "YOUR-API-KEY"
}

response = requests.get(url, headers=headers)
print(response.text)
``` 