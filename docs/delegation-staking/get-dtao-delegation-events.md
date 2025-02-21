# Get dTao Delegation Events

Returns information about dTao delegation events on the network. This endpoint is part of the dTao beta features.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | false | Filter by hotkey address (SS58 format) | - |
| coldkey | string | false | Filter by coldkey address (SS58 format) | - |
| netuid | integer | false | Network/Subnet ID | - |
| block_number | integer | false | Filter by specific block number | - |
| block_start | integer | false | Starting block number | - |
| block_end | integer | false | Ending block number | - |
| timestamp_start | string | false | Start timestamp (Unix timestamp in seconds) | - |
| timestamp_end | string | false | End timestamp (Unix timestamp in seconds) | - |
| page | integer | false | Page number for pagination | 1 |
| limit | integer | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of dTao delegation events with detailed information about the participants and amounts.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/dtao/delegation/v1', headers=headers)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| hotkey.ss58 | Hotkey address in SS58 format |
| hotkey.hex | Hotkey address in hexadecimal format |
| coldkey.ss58 | Coldkey address in SS58 format |
| coldkey.hex | Coldkey address in hexadecimal format |
| block_number | Block number when the event occurred |
| timestamp | ISO 8601 timestamp of the block |
| amount | Delegation amount in dTao (as string) |
| action | Type of delegation action performed |

## Notes
- This endpoint is part of the dTao beta features and may be subject to changes
- All amounts are returned as strings to maintain numerical precision
- You can filter events by block range or timestamp range, but not both simultaneously
- Addresses are provided in both SS58 and hexadecimal formats for flexibility
- The endpoint supports filtering by both hotkey and coldkey addresses
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- The response includes detailed information about each delegation event, including the type of action performed
- Beta features may have additional rate limits or access restrictions 