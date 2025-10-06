Assignment 4 – Part 2: Examining biological sequence diversity
Author: Devika Ranjith
Date: 6 October 2025
Course: SLE (Professional Research Practice)
Output Format: R Markdown → HTML

1. Overview

This project performs a comparative genomic analysis between two bacterial species—
Escherichia coli (K-12 substr. MG1655) and Campylobacter coli (GCA_003780985)—
to examine their sequence composition, coding DNA features, and protein-sequence characteristics.

The analysis includes:
Quantifying coding DNA sequences (CDS)
Measuring total coding DNA content
Comparing CDS length distributions
Examining nucleotide and amino-acid frequencies
Assessing codon-usage bias
Profiling k-mer (3–5-mer) composition in protein sequences

The goal is to identify genome-level and proteome-level differences reflecting each organism’s evolutionary adaptations and ecological niches.

2. Data Sources
All sequence data were downloaded directly from the Ensembl Bacteria FTP repository.
Organism	Data URL	File Type	Description
E. coli K-12 MG1655	http://ftp.ensemblgenomes.org/pub/bacteria/release-53/.../Escherichia_coli_str_k_12_substr_mg1655_gca_000005845.ASM584v2.cds.all.fa.gz	.fa.gz	Complete set of coding DNA sequences
C. coli GCA_003780985	https://ftp.ensemblgenomes.ebi.ac.uk/pub/bacteria/release-62/.../Campylobacter_coli_gca_003780985.PDT000395653.1.cds.all.fa.gz	.fa.gz	Complete set of coding DNA sequences

Packages used:
seqinr, R.utils, knitr

3. Project Structure
Folder/File	Purpose
Assignment4_Part2.Rmd	Main R Markdown script performing all analyses
ecoli_cds.fa / campylobacter_coli_cds.fa	Downloaded FASTA files containing CDS sequences
output/	Folder for summary tables and results (optional)
figures/	Folder for plots generated from each analysis (optional)

4. Analytical Workflow

Q1 – Counting Coding DNA Sequences

Purpose: Determine how many CDS sequences each organism possesses.
Inputs: ecoli_cds.fa, campylobacter_coli_cds.fa
Outputs: A summary table showing number of CDS per organism.

Result Summary:
E. coli ≈ 4239 CDS | C. coli ≈ 1976 CDS.
E. coli has > 2× the genes of C. coli, reflecting a larger, more versatile genome.

Q2 – Total Coding DNA Content

Purpose: Compute the total length (bp) of all coding sequences.
Inputs: Same CDS FASTA files.
Outputs: A table with Number of CDS and Total Coding DNA (bp) per organism.

Result Summary:
E. coli: ≈ 3.98 Mb of coding DNA
C. coli: ≈ 1.73 Mb of coding DNA
This confirms E. coli’s larger genome and greater genetic complexity.

Q3 – CDS Length Distribution, Boxplot, and Summary Statistics

Purpose: Compare coding sequence lengths between organisms.
Outputs:
Boxplot of CDS lengths by species
Table with mean and median CDS length

Result Summary:
E. coli mean ≈ 939 bp | median ≈ 831 bp
C. coli mean ≈ 874 bp | median ≈ 750 bp
E. coli genes are slightly longer and more variable, consistent with a broader protein repertoire.

Q4 – Nucleotide and Amino-Acid Frequencies

Purpose: Compare base composition and protein composition between species.
Analyses:
Count DNA bases (A, T, G, C) across all CDS.
Translate CDS to protein and compute amino-acid frequencies.
Visualize frequencies via bar plots.

Outputs:
DNA base frequency plots (E. coli vs C. coli)
Amino acid frequency plots

Interpretation:
E. coli shows higher GC content; C. coli is more AT-rich.
Amino-acid profiles differ slightly—E. coli enriched in leucine, alanine, glycine; C. coli has more polar amino acids.
These reflect genomic composition and environmental adaptation.

Q5 – Codon Usage Bias

Purpose: Quantify codon usage and compare bias between species.
Inputs: Concatenated CDS sequences for each organism.
Outputs: Codon usage tables and bar plots for each organism.

Key Findings:
E. coli prefers codons ending in G/C (third base GC bias).
C. coli prefers codons ending in A/T.
These differences reflect genome-wide GC content and translation optimization for different environments.

Q6 – K-mer Profiling (3–5 aa Length)

Purpose: Identify protein sequence motifs (k-mers) that are over- or under-represented in C. coli compared to E. coli.
Process:
Count 3-, 4-, and 5-mer frequencies in proteomes.
Compare relative frequencies between species.
Plot top 10 over- and under-represented motifs.

Outputs:
Tables of top 10 over- and under-represented k-mers.
Comparative bar plots for each k-value.

Findings:
C. coli overrepresented motifs (AAA, AAL, GAA, LAA) are rich in alanine and leucine—typical of membrane proteins.
Underrepresented motifs (WYR, CCH, RWC) contain bulky or rare residues.
E. coli shows broader distribution of k-mers, indicating greater proteomic diversity.

5. Summary of Findings
Feature	E. coli (K-12 MG1655)	C. coli (GCA_003780985)	Key Differences & Interpretation
Number of CDS	≈ 4239	≈ 1976	E. coli has > 2× more coding genes
Total coding DNA (bp)	≈ 3.98 Mbp	≈ 1.73 Mbp	Reflects larger genome and metabolic diversity of E. coli
Mean CDS length (bp)	939	874	E. coli genes slightly longer and more variable
GC content trend	Higher (G/C bias)	Lower (A/T bias)	Consistent with different genomic stabilities
Codon usage bias	Prefers G/C-ending codons	Prefers A/T-ending codons	Reflects translation optimization and environment
K-mer profile	More diverse distribution	Compact, alanine/leucine-rich motifs	Indicates genomic streamlining in C. coli

6. How the Problem Was Solved

Downloaded and uncompressed FASTA files using R.utils.
Loaded sequences via seqinr::read.fasta().
Counted and summarized CDS to address Q1 & Q2.
Computed sequence lengths, means, medians, and boxplots (Q3).
Calculated base and amino-acid frequencies and visualized via bar plots (Q4).
Generated codon usage tables and plots to quantify bias (Q5).
Performed k-mer frequency analysis for protein motif comparison (Q6).
Provided clear interpretations and comparative descriptions for each step.