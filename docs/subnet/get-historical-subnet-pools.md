# Get Historical Subnet Pools

Returns historical information about subnet pools over a specified time period or block range, including token metrics, market data, and trading activity.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | false | Filter by Network/Subnet ID | - |
| block_number | int32 | false | Filter by specific block number | - |
| block_start | int32 | false | Starting block number | - |
| block_end | int32 | false | Ending block number | - |
| timestamp_start | int64 | false | Start timestamp (Unix timestamp in seconds since 1970-01-01) | - |
| timestamp_end | int64 | false | End timestamp (Unix timestamp in seconds since 1970-01-01) | - |
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order for results | 'block_number_desc' |

## Response
The endpoint returns a paginated list of historical subnet pool states with their market metrics and trading activity.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

params = {
    'netuid': 1,
    'block_start': 4000000,
    'block_end': 4100000,
    'page': 1,
    'limit': 50
}

response = requests.get('https://api.taostats.io/api/dtao/pool/history/v1', headers=headers, params=params)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| netuid | Network/Subnet ID |
| block_number | Block number when the data was recorded |
| timestamp | ISO 8601 timestamp of the block |
| name | Name of the subnet token |
| symbol | Symbol of the subnet token |
| market_cap | Total market capitalization at this point (as string) |
| liquidity | Total liquidity in the pool at this point (as string) |
| total_tao | Total TAO tokens in the pool |
| total_alpha | Total Alpha tokens in the pool |
| alpha_in_pool | Amount of Alpha tokens in the liquidity pool |
| alpha_staked | Amount of Alpha tokens staked |
| price | Price of Alpha in TAO at this point |
| tao_volume_24_hr | Trading volume in TAO for previous 24 hours |
| tao_buy_volume_24_hr | Buy volume in TAO for previous 24 hours |
| tao_sell_volume_24_hr | Sell volume in TAO for previous 24 hours |
| buys_24_hr | Number of buy transactions in previous 24 hours |
| sells_24_hr | Number of sell transactions in previous 24 hours |
| buyers_24_hr | Number of unique buyers in previous 24 hours |
| sellers_24_hr | Number of unique sellers in previous 24 hours |

## Notes
- All numerical values are returned as strings to maintain precision
- You can filter by either block range or timestamp range, but not both simultaneously
- Historical data includes:
  - Market metrics (price, market cap, liquidity)
  - Token distribution (pool tokens, staked tokens)
  - Trading activity (volume, transactions, participants)
- The endpoint is useful for:
  - Analyzing price trends over time
  - Tracking liquidity changes
  - Monitoring trading activity patterns
  - Understanding token distribution changes
- 24-hour metrics at each historical point provide context for:
  - Trading volume trends
  - User participation patterns
  - Market activity levels
- When using timestamp filters:
  - Timestamps should be in Unix format (seconds since epoch)
  - Both start and end timestamps are inclusive
  - The maximum time range may be limited to prevent excessive data retrieval 