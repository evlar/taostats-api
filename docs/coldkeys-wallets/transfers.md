# Get Transfers

Get transfer transactions between coldkey accounts, including details like amount, timestamp, and network.

```
GET https://api.taostats.io/api/transfer/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| network | string | Yes | The network to query (e.g., 'finney') | - |
| address | string | No | Filter by SS58 or hex format address | - |
| from | string | No | Filter by sender's SS58 or hex format address | - |
| to | string | No | Filter by recipient's SS58 or hex format address | - |
| transaction_hash | string | No | Filter by specific transaction hash | - |
| extrinsic_id | string | No | Filter by specific extrinsic ID | - |
| amount_min | string | No | Minimum transfer amount | 0 |
| amount_max | string | No | Maximum transfer amount | - |
| block_number | uint32 | No | Filter by specific block number | - |
| block_start | uint32 | No | Start of block range | - |
| block_end | uint32 | No | End of block range | - |
| timestamp_start | uint32 | No | Start of timestamp range (Unix timestamp) | - |
| timestamp_end | uint32 | No | End of timestamp range (Unix timestamp) | - |
| page | uint32 | No | Page number for pagination | 1 |
| limit | uint32 | No | Number of records per page | 50 |
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
      "id": string,
      "to": {
        "ss58": string,
        "hex": string
      },
      "from": {
        "ss58": string,
        "hex": string
      },
      "network": string,
      "block_number": integer,
      "timestamp": string (ISO 8601),
      "amount": string,
      "fee": string,
      "transaction_hash": string,
      "extrinsic_id": string
    }
  ]
}
```

## Example Request

```python
import requests

url = "https://api.taostats.io/api/transfer/v1?network=finney&limit=50"
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
| id | Unique identifier for the transfer (format: "{network}-{block_number}-{index}") |
| to.ss58 | Recipient's address in SS58 format |
| to.hex | Recipient's address in hexadecimal format |
| from.ss58 | Sender's address in SS58 format |
| from.hex | Sender's address in hexadecimal format |
| network | The network where the transfer occurred |
| block_number | The block number containing the transfer |
| timestamp | When the transfer occurred (ISO 8601 format) |
| amount | Transfer amount in TAO (as string to preserve precision) |
| fee | Transaction fee in TAO (as string to preserve precision) |
| transaction_hash | Unique hash identifying the transaction |
| extrinsic_id | Identifier for the extrinsic containing the transfer |

## Notes

- All balance values are returned as strings to preserve precision
- Timestamps are in ISO 8601 format
- Block and timestamp ranges can be used together to narrow down the search period
- Results are paginated with a default of 50 records per page
- The API returns both SS58 and hexadecimal formats for addresses to support different use cases 