# Task 4: Configure public and private Azure DNS zones

In this task, you will create and configure public and private DNS zones.

---

## Configure a public DNS zone

You can configure **Azure DNS** to resolve host names in your public domain.  
For example, if you purchased the **contoso.xyz** domain name from a domain name registrar, you can configure Azure DNS to host the **contoso.com** domain and resolve `www.contoso.xyz` to the IP address of your web server or web app.

1. In the portal, search for and select **DNS zones**.
2. Select **+ Create**.
3. Configure the **Basics** tab:

   | Property       | Value                                          |
   |----------------|------------------------------------------------|
   | Subscription   | Select your subscription                       |
   | Resource group | az-104-rg4                                     |
   | Name           | contoso.com (if reserved adjust the name)      |
   | Region         | East US (review the informational icon)        |

4. Select **Review + create** and then **Create**.
5. Wait for the DNS zone to deploy and then select **Go to resource**.
6. On the **Overview** blade, notice the names of the four Azure DNS name servers assigned to the zone.  
   Copy one of the name server addresses (you will need it in a future step).
7. Expand the **DNS Management** blade and select **Recordsets**. Click **+ Add**:

   | Property   | Value     |
   |------------|-----------|
   | Name       | www       |
   | Type       | A         |
   | TTL        | 1         |
   | IP address | 10.1.1.4  |

   > 💡 In a real-world scenario, you’d enter the **public IP address** of your web server.

8. Select **Add** and verify your domain has an **A record set** named **www**.
9. Open a command prompt, and run the following command (adjust if you changed the domain name):

   ```shell
   nslookup www.contoso.com <name server name>

10. Verify the host name www.contoso.com
 resolves to the IP address you provided.
✅ This confirms name resolution is working correctly.
