# Get Stake (v2)

Returns the current stake information for validators and delegators on the network.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | false | Filter by hotkey address (SS58 format) | - |
| coldkey | string | false | Filter by coldkey address (SS58 format) | - |
| limit | integer | false | Number of results per page | 50 |
| page | integer | false | Page number for pagination | 1 |

## Response
The endpoint returns a paginated list of stake records with detailed information about validators and delegators.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/stake_balance/latest/v1', headers=headers)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| block_number | Block number when the stake record was updated |
| timestamp | ISO 8601 timestamp of the block |
| hotkey_name | Optional name assigned to the hotkey |
| hotkey.ss58 | Hotkey address in SS58 format |
| hotkey.hex | Hotkey address in hexadecimal format |
| coldkey.ss58 | Coldkey address in SS58 format |
| coldkey.hex | Coldkey address in hexadecimal format |
| stake | Current stake amount in Tao (as string) |
| created_at_timestamp | ISO 8601 timestamp when the stake record was first created |
| created_at_block_number | Block number when the stake record was first created |

## Notes
- The stake amount is returned as a string to maintain numerical precision
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- Hotkey and coldkey addresses are provided in both SS58 and hexadecimal formats for flexibility
- The endpoint returns the latest stake information from the most recent block
- Optional hotkey_name field is included when validators have registered a name 