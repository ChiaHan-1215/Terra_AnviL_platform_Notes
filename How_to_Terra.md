# Goal: The place where store Terra Anvil platform related notes

*********

## Creating a Terra Account and Linking NIH Credentials

### Important Requirements
To create a Terra account that can be linked to NIH credentials, **you cannot use a Google email address** (e.g., `xxx@gmail.com`). Instead, you must set up your Terra account using a non-Google email address, such as your NIH email.

### Step 1: Create Your Terra Account with a non-Google email
Follow the detailed instructions at this link:

https://support.terra.bio/hc/en-us/articles/360029186611-How-to-set-up-a-Terra-account-with-a-non-Google-email

**Key Point:** When creating your Google account during the setup process, select **"Use your existing email"** instead of creating a new Gmail address.

### Step 2: Log Into Terra and Link Your NIH Account
Once your account is created, follow these steps:

1. **Log into Terra:** 
   - Navigate to `https://anvil.terra.bio/`
   - Click the `Sign In` button
   - Select `Sign in with Google`
   - Log in using the account you created in Step 1

2. **Access your profile:**
   - Go to the main navigation menu by clicking the three horizontal lines at the top left of any Terra page
   - Click on your name to expand the menu, then select **Profile**

3. **Navigate to External Identities:**
   - Click on the **EXTERNAL IDENTITIES** tab

4. **Link your NIH account:**
   - Click the button to log into NIH under **External Identities**
   - You'll be redirected to an external authentication webpage
   - Follow the on-screen instructions to link your accounts

5. **Verify the connection:**
   - Once successfully linked, you'll see a link expiration deadline displayed

### Additional Resources
For detailed information about linking your NIH account in Terra, refer to:

https://support.terra.bio/hc/en-us/articles/19124069598235-Access-controlled-data-files-by-linking-your-NIH-account-in-Terra


### Step 3: Request a GCP Account Through CBIIT

- **Contact for setup:** Reach out to Wong, Shuk Wan Wendy or Seshadri, Krishnan for consultation and account setup assistance.

- **Account approval:** Once CBIIT approves your account, they will provide your GCP account information. For our lab, the details are:

```
Access your project at https://console.cloud.google.com/

Billing Account Name: NIH.NCI.xxx.xxx
Billing ID: xxx
Project ID: xxx

```

#### Important Verification Steps

:exclamation: **Step 1:** When logging into https://console.cloud.google.com/, first verify that your Google account has access to the billing account.

:exclamation: **Step 2:** Check whether the billing account has added Terra as a **Billing Account User**. If not, contact CBIIT to follow the steps outlined in this guide: [In Step 2. Link the Cloud Billing account to Terra](https://support.terra.bio/hc/en-us/articles/360026182251-How-to-set-up-billing-in-Terra-GCP)

#### Support and Troubleshooting

If you encounter any problems or need support (such as adding new members to the billing account), please submit a ticket here: [Google Cloud Service Request](https://service.cancer.gov/ncisp?id=nci_sc_cat_item&sys_id=1d7996f61b818910f360a681f54bcb31)



### Create a Terra Billing Project
Need this for Billing Project to create workspace to work on Terra.

1. Log into app.terra.bio, then click on the main navigation menu (three horizontal lines at the top left of any page). 

2. Click on your name and then go to your Billing page.

3. Click on the + Create button at the top left. 
Screenshot of Billing page with Create Terra billing project button at top highlighted

4. Select GCP Billing Project.

5. If prompted, sign in with your Google credentials.

6. Name your Billing project.

7. Select My Billing Account from the dropdown and you should see NIH.NCI.xxx.xxx in the select box and click the Create button.

:exclamation::exclamation::exclamation::exclamation: I can add people to the billing project I created so that they can also use. Instead of going through Goold billing account request.

*********


### Step 4: How to create or use public Terra workspaces


**Create your own with linked billing project**

1. Sometimes you need to create own workspace wtih linked billing project to access some database. To create one, first select `+` sign right next to top left `Workspces`.

2. Enter a unique workspace name, and optionally a description, Select a billing project we created in previous section `Create a Terra Billing Project`.
  
3. After selecting a billing project, a few more input fields will appear. Leave Bucket location set to its default value.

4. For Sharing, Addtitional Security Options, can leave it as default. and clikc `Create Workspace`

5. Now you have the workspace of your own!
   

**Finding public workspaces**

1. Once login, open main navigation menu by click 3 horizontal lines, then click `Workspaces`.

2. the section contains all kinds of feature workspaces such as GATK related pipeline, to search worksapces, click box on `search by name, project, or bucket`, then type key words.

3. if the workspce mathcs, it will showed as list below. For example when type `CCLE` in search bar, the result will pop-up showing the `CCLE-public` worksapce.


## Example of How to View IGV on Terra 

Terra has a built-in IGV (Integrative Genomics Viewer) for viewing alignments and variant calling data.

- We use the `CCLE-Public` dataset as an example. Once you access the workspace, click the three dots on the top right of screen, and clinkc `clone` to clone the workspace to our working space.

- you can change workspace name and description, but keep other options as defacult. 

- Once you have coloned the workspace, click `DATA` at the top near the `DASHBOARD`, in DATA section, enter the cell line of interest in the search box or simply click `model` to access the full table.

- In this table, there's an IGV icon at the top as shown in the image below. Select the row of the cell of interest, then click the IGV icon and select `Open with IGV`.

<img width="1322" height="403" alt="Screenshot 2025-09-17 at 10 33 32 AM" src="https://github.com/user-attachments/assets/862bec5b-fe3e-4028-8266-2a1a759aa282" />

- A pop-up table will appear showing which BAM files you want to view. Select the one of interest.

Sometimes a window will pop up asking you to select a workspace to bill to. When this appears, select the workspace we created earlier. (Since we cloned the workspcae, usually won't pop-up this selection.)

<img width="1148" height="579" alt="Screenshot 2025-09-16 at 10 16 17 AM" src="https://github.com/user-attachments/assets/32385d8b-d1ea-43cc-8e8c-ab15cf8ec194" />

Now the files can be loaded in IGV, and you can navigate the region just like the IGV desktop version.

<img width="1512" height="594" alt="Screenshot 2025-09-17 at 10 39 27 AM" src="https://github.com/user-attachments/assets/3ee04126-db2d-498c-9707-761e84303a72" />


## How to dowload stuff from Google bucket using command tools
## This needs to update!!




In this case, click top right **Select a project** and select billing account linked project. 

We use GTEx v10 GCP for example.

GTEx v10 has controlled access for their eQTL,vcf files etc in the Terra.bio workspace (https://www.gtexportal.org/home/protectedDataAccess), to dowload those file.
first loging your Terra with linked dbGAP account (In Step2). Once login, go to the workspacce page. (https://app.terra.bio/#workspaces/anvil-datastorage/AnVIL_GTEx_V10_hg38). In this Workspace, you can clikc **Open bucket in browser** in the right side of scrren and access their google bucket as shown below.


<img width="1575" height="830" alt="Screenshot 2025-11-10 at 1 37 40 PM" src="https://github.com/user-attachments/assets/2a299aef-7815-4963-937c-665d40d912b3" />


Now you can acees each folder and select which file you wnat to download, to enable download, we need to click **Select a biling project** to select our pay bucket, otherwise it will show you need **Bucket is a requester pays bucket but no user project provided.** error. 

Once click the Select a biling project section, it will show project id that we created in prevous step `Create a Terra Billing Project`. Select the project and 

![Screenshit_1.png](TEst)



Thew other way to download file is use gustil command in the Helix/CCAD2 system. 


```



```



