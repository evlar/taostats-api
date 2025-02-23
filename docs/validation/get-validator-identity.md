# Get Validator Identity

Retrieves identity information for validators, including their names, URLs, descriptions, and cryptographic signatures.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| hotkey | string | No | Filter by validator hotkey address | None |
| name | string | No | Filter by validator name | None |
| page | int32 | No | Page number for pagination | 1 |
| limit | int32 | No | Number of records per page | 200 |

## Response

The response includes pagination information and an array of validator identity records.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/validator/identity/v1"
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
| data[].name | Validator's chosen name |
| data[].url | Validator's website or social media URL |
| data[].description | Validator's self-description or mission statement |
| data[].signature | Cryptographic signature verifying the identity information |

## Notes

- The response is paginated with a default limit of 200 items per page
- Both SS58 and hex formats are provided for hotkey addresses
- The signature field can be used to verify the authenticity of the identity information
- URLs and descriptions are optional and may be empty strings
- Names are unique across all validators
- Search by name is case-insensitive 