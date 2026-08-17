# Task 1: Create a Virtual Network with Subnets Using the Portal

The organization plans a large amount of growth for core services. In this task, you create the virtual network and the associated subnets to accommodate the existing resources and planned growth.

You will use the Azure portal for this task.

## Step 1: Sign in to Azure Portal
Sign in at https://portal.azure.com.

## Step 2: Navigate to Virtual Networks
Search for and select **Virtual Networks**.

Click **Create** on the Virtual Networks page.

## Step 3: Configure the Basics tab for CoreServicesVnet

| Option | Value |
|---|---|
| Resource Group | az104-rg4 (create new if necessary) |
| Name | CoreServicesVnet |
| Region | (US) East US |

## Step 4: Configure IP Addresses

Move to the **IP Addresses** tab.

Replace the prepopulated IPv4 address space with: `10.20.0.0/16`

Select **+ Add a subnet**. Complete the name and address information for each subnet. Be sure to select **Add** for each new subnet.

Delete the default subnet either before or after creating the other subnets.

| Subnet | Option | Value |
|---|---|---|
| SharedServicesSubnet | Subnet name | SharedServicesSubnet |
| | Starting address | 10.20.10.0 |
| | Size | /24 |
| DatabaseSubnet | Subnet name | DatabaseSubnet |
| | Starting address | 10.20.20.0 |
| | Size | /24 |

> **Note:** Every virtual network must have at least one subnet. Five IP addresses are always reserved, so consider that in your planning.

## Step 5: Create the Virtual Network
Select **Review + create** to finish creating the CoreServicesVnet and its associated subnets.

Verify your configuration passed validation, then select **Create**.

Wait for the virtual network to deploy and then select **Go to resource**.

Take a minute to verify the Address space and the Subnets. Review other settings in the Settings blade.

## Step 6: Export the Template
In the **Automation** section, select **Export template**.

Wait for the template to be generated.

Download the template.

Navigate on your local machine to the Downloads folder and extract all files from the downloaded zip file.

---
Source: [AZ-104 Microsoft Learning Labs](https://microsoftlearning.github.io/AZ-104-MicrosoftAzureAdministrator/)
