# Get Subnet Owner

Returns information about subnet ownership, including ownership transfers and coldkey swaps.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | false | Filter by Network/Subnet ID | - |
| owner | string | false | Filter by owner address (SS58 format) | - |
| is_coldkey_swap | boolean | false | Filter by coldkey swap status | - |
| block_number | int32 | false | Filter by specific block number | - |
| block_start | int32 | false | Starting block number | - |
| block_end | int32 | false | Ending block number | - |
| timestamp_start | int64 | false | Start timestamp (Unix timestamp in seconds) | - |
| timestamp_end | int64 | false | End timestamp (Unix timestamp in seconds) | - |
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of subnet ownership records with ownership transfer details.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/subnet/owner/v1', headers=headers)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| block_number | Block number when the ownership record was created |
| timestamp | ISO 8601 timestamp of the block |
| netuid | Network/Subnet ID |
| owner.ss58 | Owner's address in SS58 format |
| owner.hex | Owner's address in hexadecimal format |
| is_coldkey_swap | Whether this record represents a coldkey swap |

## Notes
- The endpoint tracks subnet ownership changes over time, including:
  - Initial subnet ownership assignments
  - Ownership transfers between addresses
  - Coldkey swap events
- You can filter ownership records by:
  - Specific subnet ID (netuid)
  - Owner address
  - Block range or timestamp range
  - Coldkey swap status
- Pagination is implemented using the standard format with:
  - current_page
  - per_page (default 50)
  - total_items
  - total_pages
  - next_page
  - prev_page
- Owner addresses are provided in both SS58 and hexadecimal formats
- The is_coldkey_swap field helps distinguish between:
  - Regular ownership transfers
  - Coldkey swap operations
- Historical ownership data can be useful for:
  - Tracking subnet governance
  - Analyzing ownership patterns
  - Monitoring subnet transfers
  - Understanding coldkey swap activity 