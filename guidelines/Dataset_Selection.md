# Dataset and Sample Selection

OTAR3098 focuses on tissue protein expression in non-human primates, rats, dogs, and minipigs for Safety 2.0. These criteria adapt the [human project workflow](https://github.com/PRIDE-Archive/opentargets/blob/main/guidelines/Dataset_Selection.md) to nonclinical species. They are review guidance, not a newly validated numerical scoring system.

## Discovery and Eligibility

Search PRIDE and ProteomeXchange using organism names, synonyms, and relevant tissues. Confirm source species from deposited metadata and publications; a search FASTA does not establish the experimental organism. Distinguish macaque species and verify minipig breed/provenance rather than treating all pig studies as minipig studies.

Prioritise unperturbed tissue samples with accessible raw files and traceable metadata. Review age, sex, strain/breed, health status, tissue sampling, and preparation.

Studies with disease, knockout, drugs, dietary intervention, surgery, pregnancy, or other experimental conditions may contain useful controls. Select eligible groups separately and document their conditions. Selection of a study does not make all its samples baseline samples.

Review PTM-enriched, immunoprecipitated, affinity-enriched, cell-line, and fluid measurements separately from whole-tissue proteomes. Their inclusion in a baseline tissue atlas requires a documented scientific rationale.

## Evidence to Review

| Attribute | Review |
| --- | --- |
| Metadata | Can each sample be linked to tissue, organism, condition, and raw file? |
| Replication | Distinguish individuals, pools, injections, and fractions. Raw-file counts do not establish biological sample size. |
| Tissue relevance | Prioritise target-safety relevance and comparison with human resources. |
| Acquisition | Record DDA/DIA, labels, plex design, fractionation, and instrument. Acquisition type alone does not guarantee quality. |
| Raw-data availability | Verify access to the files for the intended sample subset. |
| Search suitability | Verify the species database, reproducible settings, and protein/gene identifiers. |
| Confounding | Review treatment, health status, age, sex, pooling, batch, and tissue composition. |
| Quality | Review identification confidence, depth, missingness, and reproducibility after reanalysis. |
| Multiomics | Record matched transcriptomics and the strength of sample/tissue matching. |
| Provenance | Cite publication, supplement, repository record, and curator decisions. |

## Status Tracking

Track selection, rerun completion, SDRF review, quality acceptance, and output publication independently. The [inventory](../data/datasets.tsv) records the curator-reported rerun collection; it does not certify baseline eligibility or release readiness.

Record exclusions and unresolved information explicitly. Do not invent demographics, health status, channel assignments, or individual identifiers to fill a template.
