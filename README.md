
---

## ✅ Let’s Re-examine the **EmployeeDetail** table from the image:

| EmployeeID | FirstName | LastName | Salary     | JoiningDate | Department | Gender |
| ---------- | --------- | -------- | ---------- | ----------- | ---------- | ------ |
| 1          | Vikas     | Ahlawat  | 600000.00  | 2013-02-15  | IT         | Male   |
| 2          | Nikita    | Jain     | 530000.00  | 2014-01-27  | HR         | Female |
| 3          | Ashish    | Kumar    | 1000000.00 | 2014-01-09  | IT         | Male   |
| 4          | Nikhil    | Sharma   | 480000.00  | 2014-01-09  | HR         | Male   |
| 5          | Anisha    | Kadan    | 500000.00  | 2014-01-09  | Payroll    | Female |
| 6          | Anish     | --       | ----       | ----        | ----       | ----   |

⚠️ **There is no Ramesh**. That was a misreading — it's **Anisha**, not Ramesh.

Thanks for your patience. Let's now rewrite **everything correctly** from scratch.

---

## ✅ FINAL, FULLY CORRECT ANSWERS:

---

### **QUERY 1**:

> Get employee name, project name (only for those who have assigned projects), ordered by first name.

```sql
SELECT E.FirstName, P.ProjectName
FROM EmployeeDetail E
INNER JOIN ProjectDetail P ON E.EmployeeID = P.EmployeeID
ORDER BY E.FirstName;
```

### ✅ Output:

```
FirstName | ProjectName
----------|----------------------
Anish     | GL Managment
Ashish    | Survey Managment
Ashish    | Task Track
Ashish    | GRS
Nikhil    | DDS
Nikita    | CLP
Nikita    | HR Managment
Vikas     | Task Track
```

---

### **QUERY 2**:

> Get employee name, project name (for all employees, even those without a project), ordered by first name.

```sql
SELECT E.FirstName, P.ProjectName
FROM EmployeeDetail E
LEFT JOIN ProjectDetail P ON E.EmployeeID = P.EmployeeID
ORDER BY E.FirstName;
```

### ✅ Output:

```
FirstName | ProjectName
----------|----------------------
Anish     | GL Managment
Anisha    | NULL
Ashish    | Survey Managment
Ashish    | Task Track
Ashish    | GRS
Nikhil    | DDS
Nikita    | CLP
Nikita    | HR Managment
Vikas     | Task Track
```

✅ **Anisha** appears with `NULL` (no project).
✅ **Anish** appears because he’s assigned to "GL Managment".

---

### **QUERY 3**:

> Get all projects, even those not assigned to any employee, ordered by employee first name (if matched).

```sql
SELECT E.FirstName, P.ProjectName
FROM ProjectDetail P
LEFT JOIN EmployeeDetail E ON P.EmployeeID = E.EmployeeID
ORDER BY E.FirstName;
```

### ✅ Output:

```
FirstName | ProjectName
----------|----------------------
Anish     | GL Managment
Ashish    | Survey Managment
Ashish    | Task Track
Ashish    | GRS
Nikhil    | DDS
Nikita    | CLP
Nikita    | HR Managment
Vikas     | Task Track
NULL      | HR Managment
```

✅ **1 unassigned project** (ProjectID 8: "HR Managment" with `NULL` EmployeeID).

---

### **QUERY 4**:

> Perform a CROSS JOIN on both tables. What is the total result set?

```sql
SELECT E.FirstName, P.ProjectName
FROM EmployeeDetail E
CROSS JOIN ProjectDetail P;
```

### ✅ Total Rows:

* 6 employees × 9 projects = **54 rows**

---

