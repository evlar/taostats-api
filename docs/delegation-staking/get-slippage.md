# Get Slippage

Returns the slippage information for token conversions between TAO and α (alpha).

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| netuid | integer | true | Network/Subnet ID | - |
| input_tokens | string | true | Amount of tokens (in billionths of tao/alpha) | - |
| direction | string | false | Direction of conversion ('tao_to_alpha' or 'alpha_to_tao') | 'tao_to_alpha' |

## Response
The endpoint returns slippage calculation details for token conversions.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

params = {
    'netuid': 64,
    'input_tokens': '1000000000',
    'direction': 'tao_to_alpha'
}

response = requests.get('https://api.taostats.io/api/slippage/v1', headers=headers, params=params)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| netuid | Network/Subnet ID |
| block_number | Block number when the calculation was performed |
| timestamp | ISO 8601 timestamp of the block |
| alpha_price | Current price of α in terms of TAO |
| output_tokens | Actual output tokens after slippage |
| expected_output_tokens | Expected output tokens without slippage |
| diff | Difference between expected and actual output tokens |
| slippage | Slippage percentage as a decimal |

## Notes
- All token amounts are returned as strings to maintain numerical precision
- The slippage value is returned as a decimal (e.g., 0.0144978752 represents ~1.45% slippage)
- The direction parameter determines whether you're converting from TAO to α or vice versa
- The alpha_price field shows the current conversion rate between TAO and α
- Token amounts should be specified in billionths (1e-9) of the token unit
- The endpoint calculates both the expected output without slippage and the actual output with slippage
- The diff field helps quantify the impact of slippage in absolute terms 