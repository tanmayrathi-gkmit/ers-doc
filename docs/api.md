# **Employee Reimursement System - API Documentation**

### **Auth API**

| Method   | Endpoint                   | Purpose / Use                             |
| -------- | -------------------------- | ----------------------------------------- |
| **POST** | `/api/auth/login/`         | Login and get JWT access + refresh tokens |
| **POST** | `/api/auth/logout/`        | Logout by blacklisting refresh token      |
| **POST** | `/api/auth/token/refresh/` | Get new access token using refresh token  |

---

### **Users API**

| Method     | Endpoint                      | Purpose / Use                          |
| ---------- | ----------------------------- | -------------------------------------- |
| **GET**    | `/api/users/`                 | List all users                         |
| **POST**   | `/api/users/`                 | Create a new user                      |
| **GET**    | `/api/users/{id}/`            | Retrieve a user by ID                  |
| **PATCH**  | `/api/users/{id}/`            | Update user details                    |
| **DELETE** | `/api/users/{id}/`            | Delete a user                          |
| **POST**   | `/api/users/{id}/change-password/` | Change password of authenticated user  |
| **GET**    | `/api/users/{id}/profile/`              | Get current authenticated user profile |

---

### **Requests API**

| Method     | Endpoint              | Purpose / Use                                 |
| ---------- | --------------------- | --------------------------------------------- |
| **GET**    | `/api/requests/`      | List all requests (admin: all, employee: own) |
| **POST**   | `/api/requests/`      | Create a new reimbursement request            |
| **GET**    | `/api/requests/{id}/` | Retrieve a specific request                   |
| **PATCH**  | `/api/requests/{id}/` | Update an existing request                    |
| **DELETE** | `/api/requests/{id}/` | Delete a request                              |

---

### **Expenses API**

| Method     | Endpoint                                    | Purpose / Use                     |
| ---------- | ------------------------------------------- | --------------------------------- |
| **GET**    | `/api/requests/{request_pk}/expenses/`      | List all expenses under a request |
| **POST**   | `/api/requests/{request_pk}/expenses/`      | Create an expense under a request |
| **GET**    | `/api/requests/{request_pk}/expenses/{id}/` | Retrieve a specific expense       |
| **PATCH**  | `/api/requests/{request_pk}/expenses/{id}/` | Update an expense                 |
| **DELETE** | `/api/requests/{request_pk}/expenses/{id}/` | Delete an expense                 |

---

**Next:** [Sast & Dast Reports](sast.md)