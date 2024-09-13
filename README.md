# nifH_microbial_drivers
A data pipeline used to search metagenomes for a gene of interest using a reference database/alignment. 
Jupyter notebooks were used for manual curation of protein sequence collections from outputs of an iterative HMMER search run with Snakemake. 
This pipeline was applied in a searh for nitrogen genes (i.e. nifH) in Tara Oceans metagenomes created by the Alexander Lab at WHOI. 
A list of relevant jupyter notebooks and how they relate to the rest of the analysis is below. 

![analysis map](https://github.com/lnblum/nifH_microbial_drivers/blob/master/analysis_map_3_15.png)
# Tara-gene-finding

Gene-finder pipeline: 
Reference alignments used for this portion of the analysis are found in the gene_alignments folder, organized by gene. Alignments produced from the iterative search technique are also present.

1.	jupyter_notebooks/NifH.ipynb
Summary: Organize gene hits which are returned from the first round of HMMER searches with a set of gene reference sequence against the metagenomes, including limiting the stringency of accepted gene sequences by e-value and extracting desired sequences (to be used in the next round of HMMER searches).

2.	jupyter_notebooks/NifH_rnd2.ipynb
Summary: Organize gene hits which are returned from the second round of HMMER searches against metagenomes (using reference sequences and validated hits from the first round). Gene sequence hits are again limited by e-value and extracting for downstream analysis.

3.	jupyter_notebooks/nifH_combo.ipynb
Summary: Combine unique gene hits from the first two rounds of HMMER searches into a final set of returned gene sequences from the metagenomes.

4.	nifH_MAGs.ipynb
Path: jupyter_notebooks/nifH_MAGs.ipynb
Summary: Associate accepted gene sequence hits from the HMMER search of the metagenomes with high quality MAGs they are found in.

5.	MAGs_analysis.ipynb
Path: jupyter_notebooks/MAGs_analysis.ipynb
Summary:This code is used to create a summary csv table of all MAGs which were found to contain one of the genes of interest and lists the name of the gene found next to the name of the MAG. This list is used to select MAGs of interest for downstream analysis.

Gene abundances pipeline:

1.	results/gene_abundances/nifH_diamond_parse.ipynb
Summary: This code was used to parse diamond output files in order to compute a metric for gene abundance for both metagenomic and metatranscriptomic data. Abundance for each sequence was normalized for multi-mapping reads (when one query sequence maps to multiple similar proteins) as well as the sequencing depth of the associated sample (in reads per million) and the length of the specific protein sequence, from those clustered at 98% identity, to which it matched. This resulted in gene abundance as reads per kilobase million (RPKM).
 
2.	Gene abundance analysis with cartopy

A.	results/gene_abundances/cartopy_abundance_analysis_model.ipynb

Summary: This code was used to create gene abundance visualizations over a global map using Cartopy. 

NifH-encoding MAGs data visualization pipeline:

1. FastANI analysis

mag_analysis/jupyter_notebooks/nifH_fastani_model.ipynb 

Summary: This code was used to analyze the results of fastANI comparison of nifH-encoding MAGs, and to cluster them based on 95% similarity.  CheckM and GTDB-TK outputs were overlayed to inform us about completion/contamination and taxonomy prediction for the MAGs of interest. 

2.	KEGG annotation & gene presence/absence heatmap creation

mag_analysis/jupyter_notebooks/nifH_kegg_annotation_model.ipynb

Shows the method for producing the complete presence/absence table and heatmap from KEGG annotation tables. 

>>>>>>> 6e99b212b6280eba1bb4820b2eb78388186f8feb
