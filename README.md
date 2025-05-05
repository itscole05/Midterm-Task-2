
#QUERY 1: INNER JOIN#
**Correct Query:**

```sql
SELECT E.FirstName, P.ProjectName  
FROM EmployeeDetail E  
INNER JOIN ProjectDetail P ON E.EmployeeID = P.EmployeeID  
ORDER BY E.FirstName;
```

**Output:**

```
FirstName   | ProjectName  
------------|------------------  
Ashish      | Task Track  
Ashish      | GRS  
Nikhil      | DDS  
Nikita      | HR Managment  
Nikita      | CLP  
Vikas       | Task Track  
```

---

**QUERY 2: LEFT JOIN**
**Correct Query:**

```sql
SELECT E.FirstName, P.ProjectName  
FROM EmployeeDetail E  
LEFT JOIN ProjectDetail P ON E.EmployeeID = P.EmployeeID  
ORDER BY E.FirstName;
```

**Output:**

```
FirstName   | ProjectName  
------------|------------------  
Ashish      | Task Track  
Ashish      | GRS  
Nikhil      | DDS  
Nikita      | HR Managment  
Nikita      | CLP  
Ramesh      | NULL  
Vikas       | Task Track  
```

---

**QUERY 3: RIGHT JOIN**
**Correct Query:**

```sql
SELECT E.FirstName, P.ProjectName  
FROM EmployeeDetail E  
RIGHT JOIN ProjectDetail P ON E.EmployeeID = P.EmployeeID  
ORDER BY E.FirstName;
```

**Output:**

```
FirstName   | ProjectName  
------------|------------------  
Ashish      | GRS  
Ashish      | Task Track  
Nikhil      | DDS  
Nikita      | CLP  
Nikita      | HR Managment  
NULL        | HR Managment  
NULL        | GL Managment  
Vikas       | Task Track  
```

---

**QUERY 4: CROSS JOIN**
**Correct Query:**

```sql
SELECT E.FirstName, P.ProjectName  
FROM EmployeeDetail E  
CROSS JOIN ProjectDetail P;
```

**Total Resultset: 54 rows**
(6 employees × 9 projects)

---

Would you like a photo of the handwritten answers as a reference?
