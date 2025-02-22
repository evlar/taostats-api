# Get Current Subnet Pools

Returns detailed information about the current state of subnet pools, including token metrics, market data, and trading activity.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | int32 | false | Filter by Network/Subnet ID | - |
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |
| order | string | false | Sort order for results | 'rank_desc' |

### Available Order Options
- Ranking: `rank_asc`, `rank_desc`
- Network ID: `netuid_asc`, `netuid_desc`
- Price: `price_asc`, `price_desc`
- Price Changes:
  - Hourly: `price_change_one_hour_asc`, `price_change_one_hour_desc`
  - Daily: `price_change_one_day_asc`, `price_change_one_day_desc`
  - Weekly: `price_change_one_week_asc`, `price_change_one_week_desc`
- Market Metrics:
  - Market Cap: `market_cap_asc`, `market_cap_desc`
  - Volume: `tao_volume_one_day_asc`, `tao_volume_one_day_desc`
- Token Balances:
  - TAO: `total_tao_asc`, `total_tao_desc`
  - Alpha: `total_alpha_asc`, `total_alpha_desc`
  - Pool Alpha: `alpha_in_pool_asc`, `alpha_in_pool_desc`
  - Staked Alpha: `alpha_staked_asc`, `alpha_staked_desc`

## Response
The endpoint returns a paginated list of subnet pools with their current market metrics and trading activity.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

params = {
    'netuid': 1,
    'order': 'rank_desc'
}

response = requests.get('https://api.taostats.io/api/dtao/pool/latest/v1', headers=headers, params=params)
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
| rank | Current ranking position |
| market_cap | Total market capitalization (as string) |
| liquidity | Total liquidity in the pool (as string) |
| total_tao | Total TAO tokens in the pool |
| total_alpha | Total Alpha tokens in the pool |
| alpha_in_pool | Amount of Alpha tokens in the liquidity pool |
| alpha_staked | Amount of Alpha tokens staked |
| price | Current price of Alpha in TAO |
| price_change_1_hour | Percentage price change in last hour |
| price_change_1_day | Percentage price change in last 24 hours |
| price_change_1_week | Percentage price change in last 7 days |
| tao_volume_24_hr | Total trading volume in TAO for last 24 hours |
| tao_buy_volume_24_hr | Buy volume in TAO for last 24 hours |
| tao_sell_volume_24_hr | Sell volume in TAO for last 24 hours |
| buys_24_hr | Number of buy transactions in last 24 hours |
| sells_24_hr | Number of sell transactions in last 24 hours |
| buyers_24_hr | Number of unique buyers in last 24 hours |
| sellers_24_hr | Number of unique sellers in last 24 hours |
| seven_day_prices | Array of historical price data points for the last 7 days |

### Seven Day Prices Object
| Field | Description |
|-------|-------------|
| block_number | Block number for this price point |
| timestamp | ISO 8601 timestamp |
| price | Price at this point in time |

## Notes
- All numerical values are returned as strings to maintain precision
- Price changes are represented as percentage values
- The seven_day_prices array provides daily price points for trend analysis
- Trading metrics (volume, transactions, participants) are tracked over 24-hour periods
- Market metrics include:
  - Total liquidity and market capitalization
  - Trading volume broken down by buy/sell activity
  - Number of unique traders and transactions
- Token metrics show distribution between:
  - Tokens in liquidity pools
  - Tokens being staked
  - Total token supply
- The endpoint provides comprehensive data for:
  - Market analysis
  - Trading activity monitoring
  - Liquidity tracking
  - Price trend analysis 