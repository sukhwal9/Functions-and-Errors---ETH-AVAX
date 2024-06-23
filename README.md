### MyToken Smart Contract

This smart contract is a basic implementation of an ERC-20 token using Solidity, emphasizing robust error handling with `revert`, `assert`, and `require`.

#### License:
MIT

#### Solidity Version:
0.8.7

#### Error Handling:
The contract employs three primary mechanisms for error handling:

- **revert**: Commonly used for validating user input, function arguments, and ensuring state consistency. Encountering a `revert` statement in a function undoes all changes made within that function call and its subcalls, maintaining the contract in a valid state.
- **require**: Similar to `revert`, `require` throws an exception and reverts the transaction if the provided condition is not met. It allows for custom error messages, aiding in debugging and providing informative feedback to users.
- **assert**: Typically used for internal error checking and ensuring invariants. If an `assert` statement fails, it indicates a logical error within the contract itself and reverts the transaction.

#### Contract Breakdown:

- **Constructor**: Initializes the contract owner to the address that deploys the contract.
- **Variables**:
  - `name`: Public string variable representing the token name ("NileshCoin").
  - `symbol`: Public string variable representing the token symbol ("NIL").
  - `totalSupply`: Public uint variable representing the total supply of tokens (initially 0).
  - `owner`: Public address variable storing the contract owner's address.
  - `balances`: Public mapping that stores the balance of each address.
- **Events**:
  - `Mint`: Emitted when tokens are minted.
  - `Burn`: Emitted when tokens are burned.
  - `Transfer`: Emitted when tokens are transferred between accounts.
- **Error**:
  - `InsufficientBalance`: Custom error thrown when attempting to burn more tokens than an address holds (uses `revert`).
- **Modifiers**:
  - `onlyOwner`: Ensures only the contract owner can call a function. Uses `assert` to verify the sender is the owner.
- **Functions**:
  - `mint(address, uint) (onlyOwner)`: Mints a specified amount of tokens to a given address. Uses `require` to ensure the caller is the owner.
  - `burn(address, uint) (onlyOwner)`: Burns a specified amount of tokens from a given address. Uses `revert` with a custom error (`InsufficientBalance`) if the address has insufficient balance.
  - `transfer(address, uint)`: Transfers tokens from the sender to a recipient address. Uses `require` to ensure the sender has enough balance for the transfer.

#### Deployment and Usage:
This contract provides a basic ERC-20 token implementation. Deploy it to a Solidity-compatible blockchain network and interact with it using web3 or other Ethereum development tools. Refer to the specific documentation for your chosen development framework for deployment and interaction instructions.
