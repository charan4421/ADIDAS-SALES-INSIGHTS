******Adidas Sales Analysis Dashboard (Power BI + Python + Machine Learning)******
***This project presents an interactive sales analysis dashboard for Adidas, visualized in Power BI.
It provides comprehensive insights into Adidas' sales performance across various dimensions such as time, regions, products, and retailers.
The dashboard integrates Python scripts for data preprocessing and leverages machine learning techniques for sales prediction and optimization*****.
***PYTHON CODE***
import pandas as pd
import numpy as np

# Loading the  dataset into the python
df = pd.read_csv('adidas_sales_data.csv')
df.fillna(0, inplace=True)
df['Invoice Date'] = pd.to_datetime(df['Invoice Date'])
start_date = '2020-01-15'
end_date = '2021-12-17'
filtered_df = df[(df['Invoice Date'] >= start_date) & (df['Invoice Date'] <= end_date)]
monthly_sales = filtered_df.groupby(filtered_df['Invoice Date'].dt.to_period('M')).agg({
    'Total Sales': 'sum',
    'Units Sold': 'sum'
}).reset_index()
print(monthly_sales.head())

**Machine Learning Integration**
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error
X = filtered_df[['Units Sold', 'Price per Unit', 'Operating Margin']]
y = filtered_df['Total Sales']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
model = RandomForestRegressor(n_estimators=100, random_state=42)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
mse = mean_squared_error(y_test, y_pred)
print(f"Mean Squared Error: {mse:.2f}")
example_data = np.array([[5000, 45, 0.42]])  # Example input (Units Sold, Price per Unit, Operating Margin)
predicted_sales = model.predict(example_data)
print(f"Predicted Sales: ${predicted_sales[0]:,.2f}")

***To provide advanced insights and predictive capabilities:

Predictive Sales Model: Using historical sales data, a machine learning model was built in Python to predict future sales trends.

Optimization: The model can forecast sales per product and region to optimize stock levels, pricing strategies, and marketing efforts.

**Tools & Technologies**

Power BI: For data visualization and dashboard creation.

Python: Used for data wrangling, preprocessing, and integrating machine learning models.

Scikit-learn: Machine learning algorithms for sales prediction.

Pandas & NumPy: Data manipulation and analysis.

Matplotlib & Seaborn: For data visualization in Python.

**Data Insights**

1. Seasonality Impact: The sales trend demonstrates clear seasonality, with peaks during summer months, likely due to increased sports activities and events.


2. Geographical Strength: The West and Midwest regions dominate the sales, suggesting the need for targeted marketing in other underperforming regions.


3. Retailer Strategy: West Gear and Foot Locker outperform other retailers, highlighting key partnerships. Lower performance from online platforms like Amazon suggests potential areas for growth in digital sales.


4. Product Focus: Men’s Street Footwear is the best-selling category, indicating high demand in this segment. The insights can inform future product development and marketing campaigns.

**SNAP SHOT OF FINAL REPORT**
![Screenshot 2024-09-14 212632](https://github.com/user-attachments/assets/65076e48-23ec-476f-b645-68e1238de030)




***ACHIEVMENTS BY THE REPORT AND PROJECT***`
1. Comprehensive Sales Dashboard: Successfully developed an interactive Power BI dashboard that visualizes Adidas' sales data across multiple dimensions such as time, region, product, and retailer.


2. Data-Driven Insights: Enabled data-driven decision-making by providing actionable insights into sales performance, regional strengths, and key product categories.


3. Predictive Modeling: Integrated a machine learning model using Python (Scikit-learn) to predict future sales trends, empowering stakeholders with foresight to optimize inventory, pricing, and marketing strategies.


4. Enhanced Visualization: Combined advanced visualizations and analytics in Power BI, including geographical sales heatmaps, product-specific sales, and retailer performance breakdowns, for better data comprehension.


5. Sales Optimization: The project highlights strategies to optimize sales performance by identifying top-performing regions, products, and retailers, and suggests areas for improvement, particularly in underperforming regions and digital sales channels.


6. Cross-Platform Integration: Seamlessly integrated Python scripts within Power BI to preprocess large datasets, bridging the gap between robust programming and user-friendly visualization.


7. Seasonality Analysis: Provided clear insights into the seasonality of Adidas sales, showcasing how peak sales occur during summer months, leading to better planning for marketing and inventory management.


8. Targeted Regional Marketing Insights: Identified geographical areas where Adidas has untapped sales potential, enabling region-specific marketing and sales strategies to drive further growth.




