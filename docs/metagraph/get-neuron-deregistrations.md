# Get Neuron Deregistrations

Returns information about neuron deregistrations across different subnets, including final incentive scores and emission amounts.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | false | Filter by Network/Subnet ID | - |
| uid | int32 | false | Filter by Neuron ID | - |
| hotkey | string | false | Filter by hotkey address (SS58 format) | - |
| block_number | int32 | false | Filter by specific block number | - |
| block_start | int32 | false | Starting block number | - |
| block_end | int32 | false | Ending block number | - |
| timestamp_start | int64 | false | Start timestamp (Unix timestamp in seconds) | - |
| timestamp_end | int64 | false | End timestamp (Unix timestamp in seconds) | - |
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of neuron deregistration events with final metrics and emission data.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/subnet/neuron/deregistration/v1', headers=headers)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| block_number | Block number when the deregistration occurred |
| timestamp | ISO 8601 timestamp of the block |
| netuid | Network/Subnet ID where the neuron was deregistered |
| uid | Neuron ID in the subnet |
| hotkey.ss58 | Hotkey address in SS58 format |
| hotkey.hex | Hotkey address in hexadecimal format |
| coldkey.ss58 | Coldkey address in SS58 format |
| coldkey.hex | Coldkey address in hexadecimal format |
| incentive | Final incentive score at deregistration (as string) |
| emission | Final emission amount at deregistration (as string) |
| was_drained | Whether the neuron's stake was drained during deregistration |

## Notes
- All numerical scores and amounts are returned as strings to maintain precision
- You can filter deregistrations by either block range or timestamp range, but not both simultaneously
- The endpoint supports filtering by subnet ID (netuid) to track deregistrations in specific subnets
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- The was_drained field indicates whether the neuron's stake was removed during deregistration
- The response includes both SS58 and hexadecimal formats for hotkey and coldkey addresses
- Final incentive scores and emission amounts provide insights into the neuron's performance at deregistration
- Historical deregistration data can be useful for analyzing network churn and validator behavior 