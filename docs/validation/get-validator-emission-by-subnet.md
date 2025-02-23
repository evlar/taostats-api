# Get Validator Emission by Subnet

Retrieves historical emission data for a validator on a specific subnet, including both direct and root emissions.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | Yes | Validator's hotkey address | None |
| netuid | int32 | Yes | Network/subnet ID | None |
| block_number | int32 | No | Filter by specific block number | None |
| block_start | int32 | No | Filter events after this block number | None |
| block_end | int32 | No | Filter events before this block number | None |
| timestamp_start | string | No | Filter events after this timestamp (ISO 8601) | None |
| timestamp_end | string | No | Filter events before this timestamp (ISO 8601) | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 50 |
| order | string | No | Sort order ('asc' or 'desc') | 'desc' |

## Response

The response includes pagination information and an array of emission records.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/dtao/hotkey_emission/v1"
headers = {
    "accept": "application/json",
    "Authorization": "YOUR-API-KEY"
}
params = {
    "hotkey": "5HK5tp6t2S59DywmHRWPBVJeJ86T61KjurYqeooqj8sREpeN",
    "netuid": 64,
    "page": 1
}

response = requests.get(url, headers=headers, params=params)
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
| data[].timestamp | Timestamp of the emission record |
| data[].netuid | Subnet ID where the emission occurred |
| data[].hotkey.ss58 | Validator's SS58 formatted hotkey address |
| data[].hotkey.hex | Validator's hex formatted hotkey address |
| data[].emission | Direct emission amount in nanoTAO |
| data[].root_emission | Root emission amount in nanoTAO |

## Notes

- All emission values are in nanoTAO units (10^9)
- Timestamps are in ISO 8601 format
- The response is paginated with a default limit of 50 items per page
- Both SS58 and hex formats are provided for hotkey addresses
- Emission data can be filtered by:
  - Block number or block range
  - Timestamp range
  - Specific subnet ID
- The emission field represents direct emissions to the validator
- The root_emission field represents emissions at the root level
- Historical data is typically available for the past 30 days
- Emissions are recorded approximately every 75 minutes (360 blocks) 