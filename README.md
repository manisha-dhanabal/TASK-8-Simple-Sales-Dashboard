#  Task 8 — Simple Sales Dashboard (Power BI)

This project demonstrates how to build a **basic interactive sales dashboard** using **Power BI**. The dashboard visualizes sales and profit performance by **month, region, and product category**, based on a Superstore-style dataset.

## Files in this Repository
- **`Superstore_Sales.csv`** — Sample dataset with fields:  
  - `Order Date` (Date)  
  - `Region` (East, West, Central, South)  
  - `Category` (Furniture, Technology, Office Supplies)  
  - `Sales` (numeric, ₹ values)  
  - `Profit` (numeric, ₹ values)  
- **Dashboard Screenshot / PDF** — Export of the Power BI dashboard.  
- **README.md** — Documentation (this file).  



## 🚀 How to Recreate the Dashboard in Power BI

1. **Load the dataset**
   - Open Power BI Desktop → **Home → Get Data → Text/CSV**  
   - Select `Superstore_Sales.csv` → **Load**  

2. **Check data types**
   - `Order Date` → Date  
   - `Region`, `Category` → Text  
   - `Sales`, `Profit` → Decimal Number  

3. **Create Month-Year column**
   ```DAX
   MonthYear = FORMAT('Superstore_Sales'[Order Date], "MMM yyyy")
   YearMonthSort = YEAR('Superstore_Sales'[Order Date]) * 100 
                 + MONTH('Superstore_Sales'[Order Date])
   ```
   - Sort `MonthYear` by `YearMonthSort` to ensure chronological order.  

4. **Create visuals**
   - **Line chart** → Sales over `MonthYear`  
   - **Bar chart** → Sales by `Region`  
   - **Donut chart** → Sales by `Category`  
   - **Slicer** → Region  

5. **(Optional) KPI Cards**
   ```DAX
   Total Sales  = SUM('Superstore_Sales'[Sales])
   Total Profit = SUM('Superstore_Sales'[Profit])
   Profit Margin = DIVIDE([Total Profit], [Total Sales])
   ```

6. **Polish & Export**
   - Add titles, enable data labels, align visuals neatly.  
   - **File → Export → PDF** (or take a screenshot).  



##  Example Insights
From the sample dataset:  
- **West region** generated the highest sales, followed by East.  
- **Technology** was the top-selling category, ahead of Furniture and Office Supplies.  
- **March 2025** was the peak sales month.  
- Overall **profit margin ~X%** (exact value shown on KPI card).  
