# Comparative Genomic and Phylogenomic Analysis of Industrial Microbial Chassis

Reproducibility repository for the manuscript **“Comparative Genomic and Phylogenomic Analysis Reveals Biosynthetic Potential of Industrial Microbial Chassis for Sustainable Production of Lactic Acid, Polyhydroxyalkanoates, Poly-γ-glutamate and Triacylglycerols.”**

## Scope
This repository archives the Bash/Python analysis scripts, Snakemake workflow, reference/mapping files, processed pathway-scoring outputs, essential OrthoFinder statistics/tree files, and publication-oriented figures. It excludes unrelated later consortium-engineering, FBA and machine-learning stages from the wider `consortia_insilico` project.

## Final analysis set
The comparative-genomics analysis contains 11 genomes: BAM (*Bacillus amyloliquefaciens*), BCO (*Heyndrickxia coagulans*, formerly *Bacillus coagulans*), BLI (*Bacillus licheniformis*), BSU (*Bacillus subtilis*), CNE (*Cupriavidus necator*), LCA (*Lacticaseibacillus casei*), LLA (*Lactococcus lactis*), LPL (*Lactiplantibacillus plantarum*), PPU (*Pseudomonas putida*), ROP (*Rhodotorula toruloides*) and YLI (*Yarrowia lipolytica*).

`metadata/initial_candidate_species.csv` is retained only as historical provenance; `metadata/final_analysis_manifest.tsv` is the final manuscript analysis set.

## Marker panels used for reported scores
The authoritative scoring definitions are those hard-coded in the analysis scripts: γ-PGA = `pgsA, pgsB, pgsC, degQ`; PHA = `phaC, phaP, phaR, phaZ`; lactic-acid-associated = `pdh, pfl`; TAG precursor = `accA, accD`.

Historical configuration/reference files contain broader exploratory marker sets and are not the definitions used to calculate the reported manuscript scores.

## Scoring
DIAMOND hits are filtered at ≥40% identity, ≥70% query coverage and E-value ≤1e-20. The best Genome–Gene hit is selected by bitscore. Gene confidence score = `0.6 × percent identity + 0.4 × query coverage`. Pathway weighted score is the mean confidence score across all markers in the panel, with absent markers contributing zero. Overall weighted score is the arithmetic mean of the four pathway weighted scores.

These are comparative genomic indices and must not be interpreted as direct predictions of fermentation titre, yield or productivity.

## OrthoFinder
The archived results support 11 species, 52,096 proteins, 40,579 proteins assigned to 5,791 orthogroups (77.9%), 289 orthogroups present in all species, 1,308 species-specific orthogroups and 89 single-copy orthogroups. The original run used OrthoFinder 3.1.5. The species-tree plotting script renders the already-generated rooted Newick tree; it does not infer the phylogeny.

## Provenance limitations
The archived Snakemake workflow begins DIAMOND processing from an existing raw DIAMOND table; the original command that generated that table was not retained as a standalone script. Likewise, the archived genome-download helper prepares organism directories but does not itself execute the NCBI download. No reconstructed command is represented as an archived original.

## Software
Key retained versions include Python 3.11.15, Snakemake 9.22.0, DIAMOND 2.2.2, OrthoFinder 3.1.5 and SeqKit 2.13.0.

## Release status
Submission package: `v1.0.0-submission`. Before DOI archival, add the final DOI and, if recovered, the accession/download manifest and original raw-DIAMOND execution command.
