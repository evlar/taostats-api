# Get Metagraph History

Returns historical information about neurons (validators) in the network's metagraph over a specified time period or block range.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | true | Network/Subnet ID | - |
| uid | int32 | false | Filter by Neuron ID | - |
| hotkey | string | false | Filter by hotkey address (SS58 format) | - |
| coldkey | string | false | Filter by coldkey address (SS58 format) | - |
| block_start | int32 | false | Starting block number | - |
| block_end | int32 | false | Ending block number | - |
| timestamp_start | int64 | false | Start timestamp (Unix timestamp in seconds since 1970-01-01) | - |
| timestamp_end | int64 | false | End timestamp (Unix timestamp in seconds since 1970-01-01) | - |
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of historical neuron states in the metagraph.

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

response = requests.get('https://api.taostats.io/api/metagraph/history/v1', headers=headers, params=params)
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
| stake | Total stake amount at this point in time (as string) |
| trust | Historical trust score |
| validator_trust | Historical validator trust score |
| consensus | Historical consensus score |
| incentive | Historical incentive score |
| dividends | Historical dividends score |
| emission | Historical emission amount |
| active | Whether the neuron was active at this point |
| validator_permit | Whether the neuron had validator permissions |
| updated | Last update block number |
| daily_reward | Daily reward amount at this point (as string) |
| registered_at_block | Block number when the neuron was registered |
| is_immunity_period | Whether the neuron was in immunity period |
| rank | Neuron's historical rank in the network |
| is_child_key | Whether this was a child key |
| axon | Historical network connectivity information |
| axon.block | Block number when axon info was updated |
| axon.ip | IP address of the node |
| axon.port | Port number |
| axon.protocol | Protocol version |
| axon.version | Axon version |
| axon.ipType | IP address type (4 for IPv4, 6 for IPv6) |

## Notes
- All numerical scores and amounts are returned as strings to maintain precision
- You can filter by either block range or timestamp range, but not both simultaneously
- The endpoint provides historical tracking of all neuron metrics and scores
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- Historical records show how neuron parameters and performance have changed over time
- The axon object contains historical network connectivity information
- Timestamps can be specified as Unix timestamps (seconds since epoch)
- The response includes the complete state of each neuron at each historical point 