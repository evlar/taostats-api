# Get Coldkey Report as CSV

Retrieves a detailed accounting report for a coldkey in CSV format, suitable for importing into spreadsheet software or accounting systems.

## Query Parameters

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| date_start | string | Yes | Start of date range in YYYY-MM-DD format (inclusive) | None |
| date_end | string | Yes | End of date range in YYYY-MM-DD format (inclusive). Must be within 12 calendar months of date_start | None |
| coldkey | string | Yes | Coldkey address to generate report for | None |
| hotkey | string | No | Filter by specific hotkey | None |
| network | string | No | Network to query (e.g., 'finney') | 'finney' |

## Response

The response is a CSV file containing detailed accounting data for the specified coldkey.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/accounting/coldkey_report_csv/v1"
headers = {
    "accept": "application/json",
    "Authorization": "YOUR-API-KEY"
}

response = requests.get(url, headers=headers)
with open('coldkey_report.csv', 'wb') as f:
    f.write(response.content)
```

## CSV Fields

| Column | Description |
|--------|-------------|
| Date | Date of the transaction/event |
| Block Number | Block number where the event occurred |
| Type | Type of transaction or event |
| Hotkey | Hotkey address involved in the transaction |
| Amount | Transaction amount in nanoTAO |
| Action | Specific action performed (e.g., stake, unstake, registration) |
| Income | Income amount if applicable |
| Registration Cost | Neuron registration cost if applicable |
| Running Balance | Running stake balance after the transaction |

## Notes

- All dates in the CSV are in YYYY-MM-DD format
- All monetary values are in nanoTAO units
- The CSV format makes it easy to:
  - Import into spreadsheet software
  - Process with accounting tools
  - Generate custom reports
  - Perform financial analysis
- The report includes all transactions and events within the specified date range
- Headers are included in the CSV output
- Timestamps are in UTC
- The file can be directly downloaded and opened in spreadsheet applications 