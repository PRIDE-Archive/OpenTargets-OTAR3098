# Reanalysis and Reporting

These are OTAR3098 processing requirements. The inherited human reporting scripts have not been established here as validated animal workflows.

## Reproducibility

Retain the accession, raw-file manifest, selected groups, reviewed SDRF, evidence, software versions, search configuration, FASTA release/checksum, contaminants, decoy/entrapment strategy, and identifier-mapping provenance. Record exclusions and quality acceptance decisions.

## DDA and DIA

For DDA, retain MaxQuant `mqpar.xml`, Experiment/fraction mappings, and the relevant quantification outputs. Verify label-free versus labelled configuration and the intensity or corrected reporter-intensity columns consumed downstream.

`assay name` must resolve the Experiment identifier in quantification results. For multiplexed data, also verify experiment/channel matching and reference/excluded channels.

For DIA, retain the DIA-NN version, report, library/search settings, and run-name mapping. Check against the report actually used and describe abundance metrics, filtering, and missing-value handling.

## Species and Identifiers

Preserve source-species protein and gene identifiers. Record the exact organism rather than using a species-group label as a taxonomic identity. Human orthologue mapping is a separate transformation whose source, release, and ambiguous relationships must be documented.

Do not reuse human gene mappings, sequence counts, or normalisation assumptions without verification. A human orthologue identifier does not mean that a protein was measured in a human sample.

## Inherited Script Settings

The root reporting scripts require manual configuration before animal use:

| Setting | Required action |
| --- | --- |
| Paths | Replace example local paths and dataset filenames. |
| Taxonomy | Replace hard-coded `NCBITaxon_9606` with the verified organism; handle mixed-species references explicitly. |
| Gene mapping | Replace `species='human'` queries with an appropriate mapping strategy. |
| Metadata | Set actual publication, provider, FASTA description/counts, software, and operating system. |
| Mode | Set baseline or differential analysis deliberately; the inherited DDA and DIA examples have different defaults. |
| Assays/labels | Verify MaxQuant experiment/channel or DIA-NN run matching. |
| Filtering | Verify contaminants, decoys, entrapment, reference pools, missingness, and abundance transformations. |

The discovery script also contains a human query and local output path. The summary scripts depend on Python analysis packages and R through `rpy2`, including `limma`. A locked, tested animal-processing environment is not currently supplied here; record the environment used for each run.

## Output Review

Review identification quality, quantitative coverage, replicates, batch effects, missingness, and baseline eligibility. Describe units and transformations. Keep native-species expression results distinct from cross-species comparisons.

Publish release locations only after checking the corresponding files and metadata. The human project's FTP archive is not automatically an OTAR3098 animal-output release.
