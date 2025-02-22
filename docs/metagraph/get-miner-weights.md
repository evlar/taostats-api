# Get Miner Weights

Returns historical information about the weights assigned between miners and validators in the network, showing how validators score and weight different miners over time.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | true | Network/Subnet ID | - |
| miner_uid | int32 | false | Filter by miner's neuron ID | - |
| validator_uid | int32 | false | Filter by validator's neuron ID | - |
| block_number | int32 | false | Filter by specific block number | - |
| block_start | int32 | false | Starting block number | - |
| block_end | int32 | false | Ending block number | - |
| timestamp_start | int64 | false | Start timestamp (Unix timestamp in seconds) | - |
| timestamp_end | int64 | false | End timestamp (Unix timestamp in seconds) | - |
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of historical weight assignments between miners and validators in the network.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

params = {
    'netuid': 1,  # Required: specify the subnet ID
    'limit': 50
}

response = requests.get('https://api.taostats.io/api/miner/weights/history/v1', headers=headers, params=params)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| block_number | Block number when the weight was recorded |
| timestamp | ISO 8601 timestamp of the block |
| netuid | Network/Subnet ID |
| miner_uid | Neuron ID of the miner being weighted |
| validator_uid | Neuron ID of the validator assigning the weight |
| weight | Weight value assigned by validator to miner (as string) |

## Notes
- All weight values are returned as strings to maintain numerical precision
- Weights typically range from 0 to 1, representing the validator's trust in the miner
- You can filter weights by either block range or timestamp range, but not both simultaneously
- The endpoint supports filtering by both miner and validator UIDs to track specific relationships
- Pagination is implemented using the standard format with current_page, per_page, total_items, total_pages, next_page, and prev_page
- Historical weight data can be useful for analyzing:
  - Validator scoring patterns
  - Miner performance over time
  - Network trust relationships
  - Changes in validator preferences
- Weight values influence reward distribution and consensus mechanisms in the network 