### Automation Workflows Documentation for n8n

This documentation outlines the setup and configuration of automation workflows for the `n8n-workflow` repository. The workflows are designed to handle event registration and communication for "Build with AI Jakarta 2025".

***

### ⚙️ Preparation

To get started, you'll need to set up a **Zeabur** account and an **n8n** project.

1.  **Create a Zeabur Account and Project**: Sign up for an account on Zeabur and subscribe to the **Developer** billing plan, which costs USD$5 to begin.
2.  **Initialize n8n**: Create a new project on Zeabur and choose the **n8n** template from the "Templates" tab.
3.  **Configure Custom Domain**: Go to the "Networking" tab and configure your custom domain, such as `n8n.gdgjakarta.com`. It is important not to delete the existing domain provided by Zeabur.

***

### 🔑 n8n Credentials

You'll need to set up credentials for various Google services and Bevy to ensure the workflows function correctly.

#### **Google Credentials**

The n8n workflows require access to Google services like Google Sheets, Gmail, and Google Drive. To set this up:

1.  **Register an Account**: First, register and log in to an n8n account.
2.  **Add Credentials**: From the n8n interface, you'll need to add credentials for `Google Sheets Trigger account`, `Gmail account`, `Google Sheets account`, and `Google Drive account`. 
3.  **Google Cloud Platform Setup**: Access the Google Cloud Platform API Credentials. The domains `https://n8n.gdgjakarta.com/rest/oauth2-credential/callback` and `https://gdgjakarta.zeabur.app/rest/oauth2-credential/callback` need to be added as **Authorized redirect URIs**.
4.  **Connect GCP to n8n**: Copy the **Client ID** and **Client Secret** from Google Cloud Platform and paste them into the corresponding fields in n8n. 
5.  **Sign In and Authorize**: Save the configuration and click **Sign In with Google** to complete the authorization process. Repeat these steps for all necessary Google credentials.

#### **Bevy API Credentials**

The workflow for registering attendees to Bevy requires specific headers to bypass authentication.

* **Required Headers**: The following headers are required to access the Bevy API:
    * `Content-Type: application/json`
    * `Cookie: sessionid={your_bevy_session_id}; csrftoken={your_bevy_csrftoken}`
    * `Referer: https://gdg.community.dev/dashboard/gdg-jakarta/events/88619/registrations`
    * `X-Csrftoken: {your_bevy_X-Csrftoken}`

* **Finding the Tokens**: You can find your `sessionid` and `csrftoken` by accessing the Bevy dashboard, opening your browser's **Developer Tools**, navigating to the **Network** tab, and expanding the **Request Headers**. The `X-Csrftoken` value can be found in the same location.
* **Important Note**: These tokens will reset whenever you log out of your Bevy account, so they must be updated again after logging back in.

***
