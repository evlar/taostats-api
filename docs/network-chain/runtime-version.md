# Get Runtime Version

Get the latest runtime version of the Bittensor network.

```
GET https://api.taostats.io/api/runtime_version/latest/v1
```

## Query Parameters

No query parameters are required for this endpoint.

## Response

A successful response returns HTTP 200 status code with the following JSON structure:

```json
{
  "pagination": {
    "current_page": integer,
    "per_page": integer,
    "total_items": integer,
    "total_pages": integer,
    "next_page": integer|null,
    "prev_page": integer|null
  },
  "data": [
    {
      "block_number": integer,
      "timestamp": string (ISO 8601),
      "runtime_version": integer
    }
  ]
}
```

## Example Request

```python
import requests

url = "https://api.taostats.io/api/runtime_version/latest/v1"
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
| block_number | The block number when this runtime version was captured |
| timestamp | When this runtime version was captured (ISO 8601 format) |
| runtime_version | The current runtime version number |

## Notes

- This endpoint always returns a single record with the latest runtime version
- Runtime versions are incremented when there are changes to the blockchain's runtime logic
- The runtime version is used to determine compatibility between nodes and the network
- Historical runtime versions can be queried using the Get Historical Runtime Version endpoint 