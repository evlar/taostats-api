# Get Subnet Coldkey Distribution

Returns information about the distribution of neurons across coldkey addresses in a subnet, showing how many neurons each coldkey controls.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | true | Network/Subnet ID | - |

## Response
The endpoint returns a paginated list of coldkey addresses and their associated neuron counts in the specified subnet.

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

response = requests.get('https://api.taostats.io/api/subnet/distribution/coldkey/v1', headers=headers, params=params)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| coldkey | Coldkey address in SS58 format |
| count | Number of neurons controlled by this coldkey in the subnet |

## Notes
- The response shows the distribution of neurons across different coldkey addresses
- The count field indicates how many neurons (validators/miners) are registered to each coldkey
- This endpoint is useful for:
  - Analyzing network decentralization
  - Identifying concentration of control
  - Monitoring subnet participation patterns
  - Understanding validator/miner ownership distribution
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- The data can help identify:
  - Large stakeholders in the network
  - Distribution of network control
  - Potential centralization concerns
- Higher counts indicate coldkeys that control multiple neurons in the subnet 