# Get Stake Balance

Retrieves the current stake balance information for validators across different subnets.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| coldkey | string | Yes | The validator's coldkey address | None |
| hotkey | string | No | Filter by validator's hotkey address | None |
| netuid | int32 | No | Filter by network/subnet ID | None |
| balance_min | string | No | Minimum balance filter in rao | None |
| balance_max | string | No | Maximum balance filter in rao | None |
| balance_as_tao_min | string | No | Minimum balance filter in tao | None |
| balance_as_tao_max | string | No | Maximum balance filter in tao | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 50 |
| order | string | No | Sort order for results | None |

## Response

The response includes pagination information and an array of current stake balance records for validators.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/dtao/stake_balance/latest/v1"
params = {
    "coldkey": "5CGwW5WJ3ES7G7WJKtqsRwb2WANBH5u9PxhFTqvRpjWMpodz"
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
| data[].block_number | Block number when the balance was recorded |
| data[].timestamp | ISO 8601 formatted timestamp of the block |
| data[].hotkey_name | Name associated with the validator's hotkey |
| data[].hotkey.ss58 | Validator's SS58 formatted hotkey address |
| data[].hotkey.hex | Validator's hex formatted hotkey address |
| data[].coldkey.ss58 | Validator's SS58 formatted coldkey address |
| data[].coldkey.hex | Validator's hex formatted coldkey address |
| data[].netuid | Network/subnet ID |
| data[].subnet_rank | Validator's rank in the subnet |
| data[].balance | Raw balance value in rao |
| data[].balance_as_tao | Balance converted to tao units |

## Notes

- Returns current stake balances for all subnets where the validator has stake
- Supports filtering by balance ranges in both rao and tao units
- Subnet rank indicates the validator's position in the subnet (lower numbers = higher rank)
- Balance values are provided in both raw (rao) and converted (tao) formats
- The response is paginated with a default limit of 50 items per page
- Timestamps are provided in ISO 8601 format
- Both SS58 and hex formats are provided for addresses 