# Get Historical Stake Balance

Retrieves historical stake balance information for a specific validator identified by their coldkey and hotkey addresses.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| coldkey | string | Yes | The validator's coldkey address in SS58 format | None |
| hotkey | string | Yes | The validator's hotkey address in SS58 format | None |
| netuid | int32 | Yes | The network/subnet ID | None |

## Response

The response includes an array of historical stake balance records, with each record containing block information, validator details, and balance data.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/dtao/stake_balance/history/v1"
params = {
    "coldkey": "5CGwW5WJ3ES7G7WJKtqsRwb2WANBH5u9PxhFTqvRpjWMpodz",
    "hotkey": "5HK5tp6t2S59DywmHRWPBVJeJ86T61KjurYqeooqj8sREpeN",
    "netuid": 64
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
| block_number | Block number when the balance was recorded |
| timestamp | ISO 8601 formatted timestamp of the block |
| hotkey_name | Name associated with the validator's hotkey |
| hotkey.ss58 | Validator's SS58 formatted hotkey address |
| hotkey.hex | Validator's hex formatted hotkey address |
| coldkey.ss58 | Validator's SS58 formatted coldkey address |
| coldkey.hex | Validator's hex formatted coldkey address |
| netuid | Network/subnet ID |
| balance | Raw balance value in rao |
| balance_as_tao | Balance converted to tao units |

## Notes

- Historical balance data is tracked per block for each validator
- Timestamps are provided in ISO 8601 format
- Both SS58 and hex formats are provided for addresses
- Balance values are provided in both raw (rao) and converted (tao) formats
- The hotkey_name field may be empty if no name is registered 