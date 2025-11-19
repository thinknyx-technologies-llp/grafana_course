# MySQL Tables for Grafana Demo

## Website Traffic Table

```sql
CREATE TABLE website_traffic (
    id INT AUTO_INCREMENT PRIMARY KEY,
    visit_date DATE NOT NULL,
    page_views INT NOT NULL,
    unique_visitors INT NOT NULL
);

INSERT INTO website_traffic (visit_date, page_views, unique_visitors)
VALUES
('2025-11-01', 120, 80),
('2025-11-02', 180, 120),
('2025-11-03', 200, 150),
('2025-11-04', 170, 110),
('2025-11-05', 220, 160),
('2025-11-06', 300, 210),
('2025-11-07', 250, 180);
```

## Daily Sales Table

```sql
CREATE TABLE daily_sales (
    id INT AUTO_INCREMENT PRIMARY KEY,
    sale_date DATE NOT NULL,
    product VARCHAR(50) NOT NULL,
    quantity INT NOT NULL,
    revenue DECIMAL(10,2) NOT NULL
);

INSERT INTO daily_sales (sale_date, product, quantity, revenue)
VALUES
('2025-11-01', 'Laptop', 5, 2500.00),
('2025-11-01', 'Keyboard', 10, 300.00),
('2025-11-01', 'Mouse', 12, 180.00),
('2025-11-02', 'Laptop', 7, 3500.00),
('2025-11-02', 'Mouse', 20, 300.00),
('2025-11-03', 'Laptop', 4, 2000.00);
```

# MySQL Queries for visualization 

## Daily Unique Visitors

```sql
SELECT
    visit_date AS time,
    unique_visitors
FROM website_traffic
ORDER BY visit_date;
```

## Page Views vs Unique Visitors 

```sql
SELECT
    visit_date,
    page_views,
    unique_visitors
FROM website_traffic
ORDER BY visit_date;
```

## Daily Revenue Over Time 

```sql
SELECT
    sale_date AS time,
    SUM(revenue) AS total_revenue
FROM daily_sales
GROUP BY sale_date
ORDER BY sale_date;
```

## Revenue Contribution by Product

```sql
SELECT
    product,
    SUM(revenue) AS revenue
FROM daily_sales
GROUP BY product;
```
