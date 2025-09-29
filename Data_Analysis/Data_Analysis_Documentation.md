# Project: Restaurant Location Recommendation Tool & Analysis ##

# Goal
To explore the dataset using EDA to identify patterns and trends that influence successful restaurant locations, focusing on transport access, population density, and competition, supported by visualizations and summary insights.

##  1.Perform exploratory data analysis (EDA) using descriptive statistics and visualizations. 

<pre>dataset.head() </pre>

returns the first 5 rows of the dataset, helping you quickly preview the structure and sample data.


 <pre>dataset.describe() </pre>

 dataset.describe() provides summary statistics (like mean, median, min, max, etc.) for all numeric columns, giving insights into data distribution and range.


 <pre> # Selecting only numeric columns for correlation
numeric_cols = dataset.select_dtypes(include=['float64', 'int64'])*
</pre>

This code selects only the numeric columns (with data types float64 and int64) from the dataset, which are suitable for correlation analysis. It filters out non-numeric columns like strings or categories.

<pre>correlation_matrix = numeric_cols.corr()
print("Correlation matrix calculated:\n", correlation_matrix)</pre>

This code calculates the correlation matrix for all numeric columns in the dataset using Pearson correlation. The matrix shows how strongly each pair of numeric variables is related with values ranging from -1 (negative correlation) to +1 (positive correlation). The print statement then displays this matrix.


<pre># Plotting the correlation heatmap
print("\nPlotting the heatmap...")
plt.figure(figsize=(10, 6))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt=".2f")
plt.title("Correlation Heatmap")
plt.tight_layout()
plt.show()
print("Heatmap displayed successfully.")</pre>

This code block generates a heatmap to visualize the correlation matrix of numeric columns in the dataset. It sets the figure size and uses Seaborn’s heatmap function with annotations to display the correlation values clearly. The coolwarm color map helps distinguish between positive and negative correlations. A title is added for context, and tight_layout() ensures proper spacing of plot elements. Finally, plt.show() displays the heatmap, and a print statement confirms that it has been successfully displayed. This visual makes it easy to understand relationships between numeric features.

<p align="center">
    <img src="Screenshots/correlation.png" alt="Correlation Heatmap" width="700">
</p>

 <img width="1155" height="737" alt="image" src="https://github.com/user-attachments/assets/7dfc9cc3-9633-4ee9-9b3e-6579de39ae76" />

                                                             Fig 1.Heatmap displayed

<pre>#Top Locations by Average Rating
location_rating = dataset.groupby("Restaurant location")["Rating"].mean().sort_values(ascending=False).head(10)
plt.figure(figsize=(10,6))
sns.barplot(x=location_rating.values, y=location_rating.index, palette="viridis")
plt.title("Top 10 Restaurant Locations by Average Rating")
plt.xlabel("Average Rating")
plt.ylabel("Location")
plt.tight_layout()
plt.show()</pre>

This code finds the top 10 restaurant locations with the highest average ratings and visualizes them using a horizontal bar chart.

<p align="center">
    <img src="Screenshots/location.png" alt="Top 10 Restaurant Locations by Average Rating" width="700">
</p>

                                                            Fig 1.Top 10 Restaurant Locations



<pre>#Footfall vs Rating
plt.figure(figsize=(8,6))
sns.scatterplot(data=dataset, x='Footfall', y='Rating', hue='Parking Availability', alpha=0.5)
plt.title("Footfall vs Rating (Color = Parking Availability)")
plt.show()</pre>

The scatter plot shows the relationship between footfall and rating of restaurants.
Restaurants with parking tend to have higher footfall and slightly better ratings.
However, there's no strong linear correlation between footfall and rating.
Most data points are clustered around mid-to-high footfall and rating values.

<p align="center">
    <img src="Screenshots/Parking Availability.png" alt="Footfall vs Rating" width="700">
</p>

                                                                Fig 1.Parking Availability

<pre># Rating vs Distance from City Centre
plt.figure(figsize=(8,6))
sns.boxplot(data=dataset, x=pd.cut(dataset['Distance from city Centre'], bins=5), y='Rating')
plt.title("Rating vs Distance from City Centre")
plt.xlabel("Distance Range")
plt.ylabel("Rating")
plt.show()</pre>

The boxplot shows how restaurant ratings vary with distance from the city centre. Overall, ratings remain fairly consistent across all distance ranges. However, restaurants located closer to the city centre tend to have slightly higher median ratings and less variation. This suggests that proximity to the city centre may positively influence customer satisfaction.

<p align="center">
    <img src="Screenshots/Distance Range.png" alt="Distance Range" width="700">
</p>

                                                        Fig 1.Parking Availability


<pre># Rating by Cuisine Type (top 10)
top_cuisines = dataset['Cuisines Type'].value_counts().head(10).index
plt.figure(figsize=(10,6))
sns.boxplot(data=dataset[dataset['Cuisines Type'].isin(top_cuisines)],
 x='Cuisines Type', y='Rating')
plt.xticks(rotation=45)
plt.title("Rating Distribution by Cuisine Type (Top 10)")
plt.tight_layout()
plt.show()</pre>

This boxplot displays the distribution of ratings for the top 10 most common cuisine types in the dataset. It reveals how customer satisfaction (in terms of ratings) varies by cuisine. Some cuisine types show consistently higher median ratings, while others have more variability. This suggests that the type of cuisine offered can influence customer perceptions and overall ratings.

<p align="center">
    <img src="Screenshots/Rating Distribution by Cuisine type.png" alt="Rating Distribution by Cuisine Type" width="700">
</p>


## 2. Summarize findings with charts and narrative explanation
Summary insights (example print statements)

print("-> Restaurants near transport hubs tend to have higher success ratings.")

print("-> Higher population density correlates with greater restaurant success.")

print("->Areas with moderate competition show better average performance.")

Restaurants located near transport hubs tend to receive higher success ratings, suggesting that accessibility plays a crucial role in customer footfall. Areas with higher population density also show a strong correlation with greater restaurant success, likely due to increased demand and visibility. Interestingly, regions with moderate competition perform better on average, possibly because they benefit from shared customer traffic without being oversaturated. Additionally, the availability of parking appears to slightly enhance both customer ratings and footfall, indicating the convenience factor matters. Overall, the top-rated restaurants are generally found in well-connected zones with a steady flow of people and balanced competitive environments.

