# Get Historical Stake

Returns historical stake information for validators and delegators over a specified time period or block range.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| coldkey | string | false | Filter by coldkey address (SS58 format) | - |
| hotkey | string | false | Filter by hotkey address (SS58 format) | - |
| block_start | integer | false | Starting block number | - |
| block_end | integer | false | Ending block number | - |
| timestamp_start | string | false | Start timestamp (Unix timestamp in seconds) | - |
| timestamp_end | string | false | End timestamp (Unix timestamp in seconds) | - |
| page | integer | false | Page number for pagination | 1 |
| limit | integer | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of historical stake records with detailed information about validators and delegators.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/stake_balance/history/v1', headers=headers)
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
| stake | Stake amount at this point in time (as string) |
| created_at_timestamp | ISO 8601 timestamp when the stake record was first created |
| created_at_block_number | Block number when the stake record was first created |

## Notes
- All stake amounts are returned as strings to maintain numerical precision
- You can filter by either block range or timestamp range, but not both simultaneously
- The order parameter determines whether results are sorted from newest to oldest (desc) or oldest to newest (asc)
- If no time range is specified, the endpoint returns the most recent historical records
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- Historical records show how stake amounts have changed over time for specific validators/delegators
- The hotkey_name field is included when validators have registered a name 