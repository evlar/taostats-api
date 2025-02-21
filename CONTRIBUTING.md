# Contributing to Taostats API Documentation

This guide explains how to document the Taostats API using Cursor IDE and Claude 3.5 Sonnet. For the complete API documentation, see the [main README](README.md).

For reference, you can find the official Taostats API documentation at [docs.taostats.io](https://docs.taostats.io/reference/welcome-to-the-taostats-api).

## Documentation Process

To begin documenting an endpoint, start a new conversation in Cursor's composer with Claude in agent mode and type:
```
document endpoint
```
Claude will check the progress checklist and guide you through documenting the next endpoint.

Alternative trigger phrases:
- `start documentation`
- `document next endpoint`
- `begin documentation`

### 1. Capture API Documentation
First, capture the API documentation from the Taostats website. You'll need to take screenshots of:

1. The parameters section
   - Take one clear screenshot showing the complete parameter table
   - Make sure all columns (Parameter, Type, Required, Description, Default) are visible

2. The response structure section
   - Usually requires 2 screenshots to capture all fields
   - Make sure all response fields and their descriptions are clearly visible
   - Don't worry about naming the files - just paste the screenshots directly into the chat

Simply paste each screenshot into the chat when Claude requests it. Claude will recognize what each screenshot contains and use it appropriately.

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

## Documentation Progress

### Core Features
- [x] Project Setup
  - [x] README.md
  - [x] CONTRIBUTING.md
  - [x] Directory structure
  - [x] Documentation format established

- [x] Price API
  - [x] Get Price
  - [x] Get Price History
  - [x] Get Price OHLC

- [x] Coldkeys/Wallets API
  - [x] Get Account
  - [x] Get Account History
  - [x] Get Transfers
  - [x] Get Exchanges

- [x] Network/Chain API
  - [x] Get Blocks
  - [x] Get Block Number over Interval
  - [x] Get Extrinsics
  - [x] Get Event
  - [x] Get Chain Calls
  - [x] Get Stats Latest
  - [x] Get Stats History
  - [x] Get Runtime Version
  - [x] Get Historical Runtime Version
  - [x] Get Proxy Calls

- [x] API Status
  - [x] Get API Status

- [ ] Delegation/Staking API
  - [x] Get Stake (v2)
  - [x] Get Slippage
  - [x] Get Historical Stake
  - [x] Get Staking/Delegation Events
  - [ ] Get dTao Delegation Events
  - [x] Get Stake Balance Sum in Tao

- [ ] Metagraph API
  - [ ] Get Metagraph
  - [ ] Get Metagraph History
  - [ ] Get Root Subnet Metagraph
  - [ ] Get Root Subnet History
  - [ ] Get Neuron Registrations
  - [ ] Get Miner Weights
  - [ ] Get Subnet Coldkey Distribution
  - [ ] Get Subnet Axon IP
  - [ ] Get Subnet Miner Incentive

- [ ] Subnet API
  - [ ] Get Subnets
  - [ ] Get Current Subnet Pools
  - [ ] Get Historical Subnet Pools
  - [ ] Get Subnet Emission
  - [ ] Get Subnet Description
  - [ ] Get Subnet Owner
  - [ ] Get Subnet History
  - [ ] Get Subnet Registration Cost
  - [ ] Get Subnet Registration Cost History
  - [ ] Get Subnet Registrations

- [ ] RPC API
  - [ ] Hosted RPC Connectivity

- [ ] Validation API
  - [ ] Get Validator
  - [ ] Get Validator History
  - [ ] Get Validator Metrics
  - [ ] Get Validator Metrics History
  - [ ] Get Parent/Child Hotkey relationships
  - [ ] Get Parent/Child Hotkey History
  - [ ] Get Validator Identity
  - [ ] Get Validator Performance
  - [ ] Get Current Validator Weights
  - [ ] Get Validator Weights History
  - [ ] Get Validator Alpha Shares
  - [ ] Get Validator Alpha Shares (Historical)
  - [ ] Get Weight Copiers

- [ ] EVM API
  - [ ] Get EVM Transaction
  - [ ] Get EVM Block
  - [ ] Get EVM Contract
  - [ ] Get EVM Log
  - [ ] Get EVM Address

- [ ] Trading View API
  - [ ] Trading View History

- [ ] Accounting API
  - [ ] Get Coldkey Report
  - [ ] Get Coldkey Report as CSV

- [ ] Live API
  - [ ] Live: Get Free Tao Balance
  - [ ] Live: Get Extrinsics for Block Range
  - [ ] Live: Get Latest Block Extrinsics
  - [ ] Live: Get Extrinsics for Specific Block
  - [ ] Live: Get Raw Extrinsics for Specific Block
  - [ ] Live: Get Node Transaction Pool
  - [ ] Live: Get Node Version
  - [ ] Live: Get Pallet Consts
  - [ ] Live: Get Pallet Consts by Id
  - [ ] Live: Get Pallet Events by Id

### Beta Features
- [ ] dTAO TESTNET BETA
  - [ ] Overview
  - [ ] Endpoints

- [ ] dTao BETA
  - [ ] Overview
  - [ ] Endpoints

## Need Help?

If you need assistance with the documentation process, please:
1. Check the existing documentation for examples
2. Review the [main README](README.md) for structure guidelines
3. Open an issue for questions or clarification 