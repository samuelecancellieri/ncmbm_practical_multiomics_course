# NCMBM Practical Multiomics Course

This repository contains practical materials for the NCMBM (Norwegian Centre for Molecular Biosciences and Medicine) course on multiomics analysis. The course introduces students to performing analysis of bulk genomic assays, including RNA-seq, ChIP-seq, and ATAC-seq, with a focus on data interpretation.

## Course Overview

This hands-on course provides students with the fundamental skills needed to analyze and interpret bulk multiomics data. Through Jupyter notebooks, students will learn to process raw sequencing data, perform quality control, align reads, and interpret biological results.

## Contents

This repository includes the following analysis pipelines:

### 1. RNA-seq Analysis

- **Notebook**: `rnaPipeline_star_alignment_paired.ipynb`
- **Description**: RNA sequencing analysis pipeline using STAR aligner for paired-end reads. Learn to quantify gene expression and identify differentially expressed genes.

### 2. ChIP-seq Analysis

- **Notebook**: `chipPipeline_bowtie2_single.ipynb`
- **Description**: Chromatin immunoprecipitation sequencing pipeline using Bowtie2 for single-end reads. Analyze protein-DNA interactions and histone modifications.
- **Notebook**: `chipPipeline_peakcalling.ipynb`
- **Description**: Peak calling workflow for ChIP-seq data to identify enriched genomic regions.

### 3. ATAC-seq Analysis

- **Notebook**: `atacPipeline_bowtie2.ipynb`
- **Description**: Assay for Transposase-Accessible Chromatin sequencing pipeline using Bowtie2. Explore chromatin accessibility and open chromatin regions.

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

1. **Clone the repository**:

   ```bash
   git clone <repository-url>
   cd ncmbm_practical_multiomics_course
   ```

2. **Set up your environment**:

   - Install required bioinformatics tools
   - Ensure Jupyter is installed: `pip install jupyter`

3. **Launch Jupyter**:

   ```bash
   jupyter notebook
   ```

4. **Open notebooks**:
   - Start with the pipeline relevant to your current module
   - Follow the instructions within each notebook

## Workflow Structure

Each notebook follows a typical bioinformatics pipeline structure:

1. **Data Preparation**: Download or locate input data
2. **Quality Control**: Assess raw data quality
3. **Preprocessing**: Trim adapters and filter low-quality reads
4. **Alignment**: Map reads to reference genome
5. **Post-processing**: Sort, index, and filter aligned reads
6. **Analysis**: Quantification, peak calling, or feature counting
7. **Visualization**: Generate plots and summary statistics
8. **Interpretation**: Biological insights and conclusions

## Data Interpretation

The course emphasizes not just running tools, but understanding and interpreting results:

- **RNA-seq**: Differential expression patterns, pathway analysis, biological significance
- **ChIP-seq**: Transcription factor binding sites, histone modification patterns, regulatory elements
- **ATAC-seq**: Open chromatin regions, nucleosome positioning, regulatory landscapes

## Best Practices

- Always perform quality control before and after each processing step
- Document your analysis parameters and decisions
- Visualize data at multiple stages to catch potential issues
- Consider biological replicates and statistical significance
- Integrate results across multiple assay types for comprehensive insights

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
