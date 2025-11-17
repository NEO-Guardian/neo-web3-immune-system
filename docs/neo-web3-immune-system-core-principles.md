# N.E.O. Web3 Immune System – Core Principles v1.0

Author: Edward Vaughan (N.E.O.)

The N.E.O. Web3 Immune System is a reusable safety and governance layer
designed to sit *in front of* sensitive smart-contract actions.

Instead of letting an app contract directly mint, transfer, or mutate
critical records (like property titles), the app must first pass through
an **Immune Guardian** contract which enforces:

1. **Policy Profiles**
   - Behaviour is driven by a profile (per chain / product / jurisdiction).
   - Profiles define: allowed actions, required checks, and escalation rules.

2. **KYC / AML / Sanctions Hooks**
   - The guardian never stores KYC data itself.
   - Instead, it integrates with external providers / oracles
     (KYC/AML, sanctions lists, PEP lists, etc.).
   - The guardian only sees yes/no or risk-score style outputs.

3. **Risk Flags and Dispute / Freeze Tags**
   - Addresses or records can be tagged with risk flags.
   - Profiles define which flags force:
     - hard block,
     - temporary freeze,
     - or “allow but log + emit alert”.

4. **Emergency Pause and Upgrade Paths**
   - A controlled pause mechanism exists for serious incidents.
   - Upgrade routes are explicit:
     - who can trigger them,
     - how changes are approved,
     - and how users are notified.

5. **Auditability by Design**
   - All sensitive decisions emit structured events:
     - which profile,
     - which checks,
     - which oracle responses,
     - final decision (allow / block / freeze).
   - This gives operators, regulators, and auditors a clear trail.

6. **Chain-Agnostic Architecture**
   - The high-level spec is chain-agnostic.
   - Each chain / product publishes its own profile(s) in `/profiles`
     and its own contract layout in `/contracts`.

## Example: Proton + NFTitle (Property Titles)

For Ubitquity / NFTitle on Proton Network, a Proton + NFTitle profile might:

- Require KYC + sanctions checks for:
  - new title mints,
  - ownership transfers,
  - and adding/removing secured interests.
- Enforce extra checks for:
  - high-risk jurisdictions,
  - politically exposed persons (PEPs),
  - or blacklisted addresses.
- Provide a clear pause / dispute mechanism where:
  - disputed titles are frozen,
  - events are emitted for external case management,
  - resolution can unfreeze or reassign titles according to off-chain
    legal outcomes.

The goal is not to replace legal process, but to provide a transparent,
programmable guardrail system that supports it.

## License

This system is released under the repo’s LICENSE file.

Third parties (including Ubitquity) are encouraged to:

- fork the repo,
- keep it open source under the same license,
- retain the original copyright notices,
- and publish their own profiles and guardian layouts for their products.
