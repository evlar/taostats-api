# Get Price History

Returns historical price data for the specified asset with pagination support.

```
GET https://api.taostats.io/api/price/history/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| asset | string | Yes | The asset to get price history for | TAO |
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

url = "https://api.taostats.io/api/price/history/v1?asset=TAO&page=1&limit=50"
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
    "per_page": 5,
    "total_items": 18115,
    "total_pages": 3623,
    "next_page": 2,
    "prev_page": null
  },
  "data": [
    {
      "created_at": "2024-10-23T15:15:05Z",
      "updated_at": "2024-10-23T15:15:05Z",
      "name": "Bittensor",
      "symbol": "TAO",
      "slug": "bittensor",
      "circulating_supply": "7380936",
      "max_supply": "21000000",
      "total_supply": "7380936",
      "last_updated": "2024-10-23T15:13:00Z",
      "price": "525.248478165591",
      "volume_24h": "109342484.115668",
      "market_cap": "3876825401.43762",
      "percent_change_1h": "-0.81742604",
      "percent_change_24h": "-5.02212301",
      "percent_change_7d": "-9.49316808",
      "percent_change_30d": "-2.39858357",
      "percent_change_60d": "54.42214736",
      "percent_change_90d": "61.70461003",
      "market_cap_dominance": "0.1696",
      "fully_diluted_market_cap": "11030218041.48"
    }
  ]
} 