# Climate Vulnerability Assessment

## Overview
This project aims to systematically assess climate vulnerability at the block level across India by developing a composite index based on three key dimensions: **Exposure**, **Sensitivity**, and **Adaptive Capacity**. The methodology integrates data from multiple government and public repositories, processes it through robust statistical transformations, and applies **Principal Component Analysis (PCA)** to derive vulnerability sub-indices for different climate hazards, including **floods, droughts, cyclones, and earthquakes**.

## Data Sources
The dataset combines publicly available records from:
- **India Data Portal (IDP)**
- **ISB-provided block-level datasets**
- **Government sources** such as census data, agricultural surveys, and institutional capacity reports

## Methodology
### 1. Data Preprocessing
- **Ratio Transformations**: Many raw variables (e.g., bank branches, households, crop areas) were converted into ratios to enable meaningful comparisons, such as:
  - `bank_branches_per_10k_population = total_branches / (total_population / 10000)`
  - `irrigated_fraction = irrigated_area / total_geographic_area`
- **Imputation**: Missing values were handled through a combination of government-sourced data and district-wise median imputation to ensure consistency.
- **Index Creation**: We designed new composite indices, such as the **Crop Vulnerability Index**, which integrates rainfed agriculture and crop diversity to assess agricultural risk exposure.
- **Variable Inversion**: Certain variables (e.g., travel time to major cities) were inverted so that all indicators align with a "higher is better" interpretation for easier downstream analysis.
- **Outlier Handling**: Extreme values in counts (e.g., total irrigated land, number of bank branches) were identified and scaled using a **Robust Scaler**, which normalizes data based on the median and interquartile range (IQR), reducing sensitivity to outliers.

### 2. PCA-Based Sub-Index Computation
- **Principal Component Analysis (PCA)** was applied separately to each climate hazard category (Floods, Droughts, Cyclones, Earthquakes) to extract meaningful patterns and reduce dimensionality.
- **Weighting Mechanism**: The sub-indices were constructed by multiplying principal components with their explained variance percentages and summing them to produce a composite score.

### 3. Final Vulnerability Score
- The final Climate Vulnerability Index (CVI) for each hazard is computed as:
  
  Vulnerability = (Exposure * Sensitivity) / Adaptive Capacity
  
- This allows policymakers and researchers to identify high-risk blocks that require targeted interventions.

## Future Improvements
- **Integration of Real-Time Data**: Incorporating satellite-based rainfall and soil moisture data for dynamic vulnerability assessment.
- **More Hazard Categories**: Extending the index to include heatwaves, landslides, and other climate-driven risks.
- **Machine Learning Approaches**: Exploring supervised models for validation against historical disaster impacts.

## License
This project is licensed under the MIT License. See `LICENSE` for details.
