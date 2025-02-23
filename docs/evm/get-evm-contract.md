# Get EVM Contract

Retrieves information about Ethereum Virtual Machine (EVM) contracts deployed on the Taostats network, with support for filtering by various parameters.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| address | string | No | Filter by contract address | None |
| owner | string | No | Filter by contract owner address | None |
| block_start | int32 | No | Filter contracts deployed after this block number | None |
| block_end | int32 | No | Filter contracts deployed before this block number | None |
| timestamp_start | int32 | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| timestamp_end | int32 | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| page | int32 | No | Page number for pagination | 0 |
| limit | int32 | No | Number of records per page | 50 |
| order | string | No | Sort order ('asc' or 'desc') | 'desc' |

## Response

The response includes pagination information and an array of EVM contract records.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/evm/contract/v1"
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
| data[].address | Contract address |
| data[].creator | Address that deployed the contract |
| data[].creation_transaction | Hash of the transaction that created the contract |
| data[].block_number | Block number when the contract was deployed |
| data[].timestamp | Timestamp of contract deployment |
| data[].bytecode | Contract bytecode |
| data[].abi | Contract ABI (if verified) |
| data[].name | Contract name (if verified) |
| data[].verified | Whether the contract is verified |
| data[].verification_date | Date when the contract was verified (if applicable) |
| data[].compiler_version | Solidity compiler version used (if verified) |
| data[].optimization | Whether compiler optimization was enabled (if verified) |
| data[].runs | Number of optimization runs (if optimization enabled) |
| data[].source_code | Contract source code (if verified) |
| data[].constructor_arguments | Arguments used in contract constructor |
| data[].implementation | Address of implementation contract (if proxy) |
| data[].is_proxy | Whether the contract is a proxy |

## Notes

- All addresses are in standard EVM hex format (0x...)
- Timestamps are in Unix timestamp format (seconds since epoch)
- The response is paginated with a default limit of 50 items per page
- Contract data can be filtered by:
  - Contract address
  - Owner/creator address
  - Deployment block range
  - Deployment timestamp range
- The ABI, source code, and other verification details are only available for verified contracts
- Bytecode is returned in hexadecimal format
- Constructor arguments are preserved for contract verification
- Proxy contracts will include a reference to their implementation contract
- The verification status helps identify contracts with available source code and documentation 