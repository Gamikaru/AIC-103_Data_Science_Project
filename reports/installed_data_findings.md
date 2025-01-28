

## 3.2. Installed Dataset Analysis

### 3.2.1. Merging License and Installed Data

To create a comprehensive view of each elevator’s lifecycle, the **Installed** dataset (`installed.json`) was merged with the previously filtered **License** dataset containing only **ACTIVE** licenses. Utilizing **`ElevatingDevicesNumber`** as the unique identifier, an **inner join** was performed, resulting in a merged dataset of **42,625** records. This merge ensured that only elevators present in both datasets were retained, accounting for **100%** of the filtered License data and **90.82%** of the Installed data. This high overlap underscores the consistency and reliability of the unique identifier across datasets.

### 3.2.2. Comparing Location Variables

A critical step involved comparing the location fields from both datasets: **`LocationoftheElevatingDevice`** (License) and **`Location of Device`** (Installed). Out of **42,625** merged records, **109** exhibited discrepancies between these two location fields. These mismatches were categorized into **Partial Mismatches** (74 instances), typically due to minor variations like abbreviations (e.g., "AV" vs. "AVE"), and **Complete Mismatches** (30 instances), indicating significant differences in address information. Additionally, **5** records had missing location data. Addressing these discrepancies is vital for ensuring data integrity in subsequent analyses.

### 3.2.3. Additional Location-Based Filtering

To enhance location accuracy, further filtering was applied based on matching postal codes extracted from both location fields. This process eliminated **100** rows with non-matching postal codes, resulting in a refined dataset of **42,525** records. This stringent filtering ensures that only records with consistent geographical information are analyzed, thereby reducing potential errors in location-based insights.

### 3.2.4. Filtering by Device Status

An additional filter was implemented to retain only elevators with a **`DeviceStatus`** of **"Active"**. This filter ensured that the analysis focused exclusively on currently operational elevators, excluding those marked as inactive or under review. Post-filtering, the dataset maintained **42,625** active records, aligning with the initial License dataset’s scope.

### 3.2.5. Cleaning High-Cardinality Variables

The **`Device Type`** column exhibited high cardinality with numerous subcategories (e.g., "Passenger Elevator", "Freight Elevator-P", "Freight Elevator-E"). To streamline this variable for analysis and modeling, a cleaning process was undertaken to consolidate similar subcategories into broader categories:
- **Passenger Elevator**: Consolidated all variations related to passenger elevators.
- **Freight Elevator**: Merged subtypes of freight elevators.
- **Escalator** and **Dumbwaiter**: Retained as distinct categories.
- **Other Device**: Aggregated any remaining miscellaneous types.

This consolidation reduced complexity, facilitating more efficient data processing and enhancing the performance of machine learning models by minimizing the dimensionality of categorical variables.

### Key Takeaways

1. **Robust Merging:** The successful merge of License and Installed datasets using `ElevatingDevicesNumber` ensured comprehensive coverage of active elevators.
2. **Location Integrity:** Identification and filtering of location mismatches enhanced the accuracy of geographical analyses.
3. **Operational Focus:** Filtering by `DeviceStatus` to retain only active elevators maintained the relevance of the dataset for current operational insights.
4. **Simplified Categorization:** Cleaning the high-cardinality `Device Type` variable streamlined the dataset, improving its suitability for advanced analytics and modeling.

### Conclusion

The Installed Dataset analysis provided a detailed understanding of the operational landscape of Rocket Elevator’s installations. By meticulously merging datasets, ensuring location consistency, and simplifying categorical variables, the analysis established a solid foundation for further explorations. These steps are crucial for enabling accurate predictive analytics and informed decision-making in subsequent phases of the project.

---
