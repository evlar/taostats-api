# Get Subnet Registration Cost

Returns the current registration cost required to register a neuron in a subnet.

## Query Parameters
None - This endpoint returns the latest registration cost without any filtering parameters.

## Response
The endpoint returns the current registration cost with associated block information.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/subnet/registration_cost/latest/v1', headers=headers)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| block_number | Block number when the registration cost was recorded |
| timestamp | ISO 8601 timestamp of the block |
| registration_cost | Current cost to register a neuron (as string) |

## Notes
- The registration cost is returned as a string to maintain numerical precision
- The cost is denominated in TAO tokens (in billionths)
- The endpoint returns the most recent registration cost from the latest block
- Registration costs can change over time based on:
  - Network demand
  - Subnet policies
  - Difficulty adjustments
- The response includes:
  - The exact block number when the cost was recorded
  - A precise timestamp for the cost data
  - The current registration cost value
- This endpoint is useful for:
  - Planning neuron registrations
  - Monitoring registration costs
  - Understanding subnet entry requirements
  - Tracking cost changes over time (when combined with historical data)
- The response is paginated but typically only returns a single record
  representing the current registration cost 