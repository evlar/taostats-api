# Get Stats History

Get historical network statistics and metrics for the Bittensor network at specific time intervals.

```
GET https://api.taostats.io/api/stats/history/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| block_number | integer | No | Filter by specific block number | - |
| block_start | integer | No | Start of block range | - |
| block_end | integer | No | End of block range | - |
| timestamp_start | integer | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| timestamp_end | integer | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| frequency | string | No | Frequency of intervals (e.g., 'by_day') | by_day |
| page | integer | No | Page number for pagination | 1 |
| limit | integer | No | Number of records per page | 50 |
| order | string | No | Sort order for results | - |

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

url = "https://api.taostats.io/api/stats/history/v1?frequency=by_day&page=1&limit=50"
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

- Data is ordered by timestamp in descending order by default
- All balance values (issued, staked, subnet_registration_cost) are returned as strings to preserve precision
- Balance values are denominated in Rao (1 TAO = 1,000,000,000 Rao)
- Active accounts/holders are determined by recent transaction activity
- The `frequency` parameter determines the interval between data points:
  - by_day: Daily statistics (default)
  - Other intervals may be added in the future
- Historical data is available from the network's inception 