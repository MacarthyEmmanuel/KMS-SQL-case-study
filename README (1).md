```markdown
# KMS SQL Case Study – Kultra Mega Stores (2009–2012)

## 🏢 Company Overview  
Kultra Mega Stores (KMS), headquartered in Lagos, Nigeria, specializes in office supplies, technology, and furniture.  
This case study analyzes sales data from 2009–2012 for the Abuja division to extract actionable insights.

---

## 📝 Analysis & Insights

### ✅ 1. Top Product Category by Sales  
```sql
SELECT TOP 1 Product_Category, SUM(Sales) AS TotalSales
FROM [KMS Sql Case Study]
GROUP BY Product_Category
ORDER BY TotalSales DESC;
```
**Result:**  
`Technology | ₦5,984,248.18`  

**Insight:**  
- Technology was the highest-selling category  
- Prioritize tech product promotions and bundles  
- Expand tech offerings in high-performing regions  

---

### ✅ 2. Top/Bottom 3 Regions by Sales  
```sql
-- Top 3 Regions
SELECT TOP 3 Region, SUM(Sales) AS TotalSales
FROM [KMS Sql Case Study]
GROUP BY Region
ORDER BY TotalSales DESC;

-- Bottom 3 Regions
SELECT TOP 3 Region, SUM(Sales) AS TotalSales
FROM [KMS Sql Case Study]
GROUP BY Region
ORDER BY TotalSales ASC;
```
**Results:**  
| Region                | Sales          |
|-----------------------|----------------|
| **Top 3**             |                |
| West                 | ₦3,597,549.27  |
| Ontario              | ₦3,063,212.48  |
| Prarie               | ₦2,837,304.61  |
| **Bottom 3**          |                |
| Nunavut              | ₦116,376.48    |
| Northwest Territories| ₦800,847.33    |
| Yukon                | ₦975,867.38    |

**Insight:**  
- Allocate more resources to top regions  
- Develop targeted promotions for underperforming regions  

---

### ✅ 3. Appliance Sales in Ontario  
```sql
SELECT SUM(Sales) AS Total_Appliance_Sales
FROM [KMS Sql Case Study]
WHERE Region = 'Ontario';
```
**Result:**  
`₦3,063,212.48`  

**Insight:**  
- Strong appliance performance suggests bundling opportunities  
- Localized marketing campaigns recommended  

---

### ✅ 4. Revenue Growth from Bottom 10 Customers  
```sql
SELECT TOP 10 Product_Category, Product_Name, Region, Unit_Price, 
       Shipping_Cost, Ship_Mode, Customer_Name, SUM(Sales) AS TotalSales
FROM [KMS Sql Case Study]
GROUP BY Product_Category, Product_Name, Region, Unit_Price, 
         Shipping_Cost, Ship_Mode, Customer_Name
ORDER BY TotalSales ASC;
```
**Insight:**  
- Implement retention campaigns for low-revenue customers  
- Analyze purchase patterns for personalized offers  
- Introduce loyalty programs  

---

### ✅ 5. Highest Shipping Cost Method  
```sql
SELECT Ship_Mode, SUM(Shipping_Cost) AS Total_Shipping_Cost
FROM [KMS Sql Case Study]
GROUP BY Ship_Mode
ORDER BY Total_Shipping_Cost DESC;
```
**Result:**  
`Delivery Truck | ₦51,971.94`  

**Insight:**  
- Optimize delivery routes for trucks  
- Negotiate carrier contracts  
- Use air freight only for high-priority orders  

---

### ✅ 6. Most Valuable Customers  
```sql
SELECT TOP 5 Customer_Name, SUM(Sales) AS Total_Sales
FROM [KMS Sql Case Study]
GROUP BY Customer_Name
ORDER BY Total_Sales DESC;
```
**Top Customers:**  
1. Sean Miller  
2. Emily Phan  
3. Philip Collins  
4. Jordan Turner  
5. Laura Graham  

**Insight:**  
- Create VIP programs for top customers  
- Assign dedicated account managers  
- Provide early access to new products  

---

### ✅ 7. Top Small Business Customer  
```sql
SELECT TOP 1 Customer_Name, Customer_Segment, SUM(Sales) AS Total_Sales
FROM [KMS Sql Case Study]
WHERE Customer_Segment = 'Small Business'
GROUP BY Customer_Segment, Customer_Name
ORDER BY Total_Sales DESC;
```
**Result:**  
`Dennis Kane | ₦75,967.59`  

**Insight:**  
- Develop B2B loyalty programs  
- Offer volume discounts to retain SMB clients  

---

### ✅ 8. Most Active Corporate Customer  
```sql
SELECT Customer_Name, COUNT(Order_ID) AS Order_Count
FROM [KMS Sql Case Study]
WHERE Customer_Segment = 'Corporate'
  AND Order_Date BETWEEN '2009-01-01' AND '2012-12-31'
GROUP BY Customer_Name
ORDER BY Order_Count DESC;
```
**Result:**  
`Justin Knight | 6 Orders`  

**Insight:**  
- Assign dedicated account managers  
- Implement tiered rewards for frequent purchasers  

---

### ✅ 9. Most Profitable Consumer  
```sql
SELECT TOP 1 Customer_Name, Customer_Segment, SUM(Profit) AS Total_Profit
FROM [KMS Sql Case Study]
WHERE Customer_Segment = 'Consumer'
GROUP BY Customer_Name, Customer_Segment
ORDER BY Total_Profit DESC;
```
**Result:**  
`Emily Phan | ₦34,005.44`  

**Insight:**  
- Analyze high-margin products purchased  
- Target similar customers with premium offers  

---

### ✅ 10. Customer Returns Analysis  
```sql
SELECT kms.Order_ID, kms.Customer_Name, kms.Customer_Segment, os.Status
FROM [KMS Sql Case Study] kms
JOIN Order_Status os ON os.Order_ID = kms.Order_ID;
```
**Insight:**  
- Identify frequently returned products  
- Implement customer feedback systems  
- Review quality control processes  

---

### ✅ 11. Shipping Cost vs Order Priority  
```sql
SELECT Ship_Mode, Order_Priority, 
       COUNT(*) AS Order_Count, 
       AVG(Shipping_Cost) AS Avg_Shipping_Cost
FROM [KMS Sql Case Study]
GROUP BY Ship_Mode, Order_Priority
ORDER BY Order_Count DESC;
```
**Insight:**  
- Align shipping methods with order urgency  
- Develop clear shipping policy tiers  
- Optimize express shipping usage  

---

## 🛠️ Skills Utilized  
- SQL Grouping & Aggregation  
- Data Filtering (`TOP`, `WHERE`, `ORDER BY`)  
- Table Joins  
- Multi-segment Analysis  
- Business Insight Generation  
```

---
## Author
- Macarthy Emmanuel
