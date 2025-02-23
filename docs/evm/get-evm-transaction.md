# Get EVM Transaction

Retrieves Ethereum Virtual Machine (EVM) transactions from the Taostats network, with support for filtering by various parameters.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| block_number | int32 | No | Filter by specific block number | None |
| block_start | int32 | No | Filter transactions after this block number | None |
| block_end | int32 | No | Filter transactions before this block number | None |
| timestamp_start | int32 | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| timestamp_end | int32 | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| hash | string | No | Filter by transaction hash | None |
| address | string | No | Filter by contract address | None |
| to | string | No | Filter by recipient address | None |
| from | string | No | Filter by sender address | None |
| method_name | string | No | Filter by method name | None |
| contract_created | string | No | Filter by created contract address | None |
| index | int32 | No | Filter by transaction index | None |
| page | int32 | No | Page number for pagination | 0 |
| limit | int32 | No | Number of records per page | 0 |
| order | string | No | Sort order ('asc' or 'desc') | None |

## Response

The response includes pagination information and an array of EVM transaction records.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/evm/transaction/v1"
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
| data[].hash | Transaction hash |
| data[].block_number | Block number containing the transaction |
| data[].timestamp | Transaction timestamp |
| data[].from | Sender's address |
| data[].to | Recipient's address |
| data[].value | Transaction value in wei |
| data[].gas_price | Gas price in wei |
| data[].gas_limit | Gas limit for the transaction |
| data[].gas_used | Actual gas used |
| data[].nonce | Transaction nonce |
| data[].index | Transaction index in the block |
| data[].input | Transaction input data |
| data[].method_name | Name of the called method (if a contract call) |
| data[].contract_created | Address of created contract (if a contract creation) |
| data[].status | Transaction status (success/failure) |
| data[].logs[] | Array of event logs |

## Notes

- All addresses are in standard EVM hex format (0x...)
- Timestamps are in Unix timestamp format (seconds since epoch)
- The response is paginated with configurable page size
- Transaction data can be filtered by:
  - Block number or block range
  - Timestamp range
  - Transaction hash
  - Addresses (from, to, contract)
  - Method name
  - Transaction index
- Gas values and transaction value are in wei (10^-18 ETH)
- Default pagination values (page and limit) are 0, which should be overridden as needed
- Method names are available for known contract interactions
- Contract creation transactions will have the created contract's address in contract_created field 