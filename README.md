# 🌐 Cloud Governance Gone Rogue – Azure Policy Lab

## 📘 Course: CST8919 – DevOps Security and Compliance

## 🔍 Summary
This lab demonstrates how to enforce cloud governance in Azure using Azure Policy. As a new Cloud Security Engineer at MapleTech Solutions, your task is to create policies that restrict resource deployment to Canada Central, enforce mandatory tagging, and block public IP addresses.

---

## 📜 Custom Policies Created

### 1. **Only-CanadaCentral**
- **Type**: Custom Policy
- **Effect**: Deny
- **Description**: Denies deployment of any Azure resource outside the Canada Central region.
- **Rule**:
  - Uses `allowedLocations` parameter to allow only "canadacentral".

### 2. **Require-ProjectName-Tag**
- **Type**: Custom Policy
- **Effect**: Deny
- **Description**: Denies deployment of any resource that does not have the `ProjectName` tag.

### 3. **Deny-Public-IP**
- **Type**: Custom Policy
- **Effect**: Deny
- **Description**: Denies creation of any Public IP address.
- **Rule**:
  - Checks if the resource type is `Microsoft.Network/publicIPAddresses` and blocks it.

---

## 📦 Initiative: MapleTech Secure Foundation
All three policies were grouped under a single initiative to streamline enforcement. The initiative was assigned to a resource group with enforcement mode set to **Enabled**.

---

## 🧪 Test Cases & Results

| Action                                         | Expected Result |
|------------------------------------------------|------------------|
| Deploy VM in East US                          | ❌ Denied         |
| Deploy Storage Account without ProjectName tag| ❌ Denied         |
| Create a Public IP                            | ❌ Denied         |
| Deploy VM in Canada Central with tag          | ✅ Allowed        |

Screenshots of each case are saved in the `/screenshots` folder.

---

## 🎥 Video Demo
:  
[🔗 Video Link](https://your-video-link-here.com)

---

## 📁 Repository Structure

```
/policy-lab
│
├── screenshots/
│   ├── vm-eastus-denied.png
│   ├── storage-no-tag-denied.png
│   ├── public-ip-denied.png
│   └── vm-canadacentral-allowed.png
│
├── policy-definitions/
│   ├── only-canadacentral.json
│   ├── require-projectname-tag.json
│   └── deny-public-ip.json
│
├── README.md
```

---

## 💡 Lessons Learned
- Azure Policy is powerful for enforcing cloud governance at scale.
- Proper use of parameters allows for reusable and flexible policies.
- Testing policies immediately after assignment helps catch misconfigurations.

---
