# Get Proxy Calls

Get proxy calls made on the Bittensor network. This endpoint is useful for tracking delegated transactions and proxy relationships.

```
GET https://api.taostats.io/api/proxy_call/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| id | string | No | Filter by proxy call ID | - |
| signer_address | string | No | Filter by proxy signer's address | - |
| real_address | string | No | Filter by real (delegating) address | - |
| network | string | No | Filter by network name | - |
| block_number | integer | No | Filter by specific block number | - |
| block_start | integer | No | Start of block range | - |
| block_end | integer | No | End of block range | - |
| timestamp_start | integer | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| timestamp_end | integer | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| extrinsic_hash | string | No | Filter by extrinsic hash | - |
| extrinsic_id | string | No | Filter by extrinsic ID | - |
| page | integer | No | Page number for pagination | 1 |
| limit | integer | No | Number of records per page | 50 |
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
      "network": string,
      "block_number": integer,
      "timestamp": string (ISO 8601),
      "signer_address": {
        "ss58": string,
        "hex": string
      },
      "real_address": {
        "ss58": string,
        "hex": string
      },
      "args": {
        "__kind": string,
        "calls": [
          {
            "__kind": string,
            "value": {
              "__kind": string,
              "call": object,
              "forceProxyType": {
                "__kind": string
              },
              "real": {
                "__kind": string,
                "value": string
              }
            }
          }
        ]
      },
      "extrinsic_id": string,
      "extrinsic_hash": string
    }
  ]
}
```

## Example Request

```python
import requests

url = "https://api.taostats.io/api/proxy_call/v1?page=1&limit=50"
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
| id | Unique identifier for the proxy call (format: "{network}-{block_number}-{index}") |
| network | The network where the proxy call was made |
| block_number | The block number containing this proxy call |
| timestamp | When the proxy call was made (ISO 8601 format) |
| signer_address.ss58 | The SS58-formatted address of the proxy signer |
| signer_address.hex | The hex representation of the proxy signer's address |
| real_address.ss58 | The SS58-formatted address of the real (delegating) account |
| real_address.hex | The hex representation of the real account's address |
| args | The arguments and details of the proxy call |
| args.__kind | The type of call (e.g., "batch") |
| args.calls | Array of calls made through the proxy |
| extrinsic_id | ID of the extrinsic containing this proxy call |
| extrinsic_hash | Hash of the extrinsic |

## Notes

- Proxy calls are ordered by block number in descending order by default
- Timestamps are in ISO 8601 format
- The `args` structure varies depending on the type of proxy call
- Common proxy call types include:
  - Staking operations (add_stake, remove_stake)
  - Batch transactions containing multiple calls
  - Other delegated operations
- The `forceProxyType` field indicates the type of proxy relationship (e.g., "Staking")
- Both SS58 and hex formats are provided for addresses to support different use cases 