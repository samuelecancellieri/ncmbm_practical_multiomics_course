# NCMBM Practical Multiomics Course

This repository contains practical materials for the NCMBM (Norwegian Centre for Molecular Biosciences and Medicine) course on multiomics analysis. The course introduces students to performing analysis of bulk genomic assays, including RNA-seq, ChIP-seq, and ATAC-seq, with a focus on data interpretation.

## Course Overview

This hands-on course provides students with the fundamental skills needed to analyze and interpret bulk multiomics data. Through Jupyter notebooks, students will learn to process raw sequencing data, perform quality control, align reads, and interpret biological results.

## Contents

This repository includes the following analysis pipelines:

### 1. RNA-seq Analysis

**Notebook**: `rnaPipeline_star_alignment_paired.ipynb`

**What it does**: Processes paired-end RNA sequencing data to measure gene expression levels. The pipeline takes raw sequencing files (FASTQ) and produces a table of gene counts that can be used for differential expression analysis.

**You will learn**:

- Quality control of sequencing reads
- Removing adapters and low-quality bases
- Aligning RNA-seq reads to a reference genome
- Counting how many reads map to each gene

**How to use it**:

1. Open the notebook in Jupyter
2. Update file paths in Step 3 (your input FASTQ files and reference genome)
3. Run each cell sequentially from top to bottom
4. Complete the TODO sections and answer review questions
5. The final output is a gene count matrix ready for statistical analysis

**Key output**: `{sample}_counts.tsv` - table of read counts per gene

### 2. ChIP-seq Analysis

#### Part 1: Sample Processing

**Notebook**: `chipPipeline_bowtie2_single.ipynb`

**What it does**: Processes single-end ChIP-seq sequencing data for both IP (immunoprecipitation) and control samples. This prepares your data for peak calling by aligning reads, removing duplicates, and creating genome browser tracks.

**You will learn**:

- Processing ChIP-seq data from raw reads to clean alignments
- Identifying and removing PCR duplicates
- Assessing library quality metrics
- Creating visualization tracks (BigWig files)

**How to use it**:

1. Run this notebook **twice** - once for your IP sample and once for your control sample
2. Update file paths in Step 3 for each sample
3. Run all cells in order
4. Complete TODO sections and quality checkpoints
5. Keep track of your processed BAM files for peak calling

**Key output**: `{sample}_final.bam` - filtered alignment file for peak calling

#### Part 2: Peak Calling

**Notebook**: `chipPipeline_peakcalling.ipynb`

**What it does**: Identifies genomic regions where your protein of interest binds to DNA by comparing IP vs control samples. This is where you discover the actual binding sites.

**You will learn**:

- Calling peaks using MACS2
- Calculating FRiP score (quality metric)
- Filtering artifact regions using ENCODE blacklist
- Interpreting peak characteristics

**How to use it**:

1. Make sure you've processed both IP and control samples first
2. Update file paths in Step 3 with your BAM files from Part 1
3. Run cells sequentially
4. Answer questions about peak quality and characteristics
5. Use the final filtered peaks for downstream analysis

**Key outputs**:

- `{experiment}_peaks_blacklisted_filtered.narrowPeak` - final peak coordinates
- Quality metrics and peak statistics

### 3. ATAC-seq Analysis

**Notebook**: `atacPipeline_bowtie2.ipynb`

**What it does**: Analyzes ATAC-seq data to identify regions of open chromatin (accessible DNA) genome-wide. The pipeline processes paired-end reads through specialized steps including read shifting and calculates important quality metrics.

**You will learn**:

- Processing ATAC-seq specific data (including hard trimming)
- Removing mitochondrial contamination
- Calculating library complexity metrics (NRF, PBC1, PBC2)
- ATAC-seq specific read shifting for Tn5 transposase
- Calling peaks without a control sample
- Assessing data quality with FRiP score

**How to use it**:

1. Update file paths in Step 3 (paired-end FASTQ files and reference genome)
2. Run cells in order - each step builds on the previous one
3. Complete TODO sections (several commands need completion)
4. Pay attention to quality metrics at each checkpoint
5. Answer review questions to understand the biology

**Key outputs**:

- `{sample}_peaks_blacklist_filtered.narrowPeak` - open chromatin regions
- Quality metrics file with chrM fraction, complexity, and FRiP scores
- BigWig track for genome browser visualization

## Learning Objectives

By completing this course, students will be able to:

- Understand the principles behind different bulk sequencing assays (RNA-seq, ChIP-seq, ATAC-seq)
- Perform quality control on raw sequencing data
- Align sequencing reads to reference genomes using appropriate tools
- Process and normalize sequencing data
- Call peaks and identify genomic features of interest
- Interpret biological significance of multiomics results
- Integrate findings across different assay types

## Prerequisites

### Required Knowledge

- Basic understanding of molecular biology and genomics
- Familiarity with Python programming
- Basic command-line experience (Unix/Linux)

### Software Requirements

- Jupyter Notebook or JupyterLab
- Python 3.x
- Bioinformatics tools:
  - STAR aligner (for RNA-seq)
  - Bowtie2 (for ChIP-seq and ATAC-seq)
  - SAMtools
  - Peak calling software (e.g., MACS2)
  - Quality control tools (e.g., FastQC)

## Getting Started

### Prerequisites

Before starting, make sure you have:

- **Jupyter Notebook** or **JupyterLab** installed
- **Singularity** (for running containerized bioinformatics tools)
- Access to reference genome files (genome index, annotation files)
- Your sequencing data files (FASTQ format)

### Quick Start Guide

1. **Clone the repository**:

   ```bash
   git clone <repository-url>
   cd ncmbm_practical_multiomics_course
   ```

2. **Launch Jupyter**:

   ```bash
   jupyter notebook
   ```

3. **Choose your pipeline**:

   - **RNA-seq**: Start with `rnaPipeline_star_alignment_paired.ipynb`
   - **ChIP-seq**: Begin with `chipPipeline_bowtie2_single.ipynb`, then `chipPipeline_peakcalling.ipynb`
   - **ATAC-seq**: Use `atacPipeline_bowtie2.ipynb`

4. **Configure your notebook**:

   - Open the notebook
   - Go to **Step 3** and update file paths:
     - Your input FASTQ files
     - Output directory location
     - Reference genome paths
     - Singularity bind directory
   - Ask your instructor for reference genome locations

5. **Run the pipeline**:

   - Execute cells one at a time (Shift + Enter)
   - Read the explanations in markdown cells
   - Complete sections marked with `# TODO`
   - Answer review questions to test your understanding

6. **Monitor progress**:
   - Each step prints status messages
   - Check for ✓ (success) or ✗ (error) symbols
   - Review quality metrics at checkpoints

## How the Notebooks Work

### Notebook Structure

All notebooks follow a consistent, easy-to-follow format:

1. **Introduction Section**: Explains what the pipeline does and what you'll learn
2. **Setup Steps**: Import libraries and define tool containers
3. **Configuration**: Set your file paths and parameters (YOU MUST UPDATE THIS)
4. **Processing Steps**: Execute the pipeline step-by-step
5. **Quality Checkpoints**: Review metrics and answer questions
6. **Summary**: Review results and discuss next steps

### Important Features

- **TODO Sections**: Some commands are incomplete - you need to fill in the missing parts (marked with `???`)
- **Review Questions**: After each major step, answer questions to test your understanding
- **Quality Metrics**: At key points, check if your data quality is acceptable
- **Progress Indicators**: Look for ✓ (success) and ✗ (error) symbols in the output

### Cell Execution Order

⚠️ **Important**: Run cells in order from top to bottom. Later cells depend on earlier ones.

### Typical Pipeline Flow

```
Raw Data → Quality Control → Trimming → Alignment → Filtering → Analysis → Results
   ↓             ↓              ↓           ↓           ↓          ↓         ↓
 FASTQ        FastQC        Clean       BAM file   Remove    Peaks/    Summary
  files       reports       reads                  artifacts  Counts    stats
```

### What Makes Each Pipeline Different?

| Pipeline     | Input Type | Alignment Tool | Unique Steps              | Output                 |
| ------------ | ---------- | -------------- | ------------------------- | ---------------------- |
| **RNA-seq**  | Paired-end | STAR           | Gene counting             | Count matrix           |
| **ChIP-seq** | Single-end | Bowtie2        | Peak calling with control | Peak coordinates       |
| **ATAC-seq** | Paired-end | Bowtie2        | Read shifting, no control | Open chromatin regions |

## Data Interpretation

The course emphasizes not just running tools, but understanding and interpreting results:

- **RNA-seq**: Differential expression patterns, pathway analysis, biological significance
- **ChIP-seq**: Transcription factor binding sites, histone modification patterns, regulatory elements
- **ATAC-seq**: Open chromatin regions, nucleosome positioning, regulatory landscapes

## Tips for Success

### Before You Start

- **Ask for help**: Get reference genome file paths from your instructor
- **Test with small data**: If available, start with a subset of reads
- **Read carefully**: Each notebook has detailed explanations
- **Check file paths**: Use absolute paths (starting with /)

### While Running

- **Don't skip cells**: Execute them in order
- **Read the output**: Check for errors or warnings
- **Save your work**: Save the notebook frequently (Ctrl+S)
- **Take notes**: Write down your answers to review questions

### Quality Control Checkpoints

Each pipeline has specific quality metrics to monitor:

**RNA-seq**:

- Alignment rate should be >70%
- Check for high duplication rates

**ChIP-seq**:

- Duplication rate should be <50%
- FRiP score should be >1%
- Need both IP and control samples

**ATAC-seq**:

- Mitochondrial reads should be <10%
- NRF should be >0.8
- FRiP score should be >20%

### Troubleshooting Common Issues

| Problem              | Possible Cause            | Solution                                |
| -------------------- | ------------------------- | --------------------------------------- |
| Container not found  | Singularity not installed | Contact system administrator            |
| File path error      | Incorrect path in Step 3  | Check file exists with `ls` command     |
| Low alignment rate   | Wrong reference genome    | Verify genome version matches your data |
| Out of memory        | Too many threads          | Reduce thread count in Step 3           |
| Missing output files | Previous step failed      | Check earlier cells for errors          |

## Resources

### Reference Materials

- Genome reference files (FASTA, GTF/GFF annotations)
- Index files for aligners
- Example datasets (links provided in notebooks)

### Additional Reading

- Papers on multiomics integration
- Tool documentation and tutorials
- Best practices for sequencing data analysis

## Troubleshooting

Common issues and solutions:

1. **Memory errors**: Reduce number of threads or process smaller data chunks
2. **File path errors**: Ensure all paths are correct and data files exist
3. **Tool not found**: Verify bioinformatics tools are properly installed and in PATH
4. **Alignment issues**: Check reference genome version matches your data

## Contributing

If you find issues or have suggestions for improvements:

- Open an issue in the repository
- Contact the course instructors
- Submit a pull request with your improvements

## Course Information

- **Course**: NCMBM Practical Multiomics
- **Focus**: Bulk RNA-seq, ChIP-seq, and ATAC-seq analysis
- **Level**: Introductory to intermediate

## License

This material is provided for educational purposes. Please cite appropriately if using these materials in other contexts.

## Contact

For questions about the course materials or technical issues, please contact the course instructors.

---

**Last Updated**: November 2025
