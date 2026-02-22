
---

# 💻 Payville Inc. Linux Infrastructure Setup – Detailed Walkthrough


## 1️⃣ **Project Overview**

This project demonstrates Linux administration skills by:

* Creating users and assigning them to appropriate groups
* Setting up company directories for each department
* Assigning the correct permissions for role-based access control (RBAC)
* Documenting the infrastructure for submission to GitHub

**Goal:** Simulate a real-world enterprise setup for a small company.

---

## 2️⃣ **Employees and Roles**

| Employee  | Role                   |
| --------- | ---------------------- |
| Andrew    | System Administrator   |
| Julius    | Legal                  |
| Chizi     | Human Resource Manager |
| Jeniffer  | Sales Manager          |
| Adeola    | Business Strategist    |
| Bach      | CEO                    |
| Gozie     | IT intern              |
| Ogochukwu | Finance Manager        |

---

## 3️⃣ **Groups to Create**

| Group      | Purpose                              |
| ---------- | ------------------------------------ |
| sysadmin   | System Administrators (full control) |
| legal      | Legal Department                     |
| hr         | Human Resources                      |
| sales      | Sales Department                     |
| strategy   | Business Strategy                    |
| management | CEO & Executives                     |
| it         | IT Intern                            |
| finance    | Finance Department                   |

---

## 4️⃣ **Step 1 – Create Groups**

```bash
sudo groupadd sysadmin
sudo groupadd legal
sudo groupadd hr
sudo groupadd sales
sudo groupadd strategy
sudo groupadd management
sudo groupadd it
sudo groupadd finance
```

✅ **Verification:**

```bash
getent group | egrep "sysadmin|legal|hr|sales|strategy|management|it|finance"
```

📸 **Screenshot:** `screenshots/groups.png`

---

## 5️⃣ **Step 2 – Create Users and Assign Groups**

```bash
sudo useradd -m -G sysadmin Andrew
sudo useradd -m -G legal Julius
sudo useradd -m -G hr Chizi
sudo useradd -m -G sales Jeniffer
sudo useradd -m -G strategy Adeola
sudo useradd -m -G management Bach
sudo useradd -m -G it Gozie
sudo useradd -m -G finance Ogochukwu
```

Set passwords for each:

```bash
sudo passwd Andrew
sudo passwd Julius
sudo passwd Chizi
sudo passwd Jeniffer
sudo passwd Adeola
sudo passwd Bach
sudo passwd Gozie
sudo passwd Ogochukwu
```

✅ **Verification:**

```bash
id Andrew Julius Chizi Jeniffer Adeola Bach Gozie Ogochukwu
```

📸 **Screenshot:** `screenshots/users.png`

---

## 6️⃣ **Step 3 – Create Company Directories**

Create the main `payville` workspace:

```bash
mkdir -p ~/assignment1/payville/{Finance\ Budgets,Contract\ Documents,Business\ Projections,Business\ Models,Employee\ Data,Company\ Vision\ and\ Mission\ Statement,Server\ Configuration\ Script}
```

---

## 7️⃣ **Step 4 – Assign Ownership (chown)**

```bash
sudo chown :finance ~/assignment1/payville/Finance\ Budgets
sudo chown :legal ~/assignment1/payville/Contract\ Documents
sudo chown :strategy ~/assignment1/payville/Business\ Projections
sudo chown :strategy ~/assignment1/payville/Business\ Models
sudo chown :hr ~/assignment1/payville/Employee\ Data
sudo chown :management ~/assignment1/payville/Company\ Vision\ and\ Mission\ Statement
sudo chown :sysadmin ~/assignment1/payville/Server\ Configuration\ Script
```

---

## 8️⃣ **Step 5 – Set Permissions (chmod)**

```bash
chmod 770 ~/assignment1/payville/Finance\ Budgets
chmod 770 ~/assignment1/payville/Contract\ Documents
chmod 770 ~/assignment1/payville/Business\ Projections
chmod 770 ~/assignment1/payville/Business\ Models
chmod 770 ~/assignment1/payville/Employee\ Data
chmod 750 ~/assignment1/payville/Company\ Vision\ and\ Mission\ Statement
chmod 700 ~/assignment1/payville/Server\ Configuration\ Script
```

✅ **Why these permissions?**

* **770** → owner + group have full access; others none (department-specific directories)
* **750** → owner + group can access; others cannot (CEO vision file)
* **700** → only owner (sysadmin) can access (server scripts)

---

## 9️⃣ **Step 6 – Verify Ownership & Permissions**

```bash
ls -ld ~/assignment1/payville/*
```

📸 **Screenshot:** `screenshots/permissions.png`

Optional numeric verification:

```bash
stat -c "%n %a %U %G" ~/assignment1/payville/*
```

---

## 10️⃣ **Step 7 – Optional: Tree View for Hierarchy**

```bash
tree ~/assignment1/payville
```

📸 **Screenshot:** `screenshots/tree.png`

---

## 11️⃣ **Step 8 – GitHub Submission**

### 11.1 Initialize Git

```bash
cd ~/assignment1
git init
```

### 11.2 Add README & Screenshots

```bash
git add README.md screenshots/
git commit -m "Add Payville Inc Linux infrastructure setup"
```

### 11.3 Connect to Remote Repo

```bash
git branch -M main
git remote add origin https://github.com/Eunnylans/Linux-user-group-access-control.git
```

### 11.4 Push

```bash
git push -u origin main
```

---

## 12️⃣ **README.md Structure**

Include:

1. **Project overview**
2. **Employee list + groups**
3. **Commands used for users, groups, directories**
4. **Ownership & permissions verification**
5. **Screenshots embedded**
6. **Optional notes on permissions and RBAC**

**Example screenshot embedding in README:**

```md
![Users](screenshots/users.png)
![Groups](screenshots/groups.png)
![Permissions](screenshots/permissions.png)
![Directory Tree](screenshots/tree.png)
```

---

## ✅ 13️⃣ **Checklist for Submission**

* [X] Users created ✅
* [X] Groups created ✅
* [X] Directories created ✅
* [X] Ownership assigned ✅
* [X] Permissions set correctly ✅
* [X] Screenshots captured ✅
* [X] README.md documented ✅
* [X] GitHub repository pushed ✅

---
