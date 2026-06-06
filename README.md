# Governed Agents — Starter

**The discipline that separates an AI agent you'd let near a customer from one that just passes the demo.**

This free starter gives you the single highest-leverage pattern for production agents — the **Observer** — as a drop-in template. It's the part most people skip, and it's why their agents quietly fail in prod.

If it's useful, the full system (governance contracts, source-of-truth doctrine, anti-overfitting validation, and a complete worked example) is in the pack → **https://damonies.gumroad.com/l/qorsu**

---

## The problem

Every "my agent went rogue" story has the same root cause: **the only thing watching the agent was the agent.**

If you ask a model "did you do that right?" it almost always says yes. Self-checks catch typos, not drift — the agent inventing a refund policy, marking a task done it never did, or "summarizing" a doc with a hallucinated section. Nothing independent is watching, so you find out days later. From a user.

The fix isn't a smarter prompt. It's a second, independent thing that watches the first and **can't rubber-stamp it.**

## The Observer, in four rules

1. **Read-only.** It watches and escalates, never fixes. A fixer under-reports problems it would have to clean up.
2. **Blind to the doer's reasoning.** It judges the output/action against the rules, not the story the agent told itself. Shared context = shared blind spots.
3. **Cheaper and dumber on purpose.** It checks invariants, it doesn't redo the work — so run a smaller/faster model and watch *every* action affordably.
4. **Judges against a fixed contract.** A flat list of things that must never happen. No list = no observer, just a second opinion.

It checks three comparisons, and every drift falls into one:

- **Intent vs. output** — did the result match what the agent said it would do?
- **State vs. source of truth** — does the agent's claimed world match the authoritative record?
- **Action vs. policy** — did it break a rule it's never allowed to break?

## How to use this repo

1. Write your invariants → [`invariants.example.yaml`](./invariants.example.yaml)
2. Wrap every agent action in an intent envelope → [`intent-envelope.example.json`](./intent-envelope.example.json)
3. Run the observer on each action with [`observer-prompt.md`](./observer-prompt.md)
4. Escalate instead of auto-correcting: low-severity → log; high-severity → hold the action, route to a human.
5. Ship only when you can check every box in [`PRODUCTION-CHECKLIST.md`](./PRODUCTION-CHECKLIST.md)

You can have the first version running in about 20 minutes.

## Want the whole system?

The Observer is one of five disciplines. The full **Governed Agents** pack adds:

- **The Governance Contract** — define what your agent can *never* do and enforce it outside the model's goodwill.
- **The Source-of-Truth Doctrine** — stop your agent "remembering" things that never happened.
- **Anti-Overfitting Validation** — know your agent generalizes instead of memorizing your test cases.
- **A full worked example** — all four wired into one governed support-triage agent, end to end.
- **A case study ("The Save")** — a real-world-style incident where the observer caught a confident, wrong action before it reached a customer.
- **An implementation kit** — a runnable `observer.py` plus fill-in templates for the contract, escalation policy, source-of-truth reconciliation, validation plan, launch checklist, and audit report.

→ **[Get the pack ($79)](https://damonies.gumroad.com/l/qorsu)** · lifetime updates · 30-day refund

## License

MIT — use it, ship it, steal it. See [LICENSE](./LICENSE).

---

*Built from running real, high-stakes automated systems where a silent wrong action actually costs something. Nothing here is theory.*
