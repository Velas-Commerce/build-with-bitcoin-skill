# Bitcoin Testnet Guide

Use this file when recommending a test environment for a project that involves writing Bitcoin or Lightning code. Only raise this topic when the user is at a stage where they will actually be running code — don't mention testnets to someone still at the idea stage.

---

## Routing guide

| Their situation | Recommend |
|---|---|
| Early prototype, full local control, no outside dependencies needed | **Regtest** |
| Ready to test integrations with other services or wallets | **Signet** |
| Wants realistic network conditions close to mainnet | **Testnet4** |
| Building on Lightning specifically | **MutinyNet** |

---

## Testnets

### Regtest (Regression Test)
- **What it is:** A local Bitcoin network you run entirely on your own machine. You control everything — block generation, coin issuance, network state.
- **Best for:** Early-stage development and prototyping. When you need to iterate fast and don't want to depend on external network conditions or faucets.
- **How to get started:** Run Bitcoin Core with `-regtest` flag. Generate blocks on demand with `bitcoin-cli generatetoaddress`.
- **Trade-offs:** Completely isolated — no external wallets can connect, no realistic network effects. Good for unit-level development, not for testing how your product works with real Lightning wallets or third-party services.

---

### Signet
- **What it is:** A public Bitcoin test network with centrally-controlled block signing. Predictable block times, stable and widely supported.
- **Best for:** Integration testing — when you need your product to interact with other services, wallets, or APIs that also run on Signet.
- **How to get started:** Run Bitcoin Core with `-signet` flag. Get test coins from a Signet faucet (signetfaucet.com or similar).
- **Trade-offs:** Dependent on external faucets for coins, but far more stable than Testnet3/4. Most major Lightning implementations support Signet.

---

### Testnet4
- **What it is:** Bitcoin's decentralised public test network (the successor to Testnet3). Behaves more like mainnet — unpredictable block times, real mining, coins available from faucets.
- **Best for:** Pre-launch testing when you want realistic network conditions. Useful when you want to simulate mainnet behaviour before going live.
- **How to get started:** Run Bitcoin Core with `-testnet4` flag. Get test coins from a Testnet4 faucet.
- **Trade-offs:** Less predictable than Signet — can have block time gaps and occasional instability. Closer to mainnet conditions, which is the point.

---

### MutinyNet
- **What it is:** A managed Signet specifically tuned for Lightning Network development. Maintained by the Mutiny team, with fast block times and good tooling support.
- **Best for:** Lightning-specific development. If the project relies on Lightning payments, channels, or routing, MutinyNet gives a stable and well-maintained environment purpose-built for this.
- **How to get started:** Connect to MutinyNet's Signet. Documentation and faucet at mutinynet.com.
- **Trade-offs:** Dependent on a third-party managed network. Generally very stable and actively maintained, but not decentralised.

---

## Notes for the brief

- Only recommend a testnet if the user is at a stage where they will actually write or run code.
- For "Add Bitcoin to Your Business" users using hosted tools (Square, WoS, Breez), testnet is irrelevant — skip it.
- For "Build a Product on Bitcoin" users, default to Signet or MutinyNet depending on whether Lightning is central to the product.
- For "Build Bitcoin Infrastructure" users, almost always start with Regtest.
- Keep the explanation brief — most founders don't need to know what Signet is in detail, just which one to use and why.
