# 04 · Coins, Tokens & Memecoins

## NFTs (Non-Fungible Tokens)

A unique token/asset with its own identity. Each token has a unique `tokenId`. Examples: digital artwork, in-game items.

**What value does the owner get when they buy an NFT?**
- **Ownership record**: the blockchain says your address owns NFT #123.
- **Ability to transfer/sell it**: you can transfer it to another wallet or sell it.
- **Access to whatever the NFT represents**: artwork, game item, membership, ticket, etc., depending on the project.
- **Potential economic value**: if someone else is willing to pay more, you can sell it for that price.
- **Other utility, such as membership**:
  - Access to a private community
  - Exclusive events
  - Discounts
  - Early access to products
  - Perhaps a physical item every year

## Utility

Utility refers to the real-world use or functions of a token.

A **utility token** is a cryptocurrency that gives the holder access to a product, service, or feature in a blockchain project.

| Type of utility | What it means | Example tokens |
|---|---|---|
| **Payments** | Used to buy goods/services on a platform | $ETH, $SOL |
| **Gas fees** | Required to process transactions on a blockchain | $ETH, $BNB, $SUI |
| **Access** | Grants access to exclusive features or communities | $LOOKS, $GMT |
| **Governance** | Lets holders vote on project decisions | $UNI, $AAVE |
| **Staking / Yield** | Earn rewards or interest by locking the token | $ATOM, $DOT |
| **In-game currency** | Used inside games to buy items or characters | $AXS, $SAND |
| **Discounts / Benefits** | Gives lower fees or special privileges | $BNB (Binance fees) |
| **NFT utility** | Used to mint, upgrade, or interact with NFTs | $APE, $MATIC |
| **Asset exposure** | Gives you exposure to a real asset, like gold, through a token that follows its price | |

### Memecoins & utility

Most memecoins (like $DOGE, $WIF, $BONK) don't have real utility. Their value comes from community hype, memes, and speculation.

Some newer memecoins are trying to add utility, like:
- Voting for community decisions
- Being used in games or staking
- Fundraising for charities

But in general, pure memecoins = no utility (just vibes).

### How to check if a token has utility

Ask:
- What can I do with this token?
- Is it required for the app or just optional?
- Is it being used by real people or just traders?

You can find the answers on: the project's website, the whitepaper, the community (Discord, Twitter), and the GitHub/codebase.

---

## Dogecoin (DOGE)

Dogecoin is a cryptocurrency that started as a joke in 2013, based on the famous Doge meme (Shiba Inu dog with Comic Sans text). It was created by Billy Markus and Jackson Palmer. Despite being a joke, it gained real traction and has become one of the top cryptocurrencies by market cap.

**How it works**
- Based on Litecoin (which itself is a fork of Bitcoin)
- Uses Proof of Work (PoW) mining, like Bitcoin
- Block time: ~1 minute
- Unlimited supply: ~10,000 DOGE are mined every minute (no max cap)
- Can be mined using the same hardware as Litecoin (merged mining with Litecoin)

**Use cases**
- Tipping content creators online
- Microtransactions (very low fees)
- In the past,Elon Musk has hinted at using Dogecoin for payments on Twitter/X and Tesla/Mars-related projects

## Shiba Inu (SHIB)

Launched in 2020 as a Dogecoin competitor (sometimes called the "Dogecoin killer"). Created anonymously by someone using the pseudonym Ryoshi. Built on Ethereum as an ERC-20 token, not a standalone blockchain.

**How it works**

SHIB is part of a larger ecosystem that includes:
- LEASH and BONE (other tokens in the ecosystem)
- ShibaSwap: a decentralized exchange
- Shibarium: a Layer 2 blockchain launched to reduce gas fees

Initial supply: 1 quadrillion tokens, but half was burned or sent to Vitalik Buterin (who burned most of them).

**Use cases**
- Decentralized finance (DeFi) via ShibaSwap
- NFTs, staking, and metaverse projects
- Payments (some merchants accept SHIB via crypto processors)

### DOGE vs. SHIB

| | **DOGE**  | **SHIB**  |
|---|---|---|
|  Origin | Classic meme coin | Meme coin with DeFi vision |
|  Tech | Litecoin-based blockchain | ERC-20 on Ethereum |
|  Supply | Inflationary (no cap) | Deflationary (burning) |
|  Future | Payment coin  | Full ecosystem (Shibarium) |

---

## Litecoin (LTC)

A fork of Bitcoin, but faster and cheaper:
- **Faster**: a block takes 2.5 minutes, while Bitcoin takes 10 minutes (4×).
- **Cheaper**: fees of about $0.1–0.2 instead of Bitcoin's $2–10. (it change constantly)

Both use Proof of Work, but Litecoin uses a different hash algorithm, **Scrypt**, designed so that anyone can join the community and start mining.

## XRP

XRP is the native cryptocurrency of the XRP Ledger (XRPL).

the main idea is to make fast, low-cost international payments, primarily targeting banks and financial institutions.

Think of it like:

XRP Ledger (XRPL) = the blockchain/network
XRP = the native asset used on that network

let's say you are in Europe and you have onlt EUR, and you want to send USD to your friend in the United States.

Traditional banking:
```
    You
    ↓
    Europe Bank
    ↓
    Correspondent Bank
    ↓
    Another Bank
    ↓
    US Bank
    ↓
    Your Friend
```

This can create:

 - multiple intermediaries
 - fees
 - delays
 - liquidity requirements
 - reconciliation between banks

With XRP :

```
    Europe bank
    │
    │ converts EUR → XRP
    ▼
    XRP
    │
    │ transferred on XRPL
    ▼
  US liquidity provider
    │
    │ converts XRP → USD
    ▼
  US bank
```

So XRP is being used as a bridge between two different currencies,and you don't necessarily need to hold XRP.


## Polygon

Polygon is a scaling solution for Ethereum. It improves speed, reduces costs, and increases efficiency for Ethereum-based applications. It was originally launched as Matic Network, then rebranded to Polygon.

### Polygon vs. XRP

| Feature | **XRP** | **Polygon** |
|---|---|---|
| **Purpose** | Cross-border payments | Scaling Ethereum (L2) |
| **Type** | Native Layer 1 asset | Layer 2 / sidechain for Ethereum |
| **Speed** | 3–5 seconds | ~1–2 seconds (PoS) |
| **Fees** | < $0.01 | < $0.01 |
| **Consensus** | Ripple Protocol Consensus Algorithm | Proof of Stake (PoS) |
| **Use cases** | Banks, remittances | dApps, DeFi, NFTs, gaming |
| **Regulation** | Under SEC scrutiny | No major legal issues |
| **Adoption** | Banks & financial institutions | Web3 startups, brands, and DeFi projects |


## Solana 
Solana is a blockchain designed to process a large number of transactions quickly and cheaply.

Its native coin is SOL.

## Solana vs. Ethereum

Both are Layer 1 blockchains. Ethereum has slow transactions with high fees, so Solana came with a new solution: faster and cheaper (lower gas fees).

| | Ethereum | Solana |
|---|---|---|
| Consensus | Proof of Stake | Proof of Stake + **Proof of History**: a cryptographic clock that orders events, used for faster transactions |

Ethereum also has its own scaling solution: Layer 2 networks such as Arbitrum.
