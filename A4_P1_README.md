Assignment 4 – Part 1: Gene Expression Analysis

Author: Devika Ranjith
Date: October 2025
Files:

Assignment4_Part1-1.Rmd
gene_expression.tsv
output/ (for text outputs)
figures/ (for plots)

1. Project Overview

This project analyses a gene expression dataset as part of Assignment 4 (Part 1).
The purpose is to develop data analysis and problem-solving skills in RStudio, demonstrate effective data handling, and generate meaningful insights from gene expression data.

The repository includes:

R Markdown code to read, process, and visualize gene expression data.
Comments within the code explaining each step.
Output directories (output/ and figures/) for saving results and visualizations.

2. Data Description

Input file:
gene_expression.tsv — A tab-separated file containing gene expression levels across multiple samples.
Rows: represent individual genes (identified by gene IDs).
Columns: represent expression values for different samples.
The file is automatically downloaded in the R script from the following URL:
https://raw.githubusercontent.com/ghazkha/Assessment4/main/gene_expression.tsv

3. Script Breakdown
Q1 – Read the Data

Purpose:
Import the gene_expression.tsv file into R with gene IDs as row names.

Code summary:
Reads the TSV file using read.table().
Uses header = TRUE and sep = "\t" for tab separation.
Displays the first few rows to confirm successful import.

Input: gene_expression.tsv
Output: gene_expr data frame in R

Q2 – Calculate Mean Expression

Purpose:
Compute the average expression value for each gene across all samples.

Code summary:
Adds a new column mean_expr to the data frame.
Uses rowMeans() to calculate the mean of each gene’s expression values.
Displays the first six genes with calculated mean values.

Output:

Updated gene_expr with a new column mean_expr.
Output displayed in the R console.

Q3 – Identify Top 10 Highly Expressed Genes

Purpose:
Find the 10 genes with the highest mean expression values.

Code summary:
Sorts all genes in descending order of mean_expr.
Selects and displays the top 10 genes.

Output:
A table of 10 genes with the highest mean expression values, shown in R.

Q4 – Count Lowly Expressed Genes

Purpose:
Determine how many genes have a mean expression level less than 10.

Code summary:
Uses sum(gene_expr$mean_expr < 10) to count genes below the threshold.
Displays the total count.

Output:
A numeric value printed in R representing the count of lowly expressed genes.

Q5 – Plot Distribution of Gene Expression

Purpose:
Visualize the distribution of mean gene expression values.

Code summary:
Creates a histogram using the hist() function.
Uses 20 bins with blue shading and black borders.
Adds labels and a title for clarity.
Saved in the figures/ folder.

Input:
gene_expr$mean_expr values

Output:
Histogram plot titled “Distribution of Mean Gene Expression”
Displayed in R and optionally saved in figures/

4. Output Structure
Folder	Description
/data	Contains input dataset gene_expression.tsv.
/output	Can store processed tables or text outputs if required.
/figures	Stores generated plots such as histograms.

5. Summary

This analysis provides an introduction to:
Data import and cleaning using R
Basic descriptive statistics (mean expression)
Ranking and filtering data
Generating visual summaries (histograms)

The code is structured and commented for readability and reproducibility.Each section corresponds directly to assignment questions and accurately addresses the required analyses.

Assignment 4 – Part 1-2: Growth Data Analysis

Author: Devika Ranjith
Date: October 2025
Files:

Assignment4_Part1.Rmd
growth_data.csv
output/ (for summary tables and text outputs)
figures/ (for generated plots)

1. Project Overview

This analysis explores tree growth over time using a dataset (growth_data.csv) containing circumference measurements at multiple time points across two study sites (“northeast” and “southwest”).

The purpose is to:
Summarize and visualize tree growth data,
Compare growth trends between sites,
Conduct a statistical test (t-test) to evaluate whether growth differs significantly between the two locations.
This section demonstrates proficiency in data summarization, visualization, and statistical testing in R.

2. Data Description

Input file:
growth_data.csv — a comma-separated file with tree growth measurements.

Columns include:
Tree_ID: unique identifier for each tree
Site: study location (northeast or southwest)
Circumf_2005_cm: circumference measured in 2005 (cm)
Circumf_2010_cm: circumference measured in 2010 (cm)
Circumf_2020_cm: circumference measured in 2020 (cm)

The file is automatically downloaded in the R script from:
https://raw.githubusercontent.com/ghazkha/Assessment4/main/growth_data.csv

3. Script Breakdown

Q6 – Column Names
Purpose:
Verify the structure of the dataset by listing all column names.

Code summary:
Ensures the output directory exists.
Extracts and saves column names as a CSV file for documentation.

Input: growth_data.csv
Output: Console display of column names
output/q06_column_names.csv

Q7 – Mean and Standard Deviation (2005 & 2020) by Site

Purpose:
Compute descriptive statistics (mean and standard deviation) for tree circumference at two time points (2005 and 2020) across sites.

Code summary:
Uses aggregate() to calculate mean and standard deviation by site.
Merges the two summary tables for a clear comparison.
Writes the results to a CSV file.

Input: growth_data.csv
Output:output/q07_mean_sd_2005_2020_by_site.csv

Displays table of mean and SD values for both years per site

Q8 – Boxplots of Tree Circumference

Purpose:
Visualize differences in tree circumference between sites in 2005 and 2020.

Code summary:
Creates two side-by-side boxplots showing circumference by site for 2005 and 2020.
Adds descriptive titles, axis labels, and colors.
Saves the combined plot as a PNG image in the figures/ directory.

Input: growth_data.csv
Output: figures/fig_q08_boxplot_2005_2020_by_site.png

Visualization of growth variation between sites and across years

Q9 – Mean Growth (2010–2020) by Site

Purpose:
Calculate the average tree growth over the most recent 10-year period (2010–2020) for each site.

Code summary:
Computes growth per tree: 2020 circumference - 2010 circumference.
Aggregates by site to find mean growth.

Displays results in the R console.

Input: growth_data.csv
Output: Table of mean growth per site (printed in console)

Q10 – Two-Sample t-Test

Purpose:
Statistically compare growth between the two sites to determine if the difference is significant.

Code summary:
Separates data into two groups: northeast and southwest.
Performs a two-sample t-test using t.test().
Extracts and prints the p-value to determine significance.

Interpretation:
A small p-value (< 0.05) suggests a significant difference in 10-year growth between the two sites.

Input: growth_data.csv
Output: t-test results displayed in the console
Numeric p-value printed

4. Output Structure
Folder	Description
/data	Contains input dataset growth_data.csv.
/output	Stores result tables such as mean/SD summaries and column names.
/figures	Contains generated visualizations (e.g., boxplots).

5. Summary
This analysis provides:
A clear summary of tree growth data by site and time,
Visual evidence of growth trends using boxplots, and
A statistical comparison between sites using a t-test.

Together, these steps address the assignment questions accurately and demonstrate the use of R for data analysis, visualization, and statistical testing in environmental datasets.