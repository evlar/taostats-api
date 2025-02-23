# Live: Get Node Transaction Pool

Retrieves the current transaction pool from a live Taostats node. This endpoint provides information about pending transactions that have not yet been included in a block.

## Response

The response includes an array of pending transactions in the node's transaction pool.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/v1/live/node/transaction-pool"
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
| pool[] | Array of pending transactions |
| pool[].encodedExtrinsic | Hexadecimal encoded transaction data |
| pool[].hash | Unique hash of the transaction |
| pool[].partialFee | Partial fee for the transaction (if available) |
| pool[].priority | Transaction priority in the pool (if available) |
| pool[].tip | Additional tip added to the transaction (if available) |

## Notes

- The transaction pool represents transactions waiting to be included in future blocks
- Each transaction includes its raw encoded data and unique hash
- Optional fields like `partialFee`, `priority`, and `tip` may be null
- The pool size varies depending on network activity
- Transactions remain in the pool until:
  - They are included in a block
  - They expire
  - They are replaced by transactions with higher fees
  - They are deemed invalid
- This endpoint is useful for:
  - Monitoring pending transactions
  - Transaction fee estimation
  - Network activity analysis
  - Transaction confirmation tracking 