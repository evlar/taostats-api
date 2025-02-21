# Get Extrinsics

Lists all primary extrinsics. To get extrinsics in batch/proxy calls use the Get Calls endpoint.

```
GET https://api.taostats.io/api/extrinsic/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| block_number | integer | No | Filter by specific block number | - |
| block_start | integer | No | Start of block range | - |
| block_end | integer | No | End of block range | - |
| timestamp_start | integer | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| timestamp_end | integer | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| hash | string | No | Filter by extrinsic hash | - |
| full_name | string | No | Filter by full name of the call | - |
| id | string | No | Filter by extrinsic ID | - |
| signer_address | string | No | Filter by signer's address | - |
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
      "timestamp": string (ISO 8601),
      "block_number": integer,
      "hash": string,
      "id": string,
      "index": integer,
      "version": integer,
      "signature": {
        "address": {
          "__kind": string,
          "value": string
        },
        "signature": {
          "__kind": string,
          "value": string
        },
        "signedExtensions": {
          "chargeTransactionPayment": string,
          "checkMetadataHash": {
            "mode": {
              "__kind": string
            }
          },
          "checkMortality": {
            "__kind": string,
            "value": integer
          },
          "checkNonce": integer
        }
      },
      "signer_address": string,
      "tip": string,
      "fee": string,
      "success": boolean,
      "error": {
        "__kind": string,
        "value": {
          "error": string,
          "index": integer
        }
      } | null,
      "call_id": string,
      "full_name": string,
      "call_args": object
    }
  ]
}
```

## Example Request

```python
import requests

url = "https://api.taostats.io/api/extrinsic/v1?limit=50"
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
| timestamp | When the extrinsic was included in a block (ISO 8601 format) |
| block_number | The block number containing this extrinsic |
| hash | The unique hash of this extrinsic |
| id | Unique identifier (format: "{block_number}-{index}") |
| index | Index of this extrinsic within its block |
| version | Version of the extrinsic format |
| signature.address | The address that signed this extrinsic |
| signature.signature | The cryptographic signature |
| signature.signedExtensions | Additional signed data for the extrinsic |
| signer_address | The SS58-formatted address of the signer |
| tip | Tip amount included with the extrinsic |
| fee | Transaction fee |
| success | Whether the extrinsic was executed successfully |
| error | Error information if the extrinsic failed, null if successful |
| call_id | Identifier for the specific call (same as id for primary extrinsics) |
| full_name | Full name of the called function (format: "Module.function") |
| call_args | Arguments passed to the function call |

## Notes

- Extrinsics are ordered by block number and index in descending order by default
- Timestamps are in ISO 8601 format
- All balance values (tip, fee) are returned as strings to preserve precision
- The `call_args` structure varies depending on the `full_name` of the call
- For batch or proxy calls, use the Get Calls endpoint to see individual calls within the extrinsic 