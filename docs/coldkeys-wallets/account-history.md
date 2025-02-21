# Get Account History

Get historical data and transactions for coldkey accounts, including daily balance snapshots and rank changes.

```
GET https://api.taostats.io/api/account/history/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| network | string | Yes | The network to query (e.g., 'finney') | - |
| page | integer | No | Page number for pagination | 1 |
| limit | integer | No | Number of records per page (max 200) | 50 |
| block_number | integer | No | Filter by specific block number | - |
| block_start | integer | No | Start of block range | - |
| block_end | integer | No | End of block range | - |
| timestamp_start | integer | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| timestamp_end | integer | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| order | string | No | Sort order for results | - |

## Response

A successful response returns HTTP 200 status code with the following JSON structure:

```json
{
  "pagination": {
    "current_page": integer,
    "per_page": integer,
    "total_items": integer,
    "total_pages": integer,
    "next_page": integer|null,
    "prev_page": integer|null
  },
  "data": [
    {
      "address": {
        "ss58": string,
        "hex": string
      },
      "network": string,
      "block_number": integer,
      "timestamp": string (ISO 8601),
      "rank": integer,
      "balance_free": string,
      "balance_staked": string,
      "balance_total": string,
      "created_on_date": string (YYYY-MM-DD),
      "created_on_network": string,
      "coldkey_swap": {
        "old_coldkey": {
          "ss58": string,
          "hex": string
        },
        "new_coldkey": {
          "ss58": string,
          "hex": string
        },
        "network": string,
        "block_number": integer,
        "timestamp": string (ISO 8601)
      } | null
    }
  ]
}
```

## Example Request

```python
import requests

url = "https://api.taostats.io/api/account/history/v1?network=finney&page=1&limit=50"
headers = {
    "accept": "application/json",
    "Authorization": "YOUR-API-KEY"
}

response = requests.get(url, headers=headers)
print(response.text)
```

## Response Fields

| Field | Description |
|-------|-------------|
| address.ss58 | The SS58 formatted address of the coldkey |
| address.hex | The hexadecimal representation of the address |
| network | The network the account exists on |
| block_number | The block number when this data was recorded |
| timestamp | The timestamp when this data was recorded |
| rank | The rank of the account by total balance |
| balance_free | The free (transferable) balance |
| balance_staked | The staked (locked) balance |
| balance_total | The total balance (free + staked) |
| created_on_date | The date the account was created |
| created_on_network | The network where the account was originally created |
| coldkey_swap | Information about coldkey migration (if applicable) |

## Notes

- Historical data is typically captured in daily snapshots
- All balance values are returned as strings to preserve precision
- Timestamps are in ISO 8601 format
- The `coldkey_swap` field will be null for accounts that haven't migrated
- Results are paginated with a maximum of 200 records per page
- Block and timestamp ranges can be used together to narrow down the search period 