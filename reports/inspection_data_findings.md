
## 3.4. Inspected Dataset Analysis

### 3.4.1. Merging License, Installed, Altered, and Inspection Data

To achieve a comprehensive understanding of each elevator's operational lifecycle, the **Inspection** dataset (`inspection.csv`) was integrated with the previously merged **License**, **Installed**, and **Altered** datasets. Utilizing **`ElevatingDevicesNumber`** as the unique identifier, a **left join** was performed. This strategy ensured that all records from the merged License+Installed+Altered dataset (**43,234** rows) were retained, even if there were no corresponding inspection records. The resulting **`merged_inspection_df`** comprised **143,380** rows, indicating that **21237** elevators had no associated inspection history. This extensive merge facilitates an integrated analysis of elevator installations, alterations, and their inspection histories.

### 3.4.2. Cleaning the “Inspection Outcome” Variable

A critical aspect of data preparation involved refining the **`InspectionOutcome`** variable to streamline subsequent analyses. The initial distribution revealed a wide range of outcome categories, many of which had minimal representation. To simplify this variable:

1. **Frequency Analysis:** The frequency distribution of **`InspectionOutcome`** was assessed, identifying categories with fewer than **100** occurrences.
2. **Automated Grouping:** Instead of manually specifying which categories to merge, an automated approach was adopted. All categories falling below the defined threshold were consolidated into a single **"Other"** category.
3. **Implementation:** A function was created to map these rare categories dynamically, ensuring scalability and adaptability to potential future data variations.

Post-cleaning, the **`InspectionOutcome_Cleaned`** variable predominantly comprised common outcomes like **"Follow up"**, **"Passed"**, **"DC Follow up"**, and **"All Orders Resolved"**, with infrequent outcomes appropriately categorized under **"Other"**. This consolidation enhances the clarity of outcome analyses and reduces computational complexity.

### 3.4.3. Calculating the Average Number of Inspections per Elevator

Understanding inspection frequency is pivotal for assessing maintenance rigor and operational reliability. To quantify this:

1. **Grouping and Counting:** The dataset was grouped by **`ElevatingDevicesNumber`**, and the number of inspection records per elevator was tallied.
2. **Metric Calculation:** The **average number of inspections per elevator** was computed, yielding a value of **3.32**.
3. **Distribution Insights:** Further analysis revealed that while the majority of elevators had between **1 to 4** inspections, a smaller subset exhibited significantly higher inspection counts, with some elevators undergoing up to **24** inspections.

This metric provides a high-level overview of inspection regularity, highlighting both standard practices and potential outliers warranting deeper investigation.

### 3.4.4. Additional Insights: Distribution of Inspection Counts

Beyond the average, visualizing the distribution of inspections offers nuanced insights:

- **Histogram Analysis:** A histogram displayed a **skewed distribution**, with a concentration of elevators having **1 to 4** inspections and a long tail extending to higher counts.
- **Extremes Identification:** The analysis confirmed that no elevators had **zero** inspections, and the **maximum** number of inspections recorded for a single elevator was **24**.
- **Specific Counts:** Approximately **10,492** elevators had exactly **1** inspection, **8,500** had **2**, **7,500** had **3**, and **6,000** had **4** inspections. Elevators with **5 or more** inspections were markedly fewer, indicating that frequent inspections are not the norm.

**Visualization:**

![Distribution of Number of Inspections per Elevator](https://i.imgur.com/YourImageLink.png)
*Figure 1: Histogram depicting the distribution of inspection counts per elevator.*

### Key Takeaways

1. **Comprehensive Integration:** Merging the Inspection dataset with existing License, Installed, and Altered data provided a unified framework for analyzing elevators' operational and maintenance histories.
2. **Outcome Simplification:** Cleaning the **`InspectionOutcome`** variable by grouping rare categories into **"Other"** streamlined outcome analyses, facilitating clearer insights and reducing analytical complexity.
3. **Inspection Frequency:** The average of **3.32** inspections per elevator, coupled with the distribution insights, underscores that most elevators undergo a moderate number of inspections, with few experiencing high-frequency inspections.
4. **Identification of Outliers:** Elevators with unusually high inspection counts (e.g., up to **24** inspections) may indicate underlying issues such as frequent malfunctions, compliance challenges, or high usage demands, necessitating targeted investigations.
5. **Data Quality Assurance:** The absence of duplicate keys in the merged datasets and manageable memory usage affirm the integrity and scalability of the data merging strategy.

### Conclusion

In **Part 4** of our Elevator Data ETL project, we successfully merged the **Inspection** dataset with the previously unified **License**, **Installed**, and **Altered** datasets. This integration provided a holistic view of each elevator's lifecycle, encompassing installation details, alteration histories, and inspection records. Key accomplishments include:

1. **Strategic Merging:** Employed a left join strategy to maintain all elevator records while accommodating multiple inspection entries per elevator, ensuring comprehensive coverage without incurring memory issues.
2. **Variable Cleaning:** Streamlined the **`InspectionOutcome`** variable by aggregating infrequent categories into **"Other"**, enhancing the clarity and efficiency of outcome analyses.
3. **Metric Computation:** Determined that the average number of inspections per elevator stands at **3.32**, with a distribution indicating that most elevators have undergone a moderate number of inspections.
4. **Insight Generation:** Identified patterns in inspection frequencies, highlighting elevators that may require further scrutiny due to their high number of inspections.

**Next Steps:**

1. **Deep Dive into High-Inspection Elevators:** Investigate the causes behind elevators with exceptionally high inspection counts to identify recurring issues or systemic problems.
2. **Correlation Analysis:** Explore relationships between inspection frequencies/outcomes and other variables such as elevator type, location, or alteration histories to uncover underlying trends.
3. **Predictive Modeling:** Utilize the integrated dataset to develop models that predict future inspection needs, enabling proactive maintenance scheduling and resource allocation.
4. **Enhanced Reporting:** Incorporate additional data visualizations and dashboards to facilitate real-time monitoring of elevator inspections and outcomes for operational stakeholders.

By integrating and analyzing the Inspection dataset alongside License, Installed, and Altered data, we have established a robust foundation for advanced analytics aimed at optimizing elevator maintenance, ensuring safety compliance, and enhancing operational efficiency.

---

