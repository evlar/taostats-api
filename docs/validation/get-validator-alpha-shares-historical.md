# Get Validator Alpha Shares (Historical)

Retrieves historical alpha shares distribution for validators across all subnets, including their share amounts and alpha values over time.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | No | Filter by validator hotkey address | None |
| netuid | int32 | No | Filter by subnet ID | None |
| block_number | int32 | No | Filter by specific block number | None |
| block_start | int32 | No | Filter events after this block number | None |
| block_end | int32 | No | Filter events before this block number | None |
| timestamp_start | int32 | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| timestamp_end | int32 | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 50 |
| order | string | No | Sort order ('asc' or 'desc') | 'desc' |

## Response

The response includes pagination information and an array of historical validator alpha share records.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/dtao/hotkey_alpha_shares/history/v1"
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
| data[].block_number | Block number when the shares were recorded |
| data[].timestamp | Timestamp of the record in ISO 8601 format |
| data[].netuid | Subnet ID where the shares are allocated |
| data[].hotkey.ss58 | Validator's SS58 formatted hotkey address |
| data[].hotkey.hex | Validator's hex formatted hotkey address |
| data[].shares | Total share amount allocated to the validator |
| data[].alpha | Alpha value in nanoAlpha units |

## Notes

- Share values are represented as strings to maintain numerical precision
- Alpha values are in nanoAlpha units (10^9)
- Timestamps are in ISO 8601 format
- The response is paginated with a default limit of 50 items per page
- Both SS58 and hex formats are provided for hotkey addresses
- Results are sorted by block number in descending order by default
- Historical data can be filtered by block number range or timestamp range
- Share distribution reflects the validator's participation across all subnets at each point in time 