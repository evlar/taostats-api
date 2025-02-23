# Get dTao Delegation Events

Returns information about dTao delegation events on the network. This endpoint is part of the dTao beta features.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | No | Hotkey of validator | - |
| coldkey | string | No | Coldkey of user | - |
| netuid | int32 | No | Network/Subnet ID | - |
| block_number | int32 | No | Filter by specific block number | - |
| block_start | int32 | No | Starting block number | - |
| block_end | int32 | No | Ending block number | - |
| timestamp_start | int32 | No | Unix timestamp (seconds since 1970-01-01) (inclusive) | - |
| timestamp_end | int32 | No | Unix timestamp (seconds since 1970-01-01) (inclusive) | - |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of results per page | 50 |
| order | string | No | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of dTao delegation events with detailed information about the participants and amounts.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/dtao/delegation/v1"
headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get(url, headers=headers)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| pagination.current_page | Current page number |
| pagination.per_page | Number of items per page |
| pagination.total_items | Total number of items across all pages |
| pagination.total_pages | Total number of pages |
| pagination.next_page | Next page number (null if no next page) |
| pagination.prev_page | Previous page number (null if no previous page) |
| data[].id | Unique identifier for the delegation event |
| data[].block_number | Block number when the event occurred |
| data[].timestamp | Timestamp of the event in ISO 8601 format |
| data[].action | Type of action ("DELEGATE" or "UNDELEGATE") |
| data[].nominator.ss58 | Nominator's SS58 address |
| data[].nominator.hex | Nominator's hex address |
| data[].delegate.ss58 | Delegate's SS58 address |
| data[].delegate.hex | Delegate's hex address |
| data[].amount | Amount of TAO delegated/undelegated |
| data[].alpha | Amount of alpha |
| data[].usd | USD value at the time of the event |
| data[].alpha_price_in_tao | Alpha price in TAO at the time of the event |
| data[].alpha_price_in_usd | Alpha price in USD at the time of the event |
| data[].netuid | Network/subnet ID |
| data[].extrinsic_id | Extrinsic ID of the event |

## Notes
- This endpoint is part of the dTao beta features and may be subject to changes
- All amounts are returned as strings to maintain numerical precision
- You can filter events by block range or timestamp range, but not both simultaneously
- Addresses are provided in both SS58 and hexadecimal formats for flexibility
- The endpoint supports filtering by both hotkey and coldkey addresses
- Pagination is implemented using the standard format
- The response includes detailed information about each delegation event, including prices and values at the time of the event
- Beta features may have additional rate limits or access restrictions 