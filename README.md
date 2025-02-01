# Apple Products Analysis

This notebook analyzes data from Apple products, specifically focusing on iPhones, and generates several visualizations to explore the relationship between product ratings, reviews, and pricing.

## Required Libraries
```python
import pandas as pd
import numpy as np
import plotly.express as px
import plotly.graph_objects as go
```

## Data Loading and Initial Exploration
First, we load the dataset and perform some basic exploration to understand its structure and check for missing values.

```python
# Load the dataset
data = pd.read_csv("apple_products.csv")

# Display the first few rows of the dataset
print(data.head())

# Check for missing values in each column
print(data.isnull().sum())

# Get statistical summary of the numeric columns
print(data.describe())
```

## Sorting the Highest Rated Products
Next, we sort the products based on their "Star Rating" and select the top 10 highest-rated products.

```python
# Sort the data by "Star Rating" in descending order
highest_rated = data.sort_values(by=["Star Rating"], ascending=False)

# Get the top 10 highest-rated products
highest_rated = highest_rated.head(10)

# Display the names of the highest-rated products
print(highest_rated['Product Name'])
```

## Bar Chart: Number of Ratings for the Highest Rated iPhones
We generate a bar chart to show the number of ratings for the highest-rated iPhones.

```python
# Plot a bar chart for the number of ratings of the highest-rated iPhones
figure = px.bar(highest_rated, 
                x='Product Name', 
                y='Number Of Ratings',
                title="Number of Ratings of Highest Rated iPhones")

# Show the plot
figure.show()
```

## Bar Chart: Number of Reviews for the Highest Rated iPhones
Similarly, we create a bar chart to show the number of reviews for the highest-rated iPhones.

```python
# Plot a bar chart for the number of reviews of the highest-rated iPhones
figure = px.bar(highest_rated, 
                x='Product Name', 
                y='Number Of Reviews',
                title="Number of Reviews of Highest Rated iPhones")

# Show the plot
figure.show()
```

## Scatter Plot: Sale Price vs Number of Ratings
We explore the relationship between the sale price of iPhones and the number of ratings they received, using a scatter plot.

```python
# Create a scatter plot for Sale Price vs Number of Ratings
figure = px.scatter(data_frame=data, 
                    x="Number Of Ratings", 
                    y="Sale Price",
                    size="Discount Percentage", 
                    trendline="ols",  # Add a trendline (OLS regression)
                    title="Relationship between Sale Price and Number of Ratings of iPhones")

# Show the plot
figure.show()
```

## Scatter Plot: Discount Percentage vs Number of Ratings
Next, we look at the relationship between the discount percentage and the number of ratings for iPhones.

```python
# Create a scatter plot for Discount Percentage vs Number of Ratings
figure = px.scatter(data_frame=data, 
                    x="Number Of Ratings", 
                    y="Discount Percentage",
                    size="Sale Price", 
                    trendline="ols",  # Add a trendline (OLS regression)
                    title="Relationship between Discount Percentage and Number of Ratings of iPhones")

# Show the plot
figure.show()
```

