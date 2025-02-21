# Get Account

Get detailed information about coldkey accounts, including balances, ranks, and creation details.

```
GET https://api.taostats.io/api/account/latest/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| network | string | Yes | The network to query (e.g., 'Finney') | - |
| page | integer | No | Page number for pagination | 1 |
| limit | integer | No | Number of records per page (max 200) | 50 |
| balance_free_min | string | No | Minimum free balance filter | 0 |
| balance_free_max | string | No | Maximum free balance filter | - |
| balance_staked_min | string | No | Minimum staked balance filter | 0 |
| balance_staked_max | string | No | Maximum staked balance filter | - |
| balance_total_min | string | No | Minimum total balance filter | 0 |
| balance_total_max | string | No | Maximum total balance filter | - |
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

url = "https://api.taostats.io/api/account/latest/v1?network=Finney&page=1&limit=50"
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

- All balance values are returned as strings to preserve precision
- Timestamps are in ISO 8601 format
- The `coldkey_swap` field will be null for accounts that haven't migrated
- Results are paginated with a maximum of 200 records per page
- Balance filters use string comparison to maintain precision 