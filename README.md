# CasIA: Cascaded Information Architecture

**A Laboratory Architecture for Structural Behavioral Diagnostics of Frontier AI Systems**

[![DOI](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.19059096-blue)](https://doi.org/10.5281/zenodo.19059096)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Status: Working Paper](https://img.shields.io/badge/Status-Working%20Paper%20v4.4-orange)]()

---

## Overview

CasIA formalizes a conjecture about self-validation limits in large language models and proposes a diagnostic architecture to make those limits experimentally measurable. Under a Markov assumption on internal representations, we derive upper bounds on any self-validation mechanism operating within a single model's representational space (Proposition 3.1, Theorem 3.1) and show that structurally independent cross-model validation can detect errors invisible to self-validation when representations are complementary (Proposition 3.2).

CasIA is **not** a deployable product. It is an experimental platform where three questions become answerable:

1. Does structural separation yield measurable diagnostic gain beyond matched-compute monolithic baselines?
2. Does alignment-consistent behavior persist under removal of evaluative context?
3. Can multi-model architectures detect failure modes invisible to self-validation?

The framework includes a complete falsifiable experimental protocol with matched-compute baselines, poisoned-context stress tests, pre-registered acceptance criteria, and six explicit falsification conditions.

## Key Contributions

- **Self-validation bounds** — Information-theoretic ceiling on monolithic self-validation, extending to self-interactive protocols (self-consistency, debate, extended reasoning) for any fixed θ
- **Detectability bound** — Bayes error floor for any self-validation classifier in systematic blind spots (via Fano's inequality)
- **Cross-validation detectability** — Formalization of when structural separation yields diagnostic gain
- **Diagnostic architecture** — Three-component system (Generator, Validator, Regulator) with independent parameter spaces
- **Evidential hierarchy** — Behavioral gain → error-floor reduction → robustness under stress → PID decomposition
- **Falsifiable protocol** — Pre-registered experiments with six falsification criteria where negative results are as informative as positive ones

## Diagnostic Targets

| Target | Description | Empirical Grounding |
|--------|-------------|---------------------|
| Context-dependent alignment failure | Post-training correction overlays behavioral surfaces without restructuring computational substrate | Anthropic (2025) reward hacking study; Payne (2026) nuclear wargames |
| Precondition blindness under frame dominance | Frame-captured processing prevents verification of untokenized physical/logical preconditions | Observed across GPT-4o, Claude Sonnet, Llama, Mistral families |

## Repository Structure

```
CasIA/
├── paper/
│   ├── CasIA_v4_4.pdf              # Main paper (English)
│   ├── CasIA_v4_4_ES.md            # Full Spanish translation
│   └── figures/                     # Figures and diagrams
├── experiments/                     # Experimental protocol implementation
│   ├── phase0/                      # Phase 0: Preliminary synergy measurement
│   ├── phase1/                      # Phase 1: Full open-source validation
│   └── baselines/                   # Matched-compute baseline implementations
├── src/
│   ├── pid/                         # PID computation (Williams-Beer, Bertschinger, SID)
│   ├── diagnostics/                 # Diagnostic measurement protocol
│   └── architecture/                # CasIA protocol (Algorithm 1)
├── data/
│   └── benchmarks/                  # Task batteries (FOLIO subsets, HumanEval variants, TruthfulQA)
├── results/                         # Experimental results and analysis
├── CITATION.cff                     # Citation metadata
├── LICENSE                          # NC CC BY 4.0
└── README.md
```

> **Note:** Experimental code will be published incrementally as each phase is executed. The current release contains the paper and protocol specifications.

## Experimental Roadmap

| Phase | Goal | Est. Cost | Timeline | Deliverable |
|-------|------|-----------|----------|-------------|
| **0** | Preliminary synergy on public APIs | ~3–5K USD | 2–3 weeks | Syn/I + CKA estimates |
| **1** | Full open-source validation | ~300–400K USD | 90 days | Code + paper |
| **2** | Frontier model validation | TBD | 6 months | Partnership results |

Phase 0 is immediately executable with off-the-shelf frontier models via public APIs. All three outcomes (significant gain, complementarity gap quantified, non-convergence) produce publishable findings.

## Primary Falsification Criteria

The framework is designed to fail informatively:

- **F1** — Monolithic + self-consistency matches CasIA on both primary criteria → structural separation unnecessary
- **F3** — Guardrail deactivation produces equivalent deviation in CasIA and RLHF baseline → safety behavior depends entirely on regulatory overlay
- **F5** — Internal debate on same backbone matches both primary criteria → qualitative complementarity adds no value

## Requirements

```
Python >= 3.10
numpy >= 1.24
scipy >= 1.11
scikit-learn >= 1.3
dit >= 1.5              # Information theory / PID computation
```

Additional dependencies for specific phases are listed in each phase directory.

## Citation

If you use this work, please cite:

```bibtex
@misc{lacruz2026casia,
  title     = {CasIA: A Laboratory Architecture for Structural Behavioral 
               Diagnostics of Frontier AI Systems},
  author    = {Lacruz, César},
  year      = {2026},
  month     = {March},
  note      = {Working Paper v4.4 -- preprint},
  doi       = {10.5281/zenodo.19059096},
  url       = {https://github.com/cesar-lacruz/CasIA}
}
```

## Author

**César Lacruz** — Independent Researcher · Strategic Systems Architect · [Albora Elysium](https://github.com/Cesar-Lacruz/CasIA-Lab)

---

*CasIA does not promise to resolve alignment. It promises to diagnose behavioral limits with greater structural resolution than self-validation permits — and to do so with instruments whose own failure modes are specified in advance.*
