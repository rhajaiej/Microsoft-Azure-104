# Lab 01 — Create a Microsoft Entra ID Tenant

> [!NOTE]
> This lab walks you through creating a new Microsoft Entra ID (Azure AD) tenant from the Azure portal. It's the foundation for a larger lab — the tenant you create here is used in every subsequent task.

**Product(s)**: Microsoft Entra ID, Azure Portal
**Estimated duration**: 15 minutes
**Level**: Beginner

## Objectives

By the end of this task, you will be able to:

- Sign in to the Azure portal using MFA
- Create a new Microsoft Entra ID tenant from the **Manage tenants** blade
- Switch to the newly created tenant and complete the initial account security setup (Microsoft Authenticator)

## Prerequisites

- A virtual machine named **LON-CL1** with a web browser
- "go deploy" Azure Cloud Share credentials (username `studentFCG26@t008.gdazcs.com`, provided by the lab environment)
- A mobile device with the Microsoft Authenticator app installed

> [!IMPORTANT]
> This task is required for the rest of the lab to function correctly.
> "go deploy" provides Azure Cloud Share credentials to make tenant creation easier. You are **not required** to use the "go deploy" Azure tenant (`go deploy Ltd (t008.gdazcs.com)`) beyond the tenant-creation steps below — once your new tenant exists, you'll carry out the rest of the lab in it.

## Task 1: Sign in to the Azure portal

1. If necessary, send the **Ctrl+Alt+Del** command and sign in to the **LON-CL1** virtual machine with username `Admin` and password `Pa55w.rd`.
2. Open a web browser and go to the Azure portal: [https://portal.azure.com](https://portal.azure.com).
3. On the **Sign in** dialog, enter the username `studentFCG26@t008.gdazcs.com`, then select **Next**.
4. On the **Enter password** dialog, enter the password `YJUf3zlqYKnDQj8K`, then select **Sign in**.

   You'll be prompted for an authentication token.

5. Select **Generate Authentication Code**.

   > [!TIP]
   > You have 60 seconds to sign in with this code before it expires and you need to generate a new one.

6. On the **Code** dialog, enter the authentication code, then select **Verify**.
7. On the **Welcome to Microsoft Azure** dialog, select **Maybe Later**. If an Azure recommendations dialog appears, close it (**X**).
8. In the Azure portal search bar, search for and select **Microsoft Entra ID**.

   Microsoft Entra ID is Azure's cloud-based identity and access management solution. Take a few minutes to explore the features listed in the left-hand navigation pane.

## Task 2: Create the new tenant

1. In Microsoft Entra ID, select **Manage tenants**.
2. On the **Manage tenants** blade, select **+ Create**.
3. On the **Create a tenant** blade, set the following option, then select **Next: Configuration**:

   | Setting | Value |
   |---|---|
   | Tenant type | Microsoft Entra ID |

4. On the **Configuration** tab, enter the following values, then select **Review + Create**:

   | Setting | Value |
   |---|---|
   | Organization name | Contoso External |
   | Initial domain name | Any valid, unique DNS name using lowercase letters and digits, starting with a letter |
   | Country/Region | United States |

   > [!NOTE]
   > The initial domain name must not match a real organization. A green check mark next to the field confirms the name is valid and available.

5. Review your selections, then select **Create**.

   > [!TIP]
   > **Known issue**: you may see the error *"Creation failed. Too many requests, please try later"* due to a Captcha verification issue in the lab environment. If this happens:
   > - Retry the creation a few times.
   > - Check the **Manage tenants** section to confirm the tenant wasn't actually created in the background.
   > - Open a new InPrivate window, sign in to the Azure portal, and retry from there.
   > - Alternatively, complete the sign-in and tenant-creation steps above on your local machine instead of the lab VM.

6. On the confirmation blade for the new tenant, select **Click here to navigate to your new tenant: Contoso Lab**.

   A new browser tab opens showing your newly created tenant.

   > [!IMPORTANT]
   > If you don't switch to the new tenant, the remaining tasks in this lab will not work.

## Task 3: Complete the account security setup

1. On the **Let's keep your account secure** dialog, select **Next**.
2. On the **Install Microsoft Authenticator** dialog, select **Next**.
3. On the **Set up your account** page, select **Next**.
4. Using the Microsoft Authenticator app on your mobile device, scan the QR code, then select **Next**.
5. On the **Let's try it out** dialog, note the code shown and enter it in the Authenticator app.
6. On the **Authenticator Added** dialog, select **Done**.

## Validation

You have successfully completed this task when:

- You're signed in to the new **Contoso External** tenant (visible in the top-right account/tenant switcher in the Azure portal).
- Microsoft Authenticator is registered as an authentication method for your account.

## Cleanup

No cleanup is required for this task — the tenant you created here is used by the rest of the lab.
