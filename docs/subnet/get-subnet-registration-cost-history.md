# Get Subnet Registration Cost History

Returns historical information about subnet registration costs over time, allowing tracking of cost changes across different blocks or time periods.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| block_number | int32 | false | Filter by specific block number | - |
| block_start | int32 | false | Starting block number | - |
| block_end | int32 | false | Ending block number | - |
| timestamp_start | int64 | false | Start timestamp (Unix timestamp in seconds since 1970-01-01) | - |
| timestamp_end | int64 | false | End timestamp (Unix timestamp in seconds since 1970-01-01) | - |
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of historical registration costs with associated block information.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/subnet/registration_cost/history/v1', headers=headers)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| block_number | Block number when the registration cost was recorded |
| timestamp | ISO 8601 timestamp of the block |
| registration_cost | Registration cost at this point in time (as string) |

## Notes
- All registration costs are returned as strings to maintain numerical precision
- The costs are denominated in TAO tokens (in billionths)
- You can filter historical data by:
  - Block range or timestamp range
  - Specific block number
- The endpoint is useful for:
  - Analyzing registration cost trends
  - Understanding cost fluctuations
  - Planning optimal registration timing
  - Historical cost analysis
- Registration costs typically change based on:
  - Network demand
  - Subnet policies
  - Difficulty adjustments
  - Market conditions
- The response is paginated with standard fields:
  - current_page
  - per_page
  - total_items
  - total_pages
  - next_page
  - prev_page
- Historical data helps track:
  - Cost volatility
  - Network growth patterns
  - Registration demand
  - Policy impacts on costs 