# Is your agent actually production-ready?

You should be able to check every box before you call it done.

- [ ] Every action is wrapped in an intent envelope before it executes.
- [ ] There is a written, flat list of invariants the agent can never violate.
- [ ] An independent observer scores actions against those invariants.
- [ ] The observer is read-only and cannot fix anything itself.
- [ ] The observer does not see the doer's chain-of-thought.
- [ ] There is a single source of truth, and the observer trusts it over the agent.
- [ ] High-severity flags hold the action and reach a human.
- [ ] Low-severity flags are logged and reviewed on a cadence.
- [ ] There is a circuit breaker that can stop the agent entirely.
- [ ] You can answer "what did the agent do yesterday?" from logs, not memory.
- [ ] You have seen the observer catch at least one real drift in testing.

If you can't check the last box, you haven't tested it hard enough yet.

---

The Observer is one of five disciplines. The full system — Governance Contract,
Source-of-Truth Doctrine, Anti-Overfitting Validation, and a complete worked
example — is in the pack: https://damonies.gumroad.com/l/qorsu
