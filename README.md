# Solidity
## Overview
MyToken is a simple ERC20-like token smart contract written in Solidity. It allows minting and burning of tokens while keeping track of balances for different addresses. This project demonstrates basic concepts of Solidity such as public variables, mappings, functions, and conditionals.

## Features

- **Public Variables**: Store the details about the token (name, abbreviation, and total supply).
- **Mapping**: Maintain a mapping of addresses to their respective token balances.
- **Mint Function**: Allows minting new tokens to a specified address.
- **Burn Function**: Allows burning tokens from a specified address, ensuring the address has enough balance.

## Contract Details

### Public Variables

- `name`: The name of the token.
- `symbol`: The abbreviation of the token.
- `totalSupply`: The total supply of the token.

### Mapping

- `balances`: A mapping from addresses to their token balances.

### Functions

- **Constructor**: Initializes the token with a name, symbol, and initial supply. The initial supply is assigned to the contract deployer’s address.
  ```solidity
  constructor(string memory _name, string memory _symbol, uint256 _initialSupply) {
      name = _name;
      symbol = _symbol;
      totalSupply = _initialSupply;
      balances[msg.sender] = _initialSupply;
  }
  ```

- **Mint Function**: Increases the total supply by the specified value and adds the same value to the balance of the specified address.
  ```solidity
  function mint(address _to, uint256 _value) public {
      totalSupply += _value;
      balances[_to] += _value;
  }
  ```

- **Burn Function**: Decreases the total supply by the specified value and deducts the same value from the balance of the specified address. It ensures that the address has enough balance to burn the specified value.
  ```solidity
  function burn(address _from, uint256 _value) public {
      require(balances[_from] >= _value, "Insufficient balance to burn");
      totalSupply -= _value;
      balances[_from] -= _value;
  }
  ```

## Getting Started

### Prerequisites

- Solidity ^0.8.18
- A development environment such as Remix IDE or Truffle

### Deployment

1. Open the contract in your preferred Solidity development environment.
2. Compile the contract using Solidity version 0.8.18 or higher.
3. Deploy the contract to your desired Ethereum network.

### Usage

1. **Minting Tokens**: Use the `mint` function to create new tokens and assign them to a specified address.
   ```solidity
   function mint(address _to, uint256 _value) public
   ```

2. **Burning Tokens**: Use the `burn` function to destroy tokens from a specified address, ensuring the address has sufficient balance.
   ```solidity
   function burn(address _from, uint256 _value) public
   ```
## Acknowledgements

This contract is a basic example to demonstrate key Solidity concepts and should not be used in production without further security reviews and enhancements.
