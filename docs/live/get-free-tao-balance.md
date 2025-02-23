# Live: Get Free Tao Balance

Retrieves the current free TAO balance and account information from a live Taostats node. This endpoint provides real-time balance information directly from the blockchain.

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| address | string | Yes | The SS58 address to check the balance for |

## Response

The response includes detailed account information including free balance, frozen amounts, locks, and nonce.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/v1/live/accounts/{address}/balance-info"
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
| at.hash | Block hash at which the balance was checked |
| at.height | Block height at which the balance was checked |
| feeFrozen | Amount frozen for fees (may not exist in current runtime) |
| free | Free balance amount in nanoTAO units |
| frozen | Total amount frozen |
| locks | Array of account locks |
| miscFrozen | Miscellaneous frozen amount (may not exist in current runtime) |
| nonce | Account transaction nonce |
| reserved | Reserved balance amount |
| tokenSymbol | Token symbol (always "TAO") |

## Notes

- Balance values are in nanoTAO units (10^9)
- This endpoint queries the live blockchain node directly
- The free balance represents the available balance that can be transferred or used
- Frozen and reserved balances indicate amounts that are locked or set aside
- The nonce indicates the number of transactions sent from this account
- Some fields like `feeFrozen` and `miscFrozen` may not exist in the current runtime
- The response includes the block hash and height to help track when the balance was retrieved
- This endpoint is useful for real-time balance monitoring and detailed account information 