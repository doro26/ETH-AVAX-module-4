# ETH-AVAX-module-4
# Ananya Token Contract

## Overview

The Ananya Token Contract is an ERC20 token implementation using the OpenZeppelin library. It includes functionalities for minting, burning, transferring, and redeeming tokens for rewards. The contract also allows for batch distribution of tokens to participants in a queue.

## Contract Details

### Name and Symbol

- **Name**: dekgen game
- **Symbol**: DGN

### Inheritance

The contract inherits from the following OpenZeppelin contracts:
- `ERC20`: Standard ERC20 token functionality.
- `Ownable`: Access control for owner-only functions.
- `ERC20Burnable`: Allows tokens to be burned.

## Functionalities

### Token Acquisition

Users can acquire tokens by providing their address and the amount of tokens they wish to purchase. These requests are added to a queue for batch processing.

```solidity
function acquireTokens(address participantAddress, uint256 tokenAmount) public;
```

### Token Distribution

The contract owner can distribute tokens in batches from the queue to the participants.

```solidity
function distributeTokens(uint256 batchSize) public onlyOwner;
```

### Token Transfer

Users can transfer tokens to another address.

```solidity
function sendTokens(address recipient, uint256 amount) public;
```

### Reward Redemption

Users can redeem their tokens for different types of rewards. Each reward type has a specific token cost associated with it.

```solidity
function redeemReward(RewardType rewardType) public;
```

### Token Burning

The contract owner can burn tokens from any account, and users can burn their own tokens when redeeming rewards.

```solidity
function burnFromAccount(address account, uint256 amount) public onlyOwner;
```

### Token Balance

Users can check their token balance.

```solidity
function getMyTokenBalance() public view returns (uint256);
```

## Reward Types and Costs

The contract supports the following reward types with their respective costs in tokens:

- **Basic**: 15 tokens
- **Standard**: 25 tokens
- **Premium**: 35 tokens
- **Ultra**: 45 tokens
- **Ultimate**: 55 tokens

## Events

The contract emits several events for key actions:

- `TokensAcquired`: Emitted when a user acquires tokens.
- `TokensDistributed`: Emitted when tokens are distributed to a participant.
- `TokensSent`: Emitted when tokens are transferred from one user to another.
- `RewardRedeemed`: Emitted when a user redeems tokens for a reward.
- `TokensBurned`: Emitted when tokens are burned.

## Functions

### `acquireTokens`

Allows users to acquire tokens and be added to the participant queue.

```solidity
function acquireTokens(address participantAddress, uint256 tokenAmount) public;
```

### `distributeTokens`

Allows the owner to distribute tokens to participants in the queue in batches.

```solidity
function distributeTokens(uint256 batchSize) public onlyOwner;
```

### `sendTokens`

Allows users to transfer tokens to another address.

```solidity
function sendTokens(address recipient, uint256 amount) public;
```

### `redeemReward`

Allows users to redeem tokens for different types of rewards.

```solidity
function redeemReward(RewardType rewardType) public;
```

### `burnFromAccount`

Allows the owner to burn tokens from any account.

```solidity
function burnFromAccount(address account, uint256 amount) public onlyOwner;
```

### `getMyTokenBalance`

Allows users to check their token balance.

```solidity
function getMyTokenBalance() public view returns (uint256);
```

### `getRewardCost`

Internal function to get the cost of a specific reward type.

```solidity
function getRewardCost(RewardType rewardType) internal pure returns (uint256);
```

### `transfer`

Overrides the ERC20 `transfer` function.

```solidity
function transfer(address to, uint256 amount) public virtual override returns (bool);
```

### `transferFrom`

Overrides the ERC20 `transferFrom` function.

```solidity
function transferFrom(address sender, address recipient, uint256 amount) public virtual override returns (bool);
```

### `approve`

Overrides the ERC20 `approve` function.

```solidity
function approve(address spender, uint256 amount) public virtual override returns (bool);
```

## Usage

To deploy and interact with the Ananya Token Contract, follow these steps:

1. **Deploy the Contract**: Deploy the contract using your preferred Ethereum development environment (e.g., Remix, Truffle).

2. **Acquire Tokens**: Users can acquire tokens by calling the `acquireTokens` function.

3. **Distribute Tokens**: The contract owner can distribute tokens to participants using the `distributeTokens` function.

4. **Transfer Tokens**: Users can transfer tokens to other addresses using the `sendTokens` function.

5. **Redeem Rewards**: Users can redeem their tokens for rewards by calling the `redeemReward` function.

6. **Burn Tokens**: The owner can burn tokens from any account using the `burnFromAccount` function, and users can burn their own tokens when redeeming rewards.

## License

This contract is licensed under the MIT License. See the LICENSE file for more details.
