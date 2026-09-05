-- ============================================================
-- E-Commerce Sales Analytics
-- SQL Analysis Queries
-- Database: ecommerce_analytics
-- Table: ecommerce_sales
-- Author: Swatantra Pandey
-- ============================================================

USE ecommerce_analytics;

-- ============================================================
-- 1. BUSINESS KPIs
-- Question: What is the overall business performance?
-- ============================================================

SELECT
    SUM(Revenue) AS Total_Revenue,
    SUM(Profit) AS Total_Profit,
    COUNT(DISTINCT Order_ID) AS Total_Orders,
    SUM(Quantity) AS Total_Units_Sold,
    ROUND(
        SUM(Revenue) / COUNT(DISTINCT Order_ID),
        2
    ) AS Average_Order_Value
FROM ecommerce_sales;

-- ============================================================
-- 2. PRODUCT PERFORMANCE
-- Question: Which products generate the most sales and profit?
-- ============================================================

SELECT
    Product,
    SUM(Quantity) AS Units_Sold,
    SUM(Revenue) AS Total_Revenue,
    SUM(Profit) AS Total_Profit
FROM ecommerce_sales
GROUP BY Product
ORDER BY Total_Revenue DESC;

-- ============================================================
-- 3. CATEGORY PERFORMANCE
-- Question: Which categories generate the most sales and profit?
-- ============================================================

SELECT
    Category,
    SUM(Quantity) AS Units_Sold,
    SUM(Revenue) AS Total_Revenue,
    SUM(Profit) AS Total_Profit
FROM ecommerce_sales
GROUP BY Category
ORDER BY Total_Revenue DESC;

-- ============================================================
-- 4. REGIONAL PERFORMANCE
-- Question: Which regions generate the most sales and profit?
-- ============================================================

SELECT
    Region,
    COUNT(DISTINCT Order_ID) AS Total_Orders,
    SUM(Quantity) AS Units_Sold,
    SUM(Revenue) AS Total_Revenue,
    SUM(Profit) AS Total_Profit
FROM ecommerce_sales
GROUP BY Region
ORDER BY Total_Revenue DESC;

-- ============================================================
-- 5. MONTHLY SALES TREND
-- Question: How do revenue, profit, and orders change over time?
-- ============================================================

SELECT
    DATE_FORMAT(Order_Date, '%Y-%m') AS Month,
    SUM(Revenue) AS Total_Revenue,
    SUM(Profit) AS Total_Profit,
    COUNT(DISTINCT Order_ID) AS Total_Orders
FROM ecommerce_sales
GROUP BY DATE_FORMAT(Order_Date, '%Y-%m')
ORDER BY Month;

-- ============================================================
-- 6. PRODUCT PROFIT MARGIN
-- Question: Which products are the most profitable by margin?
-- ============================================================

SELECT
    Product,
    SUM(Revenue) AS Total_Revenue,
    SUM(Profit) AS Total_Profit,
    ROUND(
        (SUM(Profit) / SUM(Revenue)) * 100,
        2
    ) AS Profit_Margin_Percent
FROM ecommerce_sales
GROUP BY Product
ORDER BY Profit_Margin_Percent DESC;

-- ============================================================
-- 7. TOP CUSTOMERS BY PROFIT
-- Question: Which customers generate the most profit?
-- ============================================================

SELECT
    Customer_ID,
    COUNT(DISTINCT Order_ID) AS Total_Orders,
    SUM(Revenue) AS Total_Revenue,
    SUM(Profit) AS Total_Profit
FROM ecommerce_sales
GROUP BY Customer_ID
ORDER BY Total_Profit DESC
LIMIT 10;

-- ============================================================
-- 8. TOP CUSTOMERS WITH AVERAGE ORDER VALUE
-- Question: Which high-value customers have the highest
--           average order value?
-- ============================================================

SELECT
    Customer_ID,
    COUNT(DISTINCT Order_ID) AS Total_Orders,
    SUM(Revenue) AS Total_Revenue,
    SUM(Profit) AS Total_Profit,
    ROUND(
        SUM(Revenue) / COUNT(DISTINCT Order_ID),
        2
    ) AS Average_Order_Value
FROM ecommerce_sales
GROUP BY Customer_ID
ORDER BY Total_Profit DESC
LIMIT 10;

-- ============================================================
-- 9. TOP 5 PRODUCTS BY PROFIT
-- Question: Which products contribute the most total profit?
-- ============================================================

SELECT
    Product,
    SUM(Profit) AS Total_Profit
FROM ecommerce_sales
GROUP BY Product
ORDER BY Total_Profit DESC
LIMIT 5;

-- ============================================================
-- 10. PAYMENT MODE PERFORMANCE
-- Question: How does business performance vary by payment mode?
-- ============================================================

SELECT
    Payment_Mode,
    COUNT(DISTINCT Order_ID) AS Total_Orders,
    SUM(Quantity) AS Units_Sold,
    SUM(Revenue) AS Total_Revenue,
    SUM(Profit) AS Total_Profit,
    ROUND(
        (SUM(Profit) / SUM(Revenue)) * 100,
        2
    ) AS Profit_Margin_Percent,
    ROUND(
        SUM(Revenue) / COUNT(DISTINCT Order_ID),
        2
    ) AS Average_Order_Value
FROM ecommerce_sales
GROUP BY Payment_Mode
ORDER BY Profit_Margin_Percent DESC;

-- ============================================================
-- 11. DISCOUNT ANALYSIS
-- Question: How does discount level affect sales and profitability?
-- ============================================================

SELECT
    Discount_Percent,
    COUNT(DISTINCT Order_ID) AS Total_Orders,
    SUM(Quantity) AS Units_Sold,
    SUM(Revenue) AS Total_Revenue,
    SUM(Profit) AS Total_Profit,
    ROUND(
        (SUM(Profit) / SUM(Revenue)) * 100,
        2
    ) AS Profit_Margin_Percent
FROM ecommerce_sales
GROUP BY Discount_Percent
ORDER BY Discount_Percent;

-- ============================================================
-- 12. CATEGORY PROFITABILITY
-- Question: Which categories are most profitable?
-- ============================================================

SELECT
    Category,
    SUM(Quantity) AS Units_Sold,
    SUM(Revenue) AS Total_Revenue,
    SUM(Profit) AS Total_Profit,
    ROUND(
        (SUM(Profit) / SUM(Revenue)) * 100,
        2
    ) AS Profit_Margin_Percent
FROM ecommerce_sales
GROUP BY Category
ORDER BY Profit_Margin_Percent DESC;

-- ============================================================
-- 13. REGIONAL PROFITABILITY
-- Question: Which regions are most profitable and efficient?
-- ============================================================

SELECT
    Region,
    COUNT(DISTINCT Order_ID) AS Total_Orders,
    SUM(Quantity) AS Units_Sold,
    SUM(Revenue) AS Total_Revenue,
    SUM(Profit) AS Total_Profit,
    ROUND(
        (SUM(Profit) / SUM(Revenue)) * 100,
        2
    ) AS Profit_Margin_Percent
FROM ecommerce_sales
GROUP BY Region
ORDER BY Profit_Margin_Percent DESC;

-- ============================================================
-- 14. REGION × PRODUCT PERFORMANCE
-- Question: Which products perform best in each region?
-- ============================================================

SELECT
    Region,
    Product,
    SUM(Quantity) AS Units_Sold,
    SUM(Revenue) AS Total_Revenue,
    SUM(Profit) AS Total_Profit
FROM ecommerce_sales
GROUP BY Region, Product
ORDER BY Region, Total_Revenue DESC;

-- ============================================================
-- 15. TOP PRODUCT IN EACH REGION
-- Question: What is the highest-revenue product in each region?
-- ============================================================

WITH product_region_sales AS (
    SELECT
        Region,
        Product,
        SUM(Revenue) AS Total_Revenue,
        SUM(Profit) AS Total_Profit
    FROM ecommerce_sales
    GROUP BY Region, Product
),
ranked_products AS (
    SELECT
        Region,
        Product,
        Total_Revenue,
        Total_Profit,
        ROW_NUMBER() OVER (
            PARTITION BY Region
            ORDER BY Total_Revenue DESC
        ) AS Product_Rank
    FROM product_region_sales
)
SELECT
    Region,
    Product,
    Total_Revenue,
    Total_Profit
FROM ranked_products
WHERE Product_Rank = 1
ORDER BY Region;

-- ============================================================
-- 16. TOP 3 PRODUCTS BY REGION
-- Question: What are the top 3 revenue-generating products
--           within each region?
-- ============================================================

WITH product_region_sales AS (
    SELECT
        Region,
        Product,
        SUM(Revenue) AS Total_Revenue,
        SUM(Profit) AS Total_Profit
    FROM ecommerce_sales
    GROUP BY Region, Product
),
ranked_products AS (
    SELECT
        Region,
        Product,
        Total_Revenue,
        Total_Profit,
        RANK() OVER (
            PARTITION BY Region
            ORDER BY Total_Revenue DESC
        ) AS Revenue_Rank
    FROM product_region_sales
)
SELECT
    Region,
    Product,
    Total_Revenue,
    Total_Profit,
    Revenue_Rank
FROM ranked_products
WHERE Revenue_Rank <= 3
ORDER BY Region, Revenue_Rank;

