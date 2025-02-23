# Get dTao Delegation Events

Retrieves a paginated list of dTao delegation events, including both delegate and undelegate actions.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | No | Filter by validator hotkey (delegate or nominator) | None |
| coldkey | string | No | Filter by coldkey (delegate or nominator) | None |
| netuid | int32 | No | Filter by network/subnet ID | None |
| block_number | int32 | No | Filter by specific block number | None |
| block_start | int32 | No | Filter events after this block number | None |
| block_end | int32 | No | Filter events before this block number | None |
| timestamp_start | string | No | Filter events after this timestamp (ISO 8601) | None |
| timestamp_end | string | No | Filter events before this timestamp (ISO 8601) | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 50 |
| order | string | No | Sort order ('asc' or 'desc') | 'desc' |

## Response

The response includes pagination information and an array of delegation events.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/delegation/v1"
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
| pagination.current_page | Current page number |
| pagination.per_page | Number of items per page |
| pagination.total_items | Total number of items across all pages |
| pagination.total_pages | Total number of pages |
| pagination.next_page | Next page number (null if no next page) |
| pagination.prev_page | Previous page number (null if no previous page) |
| data[].id | Unique identifier for the delegation event |
| data[].block_number | Block number when the event occurred |
| data[].timestamp | Timestamp of the event in ISO 8601 format |
| data[].action | Type of action ("DELEGATE" or "UNDELEGATE") |
| data[].nominator.ss58 | Nominator's SS58 address |
| data[].nominator.hex | Nominator's hex address |
| data[].delegate.ss58 | Delegate's SS58 address |
| data[].delegate.hex | Delegate's hex address |
| data[].amount | Amount of TAO delegated/undelegated |
| data[].alpha | Amount of alpha |
| data[].usd | USD value at the time of the event |
| data[].alpha_price_in_tao | Alpha price in TAO at the time of the event |
| data[].alpha_price_in_usd | Alpha price in USD at the time of the event |
| data[].netuid | Network/subnet ID |
| data[].extrinsic_id | Extrinsic ID of the event |

## Notes

- The endpoint supports filtering delegation events by various parameters including hotkey, coldkey, network ID, and time range
- Timestamps should be provided in ISO 8601 format
- The response includes both the SS58 and hex formats for addresses
- USD values and prices are included for historical reference
- Results are paginated with a default limit of 50 items per page 