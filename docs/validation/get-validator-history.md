# Get Validator History

Retrieves historical information about validators, including their stake, nominators, registrations, and subnet dominance.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | No | Filter by validator hotkey address | None |
| block_number | int32 | No | Filter by specific block number | None |
| block_start | int32 | No | Filter events after this block number | None |
| block_end | int32 | No | Filter events before this block number | None |
| timestamp_start | string | No | Filter events after this timestamp (ISO 8601) | None |
| timestamp_end | string | No | Filter events before this timestamp (ISO 8601) | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 50 |
| order | string | No | Sort order ('asc' or 'desc') | 'desc' |

## Response

The response includes pagination information and an array of validator records with detailed information about their stake, nominators, and subnet participation.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/validator/history/v1"
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
| data[].hotkey.ss58 | Validator's SS58 formatted hotkey address |
| data[].hotkey.hex | Validator's hex formatted hotkey address |
| data[].coldkey.ss58 | Validator's SS58 formatted coldkey address |
| data[].coldkey.hex | Validator's hex formatted coldkey address |
| data[].name | Validator's name (if set) |
| data[].block_number | Block number of the data |
| data[].timestamp | Timestamp of the data in ISO 8601 format |
| data[].created_on_date | Date when the validator was created |
| data[].rank | Validator's current rank |
| data[].nominators | Number of current nominators |
| data[].nominators_24_hr_change | Change in number of nominators over 24 hours |
| data[].system_stake | Total stake in the system |
| data[].stake | Validator's total stake |
| data[].stake_24_hr_change | Change in stake over 24 hours |
| data[].dominance | Validator's stake dominance (percentage) |
| data[].validator_stake | Amount staked by the validator themselves |
| data[].take | Validator's take rate |
| data[].total_daily_return | Total daily return |
| data[].validator_return | Validator's return |
| data[].nominator_return_per_k | Return per 1000 TAO for nominators |
| data[].apr | Annual Percentage Rate |
| data[].nominator_return_per_k_7_day_average | 7-day average return per 1000 TAO for nominators |
| data[].nominator_return_per_k_30_day_average | 30-day average return per 1000 TAO for nominators |
| data[].apr_7_day_average | 7-day average APR |
| data[].apr_30_day_average | 30-day average APR |
| data[].pending_emission | Pending emission amount |
| data[].blocks_until_next_reward | Number of blocks until next reward |
| data[].last_reward_block | Block number of last reward |
| data[].registrations | Array of subnet IDs where validator is registered |
| data[].permits | Array of subnet IDs where validator has permits |
| data[].subnet_dominance | Array of subnet-specific dominance information |
| data[].subnet_dominance[].netuid | Subnet ID |
| data[].subnet_dominance[].dominance | Validator's dominance in the subnet |
| data[].subnet_dominance[].family_stake | Total family stake in the subnet |

## Notes

- All stake values are in TAO units (10^9)
- Dominance values are expressed as decimal percentages
- Timestamps are in ISO 8601 format
- APR values are expressed as decimal percentages
- The response is paginated with a default limit of 50 items per page
- Both SS58 and hex formats are provided for hotkey and coldkey addresses
- Subnet dominance information is provided for all subnets, even if the validator has no stake in them 