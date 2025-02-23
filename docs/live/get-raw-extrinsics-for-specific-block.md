# Live: Get Raw Extrinsics for Specific Block

Retrieves the raw extrinsics data from a specific block number on the Taostats network. This endpoint provides access to the unprocessed transaction data, useful for detailed blockchain analysis or custom processing needs.

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| block_number | int32 | Yes | The block number to retrieve raw extrinsics from |

## Response

The response includes the raw extrinsics data from the specified block in its original format from the blockchain.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/v1/live/blocks/{block_number}/extrinsics-raw"
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
| block_number | The block number the extrinsics were retrieved from |
| extrinsics[] | Array of raw extrinsic objects |
| extrinsics[].bytes | Hexadecimal representation of the raw extrinsic data |
| extrinsics[].hash | Hash of the extrinsic |
| extrinsics[].index | Index of the extrinsic within the block |

## Notes

- The block number must be a valid block that exists on the network
- Raw extrinsics are returned in their original encoded format from the blockchain
- This endpoint is useful for:
  - Custom transaction parsing and processing
  - Blockchain data analysis
  - Verification of transaction encoding
  - Low-level blockchain interaction
- Returns a 404 error if the specified block number does not exist
- The raw format provides maximum flexibility for custom processing needs
- Consider using the regular extrinsics endpoint if you need parsed and formatted data 