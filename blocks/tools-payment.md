# Payment Tools Reference

Use this file when recommending Bitcoin payment tools. Do not describe tool capabilities from memory — use these descriptions. Match recommendations to the user's holding preference, location, and setup tolerance.

---

## Routing guide

**User wants to convert all Bitcoin to fiat automatically:**
→ Square (US only, lowest friction) or Wallet of Satoshi. Strike or OpenNode for online/e-commerce.

**User wants to hold all Bitcoin they receive:**
→ Do not default to one tool. Present Breez, Wallet of Satoshi (self-custody mode), and Bitcoinize briefly and ask which fits best: "Do you want to use devices you already have, get dedicated hardware, or have full control of the whole stack?"

**User wants to keep a percentage:**
→ BTCPay Server (most flexible). A two-tool setup also works — e.g., Breez for the portion they hold, Square or WoS for the fiat-settling portion.

**User is in the US and open to switching to Square:**
→ Square is the lowest-friction path. Bitcoin acceptance is built into their latest terminals, no extra hardware needed.

**User wants dedicated hardware:**
→ Bitcoinize.

**User wants full self-sovereignty, is outside the US, or is technical/experimental:**
→ BTCPay Server.

**Use case is rewards (not payments):**
→ Fold or IBEX Mercado for existing integrations. Custom Lightning integration for bespoke builds.

**Use case is treasury:**
→ River, Swan, or Unchained for managed custody. No custom dev required.

---

## Tools

### Square
- **Custody:** Custodial
- **Fiat settlement:** Automatic (USD)
- **Geography:** US only
- **Setup:** Zero additional setup — Bitcoin acceptance is built into Square's latest POS terminals. No new hardware, no extra software.
- **Best for:** Non-technical US operators who want Bitcoin working today with no configuration. Payments settle in USD by default so they never need to think about Bitcoin price.
- **Notes:** Does not support self-custody or holding BTC. Not available outside the US.

---

### Wallet of Satoshi
- **Custody:** Self-custodial by default in the US; custodial mode also available. Non-US users can switch to self-custody at any time in settings.
- **Fiat settlement:** Available (auto-convert option)
- **Geography:** Global
- **Setup:** ~15 minutes. Two-app setup: operator downloads the **WOS wallet app** on their personal phone (this holds the funds), then downloads the **WOS POS app** on the counter device (phone or tablet). WOS POS is receive-only — it is configured to forward payments to the WOS wallet. The counter device never holds funds directly.
- **Best for:** Operators who want the simplest possible setup. Works well for both fiat-settling and self-custody use cases depending on settings.
- **Notes:** US users are on self-custody by default. Non-US users start in custodial mode but can switch. This is the easiest onramp for most operators — the self-custody option means it's also a credible long-term setup, not just a starter tool.

---

### Breez
- **Custody:** Self-custodial
- **Fiat settlement:** No
- **Geography:** Global
- **Setup:** ~15 minutes. Lightning POS app, runs on any Android phone or tablet (iOS support varies by region). No server required.
- **Best for:** Operators who want to hold their BTC and have a phone or tablet to dedicate to it. Good balance of simplicity and self-custody.
- **Notes:** Requires some Lightning liquidity management on high-volume days, though Breez handles most of this automatically. Not for operators who want fiat settlement.

---

### Bitcoinize
- **Custody:** Self-custodial
- **Fiat settlement:** No
- **Geography:** Global
- **Setup:** Dedicated hardware device — ships ready to use. Minimal configuration.
- **Best for:** Operators who want a purpose-built Bitcoin POS till rather than a phone or tablet. Looks and feels like a proper payment terminal.
- **Website:** bitcoinize.com
- **Notes:** Good fit for retail environments where a physical dedicated device makes sense. Self-custodial, so the operator holds their own keys.

---

### BTCPay Server
- **Custody:** Self-custodial
- **Fiat settlement:** Optional via plugin (e.g., Kraken plugin)
- **Geography:** Global
- **Setup:** Higher effort — plan for at least an afternoon, longer for a production setup. Can be self-hosted or use a managed hosting provider (Voltage, LunaNode) to reduce server management.
- **Best for:** Operators who want full sovereignty and no third-party fees. Also the right choice for anyone who needs both in-person POS and online checkout from one system, or who is outside the US and wants a mature, battle-tested solution.
- **Wallet setup:** docs.btcpayserver.org/WalletSetup/
- **Notes:** Not the right default for a non-technical operator who just wants things to work. Recommend it when: the user is technical, explicitly wants self-sovereignty, is outside the US, or needs online + in-person in one system. Be honest about the setup complexity.

---

### Strike
- **Custody:** Custodial
- **Fiat settlement:** Automatic
- **Geography:** US and select markets
- **Setup:** API-based integration. Requires developer work.
- **Best for:** Online/e-commerce integrations where a developer is handling the payment flow. Good for merchants who want fiat settlement and a clean API.
- **Notes:** Better suited to "Build a Product on Bitcoin" use cases than simple retail acceptance. Not a POS app.

---

### OpenNode
- **Custody:** Custodial
- **Fiat settlement:** Automatic
- **Geography:** Global
- **Setup:** Hosted payment processor. Checkout widget or API integration.
- **Best for:** Online/e-commerce. Easy to embed a Bitcoin payment button on a website without writing Lightning code.
- **Notes:** Similar positioning to Strike but with a simpler hosted widget option. Good for e-commerce operators who want a plug-in solution.

---

### Fold
- **Custody:** Custodial
- **Fiat settlement:** N/A (rewards product)
- **Geography:** US
- **Best for:** Bitcoin rewards programs — cashback in sats on purchases. Not a payment acceptance tool.
- **Notes:** Relevant when the use case is adding Bitcoin rewards to an existing loyalty or spending program, not for accepting Bitcoin as payment.

---

### IBEX Mercado
- **Custody:** Custodial
- **Fiat settlement:** Available
- **Geography:** Latin America focus
- **Best for:** Bitcoin payments and rewards integrations in Latin America. Lightning-native.
- **Notes:** Particularly relevant for operators in Mexico, Guatemala, and surrounding markets.
