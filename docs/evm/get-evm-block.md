# Get EVM Block

Retrieves Ethereum Virtual Machine (EVM) blocks from the Taostats network, with support for filtering by various parameters.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| block_number | int32 | No | Filter by specific block number | None |
| block_start | int32 | No | Filter blocks after this block number | None |
| block_end | int32 | No | Filter blocks before this block number | None |
| timestamp_start | int32 | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| timestamp_end | int32 | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| hash | string | No | Filter by block hash | None |
| page | int32 | No | Page number for pagination | 0 |
| limit | int32 | No | Number of records per page | 50 |
| order | string | No | Sort order ('asc' or 'desc') | 'desc' |

## Response

The response includes pagination information and an array of EVM block records.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/evm/block/v1"
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
| data[].hash | Block hash |
| data[].number | Block number |
| data[].timestamp | Block timestamp |
| data[].parent_hash | Hash of the parent block |
| data[].nonce | Block nonce |
| data[].sha3_uncles | Hash of the block's uncles |
| data[].logs_bloom | Bloom filter for the logs |
| data[].transactions_root | Root hash of the transaction trie |
| data[].state_root | Root hash of the state trie |
| data[].receipts_root | Root hash of the receipts trie |
| data[].miner | Address of the miner who mined the block |
| data[].difficulty | Block difficulty |
| data[].total_difficulty | Total chain difficulty at this block |
| data[].size | Block size in bytes |
| data[].extra_data | Extra data field |
| data[].gas_limit | Block gas limit |
| data[].gas_used | Total gas used in the block |
| data[].transaction_count | Number of transactions in the block |
| data[].base_fee_per_gas | Base fee per gas unit |

## Notes

- All hashes are in standard EVM hex format (0x...)
- Timestamps are in Unix timestamp format (seconds since epoch)
- The response is paginated with a default limit of 50 items per page
- Block data can be filtered by:
  - Block number or block range
  - Timestamp range
  - Block hash
- Gas values are in wei (10^-18 ETH)
- The base_fee_per_gas field is only present for blocks after EIP-1559
- Transaction_count represents the number of transactions included in the block
- Difficulty and total_difficulty are important for understanding the mining process
- The logs_bloom field can be used to efficiently search for logs 