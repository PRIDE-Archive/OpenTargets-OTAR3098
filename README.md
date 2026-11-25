# Open Targets OTAR3098: Preclinical Tissue Proteomics

OTAR3098 curates and reanalyses public proteomics datasets from non-human primates (NHP), rats, dogs, and minipigs for the Safety 2.0 project. The aim is to characterise tissue protein expression in nonclinical species and support comparison with human expression resources.

The workflow builds on the [human Open Targets proteomics project (OTAR3091)](https://github.com/PRIDE-Archive/opentargets), with species-specific sample annotation, search databases, and identifier mapping.

## Dataset Collection

The working collection contains **33 distinct datasets reported as rerun by the project curator**. Rerun status does not imply completed metadata review, quality acceptance, or publication of processed outputs.

| Species group | Datasets | Accessions |
| --- | ---: | --- |
| NHP | 8 | PXD001842, PXD008825, PXD011398, PXD013597, PXD070242, PXD023520, PXD062952, PXD066108 |
| Rat | 19 | PXD001839, PXD003375, PXD004364, PXD006692, PXD012677, PXD013543, PXD015928, PXD016793, PXD016958, PXD070315, PXD045910, PXD020184, PXD022466, PXD050758, PXD059025, PXD026871, PXD034443, PXD059562, PXD068084 |
| Dog | 4 | PXD003094, PXD033420, PXD052932, PXD070290 |
| Minipig | 4 | PXD025482, PXD069137, PXD070292, PXD074506 |

See the [dataset inventory](data/datasets.tsv) for accession links, local curation review notes, and SDRF availability in this repository. Repeated accessions are counted once. Studies containing perturbations require baseline eligibility assessment at sample level.

## Workflow

### 1. Dataset and Sample Selection

Search PRIDE and ProteomeXchange by organism and tissue, including relevant MassIVE-hosted studies. Review publications, supplements, and repository metadata using the [OTAR3098 selection criteria](guidelines/Dataset_Selection.md). Record retained groups, exclusions, and unresolved information.

### 2. SDRF Curation

Annotate samples, tissues, organisms, conditions, raw files, fractions, replicates, and labels using the [SDRF-Proteomics specification](https://github.com/bigbio/proteomics-sample-metadata/blob/master/sdrf-proteomics/README.adoc).

Use the [curation guidance](guidelines/SDRF_Curation.md) and [SDRF files included here](sdrf). Choose DDA baseline, DDA TMT, or DIA layouts as appropriate. Keep pools and reference channels distinct from biological replicates. Record unsupported values as `not available`, rather than copying template example values.

### 3. Raw-Data Reanalysis

| Acquisition | Reanalysis | Inputs to downstream reporting |
| --- | --- | --- |
| DDA label-free | MaxQuant | `proteinGroups.txt`, SDRF, search parameters |
| DDA TMT/iTRAQ/SILAC | MaxQuant with appropriate label configuration | Quantification results, SDRF, channel/sample mapping, search parameters |
| DIA | DIA-NN | DIA-NN report, SDRF, library/search configuration |

Use an organism-appropriate FASTA and record its release, identifiers, contaminants, decoys, and any entrapment sequences. Preserve source-species identifiers; human orthologue mapping is a separate downstream transformation.

For MaxQuant, `assay name` must match the relevant **Experiment** identifier used by the quantification columns. Fractions from one experiment share that identifier; multiplexed data also require channel matching. For DIA, verify sample/run names against the report consumed by the reporting script.

### 4. Quality Review and Export

Review identification quality, contaminants and decoys, quantitative coverage, missingness, replicates, batches, and reference-channel handling before releasing expression summaries. Keep baseline samples distinct from treatment or disease comparisons.

**The inherited reporting scripts still contain human-specific and dataset-specific settings and require adaptation before animal use.** Both summary scripts hard-code human taxonomy (`NCBITaxon_9606`), human gene queries, and human database descriptions, alongside local paths and publication metadata.

| Script | Purpose |
| --- | --- |
| [Download PRIDE-Datasets.py](Download%20PRIDE-Datasets.py) | Dataset discovery; currently configured for a human query and local output path |
| [OpenTargets_dataset_Summary_reportfile.py](OpenTargets_dataset_Summary_reportfile.py) | DDA and labelled-data post-processing |
| [OpenTargets_DIA_Summary_report.py](OpenTargets_DIA_Summary_report.py) | DIA post-processing |
| [OPTAR_Baseline_TissueSpecificityScoring.py](OPTAR_Baseline_TissueSpecificityScoring.py) | Downstream tissue-specificity scoring |

See [reanalysis and reporting requirements](guidelines/Reanalysis.md). Repository presence does not establish validation across the four species groups.

## Repository Contents

- [Dataset inventory](data/datasets.tsv): collection, rerun status, local review notes, and repository SDRF availability.
- [Guidelines](guidelines): selection, curation, and reanalysis requirements.
- [SDRF annotations](sdrf): files currently committed to this repository.

## Data Availability

Original datasets are linked in the inventory. Additional SDRFs and animal processed-data release locations will be documented as they are reviewed and published.

The [human processed-data archive](https://ftp.pride.ebi.ac.uk/pub/databases/pride/resources/proteomes/otargets/) is a related resource, not a verified release location for OTAR3098 animal outputs.

## Contributing

Submit dataset additions and annotation corrections through a pull request. Include the accession, source evidence, retained groups, processing configuration, and validation status. Keep raw data and large search outputs in an appropriate data repository.

