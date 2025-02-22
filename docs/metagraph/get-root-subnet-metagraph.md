# Get Root Subnet Metagraph

Returns detailed information about neurons (validators) in the root subnet metagraph, including their stake, consensus, and subnet weights.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of neurons in the root subnet with their current state and subnet weights.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/metagraph/root/latest/v1', headers=headers)
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
| stake | Total stake amount (as string) |
| consensus | Consensus score |
| senator | Whether the neuron is a senator |
| rank | Neuron's rank in the network |
| pruning_score | Pruning score for the neuron |
| subnet_weights | Object containing weights for each subnet (0-52) |

## Notes
- All numerical scores and amounts are returned as strings to maintain precision
- The subnet_weights object contains the neuron's weight distribution across all subnets
- Subnet weights are indexed from 0 to 52, representing different network subnets
- The senator field indicates whether the neuron has senator status in the root subnet
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- The pruning_score indicates the neuron's effectiveness in network pruning
- The response includes both SS58 and hexadecimal formats for hotkey and coldkey addresses
- Root subnet neurons play a crucial role in subnet governance and weight assignment 