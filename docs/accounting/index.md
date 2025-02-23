# Accounting API

The Accounting API provides financial reporting and analysis tools for Bittensor network participants, helping track rewards, emissions, and other financial metrics.

## Available Endpoints

- [Get Coldkey Report](get-coldkey-report.md) - Generate detailed financial report for a coldkey
- [Get Coldkey Report as CSV](get-coldkey-report-csv.md) - Export coldkey financial data in CSV format

## Common Parameters

All Accounting API endpoints support these common parameters:

| Parameter | Type | Required | Description | Default |
|-----------|------|----------|-------------|---------|
| coldkey | string | Yes | Coldkey address in SS58 format | None |
| start_date | string | No | Start date (ISO 8601) | None |
| end_date | string | No | End date (ISO 8601) | None |
| include_subtotals | boolean | No | Include period subtotals | false |
| format | string | No | Response format (JSON/CSV) | "json" |

## Response Format

JSON responses follow the standard format:

```json
{
    "success": true,
    "data": {
        // Report data
    },
    "timestamp": "2025-02-23T19:12:00.001Z"
}
```

CSV responses are provided as downloadable files with appropriate headers.

## Notes

- All monetary values are provided in both rao and tao units
- Dates and times use ISO 8601 format
- Reports can span any date range
- CSV exports include headers and data type hints
- Subtotals are provided per day, month, and year when requested
- Transaction categorization follows standard accounting practices
- All amounts include 8 decimal precision 