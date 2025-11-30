# **Employee Reimursement System – Functional Documentation**

This section explains how the system works from the point of view of both Employee and Admin users.

## **Employee**

#### Login / Register
- User logs in using username and password.
- After login, they see their dashboard (list of reimbursement requests).
- JWT token is used to authenticate API calls.

#### Create reimbursement request
- Click "Add Reimbursement Request".
- Enter reimbursement request's details: title, description, start date, end date.
- Reimbursement request is saved with status = Draft.
- Reimbursement request can be edited or deleted before submission.

#### Add Expenses
- Each reimbursement request can have multiple expenses.
- Each expense includes:
    - Title  
    - Date & Time  
    - Category (Food, Transport, Lodging, Other)  
    - Amount  
    - Description (optional)
- User can edit or delete expenses while reimbursement request is still Draft.

#### Submit reimbursement request
- When all expenses are added, user clicks Submit.
- Reimbursement request status becomes Submitted.
- Editing is locked after submission.
- Admin sees in dashboard.
- Admin updates reimbursement request status


### **Employee Flow Overview**

![Employee Reimbursement Flowchart](assets/images/emp-flow.svg){ width="50%" style="display:block; margin-left:auto; margin-right:auto;" }

---

## **Admin User**

#### Login
- Admin logs in to view dashboard.

#### View Submitted reimbursement requests
- All employee reimbursement requests appear with status (Draft, Submitted, Approved, Rejected).
- Admin can open each reimbursement request to view its details and expenses.

#### Approve / Reject
- Admin can click Approve or Reject.
- On approval, reimbursement request status changes to Approved.
- On rejection, status changes to Rejected.


### **Admin Flow Overview**

![Admin Reimbursement Flowchart](assets/images/admin-flow.svg){ width="60%" style="display:block; margin-left:auto; margin-right:auto;"}

---

**Next:** [Use Cases](bus-sys-use.md)
