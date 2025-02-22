# Get Metagraph

Returns detailed information about neurons (validators) in the network's metagraph, including their status, stake, and network parameters.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | true | Network/Subnet ID | - |
| search | string | false | Search across UID, hotkey, coldkey, axon_ip | - |
| uid | int32 | false | Neuron ID | - |
| active | boolean | false | Filter by active status | - |
| hotkey | string | false | Filter by hotkey address (SS58 or hex format) | - |
| coldkey | string | false | Filter by coldkey address (SS58 or hex format) | - |
| validator_permit | boolean | false | Filter by validator permit status | - |
| is_immunity_period | boolean | false | Filter by immunity period status | - |
| is_child_key | boolean | false | Filter by child key status | - |
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of neurons with their current state in the metagraph.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

params = {
    'netuid': 1,  # Replace with desired subnet ID
    'limit': 50
}

response = requests.get('https://api.taostats.io/api/metagraph/latest/v1', headers=headers, params=params)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| hotkey.ss58 | Hotkey address in SS58 format |
| hotkey.hex | Hotkey address in hexadecimal format |
| coldkey.ss58 | Coldkey address in SS58 format |
| coldkey.hex | Coldkey address in hexadecimal format |
| netuid | Network/Subnet ID |
| uid | Neuron ID in the subnet |
| block_number | Block number when the data was recorded |
| timestamp | ISO 8601 timestamp of the block |
| stake | Total stake amount (as string) |
| trust | Trust score |
| validator_trust | Validator trust score |
| consensus | Consensus score |
| incentive | Incentive score |
| dividends | Dividends score |
| emission | Emission amount |
| active | Whether the neuron is currently active |
| validator_permit | Whether the neuron has validator permissions |
| updated | Last update block number |
| daily_reward | Daily reward amount (as string) |
| registered_at_block | Block number when the neuron was registered |
| is_immunity_period | Whether the neuron is in immunity period |
| rank | Neuron's rank in the network |
| is_child_key | Whether this is a child key |
| axon | Object containing network connectivity information |
| axon.block | Block number when axon info was last updated |
| axon.ip | IP address of the node |
| axon.port | Port number |
| axon.protocol | Protocol version |
| axon.version | Axon version |
| axon.ipType | IP address type (4 for IPv4, 6 for IPv6) |

## Notes
- All numerical scores and amounts are returned as strings to maintain precision
- The axon object contains network connectivity information for the neuron
- The search parameter can be used to find neurons by various identifiers
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- Multiple boolean filters can be combined to find specific types of neurons
- The endpoint returns the latest state of the metagraph from the most recent block
- Trust, consensus, and incentive scores are used to determine neuron rankings and rewards
- The validator_permit field indicates whether the neuron has permission to validate on the network 