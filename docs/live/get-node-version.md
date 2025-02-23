# Live: Get Node Version

Retrieves version information about the running Taostats node, including the blockchain name, client implementation, and version details.

## Response

The response includes basic information about the node's version and implementation.

## Example Request

```python
import requests

url = "https://api.taostats.io/api/v1/live/node/version"
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
| chain | Name of the blockchain network (e.g., "Bittensor") |
| clientImplName | Name of the client implementation (e.g., "node-subtensor") |
| clientVersion | Version string of the client software |

## Notes

- This endpoint provides basic version information about the running node
- The version information is useful for:
  - Compatibility checking
  - Troubleshooting
  - Ensuring you're connected to the correct network
  - Verifying client software versions
- The client version typically includes:
  - Major version number
  - Minor version number
  - Patch version
  - Build information or commit hash
- This information can be important when:
  - Debugging network issues
  - Planning for upgrades
  - Ensuring network compatibility
  - Verifying node deployment 