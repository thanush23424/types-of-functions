# MyToken Smart Contract

## Overview

MyToken is an ERC-20 compliant smart contract written in Solidity. It includes functionalities for minting, burning, and transferring tokens. The contract leverages OpenZeppelin libraries for security and standardization, ensuring robustness and adherence to best practices in smart contract development.

## Features

- **ERC-20 Compliance:** Implements the standard ERC-20 interface, ensuring compatibility with existing infrastructure and tools.
- **Minting:** Allows the contract owner to mint new tokens.
- **Burning:** Allows any token holder to burn their tokens, reducing the total supply.
- **Transfer:** Enables token holders to transfer tokens to other addresses.
- **Ownership:** Utilizes the Ownable contract from OpenZeppelin to restrict certain functions to the contract owner.

### Minting Tokens

The contract owner can mint new tokens to a specified address.

```solidity
function mintTokens(address receiver, uint256 quantity) external onlyOwner {
    _mint(receiver, quantity);
}
```

### Burning Tokens

Any token holder can burn their tokens to reduce the total supply.

```solidity
function burnTokens(uint256 amount) public {
    _burn(msg.sender, amount);
}
```

### Transferring Tokens

Token holders can transfer tokens to another address.

```solidity
function transferTokens(address receiver, uint256 quantity) public virtual returns (bool) {
    _transfer(_msgSender(), receiver, quantity);
    return true;
}
```

## Security Considerations

- **Ownership:** Only the owner of the contract can mint new tokens. This is enforced by the `onlyOwner` modifier provided by the OpenZeppelin `Ownable` contract.
- **Burning:** Token holders can burn their own tokens, preventing accidental loss of tokens by others.
- **OpenZeppelin:** The contract uses well-audited libraries from OpenZeppelin to ensure security and reliability.

## License

This project is licensed under the MIT License.
