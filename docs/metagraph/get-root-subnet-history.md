# Get Root Subnet History

Returns historical information about neurons (validators) in the root subnet metagraph over a specified time period or block range.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | false | Filter by hotkey address (SS58 format) | - |
| block_start | int32 | false | Starting block number | - |
| block_end | int32 | false | Ending block number | - |
| timestamp_start | int64 | false | Start timestamp (Unix timestamp in seconds) | - |
| timestamp_end | int64 | false | End timestamp (Unix timestamp in seconds) | - |
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of historical root subnet neuron states with their subnet weights over time.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/metagraph/root/history/v1', headers=headers)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| hotkey.ss58 | Hotkey address in SS58 format |
| hotkey.hex | Hotkey address in hexadecimal format |
| coldkey.ss58 | Coldkey address in SS58 format |
| coldkey.hex | Coldkey address in hexadecimal format |
| uid | Neuron ID in the root subnet |
| block_number | Block number when the data was recorded |
| timestamp | ISO 8601 timestamp of the block |
| stake | Total stake amount at this point in time (as string) |
| consensus | Historical consensus score |
| senator | Whether the neuron was a senator at this point |
| rank | Neuron's historical rank in the network |
| pruning_score | Historical pruning score |
| subnet_weights | Object containing historical weights for each subnet (0-56) |

## Notes
- All numerical scores and amounts are returned as strings to maintain precision
- You can filter by either block range or timestamp range, but not both simultaneously
- The subnet_weights object shows how the neuron's weight distribution across subnets changed over time
- Subnet weights are indexed from 0 to 56, representing different network subnets
- The senator field tracks changes in senator status over time
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- The pruning_score shows historical effectiveness in network pruning
- Historical records help track changes in neuron parameters and subnet weight assignments over time
- The response includes both SS58 and hexadecimal formats for hotkey and coldkey addresses 