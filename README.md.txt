Differential Gene Expression Analysis of Colorectal Adenocarcinoma
GSE142279 | RNA-Seq | limma | R/Bioconductor

Background
Colorectal cancer (CRC) is one of the leading causes of cancer-related morbidity and mortality worldwide. Tumorigenesis involves widespread transcriptomic reprogramming — alterations in gene expression that drive aberrant cell proliferation, evasion of apoptosis, metabolic rewiring, and immune dysregulation.
RNA sequencing (RNA-Seq) enables genome-wide quantification of transcript abundance, making it a powerful tool for comparing gene expression between disease and healthy tissues. Differential expression analysis identifies genes whose expression levels are statistically altered between conditions, providing molecular insight into disease mechanisms.
This project applies a differential expression workflow to paired colorectal adenocarcinoma and normal tissue samples, using publicly available RNA-Seq data from the NCBI Gene Expression Omnibus (GEO).

Objective
To identify differentially expressed genes (DEGs) between colorectal adenocarcinoma tumor tissues and matched normal tissues, and to interpret the transcriptional alterations in the context of colorectal cancer biology.

Data Source
Field	Details
GEO Accession	GSE142279
Platform	RNA-Seq (FPKM-normalized)
Organism	Homo sapiens
Tissue	Colorectal adenocarcinoma vs. matched normal colon tissue
Total Samples	4
Tumor Samples	2
Normal Samples	2
Design	Paired tumor-normal comparison

Significance of this dataset?
Colorectal cancer remains one of the leading causes of cancer-related morbidity and mortality worldwide. This dataset provides paired tumor-normal RNA-Seq samples, enabling direct comparison of transcriptional changes associated with tumorigenesis. The paired design reduces inter-individual variability, increasing the statistical power to detect biologically meaningful differences.

Workflow
```
GEO (GSE142279)
      │
      ▼
Processed FPKM Matrix (downloaded)
      │
      ▼
Data Import \\\& Preprocessing in R
  - Log2 transformation
  - Filtering of low-expression genes
      │
      ▼
Differential Expression Analysis
  - limma (Bioconductor)
  - Paired tumor vs. normal design matrix
  - Adjusted p-value threshold: 0.05 (Benjamini-Hochberg FDR)
      │
      ▼
Visualisation
  - PCA plot
  - Volcano plot
  - DEG.csv (top DEGs)
      │
      ▼
Interpretation \\\& Reporting


> Note: Raw FASTQ processing steps (trimming, alignment, quantification) were not performed in this analysis. The starting point was the processed FPKM expression matrix available on GEO.



## Results

### Summary

|Metric|Count|
|-|-|
|Total genes tested | 12,407|
|Total DEGs (adj. p < 0.05) | \*\*1,043\*\*|
|Upregulated in tumor | \*\*512\*\*|
|Downregulated in tumor | \*\*531\*\*|

\\---

### Top Upregulated Genes \*(ranked by log fold change)\*

|Gene Symbol|Ensembl ID|log₂FC|Function|
|-|-|-|-|
|\*S100P\*|ENSG00000163993|5.37|Calcium-binding protein; metastasis-associated|
|\*CA9\*|ENSG00000107159|5.05|Carbonic anhydrase IX; hypoxia marker; tumour microenvironment|
|\*CXCL8\*|ENSG00000169429|4.57|Pro-inflammatory chemokine; angiogenesis and immune recruitment|
|\*TACSTD2\*|ENSG00000184292|4.50|Tumour-associated calcium signal transducer; epithelial cancer marker|
|\*ETV4\*|ENSG00000175832|4.46|ETS transcription factor; invasion and metastasis|
|\*MMP7\*|ENSG00000137673|4.43|Matrix metalloproteinase; extracellular matrix remodelling|

#### Additionally Highly Upregulated

|Gene Symbol|Ensembl ID|Function|
|-|-|-|
|\*PRSS22\*|ENSG00000005001|Serine protease; proteolytic activity in tumour environment|
|\*SPP1\*|ENSG00000118785|Osteopontin; cell adhesion and tumour progression|
|\*TCN1\*|ENSG00000134827|Transcobalamin-1; vitamin B12 transport; elevated in GI cancers|
|\*CLDN2\*|ENSG00000165376|Claudin-2; tight junction protein; upregulated in colorectal cancer|

\\---

### Top Downregulated Genes \*(ranked by log fold change)\*

|Gene Symbol|Ensembl ID|log₂FC|Function|
|-|-|-|-|
|\*AQP8\*|ENSG00000103375|−7.23|Aquaporin-8; water channel; expressed in normal colonic epithelium|
|\*ZG16\*|ENSG00000174992|−6.15|Zymogen granule protein; mucosal barrier and secretory function|
|\*SLC26A3\*|ENSG00000091138|−6.14|Chloride/bicarbonate exchanger; intestinal ion transport|
|\*GUCA2A\*|ENSG00000197273|−5.98|Guanylate cyclase activator; normal colonic epithelial differentiation|
|\*GUCA2B\*|ENSG00000044012|−5.88|Guanylate cyclase activator; intestinal secretion regulation|
|\*IGHA2\*|ENSG00000211890|−5.87|Immunoglobulin heavy constant alpha-2; mucosal IgA immunity|

#### Additionally Highly Downregulated

|Gene Symbol|Ensembl ID|Function|
|-|-|-|
|\*JCHAIN\*|ENSG00000132465|Joining chain of multimeric IgA and IgM; mucosal immune response|
|\*IGHA1\*|ENSG00000211895|Immunoglobulin heavy constant alpha-1; mucosal IgA response|
|\*CEACAM7\*|ENSG00000007306|Carcinoembryonic antigen-related cell adhesion molecule; epithelial differentiation|
|\*CLCA4\*|ENSG00000016602|Calcium-activated chloride channel regulator; epithelial barrier function|





Biological Interpretation
The analysis identified 1,043 differentially expressed genes between colorectal adenocarcinoma and matched normal tissues, indicating extensive transcriptomic reprogramming associated with tumour development.

Upregulated genes reflect hallmarks of cancer biology. S100P and CA9 point to a hypoxic, metabolically stressed tumour microenvironment — CA9 is a direct target of HIF-1α and serves as a reliable hypoxia biomarker in solid tumours. CXCL8 drives pro-inflammatory signalling, immune cell recruitment, and angiogenesis, all of which support tumour growth. TACSTD2 (TROP2) is a well-established epithelial cancer antigen currently targeted in antibody-drug conjugate therapies. ETV4, an ETS family transcription factor, promotes tumour invasion and metastasis, while MMP7 degrades extracellular matrix components to facilitate local spread. The upregulation of tight junction protein CLDN2 and secretory protease PRSS22 further reflects remodelling of the epithelial architecture in tumour tissue. SPP1 (Osteopontin) and TCN1 are frequently elevated in gastrointestinal malignancies and have been proposed as circulating biomarker candidates.

Downregulated genes highlight a profound loss of normal colonic epithelial identity. AQP8, SLC26A3, GUCA2A, and GUCA2B are all highly expressed in differentiated colonocytes and are responsible for water transport, ion exchange, and secretory signalling in the normal colon. Their collective downregulation is consistent with the dedifferentiation that characterises colorectal adenocarcinoma. ZG16 is a lectin involved in mucosal barrier function and is among the most consistently downregulated genes in colorectal cancer transcriptomic studies. The loss of immunoglobulin-related genes (IGHA1, IGHA2, JCHAIN) and CEACAM7 suggests altered mucosal immune defence and disrupted cell adhesion programmes in the tumour epithelium. CLCA4 downregulation has been linked to loss of epithelial differentiation and increased tumour aggressiveness in colorectal cancer.

Collectively, these findings reveal dysregulation across cell proliferation, apoptosis, metabolic adaptation, extracellular matrix remodelling, ion transport, epithelial differentiation, and mucosal immunity — processes central to colorectal carcinogenesis.

By identifying genes and pathways altered in colorectal adenocarcinoma, this analysis contributes to understanding disease mechanisms and highlights potential candidates for future biomarker discovery and therapeutic target investigations



## Tools Used

|Tool / Package|Purpose|
|-|-|
|R (v4.x)|              Statistical computing environment|
|limma (Bioconductor)| Differential expression analysis|
|ggplot2|               Volcano plot visualisation|
|pheatmap|                Heatmap of top DEGs|
|GEOquery|                 GEO data retrieval|
|dplyr /             tidyverse |Data wrangling|



## Repository Structure

```
Transcriptomic-Analysis-of-Colorectal-Adenocarcinoma-Using-Public-FPKM-Expression-Data/
├── README.md
├── .gitignore
├── .RData
├── .Rhistory
├── figures/
│   ├── pca_plot.png
│   ├── volcano_plot.png
│   └── heatmap_top50.png
├── results/
│   ├── DEGs_from_GEO_FPKM.csv
│   └── significant_DEGs.csv
└── meta/
```





## About the Author

\*\*Abdul-Waliyy Ayandiran\*\* is a final-year Physiology student at the University of Lagos with interests in bioinformatics, genomics, cancer biology, and translational physiology. His work focuses on applying computational approaches to investigate disease mechanisms and support precision medicine research.
