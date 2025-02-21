# Get Chain Calls

This endpoint lists all extrinsics - as some calls can be nested inside batch/proxy calls.

```
GET https://api.taostats.io/api/call/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| network | string | Yes | Network to query (e.g., 'finney') | - |
| block_number | integer | No | Filter by specific block number | - |
| block_start | integer | No | Start of block range | - |
| block_end | integer | No | End of block range | - |
| timestamp_start | integer | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| timestamp_end | integer | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| success | boolean | No | Filter by call success status | - |
| full_name | string | No | Filter by full name of the call | - |
| id | string | No | Filter by call ID | - |
| extrinsic_id | string | No | Filter by extrinsic ID | - |
| parent_id | string | No | Filter by parent call ID | - |
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
      "extrinsic_id": string,
      "parent_id": string|null,
      "extrinsic_index": integer,
      "success": boolean,
      "error": {
        "extra_info": string,
        "name": string,
        "pallet": string
      }|null,
      "pallet": string,
      "name": string,
      "full_name": string,
      "args": object,
      "origin": {
        "__kind": string,
        "value": object
      },
      "origin_address": string,
      "timestamp": string (ISO 8601),
      "block_number": integer
    }
  ]
}
```

## Example Request

```python
import requests

url = "https://api.taostats.io/api/call/v1?network=finney"
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
| id | Unique identifier for the call (format: "{block_number}-{extrinsic_index}[-{index}]") |
| extrinsic_id | ID of the extrinsic containing this call |
| parent_id | ID of the parent call (for nested calls), null for top-level calls |
| extrinsic_index | Index of the extrinsic within its block |
| success | Whether the call was executed successfully |
| error | Error information if the call failed, null if successful |
| pallet | Name of the pallet containing the called function |
| name | Name of the called function |
| full_name | Full name of the called function (format: "Pallet.function") |
| args | Arguments passed to the function |
| origin | Information about the call's origin (system, signed, etc.) |
| origin_address | The address that originated the call |
| timestamp | When the call was executed (ISO 8601 format) |
| block_number | The block number containing this call |

## Notes

- Calls are ordered by block number and index in descending order by default
- Timestamps are in ISO 8601 format
- The `args` structure varies depending on the call type
- Common call types include:
  - SubtensorModule.add_stake: Add stake to a hotkey
  - SubtensorModule.remove_stake: Remove stake from a hotkey
  - SubtensorModule.burned_register: Register a new neuron
  - Balances.transfer_keep_alive: Transfer tokens while keeping account alive
- Parent/child relationships are used to represent nested calls (e.g., in batch transactions)
- The `error` field provides detailed information when a call fails, including:
  - name: The type of error
  - pallet: The pallet where the error occurred
  - extra_info: Additional error details 