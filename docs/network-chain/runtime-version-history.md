# Get Historical Runtime Version

Get the history of runtime version changes in the Bittensor network.

```
GET https://api.taostats.io/api/runtime_version/history/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| block_start | integer | No | Start of block range | - |
| block_end | integer | No | End of block range | - |
| timestamp_start | integer | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| timestamp_end | integer | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| page | integer | No | Page number for pagination | 1 |
| limit | integer | No | Number of records per page | 50 |
| order | string | No | Sort order for results | - |

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

url = "https://api.taostats.io/api/runtime_version/history/v1"
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
| block_number | The block number when this runtime version was activated |
| timestamp | When this runtime version was activated (ISO 8601 format) |
| runtime_version | The runtime version number |

## Notes

- Data is ordered by block number in descending order by default
- Each record represents a change in the runtime version
- Runtime versions are incremented when there are changes to the blockchain's runtime logic
- The runtime version is used to determine compatibility between nodes and the network
- Historical data is available from the network's inception
- Use the timestamp or block range parameters to filter the history to a specific time period 