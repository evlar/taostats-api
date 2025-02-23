# Live: Get Latest Block Extrinsics

Retrieves the extrinsics (blockchain transactions) from the most recent block on the Taostats network. This endpoint provides real-time access to the latest block's transactions, events, and metadata.

## Response

The response includes detailed information about the latest block, including all extrinsics, events, and block metadata.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/v1/live/blocks/head"
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
| authorId | Block author's identifier (if available) |
| extrinsicRoot | Root hash of all extrinsics in the block |
| extrinsics[] | Array of extrinsics in the block |
| extrinsics[].args | Arguments passed to the extrinsic |
| extrinsics[].era | Era information (mortal or immortal) |
| extrinsics[].events[] | Array of events triggered by the extrinsic |
| extrinsics[].hash | Unique hash of the extrinsic |
| extrinsics[].method | Called method information (pallet and method name) |
| extrinsics[].nonce | Transaction nonce (if applicable) |
| extrinsics[].signature | Transaction signature details (if signed) |
| extrinsics[].success | Whether the extrinsic executed successfully |
| finalized | Whether the block is finalized |
| hash | Block hash |
| logs[] | Array of block logs |
| number | Block number |
| parentHash | Hash of the parent block |
| stateRoot | Root hash of the state after block execution |

## Notes

- This endpoint returns information about the most recent block on the network
- The response structure is identical to the block range endpoint but only returns a single block
- Each extrinsic contains detailed information about the transaction, its parameters, and resulting events
- Events provide information about state changes caused by the extrinsic
- The response includes both successful and failed transactions
- Block metadata includes important hashes and verification information
- Some fields may be null depending on the type of extrinsic
- The block may not be finalized at the time of the request
- This endpoint is useful for real-time monitoring of network activity 