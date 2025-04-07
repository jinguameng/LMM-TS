# LMM-TS
Longitudinal GWAS with Classic LMM Two-Step Approach

![LMM-TS drawio](https://github.com/user-attachments/assets/fce2e812-fd0e-4db0-a73f-bd93f6f8f073)


# Arguments
**pheno_file**: Full path to the phenotype file, longitudinal dataset with long-format
  - RDS format
  - covariates should be included for LMM analysis
  - FID and IID columns should also be included
  - Example pheno_file: /data/h_vmac/zhanm32/SPAREAD/DATA/ADNI/CTS_ADNI.rds

**geno_file**: Full path to the genotype file, file prefix included (PLINK .bim format)

**frq_file**: Full path and full name of the SNP frequency file (e.g. /data/h_vmac/zhanm32/SPAREAD/DATA/ADNI/ADNI_EUR_snpweights_baseline_frq.frq)

**id_col**: Column name in the phenotype file representing subject IDs

**time_col**: Column name in the phenotype file representing time variable

**y_col**: Outcome variable column name

**fixedEffects**: Comma-separated list of fixed effects for LMM model (e.g., "Age,Sex,Education")

**outpath**: Full path to save the LMM-TS outputs

**outprefix**: Prefix of output

# Example Usaga
Rscript /data/h_vmac/zhanm32/SPAREAD/CODE/scripts/LMMTS.R \
"/data/h_vmac/zhanm32/SPAREAD/DATA/ADNI/CTS_ADNI.rds" \
"/data/h_vmac/zhanm32/SPAREAD/DATA/ADNI/ADNI_EUR_snpweights_baseline" \
"/data/h_vmac/zhanm32/SPAREAD/DATA/ADNI/ADNI_EUR_snpweights_baseline_frq.frq" \
"ID" \
"interval_years" \
"SPARE_AD" \
"Sex,PHC_Age_T1_MUSE,Education" \
"/data/h_vmac/zhanm32/SPAREAD/OUTPUT/longitudinalGWAS/LMMTS/" \
"EUR_ADNI"

# Important Note
- Required packages: data.table, lme4, lmerTest, tidyverse, qqman
- Ensure that the phenotype file is cleaned before running this script:
  1. handle missingness yourself before running the R script
  2. make sure at least two time points per individuals
  3. make sure the pheno_file include FID and IID columns that matching the geno file
- Current code only support quantitative trait. 
