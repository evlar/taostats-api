# Get Block Number over Interval

Get block numbers at specific time intervals. This endpoint is useful for tracking block production over time.

```
GET https://api.taostats.io/api/block/interval/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| frequency | string | Yes | Frequency of intervals (e.g., 'by_day') | - |
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
      "timestamp": string (ISO 8601)
    }
  ]
}
```

## Example Request

```python
import requests

url = "https://api.taostats.io/api/block/interval/v1?frequency=by_day&page=1&limit=50"
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
| block_number | The block number at this interval |
| timestamp | The timestamp for this interval in ISO 8601 format |

## Notes

- Data is ordered by timestamp in descending order by default
- Timestamps are in ISO 8601 format with millisecond precision
- Results are paginated with a default of 50 records per page
- The frequency parameter determines the interval between data points (e.g., 'by_day' for daily intervals) 