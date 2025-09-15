# Task 2: Create a virtual network and subnets using a template

In this task, you create the **ManufacturingVnet** virtual network and associated subnets.  
The organization anticipates growth for the manufacturing offices, so the subnets are sized for the expected growth.  
For this task, you use a template to create the resources.

---

## Step 1: Locate the template file
- Find the **template.json** file exported in the previous task (should be in your *Downloads* folder).
- Edit the file using the editor of your choice.  
- Many editors have a **change all occurrences** feature.  
- If you are using Visual Studio Code, ensure you are working in a **trusted window** (not restricted mode).  
- Consult the architecture diagram to verify the details.

---

## Step 2: Make changes for the ManufacturingVnet virtual network
- Replace all occurrences of **CoreServicesVnet** with **ManufacturingVnet**.
  <img width="1441" height="855" alt="image" src="https://github.com/user-attachments/assets/3dd03331-6e48-4818-b8fc-8d6ee482e70d" />

- Replace all occurrences of **10.20.0.0** with **10.30.0.0**.
  <img width="1437" height="854" alt="image" src="https://github.com/user-attachments/assets/f6b86c47-9e7b-4b67-9eab-9eeb98e548bd" />


---

## Step 3: Make changes for the ManufacturingVnet subnets
- Change all occurrences of **SharedServicesSubnet** to **SensorSubnet1**.
  <img width="1478" height="909" alt="image" src="https://github.com/user-attachments/assets/a30d528e-5962-4cad-9977-349401828652" />

- Change all occurrences of **10.20.10.0/24** to **10.30.20.0/24**.
  <img width="1439" height="855" alt="image" src="https://github.com/user-attachments/assets/d94661fd-e965-493c-b8a2-804503cb2ed9" />

- Change all occurrences of **DatabaseSubnet** to **SensorSubnet2**.
  <img width="1440" height="851" alt="image" src="https://github.com/user-attachments/assets/db991cd6-d7e7-4a00-a495-40205f275e9c" />

- Change all occurrences of **10.20.20.0/24** to **10.30.21.0/24**.
  <img width="1441" height="855" alt="image" src="https://github.com/user-attachments/assets/e769f17c-89d8-4ec2-b7eb-c104b5a29b29" />


📌 Read back through the file and ensure everything looks correct.  
Use the architecture diagram for resource names and IP addresses.  
Be sure to **Save your changes**.  

> **Note:** There is a completed template file in the *lab files* directory.

---

## Step 4: Make changes to the parameters file
- Locate the **parameters.json** file exported in the previous task (should be in your *Downloads* folder).  
- Edit the file using the editor of your choice.  
- Replace the one occurrence of **CoreServicesVnet** with **ManufacturingVnet**.
  <img width="1443" height="855" alt="image" src="https://github.com/user-attachments/assets/8cca3e8a-5471-46be-848b-ba0b897e8a7a" />

- Save your changes.  

---

## Step 5: Deploy the custom template
1. In the portal, search for and select **Deploy a custom template**.
   <img width="1434" height="778" alt="image" src="https://github.com/user-attachments/assets/8b13540d-9793-476d-9fab-da67671b02bf" />

3. Select **Build your own template in the editor** and then **Load file**.  
4. Select the **template.json** file with your Manufacturing changes, then select **Save**.
   <img width="1435" height="779" alt="image" src="https://github.com/user-attachments/assets/1adfdcf0-dc02-4913-b76a-e1e927b03370" />

6. Select **Edit parameters**, and then **Load file**.  
7. Select the **parameters.json** file with your Manufacturing changes, then select **Save**.
   <img width="1437" height="778" alt="image" src="https://github.com/user-attachments/assets/7ee8beb6-2e78-4ae0-b69a-1e52242fc4be" />
   <img width="1439" height="778" alt="image" src="https://github.com/user-attachments/assets/8b67df89-fcab-406b-b5ba-5b966093f30e" />

9. Ensure your resource group, **az104-rg4**, is selected.  
10. Select **Review + create** and then **Create**.
    <img width="1438" height="779" alt="image" src="https://github.com/user-attachments/assets/2af37bb8-ae42-4e68-831b-9da2e892cebb" />

12. Wait for the template to deploy, then confirm (in the portal) that the **Manufacturing virtual network and subnets** were created.
    <img width="1439" height="784" alt="image" src="https://github.com/user-attachments/assets/419fd834-3894-4eef-b5e3-8f2ea7f95263" />

---
