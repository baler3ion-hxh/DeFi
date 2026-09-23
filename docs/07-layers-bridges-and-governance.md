# 07 · Layers, Bridges & Governance

## Blockchain layers

| Layer | Role | Examples |
|---|---|---|
| **Layer 0** | The Network infrastructure: the base protocols that other blockchains are built on  | e.g. Polkadot, Cosmos |
| **Layer 1** | The main blockchain network where transactions happen and blocks are produced | **Bitcoin**: peer-to-peer payments. **Ethereum**: supports smart contracts and dApps |
| **Layer 2** | Scaling solutions built on top of Layer 1: improve speed, reduce fees, or add features without changing the base layer | **Arbitrum / Optimism**: rollups that batch transactions. **Lightning Network** (Bitcoin): fast off-chain payments. **zkSync / StarkNet**: zero-knowledge rollups for privacy & scalability |
| **Layer 3** | The application layer, where dApps live. They use smart contracts on Layer 1 or Layer 2 to deliver real-world use cases | **Uniswap** (DeFi DEX), **Aave** (lending platform) |

**Example: an Ethereum-based dApp**
- **Layer 0**: Ethereum network nodes connected via TCP/IP and P2P
- **Layer 1**: Ethereum mainnet stores smart contracts and tokens
- **Layer 2**: Arbitrum reduces gas fees for users of that dApp
- **Layer 3**: Uniswap is the DeFi app users interact with

## Bridges

A bridge is infrastructure that allows people to transfer (exchange) tokens from one network to another (chain to chain). There are two types of security mechanism:

1. **Centralized (trust-based)**: you trust your crypto to a third party who verifies the transaction and converts your coins. Example: **WBTC** (wrapped Bitcoin: Bitcoin wrapped as an ERC-20 so it can be used on Ethereum).
2. **Decentralized (trustless)**: uses smart contracts and sometimes external networks (oracles, relayers) for verification.

### How do bridges work?

There are several designs. Here is the simplified concept:

1. **Lock & Mint** (the most common model)
   - You lock your token (e.g. ETH) on the source chain.
   - The bridge mints an equivalent token (e.g. wrapped ETH, wETH) on the destination chain.
   - When you want to move back, the wrapped token is burned and the original is unlocked.
2. **Burn & Mint**
   - Instead of locking, the original token is burned.
   - Then a new token is minted on the target chain.
3. **Liquidity-pool based**
   - Some bridges use liquidity pools on both sides, like DEXs.
   - The bridge swaps your token for a version that already exists on the other chain (like a vault system).

### Why we need bridges

- Moving USDT from Ethereum to Solana to use **cheaper fees**
- Using Ethereum-native tokens in a gaming app on Polygon
- Bridging assets from Ethereum to an L2 (like Arbitrum) to **save gas**
- Cross-chain DeFi arbitrage (using other dApps on other chains)

## Versions of dApps

Because there is no centralized data, developers cannot upgrade dApps (smart contracts cannot be changed). So when developers want to add new features to a dApp, they create a new version with a **new address** (the old one still exists) and convince users to move to it.

## Proxy contracts

A proxy contract acts as an intermediary, delegating calls to an implementation contract while storing the state data. This pattern allows the contract's logic to be upgraded without changing its address or affecting the stored data.

## DAOs

**DAO = Decentralized Autonomous Organization**

- **Decentralized**: no single person or company has full control; decision-making is shared.
- **Autonomous**: operates automatically based on the rules coded into the smart contracts.
- **Organization**: a group with a shared goal (managing a protocol, investing in projects, funding development, etc.).
