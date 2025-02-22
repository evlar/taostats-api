# Get Subnet Axon IP Distribution

Returns information about the distribution of neurons across IP addresses in a subnet, showing how many neurons are operating from each IP address.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | true | Network/Subnet ID | - |

## Response
The endpoint returns a paginated list of IP addresses and their associated neuron counts in the specified subnet.

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

response = requests.get('https://api.taostats.io/api/subnet/distribution/ip/v1', headers=headers, params=params)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| ip | IP address of the axon endpoint |
| count | Number of neurons operating from this IP address |

## Notes
- The response shows the distribution of neurons across different IP addresses
- The count field indicates how many neurons are running from each IP address
- This endpoint is useful for:
  - Analyzing network infrastructure distribution
  - Identifying potential centralization of network resources
  - Monitoring geographical distribution of nodes
  - Detecting potential multi-neuron hosting setups
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- The data can help identify:
  - Cloud provider usage patterns
  - Network infrastructure concentration
  - Geographical node distribution
  - Potential security or reliability concerns
- Higher counts indicate IP addresses that host multiple neurons, which could represent:
  - Cloud-hosted node clusters
  - Data center deployments
  - Multi-validator setups 