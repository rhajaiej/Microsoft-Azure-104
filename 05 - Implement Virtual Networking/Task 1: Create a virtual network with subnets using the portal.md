# Task 1: Create a virtual network with subnets using the portal

The organization plans a large amount of growth for core services..
In this task, you create the virtual network and the associated subnets to accommodate the existing resources and planned growth.  
You will use the **Azure portal** for this task.

---

## Step 1: Sign in to Azure Portal

Sign in at [https://portal.azure.com](https://portal.azure.com).

---

## Step 2: Navigate to Virtual Networks

1. Search for and select **Virtual Networks**.
<img width="1443" height="784" alt="image" src="https://github.com/user-attachments/assets/5fefe617-cfe4-481f-bf6c-c49d83463242" />





 
3. Click **Create** on the Virtual Networks page.

---

## Step 3: Configure the Basics tab for CoreServicesVnet

| Option          | Value                       |
|-----------------|-----------------------------|
| Resource Group  | az104-rg4 (create new if necessary) |
| Name            | CoreServicesVnet            |
| Region          | (US) East US                |

<img width="1435" height="781" alt="image" src="https://github.com/user-attachments/assets/baf21e3b-7f62-4607-9602-6d956ceaeb4c" />


---

## Step 4: Configure IP Addresses

1. Move to the **IP Addresses** tab.  
2. Replace the prepopulated IPv4 address space with:  10.20.0.0/16

<img width="1435" height="779" alt="image" src="https://github.com/user-attachments/assets/27aced9c-08c2-4e5e-88c3-35c707b47680" />




4. Select **+ Add a subnet**. Complete the name and address information for each subnet. Be sure to select **Add** for each new subnet.  
5. Delete the default subnet either before or after creating the other subnets.

| Subnet              | Option         | Value           |
|--------------------|----------------|----------------|
| SharedServicesSubnet | Subnet name   | SharedServicesSubnet |
|                     | Starting address | 10.20.10.0    |
|                     | Size           | /24             |
| DatabaseSubnet      | Subnet name    | DatabaseSubnet |
|                     | Starting address | 10.20.20.0    |
|                     | Size           | /24             |

> **Note:** Every virtual network must have at least one subnet. Five IP addresses are always reserved, so consider that in your planning.

<img width="1438" height="782" alt="image" src="https://github.com/user-attachments/assets/bfeaab95-fae2-49cf-b451-c12d59825f29" />
<img width="1440" height="779" alt="image" src="https://github.com/user-attachments/assets/df299413-53d7-401b-8b9e-8061132abb1f" />
<img width="1438" height="737" alt="image" src="https://github.com/user-attachments/assets/72cefcf4-24d3-42c8-9f49-a1005542cc5a" />


---

## Step 5: Create the Virtual Network

1. Select **Review + create** to finish creating the **CoreServicesVnet** and its associated subnets.  
2. Verify your configuration passed validation, then select **Create**.
<img width="1439" height="780" alt="image" src="https://github.com/user-attachments/assets/d4445f0a-3df5-43ef-847e-09caf6e7737a" />

  
4. Wait for the virtual network to deploy and then select **Go to resource**.  
5. Take a minute to verify the **Address space** and the **Subnets**. Review other settings in the **Settings** blade.
<img width="1438" height="781" alt="image" src="https://github.com/user-attachments/assets/7407b22b-b974-4e45-ac4f-b281fc33d6ad" />
<img width="1440" height="782" alt="image" src="https://github.com/user-attachments/assets/9a0ecd68-d255-48c9-a65f-bcf59b1285d8" />



---

## Step 6: Export the Template

1. In the **Automation** section, select **Export template**.
<img width="1438" height="780" alt="image" src="https://github.com/user-attachments/assets/fd701c92-b297-40e6-bc9d-db7744795b68" />


3. Wait for the template to be generated.  
4. Download the template.  
5. Navigate on your local machine to the **Downloads** folder and **Extract all** files from the downloaded zip file.


