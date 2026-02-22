
# Payville Inc. Linux Infrastructure Setup

## Project Overview

This project demonstrates Linux system administration skills by creating users, groups, and secure company directories for Payville Inc. Proper role-based access control (RBAC) is implemented using Linux users, groups, and permissions following enterprise best practices.

---

## Company Staff and Roles

| Employee  | Role                   |
| --------- | ---------------------- |
| Andrew    | System Administrator   |
| Julius    | Legal                  |
| Chizi     | Human Resource Manager |
| Jeniffer  | Sales Manager          |
| Adeola    | Business Strategist    |
| Bach      | CEO                    |
| Gozie     | IT Intern              |
| Ogochukwu | Finance Manager        |

---

## Step 1: Create Groups

```bash
groupadd admin
groupadd legal
groupadd hr
groupadd sales
groupadd strategy
groupadd executive
groupadd it
groupadd finance
```

---

## Step 2: Create Users and Assign Groups

```bash
useradd -m -G admin andrew
useradd -m -G legal julius
useradd -m -G hr chizi
useradd -m -G sales jeniffer
useradd -m -G strategy adeola
useradd -m -G executive bach
useradd -m -G it gozie
useradd -m -G finance ogochukwu
```

Set passwords:

```bash
passwd andrew
passwd julius
passwd chizi
passwd jeniffer
passwd adeola
passwd bach
passwd gozie
passwd ogochukwu
```

---

## Step 3: Create Company Directories

```bash
mkdir -p /company/{finance_budgets,contract_documents,business_projections,business_models,employee_data,vision_mission,server_scripts}
```

---

## Step 4: Assign Group Ownership

```bash
chown :finance /company/finance_budgets
chown :legal /company/contract_documents
chown :strategy /company/business_projections
chown :strategy /company/business_models
chown :hr /company/employee_data
chown :executive /company/vision_mission
chown :admin /company/server_scripts
```

---

## Step 5: Set Permissions

```bash
chmod 770 /company/finance_budgets
chmod 770 /company/contract_documents
chmod 770 /company/business_projections
chmod 770 /company/business_models
chmod 770 /company/employee_data
chmod 750 /company/vision_mission
chmod 700 /company/server_scripts
```

---

## Step 6: Verification Commands

```bash
id andrew
getent group
ls -l /company
```

---

## Screenshots Included

* Created users and groups
* Company directory structure
* Directory permissions and ownership

---

## Tools Used

* Linux (Ubuntu)
* Bash Shell
* Git & GitHub

---

## Author

Eunice Abieyuwa Igbinedion
