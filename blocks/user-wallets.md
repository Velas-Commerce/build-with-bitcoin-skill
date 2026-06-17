# Product Wallet Architecture Reference

Use this file when a "Build a Product on Bitcoin" user needs to provision Lightning wallets for their users, or asks about self-custodial options for a multitenant product. Do not recommend Greenlight nodes connected to Breez SDK — it is outdated. Use Breez SDK Liquid or Spark nodeless implementations instead.

---

## Routing guide

| Their situation                                            | Recommend                           |
| ---------------------------------------------------------- | ----------------------------------- |
| MVP / proof of concept, happy to custody funds short-term  | LNBits on Voltage                   |
| Micropayments (sub-1000 sat transactions)                  | Breez SDK — Spark                   |
| Standard Lightning payments (1000+ sats)                   | Breez SDK — Liquid                  |
| Maximum control, full custom node per user                 | LDK                                 |
| Privacy-first, community or creator platform               | Fedimint (existing mint)            |
| Simplest e-cash, small community or credits system         | Cashu (existing mint)               |
| Audience is Bitcoin-native and will have their own wallets | NWC (Nostr Wallet Connect) or LNURL |

---

## MVP / custodial options (ship fast, validate demand)

### LNBits on Voltage

- **Custody:** Custodial (platform holds user funds)
- **Best for:** MVPs and proof-of-concept builds. Get a working multitenant Lightning wallet system in front of users with minimal setup.
- **How it works:** LNBits is an open-source accounts and wallet system that sits on top of a Lightning node. Both Voltage and LNBits.com provides managed Lightning node infrastructure, so the builder doesn't need to run a node themselves. Each user gets a sub-wallet with their own balance.
- **Setup:** Spin up a node on lnbits.com or Voltage, point LNBits at it. Under an hour for a working setup.
- **When to recommend:** The team wants to validate the product concept before committing to a self-custodial architecture. Good explicit stepping stone — frame it as "build this first, migrate later."
- **Notes:** The platform holds user funds. This is fine for a POC but must be disclosed to users and replaced before any serious scale. Design the payment layer with this migration in mind from day one.
- **Website:** lnbits.com / voltage.cloud

---

## Embedded wallet options (platform provisions wallets for users)

### Breez SDK — Spark

- **Custody:** Non-custodial
- **Best for:** Micropayments. Spark is a Lightning-compatible protocol optimised for very small payment amounts (under ~1000 sats).
- **How it works:** Breez SDK provisions a wallet server-side. The user holds their own keys. No external Lightning node required from the builder.
- **When to recommend:** The product revolves around very small payments — pay-per-request APIs, streaming sats, micro-tipping, metered AI inference.
- **Notes:** This is the current recommended path for self-custodial embedded wallets at micropayment and regular payments at scale. Replaces Greenlight.

### Breez SDK — Liquid

- **Custody:** Non-custodial
- **Best for:** Standard Lightning-range payments (1000+ sats). Liquid is a Bitcoin sidechain with fast, confidential transactions.
- **How it works:** Same Breez SDK integration path as Spark, different settlement layer.
- **When to recommend:** Content monetisation, creator platforms, pay-per-article — anything where payments are typically above 1000 sats.
- **Notes:** Good fit for multitenant platforms where each creator needs their own wallet provisioned programmatically. Simpler ops than running per-user Lightning nodes, can be a good fit if the user would rather use Blockstream Liquid than Spark.

### LDK (Lightning Dev Kit)

- **Custody:** Non-custodial
- **Best for:** Teams that want full control of the Lightning implementation.
- **When to recommend:** The team has strong Lightning expertise and wants to own the full stack. Significant engineering lift — not the default recommendation.
- **Notes:** Maximum flexibility, maximum complexity. Only recommend if Breez SDK doesn't fit the use case or the team has a specific reason to run custom nodes, for example, novel lightning implementations.

---

## Federated / e-cash options

### Fedimint

- **Custody:** Federated (trust-minimised, distributed across guardians — not a single custodian)
- **Best for:** Community or creator platforms where privacy and distributed trust matter.
- **How it works:** A federation of operators (typically 3–5 guardians) runs a mint. Users hold e-cash tokens redeemable for Bitcoin/Lightning. No single operator controls all funds.
- **Hosting:** The builder does not need to run their own Fedimint. Existing public mints are available — users can onboard to one without the platform running any mint infrastructure.
- **When to recommend:** Privacy is a feature (anonymous payments, creator anonymity). Community savings, group treasury, or circular economy use cases.
- **Notes:** Technically custodial at the federation level, but distributed and trust-minimised. Be clear with users about this distinction.

### Cashu

- **Custody:** Custodial at the mint operator level
- **Best for:** Simple e-cash use cases, lightweight token systems, or internal platform credits.
- **How it works:** A mint issues bearer tokens. Users spend them like digital cash — fast and private.
- **Hosting:** Like Fedimint, users can use existing public Cashu mints. The builder doesn't need to operate one.
- **When to recommend:** Simpler than Fedimint, lower trust guarantees. Good for prototyping or reward/credit systems where privacy matters but federation is overkill.
- **Notes:** The mint operator is a single trust point. Be transparent with users about this.

---

## User-connected wallet options (Bitcoin-native audience only)

Only recommend these options if the discovery conversation confirmed the target audience is Bitcoin/Lightning-native — meaning users are likely to already have a Lightning wallet. For a general public audience, these options add too much onboarding friction and will kill conversion. Use an embedded wallet option instead.

### NWC — Nostr Wallet Connect

- **Best for:** Platforms where creators or users already have a Lightning wallet and want to connect it.
- **How it works:** User authorises the platform to initiate payments on their behalf via NWC protocol. The platform never holds funds.
- **When to recommend:** Audience is Bitcoin-native. Strong self-custody story, zero custody risk for the platform. Not suitable for general public onboarding.

### LNURL / Lightning Address

- **Best for:** Static inbound payment links, Lightning addresses, simple tipping flows.
- **When to recommend:** Audience is Bitcoin-native and the use case is inbound payments only (receiving tips, subscriptions, donations). Less suited to outbound or platform-initiated payments, however works well with offline receive features built into Breez SDK and can make very user-friendly UX with LNBits.

---

## Notes for the brief

- **Do not recommend Greenlight.** It is outdated. Breez SDK (Spark or Liquid) is the current recommended path for self-custodial embedded wallets.
- For micropayments specifically: LNBits or Breez SDK with Spark is the recommendation.
- For content monetisation / creator platforms: LNBits or Breez SDK with Spark or Liquid is the starting point.
- If the team needs to ship fast and validate demand first: LNBits on LNbits.com or Voltage is the default custodial MVP path. Design the payment layer to be swappable. Clearly flag it as a stepping stone, not the production architecture.
- Fedimint and Cashu do not require the builder to run their own mint — existing public mints can handle this. Flag this when a builder seems put off by the infrastructure overhead or wants to add privacy or experimental features.

---

## TODO

- **Escrow patterns** — The skill currently has no guidance on Lightning escrow for milestone-based or conditional payment flows (e.g. HODL invoices, DLCs, Cashu-as-escrow). When a builder asks about this, the skill goes too deep into implementation design. Need to decide: what primitives to surface, what to leave to the builder, and whether a `blocks/escrow.md` reference file makes sense.
