# Get Neuron Registrations

Returns information about neuron registrations across different subnets, including registration costs and associated keys.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | false | Filter by Network/Subnet ID | - |
| uid | int32 | false | Filter by Neuron ID | - |
| hotkey | string | false | Filter by hotkey address (SS58 format) | - |
| coldkey | string | false | Filter by coldkey address (SS58 format) | - |
| block_number | int32 | false | Filter by specific block number | - |
| block_start | int32 | false | Starting block number | - |
| block_end | int32 | false | Ending block number | - |
| timestamp_start | int64 | false | Start timestamp (Unix timestamp in seconds) | - |
| timestamp_end | int64 | false | End timestamp (Unix timestamp in seconds) | - |
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of neuron registration events with registration costs and associated keys.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/subnet/neuron/registration/v1', headers=headers)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| block_number | Block number when the registration occurred |
| timestamp | ISO 8601 timestamp of the block |
| netuid | Network/Subnet ID where the neuron was registered |
| uid | Assigned Neuron ID in the subnet |
| hotkey.ss58 | Hotkey address in SS58 format |
| hotkey.hex | Hotkey address in hexadecimal format |
| coldkey.ss58 | Coldkey address in SS58 format |
| coldkey.hex | Coldkey address in hexadecimal format |
| registration_cost | Cost of registration in TAO (as string) |

## Notes
- All costs are returned as strings to maintain numerical precision
- You can filter registrations by either block range or timestamp range, but not both simultaneously
- The endpoint supports filtering by subnet ID (netuid) to track registrations in specific subnets
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- Registration costs may vary over time and between different subnets
- The response includes both SS58 and hexadecimal formats for hotkey and coldkey addresses
- Each registration event creates a unique neuron identified by its UID within the specified subnet
- Historical registration data can be useful for analyzing network growth and participation costs 