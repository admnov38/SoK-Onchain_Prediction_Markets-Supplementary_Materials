# Supplementary Material for "On-Chain Prediction Markets"

Supporting data for the ACM Computing Surveys submission *On-Chain Prediction Markets* (Novocký, Košťál, Ries). Everything here is either the authors' own working data or independently verified against public sources.

## What is here, and how it relates to the paper

Some of this data also appears in the paper as typeset tables. Those files are provided here as machine-readable exports, alongside the full catalogue and the per-cell scoring detail that the paper has no room to print.

| File | In the paper | What this file adds |
|---|---|---|
| `protocol_classification.csv` | Table 4 (35 protocols, 7 dimensions) | The same table as data |
| `security_matrix.md`, `security_matrix_heatmap.html`, `security_matrix_worksheet.csv` | Table 5 scores (14 by 14) | The matrix plus a justification and evidence note for every cell |
| `protocol_catalogue.csv` | Table 4 lists 35 | The full 76-protocol catalogue, including the 41 the paper does not classify |
| `protocol_catalogue_verification.csv` | not in the paper | An independent outside-in check of the catalogue |
| `figures/taxonomy_hierarchy.png`, `.pdf` | not in the paper | The seven-dimensional taxonomy figure |

The grading rubric behind the worksheet is Appendix A of the paper.

## Files

### `index.html`

The landing page. It renders the catalogue, the full security matrix with click-to-read cell detail, and the taxonomy figure in one page. Start here if you are browsing.

### `protocol_catalogue.csv`

The survey's complete catalogue of 76 implementations across the seven taxonomy dimensions. The counts reconcile with the paper, 35 classified (`InTable4=Yes`) and 41 not classified (`InTable4=No`), matching the footnote in the comparative-analysis section. Columns are `Name, D1_MarketMechanism, D2_OracleType, D3_OutcomeStructure, D4_MarketCreation, D5_BlockchainPlatform, D6_GovernanceModel, D7_CollateralModel, Status, InTable4, ReasonIfOmitted`.

### `protocol_classification.csv`

The 35 classified protocols across the seven dimensions, with a `Block` column (Analyzed, Featured, Additional). This mirrors Table 4.

### Security matrix, in three formats

All 14 protocols by 14 attack vectors, so 196 cells. Scores are transcribed from Table 5 and reproduce the paper's four findings. 23 cells cite a specific reference. The other 173 note the Appendix A rubric applied to each protocol's architecture, with no citation invented where none exists.

`security_matrix.md` reads inline on GitHub, with a color-coded score grid, the four findings, and a per-protocol table of vector, score, justification, and evidence. Start here for the matrix. `security_matrix_heatmap.html` is a standalone color heatmap where clicking any cell shows its justification and evidence. `security_matrix_worksheet.csv` is the machine-readable source, with columns `Protocol, Vector, Score, RubricLevel, Justification, Evidence`.

### `protocol_catalogue_verification.csv`

A separate verification pass built from DeFiLlama's prediction-market category and corroborating coverage, 54 names each with a source. 40 of the 76 catalogued protocols appear here, corroborating the core of the catalogue.

### `figures/taxonomy_hierarchy.png`, `.pdf`

The seven-dimensional taxonomy of on-chain prediction markets with representative protocols in each category. The PNG is for web display and the PDF is the vector original.

## Notes on the data

Two catalogue rows carry limited public information, LiveStakes (status unknown) and ProphetX (pre-launch). Both are marked accordingly and kept for completeness. Every score and every protocol listed is drawn from public sources.

## Citation

> A. Novocký, K. Košťál, M. Ries. "SoK: On-Chain Prediction Markets." *ACM Computing Surveys* (under review), 2026.

## License

Data and figure © the authors. Pick a license before publishing. CC BY 4.0 is a common choice for supplementary data. Add a `LICENSE` file.
