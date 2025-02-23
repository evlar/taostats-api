# Live: Get Pallet Consts

Retrieves the constant values defined in a specific pallet (module) from the Taostats blockchain. This endpoint provides access to the runtime constants that are defined within the specified pallet.

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| pallet_id | string | Yes | The identifier of the pallet (module) to retrieve constants from |

## Example Request

```python
import requests

url = "https://api.taostats.io/api/v1/live/pallets/{pallet_id}/consts"
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
| constants[] | Array of constant definitions |
| constants[].name | Name of the constant |
| constants[].type | Data type of the constant |
| constants[].value | Value of the constant |
| constants[].documentation | Description or documentation of the constant's purpose |

## Notes

- The pallet_id must be a valid pallet name in the runtime
- Constants are immutable values defined in the blockchain runtime
- Common pallet constants might include:
  - Fee parameters
  - Time intervals
  - Threshold values
  - System limits
  - Configuration values
- This endpoint is useful for:
  - Understanding blockchain parameters
  - Smart contract development
  - Network analysis
  - Integration testing
- Returns a 404 error if the specified pallet does not exist
- Returns a 500 error if there's an issue retrieving the constants
- The response structure may vary depending on the specific pallet and its defined constants 