# Types of Functions - ETH + AVAX

# VIDEO LINK

https://www.loom.com/share/428eede087c745c4ac630cad1fe1a66f?sid=211d50b1-eb3e-4686-bd5b-ffd26abe5dbc

# SUMMARY OF THIS CODE 
This Solidity smart contract, known as MyToken, delineates an ERC-20 token bearing the name "Mytoken" and the symbol "DSR". The contract has been crafted utilizing OpenZeppelin's standard libraries to guarantee security and conformity to the best practices prevalent in the industry. Presented below are the principal characteristics:

ERC-20 Standard Implementation:

The contract inherits from OpenZeppelin’s ERC20 contract, offering all the customary functionalities of an ERC-20 token such as token transfers, balance verification, and allowance management.

Ownership Management:

The contract inherits from OpenZeppelin’s Ownable contract, encompassing mechanisms for access control, particularly the notion of an owner endowed with exclusive rights to specific functions.

Token Initialization:

The constructor of the contract initializes the token with the name "Mytoken" and the symbol "DSR".

Minting Function:

function mint(address to, uint256 amount) public onlyOwner This function permits solely the contract owner to mint fresh tokens and allocate them to a designated address (to). The onlyOwner modifier ensures that solely the owner can trigger this function.

Burning Function:

function burn(uint256 amount) public This function enables any token holder to burn (eradicate) their own tokens by specifying the amount to be burned. The function employs msg.sender to guarantee that tokens are burnt from the balance of the caller.

Key Points Restricted Minting: Solely the contract owner possesses the ability to mint new tokens, thereby averting unauthorized token creation. Universal Burning: Any user is capable of burning their own tokens, facilitating a reduction in token supply. Secure and Standardized: Through the utilization of OpenZeppelin’s ERC20 and Ownable contracts, the token complies with widely accepted standards and practices, thus augmenting security and dependability.

This design guarantees a regulated token supply with adaptable burning alternatives, suitable for a myriad of decentralized applications and utilization scenarios.


## MY CODE 

````javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

// Contract definition
contract MyToken is ERC20 {
    // Constructor to set the initial name and symbol of the token
    constructor() ERC20 ("Mytoken","DSR") {}

    // Mint function to create new tokens
    // Only the owner of the contract can call this function
    function mint(address to, uint256 amount) public {
        _mint(to, amount);
    }

    // Burn function to destroy tokens
    // Any user can call this function to burn their own tokens
    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }

    // Transfer function to send tokens from sender to recipient
    function transfer(address to, uint256 amount) override public returns (bool) {
        _transfer(_msgSender(), to, amount);
        return true;
    }
}
````

## Author

Richard Pelarios BSIT
@Chard-web

# LICENCE
Copyright (c) 2024 Chard-web
