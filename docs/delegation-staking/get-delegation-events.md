# Get Staking/Delegation Events

Returns information about staking and delegation events on the network, including delegator-validator relationships and balances.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| delegate | string | false | Filter by delegate/validator address (SS58 format) | - |
| nominator | string | false | Filter by nominator/delegator address (SS58 format) | - |
| netuid | integer | false | Network/Subnet ID | - |
| action | string | false | Type of action to filter by | 'all' |
| extrinsic_id | string | false | Filter by specific extrinsic ID | - |
| amount_min | string | false | Minimum amount in TAO (in billionths) | - |
| amount_max | string | false | Maximum amount in TAO (in billionths) | - |
| block_number | integer | false | Filter by specific block number | - |
| block_start | integer | false | Starting block number | - |
| block_end | integer | false | Ending block number | - |
| timestamp_start | string | false | Start timestamp (Unix timestamp in seconds) | - |
| timestamp_end | string | false | End timestamp (Unix timestamp in seconds) | - |
| page | integer | false | Page number for pagination | 1 |
| limit | integer | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of staking and delegation events with detailed information about the participants and amounts.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

params = {
    'action': 'all',
    'page': 1,
    'limit': 50
}

response = requests.get('https://api.taostats.io/api/delegation/v1', headers=headers, params=params)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| nominator.ss58 | Nominator/delegator address in SS58 format |
| nominator.hex | Nominator/delegator address in hexadecimal format |
| delegate.ss58 | Delegate/validator address in SS58 format |
| delegate.hex | Delegate/validator address in hexadecimal format |
| block_number | Block number when the event occurred |
| timestamp | ISO 8601 timestamp of the block |
| balance | Current delegation balance in TAO (as string) |
| delegate_from | Block number when the delegation relationship started |
| delegate_from_timestamp | ISO 8601 timestamp when the delegation relationship started |

## Notes
- All balance amounts are returned as strings to maintain numerical precision
- You can filter events by block range or timestamp range, but not both simultaneously
- The action parameter can be used to filter specific types of delegation events
- Addresses are provided in both SS58 and hexadecimal formats for flexibility
- The endpoint supports filtering by both delegator (nominator) and validator (delegate) addresses
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- The delegate_from fields help track the history of delegation relationships 