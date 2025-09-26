## Goal: Since WGS BAM files are often huge, using samtools to slice region of interest would be apprachable.

### Step1. Startup script file to update SAMtools to the current version

To set up correct version of samtools, follow the reference: 

- [Update samtools](https://support.terra.bio/hc/en-us/articles/20830480758555-Using-GA4GH-DRS-URIs-and-SAMtools-for-interacting-with-genomic-data-files)


below is the setup script for update samtools, to save it, once in the workspace webpage, go to **Browse Workspace files** on the right side with folder icon on it. 
Once enter can create/upload files. save below script as xxx.sh  and click copy URL once it saved.

```
#! /usr/bin/env bash

apt update

conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge
conda install "SAMtools>=1.13"

```
To create VM, select Juypter setting so that it will have vitiual linux termainal eariser for linux user negation.
With the URL copy now can enter this copied URL below **Startup script Optional** when createing VM and select desire CPUs memory etc. 

### Step2.

Once VM is created, first check the samtools version to see `samtools v1.21`

Below is the step in terminal 

```
test
gs://fc-secure-8df0d2f5-1c5c-4150-8da6-771e376c42f6/phs003181.v2.p1/data_files/NABEC_KEN-1066_FTX/reads/NABEC_KEN-1066_FTX.GRCh38.bam

export GCS_OAUTH_TOKEN=$(gcloud auth application-default print-access-token) # Note: only 1 hour usage, after that had to reactivate again

# othter way is use below to continue activate 

gcloud auth application-default login

# Set the billing project ID (or number) that should be charged
export GCS_REQUESTER_PAYS_PROJECT=<YOUR_PROJECT_ID> # get this gcp id from click the cloned dashborad, and see id of the bucket "Google Project ID"

# check to see if it can now see BAM files
samtools view -b gs://BUCKET/path/reads.bam | head 


```

In other to dowlonad multiple bam files, first create the link file.
the file will look like with each line represent the link of bam file:
```
 gs://xxx/xxx/A549.bam
 gs://xxx/xxx/RT4.bam
 ...
```
To slice it for list of WGS download link in WGS_list.txt:

```
mkdir ~/bam_slice

outdir=/home/jupyter/bam_slice
region="chr14:94672700-96481700"
mkdir -p "$outdir"

while IFS= read -r i; do
  base="$(basename "$i")"   # e.g. CDS-EQ7NTo.bam
  out="$outdir/${base%.bam}_chr14_94672700_96481700.bam"
  samtools view "$i" "$region" -b -o "$out"
done < WGS_list.txt

```
Now we have the files saved in the VM storage, have to move to our workspace

located the workspacce gcp adress, it on the right side of Dashbroad with something look like `fc-secure-xxxx`
copy the path and use the `gsutil` to copy the files look like below example
you can also create the folder for easier negavation

## ! Note: below is still underdevelopment, there may be faster way to do that.

`gsutil cp -r /home/jupyter/bam_slice gs://fc-secure-xxxx/project1/`

Now save the files to local by using `gutil` as well.

Below is example to save files in the current dictionary

`gsutil -u bucket_id cp -r gs://fc-secure-xxxx/project1/ .` 




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


