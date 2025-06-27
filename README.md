# finaltask4

## 📊 Task 4: SQL for Data Analysis - Elevate Labs Internship

### ✅ Objective:
Use SQL queries to extract and analyze data from a relational ecommerce-style database.

---

### 🛠 Tools Used:
- MySQL Workbench
- Dataset: final4 (tables: orders, order_details, pizzas, pizza_types)

---

### 📁 Files Included:
- task4_final4.sql → All SQL queries used in this task
- screenshots/ → Folder containing screenshots of SQL outputs
- README.md → This explanation file

---

### 🔍 SQL Queries Summary:

1. *Total number of orders*
    sql
    SELECT COUNT(*) AS total_orders FROM orders;
    

2. *Total number of pizzas ordered*
    sql
    SELECT SUM(quantity) AS total_pizzas_ordered FROM order_details;
    

3. *Total revenue*
    sql
    SELECT SUM(od.quantity * p.price) AS total_revenue
    FROM order_details od
    JOIN pizzas p ON od.pizza_id = p.pizza_id;
    

4. *Most popular pizza*
    sql
    SELECT od.pizza_id, SUM(od.quantity) AS total_ordered
    FROM order_details od
    GROUP BY od.pizza_id
    ORDER BY total_ordered DESC
    LIMIT 1;
    

5. *Top 5 best-selling pizza types*
    sql
    SELECT pt.name, SUM(od.quantity) AS total_sold
    FROM order_details od
    JOIN pizzas p ON od.pizza_id = p.pizza_id
    JOIN pizza_types pt ON p.pizza_type_id = pt.pizza_type_id
    GROUP BY pt.name
    ORDER BY total_sold DESC
    LIMIT 5;
    

6. *Daily revenue*
    sql
    SELECT o.order_date, SUM(od.quantity * p.price) AS daily_revenue
    FROM orders o
    JOIN order_details od ON o.order_id = od.order_id
    JOIN pizzas p ON od.pizza_id = p.pizza_id
    GROUP BY o.order_date;
    

7. *Create a view for daily revenue*
    sql
    CREATE VIEW daily_revenue_summary AS
    SELECT o.order_date, SUM(od.quantity * p.price) AS revenue
    FROM orders o
    JOIN order_details od ON o.order_id = od.order_id
    JOIN pizzas p ON od.pizza_id = p.pizza_id
    GROUP BY o.order_date;
    

8. *Create index for optimization*
    sql
    CREATE INDEX idx_order_date ON orders(order_date);
    

---

### 📌 Submission Notes:
- All SQL queries were tested in MySQL Workbench.
- Screenshots of output are stored in /screenshots/ folder.
- No paid tools used; everything done using open-source MySQL.

---

### ✍ Prepared by:
*Name:* Ankit Kumar Maity  
*GitHub:* [Ankit2004ml](https://github.com/Ankit2004ml)
