# 💻 Laptop Request Catalog Item (ServiceNow)

## 📌 Project Overview

The **Laptop Request Catalog Item** project streamlines how employees request laptops through a dynamic and user-friendly ServiceNow interface. It replaces manual, error-prone processes with an automated, efficient solution using the Service Catalog module.

---

## 🚀 Problem Statement

The organization needed a faster, more accurate system for laptop requests. The old manual method lacked:

- Dynamic form behavior
- Validation controls
- UI reset options
- Trackable deployment process

---

## 🎯 Objectives

- Build a Service Catalog item with dynamic fields
- Add form reset functionality via UI Actions
- Implement conditional logic using Catalog UI Policies
- Export and retrieve the solution using Update Sets
- Enable full deployment and testing in different instances

---

## 🔧 Implementation Steps

### 🧱 1. Create a Local Update Set
- Navigate to `All > Update Sets > Local Update Sets`
- Create a new update set: `Laptop Request`
- Click **Submit** and **Make Current**

### 📦 2. Create Service Catalog Item
- Navigate to `All > Service Catalog > Maintain Items`
- Add a new item:  
  - **Name**: Laptop Request  
  - **Catalog**: Service Catalog  
  - **Category**: Hardware  
  - **Short Description**: Use this item to request a new laptop

### 📝 3. Add Variables
| Variable Name           | Type            | Order |
|-------------------------|------------------|--------|
| Laptop Model            | Single Line Text | 100    |
| Justification           | Multi Line Text  | 200    |
| Additional Accessories  | Checkbox         | 300    |
| Accessories Details     | Multi Line Text  | 400    |

---

## 🔀 4. Create Catalog UI Policy

- **Name**: Show Accessories Details
- **Condition**: `additional_accessories == true`
- **Action**:  
  - Variable: `accessories_details`  
  - Mandatory: ✅  
  - Visible: ✅  

---

## 🔁 5. Create UI Action (Reset Form)

- Table: `sc_cart` (Shopping Cart)
- Action Name: `Reset Form`
- Client: ✅

**Script:**
```javascript
function resetForm() {
    g_form.clearForm();
    alert("The form has been reset.");
}
📥7. Import to Target Instance
Login to another ServiceNow instance
Go to Update Sets > Retrieved Update Sets
Click Import Update Set from XML
Upload the XML file
Preview & Commit
🧪 8. Test Catalog Item
Go to Service Catalog > Hardware
Search and open Laptop Request item
Test dynamic behavior (e.g., accessory details field shows up only when checkbox is checked)
✅ Conclusion
This project enhances employee satisfaction and service delivery by:

Making the request process intuitive
Reducing delays and errors
Ensuring consistency across deployments
Leveraging powerful ServiceNow tools like UI Policies, Actions, and Update Sets
🛠️ Built With
🔧 ServiceNow
🧩 Update Sets
🖼️ Catalog UI Policies
⚙️ UI Actions
📎 Demo video File: https://drive.google.com/file/d/15D9VX7YcYNp63K3_colQAtFQeVuWwo_U/view?usp=drivesdk
