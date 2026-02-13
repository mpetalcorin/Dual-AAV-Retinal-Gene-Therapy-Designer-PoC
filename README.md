# Dual-AAV-Retinal-Gene-Therapy-Designer-PoC
A capacity-aware, DoE-driven proof-of-concept pipeline that scores, ranks, and visualizes dual-AAV retinal transgene designs for MYO7A and ABCA4, with QC proxies and decision-grade validation planning outputs.
# Dual-AAV Retinal Gene Therapy Gene Designer PoC (MYO7A, ABCA4)

This repository contains a proof-of-concept (PoC) “gene designer” workflow for oversized retinal gene therapy payloads that require dual-AAV delivery, using MYO7A (Usher syndrome type 1B) and ABCA4 (Stargardt disease) as reference programs. The PoC treats transgene design as an optimization problem under AAV capacity constraints and models common failure modes, including truncated products, cryptic RNA processing, imbalance between halves, and cell stress. It outputs ranked candidate construct designs, decision-grade validation planning artifacts, and publication-style figures and tables.

## What this PoC does

- **Capacity-aware cassette architecture**
  - Builds conceptual dual-vector designs for large genes that exceed single-AAV capacity.
  - Enforces size discipline at the half-vector level and penalizes oversize risk.

- **Junction and split logic**
  - Supports platform-aware “joining” logic as design factors (e.g., hybrid-like reconstitution / splice-joining proxies).
  - Explores split fraction and half-balance modes to reduce limiting-half bottlenecks.

- **Sequence-level QC proxies for transcript fidelity**
  - Scores constructs for proxy risks: cryptic splicing, premature termination, repeats/homopolymers, GC extremes, and CpG burden.
  - Implements right-sizing logic to avoid proteostasis stress while preserving functional thresholds.

- **Decision-grade validation planning**
  - Generates a DoE matrix (promoter × split strategy × UTR × polyA × intron, plus other toggles if enabled).
  - Auto-generates an assay mapping (WB, FACS, immunostaining, functional proxy readouts) across RPE vs photoreceptor-like contexts.
  - Exports checklists, plate map layouts (non-procedural), and a high-level milestone timeline.

- **Publication-style outputs**
  - Figures: dose/transduction proxy curves, cassette size vs expression, sequence-risk vs expression, feature importance, Pareto plots, and program-specific functional proxies.
  - Tables: model metrics, permutation/feature importance, and ranked top candidates per program.

## Repository structure

```
├── src/
│   ├── gene_designer_poc.py                  # Main PoC script (design → scoring → ranking → exports)
│   ├── planning_artifacts.py                 # v3.1/vNext planning artifacts (matrix, checklists, plate maps, timeline)
│   └── plotting.py                           # Figure generation utilities
├── figures/
│   ├── fig1_aav8_dose_transduction_v2.png
│   ├── fig2_cassette_size_vs_expression_v2.png
│   ├── fig3_sequence_risk_vs_expression_v2.png
│   ├── fig4_feature_importance_v2.png
│   ├── fig5_pareto_myo7a_v2.png
│   ├── fig6_abca4_expr_vs_lipofuscin_v2.png
│   └── vector_maps/                          # Linear cassette drawings (A/B halves) for shortlisted constructs
├── tables/
│   ├── table_model_metrics_v2.csv
│   ├── table_permutation_importance_v2.csv
│   ├── table_top20_myo7a_candidates_v2.csv
│   └── table_top20_abca4_candidates_v2.csv
├── outputs/
│   ├── manifest_v*.json                      # Export manifest of generated artifacts
│   └── DECISION_PACK_*.md                    # Shortlist summary and gates
├── modelcard.md
├── datasheet.md
└── README.md
```
## How to run (local)
	1.	Create an environment and install dependencies:
	•	Python 3.10+ recommended
	•	Dependencies: numpy, pandas, matplotlib
	2.	Run the main PoC script:
	•	This generates ranked candidates and exports figures/tables.
	3.	(Optional) Run planning artifacts:
	•	Produces assay-variable matrix, checklists, plate map layouts, and timeline plan.

Note: It outputs planning artifacts and conceptual validation checklists without procedural experimental steps.

## Outputs (what to look at first)
### Figures
	•	fig2_cassette_size_vs_expression_v2.png shows the relationship between vector size discipline and predicted expression.
	•	fig3_sequence_risk_vs_expression_v2.png shows how transcript-risk features trade off with predicted expression.
	•	fig5_pareto_myo7a_v2.png summarizes stress vs functional proxy in a Pareto view.
	•	Linear cassette maps in figures/vector_maps/ show the architecture of A/B halves with labeled regions.
### Tables
	•	table_top20_*_candidates_v2.csv are the ranked shortlists per program.
	•	table_permutation_importance_v2.csv indicates which factors most influence the functional proxy.
	•	table_model_metrics_v2.csv summarizes proxy-model performance and calibration (if enabled).

## Intended use
	•	Internal R&D planning and hypothesis generation for dual-AAV cassette architecture.
	•	Construct panel design and decision-making support (DoE + assay mapping).
	•	Training and communication tool for explaining cassette trade-offs and failure modes.

## Not intended use
	•	Not a substitute for real construct synthesis, manufacturing QC, or in vivo studies.
	•	Not a clinical decision tool.
	•	Not a validated predictor of human outcomes.

## License
MIT

## Citation
If you use this repository, cite it as:
**Petalcorin, M. I. R.** (2026) Dual-AAV Retinal Gene Therapy Gene Designer PoC (MYO7A, ABCA4). GitHub repository.
