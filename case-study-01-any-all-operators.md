# 🧠 Case Study 01 — Understanding ANY & ALL Operators in Subqueries

### 🎯 Topic Focus
ANY / ALL operators, comparison logic in subqueries, and how Oracle evaluates result sets.

---

## 🔍 Problem Scenario

We want to compare an employee’s salary against the salaries of employees in another department.

Business Question:

> “Find employees whose salary is higher than **ANY** salary in Department X  
> and employees whose salary is higher than **ALL** salaries in Department X.”

This exercise helps understand:

- how ANY works
- how ALL works
- why logic differs from MAX/MIN usage
- how Oracle evaluates comparison subqueries

---

## 🧩 Step 1 — Understanding The Goal (Before Writing SQL)

We do **not** write SQL immediately.

First we reason:

✔ What is the dataset?  
✔ What are we comparing?  
✔ Is comparison made to one value or multiple values?  
✔ Do we want:  
→ higher than at least one value (ANY)  
→ higher than all values (ALL)?

---

## 🧮 Logical Breakdown

### `> ANY`
Means:
```
Greater than at least one value in the subquery result
```

Equivalent to:
```
> MIN(value)
```

---

### `> ALL`
Means:
```
Greater than every value in the subquery result
```

Equivalent to:
```
> MAX(value)
```

But ❗ not always logically identical in all scenarios —  
that’s why we analyze both approaches.

---

## 🧪 SQL Solution (Draft Version)

> This query will be filled with real HR schema examples later.

```sql
-- Employees whose salary is greater than ANY salary in Dept X
SELECT employee_id, first_name, salary
FROM employees
WHERE salary > ANY (
    SELECT salary FROM employees WHERE department_id = 50
);

-- Employees whose salary is greater than ALL salaries in Dept X
SELECT employee_id, first_name, salary
FROM employees
WHERE salary > ALL (
    SELECT salary FROM employees WHERE department_id = 50
);
```

---

## 🧠 Explanation (Step-by-Step Thinking)

We explain:

1) what ANY returns  
2) how Oracle compares multiple values  
3) why output differs from ALL  
4) when MAX/MIN gives misleading results  
5) real-life business interpretation

---

## 💡 Key Takeaways

✔ ANY = “at least one comparator value”  
✔ ALL = “must satisfy all comparator values”  
✔ Result depends on dataset distribution  
✔ Understanding logic matters more than syntax

---

## 📝 Notes & Reflection (My Learning)

Here I write my own thoughts:

- what confused me at first
- what clicked after practice
- how I’d explain this to someone else

This section helps track my learning progress.

---

📌 More case studies coming soon…

