# Get Validator Weights History

Retrieves historical weight settings by validators for their peers in the network, including version information and weight distributions over time.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | No | Filter by validator hotkey address | None |
| netuid | int32 | No | Filter by subnet ID | None |
| uid | int32 | No | Filter by validator UID | None |
| block_number | int32 | No | Filter by specific block number | None |
| block_start | int32 | No | Filter events after this block number | None |
| block_end | int32 | No | Filter events before this block number | None |
| timestamp_start | int32 | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| timestamp_end | int32 | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| page | int32 | No | Page number for pagination | 0 |
| limit | int32 | No | Number of records per page | 0 |
| order | string | No | Sort order ('asc' or 'desc') | None |

## Response

The response includes pagination information and an array of historical validator weight records.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/validator/weights/history/v1"
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
| pagination.current_page | Current page number |
| pagination.per_page | Number of items per page |
| pagination.total_items | Total number of items across all pages |
| pagination.total_pages | Total number of pages |
| pagination.next_page | Next page number (null if no next page) |
| pagination.prev_page | Previous page number (null if no previous page) |
| data[].hotkey | Object containing validator's hotkey information |
| data[].netuid | Subnet ID where the weights were set |
| data[].uid | Validator's unique identifier in the subnet |
| data[].block_number | Block number when the weights were set |
| data[].timestamp | Timestamp of the weight setting |
| data[].version_key | Version key of the weights (if applicable) |
| data[].call | Type of call used to set weights |
| data[].weights_hash | Hash of the weights |
| data[].weights | Array of weight objects |
| data[].weights[].uid | Target validator's unique identifier |
| data[].weights[].weight | Weight assigned to the target validator (as a string) |

## Notes

- Weights are expressed as decimal strings with high precision (e.g., "0.79987792782482642863")
- Timestamps are in Unix timestamp format (seconds since epoch)
- The response is paginated with configurable page size
- Weight values represent the trust or importance a validator assigns to other validators in the network
- The `weights` array contains entries for all validators in the subnet
- Historical data can be filtered by:
  - Block number or block range
  - Timestamp range
  - Specific validator (using hotkey or uid)
  - Subnet ID
- Results can be ordered ascending or descending
- Default pagination values (page and limit) are 0, which should be overridden as needed 