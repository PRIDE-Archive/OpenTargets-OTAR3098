# SDRF Curation

Follow the [SDRF-Proteomics specification](https://github.com/bigbio/proteomics-sample-metadata/blob/master/sdrf-proteomics/README.adoc) using original study evidence. Template example values are not evidence for a new dataset.

## Sample and Run Identity

- Preserve source organism, tissue/region, age, sex, strain/breed, stage, health status, and treatment when supported by sources.
- Distinguish biological samples from raw files. Fractions and repeated injections are not independent biological replicates.
- Record pools and known pool composition; do not expand pooled measurements into artificial individuals.
- Match raw filenames to rerun inputs. If renamed, retain a mapping to deposited names and URIs.
- For MaxQuant, map `assay name` to the Experiment identifier resolving the relevant quantification columns. Generated per-file assay identifiers may need correction before reporting.
- For DIA, verify run matching against the report. A sequential sample number is not a fraction identifier.

## Labels and References

For TMT/iTRAQ, annotate assigned sample/channel combinations against the corresponding raw fractions. Verify plexes, channel assignments, shared references, and empty channels from sample sheets or supplements. The number of configured channels does not establish a channel-to-treatment mapping.

Keep reference pools distinct from biological tissue samples. For super-SILAC, retain the organism and cell-line provenance of the heavy reference instead of assigning the tissue species to it.

## Technical Metadata

Record instrument, cleavage agents, labels, modifications, search tolerances, technical replicates, and fractions. Distinguish original acquisition metadata from reanalysis search settings, document the workflow described, and verify controlled-vocabulary names against accessions.

Retain PXD and hosting-repository identifiers where applicable. A MassIVE accession does not replace a PXD accession in `comment[proteomexchange accession number]`.

Use `not available` for unsupported or unreported values and `not applicable` for fields that do not apply. Keep annotation evidence and unresolved questions with the dataset.

## Review Before Release

1. Verify row widths and accession values.
2. Compare raw-file coverage with retained rerun inputs, including renamed files.
3. Check sample identity, replicates, pools, fractions, plexes, and labels.
4. Verify biological annotations against source evidence.
5. Match assays to MaxQuant Experiment/channel identifiers or DIA-NN run names.
6. Run a current SDRF-Proteomics validator and document the results.
7. Record gaps and review status before releasing derived results.

Structural checks do not establish biological accuracy or full specification compliance. Existing repository annotations and local generated drafts require this review.
