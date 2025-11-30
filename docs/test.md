# **Employee Reimursement System - Test Planning**

## **Backend Unit Test Cases**


### **1. Admin can login**

**Purpose:** Verify successful authentication for admin user.
**Precondition:** Admin user exists.

**Steps:**
Send POST `/api/auth/login/` with admin credentials.

**Expected Result:**

* Status `200`
* Contains `access` and `refresh` tokens



### **2. Employee can login**

**Purpose:** Verify employee login.
**Precondition:** Employee exists.

**Steps:**
POST credentials to `/api/auth/login/`.

**Expected Result:**

* Status `200`
* Contains `access` token


### **3. Admin can create user**

**Purpose:** Only admin should be able to create users.
**Precondition:** Admin authenticated.

**Steps:**
POST `/api/users/` with valid payload.

**Expected Result:**
`201` and user created.



### **4. Employee cannot create user**

**Purpose:** Verify access control.

**Steps:**

1. Login as employee.
2. POST `/api/users/`.

**Expected Result:**
`403`, user not created.
### **5. Admin can list users**

**Purpose:** Admin should be able to see all users.

**Steps:**
GET `/api/users/` as admin.

**Expected Result:**
`200` with list of users.



### **6. Employee cannot list users**

**Steps:**
GET `/api/users/` as employee.

**Expected Result:**
`403`



### **7. User can change password**

**Purpose:** Validate password update behavior.

**Steps:**

1. POST `/api/users/{id}/change-password/` with old + new passwords.
2. Attempt login with new password.

**Expected Result:**

* Status `200`
* Login works with new password



### **8. Soft delete user**

**Purpose:** Validate soft delete logic.

**Steps:**

1. DELETE `/api/users/<id>/` as admin.
2. GET list.
3. Attempt login.

**Expected Result:**

* `deleted_at` set and `is_active=False`
* User not visible in list
* Login fails




### **9. Employee creates request**

**Purpose:** Verify request creation.

**Steps:**
POST `/api/requests/` with valid data.

**Expected Result:**
`201`, request saved.



### **10. Start date must be before end date**

**Purpose:** Validate date logic.

**Steps:**
POST body with `end_date < start_date`.

**Expected Result:**
`400` with validation error on `end_date`.



### **11. Cannot submit without expenses**

**Purpose:** Submitted requests must contain at least one expense.

**Steps:**

1. Create draft request.
2. PATCH status → `submitted`.

**Expected Result:**
`400` with appropriate error.



### **12. Admin cannot see draft requests**

**Purpose:** Drafts should be visible only to the creator.

**Steps:**

1. Create draft for employee.
2. GET `/api/requests/` as admin.

**Expected Result:**
Draft not included in results.


### **13. Expense date must be within request range**

**Purpose:** Validate date constraints.

**Steps:**

1. Create request.
2. POST expense with out-of-range date.

**Expected Result:**
`400` with validation error.



### **14. Amount must be positive**

**Purpose:** Prevent invalid amounts.

**Steps:**
POST expense with negative amount.

**Expected Result:**
`400` error.



### **15. Employee cannot modify expense after submit**

**Purpose:** Lock expenses after submission.

**Steps:**

1. Create request + expense.
2. Submit request.
3. Attempt to PATCH expense.

**Expected Result:**
`403`

## **Frontend Unit Test Cases**

### **1. `apiRequest` adds Authorization header when `auth=true`**

**Purpose:** Ensure authenticated API requests automatically append the Bearer token.
**Preconditions:**

* `access` token exists in `localStorage`
* `api.js` is loaded in the DOM environment

**Steps:**

1. Load `api.js` into test scope.
2. Mock `fetch()` to return a successful JSON response.
3. Set `localStorage.access = 'tok-123'`.
4. Call `apiRequest('/test/endpoint', 'GET', null, true)`.

**Expected Result:**

* `fetch` is called with the correct URL.
* Header contains `Authorization: Bearer tok-123`.
* Response returned: `{ success: true }`.



### **2. `apiRequest` refreshes token on 401 and retries request**

**Purpose:** Verify the silent token refresh flow.
**Preconditions:**

* `access = oldtoken`
* `refresh = refresh-token`
* `fetch()` mock sequence:

  * First call → `401`
  * Refresh endpoint → `200`
  * Retry call → `200`

**Steps:**

1. Call `apiRequest('/protected', 'GET', null, true)`.
2. First call receives `401`.
3. `refreshToken()` is executed.
4. New token saved.
5. Original request retried.

**Expected Result:**

* Final response `{ ok: true }`.
* `localStorage.access === 'newtoken'`.
* `fetch` called at least 3 times.



### **3. `refreshToken` throws error when refresh token missing**

**Purpose:** Ensure error handling when refresh token does not exist.
**Preconditions:** `localStorage.refresh` is removed.

**Steps:**
Call `window.api.refreshToken()`.

**Expected Result:**

* Throws error: `Missing refresh token`.
* No API calls executed.
