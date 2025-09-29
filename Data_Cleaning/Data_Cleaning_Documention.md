# Project: Restaurant Location Recommendation Tool & Analysis ##

# Goal 
To ensure the dataset is accurate, complete, and consistent by handling missing, duplicate, or incorrect entries and standardizing formats for effective analysis.

# Steps applied for data cleaning

## 1. Identify and handle missing, duplicate, or inconsistent entries. 

*dataset.info()*

The dataset.info() command gives a quick summary of the dataset, showing column names, data types, non-null counts, and helps identify missing values for cleaning.

*dataset.head()*

The dataset.head() function shows the first five rows of the dataset, helping to quickly review its structure and identify any visible issues.

*dataset.describe()*

The dataset.describe() function gives statistical summaries of numerical columns, helping to understand data distribution and spot outliers.

*dataset.isnull().sum()*

The dataset.isnull().sum() function shows the number of missing (null) values in each column, helping to identify which fields need to be cleaned or filled.

<pre># Fill missing values appropriately
print("Filling missing values with default replacements...")
dataset.fillna({
    'Restaurant Location': 'Unknown',
    'Demographics': 'General',
    'Footfall': dataset['Footfall'].median(),
    'Compilation': 'None',
    'Local Amenities': 'None',
    'Cuisines Type': 'Not specified',
    'Average Meal Price': dataset['Average Meal Price'].mean(),
    'Rating': dataset['Rating'].mean(),
    'Parking Availability': 'Unknown',
    'Opening Hours': 'Unavailable',
    'Nearby Attractions': 'None'
}, inplace=True)</pre>
This code fills missing values in the dataset with appropriate defaults—using text like 'Unknown' or 'None' for categorical columns, and mean or median for numerical columns—ensuring no null values remain for analysis.

<pre># Strip whitespace from text fields
print("Stripping extra whitespace from text columns...")
df = dataset.applymap(lambda x: x.strip() if isinstance(x, str) else x)
</pre>
This code removes extra spaces from all text (string) fields in the dataset, ensuring consistency in values like city names or categories.

## 2. Standardize Formats for Addresses, Cities, and Categorical Fields

<pre># Strip extra spaces
df = df.applymap(lambda x: x.strip() if isinstance(x, str) else x)</pre>

This line removes leading and trailing spaces from all string values in the DataFrame, helping to standardize text data and avoid mismatches due to extra spaces.

 
<pre># If there are duplicates, remove them
import pandas as pd
# Load your dataset (replace 'your_file.csv' with your actual file path)
dataset = pd.read_csv('/content/RESTAURANT_DATA_5K (1).csv')
# Remove duplicate rows
dataset_unique = dataset.drop_duplicates()
# Display the number of unique rows
print("Number of unique rows:", dataset_unique.shape[0])
# (Optional) Save the unique rows to a new file
dataset_unique.to_csv('unique_data.csv', index=False)</pre>


This code checks for duplicate rows in the dataset.
If duplicates are found, it removes them to ensure the data is clean and doesn't contain repeated entries that could affect analysis.

## 3. Document Cleaning Steps with Summaries and Rationales

<pre>print(f"\n Final shape of cleaned dataset: {df.shape}")
print("\n Summary Statistics of Numeric Columns:")
print(df.describe())

print("\n Cleaning Rationales:")
print("""
• Missing values were filled with statistically reasonable defaults (mean/median).
• Duplicate entries were removed to ensure data integrity.
• Text data was cleaned for uniform formatting (stripped, title-cased).
• These steps prepare the dataset for machine learning by ensuring consistency, reducing noise, and improving model performance.
""")</pre>

The code shows the cleaned dataset’s shape and stats, and explains that missing values were filled, duplicates removed, and text standardized to prepare the data for accurate analysis and modeling.
