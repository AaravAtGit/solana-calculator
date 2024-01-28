# Solana Calculator Smart Contract

This repository contains a Solana smart contract that performs basic mathematical operations (addition and subtraction). The contract is written in Rust and utilizes the Solana blockchain platform.

## Code Overview

The main logic of the smart contract is implemented in the `process_instruction` function. Here is a brief overview of the key components:

### Data Structures

```rust
use borsh::{BorshDeserialize, BorshSerialize};
use solana_program::{...};

// Define the type of state stored in accounts
#[derive(BorshSerialize, BorshDeserialize, Debug)]
pub struct CalculatorAccount {
    pub result: f64,
}
```

- The `CalculatorAccount` struct represents the state stored in Solana accounts, holding the result of mathematical operations.

### Entrypoint

```rust
entrypoint!(process_instruction);
```

- The `entrypoint!` macro declares the entry point of the Solana program, pointing to the `process_instruction` function.

### Program Logic

```rust
pub fn process_instruction(
    program_id: &Pubkey,
    accounts: &[AccountInfo],
    instruction_data: &[u8],
) -> ProgramResult {
    // Main logic of the program
    // ...
}
```

- The `process_instruction` function is the core of the smart contract. It handles account creation, deserialization, and performs addition or subtraction based on user input.

### Operations

```rust
pub fn calculate_sum(account: &mut CalculatorAccount, num1: f64, num2: f64) {
    account.result = num1 + num2;
}

pub fn calculate_difference(account: &mut CalculatorAccount, num1: f64, num2: f64) {
    account.result = num1 - num2;
}
```

- The `calculate_sum` and `calculate_difference` functions perform the actual addition and subtraction operations.

### Testing

```rust
#[cfg(test)]
mod tests {
    // Unit tests to verify contract functionality
    // ...
}
```

- The code includes a testing module with a test function to ensure the correctness of the smart contract.

## Deployment

To deploy the Solana smart contract, follow these steps:

1. Ensure Solana tools are installed.

2. Clone the repository.

3. Navigate to the project directory.

4. Run `cargo build-bpf` to build the program.

5. Deploy the program using the Solana deployment command (`solana deploy`).

6. Interact with the deployed contract using Solana CLI or a Solana wallet.
