# Counter Smart Contract

My first Solidity smart contract deployed on the Ethereum Sepolia Testnet.

## Project Overview

This project started as a simple counter contract built in Solidity and gradually evolved into a complete introduction to the Ethereum development workflow.

The goal was not to build a complex application, but to understand the fundamental concepts behind blockchain development by creating and deploying a real smart contract.

By the end of the project, the contract was successfully deployed to the Ethereum Sepolia testnet and interacted with through MetaMask.

---

## Features

* Store a counter value on-chain
* Increment the counter
* Decrement the counter
* Reset the counter
* Owner-only access control
* Event emission for state changes
* Deployment to Ethereum Sepolia Testnet

---

## Smart Contract

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.19;

contract Counter {
    uint public value;
    address public owner;

    event Increment(address indexed caller, uint newValue);
    event Decrement(address indexed caller, uint newValue);
    event Reset(address indexed caller, uint newValue);

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "Not owner");
        _;
    }

    function reset() public onlyOwner {
        value = 0;
        emit Reset(msg.sender, value);
    }

    function increment() public onlyOwner {
        value += 1;
        emit Increment(msg.sender, value);
    }

    function decrement() public onlyOwner {
        value -= 1;
        emit Decrement(msg.sender, value);
    }

    function get() public view returns (uint) {
        return value;
    }
}
```

---
## Deployment Information

Network: Ethereum Sepolia

Contract Address:
0x74a1f798544089bc2ff3fd831b67b28e5d6323be

Deployment Transaction:
0xe2f10b82773ab0d46ff36bf14c47ebddad6cd12adbdbab70c5e029c9017499dd

Sepolia explorer:
https://sepolia.etherscan.io/tx/0xe2f10b82773ab0d46ff36bf14c47ebddad6cd12adbdbab70c5e029c9017499dd
---

## What I Learned

### 1. Smart Contracts Are Programs On The Blockchain

A smart contract is code deployed to a blockchain network.

Once deployed, it exists independently of my computer, IDE, or wallet.

The contract continues to exist as long as the blockchain exists.

---

### 2. State Lives On-Chain

```solidity
uint public value;
```

The `value` variable is stored on the blockchain.

Changing it requires a blockchain transaction.

Reading it does not.

---

### 3. Read vs Write Functions

Read functions:

```solidity
value()
owner()
get()
```

* No transaction
* No gas fee
* No MetaMask confirmation

Write functions:

```solidity
increment()
decrement()
reset()
```

* Create a transaction
* Require a wallet signature
* Consume gas
* Trigger MetaMask confirmation

---

### 4. Ownership And Access Control

```solidity
modifier onlyOwner()
```

The owner is set during deployment:

```solidity
owner = msg.sender;
```

Only the owner can modify the counter.

This introduced the concept of authorization inside smart contracts.

---

### 5. Events

```solidity
event Increment(address indexed caller, uint newValue);
```

Events are blockchain logs.

They allow frontends, explorers, and external applications to track contract activity.

Example:

```text
Increment
Caller: 0x...
New Value: 1
```

Events create a permanent history of contract actions.

---

### 6. MetaMask

MetaMask acts as a wallet and transaction signer.

When calling a state-changing function:

```text
User
↓
MetaMask signs transaction
↓
Transaction sent to network
↓
Block confirmed
↓
State updated
```

MetaMask proves ownership of the account through cryptographic signatures.

---

### 7. Gas Fees

Every state-changing transaction consumes gas.

Gas pays validators for processing transactions.

Even on testnets:

```text
Deploy Contract
Increment
Decrement
Reset
```

all require gas.

Read-only functions do not.

---

### 8. Testnets

This project was deployed on:

Ethereum Sepolia Testnet

Sepolia behaves like Ethereum Mainnet but uses test ETH instead of real money.

This allows developers to experiment safely.

---

### 9. Etherscan

After deployment, the contract became visible on Sepolia Etherscan.

This demonstrated that blockchain data is public and verifiable.

I could inspect:

* Contract address
* Transactions
* Events
* Gas usage
* Block numbers

---

## Development Journey

### Phase 1

* Learn Solidity basics
* Create a Counter contract
* Deploy in Remix VM

### Phase 2

* Add decrement functionality
* Add ownership
* Add reset functionality
* Add events

### Phase 3

* Install MetaMask
* Configure Sepolia network
* Obtain Sepolia ETH from faucet

### Phase 4

* Connect Remix to MetaMask
* Deploy contract to Sepolia
* Verify deployment on Etherscan
* Execute live transactions

---

## Biggest Lesson

Research alone created understanding.

Building created conviction.

Before deployment, blockchain concepts existed mostly as ideas.

After deployment, they became experiences.

The moment the contract appeared on Etherscan was the moment the entire system became real.

---

## Next Steps

* Build a frontend using HTML + JavaScript
* Connect MetaMask from the browser
* Read contract state from a webpage
* Execute transactions from a webpage
* Learn Ethers.js
* Turn the contract into a simple dApp

---

## Status

✅ Contract written

✅ Contract tested locally

✅ Events implemented

✅ Ownership implemented

✅ MetaMask configured

✅ Sepolia ETH acquired

✅ Contract deployed to Sepolia

✅ Transactions executed on-chain

⏳ Frontend integration
