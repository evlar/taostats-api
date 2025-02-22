# Get Subnet History

Returns historical information about subnet configurations and metrics over time, including registration settings, difficulty adjustments, and recycling statistics.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | true | Network/Subnet ID | - |
| frequency | string | false | Data frequency/aggregation level | - |
| block_number | int32 | false | Filter by specific block number | - |
| block_start | int32 | false | Starting block number | - |
| block_end | int32 | false | Ending block number | - |
| timestamp_start | int64 | false | Start timestamp (Unix timestamp in seconds) | - |
| timestamp_end | int64 | false | End timestamp (Unix timestamp in seconds) | - |
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of historical subnet states with detailed configuration and performance metrics.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

params = {
    'netuid': 1,  # Required: specify the subnet ID
    'limit': 50
}

response = requests.get('https://api.taostats.io/api/subnet/history/v1', headers=headers, params=params)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| activity_cutoff | Number of blocks after which a neuron is considered inactive |
| registration_allowed | Whether new registrations are currently allowed |
| target_regs_per_interval | Target number of registrations per interval |
| min_burn | Minimum burn amount required for registration (as string) |
| max_burn | Maximum burn amount allowed for registration (as string) |
| bonds_moving_avg | Moving average of bond amounts (as string) |
| max_regs_per_block | Maximum number of registrations allowed per block |
| serving_rate_limit | Rate limit for serving requests (as string) |
| max_validators | Maximum number of validators allowed in the subnet |
| adjustment_alpha | Alpha parameter for difficulty adjustment (as string) |
| difficulty | Current registration difficulty (as string) |
| last_adjustment_block | Block number of the last difficulty adjustment |
| blocks_since_last_step | Number of blocks since the last step |
| blocks_until_next_epoch | Number of blocks until the next epoch |
| blocks_until_next_adjustment | Number of blocks until the next difficulty adjustment |
| recycled_lifetime | Total amount recycled over subnet lifetime (as string) |
| recycled_24_hours | Amount recycled in the last 24 hours (as string) |
| recycled_since_registration | Amount recycled since last registration (as string) |

## Notes
- All numerical values are returned as strings to maintain precision
- The endpoint provides historical tracking of:
  - Registration parameters and restrictions
  - Difficulty adjustment metrics
  - Recycling statistics
  - Network configuration changes
- You can filter historical data by:
  - Block range or timestamp range
  - Specific block number
  - Data frequency/aggregation level
- The response includes detailed metrics about:
  - Network participation controls
  - Difficulty adjustment mechanisms
  - Resource recycling patterns
- Historical data is useful for:
  - Analyzing subnet growth patterns
  - Understanding difficulty adjustments
  - Tracking registration trends
  - Monitoring recycling activity
- Registration parameters show:
  - Current registration status
  - Burn amount requirements
  - Rate limiting controls
- Difficulty metrics indicate:
  - Current registration challenge
  - Adjustment schedules
  - Network growth control 