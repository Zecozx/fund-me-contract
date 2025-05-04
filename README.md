
# 💸 FundMe Contract

A smart contract for receiving ETH donations with a minimum USD value enforced via Chainlink price feeds. Built with Solidity and using a custom `PriceConverter` library.

---

## 🧠 What It Does

- Accepts ETH donations (with real USD conversion check).
- Uses Chainlink price feeds for ETH/USD price.
- Allows only the contract owner to withdraw all funds.
- Automatically handles direct ETH transfers via `receive()` and `fallback()`.

---

## 🧱 Contracts

### 🔹 FundMe.sol

```solidity
function fund() public payable
function withdraw() public onlyOwner
```

- Stores each funder's address and amount donated.
- Enforces minimum contribution of `$5` (in ETH).
- Withdraws ETH to owner via `.call`.

### 🔹 PriceConverter.sol (Library)

```solidity
function getConversionRate(uint256 ethAmount) returns (uint256)
```

- Fetches ETH price using Chainlink AggregatorV3.
- Converts `msg.value` to USD for validation.

---

## 🔐 Access Control

Only the contract deployer (owner) can withdraw funds:
```solidity
modifier onlyOwner
```

---

## 🧪 Tech Stack

- Solidity ^0.8.18
- Chainlink Oracle (ETH/USD)
- Remix / Hardhat compatible

---

## 🧾 License

MIT — feel free to use, fork, or build on top of it.

---

## 📌 Notes

- This project is for learning purposes.
- ETH/USD oracle address is hardcoded for Sepolia testnet.
- Adjust the oracle address if deploying to another network.

---

## 🙌 Created With

Solidity & Chainlink ❤️
