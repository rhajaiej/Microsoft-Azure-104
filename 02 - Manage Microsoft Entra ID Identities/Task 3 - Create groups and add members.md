# Task 3: Create Groups and Add Members

In this task, you create a group account. Group accounts can include user accounts or devices. There are two basic ways members are assigned to groups: Statically and Dynamically. Static groups require administrators to add and remove members manually. Dynamic groups update automatically based on the properties of a user account or device — for example, job title.

1. In the Azure portal, search for and select **Microsoft Entra ID**. In the Manage blade, select **Groups**.
2. Take a minute to familiarize yourself with the group settings in the left pane.
   - **Expiration** lets you configure a group lifetime in days. After that time the group must be renewed by the owner.
   - **Naming policy** lets you configure blocked words and add a prefix or suffix to group names.
3. In the **All groups** blade, select **+ New group** and create a new group.

| Setting | Value |
|---|---|
| Group type | Security |
| Group name | IT Lab Administrators |
| Group description | Administrators that manage the IT lab |
| Membership type | Assigned |

> **Note:** An Entra ID Premium P1 or P2 license is required for dynamic membership. If other membership types are available, the options will show up in the drop-down.

4. Select **No owners selected**.
5. In the Add owners page, search for and select yourself (shown in the top right corner) as the owner. Notice you can have more than one owner.
6. Select **No members selected**.
7. In the Add members pane, search for and select the **az104-user1** and the guest user you invited. Add both of the users to the group.
8. Select **Create** to deploy the group.
9. Refresh the page and ensure your group was created.
10. Select the new group and review the **Members** and **Owners** information.

> **Note:** You may be managing a large number of groups. Does your organization have a plan for creating groups and adding members?

## Extend your learning with Copilot

Copilot can assist you in learning how to use the Azure scripting tools. Copilot can also assist in areas not covered in the lab or where you need more information. Open an Edge browser and choose Copilot (top right) or navigate to copilot.microsoft.com. Take a few minutes to try these prompts:

- What are the Azure PowerShell and CLI commands to create a security group called IT Admins? Provide the official command reference page.
- Provide a step-by-step strategy for managing users and groups in Microsoft Entra ID.
- What are the steps in the Azure portal to bulk create users and groups?
- Provide a comparison table of internal and external Microsoft Entra ID user accounts.

## Learn more with self-paced training

- **Understand Microsoft Entra ID.** Compare Microsoft Entra ID to Active Directory DS, learn about Microsoft Entra ID P1 and P2, and explore Microsoft Entra Domain Services for managing domain-joined devices and apps in the cloud.
- **Create Azure users and groups in Microsoft Entra ID.** Create users in Microsoft Entra ID. Understand different types of groups. Create a group and add members. Manage business-to-business guest accounts.
- **Allow users to reset their password with Microsoft Entra self-service password reset.** Evaluate self-service password reset to allow users in your organization to reset their passwords or unlock their accounts. Set up, configure, and test self-service password reset.

## Key takeaways

Congratulations on completing the lab. Here are some main takeaways for this lab:

- A tenant represents your organization and helps you to manage a specific instance of Microsoft cloud services for your internal and external users.
- Microsoft Entra ID has user and guest accounts. Each account has a level of access specific to the scope of work expected to be done.
- Groups combine together related users or devices. There are two types of groups including Security and Microsoft 365.
- Group membership can be statically or dynamically assigned.

---
Source: [AZ-104 Microsoft Learning Labs — LAB_01: Manage Entra ID Identities](https://microsoftlearning.github.io/AZ-104-MicrosoftAzureAdministrator/Instructions/Labs/LAB_01-Manage_Entra_ID_Identities.html)
