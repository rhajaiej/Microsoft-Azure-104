# Task 4: Configure Public and Private Azure DNS Zones

In this task, you will **create and configure public and private DNS zones** in Azure.

---

## 1. Configure a Public DNS Zone

Azure DNS can resolve host names in your **public domain**.  
For example, if you purchased the `contoso.xyz` domain name from a registrar, you can configure Azure DNS to host `contoso.com` and resolve `www.contoso.xyz` to the IP address of your web server or app.

### Steps:
1. In the **Azure portal**, search for and select **DNS zones**.
2. Select **+ Create** and configure the Basics tab:

| Property       | Value                 |
|----------------|-----------------------|
| Subscription   | Select your subscription |
| Resource group | `az-104-rg4`          |
| Name           | `contoso.com` (adjust if reserved) |
| Region         | East US               |

3. Select **Review + create** → **Create**.  
4. After deployment, select **Go to resource**.  
   - On the **Overview** blade, note the **four Azure DNS name servers** assigned to the zone. Copy one of the name server addresses (needed later).
5. Expand the **DNS Management** blade → **Recordsets → + Add**. Configure:

| Property | Value      |
|----------|------------|
| Name     | `www`      |
| Type     | `A`        |
| TTL      | `1`        |
| IP address | `10.1.1.4` |

> **Note:** In production, use the **public IP address** of your web server.

6. Verify that the domain has an `A` record set named `www`.
7. Open a **command prompt** and test name resolution:

```shell
nslookup www.contoso.com <name server name>
✅ You should see www.contoso.com resolve to the IP address provided.

2. Configure a Private DNS Zone
A private DNS zone provides name resolution within virtual networks.
It is only accessible from linked virtual networks and not from the Internet.

Steps:
In the Azure portal, search for and select Private DNS zones.

Select + Create and configure the Basics tab:

Property	Value
Subscription	Select your subscription
Resource group	az-104-rg4
Name	private.contoso.com (adjust if renamed)
Region	East US

Select Review + create → Create.

After deployment, select Go to resource.

Notice the Overview blade shows no name server records.

Expand DNS Management → Virtual network links → + Add. Configure:

Property	Value
Link name	manufacturing-link
Virtual network	ManufacturingVnet

Select Create and wait for the link to finish.

From the DNS Management blade, select + Recordsets and add VM records. Example:

Property	Value
Name	sensorvm
Type	A
TTL	1
IP address	10.1.1.4

✅ You have now:

Configured a public DNS zone (contoso.com) with an A record (www).

Configured a private DNS zone (private.contoso.com), linked to a VNET, and added VM records.
