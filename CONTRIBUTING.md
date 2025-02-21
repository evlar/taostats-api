# Contributing to Taostats API Documentation

This guide explains how to document the Taostats API using Cursor IDE and Claude 3.5 Sonnet. For the complete API documentation, see the [main README](README.md).

## Documentation Process

### 1. Capture API Documentation
First, capture the API documentation from the Taostats website. This includes:
- Endpoint details
- Query parameters
- Response structure
- Example requests and responses

Here's an example of documenting the Get Transfers endpoint:

#### Overview and Endpoint
![API Overview](Screenshot from 2025-02-20 19-47-09.png)

#### Query Parameters
![API Parameters](Screenshot from 2025-02-20 19-47-47.png)

#### Response Structure
![Response Structure 1](Screenshot from 2025-02-20 19-48-05.png)
![Response Structure 2](Screenshot from 2025-02-20 19-48-24.png)

### 2. Test the API Endpoint
Make a test request to get a real response from the API. Here's an example:

```python
import requests

url = "https://api.taostats.io/api/transfer/v1?network=finney&limit=50"
headers = {
    "accept": "application/json",
    "Authorization": "YOUR-API-KEY"
}

response = requests.get(url, headers=headers)
print(response.text)
```

### 3. Document Using Cursor + Claude

1. Open Cursor IDE and start a new conversation with Claude in the composer
2. Set Claude to agent mode
3. Share the following with Claude:
   - Screenshots of the API documentation (as shown above)
   - Your test request code
   - The API response

Claude will help create properly formatted markdown documentation following our standard structure:
- Endpoint description
- URL and method
- Query parameters table
- Response structure
- Example request and response
- Field descriptions
- Notes and additional information

### 4. Review and Commit

The documentation should be organized in the following structure:
```
docs/
├── category/           # e.g., coldkeys-wallets/
│   ├── index.md       # Category overview
│   └── endpoint.md    # Individual endpoint docs
```

## Tips for Good Documentation

1. **Consistency**: Follow the existing documentation format
2. **Completeness**: Include all parameters and response fields
3. **Examples**: Provide clear, working example requests
4. **Clarity**: Use tables for parameters and field descriptions
5. **Structure**: Maintain the established directory organization

## Need Help?

If you need assistance with the documentation process, please:
1. Check the existing documentation for examples
2. Review the [main README](README.md) for structure guidelines
3. Open an issue for questions or clarification 