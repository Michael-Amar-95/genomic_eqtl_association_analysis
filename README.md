# BXD eQTL Analysis

## Overview

This project investigates the genetic basis of gene expression variation in BXD recombinant inbred mouse strains using genome-wide eQTL analysis.

The analysis integrates genotype and gene expression data to identify genetic loci associated with gene expression levels, distinguish cis-acting and trans-acting eQTLs, and identify genomic regions containing trans-regulatory hotspots.

The complete analysis was implemented in Python using a Jupyter Notebook.

## Biological Context

BXD recombinant inbred lines are genetically defined mouse strains that can be used to study relationships between genetic variation and phenotypic or molecular traits.

In this project, gene expression measurements were analyzed together with genomic SNP information to identify loci associated with variation in gene expression.

An expression quantitative trait locus (eQTL) is a genomic locus associated with the expression level of a gene.

Two types of eQTLs were investigated:

- **Cis-eQTL** – the associated SNP is located within 2 Mbp of the regulated gene.
- **Trans-eQTL** – the associated SNP is located more than 2 Mbp from the regulated gene.

## Analysis Pipeline

The analysis consists of the following stages:

1. Genotype preprocessing and representative SNP selection
2. Gene expression preprocessing
3. Aggregation of expression measurements across individuals from the same BXD strain
4. Genome-wide association testing
5. Identification of the strongest eQTL for each gene
6. Multiple-testing correction using False Discovery Rate (FDR)
7. Classification of significant associations into cis and trans eQTLs
8. Identification of trans-eQTL hotspots
9. Statistical and graphical analysis of the resulting associations

## Genotype Preprocessing

Genotype information was obtained from the BXD genotyping data.

To reduce redundant genomic markers, neighboring loci with identical genotype information across the BXD strains were filtered, retaining representative genomic loci.

This reduces the number of redundant association tests while preserving the relevant genetic information.

## Gene Expression Preprocessing

Gene expression data were provided as a matrix in which:

- Rows represent genes
- Columns represent BXD strains

When multiple individuals from the same strain were available, their expression measurements were averaged to obtain a representative expression value for each strain.

This produced a strain-level expression matrix suitable for association analysis with the genotype data.

## Genome-Wide Association Analysis

For each gene, its expression level was tested for association with the genotype at each representative genomic locus.

The analysis used:

- F-tests
- Linear regression
- Association tests
- P-values for statistical significance
- False Discovery Rate (FDR) correction for multiple testing

The association analysis was performed across the genome to identify genomic loci whose genotype is significantly associated with variation in gene expression.

For each gene, the strongest associated eQTLs were identified based on the association statistics.

## Statistical Methods

### F-test

F-tests were used to evaluate whether genotype groups explain a significant amount of variation in gene expression.

### Linear Regression

Linear regression was used to model the relationship between genotype and gene expression.

Conceptually:

```text
Gene Expression ~ Genotype
The resulting statistical significance provides a measure of evidence for an association between a genomic locus and gene expression.

## Association Tests

Genome-wide association tests were performed between representative SNP loci and gene expression measurements.

The resulting P-values were used to identify the strongest genotype-expression associations.

## False Discovery Rate (FDR)

Because thousands of SNP-gene associations were tested, multiple-testing correction was required.

False Discovery Rate (FDR) correction was applied to control the expected proportion of false discoveries among the statistically significant associations.

## Cis and Trans eQTLs

Significant SNP-gene associations were classified according to their genomic distance.

- **Cis-eQTL:** SNP-gene distance ≤ 2 Mbp
- **Trans-eQTL:** SNP-gene distance > 2 Mbp

This distinction allows local regulatory effects to be separated from long-range regulatory effects.

## Visualization

Several visualizations were generated to characterize the eQTL landscape.

### Number of Genes Associated with Each eQTL

The number of genes significantly associated with each genomic locus was calculated and plotted across the genome.

Regions associated with a large number of genes can indicate potential **trans-eQTL hotspots**.

### Cis vs. Trans P-value Distribution

The distributions of association P-values were compared between cis-associated and trans-associated genes.

This provides a statistical view of the differences between local and distant regulatory associations.

### Genome-Wide eQTL Visualization

A genome-wide scatter plot was generated to visualize the locations and strengths of gene-locus associations.

The visualization highlights:

- Cis-eQTLs
- Trans-eQTLs
- Strong associations
- Potential trans-regulatory hotspots

## Technologies and Methods

- Python
- Jupyter Notebook
- Statistical genetics
- eQTL mapping
- F-tests
- Linear regression
- Genome-wide association testing
- False Discovery Rate (FDR)
- Genomic data preprocessing
- Statistical data visualization
