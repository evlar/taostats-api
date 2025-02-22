# Get Subnet Miner Incentive Distribution

Returns information about the distribution of incentive scores across neurons in a subnet, showing the current incentive values and immunity period status.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | true | Network/Subnet ID | - |

## Response
The endpoint returns a paginated list of neurons with their incentive scores and immunity period status.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

params = {
    'netuid': 1  # Required: specify the subnet ID
}

response = requests.get('https://api.taostats.io/api/subnet/distribution/incentive/v1', headers=headers, params=params)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| block_number | Block number when the incentive data was recorded |
| incentive | Incentive score value (as string) |
| is_immunity_period | Whether the neuron is in immunity period |

## Notes
- All incentive scores are returned as strings to maintain numerical precision
- The response shows the distribution of incentive scores across neurons in the subnet
- Incentive scores typically range from 0 to 1, representing the neuron's performance and reward potential
- The is_immunity_period field indicates whether a neuron is currently protected from incentive penalties
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- This endpoint is useful for:
  - Analyzing reward distribution patterns
  - Understanding neuron performance metrics
  - Monitoring network participation quality
  - Identifying high-performing neurons
- The data can help identify:
  - Performance distribution across the network
  - Impact of immunity periods on incentive scores
  - Overall subnet health and participation quality 