# Get Subnets

Returns detailed information about all subnets in the network, including their configuration parameters, registration settings, and recycling statistics.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | false | Filter by Network/Subnet ID | - |
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of subnets with their current configuration and status.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/subnet/latest/v1', headers=headers)
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
- The endpoint provides comprehensive information about subnet configuration and status
- Registration parameters help understand the current state of subnet growth:
  - registration_allowed indicates if new neurons can join
  - target_regs_per_interval and max_regs_per_block control growth rate
  - min_burn and max_burn define registration cost bounds
- Difficulty adjustment parameters show how the network adapts:
  - adjustment_alpha controls the rate of difficulty changes
  - blocks_until_next_adjustment shows when the next change will occur
- Recycling statistics provide insights into subnet activity:
  - recycled_lifetime shows total historical recycling
  - recycled_24_hours indicates recent activity
  - recycled_since_registration shows activity since last registration
- The activity_cutoff parameter defines when neurons are considered inactive
- The max_validators field limits the size of the subnet 