# GSA_Property_Analysis
This project analyzes the **Inventory of Owned and Leased Properties (IOLP)** dataset, which contains information about properties owned or leased by the **General Services Administration (GSA)**. Properties are located across the United States, Puerto Rico, Guam, and American Samoa. 

The goal is to understand how government buildings and spaces are used, whether they are owned or rented, and explore their location, size, and condition.

---

## Dataset Details

- **Source:** General Services Administration (GSA)
- **Size:** 7,588 rows and 19 columns
- **Format:** CSV, with both numerical and categorical data
- **Key Features:**
  - Location Code, Real Property Asset Name, Installation Name
  - Owned or Leased, GSA Region
  - Address, Longitude, Latitude
  - Rentable and Available Square Feet
  - Construction Date, Congressional District
  - Lease Number, Lease Effective & Expiration Dates
  - Real Property Asset Type, Building Status (Owned Only)

---

## Data Preprocessing & Transformation

1. **Handling Missing Values:**  
   - Dropped `Installation Name` due to 99.37% missing values.

2. **Outlier Detection:**  
   - Applied **IQR method** to identify outliers in numerical columns.

3. **Geospatial Transformation:**  
   - Combined `Longitude` & `Latitude` to create a geometry column using **Shapely Points**.  
   - Converted DataFrame to **GeoDataFrame** using **GeoPandas**.

4. **Skewness Analysis:**  
   - Identified numerical columns with absolute skewness ≥ 0.6 for potential normalization.

5. **Encoding Categorical Variables:**  
   - **Frequency Encoding:** High-cardinality columns (e.g., Location Code, Real Property Asset Name, City, Lease Number).  
   - **One-Hot Encoding:** Low-cardinality, non-ordinal columns (e.g., State, Real Property Asset Type).

6. **Date Feature Engineering:**  
   - Converted lease dates to datetime format.  
   - Extracted Year, Month, Day features and calculated **Leasing Duration**.

7. **Handling Negative/Zero Values:**  
   - Shifted Rentable and Available Square Feet to positive values.

8. **Normalization & Scaling:**  
   - Applied log transformation to Rentable & Available Square Feet.  
   - Scaled values using **MinMaxScaler** to [0,1].

---

## Exploratory Data Analysis (EDA)

- **Interactive Map:**  
  - Visualizes properties across the U.S., color-coded by state.
- **Heatmap of Rentable Square Feet:**  
  - Shows regions with largest properties (e.g., Texas, California, Northeast).  
- **State-Wise Property Distribution:**  
  - Highest concentration in CA, TX, FL.  
- **City-Wise Distribution in California:**  
  - Dominance in San Diego, San Francisco, Sacramento, and Fresno.  
- **Rentable vs Available Space:**  
  - Bubble size represents rentable space, color shows utilization rate.  
- **Lease Trends Over Time:**  
  - Increase in lease starts after 2000; peak expirations around 2025.  
- **Asset Type Distribution:**  
  - Majority are **buildings**, fewer land and structures.  
- **Advanced Analysis:**  
  - Properties within 10km of San Diego.  
  - DBSCAN clustering for spatial patterns.  
  - Integration with population estimates for city-level insights.

---

## Key Insights

- Federal properties are concentrated in major urban and coastal areas.  
- Large buildings tend to have higher utilization rates.  
- Lease start trends indicate increasing demand after 2000.  
- California, Texas, and Florida dominate in property counts.  
- Clustering reveals spatial patterns useful for investment and strategic planning.

---
## Website link : https://sykang16.github.io/
