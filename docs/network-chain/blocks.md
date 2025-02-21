# Get Blocks

Get information about blocks on the Bittensor network.

```
GET https://api.taostats.io/api/block/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| page | integer | No | Page number for pagination | 1 |
| limit | integer | No | Number of records per page | 50 |
| block_number | integer | No | Filter by specific block number | - |
| block_start | integer | No | Start of block range | - |
| block_end | integer | No | End of block range | - |
| timestamp_start | integer | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| timestamp_end | integer | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| spec_version | integer | No | Filter by specific spec version | - |
| validator | string | No | Filter by validator address (SS58 format) | - |

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
      "block_number": integer,
      "hash": string,
      "parent_hash": string,
      "state_root": string,
      "extrinsics_root": string,
      "spec_name": string,
      "spec_version": integer,
      "impl_name": string,
      "impl_version": integer,
      "timestamp": string (ISO 8601),
      "validator": string|null,
      "events_count": integer,
      "extrinsics_count": integer,
      "calls_count": integer
    }
  ]
}
```

## Example Request

```python
import requests

url = "https://api.taostats.io/api/block/v1?page=1&limit=50"
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
| block_number | The block number |
| hash | The unique hash of this block |
| parent_hash | The hash of the parent block |
| state_root | The state root hash |
| extrinsics_root | The root hash of the extrinsics |
| spec_name | The name of the runtime specification |
| spec_version | The version of the runtime specification |
| impl_name | The name of the runtime implementation |
| impl_version | The version of the runtime implementation |
| timestamp | When the block was created (ISO 8601 format) |
| validator | The validator's address (null if not available) |
| events_count | Number of events in this block |
| extrinsics_count | Number of extrinsics in this block |
| calls_count | Number of calls in this block |

## Notes

- Block data is ordered by block number in descending order by default
- Timestamps are in ISO 8601 format
- Block and timestamp ranges can be used together to narrow down the search period
- Results are paginated with a default of 50 records per page
- The validator field may be null if the validator information is not available 