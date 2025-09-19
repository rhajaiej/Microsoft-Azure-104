# Task 3: Create and Configure Communication between an Application Security Group (ASG) and a Network Security Group (NSG)

In this task, we create an **Application Security Group (ASG)** and a **Network Security Group (NSG)**.  
The NSG will have:
- An **inbound security rule** that allows traffic from the ASG.
- An **outbound security rule** that denies access to the Internet.

---

## 1. Create the Application Security Group (ASG)

1. In the **Azure portal**, search for and select **Application security groups**.
2. Click **Create** and provide the following information:

| Setting        | Value         |
|----------------|---------------|
| Subscription   | your subscription |
| Resource group | `az104-rg4`   |
| Name           | `asg-web`     |
| Region         | East US       |

3. Click **Review + create** and then **Create** after validation.

> **Note:** At this point, you would associate the ASG with virtual machine(s).  
> These machines will be affected by the inbound NSG rule created later.

---

## 2. Create the Network Security Group (NSG) and Associate it with `CoreServicesVnet`

1. In the **Azure portal**, search for and select **Network security groups**.  
   *(Alternatively: Azure portal menu → Create a resource → Networking → Network security group)*

2. Click **+ Create** and fill in the Basics tab:

| Setting        | Value         |
|----------------|---------------|
| Subscription   | your subscription |
| Resource group | `az104-rg4`   |
| Name           | `myNSGSecure` |
| Region         | East US       |

3. Click **Review + create** → **Create**.  
4. After deployment, click **Go to resource**.  
5. Under **Settings**, click **Subnets → Associate** and provide:

| Setting           | Value                       |
|-------------------|-----------------------------|
| Virtual network   | `CoreServicesVnet (az104-rg4)` |
| Subnet            | `SharedServicesSubnet`      |

6. Click **OK** to save the association.

---

## 3. Configure an Inbound Security Rule to Allow ASG Traffic

1. In your NSG resource, go to **Settings → Inbound security rules**.
2. Review the default inbound rules (only VNETs and load balancers are allowed).
3. Click **+ Add** and configure:

| Setting                         | Value      |
|---------------------------------|------------|
| Source                          | Application security group |
| Source application security groups | `asg-web` |
| Source port ranges              | `*`        |
| Destination                     | Any        |
| Service                         | Custom     |
| Destination port ranges         | `80,443`   |
| Protocol                        | TCP        |
| Action                          | Allow      |
| Priority                        | 100        |
| Name                            | `AllowASG` |

4. Click **Add** to save the inbound rule.

---

## 4. Configure an Outbound NSG Rule that Denies Internet Access

1. In the NSG resource, go to **Outbound security rules**.
2. Notice the default rule: `AllowInternetOutboundRule` (priority `65001`), which **cannot be deleted**.
3. Click **+ Add** and configure:

| Setting              | Value         |
|----------------------|---------------|
| Source               | Any           |
| Source port ranges   | `*`           |
| Destination          | Service tag   |
| Destination service tag | Internet   |
| Service              | Custom        |
| Destination port ranges | `*`        |
| Protocol             | Any           |
| Action               | Deny          |
| Priority             | 4096          |
| Name                 | `DenyInternetOutbound` |

4. Click **Add** to save the outbound rule.

---
