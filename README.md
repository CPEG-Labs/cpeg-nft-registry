# cpeg-nft-registry

> **Status: Testnet (Base Sepolia)**

Public append-only on-chain NFT event registry for the CPEG protocol on Base.

Every CPEG NFT mint, burn, and tier evolution is permanently recorded here as JSON metadata and a pixel art SVG image. Data only grows. Nothing is ever overwritten.

---

## Structure

```
nfts/
  {wallet-address}/
    {timestamp}-mint-{tier}.json
    {timestamp}-mint-{tier}.svg
    {timestamp}-upgrade-{tier}.json
    {timestamp}-upgrade-{tier}.svg
    {timestamp}-burn.json
  index.json
```

---

## Event JSON Format

```json
{
  "event": "mint",
  "holder": "0x...",
  "old_tier": 0,
  "new_tier": 1,
  "tier_name": "Common",
  "tx_hash": "0x...",
  "block": 12345678,
  "timestamp": "2026-05-24T00:00:00Z",
  "cpeg_contract": "0x2E0033cBEf75c07c145080CC759cB04BAf0876E2",
  "multiplier": "1.0x",
  "image_file": "nfts/{wallet}/{timestamp}-mint-common.svg"
}
```

---

## NFT Tiers

| Tier | Balance Required | Reward Multiplier |
|---|---|---|
| Common | 10M to 50M CPEG | 1.0x |
| Uncommon | 50M to 100M CPEG | 1.5x |
| Rare | 100M to 500M CPEG | 2.0x |
| Epic | 500M to 1B CPEG | 2.5x |
| Legendary | 1B to 2B CPEG | 4.0x |
| Mythic | 2B+ CPEG | 6.0x |

---

## How This Works

The CPEG API server listens to Synced events emitted by the CPEG smart contract on Base.
Each event triggers a commit to this repository with JSON metadata and a pixel art SVG image.
Commits are batched every 60 seconds. Author is the CPEG GitHub App.

---

## Contract

CPEG NFT contract (Base Sepolia): `0x2E0033cBEf75c07c145080CC759cB04BAf0876E2`

---

## Links

- Website: https://cpeg.io
- Smart contracts: https://github.com/CPEG-Labs/cpeg-contracts
- App: https://github.com/CPEG-Labs/cpeg-app
