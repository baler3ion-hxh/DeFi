# 08 · Security & Research

## Rug pulls

A rug pull is a scam in the crypto world where developers or insiders suddenly withdraw all liquidity or funds from a project, leaving investors with worthless tokens.

### How to avoid a rug pull

**Red flags**

| ❗ Red flag | 🔎 What it means |
|---|---|
| ❌ No audit | The smart contract wasn't reviewed for traps. |
| 🐱‍👤 Anonymous devs | You don't know who is behind the project. |
| 🚫 Liquidity not locked | The devs can remove the liquidity at any time. |
| 💰 Low liquidity | $2M volume but only $10K liquidity? Dangerous. |
| 📈 Sudden pump | The token price spikes extremely fast, often manipulated. |
| 🔒 Trading restrictions | You can't sell, only buy (honeypot). |
| 💻 Copy-paste website | Same layout as many scams, zero originality. |
| 🤯 Too good to be true | "Guaranteed 1000x" or absurd APY rewards. |
| 🪙 Token ownership | Devs still own most of the supply or control minting. |

**Green flags**

| ✅ Green flag | 🔎 Why it matters |
|---|---|
| 🧾 Audited code | Reviewed by a 3rd party like Certik or Slowmist. |
| 🔐 Liquidity locked | Through services like PinkLock, UniCrypt, etc. |
| 🧑‍💻 Transparent team | Real people with history, LinkedIn, Twitter, etc. |
| 🛠 Open source | You can verify the code on-chain. |
| 📊 Healthy tokenomics | Fair launch, capped supply, community share. |
| 📅 Roadmap & updates | Active devs, GitHub commits, updates on social media. |
| 🧼 Community involvement | Not just hype, but real discussions and Q&A. |

## How to read token contracts (check for scams)

1. **Get the verified contract** using a block explorer:
   - Ethereum: etherscan.io
   - BSC: bscscan.com
   - Solana: solscan.io (for basic token info, code is harder to inspect)
2. **Look for red flags** (keywords, functions, etc.) that indicate the token is a scam.
3. **Liquidity checks.** Use tools: DexTools, GoPlus Token Security, TokenSniffer, DeFi Scanner. What to check:
   - Is liquidity locked? Check for locks on Unicrypt, PinkSale, or Team Finance.
   - Liquidity % held by the dev? If one wallet owns a large % of LP tokens, it's very risky.
   - Liquidity burnt? Safer.
4. **Check for proxy/upgradeable contracts.** Scam tokens may use proxy contracts to upgrade logic after launch (even if the code looks safe now).
5. **External libraries or imports.** Some contracts import other files (like `Ownable.sol`, `SafeMath.sol`, `UniswapRouter.sol`). Check:
   - Do any functions use external contracts that could be swapped or controlled by the dev?
   - Any obfuscated logic (very long variable names, complex loops) is suspicious.

## How to read white papers

### 1. What is a white paper?

A white paper is the summary of a coin project: the reason behind it, plus other details like the roadmap, the problem it will solve, etc. A good white paper has useful information and answers all the questions investors may ask.

### 2. Modern patterns in white papers

- **The reason behind the project**: why the project started, the problem & the solution. For example, Bitcoin solved the problem of transactions with a peer-to-peer payment solution.
- **Utility & use case**: explains the solution and the advantages of the project. For example, a new blockchain with faster transactions, a new DeFi protocol, etc.
- **The blockchain architecture behind the project**:
  - The algorithm they use (PoS, PoW)
  - Why they use this blockchain instead of others
- **The distribution & utility of the token**: distribution is the key to success. You should know how many tokens are distributed and how they are distributed.
- **The team behind it**: search whether the team worked on any successful project before.
- **References**: where they got their information from.

### 3. White paper red flags

- The white paper is hard to get (they don't want you to see it)
- The length of the white paper
- They can't explain it and use words like "the revolution of this coin", "the next Bitcoin", "ETH killer", etc.

Bitcoin White paper : https://bitcoin.org/bitcoin.pdf

## Yellow paper: the technical blueprint

**Goal:** provides the mathematical, cryptographic, and algorithmic specifications of a project, often meant for developers, researchers, and engineers.

**Contents usually include**
- Detailed protocol specs
- Formal algorithms or pseudocode
- Mathematical models
- Network and consensus mechanics
- Virtual machine architecture

**Example:** Ethereum's yellow paper (by Gavin Wood) is a dense, formal document describing how the Ethereum Virtual Machine (EVM) operates, with formulas and code-level explanations.

Link : https://ethereum.github.io/yellowpaper/paper.pdf

## How to DYOR (Do Your Own Research)

- Look at the price history first
- Look at the website: is it professional, or does it have mistakes (bad vocabulary, crazy roadmap, etc.)?
- Read the white paper
- Look at the devs: do they have any old projects?
- Check social media (Twitter, Telegram, Reddit, Medium, etc.)
- Look at market cap, liquidity, how much the devs hold, how many tokens are locked, etc.
- Copy the token address and check it on honeypot.is to see if it's a scam
