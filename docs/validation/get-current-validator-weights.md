# Get Current Validator Weights

Retrieves the current weights set by validators for their peers in the network, including version information and weight distributions.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | No | Filter by validator hotkey address | None |
| netuid | int32 | No | Filter by subnet ID | None |
| version_key | string | No | Filter by version key | None |
| call | string | No | Filter by call type (e.g., 'reveal_crv3_weights') | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 50 |

## Response

The response includes pagination information and an array of validator weight records.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/validator/weights/latest/v1"
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
| pagination.current_page | Current page number |
| pagination.per_page | Number of items per page |
| pagination.total_items | Total number of items across all pages |
| pagination.total_pages | Total number of pages |
| pagination.next_page | Next page number (null if no next page) |
| pagination.prev_page | Previous page number (null if no previous page) |
| data[].hotkey.ss58 | Validator's SS58 formatted hotkey address |
| data[].hotkey.hex | Validator's hex formatted hotkey address |
| data[].netuid | Subnet ID where the weights are set |
| data[].uid | Validator's unique identifier in the subnet |
| data[].block_number | Block number when the weights were set |
| data[].timestamp | Timestamp of the weight setting in ISO 8601 format |
| data[].version_key | Version key of the weights (if applicable) |
| data[].call | Type of call used to set weights (e.g., 'reveal_crv3_weights') |
| data[].weights_hash | Hash of the weights (if applicable) |
| data[].reveal_round | Round number of the weight reveal (if applicable) |
| data[].weights | Array of weight objects |
| data[].weights[].uid | Target validator's unique identifier |
| data[].weights[].weight | Weight assigned to the target validator (0-1) |

## Notes

- Weights are expressed as decimal values between 0 and 1
- Timestamps are in ISO 8601 format
- The response is paginated with a default limit of 50 items per page
- Both SS58 and hex formats are provided for hotkey addresses
- Weight values represent the trust or importance a validator assigns to other validators in the network
- The `weights` array contains entries for all validators in the subnet, even if they have zero weight
- The `call` field typically indicates the mechanism used to submit weights (e.g., 'reveal_crv3_weights')
- Weight distributions may vary by subnet and validator strategy 