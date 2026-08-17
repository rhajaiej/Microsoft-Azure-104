# Lab 02 — Configure Azure Virtual Networking, Security, and DNS

> [!NOTE]
> The organization plans significant growth across its core services and manufacturing offices. In this lab, you build out the virtual networking foundation for that growth: a virtual network with subnets (created two ways — through the portal and through an ARM template), network-level security with an Application Security Group and Network Security Group, and public/private DNS resolution.

**Product(s)**: Azure Virtual Network, Azure Resource Manager templates, Network Security Groups, Application Security Groups, Azure DNS
**Estimated duration**: 90 minutes
**Level**: Intermediate

## Objectives

By the end of this lab, you will be able to:

- Create a virtual network with a custom IPv4 address space and multiple subnets, using the Azure portal
- Export a virtual network as an ARM template and redeploy it with modified names and address ranges
- Create an Application Security Group (ASG) and a Network Security Group (NSG), and configure inbound/outbound rules between them
- Create and configure a public Azure DNS zone and a private Azure DNS zone

## Prerequisites

- An active Azure subscription
- Permissions to create resources (Contributor role or higher) on the target subscription
- Access to the Azure portal
- A code editor (e.g., Visual Studio Code) for editing JSON template files
- Access to a command prompt for running `nslookup`
- The lab's network architecture diagram, for reference when renaming resources

## Task 1: Create a virtual network with subnets using the portal

You will use the Azure portal for this task.

### Step 1: Sign in to the Azure portal

1. Go to [https://portal.azure.com](https://portal.azure.com) and sign in with your Azure account credentials.

### Step 2: Navigate to Virtual Networks

1. In the Azure portal search bar, search for and select **Virtual Networks**.

   ![Virtual Networks search results in the Azure portal](images/01-virtual-networks-search.png)

2. On the **Virtual Networks** page, select **Create**.

### Step 3: Configure the Basics tab for CoreServicesVnet

1. On the **Basics** tab, set the following options:

   | Setting | Value |
   |---|---|
   | Resource Group | `az104-rg4` (create new if it doesn't exist) |
   | Name | `CoreServicesVnet` |
   | Region | (US) East US |

   ![Basics tab configured with CoreServicesVnet settings](images/02-basics-tab.png)

### Step 4: Configure IP addresses

1. Move to the **IP Addresses** tab.
2. Replace the pre-populated IPv4 address space with `10.20.0.0/16`.

   ![IPv4 address space set to 10.20.0.0/16](images/03-ipv4-address-space.png)

3. Select **+ Add a subnet**. Complete the name and address information for each subnet below, selecting **Add** after each one.

   | Subnet | Setting | Value |
   |---|---|---|
   | SharedServicesSubnet | Subnet name | `SharedServicesSubnet` |
   | | Starting address | `10.20.10.0` |
   | | Size | `/24` |
   | DatabaseSubnet | Subnet name | `DatabaseSubnet` |
   | | Starting address | `10.20.20.0` |
   | | Size | `/24` |

4. Delete the default subnet, either before or after creating the two subnets above.

   > [!NOTE]
   > Every virtual network must have at least one subnet. Azure always reserves five IP addresses per subnet — factor that into your address planning.

   ![Add subnet panel for SharedServicesSubnet](images/04-add-subnet-shared-services.png)
   ![Add subnet panel for DatabaseSubnet](images/05-add-subnet-database.png)
   ![Final subnet list showing both subnets](images/06-subnet-list.png)

### Step 5: Create the virtual network

1. Select **Review + create**.
2. Verify your configuration passed validation, then select **Create**.

   ![Review and create validation passed](images/07-review-create-validation.png)

3. Wait for the deployment to finish, then select **Go to resource**.
4. Take a minute to verify the **Address space** and **Subnets**, and review the other settings in the **Settings** blade.

   ![Virtual network overview showing address space and subnets](images/08-vnet-overview.png)
   ![Virtual network Settings blade](images/09-vnet-settings.png)

### Step 6: Export the template

1. In the **Automation** section, select **Export template**.

   ![Export template option in the Automation section](images/10-export-template.png)

2. Wait for the template to be generated, then select **Download**.
3. On your local machine, navigate to the **Downloads** folder and extract all files from the downloaded `.zip` file.

## Task 2: Create a virtual network and subnets using a template

In this task, you create the **ManufacturingVnet** virtual network and its associated subnets. The organization anticipates growth for the manufacturing offices, so the subnets are sized accordingly. You use an ARM template to create these resources.

### Step 1: Locate the template file

1. Find the `template.json` file exported in Task 1 (should be in your **Downloads** folder).
2. Open the file in the editor of your choice.

   > [!TIP]
   > Many editors support a "replace all occurrences" feature — it will speed up the edits below. If you're using Visual Studio Code, make sure you're working in a trusted window (not Restricted Mode).

3. Consult the architecture diagram to verify resource names and IP ranges before making changes.

### Step 2: Update the virtual network definition

1. Replace all occurrences of `CoreServicesVnet` with `ManufacturingVnet`.
2. Replace all occurrences of `10.20.0.0` with `10.30.0.0`.

### Step 3: Update the subnet definitions

1. Replace all occurrences of `SharedServicesSubnet` with `SensorSubnet1`.
2. Replace all occurrences of `10.20.10.0/24` with `10.30.20.0/24`.
3. Replace all occurrences of `DatabaseSubnet` with `SensorSubnet2`.
4. Replace all occurrences of `10.20.20.0/24` with `10.30.21.0/24`.

> [!IMPORTANT]
> Read back through the file and confirm every name and IP address matches the architecture diagram, then save your changes.

> [!NOTE]
> A completed reference template is available in the lab files directory if you want to compare your edits.

### Step 4: Update the parameters file

1. Locate the `parameters.json` file exported in Task 1 (also in your **Downloads** folder).
2. Open it in your editor.
3. Replace the single occurrence of `CoreServicesVnet` with `ManufacturingVnet`.
4. Save your changes.

### Step 5: Deploy the custom template

1. In the Azure portal, search for and select **Deploy a custom template**.
2. Select **Build your own template in the editor**, then **Load file**.
3. Select your edited `template.json` file, then select **Save**.
4. Select **Edit parameters**, then **Load file**.
5. Select your edited `parameters.json` file, then select **Save**.
6. Confirm the **Resource group** is set to `az104-rg4`.
7. Select **Review + create**, then **Create**.
8. Wait for the deployment to finish, then confirm in the portal that the **ManufacturingVnet** virtual network and its subnets were created.

## Task 3: Create and configure communication between an ASG and an NSG

In this task, you create an Application Security Group (ASG) and a Network Security Group (NSG). The NSG includes an inbound rule that allows traffic from the ASG, and an outbound rule that denies internet access.

### Step 1: Create the Application Security Group (ASG)

1. In the Azure portal, search for and select **Application security groups**.
2. Select **Create** and provide the following information:

   | Setting | Value |
   |---|---|
   | Subscription | Your subscription |
   | Resource group | `az104-rg4` |
   | Name | `asg-web` |
   | Region | East US |

3. Select **Review + create**, then **Create** once validation passes.

   > [!NOTE]
   > At this point, you would normally associate the ASG with one or more virtual machines. Those machines are what the inbound NSG rule created below will affect.

### Step 2: Create the Network Security Group (NSG) and associate it with CoreServicesVnet

1. In the Azure portal, search for and select **Network security groups** (alternatively: **Create a resource** → **Networking** → **Network security group**).
2. Select **+ Create** and fill in the **Basics** tab:

   | Setting | Value |
   |---|---|
   | Subscription | Your subscription |
   | Resource group | `az104-rg4` |
   | Name | `myNSGSecure` |
   | Region | East US |

3. Select **Review + create**, then **Create**.
4. After deployment, select **Go to resource**.
5. Under **Settings**, select **Subnets** → **Associate**, and provide:

   | Setting | Value |
   |---|---|
   | Virtual network | `CoreServicesVnet` (`az104-rg4`) |
   | Subnet | `SharedServicesSubnet` |

6. Select **OK** to save the association.

### Step 3: Configure an inbound security rule to allow ASG traffic

1. In your NSG resource, go to **Settings** → **Inbound security rules**.
2. Review the default inbound rules — only VNet and load balancer traffic is allowed by default.
3. Select **+ Add** and configure:

   | Setting | Value |
   |---|---|
   | Source | Application security group |
   | Source application security groups | `asg-web` |
   | Source port ranges | `*` |
   | Destination | Any |
   | Service | Custom |
   | Destination port ranges | `80,443` |
   | Protocol | TCP |
   | Action | Allow |
   | Priority | `100` |
   | Name | `AllowASG` |

4. Select **Add** to save the rule.

### Step 4: Configure an outbound rule that denies internet access

1. In the NSG resource, go to **Outbound security rules**.
2. Note the default rule, `AllowInternetOutboundRule` (priority `65001`) — it can't be deleted.
3. Select **+ Add** and configure:

   | Setting | Value |
   |---|---|
   | Source | Any |
   | Source port ranges | `*` |
   | Destination | Service tag |
   | Destination service tag | Internet |
   | Service | Custom |
   | Destination port ranges | `*` |
   | Protocol | Any |
   | Action | Deny |
   | Priority | `4096` |
   | Name | `DenyInternetOutbound` |

4. Select **Add** to save the rule.

## Task 4: Configure public and private Azure DNS zones

In this task, you create and configure a public and a private Azure DNS zone.

### Part A — Configure a public DNS zone

Azure DNS can resolve host names in a public domain you own. For example, if you purchased `contoso.com` from a domain registrar, you can configure Azure DNS to host the domain and resolve `www.contoso.com` to the IP address of your web server or web app.

1. In the Azure portal, search for and select **DNS zones**.
2. Select **+ Create**.
3. Configure the **Basics** tab:

   | Setting | Value |
   |---|---|
   | Subscription | Your subscription |
   | Resource group | `az104-rg4` |
   | Name | `contoso.com` (adjust if this name is already reserved) |
   | Region | East US |

   > [!TIP]
   > Review the informational icon next to **Region** for details on how it's used.

4. Select **Review + create**, then **Create**.
5. Wait for the DNS zone to deploy, then select **Go to resource**.
6. On the **Overview** blade, note the four Azure DNS name server addresses assigned to the zone. Copy one of them — you'll need it in a later step.
7. Expand **DNS Management**, select **Recordsets**, then select **+ Add**:

   | Setting | Value |
   |---|---|
   | Name | `www` |
   | Type | A |
   | TTL | `1` |
   | IP address | `10.1.1.4` |

   > [!NOTE]
   > In a real-world scenario, you'd enter the public IP address of your actual web server here.

8. Select **Add**, and confirm your domain now has an A record named `www`.
9. Open a command prompt and run the following, adjusting the domain name if needed:

   ```
   nslookup www.contoso.com <name server address>
   ```

10. Confirm that `www.contoso.com` resolves to the IP address you provided — this confirms name resolution is working correctly.

### Part B — Configure a private DNS zone

A private DNS zone provides name resolution within the virtual networks it's linked to. It's only accessible from those virtual networks — not from the internet.

1. In the Azure portal, search for and select **Private DNS zones**.
2. Select **+ Create**.
3. On the **Basics** tab, enter:

   | Setting | Value |
   |---|---|
   | Subscription | Your subscription |
   | Resource group | `az104-rg4` |
   | Name | `private.contoso.com` (adjust if renamed) |
   | Region | East US |

4. Select **Review + create**, then **Create**.
5. Wait for the zone to deploy, then select **Go to resource**.
6. Note that the **Overview** blade shows no name server records — this is expected for a private zone.
7. Expand **DNS Management**, select **Virtual network links**, and configure the link:

   | Setting | Value |
   |---|---|
   | Link name | `manufacturing-link` |
   | Virtual network | `ManufacturingVnet` |

8. Select **Create** and wait for the link to be created.
9. From **DNS Management**, select **+ Recordsets**, and add a record for each virtual machine that needs private name resolution:

   | Setting | Value |
   |---|---|
   | Name | `sensorvm` |
   | Type | A |
   | TTL | `1` |
   | IP address | `10.1.1.4` |

## Validation

You have successfully completed this lab when:

- The **CoreServicesVnet** virtual network exists in **az104-rg4** with address space `10.20.0.0/16`, containing **SharedServicesSubnet** (`10.20.10.0/24`) and **DatabaseSubnet** (`10.20.20.0/24`), with the default subnet removed.
- The **ManufacturingVnet** virtual network exists with address space `10.30.0.0/16`, containing **SensorSubnet1** (`10.30.20.0/24`) and **SensorSubnet2** (`10.30.21.0/24`).
- The **asg-web** Application Security Group and **myNSGSecure** Network Security Group exist, the NSG is associated with **SharedServicesSubnet**, and it has an `AllowASG` inbound rule and a `DenyInternetOutbound` outbound rule.
- The **contoso.com** public DNS zone resolves `www.contoso.com` to `10.1.1.4` via `nslookup`.
- The **private.contoso.com** private DNS zone is linked to **ManufacturingVnet** and contains an A record for `sensorvm`.

## Cleanup

If this lab is part of a larger AZ-104 series, keep the **az104-rg4** resource group and its resources — they're likely reused in later labs. Otherwise, delete the resource group to remove the virtual networks, NSG, ASG, and DNS zones together and avoid ongoing costs.
