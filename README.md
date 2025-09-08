# Goal: The place where store Terra Anvil platform related notes

*********

## Creating a Terra Account and Linking NIH Credentials

### Important Requirements
To create a Terra account that can be linked to NIH credentials, **you cannot use a Google email address** (e.g., `xxx@gmail.com`). Instead, you must set up your Terra account using a non-Google email address, such as your NIH email.

### Step 1: Create Your Terra Account
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

*********

# How to login lab GCP account
*********
# How to link to Terra platform

Ref, in Step2: https://support.terra.bio/hc/en-us/articles/360046295092-Claim-300-Google-credits-to-explore-Terra
*********
### Link GCP bucket to Terra

  Link GCP to your Terra account so that it can download or do analysis on platform.

1. When logged into Google Chrome with your Terra user ID, go to the [Google Cloud Console Billing page](https://console.cloud.google.com/billing).

2. Select the **checkbox beside the Google Cloud Billing account** you will use for Terra. For free trial credits, this will be **My Billing Account**.

3. On the right panel, below the billing account's name, select the **Add Principal** button.

4. Add `terra-billing@terra.bio` under **New Principal** in the form.

5. In the dropdown, select the Billing role **Billing Account User**.

6. Don't forget the **Save** button!

*********



### Create a Terra Billing Project
Need this for Billing Project to create workspace to work on Terra.

1. Log into app.terra.bio, then click on the main navigation menu (three horizontal lines at the top left of any page). 

2. Click on your name and then go to your Billing page.

3. Click on the + Create button at the top left. 
Screenshot of Billing page with Create Terra billing project button at top highlighted

4. Select GCP Billing Project.

5. If prompted, sign in with your Google credentials.

6. Name your Billing project.

7. Select My Billing Account from the dropdown ("My Billing Account" is the default name for your GCP free credits, and it should be the only option) and click the Create button.



*********


# How to use Terra platform
*********
# How to dowload stuff from Google bucket using command tools



