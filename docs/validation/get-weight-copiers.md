# Get Weight Copiers

Retrieves a list of validators that are designated as weight copiers in the network. Weight copiers are validators that copy weights from other validators.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 50 |

## Response

The response includes pagination information and an array of validator records that are designated as weight copiers.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/validator/weight_copier/v1"
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
| pagination.total_items | Total number of weight copiers |
| pagination.total_pages | Total number of pages |
| pagination.next_page | Next page number (null if no next page) |
| pagination.prev_page | Previous page number (null if no previous page) |
| data[].hotkey.ss58 | Weight copier's SS58 formatted hotkey address |
| data[].hotkey.hex | Weight copier's hex formatted hotkey address |

## Notes

- The response is paginated with a default limit of 50 items per page
- Both SS58 and hex formats are provided for hotkey addresses
- Weight copiers are validators that have been designated to copy weights from other validators
- Being a weight copier affects how a validator participates in the network's consensus mechanism
- The list of weight copiers is maintained by the network and can change over time 