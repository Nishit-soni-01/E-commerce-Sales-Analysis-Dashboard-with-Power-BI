# E-commerce-Sales-Analysis-Dashboard

### Dashboard Link: https://app.powerbi.com/Redirect?action=OpenReport&appId=e81aecda-c46c-48d4-927e-a09b3bdfc65b&reportObjectId=c7e3d424-f22e-4a7c-9c4c-fa9555fe1ef4&ctid=3ad87f0e-1f93-41bd-94f4-82c37d971c88&reportPage=79fa2a2a2000ddbc59eb&pbi_source=appShareLink&portalSessionId=b9553b75-43ce-48e9-acec-06112e68f3b5

## Problem Statement

This interactive dashboard provides a multi-faceted analysis of e-commerce sales data, designed to empower business leaders with actionable insights. The primary goal is to dissect sales performance through various lenses: product popularity, geographical distribution, promotional effectiveness, and long-term trends.

The report answers critical business questions such as:
* Which products are the top and bottom performers by sales and quantity?
* How do sales and profits trend over different time periods?
* What is the relationship between net sales and profits?
* Which cities are the most significant contributors to sales?
* How effective are different promotional campaigns?

By enabling dynamic period-over-period comparisons and drill-down capabilities, this tool helps stakeholders identify growth opportunities, optimize inventory, and refine marketing strategies.

### Steps Followed

-   **Step 1:** Loaded the dataset (CSV/Excel file) into Power BI Desktop.
-   **Step 2:** Opened the Power Query Editor to perform data cleaning and transformation. Checked for errors, handled null values, and ensured correct data types for columns like `Date`, `Net Sales`, and `Profits`.
-   **Step 3:** In the report view, a clean and professional theme was chosen to ensure clarity and readability of the visuals.
-   **Step 4:** Added key **Slicers** to the report for dynamic filtering, including `Date`, `Customer Name`, `Product Name`, and `Promotion Name`.
-   
  <img width="1407" height="118" alt="Screenshot 2025-09-20 153333" src="https://github.com/user-attachments/assets/2708a968-496a-4c97-a15b-bf0b5946757f" />

-   **Step 5:** To enable the period-over-period comparison feature, two **Calculated Tables** for dates were created using the following DAX expressions:
    ```dax
    Date Table 1 = CALENDARAUTO()
    ```
    ```dax
    Date Table 2 = CALENDARAUTO()
    ```
<img width="1349" height="185" alt="Screenshot 2025-09-20 162342" src="https://github.com/user-attachments/assets/a0d0a678-1570-483e-854b-ac01a7ecf02a" />

  
-   **Step 6:** Created several key DAX **Measures**. The measures for period comparison were specifically designed to work with an inactive relationship to `Date Table 2`, activated by the `USERELATIONSHIP` function.
    
    *Measures for Period 2 Comparison:*
    ```dax
    Quantity sold = CALCULATE(SUM('Fact Table'[Units Sold]),
    ALL('Date Table 1'),
    USERELATIONSHIP('Date Table 2'[Date],'Fact Table'[Date (dd/mm/yyyy)]))
    ```
    ```dax
    Sum of Net Sales = CALCULATE(SUM('Fact Table'[Net sales  ]),
    ALL('Date Table 1'),
    USERELATIONSHIP('Date Table 2'[Date],'Fact Table'[Date (dd/mm/yyyy)]))
    ```
    ```dax
    Total Profit = CALCULATE(SUM('Fact Table'[Profits  ]),
    ALL('Date Table 1'),
    USERELATIONSHIP('Date Table 2'[Date],'Fact Table'[Date (dd/mm/yyyy)]))
    ```
    *Base Measure for General Visuals:*
    ```dax
    Sum Dim = SUM('Fact Table'[Net sales  ])
    ```
-   **Step 7:** Designed the main dashboard page with a variety of visuals:
    -   A **Map** visual to show "Sales by City."
    -   A **Bar Chart** to display "Average Discount by Promotion Categories."
    -   A **Scatter Plot** to visualize the relationship between "Profits V/s Net sales."
    -   An **Area Chart** to show the trend of "Net Sales by Period."
-   **Step 8:** Created a dedicated "Product Details" page.
    -   Used **Bar Charts** to showcase the "Top 5 Products" and "Bottom 5 Products" based on both `Total Sales` and `Total Quantity Sold`.
-   **Step 9:** Built a "Period Comparison" page.
    -   Implemented two separate **Date Slicers** (one linked to 'Date Table 1' and the other to 'Date Table 2') allowing users to select two distinct time periods.
    -   Used **Bar Charts** and **KPI Cards** to compare `Total Sales`, `Total Profit`, and `Total Quantity Sold` between the two selected periods.
-   **Step 10:** Added a "Detailed View" page containing a **Table** visual. This table displays granular order-level information and can be filtered using the main slicers, allowing for deep-dive analysis.
-   **Step 11:** The final report was published to the Power BI Service to be shared with relevant stakeholders.

---

# Snapshot of Dashboard
<img width="1305" height="721" alt="Screenshot 2025-09-20 143907" src="https://github.com/user-attachments/assets/6a593598-e2d1-4f61-9aa4-34183fd11a56" />
<img width="1291" height="725" alt="Screenshot 2025-09-20 143955" src="https://github.com/user-attachments/assets/307f20ad-590d-4bdd-9548-40461da89b3a" />
<img width="1332" height="725" alt="Screenshot 2025-09-20 143940" src="https://github.com/user-attachments/assets/fbdfb629-8056-4e69-afbd-075f8e2de807" />
<img width="1301" height="724" alt="Screenshot 2025-09-20 143928" src="https://github.com/user-attachments/assets/668f2626-6afc-4b7f-9e41-62a748e34035" />
<img width="1299" height="724" alt="Screenshot 2025-09-20 144006" src="https://github.com/user-attachments/assets/d6c794a1-33d6-4b30-8214-efef3c946139" />



---

# Report Snapshot (Different Views)
<img width="1410" height="792" alt="Screenshot 2025-09-20 163023" src="https://github.com/user-attachments/assets/27a19132-1ab7-495b-8982-e21dc1d3cef9" />
<img width="1421" height="800" alt="Screenshot 2025-09-20 162946" src="https://github.com/user-attachments/assets/132f1a64-10df-42ce-95c2-2864104f6f28" />
<img width="1363" height="779" alt="Screenshot 2025-09-20 162920" src="https://github.com/user-attachments/assets/dfc737c4-f975-4ed8-9ce1-20eb2eca5dcf" />
<img width="1320" height="781" alt="Screenshot 2025-09-20 162903" src="https://github.com/user-attachments/assets/220e52d7-3cbd-4a47-ae1d-dc8838430e37" />
<img width="1402" height="770" alt="Screenshot 2025-09-20 162830" src="https://github.com/user-attachments/assets/97849215-9d67-4019-bf67-1f2520a9fc04" />
<img width="1409" height="760" alt="Screenshot 2025-09-20 162805" src="https://github.com/user-attachments/assets/74dce97b-a0cb-427d-bb47-6e71b502f297" />
<img width="1402" height="776" alt="Screenshot 2025-09-20 162749" src="https://github.com/user-attachments/assets/f06d842b-d8e3-485e-aca5-1ba28a596288" />
<img width="1397" height="783" alt="Screenshot 2025-09-20 162721" src="https://github.com/user-attachments/assets/c690460b-28f6-435a-a620-b1a3d13ab52e" />
<img width="1396" height="776" alt="Screenshot 2025-09-20 162653" src="https://github.com/user-attachments/assets/bf270109-c027-41df-8a2c-59a522987580" />
<img width="1393" height="788" alt="Screenshot 2025-09-20 162629" src="https://github.com/user-attachments/assets/e8c202b3-15f2-41c5-9875-5e38aafd3a36" />
<img width="1397" height="775" alt="Screenshot 2025-09-20 163044" src="https://github.com/user-attachments/assets/a770d3e5-2da8-4154-8e8e-d1a27cc41c3e" />





---

# Insights

This dashboard reveals several key insights into the company's sales performance between Jan 2020 and Dec 2024.

### [1] Overall Performance KPIs

-   **Total Sales:** \$122 Million
-   **Total Profit:** \$12.2 Million
-   **Total Quantity Sold:** 7.1K Units
-   **Total Orders Processed:** 3,510
-   **Overall Profit Margin:** The data indicates a healthy and consistent **10%** profit margin ($12.2M profit on $122M sales).

### [2] Product Performance

-   **Top Selling Products:** High-value electronics dominate the sales charts, with the **Apple iPhone 14** (\$21.4M) and **Apple MacBook Air** (\$19.6M) being the top revenue generators.
-   **Bottom Selling Products:** Lower-priced items such as the **Tupperware Lunch Box** (\$0.26M) and **Colgate Toothpaste** (\$0.02M) are among the lowest contributors to sales revenue.
-   **Top Products by Quantity:** While the **Apple iPhone 14** also leads in quantity, other items like **Raymond Suit** and **Fossil Smartwatch** appear in the top 5 by volume, indicating their popularity despite lower price points.

### [3] Promotional Effectiveness

-   The **"Weekend Sale"** is the most aggressive promotion, offering the highest average discount (23K).
-   Promotions like **"New Year Sale"** and **"Festive Discount"** have significantly lower average discounts, suggesting they may be targeted at specific products or have different strategic goals.

### [4] Geographical Distribution

-   Sales are heavily concentrated in major metropolitan cities, including **Delhi, Mumbai, Bangalore, Pune, and Nagpur**, which are key markets.

### [5] Financial Health

-   The scatter plot of **Profits vs. Net Sales** shows a strong, positive linear relationship. This indicates that profitability scales consistently with sales, and there are no widespread issues with unprofitable orders.

### [6] Sales Trends

-   The "Net Sales by Period" chart, showing daily sales, indicates high volatility and frequent spikes. This pattern is typical for a retail business and can be analyzed further on a monthly or quarterly basis to identify clear seasonality.
