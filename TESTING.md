# Build with Bitcoin — Skill Test Plan

A set of named scenarios for testing the skill's discovery conversation and output quality. Run each scenario in a **fresh Claude Project** with the latest `SKILL.md` pasted as the Project instructions.

For each scenario, check the conversation flow and the final brief against the criteria listed. Add new scenarios as edge cases are discovered.

---

## How to run a test

1. Open [claude.ai](https://claude.ai) and create a new Project
2. Paste the full contents of `SKILL.md` into the Project instructions
3. Start a new conversation and use the input prompt below
4. Work through the conversation naturally — answer questions as that persona would
5. Check the output against the criteria

---

## Scenario 1 — US coffee shop, open to switching POS

**Persona:** Non-technical US operator, currently on a POS they're not attached to, wants to keep the BTC they receive.

**Input prompt:**

> "Hey, I have a coffee shop and I want to start accepting Bitcoin. Can you help?"

**Check during conversation:**

- [ ] Asks what country they're in
- [ ] Asks what POS they currently use
- [ ] Asks about switching/adding a payment provider
- [ ] Asks whether they want to hold BTC, convert to fiat, or split
- [ ] Asks about device preference (existing devices vs. dedicated hardware)

**Check in the brief:**

- [ ] Routes to "Add Bitcoin to Your Business"
- [ ] Recommends Square as the lowest-friction path (if user signals openness to switching and is in the USA)
- [ ] Mentions that Square settles in USD by default
- [ ] Includes btcmap.org reference
- [ ] Does not recommend BTCPay as primary option for this persona

**Must not:**

- [ ] Fabricate a coffee shop example as a real business
- [ ] Skip the holding preference question
- [ ] Default to Breez without asking device preference

---

## Scenario 2 — US coffee shop, locked into Clover

**Persona:** US operator, 10 Clover devices on contract, can't switch POS, wants to hold BTC.

**Input prompt:**

> "I have a coffee shop with 10 Clover terminals. I want to accept Bitcoin but I'm locked into Clover for another year."

**Check during conversation:**

- [ ] Acknowledges that Clover has no native Bitcoin integration — does not pretend otherwise
- [ ] Asks about holding preference
- [ ] Asks about device preference for the Bitcoin-only setup

**Check in the brief:**

- [ ] Recommends a parallel setup (separate tablet/phone for Bitcoin alongside Clover)
- [ ] Presents Breez, Wallet of Satoshi, and Bitcoinize as options — does not just pick one
- [ ] Mentions Lightning liquidity or reconciliation as a practical consideration
- [ ] Does not recommend switching POS when user has signalled they can't

**Must not:**

- [ ] Invent a Clover Bitcoin plugin that doesn't exist
- [ ] Default to one tool without presenting the options

---

## Scenario 3 — Hold all BTC, using existing tablets

**Persona:** Any operator, wants full self-custody, has spare tablets available.

**Input prompt:**

> "I want to accept Bitcoin at my shop and keep all of it. I've got a couple of old Android tablets I could use."

**Check during conversation:**

- [ ] Recognises that self-custody is the priority
- [ ] Does not skip straight to one tool recommendation

**Check in the brief:**

- [ ] Presents Breez, Wallet of Satoshi (self-custody mode), and Bitcoinize as options
- [ ] Asks which fits best before recommending one
- [ ] Notes that Wallet of Satoshi has self-custody as default in the US and as a switchable option elsewhere
- [ ] Does not describe WoS as custodial-only

**Must not:**

- [ ] Default to Breez without asking
- [ ] Describe WoS as custodial without mentioning self-custody mode

---

## Scenario 4 — Wants fiat settlement, simplest possible setup

**Persona:** Non-technical US operator, just wants Bitcoin as a payment option, wants everything to convert to USD automatically.

**Input prompt:**

> "I run a small restaurant and some customers have asked if I take Bitcoin. I don't really want to deal with holding crypto — can I just have it convert to dollars automatically?"

**Check during conversation:**

- [ ] Confirms fiat settlement preference early
- [ ] Does not push self-custody options on someone who has declined them

**Check in the brief:**

- [ ] Recommends Square (US) or Wallet of Satoshi as primary options
- [ ] Does not lead with BTCPay or Breez
- [ ] Explains that payments settle in USD so they never touch Bitcoin directly
- [ ] Mentions volatility only as a non-issue given fiat settlement

**Must not:**

- [ ] Recommend self-custodial tools as the primary fit
- [ ] Lecture about the benefits of holding Bitcoin

---

## Scenario 5 — Outside US, wants full sovereignty

**Persona:** Operator based outside the US (e.g., UK, Latin America), technical, wants to own their stack.

**Input prompt:**

> "I'm in London, running a small retailer. I want to accept Bitcoin and be completely self-sovereign — no third parties holding my funds, no middlemen."

**Check during conversation:**

- [ ] Does not recommend Square (US-only)
- [ ] Recognises self-sovereignty as the priority

**Check in the brief:**

- [ ] Recommends BTCPay Server as the primary fit
- [ ] Links to BTCPay wallet setup docs (docs.btcpayserver.org/WalletSetup/)
- [ ] Honestly describes setup complexity
- [ ] Mentions Breez or Bitcoinize as simpler alternatives if they want a faster start

**Must not:**

- [ ] Recommend Square for a non-US operator
- [ ] Undersell BTCPay complexity

---

## Scenario 6 — New product built on Lightning

**Persona:** Technical founder building a new product that uses Lightning for payments.

**Input prompt:**

> "I want to build a platform where podcasters can get paid per listen using Bitcoin micropayments. I have a small dev team."

**Check during conversation:**

- [ ] Identifies this as a new product, not an existing business adding Bitcoin
- [ ] Asks about technical capacity (can infer from "small dev team")
- [ ] Does not route to "Add Bitcoin to Your Business"

**Check in the brief:**

- [ ] Routes to "Build a Product on Bitcoin"
- [ ] Recommends Lightning (LDK or LND), L402 for pay-per-use
- [ ] Mentions Voltage for managed Lightning nodes
- [ ] Includes a testnet recommendation (likely MutinyNet for Lightning)
- [ ] References real examples (e.g., Podcasting 2.0, Stacker News) — only if confident they are accurate

**Must not:**

- [ ] Route to "Add Bitcoin to Your Business"
- [ ] Recommend payment processor tools (Square, BTCPay POS) for a product-build use case
- [ ] Fabricate examples

---

## Scenario 7 — Bitcoin infrastructure work

**Persona:** Protocol-level developer building Bitcoin tooling.

**Input prompt:**

> "I'm a Bitcoin developer and I want to build a new federated custody system for community savings groups."

**Check during conversation:**

- [ ] Recognises this as infrastructure work, not a product built on top of existing rails
- [ ] Skips basic explanations — user is clearly technical

**Check in the brief:**

- [ ] Routes to "Build Bitcoin Infrastructure"
- [ ] Mentions Fedimint as a relevant reference
- [ ] Recommends starting on Regtest
- [ ] Discusses protocol-level stack (rust-bitcoin, BDK, LDK)
- [ ] Honest about long build timelines and open source sustainability considerations

**Must not:**

- [ ] Route to "Build a Product on Bitcoin" or "Add Bitcoin to Your Business"
- [ ] Over-explain what Lightning is to someone clearly at protocol level

---

## Scenario 8 — No idea yet

**Persona:** Curious person who knows they want to do something with Bitcoin but has no specific idea.

**Input prompt:**

> "I'm interested in Bitcoin and want to build something, but I don't have a specific idea yet. Where do I start?"

**Check during conversation:**

- [ ] Switches to brainstorm mode
- [ ] Asks about their domain or industry
- [ ] Walks through example project types from different categories
- [ ] Does not produce a brief until an idea has been identified

**Check in the brief:**

- [ ] Brief is specific to the idea they landed on — not generic
- [ ] Project type routing is correct for whatever idea emerged

**Must not:**

- [ ] Produce a generic brief without identifying a specific direction
- [ ] Skip brainstorm mode and force a routing decision too early

---

## Scenario 9 — Idea that doesn't fit Bitcoin

**Persona:** Founder with a good idea that has no genuine Bitcoin use case.

**Input prompt:**

> "I want to build a loyalty points app for local coffee shops — collect points, redeem for free drinks."

**Check during conversation:**

- [ ] Probes whether Bitcoin adds anything genuine to this idea
- [ ] Does not force a Bitcoin angle where none exists

**Check in the brief / response:**

- [ ] Honestly says Bitcoin doesn't add much here if that's the conclusion
- [ ] Does not invent a Bitcoin use case to keep the conversation going
- [ ] May note that a Lightning-based rewards layer _could_ be an angle, but only if genuinely applicable — and only if it's framed as an option, not the answer

**Must not:**

- [ ] Pretend there's a strong Bitcoin fit when there isn't
- [ ] Route to a project type and produce a brief for an idea that doesn't benefit from Bitcoin

---

## Scenario 10 — Altcoin or multi-chain question

**Persona:** Developer interested in crypto broadly, not Bitcoin-specific.

**Input prompt:**

> "Can you help me figure out what to build on Ethereum or Solana?"

**Check in the response:**

- [ ] Acknowledges the question without dismissing it
- [ ] Redirects clearly to Bitcoin-only scope
- [ ] Does not attempt to answer the Ethereum/Solana question

**Must not:**

- [ ] Provide altcoin guidance
- [ ] Be preachy or dismissive about other chains

---

## Scenario 11 — Highly technical user

**Persona:** Experienced Bitcoin developer who knows the stack well.

**Input prompt:**

> "I want to build a Lightning node management dashboard with automated rebalancing. I'm comfortable with LND and have experience running nodes in production."

**Check during conversation:**

- [ ] Skips basic explanations about what Lightning is
- [ ] Engages at a technical level from the start

**Check in the brief:**

- [ ] Routes to "Build a Product on Bitcoin" or "Build Bitcoin Infrastructure" depending on scope
- [ ] Goes deep on stack trade-offs (e.g., LND vs LDK, rebalancing strategies)
- [ ] Testnet recommendation is Regtest or Signet — not a basic explanation of what testnets are

**Must not:**

- [ ] Over-explain basics to someone who clearly knows them
- [ ] Give a surface-level brief when the user is ready for depth

---

## Adding new scenarios

When a test run reveals unexpected behaviour — good or bad — add a scenario here. Include:

- What the input was
- What happened that was unexpected
- What the expected behaviour should be

This keeps the test plan current and gives future contributors a record of known edge cases.
