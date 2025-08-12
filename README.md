

SELECT 
  o.order_id, o.order_date, o.quantity,
  c.customer_name, c.city,
  p.product_name, p.price,
  cmp.company_name, cmp.industry
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN products p ON o.product_id = p.product_id
JOIN companies cmp ON c.company_id = cmp.company_id;



SELECT cmp.company_name, SUM(p.price * o.quantity) AS total_revenue
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN products p ON o.product_id = p.product_id
JOIN companies cmp ON c.company_id = cmp.company_id
GROUP BY cmp.company_name
ORDER BY total_revenue DESC;

SELECT DATE_FORMAT(order_date, '%Y-%m') AS month, 
       SUM(p.price * o.quantity) AS monthly_revenue
FROM orders o
JOIN products p ON o.product_id = p.product_id
GROUP BY month
ORDER BY month;

SELECT DATE_FORMAT(order_date, '%Y-%m') AS month, 
       SUM(p.price * o.quantity) AS monthly_revenue
FROM orders o
JOIN products p ON o.product_id = p.product_id
GROUP BY month
ORDER BY month;


SELECT c.customer_name, SUM(p.price * o.quantity) AS total_spent
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN products p ON o.product_id = p.product_id
GROUP BY c.customer_name
ORDER BY total_spent DESC
LIMIT 5;


