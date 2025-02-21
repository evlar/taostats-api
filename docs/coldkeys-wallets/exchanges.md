# Get Exchanges

Get exchange-related information and transactions for coldkeys.

```
GET https://api.taostats.io/api/coldkeys-wallets/exchanges/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| ss58_address | string | Yes | The SS58 formatted address of the coldkey | - |
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
      // Exchange data fields will be documented once example response is provided
    }
  ]
}
```

## Example Request

```python
import requests

url = "https://api.taostats.io/api/coldkeys-wallets/exchanges/v1"
params = {
    "ss58_address": "5FYtQMwuW7qvGXWKw3skKuRCEPXNi6k8hqgTusk7mgZAGxqk",
    "page": 1,
    "limit": 50
}
headers = {
    "accept": "application/json",
    "Authorization": "YOUR-API-KEY"
}

response = requests.get(url, params=params, headers=headers)
print(response.text)
```

## Response Fields

*Complete field descriptions will be added once example response is provided* 