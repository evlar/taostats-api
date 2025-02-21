# Get Stake Balance Sum in Tao

Returns the aggregated stake balance in TAO for each coldkey, ranked by total balance.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| coldkey | string | false | Filter by coldkey address (SS58 format) | - |
| total_balance_as_tao_min | string | false | Minimum total balance in TAO | - |
| total_balance_as_tao_max | string | false | Maximum total balance in TAO | - |
| page | integer | false | Page number for pagination | 1 |
| limit | integer | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of coldkey addresses and their total stake balances, sorted by rank.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/dtao/stake_balance_aggregated/latest/v1', headers=headers)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| block_number | Block number when the balance was recorded |
| rank | Ranking position based on total balance |
| timestamp | ISO 8601 timestamp of the block |
| coldkey.ss58 | Coldkey address in SS58 format |
| coldkey.hex | Coldkey address in hexadecimal format |
| total_balance_as_tao | Total stake balance in TAO (as string) |

## Notes
- All balance amounts are returned as strings to maintain numerical precision
- Results are ranked by total balance in descending order by default
- The endpoint provides both SS58 and hexadecimal formats for coldkey addresses
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- Balance filtering can be done using total_balance_as_tao_min and total_balance_as_tao_max parameters
- The response includes the block number and timestamp when the balances were recorded
- Each record includes a rank field indicating its position in the overall balance ranking 