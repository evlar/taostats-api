# Get Stats Latest

Get the latest network statistics and metrics for the Bittensor network.

```
GET https://api.taostats.io/api/stats/latest/v1
```

## Query Parameters

No query parameters are required for this endpoint.

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
      "block_number": integer,
      "timestamp": string (ISO 8601),
      "issued": string,
      "staked": string,
      "accounts": integer,
      "active_accounts": integer,
      "balance_holders": integer,
      "active_balance_holders": integer,
      "extrinsics": integer,
      "transfers": integer,
      "subnets": integer,
      "subnet_registration_cost": string
    }
  ]
}
```

## Example Request

```python
import requests

url = "https://api.taostats.io/api/stats/latest/v1"
headers = {
    "accept": "application/json",
    "Authorization": "YOUR-API-KEY"
}

response = requests.get(url, headers=headers)
print(response.text)
```

## Response Fields

| Field | Description |
|-------|-------------|
| block_number | The block number these statistics were captured at |
| timestamp | When these statistics were captured (ISO 8601 format) |
| issued | Total amount of TAO tokens issued (in Rao, 1 TAO = 1e9 Rao) |
| staked | Total amount of TAO tokens staked (in Rao) |
| accounts | Total number of accounts ever created |
| active_accounts | Number of accounts that have had activity |
| balance_holders | Total number of accounts holding TAO |
| active_balance_holders | Number of accounts holding TAO that have had activity |
| extrinsics | Total number of extrinsics processed |
| transfers | Total number of token transfers |
| subnets | Number of active subnets |
| subnet_registration_cost | Current cost to register a subnet (in Rao) |

## Notes

- This endpoint always returns a single record with the latest statistics
- All balance values (issued, staked, subnet_registration_cost) are returned as strings to preserve precision
- Balance values are denominated in Rao (1 TAO = 1,000,000,000 Rao)
- Active accounts/holders are determined by recent transaction activity
- The statistics are updated with each new block 