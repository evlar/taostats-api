# Get Subnet Emission

Returns information about subnet token emissions and rewards over time, including pool balances and reward distributions.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | false | Filter by Network/Subnet ID | - |
| block_number | int32 | false | Filter by specific block number | - |
| block_start | int32 | false | Starting block number | - |
| block_end | int32 | false | Ending block number | - |
| timestamp_start | int64 | false | Start timestamp (Unix timestamp in seconds since 1970-01-01) | - |
| timestamp_end | int64 | false | End timestamp (Unix timestamp in seconds since 1970-01-01) | - |
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order for results | 'block_number_desc' |

## Response
The endpoint returns a paginated list of subnet emission records with pool balances and reward metrics.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

params = {
    'netuid': 1,
    'block_start': 4000000,
    'block_end': 4100000,
    'page': 1,
    'limit': 50
}

response = requests.get('https://api.taostats.io/api/dtao/subnet_emission/v1', headers=headers, params=params)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| netuid | Network/Subnet ID |
| block_number | Block number when the emission data was recorded |
| timestamp | ISO 8601 timestamp of the block |
| name | Name of the subnet token |
| symbol | Symbol of the subnet token |
| tao_in_pool | Amount of TAO tokens in the pool |
| alpha_in_pool | Amount of Alpha tokens in the pool |
| alpha_rewards | Reward amount in Alpha tokens |

## Notes
- All numerical values are returned as strings to maintain precision
- You can filter by either block range or timestamp range, but not both simultaneously
- The endpoint provides insights into:
  - Pool balance changes over time
  - Alpha token reward distributions
  - TAO/Alpha token ratios
- Pool metrics help understand:
  - Liquidity dynamics
  - Reward distribution patterns
  - Token supply changes
- The data is useful for:
  - Tracking pool balance changes
  - Monitoring reward distributions
  - Analyzing liquidity trends
  - Understanding token economics
- When using timestamp filters:
  - Timestamps should be in Unix format (seconds since epoch)
  - Both start and end timestamps are inclusive
  - The maximum time range may be limited to prevent excessive data retrieval
- Records are typically captured at regular intervals
- Each record provides a snapshot of:
  - Current pool balances
  - Reward distributions
  - Token supply metrics 