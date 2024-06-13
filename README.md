# MyToken

A simple ERC20-like token contract written in Solidity. This contract allows the minting and burning of tokens, maintaining the total supply and balances of different addresses.

## Description

MyToken is a basic Solidity smart contract that demonstrates the creation and management of a token on the Ethereum blockchain. It includes public variables to store the token details, a mapping to keep track of balances, and functions for minting and burning tokens. This project serves as an introductory example for those looking to learn about Solidity and smart contract development.

## Getting Started

### Installing

To work with this contract, you'll need to use Remix, an online Solidity IDE. Follow these steps to set up and run the contract:

1. Go to the Remix website: [https://remix.ethereum.org/](https://remix.ethereum.org/).
2. Create a new file by clicking on the "+" icon in the left-hand sidebar.
3. Save the file with a `.sol` extension (e.g., `MyToken.sol`).
4. Copy and paste the following code into the file:

    ```solidity
    // SPDX-License-Identifier: MIT
    pragma solidity 0.8.18;

    /*
           REQUIREMENTS
        1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
        2. Your contract will have a mapping of addresses to balances (address => uint)
        3. You will have a mint function that takes two parameters: an address and a value. 
           The function then increases the total supply by that number and increases the balance 
           of the address by that amount
        4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
           It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
           and from the balance of the address.
        5. Lastly, your burn function should have conditionals to make sure the balance of account is greater than or equal 
           to the amount that is supposed to be burned.
    */

    contract MyToken {

        // public variables here
        string public name;
        string public symbol;
        uint256 public totalSupply;

        // mapping variable here
        mapping(address => uint256) public balances;

        // constructor to initialize the token details
        constructor(string memory _name, string memory _symbol, uint256 _initialSupply) {
            name = _name;
            symbol = _symbol;
            totalSupply = _initialSupply;
            balances[msg.sender] = _initialSupply;
        }

        // mint function
        function mint(address _to, uint256 _value) public {
            totalSupply += _value;
            balances[_to] += _value;
        }

        // burn function
        function burn(address _from, uint256 _value) public {
            require(balances[_from] >= _value, "Insufficient balance to burn");
            totalSupply -= _value;
            balances[_from] -= _value;
        }
    }
    ```

### Executing Program

To compile and deploy the contract, follow these steps:

1. **Compile the Contract**:
   - Click on the "Solidity Compiler" tab in the left-hand sidebar.
   - Ensure the "Compiler" option is set to "0.8.18" (or another compatible version).
   - Click on the "Compile MyToken.sol" button.

2. **Deploy the Contract**:
   - Click on the "Deploy & Run Transactions" tab in the left-hand sidebar.
   - Select the "MyToken" contract from the dropdown menu.
   - Click on the "Deploy" button.

3. **Interact with the Contract**:
   - After deployment, you can mint tokens by calling the `mint` function.
   - You can burn tokens by calling the `burn` function.

### Help

For common issues, ensure that:

- You are using the correct Solidity version (0.8.18).
- The addresses and values provided for minting and burning are valid.
- The address you are trying to burn from has enough tokens.

If you encounter issues, you can refer to the Remix documentation or use their integrated help tools.

## Authors
Shourya Agarwal
@shourya005

## License

This project is licensed under the MIT License - see the LICENSE.md file for details.
