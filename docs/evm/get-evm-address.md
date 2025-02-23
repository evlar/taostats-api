# Get EVM Address

Converts a Substrate SS58 address to its corresponding Ethereum Virtual Machine (EVM) address format. This endpoint is useful for cross-chain operations and address format conversions.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| ss58_address | string | Yes | The SS58-formatted address to convert | None |

## Response

The response includes the converted EVM address.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/evm/address_from_ss58/v1"
headers = {
    "accept": "application/json",
    "Authorization": "YOUR-API-KEY"
}
params = {
    "ss58_address": "5CVS9d1NcQyWKUyadLevwGxg6LgBcF9Lik6NSnbe5q59jwhE"
}

response = requests.get(url, headers=headers, params=params)
print(response.text)
```

## Response Fields

| Field | Description |
|-------|-------------|
| address | The converted EVM address in hex format (0x...) |
| original_ss58 | The original SS58 address that was converted |

## Notes

- The input SS58 address must be a valid Substrate address format
- The output EVM address is returned in standard hex format with '0x' prefix
- This endpoint is useful for:
  - Cross-chain operations between Substrate and EVM chains
  - Address format conversion for compatibility
  - Mapping between SS58 and EVM address spaces
- The conversion is deterministic - the same SS58 address will always yield the same EVM address
- Returns a 400 error if the provided SS58 address is invalid
- The conversion preserves the account identity across different address formats 