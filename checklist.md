# API Documentation Checklist

## Price API
- [x] Get Price
- [x] Get Price History
- [x] Get Price OHLC

## Coldkeys/Wallets API
- [x] Get Account
- [x] Get Account History
- [x] Get Transfers
- [x] Get Exchanges

## Network/Chain API
- [x] Get Blocks
- [x] Get Block Number over Interval
- [x] Get Extrinsics
- [x] Get Events
- [x] Get Chain Calls
- [x] Get Stats Latest
- [x] Get Stats History
- [x] Get Runtime Version
- [x] Get Historical Runtime Version
- [x] Get Proxy Calls

## API Status
- [x] Get API Status

## Delegation/Staking API
- [x] Get Stake (v2)
- [x] Get Historical Stake
- [x] Get Stake Balance
- [x] Get Stake Balance Sum in Tao
- [x] Get Slippage
- [x] Get Delegation Events
- [x] Get dTao Delegation Events
- [x] Get dTAO Delegation Events

## Metagraph API
- [x] Get Metagraph
- [x] Get Metagraph History
- [x] Get Root Subnet Metagraph
- [x] Get Root Subnet History
- [x] Get Neuron Registrations
- [x] Get Neuron Deregistrations
- [x] Get Miner Weights
- [x] Get Subnet Coldkey Distribution
- [x] Get Subnet Axon IP
- [x] Get Subnet Miner Incentive

## Validation API
- [x] Get Validator
- [x] Get Validator History
- [x] Get Validator Metrics
- [x] Get Validator Metrics History
- [x] Get Parent/Child Hotkey
- [x] Get Parent/Child Hotkey History
- [x] Get Validator Identity
- [x] Get Validator Performance
- [x] Get Current Validator Weights
- [x] Get Validator Weights History
- [x] Get Validator Alpha Shares
- [x] Get Validator Alpha Shares (Historical)
- [x] Get Weight Copiers
- [x] Get Validator Emission by Subnet

## EVM API
- [x] Get EVM Transaction
- [x] Get EVM Block
- [x] Get EVM Contract
- [x] Get EVM Log
- [x] Get EVM Address

## Trading View API
- [x] Get Trading View History

## Accounting API
- [x] Get Coldkey Report
- [x] Get Coldkey Report as CSV

## Live API
- [x] Get Free Tao Balance
- [x] Get Extrinsics for Block Range
- [x] Get Latest Block Extrinsics
- [x] Get Extrinsics for Specific Block
- [x] Get Raw Extrinsics for Specific Block
- [x] Get Node Transaction Pool
- [x] Get Node Version
- [x] Get Pallet Consts
- [x] Get Pallet Consts by Id
- [x] Get Pallet Events by Id

## Hosted RPC API
- [x] WebSocket Connection (Mainnet)
- [x] HTTP Connection (Mainnet)
- [x] WebSocket Connection (Testnet)
- [x] HTTP Connection (Testnet)

## dTAO API (Beta)
- [x] Get Historical Stake Balance
- [x] Get Stake Balance
- [x] Get Validator Emission by Subnet

## Notes

### Duplicate Endpoints
1. "Get dTao Delegation Events" and "Get dTAO Delegation Events" appear to be the same endpoint with different capitalization
   - Both exist in docs/delegation-staking/
   - One at dtao-delegation-events.md
   - One at get-dtao-delegation-events.md
   - They share similar functionality but have slightly different documentation

### Potential Overlaps
1. "Get Validator Emission by Subnet" appears in both:
   - Validation API section
   - dTAO API (Beta) section
   - The endpoints appear to be the same, with the same path (/api/dtao/hotkey_emission/v1)

### Documentation Status
- Some endpoints are marked as beta or under development
- Some endpoints have incomplete example responses or fields
- Will continue noting any other patterns or issues as the verification continues

### Documentation Patterns
1. Subnet-related endpoints consistently require a `netuid` parameter
2. Most endpoints support pagination with standard parameters (page, limit, order)
3. Historical endpoints typically support both block range and timestamp range filtering
4. Address fields are consistently provided in both SS58 and hexadecimal formats
5. Numerical values are consistently returned as strings to maintain precision
6. Historical endpoints follow a consistent naming pattern (e.g., latest/v1 vs history/v1)
7. Most endpoints support flexible filtering options (by address, block number, timestamp, etc.) 