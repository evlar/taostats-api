# Get API Status

Returns the current status of the Taostats API, including version information and timestamp.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| None | - | - | - | - |

## Response
The endpoint returns a JSON object containing the API status information.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/status/v1', headers=headers)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| ok | Boolean indicating if the API is operational |
| version | Current version of the API |
| status.timestamp | ISO 8601 timestamp of when the status was checked |

## Notes
- This endpoint can be used to check if the API is operational and to get the current version
- The timestamp is provided in ISO 8601 format with UTC timezone
- Regular status checks are recommended for monitoring API availability 