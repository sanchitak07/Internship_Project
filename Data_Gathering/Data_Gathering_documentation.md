# Project: Restaurant Location Recommendation Tool & Analysis ##

# Goal
To obtain or generate a dataset that accurately represents restaurant locations in Indian cities, including factors like demographics, footfall, competition, and local amenities — enabling realistic analysis and decision-making for restaurant business planning and location optimization.

# Objective
The objective of this step is to develop or obtain a dataset that reflects the restaurant landscape in Indian cities. Since public datasets often lack details like local footfall, competition levels, and neighborhood amenities, we created a synthetic dataset inspired by real-world patterns. This dataset is designed to support location-based recommendation systems, performance prediction, and spatial business analysis.

# Dataset Overview
The Indian Restaurant Dataset – RESTAURANT_DATA_3K consists of over 3,000 entries detailing restaurant information across major Indian cities such as Mumbai, Delhi, Bengaluru, and Chennai. Each entry includes attributes like restaurant name, city, address, cuisine types, average cost for two, user ratings, number of votes, and availability of services like online delivery or table booking. The dataset also includes geolocation data (latitude and longitude), enabling spatial analysis and mapping. Designed for restaurant analysis, recommendation systems, and location-based modeling, it offers structured data suitable for machine learning and business intelligence projects. While it lacks time-based data and actual sales or footfall figures, it provides a rich foundation for understanding restaurant characteristics and customer preferences across diverse urban regions in India.

# Key Attributes Included:
Restaurant_Name: The name of the restaurant
City: Indian city where the restaurant is located (e.g., Mumbai, Delhi, Bangalore)
Location: Specific neighborhood or area within the city
Cuisine_Type: Type of food served (e.g., North Indian, Chinese, Mughlai)
Rating: Average customer rating (1.0 to 5.0 scale)
Price_Range: Price category (Low, Medium, High)
Delivery_Option: Whether the restaurant offers delivery (Yes/No)
Online_Ordering: Availability of online ordering (Yes/No)
Votes: Number of customer reviews or ratings
Footfall: Estimated customer footfall per month
Competition_Level: Number of similar restaurants in a 1 km radius
Amenities_Nearby: Presence of nearby amenities (malls, colleges, offices)
Opening_Hours: Hours of operation (e.g., 10 AM – 11 PM)

# Approach to Data Generation
Due to the lack of a comprehensive open-source dataset that captures Indian restaurant dynamics, a synthetic dataset was built using structured rules and assumptions based on actual food service industry trends in India.

# Considerations
City Size and Type: Mix of Tier-1 (e.g., Mumbai, Delhi) and Tier-2 (e.g., Nagpur, Jaipur) cities
Cuisine Distribution: Based on Zomato/Swiggy trends in urban areas
Ratings & Votes: Simulated using a normal distribution and Poisson distribution respectively
Footfall: Modeled based on city population, neighborhood type, and restaurant type
Competition_Level: Estimated number of similar cuisine outlets nearby
Amenities: Simulated presence of high-traffic generators (malls, colleges, tech parks)
Weekday vs Weekend: Implicit trends simulated by varying footfall and votes

# Methodology
Cuisine_Type: Sampled from top 10 cuisines found across Indian food delivery platforms.
Rating: Normally distributed around 3.5 with standard deviation to reflect review variability.
Price_Range: Categorized based on restaurant type and inferred footfall.
Footfall & Competition_Level: Simulated using a scaled random range influenced by city tier and neighborhood.
Votes: Poisson-distributed to reflect typical user review behavior.
Delivery/Ordering Flags: Set with higher probability in metro cities.

# Why Synthetic Data?
No open dataset combines all relevant variables like competition, footfall, and amenities.
Indian restaurant data from APIs (e.g., Zomato) is often restricted or incomplete.
Synthetic data offers flexibility and realism based on:
Real-world listings and user reviews
Indian metro and Tier-2 city structures
Varying consumer and food trends

# Summary
This synthetic restaurant dataset was generated to reflect Indian urban dining ecosystems realistically and flexibly. It serves as a strong foundation for:
Spatial analysis of restaurant success
Location-based recommendations
Performance forecasting
Urban planning insights
The inclusion of contextual factors like footfall, competition, and delivery services makes this dataset suitable for training machine learning models and running business intelligence simulations.












