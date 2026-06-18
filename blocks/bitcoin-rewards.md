# Bitcoin Rewards & Circular Economy Reference

Use this file when a builder wants to add Bitcoin rewards, build incentive mechanics, or design a platform where value recycles inside a community. Covers simple reward distribution (platform → user) and more sophisticated circular economy designs.

---

## The core opportunity

Lightning micropayments make it viable to send tiny fractions of a bitcoin instantly at near-zero cost. This unlocks rewards and engagement mechanics that are not viable with traditional payments:

- **Gaming reward payouts** — real value for in-game achievements, not dubious tokens
- **Fitness and challenge incentives** — fund a prize pool, distribute to winners automatically
- **Value-for-value tipping** — users tip each other for content, work, or contributions
- **Loyalty and cashback** — sats back on purchases, redeemable anywhere Bitcoin is accepted
- **Community circular economies** — value earned on the platform stays in the community and recycles

The key differentiator from token schemes: Bitcoin is real, globally spendable value. Users can convert earnings to local currency, spend at merchants, or hold long-term. That's what creates the "aha moment" — when a user earns sats on your platform and spends them on something real.

---

## The four pillars of a circular economy

**1. Grassroots interest** — Build for communities that are already passionate about something. Find a niche: gaming, fitness, trading, local commerce, content creation. This only works if the community is open to integrating economics with their passion. The mainstream gaming community rejected NFTs because they felt extractive — Bitcoin rewards work because they add real, spendable value.

**2. Community organisation** — Someone has to do onboarding. The tech is the easy part. Getting people onto the platform, educating them on wallets, and providing community support is the harder problem. Design the UX for your community's technical level, not yours.

**3. Practical payments** — The more real-world utility the platform wallet provides, the better. Users need to be able to spend what they earn. Show them where: local merchants (btcmap.org), gift cards, exchange to local currency. Value has to escape the platform to feel real.

**4. Priming the pump** — Empty wallets kill network effects. Use micropayments to reward early engagement — posts, challenges, referrals, contributions. Invest in users before expecting them to invest in each other. This seeds the circular flow.

---

## Routing guide

| Use case                                      | Recommend                                                    |
| --------------------------------------------- | ------------------------------------------------------------ |
| Simple reward distribution (platform → user)  | LNBits                                                       |
| User-to-user tipping, general audience        | LNBits sub-wallets                                           |
| User-to-user tipping, Bitcoin-native audience | LNBits + NWC or LNURL                                        |
| Challenge / prize pool with winner payout     | LNBits                                                       |
| Loyalty / rewards integration (Latin America) | IBEX Mercado                                                 |
| Full circular economy with embedded wallets   | LNBits (MVP) → Breez SDK or LDK (scale)                      |
| Value-for-value / podcasting                  | NWC or LNURL for Bitcoin-native audience; LNBits for general |

---

## Tools

### LNBits

The default starting point for rewards and circular economy builds. Each user gets a sub-wallet on the platform's Lightning node. The platform credits sats directly, users tip each other, and withdrawals go to any Lightning wallet.

- **Setup:** lnbits.com or Voltage
- **Best for:** MVP and production reward distribution, user sub-wallets, challenge prize pools
- **Custody:** Custodial — the platform holds funds. Disclose this clearly to users. Build a withdrawal path from day one.
- **Extensions:** LNBits has a library of extensions for tipping, rewards, vouchers, and more. Check these before building custom logic — the functionality often already exists.

### Breez SDK

For platforms that want to give users genuinely self-custodial wallets at scale — user holds their own keys, platform never touches funds.

- **Best for:** Moving beyond LNBits MVP when self-custody matters to the community
- **See:** blocks/user-wallets.md for full Breez SDK routing (Spark vs Liquid)

### NWC — Nostr Wallet Connect

For platforms targeting Bitcoin-native users who already have wallets and want to connect them.

- **Best for:** Value-for-value, content tipping, Bitcoiner-focused platforms
- **Not for:** General public — too much onboarding friction for users new to Bitcoin

### IBEX Mercado

Latin America Lightning-native rewards and payments integration.

---

## Real examples (verified)

- **Fountain FM** — Podcasting app where listeners send value directly to podcasters using Bitcoin. Value-for-value model.
- **Primal** — Social media platform where users tip each other with Bitcoin for valuable posts and content.
- **Stacker News** — News and commentary platform where users pay each other in sats for sharing quality content.
- **Workit** — Fitness platform where users join challenges and fund Bitcoin prize pools for winners.

These platforms share a common pattern: a passionate niche community + Bitcoin as the reward layer + clear real-world utility for earned sats.

---

## Design principles for the brief

- **Lead with the aha moment.** Every recommendation should connect back to: what does the user actually do with the sats they earn? If you can't answer that, the rewards mechanic will feel hollow. Point users toward btcmap.org for in-person spending and show them off-ramp options.
- **Start custodial, disclose clearly.** LNBits is the right MVP path. Be transparent with users that the platform holds funds. Build a self-custody withdrawal path from day one.
- **Prime the pump.** Recommend the builder budget for initial reward distribution to seed engagement. Don't launch with empty wallets — the network effect won't start.
- **Don't wrap Bitcoin in a custom token.** Bitcoin is the reward. A custom token layer adds complexity and destroys the real-value proposition. Keep it sats.
- **Warn about extractive mechanics.** Communities resist economic integration that feels extractive. The mechanic has to add value to what users already care about, not monetise it against them.
