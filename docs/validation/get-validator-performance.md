# Get Validator Performance

Retrieves performance metrics for a specific validator on a given subnet, including emission rates, block updates, and tempo information.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | Yes | Validator hotkey address to query | None |
| netuid | int32 | Yes | Network/subnet ID | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 200 |
| order | string | No | Sort order ('asc' or 'desc') | 'desc' |

## Response

The response includes pagination information and an array of validator performance records.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/validator/performance/v1"
params = {
    "hotkey": "5CVS9d1NcQyWKUyadLevwGxg6LgBcF9Lik6NSnbe5q59jwhE",
    "netuid": 0
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
| pagination.current_page | Current page number |
| pagination.per_page | Number of items per page |
| pagination.total_items | Total number of items across all pages |
| pagination.total_pages | Total number of pages |
| pagination.next_page | Next page number (null if no next page) |
| pagination.prev_page | Previous page number (null if no previous page) |
| data[].netuid | Network/subnet ID |
| data[].hotkey | Validator's hotkey object containing SS58 and hex formats |
| data[].block_number | Block number when the performance was recorded |
| data[].timestamp | Timestamp of the performance record |
| data[].emission | Emission rate for the validator |
| data[].blocks_since_weight_set | Number of blocks since the last weight update |
| data[].update_status | Status of the validator's last update |
| data[].tempo | Validator's tempo (update frequency) |

## Notes

- Both `hotkey` and `netuid` parameters are required
- The response is paginated with a default limit of 200 items per page
- Performance metrics are specific to a validator's activity on a particular subnet
- Emission values are in TAO units
- Timestamps are in ISO 8601 format
- The update_status field indicates whether the validator is actively participating in the network
- Tempo represents the frequency at which the validator updates their weights 