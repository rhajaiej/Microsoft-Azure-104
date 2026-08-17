# Task 2: Create and Configure User Accounts

In this task, you will create and configure user accounts. User accounts will store user data such as name, department, location, and contact information.

1. Sign in to the Azure portal - https://portal.azure.com.
2. To proceed to the portal, select **Cancel** on the Welcome to Azure splash screen.

> **Note:** The Azure portal is used in all the labs. If you are new to Azure, search for and select **Quickstart Center**. Take a few minutes to watch the *Getting started in the Azure portal* video. Even if you have used the portal before, you will find a few tips and tricks on navigating and customizing the interface.

3. Search for and select **Microsoft Entra ID**. Microsoft Entra ID is Azure's cloud-based identity and access management solution. Take a few minutes to familiarize yourself with some of the features listed in the left pane.
4. Select the **Overview** blade and then the **Manage tenants** tab.

> **Did you know?** A tenant is a specific instance of Microsoft Entra ID containing accounts and groups. Depending on your situation, you can create more tenants and switch between them.

5. Return to the Entra ID page by pressing back in the browser or selecting the option in the breadcrumb menu.
6. As you have time, explore other options such as **Licenses** and **Password reset**.

## Create a new user

1. In the **Manage** blade, select **Users**; then in the **New user** drop-down select **Create new user**.
2. Create a new user with the following settings (leave others with their defaults). On the Properties tab notice all the different types of information that can be included in the user account.

| Setting | Value |
|---|---|
| User principal name | az104-user1 |
| Display name | az104-user1 |
| Auto-generate password | checked |
| Account enabled | checked |
| Job title (Properties tab) | IT Lab Administrator |
| Department (Properties tab) | IT |
| Usage location (Properties tab) | United States |

3. Once you have finished reviewing, select **Review + create** and then **Create**.
4. Refresh the page and confirm your new user was created.

## Invite an external user

1. In the **New user** drop-down select **Invite an external user**.

| Setting | Value |
|---|---|
| Email | your email address |
| Display name | your name |
| Send invite message | check the box |
| Message | Welcome to Azure and our group project |

2. Move to the **Properties** tab. Complete the basic information, including these fields.

| Setting | Value |
|---|---|
| Job title | IT Lab Administrator |
| Department | IT |
| Usage location (Properties tab) | United States |

3. Select **Review + invite**, and then **Invite**.
4. Refresh the page and confirm the invited user was created. You should receive the invitation email shortly.

> **Note:** It is unlikely you will be creating user accounts individually. Do you know how your organization plans to create and manage user accounts?

---
Source: [AZ-104 Microsoft Learning Labs](https://microsoftlearning.github.io/AZ-104-MicrosoftAzureAdministrator/)
