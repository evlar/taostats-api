# Live: Get Extrinsics for Specific Block

Retrieves all extrinsics (blockchain transactions) from a specific block number on the Taostats network. This endpoint provides detailed information about transactions, events, and block metadata for a particular block.

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| block_number | int32 | Yes | The block number to retrieve extrinsics from |

## Response

The response includes detailed information about the specified block, including all extrinsics, events, and block metadata.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/v1/live/blocks/{block_number}"
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

- The block number must be a valid block that exists on the network
- The response structure is identical to the block range and latest block endpoints
- Each extrinsic contains detailed information about the transaction, its parameters, and resulting events
- Events provide information about state changes caused by the extrinsic
- The response includes both successful and failed transactions
- Block metadata includes important hashes and verification information
- Some fields may be null depending on the type of extrinsic
- This endpoint is useful for historical analysis of specific blocks
- Returns a 404 error if the specified block number does not exist 