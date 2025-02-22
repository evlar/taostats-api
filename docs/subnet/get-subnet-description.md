# Get Subnet Description

Returns detailed information about all subnets in the network, including their names, descriptions, hardware requirements, and associated resources.

## Query Parameters
| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| page | int32 | false | Page number for pagination | 1 |
| limit | int32 | false | Number of results per page | 50 |

## Response
The endpoint returns a paginated list of subnets with their descriptive information and associated metadata.

## Example Request

```python
import requests

headers = {
    'accept': 'application/json',
    'Authorization': 'YOUR-API-KEY'
}

response = requests.get('https://api.taostats.io/api/subnet/description/v1', headers=headers)
print(response.json())
```

## Response Fields
| Field | Description |
|-------|-------------|
| netuid | Network/Subnet ID |
| bittensor_id | Bittensor network identifier (e.g., alpha, beta, gamma) |
| name | Human-readable name of the subnet |
| description | Detailed description of the subnet's purpose and functionality |
| hw_requirements | URL or text describing hardware requirements for participation |
| github | URL to the subnet's GitHub repository |
| image_url | URL to the subnet's banner or logo image |

## Notes
- The endpoint provides comprehensive information about each subnet's:
  - Purpose and functionality through detailed descriptions
  - Technical requirements for participation
  - Associated resources (GitHub repositories, documentation)
  - Visual assets (logos, banners)
- Pagination is implemented using the standard format with:
  - current_page
  - per_page (default 50)
  - total_items
  - total_pages
  - next_page
  - prev_page
- The bittensor_id field uses Greek alphabet identifiers for established subnets
- Hardware requirements may be provided as direct URLs to specification documents
- Some fields (description, hw_requirements, image_url) may be empty strings if not specified
- The response includes both active and planned subnets in the network
- Each subnet entry provides links to its official resources and documentation 