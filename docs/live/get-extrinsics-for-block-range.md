# Live: Get Extrinsics for Block Range

Retrieves all extrinsics (blockchain transactions) within a specified block range from a live Taostats node. This endpoint provides detailed information about transactions, including their parameters, events, and execution status.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| block_start | int32 | Yes | Starting block number (inclusive) | None |
| block_end | int32 | Yes | Ending block number (inclusive) | None |

## Response

The response includes an array of blocks, with each block containing its extrinsics, events, and metadata.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/v1/live/blocks"
params = {
    "block_start": 4991000,
    "block_end": 4991001
}
headers = {
    "accept": "application/json",
    "Authorization": "YOUR-API-KEY"
}

response = requests.get(url, headers=headers, params=params)
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

- Block range is inclusive of both start and end blocks
- Each extrinsic contains detailed information about the transaction, its parameters, and resulting events
- Events provide information about state changes caused by the extrinsic
- The response includes both successful and failed transactions
- Block metadata includes important hashes and verification information
- Some fields may be null depending on the type of extrinsic
- Timestamps in the response are in Unix timestamp format (milliseconds since epoch)
- Large block ranges may result in significant response sizes 