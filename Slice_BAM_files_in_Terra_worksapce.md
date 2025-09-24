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


### Update!

- samtools v1.21

Once set up this and GCP seems work!

```
test
gs://fc-secure-8df0d2f5-1c5c-4150-8da6-771e376c42f6/phs003181.v2.p1/data_files/NABEC_KEN-1066_FTX/reads/NABEC_KEN-1066_FTX.GRCh38.bam

export GCS_OAUTH_TOKEN=$(gcloud auth application-default print-access-token) # Note: only 1 hour usage, after that had to reactivate again

# othter way is use below to continue activate 

gcloud auth application-default login

# Set the billing project ID (or number) that should be charged
export GCS_REQUESTER_PAYS_PROJECT=<YOUR_PROJECT_ID> # get this gcp id from click the cloned dashborad, and see id of the bucket "Google Project ID"

samtools view -b gs://BUCKET/path/reads.bam | head 

```
********************************************
********************************************

## For downloading BAM file

### Helix in Biowulf and ccad2 can use gsutil command to download stuff

- example as below
  
```
# once login to Helix/CCAD2

module load google-cloud-sdk

# follow URL to login google
gcloud auth login

# once sucess, use code shown before
gsutil -u <PROJECT_ID> cp 'gs://fc-secure-ff8156a3-ddf3-42e4-9211-0fd89da62108/xxx.md.bam' .


```


