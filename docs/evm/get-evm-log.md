# Get EVM Log

Retrieves event logs from Ethereum Virtual Machine (EVM) transactions on the Taostats network, with support for filtering by various parameters.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| block_number | int32 | No | Filter by specific block number | None |
| block_start | int32 | No | Filter logs after this block number | None |
| block_end | int32 | No | Filter logs before this block number | None |
| timestamp_start | int32 | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| timestamp_end | int32 | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| transaction_hash | string | No | Filter by transaction hash | None |
| address | string | No | Filter by contract address | None |
| event_name | string | No | Filter by event name | None |
| topic0 | string | No | Filter by first topic (event signature) | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 50 |
| order | string | No | Sort order ('asc' or 'desc') | 'desc' |

## Response

The response includes pagination information and an array of EVM event log records.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/evm/log/v1"
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
| data[].address | Contract address that generated the log |
| data[].block_number | Block number containing the log |
| data[].block_hash | Hash of the block |
| data[].transaction_hash | Hash of the transaction |
| data[].transaction_index | Index of the transaction in the block |
| data[].log_index | Index of the log in the transaction |
| data[].timestamp | Timestamp when the log was created |
| data[].removed | Whether the log was removed due to chain reorganization |
| data[].topics | Array of topics (indexed parameters) |
| data[].data | ABI-encoded log data |
| data[].event_name | Name of the event (if known) |
| data[].event_signature | Event signature hash |
| data[].decoded_data | Object containing decoded log parameters (if ABI is known) |

## Notes

- All addresses and hashes are in standard EVM hex format (0x...)
- Timestamps are in Unix timestamp format (seconds since epoch)
- The response is paginated with a default limit of 50 items per page
- Log data can be filtered by:
  - Block number or block range
  - Timestamp range
  - Transaction hash
  - Contract address
  - Event name
  - Topic (event signature)
- Topics array contains indexed event parameters:
  - topics[0] is always the event signature (keccak256 hash of the event name and parameter types)
  - topics[1+] contain indexed parameters in order
- The data field contains non-indexed parameters encoded according to the event ABI
- Decoded data is only available for known event signatures
- Event names are available for common/known contract events
- Logs marked as removed should be handled appropriately in applications 