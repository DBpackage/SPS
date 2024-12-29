# How to make SPS?
This README provides guidance on how to generate SPS sequences from protein sequences.

## 1. References
To generate SPS sequences from the protein sequences in your unique dataset, the following two studies were referenced:

SCRATCH: A protein structure and structural feature prediction server [https://doi.org/10.1093/nar/gki396]

DeepAffinity: Interpretable deep learning of compound–protein affinity through unified recurrent and convolutional neural networks [https://doi.org/10.1093/bioinformatics/btz111]

Notably, the Supplementary section of the DeepAffinity paper provides detailed explanations of the meaning and generation algorithm for SPS sequences. We recommend referring to it for additional guidance.

## 2. Tools and Environments 
The SCRATCH tool and installation guide can be downloaded from the following link:
[https://download.igb.uci.edu/]

In this study, we used SCRATCH-1D release 2.0 for Ubuntu (2021, Ubuntu Only, 1.4 GB) version.

The structured protein sequence data (.acc, .ss3) obtained using the SCRATCH tool must undergo further grouping through DeepAffinity's SPS generation algorithm to produce final SPS sequences.

To set up the environment for SPS generation on a Linux server, please refer to the following GitHub repository:
[https://github.com/Shen-Lab/DeepAffinity]

* We have provided a yaml file that specifies the environment required to run the SCRATCH tool we used. However, we cannot guarantee that this environment will be installed without conflicts on all user systems.

## 3. SPS generation process:
### 1. Extract Unique Protein Sequences:
Identify and extract unique protein sequences from your Drug-Target Protein pair dataset to avoid redundancy.
### 2. Create FASTA Files:
Divide the unique protein sequences into smaller groups, ensuring each group contains a manageable number of proteins (recommended: up to 200 proteins per FASTA file). Save these groups in FASTA format for input into subsequent steps.
(please refer to 01_Make_Fasta_From_UniqueCSV.ipynb)
### 3. Run SCRATCH-1D Tool:
Use the SCRATCH-1D tool to process the FASTA files. This tool generates .acc (solvent accessibility) and .ss3 (secondary structure) files for each protein sequence.
### 4. Group and Combine Files:
Apply the grouping method provided by DeepAffinity to merge the .acc, .ss3, and FASTA files into the final SPS format. This ensures consistency and compatibility with downstream analyses.
(please refer to 02_Processing_4_SPS.ipynb)
### 5. Repeat for All Proteins:
Iterate steps 2 to 4 until SPS data has been generated for all unique protein sequences.
