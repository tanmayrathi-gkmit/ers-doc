# **Employee Reimursement System – Use Case Documentation**

### **Purpose**
This document describes the key **use cases** for the **Employee Reimursement System**.  
The goal is to simplify and digitize the organization’s reimbursement process by replacing manual Google Forms and emails with a transparent, efficient, and centralized digital system.

### **Business Overview**
Currently, employees submit travel or work-related reimbursement claims manually using forms or spreadsheets.  
This process is slow, error-prone, and lacks visibility for both employees and administrators.

#### The **Employee Reimursement System** aims to:
- Reduce manual effort and increase operational efficiency.  
- Provide better transparency and accountability.  
- Maintain accurate financial records for audit and reporting.  
- Create a clear approval workflow between employees and admins.  

### **Use Case 1: Employee – Submit Reimbursement**

#### **Actors**
- **Employee** – Staff member submitting a reimbursement request.  
- **System** – The Employee Reimursement System that manages reimbursement request and expenses.  
- **Admin** – Reviewer who validates and approves or rejects the reimbursement request.

#### **Goal**
To allow employees to easily create, manage, and submit reimbursement requests for business-related trips or expenses.

#### **Scenario**
1. The employee logs into the system.  
2. Creates a new **reimbursement request** record.  
3. Adds one or more **expenses** under the trip (e.g., travel, accommodation, meals).   
4. Can **edit or delete** expenses anytime before submission.  
5. Once finalized, the employee **submits** the reimbursement request for admin approval.  
6. The system stores the request, updates its status to **Submitted**, and notifies the admin.  

#### **Preconditions**
- The employee must be logged into the system.  
- The reimbursement request must contain at least one expense.  
- Reimbursement policies must be defined by the organization.  

#### **Postconditions**
- The reimbursement request is stored in the database.  
- The reimbursement request status changes to **Submitted**.  
- The request becomes visible to the admin for review.  

### **Use Case 2: Admin – Approve or Reject Reimbursement Request**

#### **Actors**
- **Admin / Finance Department** – Authorized user who reviews and validates claims.  
- **Employee** – Claim submitter who receives feedback. 
- **System** – Handles record updates, notifications, and data logging.

#### **Goal**
To ensure that all submitted reimbursement requests are reviewed and processed efficiently while maintaining compliance with company reimbursement policies.

#### **Scenario**
1. The admin logs into the system.  
2. Views the list of **submitted reimbursement requests**.  
3. Selects a trip to review its details, expenses, and uploaded receipts.  
4. Verifies the validity and compliance of expenses.  
5. Approves or rejects the reimbursement request.  
6. The system updates the status to **Approved** or **Rejected** and notifies the employee.  
7. Approved claims are recorded for payment processing.  

#### **Preconditions**
- The admin must be logged into the system.  
- At least one reimbursement request must exist for review.  
- Expense approval policies must be pre-configured in the system.  

#### **Postconditions**
- The reimbursement request status is updated to **Approved** or **Rejected**.  
- All actions are recorded in the database for audit purposes.  

### **Overall Outcome**
The **Employee Reimursement System** makes the reimbursement process faster, easier, and more transparent for everyone in the organization.  
Instead of using Google Forms or emails, all tasks, from expense submission to final approval, happen in one system.

#### **With this system:**
- Employees can easily add, track, and manage their reimbursement requests.  
- Admins can review and approve requests efficiently from one dashboard.  
- It saves time, reduces human error, and keeps all data organized.  
- The workflow becomes smoother, fair, and paperless.  
---

**Next:** [Technical Documentation](technical.md)