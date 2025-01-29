

## 3.1. License Dataset Analysis

### 3.1.1. Identifying a Unique Elevator Identifier

To effectively track each elevator throughout its lifecycle across multiple datasets, the **`ElevatingDevicesNumber`** was identified as the unique identifier. This variable is present in all primary datasets—**License**, **Inspection**, **Installed**, and **Altered**—ensuring consistency and facilitating seamless data merging. Verification confirmed that `ElevatingDevicesNumber` is unique within the **License** and **Installed** datasets, while it appropriately accommodates multiple records in the **Inspection** and **Altered** datasets, reflecting multiple inspections or alterations per elevator.

### 3.1.2. Geographical Distribution of Elevators

An analysis of the **`LocationoftheElevatingDevice`** column revealed that the majority of elevators are located in the province of **Ontario (ON)**, Canada (**CA**). By extracting and standardizing the **State/Province** and **Country** information, it was confirmed that **ON, CA** is the predominant location, encompassing over 42,000 active licenses. This geographical concentration highlights the focus area for Rocket Elevator’s operational data.

### 3.1.3. Filtering Active Licenses

Focusing on operational relevance, the dataset was filtered to include only records with a **`LICENSESTATUS`** of **ACTIVE**. This filtering ensures that subsequent analyses pertain solely to currently operational elevators, excluding those that are expired, canceled, or otherwise inactive. Post-filtering, all 42,625 records maintained an **ACTIVE** status, indicating no inactive records were present in the initial dataset.

### 3.1.4. Verifying Uniqueness Post-Filtering

Post-filtering verification confirmed that **`ElevatingDevicesNumber`** remains unique within the filtered **License** dataset. This uniqueness is crucial for maintaining data integrity and preventing ambiguities in further analyses and machine learning applications.

### 3.1.5. License Expiry Trends

A time series analysis of **`LICENSEEXPIRYDATE`** was conducted to visualize the monthly count of license expirations. The analysis spanned from **November 2016** to **November 2017**, revealing fluctuations in expiration counts across different months. Notably, **December 2016** and **January 2017** exhibited higher expiration counts, peaking at **2,972** and **4,025** respectively. This trend analysis provides insights into renewal patterns and potential periods requiring heightened administrative attention.

### 3.1.6. Expirations by Year-Month

A detailed table enumerating license expirations by **Year-Month** was created, displaying counts only for months with more than five expirations. This table underscores the temporal distribution of license renewals and expirations, facilitating targeted strategies for license management and forecasting future trends.

### Key Takeaways

1. **Unique Identification:** `ElevatingDevicesNumber` serves as a reliable unique identifier across all datasets, ensuring accurate tracking and merging of elevator records.
2. **Dominant Geography:** The majority of elevators are operational in Ontario, Canada, which aligns with Rocket Elevator’s primary service region.
3. **Active Focus:** Filtering for **ACTIVE** licenses ensures that analyses remain relevant to currently operational elevators.
4. **Expiry Insights:** Monthly trends in license expirations highlight critical periods for renewal processes, aiding in proactive management and resource allocation.

### Conclusion

The License Dataset analysis establishes a robust foundation for subsequent data integration and machine learning endeavors. By confirming the uniqueness of `ElevatingDevicesNumber` and understanding the geographical distribution and temporal trends of license expirations, Rocket Elevator is better positioned to leverage this data for predictive analytics and operational optimizations.

---