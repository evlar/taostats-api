# Live: Get Pallet Consts by Id

Retrieves a specific constant value by its ID from a specified pallet (module) in the Taostats blockchain. This endpoint provides targeted access to individual runtime constants.

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| pallet_id | string | Yes | The identifier of the pallet (module) containing the constant |
| id | string | Yes | The identifier of the specific constant to retrieve |

## Example Request

```python
import requests

url = "https://api.taostats.io/api/v1/live/pallets/{pallet_id}/consts/{id}"
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
| name | Name of the constant |
| type | Data type of the constant |
| value | Value of the constant |
| documentation | Description or documentation of the constant's purpose |

## Notes

- Both pallet_id and id must be valid identifiers in the runtime
- This endpoint returns a single constant rather than an array of all constants
- Useful for when you need to monitor or retrieve a specific blockchain parameter
- Common use cases include:
  - Retrieving specific fee parameters
  - Checking configuration values
  - Verifying system limits
  - Reading network parameters
- Returns a 404 error if either:
  - The specified pallet does not exist
  - The specified constant id does not exist in the pallet
- The value format in the response depends on the constant's type
- More efficient than retrieving all constants when only one is needed 