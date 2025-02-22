# Get Subnet Registrations

Returns information about subnet registration events, including registration costs, recycled amounts, and the addresses involved in the registration process.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | false | Filter by Network/Subnet ID | - |
| owner | string | false | Filter by owner address (SS58 format) | - |
| registered_by | string | false | Filter by registering address (SS58 format) | - |
| block_number | int32 | false | Filter by specific block number | - |
| block_start | int32 | false | Starting block number | - |
| block_end | int32 | false | Ending block number | - |
| timestamp_start | int64 | false | Start timestamp (Unix timestamp in seconds since 1970-01-01) | - |
| timestamp_end | int64 | false | End timestamp (Unix timestamp in seconds since 1970-01-01) | - |
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order ('asc' or 'desc') | 'desc' |

## Response
The endpoint returns a paginated list of subnet registration events with detailed information about each registration.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/subnet/registration/v1', headers=headers)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| block_number | Block number when the registration occurred |
| timestamp | ISO 8601 timestamp of the block |
| netuid | Network/Subnet ID where the registration occurred |
| registration_cost | Cost paid for registration (as string) |
| recycled_at_registration | Amount recycled during registration (as string) |
| owner.ss58 | Owner's address in SS58 format |
| owner.hex | Owner's address in hexadecimal format |
| registered_by.ss58 | Registering address in SS58 format |
| registered_by.hex | Registering address in hexadecimal format |

## Notes
- All numerical values (costs, recycled amounts) are returned as strings to maintain precision
- The costs are denominated in TAO tokens (in billionths)
- The endpoint provides information about:
  - Registration timing and location (block, timestamp, subnet)
  - Associated costs and recycling
  - Ownership and registration authority
- You can filter registrations by:
  - Specific subnet ID (netuid)
  - Owner address
  - Registering address
  - Block range or timestamp range
- The response includes both SS58 and hexadecimal formats for addresses
- The owner and registered_by addresses may be:
  - The same (self-registration)
  - Different (registration by another party)
- The recycled_at_registration field shows:
  - Amount of TAO recycled during registration
  - May be "0" if no recycling occurred
- This endpoint is useful for:
  - Tracking subnet growth
  - Monitoring registration patterns
  - Analyzing registration costs
  - Understanding recycling behavior
  - Identifying registration authorities 