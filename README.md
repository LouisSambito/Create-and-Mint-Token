# MyToken (ERC20 Token)

This project is a coin generator that allows minting and burning tokens. The main contract file is `MyToken.sol`, and it is used with the Remix IDE.





## Overview

MyToken contract allows:
- Minting of tokens to the deployer's address.
- Minting of additional tokens 
- Burning of tokens

## Installation

To use MyToken in your project

1. Install necessary dependencies:

    npm install @openzeppelin/contracts@4.9.0

2. Open Remix.etherium.org

   Find The project in the WORKSPACE inside the folder "Contracts"
   you will find MyToken.sol


```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts@4.9.0/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts@4.9.0/token/ERC20/extensions/ERC20Burnable.sol";
import "@openzeppelin/contracts@4.9.0/access/Ownable.sol";

contract MyToken is ERC20, ERC20Burnable, Ownable {
    constructor(string memory name, string memory symbol, uint256 initialSupply) ERC20(name, symbol) {
        _mint(msg.sender, initialSupply);
    }

    function mint(address account, uint256 amount) public onlyOwner {
        _mint(account, amount);
    }

    function burnFrom(address account, uint256 amount) public override {
        _burn(account, amount); // Using _burn directly
    }

    function transfer(address recipient, uint256 amount) public virtual override returns (bool) {
        _transfer(_msgSender(), recipient, amount);
        return true;
    }
}

```
## Usage
Deploy the contract specifying the token name, symbol, and initial supply.
Use mint function to mint more tokens.
Use burnFrom function to burn tokens from an account.
Transfer tokens using standard ERC20 transfer function.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
































