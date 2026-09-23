# 03 · Ethereum & Smart Contracts

Most dApps are built on Ethereum, so this chapter goes deeper into it.

## What is Ethereum?

Ethereum is a programmable blockchain that people can build software on, to create valuable products, services and organizations in a decentralized, permissionless, censorship-resistant way (dApps).

To make it even simpler: Ethereum is basically a **"world computer"** that executes applications on top of a blockchain.

## Ethereum vs. Bitcoin

Ethereum's purpose is not mainly to be a currency payment network like Bitcoin. Ether ($ETH) is necessary for the operation of Ethereum, and is intended as a *utility currency* to pay for the usage of the world computer (Ether is the digital coin of the Ethereum network).

Ethereum is a general-purpose, programmable blockchain that executes code. It can function as a computer, and applications can be implemented on it. This is why you can have decentralized applications on it.

## Ether currency units

Ether can be divided into smaller units, down to the smallest unit possible, called **wei**. It's like the penny for the US dollar.

Most often you will use **gwei** (giga-wei, connected to gas fees) and **ether** ($ETH).

## A general-purpose blockchain

Bitcoin's blockchain tracks the state of units of bitcoin and their ownership. You can think of Bitcoin as a distributed calculator that only keeps track of money.

Instead of tracking just money, Ethereum tracks any kind of data that can be stored as a key–value pair.

Ethereum's state machine can:
- Store data (variables, balances, contract storage)
- Store and execute code (smart contracts)
- Update its state according to consensus rules

Each transaction can:
- Deploy code (a smart contract)
- Call existing code
- Change stored data

So Ethereum is like a distributed computer that can store and run any kind of program, while everyone in the world agrees on its current state through consensus.

## Two types of accounts

Both have Ethereum addresses and can hold ETH.

### 1. Externally Owned Accounts (EOAs)

The type of account you create through your wallet. These accounts have a private key. Having access to the private key means you have access to funds or contracts.

Only EOAs can initiate transactions, but contracts can react to transactions by calling other contracts.

*Example:* your MetaMask wallet `0xabc123...` is an EOA. If you sign a transaction with your private key, you can send ETH to another address, or interact with a contract (like a DEX or an NFT marketplace).

### 2. Contract accounts (smart contracts)

A contract account is a smart contract deployed to the network, controlled by its code. It contains logic that runs on the Ethereum Virtual Machine (EVM). A contract account does **not** have a private key. It is controlled by the logic of the code. Contract accounts also have addresses, just like EOAs.

You need smart contracts to write application code. Uniswap, OpenSea and other applications all have product-specific smart contracts.

*Example:* a decentralized exchange (DEX) or an NFT smart contract. When an EOA sends a transaction to the contract's address, the EVM executes the contract's code. The contract might update balances, transfer tokens, or call another contract.

### EOA vs. contract account

| Feature | EOA | Contract account |
|---|---|---|
| Controlled by | Private key | Smart contract code |
| Can initiate transactions? | ✅ Yes | ❌ No (only responds to calls) |
| Has code? | ❌ No | ✅ Yes |
| Gas to execute? | Only for sending/interaction | For running code |

## Smart contracts

A smart contract is code executed on the blockchain when specific conditions are met. For example: I send 10 ETH to the contract and the contract sends me USDC.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.19;

contract HelloWorld {
    function helloWorld() external pure returns (string memory) {
        return "Hello, World!";
    }
}
```

**Key properties**

| Property | Meaning |
|---|---|
| **Computer programs** | Smart contracts are simply computer programs. The word "contract" has no legal meaning here. |
| **Immutable** | Once deployed, the code cannot change. The only way to modify a smart contract is to deploy a new instance. |
| **Deterministic** | The outcome of execution is the same for everyone who runs it, given the transaction context and the state of the blockchain at that moment. |
| **EVM context** | Contracts have a very limited execution context: their own state, the context of the calling transaction, and some information about the most recent blocks. |
| **Decentralized world computer** | The EVM runs as a local instance on every node, but all instances start from the same state and produce the same final state, so the system operates as a single "world computer". |

## Life cycle of a smart contract

### 1. Deployment
Contracts are deployed using a special transaction:
- You send a contract creation transaction
- It is sent to a special empty recipient (no `to` address)
- It contains the contract bytecode in the data field
- After deployment, the contract has its own Ethereum address

> A smart contract has no private key. No one "owns" it at the protocol level unless the code gives privileges. The contract "owns itself".

### 2. Contracts run ONLY when triggered by a transaction
Smart contracts do not run automatically, in the background, or on their own. Execution only starts from an EOA sending a transaction. Then the contract can call other contracts. Everything ultimately starts from a human- or bot-controlled EOA.

### 3. Single-threaded execution
There is no parallel execution. Everything runs in a strict, linear order. This is important for security because concurrency bugs don't exist, but front-running does.

### 4. Transactions are atomic
An Ethereum transaction is all or nothing: either everything completes successfully, or everything is reverted as if nothing happened. **Gas spent is not refunded, even on failure.**

**Scenario 1: EOA → EOA (simple payment).** Alice sends 1 ETH to Bob.
- If successful: Alice's balance decreases, Bob's increases.
- If reverted: no ETH is moved, state is unchanged, only gas is lost.

**Scenario 2: EOA → Contract (no external calls).** The contract runs some logic and updates its state.
- If successful: storage updates stay, ETH transfers stay, events are logged.
- If reverted: everything goes back to the previous state, only gas is lost.

**Scenario 3: EOA → Contract → Contract (errors propagate).** (Safe)

If Contract A calls Contract B and B reverts, A also reverts and the entire transaction reverts. This is the normal and safe behavior: no partial state changes.

**Scenario 4: EOA → Contract → Contract (errors NOT propagated).** (Dangerous)

Contract A calls Contract B but does *not* revert if B fails. A continues and A's state changes are saved, while B's state changes revert. This results in partial state updates.

Why it's dangerous:
- Some parts of the system think the call succeeded, others think it failed
- It can cause inconsistent balances, stuck tokens, and broken logic

### 5. Code is immutable
Once deployed, contract code cannot be edited and storage cannot be erased unless the contract allows it. **But** a contract can contain a `SELFDESTRUCT` instruction. Since the Dencun upgrade in 2024 (EIP-6780), it only deletes the contract if it is called in the **same transaction** that created the contract.
In that case it:
- Removes its code
- Removes its storage
- Leaves an empty account
- Does **not** remove the history from the blockchain


### 6. Languages
- **Solidity**: main and mandatory
- **Vyper**: secondary but security-friendly
- Others: niche and almost unused

## Transactions

An Ethereum transaction is a signed message created by an EOA.
- Transactions are the only way the Ethereum state changes.
- Contracts cannot run by themselves.
- The EVM does nothing until a transaction triggers it.

### Structure of a transaction

| Field | Purpose |
|---|---|
| **Nonce** | A counter that increases each time the sender creates a transaction. Prevents replay attacks and ensures ordering. |
| **Gas price** | How much the sender is willing to pay per gas unit. |
| **Gas limit** | Maximum gas the sender will buy. Protects the sender from running out of funds. |
| **Recipient** | The destination address (EOA or contract). |
| **Value** | Amount of ETH sent (in wei). |
| **Data** | Payload for contract calls. Empty for a simple ETH transfer. |
| **v, r, s** | The ECDSA (Elliptic Curve Digital Signature Algorithm) signature. Proves the sender owns the private key. |

### Transactions vs. calls

**Transactions (write operations)**
A transaction is an instruction sent to the blockchain to do something and change its state.
- Sends a signed message to the network
- Requires gas fees
- Changes state (e.g. balances, variables)
- Is included in a block by a validator
- Immutable and permanent

Examples: sending ETH from Alice to Bob, minting an NFT, swapping tokens on Uniswap, voting on a DAO proposal, calling a smart contract function that modifies state (e.g. `transfer()`).

**Calls (read-only operations)**
A call is a local query to the blockchain: asking for information without changing anything.
- Read-only: no state change
- Free: no gas needed
- Not broadcast to the blockchain
- Happens off-chain, via your local Ethereum node (or an API like Infura)

Examples: checking your wallet balance (`balanceOf`), getting the current block number, reading smart contract variables (like token name or owner), estimating gas or simulating a transaction (`callStatic`).

### On-chain vs. off-chain

| | Where | Characteristics |
|---|---|---|
| **On-chain** | On the blockchain, visible in blocks | Costly, slow, permanent |
| **Off-chain** | Outside the blockchain, usually in apps or external systems | Fast, free, temporary |

## ERC standards

ERC standards are rules that applications/contracts can follow:

```
ERC
├── ERC-20   → rules for fungible tokens
├── ERC-721  → rules for NFTs
└── ERC-4626 → rules for tokenized vaults
```

### ERC-20 (Ethereum Request for Comments)

A token standard: a list of rules that any token issued on the Ethereum blockchain must follow. Think of ERC-20 as a blueprint that tells developers how to create a token on Ethereum that behaves like other tokens.

### IERC20 vs. ERC20

| | What it is |
|---|---|
| **IERC20** | The *interface* (the rules/API). If you want to behave like an ERC-20 token, you should have these functions. It does not contain the actual token logic. |
| **ERC20** | An *implementation* of those rules. For example, OpenZeppelin provides an ERC20 contract that implements ERC-20. You don't have to write `transfer()`, `balanceOf()`, allowances, events, etc. yourself. |

## Tokens on Ethereum

Tokens are not like $ETH, because the Ethereum network does not know anything about them.

Sending/owning $ETH is built into the Ethereum network, but sending/owning tokens like $SHIB is not. The $ETH balance of accounts is handled at the protocol level, but the token balance of accounts is handled at the smart contract level.

- If you send ETH → the protocol updates balances automatically.
- If you send tokens → the token contract code runs and updates its internal balances.

If you want to create a new token, you have to use smart contracts with rules for ownership, transfers, etc.
