# DegenToken 

## Overview

The DegenToken smart contract is an Ethereum-based ERC-20 token that incorporates additional functionality for minting, burning, transferring, and redeeming supplements. It also includes ownership management through the Ownable contract and utilizes the OpenZeppelin library for ERC-20 and Ownable implementations.

## Features

1. **Minting:**
   - Only the owner (deployer) of the smart contract can mint new tokens to a specified address.

   ```solidity
   function mint(address target, uint256 volume) public onlyOwner {
       _mint(target, volume);
   }
   ```

2. **Burning:**
   - Users can burn their own tokens, and a log message is emitted upon a successful burn.

   ```solidity
   function burn_(uint256 volume) public payable {
       require(balanceOf(msg.sender) >= volume, "INSUFFICIENT FUNDS!!");
       _burn(msg.sender, volume);
       emit LogMessage("Burned volume");
   }
   ```

3. **Transferring:**
   - Users can transfer tokens to other addresses, subject to the availability of sufficient funds.

   ```solidity
   function transfer_(address recipient, uint256 volume) external {
       require(balanceOf(msg.sender) >= volume, "INSUFFICIENT FUNDS!!");
       _transfer(msg.sender, recipient, volume);
   }
   ```

4. **Supplement Management:**
   - The smart contract allows the owner to set prices and quantities for supplements, redeem supplements, and remove supplements.

   ```solidity
   function setSupplementPricesAndQuantities(
       string memory supplementName,
       uint256 price,
       uint256 num
   ) external onlyOwner {
       // ...
   }

   function redeemSupplement(
       string memory supplementName,
       uint256 num
   ) external payable {
       // ...
   }

   function removeSupplement(string memory supplementName) external onlyOwner {
       // ...
   }
   ```

5. **Events:**
   - The contract emits a log message event (`LogMessage`) during specific operations to provide transparency and facilitate monitoring.

   ```solidity
   event LogMessage(string message);
   ```

## Usage

1. **Deployment:**
   - Deploy the DegenToken smart contract on an Ethereum-compatible blockchain.

2. **Minting:**
   - The owner can mint new tokens using the `mint` function.

3. **Burning:**
   - Users can burn their tokens using the `burn_` function.

4. **Transferring:**
   - Users can transfer tokens to other addresses using the `transfer_` function.

5. **Supplement Management:**
   - The owner can set supplement prices and quantities, redeem supplements, and remove supplements.

6. **Events:**
   - Monitor the emitted `LogMessage` events for specific actions.

## Development

- The contract is built using Solidity version 0.8.0.
- OpenZeppelin contracts are used for ERC-20, Ownable, and ERC20Burnable implementations.
- The contract has been tested using the Hardhat development environment.

## License

This smart contract is released under the MIT License. See the SPDX-License-Identifier at the beginning of the contract file for details.

## Author 

Shashi preetham

apashyamkirikiri4321@gmail.com
