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
<img width="1443" height="784" alt="image" src="https://github.com/user-attachments/assets/0b191bb8-7d2d-40e6-aa5c-290cda1c2276" />

 
3. Click **Create** on the Virtual Networks page.

---

## Step 3: Configure the Basics tab for CoreServicesVnet

| Option          | Value                       |
|-----------------|-----------------------------|
| Resource Group  | az104-rg4 (create new if necessary) |
| Name            | CoreServicesVnet            |
| Region          | (US) East US                |

<img width="1435" height="781" alt="image" src="https://github.com/user-attachments/assets/b7d09228-de0d-45da-9a03-bd7ad9c76fc5" />



---

## Step 4: Configure IP Addresses

1. Move to the **IP Addresses** tab.  
2. Replace the prepopulated IPv4 address space with:  10.20.0.0/16
<img width="1435" height="779" alt="image" src="https://github.com/user-attachments/assets/796c6b2d-dbfb-4fe7-8580-4e3808462a39" />



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
<img width="1438" height="782" alt="image" src="https://github.com/user-attachments/assets/c6f04077-aeae-4d5e-a890-09dddb6dfaff" />
<img width="1440" height="779" alt="image" src="https://github.com/user-attachments/assets/c5c38af6-fc67-4591-a965-83cf229d4b74" />
<img width="1438" height="737" alt="image" src="https://github.com/user-attachments/assets/308a636a-b333-4431-8d8b-2edf1a1def72" />

---

## Step 5: Create the Virtual Network

1. Select **Review + create** to finish creating the **CoreServicesVnet** and its associated subnets.  
2. Verify your configuration passed validation, then select **Create**.
<img width="1439" height="780" alt="image" src="https://github.com/user-attachments/assets/aff63e09-e861-4f61-9d27-139bc4b16886" />
  
4. Wait for the virtual network to deploy and then select **Go to resource**.  
5. Take a minute to verify the **Address space** and the **Subnets**. Review other settings in the **Settings** blade.
<img width="1438" height="781" alt="image" src="https://github.com/user-attachments/assets/9409c98e-8489-4540-a039-d52a6ab47399" />
<img width="1440" height="782" alt="image" src="https://github.com/user-attachments/assets/4387628f-a89a-4eb4-bf44-892b8366260b" />


---

## Step 6: Export the Template

1. In the **Automation** section, select **Export template**.
<img width="1438" height="780" alt="image" src="https://github.com/user-attachments/assets/06affa68-739d-4352-a7b3-218a48ffc2b0" />

3. Wait for the template to be generated.  
4. Download the template.  
5. Navigate on your local machine to the **Downloads** folder and **Extract all** files from the downloaded zip file.


