# Get Parent/Child Hotkey History

Retrieves historical information about parent/child relationships between validator hotkeys, including stake distribution and take rates over time.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | No | Filter by validator hotkey address | None |
| netuid | int32 | No | Filter by subnet ID | None |
| block_number | int32 | No | Filter by specific block number | None |
| block_start | int32 | No | Filter events after this block number | None |
| block_end | int32 | No | Filter events before this block number | None |
| timestamp_start | string | No | Start of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| timestamp_end | string | No | End of timestamp range in Unix timestamp (seconds since 1970-01-01) (inclusive) | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 50 |
| order | string | No | Sort order ('asc' or 'desc') | 'desc' |

## Response

The response includes pagination information and an array of historical validator records with their parent/child relationships and stake distribution.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/hotkey/family/history/v1"
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
| data[].hotkey.ss58 | Validator's SS58 formatted hotkey address |
| data[].hotkey.hex | Validator's hex formatted hotkey address |
| data[].coldkey.ss58 | Validator's SS58 formatted coldkey address |
| data[].coldkey.hex | Validator's hex formatted coldkey address |
| data[].block_number | Block number of the data |
| data[].timestamp | Timestamp of the data in ISO 8601 format |
| data[].netuid | Subnet ID where the validator is registered |
| data[].stake | Validator's direct stake |
| data[].family_stake | Total stake including children's stake |
| data[].take | Validator's take rate |
| data[].childkey_take | Take rate for child validators |
| data[].children | Array of child validator hotkeys |
| data[].parents | Array of parent validator hotkeys |
| data[].root_weight | Root weight in the validator hierarchy |
| data[].root_stake | Stake at the root level |
| data[].alpha_stake | Stake in alpha |
| data[].root_stake_as_alpha | Root stake converted to alpha |
| data[].total_alpha_stake | Total stake in alpha including all relationships |
| data[].family_root_stake | Total root stake for the family |
| data[].family_alpha_stake | Total alpha stake for the family |
| data[].family_root_stake_as_alpha | Family root stake converted to alpha |
| data[].family_total_alpha_stake | Total family stake in alpha |

## Notes

- All stake values are in TAO units (10^9)
- Take rates are expressed as decimal values between 0 and 1
- Timestamps are in ISO 8601 format
- The response is paginated with a default limit of 50 items per page
- Both SS58 and hex formats are provided for hotkey and coldkey addresses
- Family relationships include both parent and child validators
- Alpha stake represents stake in the alpha subnet 