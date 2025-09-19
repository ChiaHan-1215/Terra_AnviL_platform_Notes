## Goal: Since WGS BAM files are often huge, using samtools to slice region of interest would be apprachable.

## code:
- [Update samtools](https://support.terra.bio/hc/en-us/articles/20830480758555-Using-GA4GH-DRS-URIs-and-SAMtools-for-interacting-with-genomic-data-files)

Startup script file to update SAMtools to the current version
```
#! /usr/bin/env bash

apt update

conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge
conda install "SAMtools>=1.13"

```

- 
Once create a VM, go to the termainl consle


```
# the key script, the -u bucket is the bucket id used in billing project of this copy of workspace.

gsutil -u <PROJECT_ID> cat gs://cclebams/wgs_hg38/xxx-XVt7q2.hg38.bam \
  | samtools view -b - chr5:123-123456 > chr5_slice.bam


# BUT it's actully cost same amout fee compare to download whole bam first and then slice locally...

# 2, use gcsfuse, still not try out yet

# Mount with billing project (Requester Pays)
mkdir -p ~/gcs-ccle
gcsfuse --billing-project <PROJECT_ID> -o ro cclebams ~/gcs-ccle

# Slice to BAM (uses .bai for random access)
samtools view -b ~/gcs-ccle/wgs_hg38/xxx-XVt7q2.hg38.bam chr5:123-123456 > chr5_slice.bam
samtools index chr5_slice.bam

```
