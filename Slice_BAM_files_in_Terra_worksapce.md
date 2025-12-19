# SAMtools WGS BAM File Processing Guide

## Goal
Since WGS BAM files are often huge, using SAMtools to slice regions of interest is an approachable solution.

## Step 1: Startup Script to Update SAMtools to Current Version

To set up the correct version of SAMtools, follow this reference: 
- [Update SAMtools](https://support.terra.bio/hc/en-us/articles/20830480758555-Using-GA4GH-DRS-URIs-and-SAMtools-for-interacting-with-genomic-data-files)

Below is the setup script to update SAMtools. To save it, go to your workspace webpage and click **Browse Workspace files** on the right side (folder icon). Once there, you can create/upload files. Save the script below as `xxx.sh` and click "Copy URL" once saved.

```bash
#!/usr/bin/env bash
apt update
conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge
conda install "SAMtools>=1.13"
```

To create a VM, select Jupyter settings so it will have a virtual Linux terminal for easier Linux user navigation. With the copied URL, you can now enter this URL in the **Startup script (Optional)** field when creating the VM and select desired CPUs, memory, etc.

## Step 2: Setting Up and Using SAMtools

Once the VM is created, first check the SAMtools version to confirm `samtools v1.21` is installed.

Below are the steps in the terminal:

```bash
# Test with example BAM file
gs://fc-secure-8df0d2f5-1c5c-4150-8da6-771e376c42f6/phs003181.v2.p1/data_files/NABEC_KEN-1066_FTX/reads/NABEC_KEN-1066_FTX.GRCh38.bam

# Set up authentication (Note: only valid for 1 hour, reactivate as needed)
export GCS_OAUTH_TOKEN=$(gcloud auth application-default print-access-token)

# Alternative way to continue activation
gcloud auth application-default login

# Set the billing project ID that should be charged
export GCS_REQUESTER_PAYS_PROJECT=<YOUR_PROJECT_ID>  # Get this GCP ID from the cloned dashboard bucket "Google Project ID"

# Check if you can now access BAM files
samtools view -b gs://BUCKET/path/reads.bam | head 
```

### Processing Multiple BAM Files

To download multiple BAM files, first create a link file. The file should look like this, with each line representing a BAM file link:
**THIS PART SHOULD BE MORE DETAILED**

```
gs://xxx/xxx/A549.bam
gs://xxx/xxx/RT4.bam
...
```

save it as `WGS_list.txt`:

```bash
mkdir ~/bam_slice
outdir=/home/jupyter/bam_slice
region="chr14:94672700-96481700"
mkdir -p "$outdir"

while IFS= read -r i; do
  base="$(basename "$i")"   # e.g. CDS-EQ7NTo.bam
  out="$outdir/${base%.bam}_chr14.bam"
  samtools view "$i" "$region" -b -o "$out"
done < WGS_list.txt
```

### Transferring Files to Workspace

Now that the files are saved in VM storage, you need to move them to your workspace. Locate the workspace GCP address on the right side of the dashboard (something like `fc-secure-xxxx`). Copy this path and use `gsutil` to transfer the files as shown in the example below. You can also create folders for easier navigation.

**Note: The following is still under development; there may be faster methods.**

```bash
gsutil cp -r /home/jupyter/bam_slice gs://fc-secure-xxxx/project1/
```

To save files locally, use `gsutil` as well. Below is an example to save files in the current directory:

```bash
gsutil -u bucket_id cp -r gs://fc-secure-xxxx/project1/ .
```

---

## Alternative: Downloading BAM Files on Helix/Biowulf

Helix in Biowulf and CCAD2 can use the `gsutil` command to download files directly.

### Example Process:

```bash
# Once logged into Helix/CCAD2
module load google-cloud-sdk

# Follow the URL to login to Google
gcloud auth login

# Once successful, use the following command
gsutil -u <PROJECT_ID> cp 'gs://fc-secure-ff8156a3-ddf3-42e4-9211-0fd89da62108/xxx.md.bam' .
```
