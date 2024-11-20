# Color Blindness Analysis:

## Overview
This project analyzes X chromosome data to study gene configurations associated with color blindness. The goal is to align sequencing reads to the reference sequence, map them to the red and green gene exons, and determine the most likely configuration responsible for color blindness.

---

## Problem Statement
The assignment involves:
1. Aligning 3 million reads to the X chromosome reference sequence using the Burrows-Wheeler Transform (BWT) with up to **two mismatches**.
2. Counting reads mapping to exons of the **red** and **green** genes:
   - **Unambiguous mapping**: Count as 1.
   - **Ambiguous mapping**: Count as 0.5 for each gene.
3. Calculating probabilities for different gene configurations and identifying the most probable configuration responsible for color blindness.

---

## Dataset
The following files are used in the analysis:
1. **`chrX.fa`**: The X chromosome's reference sequence in FASTA format.
2. **`reads`**: Contains sequencing reads for alignment to the reference sequence.
3. **`chrX_map.txt`**: Provides exon positions for the red and green genes.
4. **`chrX_last_col.txt`**: The last column of the Burrows-Wheeler Transform (BWT) of the X chromosome reference sequence.

---

## Approach
### Step 1: Data Preprocessing
- **Reference Sequence**: The reference sequence is processed from the FASTA file, concatenating all sequence lines into a single continuous string.
- **Reads**: Sequencing reads are preprocessed to replace 'N' with 'A' for compatibility with genomic alignment.
- **Exon Locations**: Exon positions for the red and green genes are loaded and organized for mapping purposes.
- **BWT Data**: The BWT last column is read along with rank and count information for efficient read alignment.

### Step 2: Read Alignment
Reads are aligned to the reference sequence using a sliding window approach, allowing up to two mismatches per alignment. The Burrows-Wheeler Transform data is utilized to optimize this process.

### Step 3: Gene Mapping
Aligned reads are mapped to the exons of the red and green genes. Counts are calculated:
- **1 for unambiguous mapping**: Read maps uniquely to one gene.
- **0.5 for ambiguous mapping**: Read maps to both genes.

### Step 4: Configuration Probabilities
For each gene configuration, the probabilities are calculated based on the total counts of reads mapping to the red and green genes.

---

## Results
The analysis outputs:
1. Total counts of reads mapping to the **red** and **green** genes.
2. Probabilities for each gene configuration.
3. The **most likely configuration** responsible for color blindness, identified as **Config3** in this study.

---

## Key Functions
### Data Processing
- **`process_reference_file`**: Loads and processes the X chromosome reference sequence.
- **`process_reads_file`**: Preprocesses sequencing reads to handle missing nucleotides.
- **`process_exon_locations`**: Loads and extracts exon locations for the red and green genes.
- **`read_bwt_last_column`**: Reads the BWT last column for efficient alignment.

### Read Alignment and Mapping
- **`find_matches_with_mismatches`**: Identifies potential alignment positions allowing up to two mismatches.
- **`count_gene_mappings`**: Counts reads mapping to the red and green gene exons.

### Probabilities and Results
- **`calculate_probabilities`**: Computes configuration probabilities based on gene counts.
- **`align_reads`**: Manages alignment and mapping for all reads.

---

## Conclusion
The analysis reveals that **Config3** has the highest probability among the configurations, suggesting it as the most likely cause of color blindness. The study provides insights into gene configurations and their association with this genetic condition.


