# N.E.O. Web3 Immune System

**Author:** Edward Vaughan (N.E.O.)  
**Primary Use Case (Profile v1.0):** Ubitquity / NFTitle on Proton Network  

The **N.E.O. Web3 Immune System** is a reusable safety and governance layer
designed to sit in front of sensitive smart-contract actions.

Instead of letting an app contract directly mint, transfer, or mutate critical
records (like property titles), the app must first pass through an **Immune
Guardian** contract which enforces:

- Policy profiles (per jurisdiction / product)
- KYC / AML / sanctions requirements (via external providers)
- Risk flags and dispute / freeze tags
- Emergency pause and controlled upgrade paths

This repo contains:

- A **chain-agnostic core spec**  
- A **Proton + NFTitle profile v1.0**  
- A reference layout for a Proton **`ubitguardian`** contract  
- Example flows and PDF documentation bundles

---

## Structure

```text
core-spec/
  neo_immune_system_core.md      # Chain-agnostic principles

profiles/
  proton_nfTitle_v1.md           # Detailed Proton + NFTitle profile spec

contracts/
  proton/
    ubitguardian/
      src/                       # Proton contract implementation (to be filled by integrator)
      tests/                     # Tests
      README.md                  # How to deploy on Proton

examples/
  proton_nfTitle_flow.md         # Example end-to-end flows

docs/
  neo_immune_system_proton_nfTitle_pack_v1_0.pdf        # Full integration pack
  neo_immune_system_proton_nfTitle_pitch_deck_v1_0.pdf  # Exec-level pitch deck
