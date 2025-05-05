
---

## 🔹 **Database Summary**

### **EmployeeDetail Table**

| EmployeeID | FirstName | LastName | Salary     | JoiningDate         | Department | Gender |
| ---------- | --------- | -------- | ---------- | ------------------- | ---------- | ------ |
| 1          | Vikas     | Ahlawat  | 600000.00  | 2013-02-15 11:16:28 | IT         | Male   |
| 2          | Nikita    | Jain     | 530000.00  | 2014-01-27 19:31:07 | HR         | Female |
| 3          | Ashish    | Kumar    | 1000000.00 | 2014-01-09 10:56:07 | IT         | Male   |
| 4          | Nikhil    | Sharma   | 480000.00  | 2014-01-09 10:56:07 | HR         | Male   |
| 5          | Ramesh    | Kadan    | 500000.00  | 2014-01-09 09:31:07 | Payroll    | Male   |

### **ProjectDetail Table**

| ProjectID | EmployeeID | ProjectName      |
| --------- | ---------- | ---------------- |
| 1         | 1          | Task Track       |
| 2         | 2          | CLP              |
| 3         | 3          | Survey Managment |
| 4         | 2          | HR Managment     |
| 5         | 3          | Task Track       |
| 6         | 3          | GRS              |
| 7         | 4          | DDS              |
| 8         | NULL       | HR Managment     |
| 9         | NULL       | GL Managment     |

---

## ✅ **QUERY 1**

**Task**: Use `INNER JOIN` to get employee **first name** and **project name** (only for assigned projects), ordered by **first name**.

### ✅ Correct Query:

```sql
SELECT E.FirstName, P.ProjectName
FROM EmployeeDetail E
INNER JOIN ProjectDetail P ON E.EmployeeID = P.EmployeeID
ORDER BY E.FirstName;
```

### ✅ Output:

```
FirstName | ProjectName
----------|-------------------
Ashish    | Survey Managment
Ashish    | Task Track
Ashish    | GRS
Nikhil    | DDS
Nikita    | CLP
Nikita    | HR Managment
Vikas     | Task Track
```

---

## ✅ **QUERY 2**

**Task**: Get employee first name and project name (even if the employee has no project), ordered by **first name**.

### ✅ Correct Query:

```sql
SELECT E.FirstName, P.ProjectName
FROM EmployeeDetail E
LEFT JOIN ProjectDetail P ON E.EmployeeID = P.EmployeeID
ORDER BY E.FirstName;
```

### ✅ Output:

```
FirstName | ProjectName
----------|-------------------
Ashish    | Survey Managment
Ashish    | Task Track
Ashish    | GRS
Nikhil    | DDS
Nikita    | CLP
Nikita    | HR Managment
Ramesh    | NULL
Vikas     | Task Track
```

---

## ✅ **QUERY 3**

**Task**: Get all **project names**, even if they aren't assigned to any employee. Show employee first name (if any), ordered by **first name**.

### ✅ Correct Query:

```sql
SELECT E.FirstName, P.ProjectName
FROM ProjectDetail P
LEFT JOIN EmployeeDetail E ON P.EmployeeID = E.EmployeeID
ORDER BY E.FirstName;
```

### ✅ Output:

```
FirstName | ProjectName
----------|-------------------
Ashish    | Survey Managment
Ashish    | Task Track
Ashish    | GRS
Nikhil    | DDS
Nikita    | CLP
Nikita    | HR Managment
NULL      | HR Managment
NULL      | GL Managment
Vikas     | Task Track
```

---

## ✅ **QUERY 4**

**Task**: Perform a `CROSS JOIN` on both tables. Show total result set and the query.

### ✅ Correct Query:

```sql
SELECT E.FirstName, P.ProjectName
FROM EmployeeDetail E
CROSS JOIN ProjectDetail P;
```

### ✅ Total Result Set:

* `5 employees × 9 projects = 45 rows`

---

Would you like this formatted into a printable document or handwritten-style layout for submission?
