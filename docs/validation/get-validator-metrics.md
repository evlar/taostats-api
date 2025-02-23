# Get Validator Metrics

Retrieves the latest metrics for validators, including their stake, trust, emissions, and subnet participation.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | No | Filter by validator hotkey address | None |
| netuid | int32 | No | Filter by subnet ID | None |
| uid | int32 | No | Filter by validator UID | None |
| block_number | int32 | No | Filter by specific block number | None |
| stake_min | string | No | Filter by minimum stake amount | None |
| stake_max | string | No | Filter by maximum stake amount | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 50 |

## Response

The response includes pagination information and an array of validator metrics with detailed information about their stake, trust, emissions, and subnet participation.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/validator/metrics/latest/v1"
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