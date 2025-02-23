# Get Validator Metrics History

Retrieves historical metrics for validators, including their stake, trust, emissions, and subnet participation over time.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | No | Filter by validator hotkey address | None |
| coldkey | string | No | Filter by validator coldkey address | None |
| netuid | int32 | No | Filter by subnet ID | None |
| block_number | int32 | No | Filter by specific block number | None |
| block_start | int32 | No | Filter events after this block number | None |
| block_end | int32 | No | Filter events before this block number | None |
| timestamp_start | string | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| timestamp_end | string | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 50 |
| order | string | No | Sort order ('asc' or 'desc') | 'desc' |

## Response

The response includes pagination information and an array of historical validator metrics.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/validator/metrics/history/v1"
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
| data[].coldkey.ss58 | Validator's SS58 formatted coldkey address |
| data[].coldkey.hex | Validator's hex formatted coldkey address |
| data[].hotkey.ss58 | Validator's SS58 formatted hotkey address |
| data[].hotkey.hex | Validator's hex formatted hotkey address |
| data[].netuid | Subnet ID where the validator is registered |
| data[].uid | Validator's unique identifier |
| data[].block_number | Block number of the data |
| data[].timestamp | Timestamp of the data in ISO 8601 format |
| data[].active | Whether the validator is currently active |
| data[].validator_permit | Whether the validator has permission to validate |
| data[].is_immunity_period | Whether the validator is in immunity period |
| data[].updated | Number of blocks since last update |
| data[].registered_block_number | Block number when the validator registered |
| data[].rank | Validator's current rank |
| data[].validator_trust | Validator's trust score |
| data[].stake | Validator's total stake |
| data[].emission | Validator's emission amount |
| data[].daily_reward | Validator's daily reward |
| data[].incentive | Validator's incentive score |
| data[].consensus | Validator's consensus score |
| data[].dividends | Validator's dividend amount |
| data[].trust | Validator's overall trust score |
| data[].axon_info | Validator's axon information (if available) |
| data[].axon_info.block | Block number of axon info update |
| data[].axon_info.ip | Validator's IP address |
| data[].axon_info.port | Validator's port number |
| data[].axon_info.ipType | IP address type |
| data[].axon_info.protocol | Protocol version |
| data[].axon_info.version | Axon version |

## Notes

- All stake and emission values are in TAO units (10^9)
- Trust scores are expressed as decimal values between 0 and 1
- Timestamps are in ISO 8601 format
- The response is paginated with a default limit of 50 items per page
- Both SS58 and hex formats are provided for hotkey and coldkey addresses
- Axon information may be null if the validator hasn't registered their endpoint
- Historical data can be filtered by block number range or timestamp range 