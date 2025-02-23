# Get Stake Balance

Retrieves the current stake balance information for validators across different subnets, including both raw balance and TAO-denominated values.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| coldkey | string | No | Filter by stakeholder's coldkey address | None |
| hotkey | string | No | Filter by validator's hotkey address | None |
| netuid | int32 | No | Filter by subnet ID | None |
| balance_min | string | No | Filter by minimum balance in nanoTAO | None |
| balance_max | string | No | Filter by maximum balance in nanoTAO | None |
| balance_as_tao_min | string | No | Filter by minimum balance in TAO | None |
| balance_as_tao_max | string | No | Filter by maximum balance in TAO | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 50 |
| order | string | No | Sort order ('asc' or 'desc') | 'desc' |

## Response

The response includes pagination information and an array of stake balance records.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/dtao/stake_balance/latest/v1"
headers = {
    "accept": "application/json",
    "Authorization": "YOUR-API-KEY"
}
params = {
    "coldkey": "5HTfxx3oXmZPPVrTNeBgwNjTaDLMYvJ72eB8JqRJPW7Suja3"
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
| data[].block_number | Block number when the balance was recorded |
| data[].timestamp | Timestamp of the balance record |
| data[].hotkey_name | Name of the validator (if set) |
| data[].hotkey.ss58 | Validator's SS58 formatted hotkey address |
| data[].hotkey.hex | Validator's hex formatted hotkey address |
| data[].coldkey.ss58 | Stakeholder's SS58 formatted coldkey address |
| data[].coldkey.hex | Stakeholder's hex formatted coldkey address |
| data[].netuid | Subnet ID where the stake is allocated |
| data[].subnet_rank | Validator's rank in the subnet |
| data[].balance | Raw balance amount in nanoTAO |
| data[].balance_as_tao | Balance converted to TAO units |

## Notes

- All balance values are provided in both nanoTAO (raw) and TAO units
- Timestamps are in ISO 8601 format
- The response is paginated with a default limit of 50 items per page
- Both SS58 and hex formats are provided for addresses
- Balance data can be filtered by:
  - Coldkey address (stakeholder)
  - Hotkey address (validator)
  - Subnet ID
  - Balance ranges (in both nanoTAO and TAO)
- Subnet rank indicates the validator's position in their subnet
- The hotkey_name field may be null if no name has been set
- Balance values are strings to maintain numerical precision 