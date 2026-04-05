Voici ton texte converti en **format Markdown propre pour GitHub** 👇
👉 Tu peux copier-coller directement dans un fichier `.md`

---

# 🧪 Lab 01 - Manage Microsoft Entra ID Identities

This is the first in a series of labs for Azure Administrators. In this lab, you learn about users and groups. Users and groups are the basic building blocks for an identity solution.

---

## 📘 Scenario

Your organization is building a new lab environment for pre-production testing of apps and services.

A few engineers are being hired to manage the lab environment, including virtual machines.

To allow authentication using Microsoft Entra ID, you must provision users and groups.

To minimize administrative overhead, group membership should be updated automatically based on job titles.

---

## 🎯 Job Skills

* Task 1: Create an Entra ID tenant
* Task 2: Create and configure user accounts
* Task 3: Create groups and add members

---

# 🧩 Task 1: Create an Entra ID Tenant

> ⚠️ **Important**
> This task is required for the rest of the lab.

### Steps

1. Log into the virtual machine:

   ```
   Username: Admin
   Password: Pa55w.rd
   ```

2. Open browser → go to:

   ```
   https://portal.azure.com
   ```

3. Sign in using provided credentials

4. Complete authentication (code verification)

5. In Azure portal:

   * Search → **Microsoft Entra ID**

6. Click:

   ```
   Manage tenants → + Create
   ```

---

### ⚙️ Configuration

| Setting     | Value              |
| ----------- | ------------------ |
| Tenant type | Microsoft Entra ID |

Click **Next: Configuration**

| Setting             | Value            |
| ------------------- | ---------------- |
| Organization name   | Contoso External |
| Initial domain name | Unique DNS name  |
| Country/Region      | United States    |

---

### 🚀 Deployment

* Click **Review + Create**
* Click **Create**

> ⚠️ If error: *Too many requests*

* Retry multiple times
* Check if tenant was created
* Use private browser window

---

### 🔐 Security Setup

* Configure **Microsoft Authenticator**
* Scan QR code
* Validate authentication

---

# 👤 Task 2: Create and Configure User Accounts

## ℹ️ About Tenants

A tenant is an instance of Microsoft Entra ID containing:

* Users
* Groups

---

## ➕ Create a New User

1. Go to:

   ```
   Microsoft Entra ID → Users → New user
   ```

2. Fill:

| Setting                | Value       |
| ---------------------- | ----------- |
| User principal name    | az104-user1 |
| Display name           | az104-user1 |
| Auto-generate password | ✅           |
| Account enabled        | ✅           |

### Properties

| Setting        | Value                |
| -------------- | -------------------- |
| Job title      | IT Lab Administrator |
| Department     | IT                   |
| Usage location | United States        |

👉 Click **Review + Create → Create**

---

## 🌍 Invite External User

1. Click:

   ```
   New user → Invite external user
   ```

2. Fill:

| Setting      | Value            |
| ------------ | ---------------- |
| Email        | Your email       |
| Display name | Your name        |
| Message      | Welcome to Azure |

### Properties

| Setting        | Value                |
| -------------- | -------------------- |
| Job title      | IT Lab Administrator |
| Department     | IT                   |
| Usage location | United States        |

👉 Click **Review + Invite**

---

# 👥 Task 3: Create Groups and Add Members

## 📘 Group Types

* **Static** → manual
* **Dynamic** → automatic (based on properties)

---

## ➕ Create Group

1. Go to:

   ```
   Azure portal → Groups → New group
   ```

2. Fill:

| Setting         | Value                                 |
| --------------- | ------------------------------------- |
| Group type      | Security                              |
| Group name      | IT Lab Administrators                 |
| Description     | Administrators that manage the IT lab |
| Membership type | Assigned                              |

---

## 👑 Add Owners

* Select yourself as owner

---

## 👨‍💻 Add Members

Add:

* `az104-user1`
* Invited guest user

👉 Click **Create**

---

## 🔍 Verify

* Check **Members**
* Check **Owners**

---

# 🤖 Extend Your Learning with Copilot

Try prompts like:

* Azure PowerShell commands to create a group
* Strategy for managing users and groups
* Bulk creation of users
* Internal vs external users comparison

---

# 📚 Learn More

* Microsoft Entra ID fundamentals
* Create users and groups
* Self-service password reset

---

# ✅ Key Takeaways

* A **tenant** represents your organization
* Microsoft Entra ID supports:

  * Internal users
  * Guest users
* **Groups**:

  * Security
  * Microsoft 365
* Membership:

  * Static
  * Dynamic

---

## 🎉 Conclusion

You have successfully completed this lab on Microsoft Entra ID identity management.

---

## 💡 Si tu veux aller plus loin

Je peux :

* ajouter des **captures d’écran propres**
* transformer ça en **portfolio GitHub pro**
* ou en **documentation style entreprise**

Dis-moi 👍
