# Get Event

Get events emitted by the blockchain, including system events, transaction results, and module-specific events.

```
GET https://api.taostats.io/api/event/v1
```

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| block_number | integer | No | Filter by specific block number | - |
| block_start | integer | No | Start of block range | - |
| block_end | integer | No | End of block range | - |
| timestamp_start | integer | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| timestamp_end | integer | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) | - |
| pallet | string | No | Filter by pallet name (e.g., 'System', 'Balances') | - |
| phase | string | No | Filter by event phase | - |
| name | string | No | Filter by event name | - |
| full_name | string | No | Filter by full event name (format: "Pallet.EventName") | - |
| extrinsic_id | string | No | Filter by extrinsic ID | - |
| call_id | string | No | Filter by call ID | - |
| id | string | No | Filter by event ID | - |
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
      "id": string,
      "extrinsic_index": integer,
      "index": integer,
      "phase": string,
      "pallet": string,
      "name": string,
      "full_name": string,
      "args": object,
      "block_number": integer,
      "extrinsic_id": string,
      "call_id": string|null,
      "timestamp": string (ISO 8601)
    }
  ]
}
```

## Example Request

```python
import requests

url = "https://api.taostats.io/api/event/v1?limit=50"
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
| id | Unique identifier for the event (format: "{block_number}-{index}") |
| extrinsic_index | Index of the extrinsic that emitted this event |
| index | Index of this event within its block |
| phase | Phase when the event was emitted (e.g., "ApplyExtrinsic") |
| pallet | Name of the pallet that emitted the event |
| name | Name of the event |
| full_name | Full name of the event (format: "Pallet.EventName") |
| args | Arguments/data associated with the event |
| block_number | The block number containing this event |
| extrinsic_id | ID of the extrinsic that emitted this event |
| call_id | ID of the specific call that emitted this event (null for system events) |
| timestamp | When the event was emitted (ISO 8601 format) |

## Notes

- Events are ordered by block number and index in descending order by default
- Timestamps are in ISO 8601 format
- The `args` structure varies depending on the event type
- Common event types include:
  - System.ExtrinsicSuccess: Indicates successful extrinsic execution
  - System.ExtrinsicFailed: Indicates failed extrinsic execution with error details
  - TransactionPayment.TransactionFeePaid: Details about transaction fees
  - Module-specific events (e.g., Balances.Transfer, SubtensorModule.StakeRemoved) 