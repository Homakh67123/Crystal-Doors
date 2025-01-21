Crystal Doors Dashboard: Informative Overview
The Crystal Doors Dashboard is a meticulously designed analytical tool that provides a comprehensive, interactive snapshot of the business's key performance metrics and operational
insights. It is structured to present data in an intuitive, user-friendly layout that facilitates informed decision-making.
---------------------------------------------------------------------------------------------------------------------------------
Dashboard Structure:
KPIs Section:

Total Orders: Displays the cumulative number of orders placed, giving a quick overview of business activity.     #Total Orders = COUNT('01 01 2024 to 06 12 2024'[Order No])
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total Revenue: Summarizes the total income generated from orders, reflecting the financial health.      #Total revenue = SUM('01 01 2024 to 06 12 2024'[ Order Total  Price])
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Average Order Value: Calculates the average revenue per order, highlighting the spending pattern.   
#Average Order Value = DIVIDE(SUM('01 01 2024 to 06 12 2024'[ Order Total  Price]),SUM('01 01 2024 to 06 12 2024'[ Items Count]))
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Total Discounts: Shows the total value of discounts provided, indicating the effectiveness of promotional strategies.
#TotalDiscounts = SUM('01 01 2024 to 06 12 2024'[ Discount])
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Visuals Section:

Donut Chart: 
Depicts the breakdown of order statuses (Delivered,draft,Production,Production Completed,Production Programmed, Production Pressed,Waiting Confirmation,Production Queued,Waiting Payment)
to track the order lifecycle.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Bar Chart: 
Lists the top 5 customers by revenue, showcasing key contributors to the business’s profitability.

The DAX expression uses the GROUPBY function in Power BI to create a summary table. It groups the data from the table '01 01 2024 to 06 12 2024' by the Customer column and calculates the count of Order No for each customer using COUNTX with CURRENTGROUP(). The result is a new table (order_customer) that shows each unique customer along with the number of orders they placed during the specified date range.

#order_customer = GROUPBY('01 01 2024 to 06 12 2024','01 01 2024 to 06 12 2024'[ Customer],"count",COUNTX(CURRENTGROUP(),'01 01 2024 to 06 12 2024'[Order No]))
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Stacked Bar Chart: 
Compares different delivery types against on-time and delayed deliveries, helping to monitor logistics efficiency.

#OnTimeStatus = IF(
    DATEDIFF('01 01 2024 to 06 12 2024'[ Created On], '01 01 2024 to 06 12 2024'[ Delivery Date], DAY) <= 5,
    "On-Time",
    "Delayed"
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Scatter Chart: Analyzes popular product attributes (Design, Thickness, Edge Type) in relation to total orders, aiding in product performance assessment.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Pie Chart: Shows the distribution of updates by users, indicating engagement levels.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Filters and Slicers:

Date : Enables temporal analysis by filtering data within a specified time frame.
Customer Name: Allows focus on individual customer data for personalized insights.
Product Design: Filters data by different product designs to analyze trends and preferences.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Key Features:
Interactivity: The dashboard is equipped with interactive elements such as clickable visuals that dynamically update KPIs and other charts, enhancing user engagement.
Tooltips: Hovering over data points provides additional context and details, enabling deeper insights without cluttering the visual space.
Drill-Down Capability: Users can explore granular details by interacting with charts, making it easy to dive into specific data points.
Benefits:
Comprehensive Overview: The dashboard aggregates essential business metrics and operational data on a single page, ensuring that critical information is readily accessible.
Actionable Insights: The combination of KPIs, various chart types, and slicers provides a robust analytical framework to derive actionable business insights.
User-Friendly Design: The clean layout and interactive features are designed to enhance usability and facilitate quick data interpretation.
