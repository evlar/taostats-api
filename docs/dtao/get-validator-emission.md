# Get Validator Emission by Subnet

Retrieves emission information for a validator across different subnets, including both subnet-specific and root network emissions.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | Yes | The validator's hotkey address | None |
| netuid | int32 | No | Filter by network/subnet ID | None |
| block_number | int32 | No | Filter by specific block number | None |
| block_start | int32 | No | Start of block range (inclusive) | None |
| block_end | int32 | No | End of block range (inclusive) | None |
| timestamp_start | string | No | Start timestamp (ISO 8601) | None |
| timestamp_end | string | No | End timestamp (ISO 8601) | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 50 |
| order | string | No | Sort order for results | None |

## Response

The response includes pagination information and an array of emission records across different subnets.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/dtao/hotkey_emission/v1"
params = {
    "hotkey": "5HK5tp6t2S59DywmHRWPBVJeJ86T61KjurYqeooqj8sREpeN",
    "page": 1
}
headers = {
    "accept": "application/json",
    "Authorization": "YOUR-API-KEY"
}

response = requests.get(url, params=params, headers=headers)
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
| data[].block_number | Block number when the emission was recorded |
| data[].timestamp | ISO 8601 formatted timestamp of the block |
| data[].netuid | Network/subnet ID |
| data[].hotkey.ss58 | Validator's SS58 formatted hotkey address |
| data[].hotkey.hex | Validator's hex formatted hotkey address |
| data[].emission | Subnet-specific emission value |
| data[].root_emission | Root network emission value |

## Notes

- Returns emission data for each subnet where the validator is active
- Both subnet-specific and root network emissions are provided
- Emissions can be filtered by block number or timestamp ranges
- The response is paginated with a default limit of 50 items per page
- Timestamps are provided in ISO 8601 format
- Both SS58 and hex formats are provided for hotkey addresses
- A value of 0 for both emission and root_emission indicates no emissions for that subnet 