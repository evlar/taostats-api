# Get Coldkey Report

Retrieves a detailed accounting report for a coldkey, including income, stake balances, and neuron registrations over a specified time period.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| date_start | string | Yes | Start of date range in YYYY-MM-DD format (inclusive) | None |
| date_end | string | Yes | End of date range in YYYY-MM-DD format (inclusive). Must be within 12 calendar months of date_start | None |
| coldkey | string | Yes | Coldkey address to generate report for | None |
| hotkey | string | No | Filter by specific hotkey | None |
| network | string | No | Network to query (e.g., 'finney') | 'finney' |

## Response

The response includes pagination information and detailed accounting data for the specified coldkey.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/accounting/coldkey_report/v1"
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
| data[].income | Total income for the period |
| data[].neuron_registration_cost | Cost of neuron registrations |
| data[].stake_balances[] | Array of stake balance records |
| data[].stake_balances[].block_number | Block number of the balance record |
| data[].stake_balances[].timestamp | Timestamp of the balance record |
| data[].stake_balances[].hotkey | Hotkey object containing SS58 and hex addresses |
| data[].stake_balances[].coldkey | Coldkey object containing SS58 and hex addresses |
| data[].stake_balances[].stake | Total stake amount |
| data[].stake_balances[].added | Amount of stake added |
| data[].stake_balances[].removed | Amount of stake removed |
| data[].stake_balances[].action | Type of stake action performed |
| data[].neuron_registrations[] | Array of neuron registration records |

## Notes

- All dates should be provided in YYYY-MM-DD format
- All monetary values (income, stake, etc.) are in nanoTAO units
- The report includes:
  - Total income for the period
  - Stake balance changes
  - Neuron registration costs and details
- Results are paginated with configurable page size
- Both SS58 and hex formats are provided for addresses
- The response includes a complete accounting history for the specified period 