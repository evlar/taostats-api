# Get Validator

Retrieves detailed information about a validator, including their stake, nominators, registrations, and subnet dominance.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | No | Filter by validator hotkey address | None |
| stake_min | string | No | Filter by minimum stake amount | None |
| stake_max | string | No | Filter by maximum stake amount | None |
| sor_min | string | No | Filter by minimum stake over rank | None |
| sor_max | string | No | Filter by maximum stake over rank | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 50 |
| order | string | No | Sort order ('asc' or 'desc') | 'desc' |

## Response

The response includes detailed validator information and pagination details.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/validator/latest/v1"
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
| hotkey.ss58 | Validator's SS58 formatted hotkey address |
| hotkey.hex | Validator's hex formatted hotkey address |
| coldkey.ss58 | Validator's SS58 formatted coldkey address |
| coldkey.hex | Validator's hex formatted coldkey address |
| name | Validator's name (if set) |
| block_number | Block number of the data |
| timestamp | Timestamp of the data in ISO 8601 format |
| created_on_date | Date when the validator was created |
| rank | Validator's current rank |
| nominators | Number of current nominators |
| nominators_24_hr_change | Change in number of nominators over 24 hours |
| system_stake | Total stake in the system |
| stake | Validator's total stake |
| stake_24_hr_change | Change in stake over 24 hours |
| dominance | Validator's stake dominance (percentage) |
| validator_stake | Amount staked by the validator themselves |
| take | Validator's take rate |
| total_daily_return | Total daily return |
| validator_return | Validator's return |
| nominator_return_per_k | Return per 1000 TAO for nominators |
| apr | Annual Percentage Rate |
| nominator_return_per_k_7_day_average | 7-day average return per 1000 TAO for nominators |
| nominator_return_per_k_30_day_average | 30-day average return per 1000 TAO for nominators |
| apr_7_day_average | 7-day average APR |
| apr_30_day_average | 30-day average APR |
| pending_emission | Pending emission amount |
| blocks_until_next_reward | Number of blocks until next reward |
| last_reward_block | Block number of last reward |
| registrations | Array of subnet IDs where validator is registered |
| permits | Array of subnet IDs where validator has permits |
| subnet_dominance | Array of subnet-specific dominance information |
| subnet_dominance[].netuid | Subnet ID |
| subnet_dominance[].dominance | Validator's dominance in the subnet |
| subnet_dominance[].family_stake | Total family stake in the subnet |

## Notes

- All stake and return values are in TAO units (10^9)
- Dominance values are expressed as decimal percentages
- Timestamps are in ISO 8601 format
- APR values are expressed as decimal percentages
- The response is paginated with a default limit of 50 items per page
- Both SS58 and hex formats are provided for hotkey and coldkey addresses
- Subnet dominance information is provided for all subnets, even if the validator has no stake in them 