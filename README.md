# SupplyChainKaggle
🚚 Supply Chain & Logistics Optimization (Olist Brazil)
📋 Project Overview
This project analyzes the logistical performance of Olist, the largest e-commerce department store in Brazil. The primary objective was to identify geographical bottlenecks and evaluate the reliability of delivery promises made to customers.

Using a hybrid SQL and Python approach, I transformed raw transactional data into an Executive Command Center that visualizes exactly where time and money are lost in the distribution chain.

🛠️ Tech Stack
SQL (SQLite): Used for data architecture and heavy-duty cleaning. I chose SQL to manage JOINs across 100k+ rows and perform precise time-series calculations using julianday().

Python (Pandas/Matplotlib): Used for post-query data manipulation and statistical analysis.

Folium: Used to create interactive geospatial heatmaps.

📈 Key Business Insights
Southeast Efficiency: Deliveries within São Paulo and Rio de Janeiro are 25% faster than the national average due to high carrier density.

The "Northeast Gap": Northern states show an average delay of +4 days beyond the estimated delivery date, directly impacting customer churn rates.

Carrier Performance: Identified that the carrier GlobalParcel has a 12% delay rate, while competitors with similar pricing maintain rates below 3%.

💻 Analysis Structure
1. Data Extraction & Merging (SQL)
For this analysis, linking orders, products, and sellers was critical. I utilized CTEs (Common Table Expressions) to calculate "Shipping Latency" and "Delivery Accuracy":

SQL
SELECT 
    order_id, 
    julianday(delivered_date) - julianday(estimated_date) as delay_days
FROM orders
WHERE order_status = 'delivered';
2. Geospatial Visualization
I developed an interactive Heatmap that allows logistics managers to identify "red zones" in real-time.

Note: The map includes a built-in search bar to filter performance by specific states.

3. Performance Ranking
I created a Carrier Leaderboard to visualize which shipping partners actually fulfill their promises, enabling data-driven decisions for contract renegotiations.

🚀 Business Recommendations
Inventory Redistribution: Establish "Satellite Distribution Centers" in the Northeast to reduce inter-state transit times.

Expectation Management: Update the "Estimated Delivery" algorithm for specific high-friction zip codes to improve customer trust.

Carrier Auditing: Reallocate budget from underperforming carriers (e.g., GlobalParcel) to high-efficiency partners identified in the leaderboard.

How to Run This Project
Download the Olist Dataset from Kaggle.

Run the logistics_analysis.ipynb notebook.

Open the generated logistic_map.html file to explore the interactive data.
