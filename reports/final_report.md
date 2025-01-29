# Final Report

## 1. Introduction

### 1.1 Project Background

Rocket Elevator, a leading provider of elevator solutions, is committed to enhancing its operational efficiency and customer satisfaction through data-driven strategies. In the era of digital transformation, leveraging comprehensive elevator data enables Rocket Elevator to optimize maintenance schedules, predict potential issues, and ensure compliance with safety regulations. This project aims to analyze various datasets related to elevator operations, including licensing, installation, alterations, inspections, and incident reports, to derive actionable insights that support informed decision-making and strategic planning.

### 1.2 Objectives

- **Data Integration:** Merge and consolidate data from multiple sources to create a unified dataset for comprehensive analysis.
- **Data Cleaning:** Perform thorough data cleaning to ensure accuracy and reliability of the datasets.
- **Feature Engineering:** Extract and derive new features to enhance the analytical depth and model performance.
- **Exploratory Data Analysis (EDA):** Conduct EDA to uncover patterns, trends, and correlations within the data.
- **Visualization:** Generate insightful visualizations to effectively communicate findings.
- **Reporting and Presentation:** Compile findings into a concise report and develop a presentation to communicate key insights and recommendations.
- **GitHub Repository Maintenance:** Utilize the CookieCutter Data Science template to maintain project work in a private GitHub repository, ensuring reproducibility and collaboration.

## 2. Methodology

### 2.1 Data Collection

Data for this project was sourced from Rocket Elevator’s internal databases and external APIs. The primary datasets include:

- **License Dataset (`license.csv`):** Contains records of elevator licenses, including status and expiration dates.
- **Installed Dataset (`installed.json`):** Details about elevator installations, including locations and device statuses.
- **Altered Dataset (`altered.json`):** Logs of alterations made to elevators post-installation.
- **Inspection Dataset (`inspection.csv`):** Records of inspections conducted on elevators, including outcomes.
- **Incident Dataset (`incident.json`):** Reports of incidents involving elevators, providing narratives and details.

### 2.2 Data Cleaning and Preprocessing

The data cleaning process involved:

- **Handling Missing Values:** Addressed missing entries by imputing or removing incomplete records where necessary.
- **Filtering Data:** Focused on records with an **ACTIVE** license status to ensure relevance.
- **Standardizing Formats:** Ensured consistency in data formats across datasets, particularly for date fields and categorical variables.
- **Merging Datasets:** Utilized **`ElevatingDevicesNumber`** as the unique identifier to merge datasets, ensuring accurate linkage of records across different data sources.
- **Removing Duplicates:** Eliminated duplicate records to maintain data integrity.

### 2.3 Feature Engineering

New features were derived to enhance analysis capabilities:

- **Extraction of Location Details:** Parsed geographical information to facilitate location-based analyses.
- **Inspection Frequency:** Calculated the number of inspections per elevator to assess maintenance rigor.
- **Alteration Counts:** Determined the frequency of alterations to identify elevators with high modification histories.
- **Textual Data Processing:** Cleaned and processed incident narratives to generate word clouds and perform frequency analysis.

### 2.4 Data Analysis and Visualization

Exploratory Data Analysis (EDA) was conducted to uncover underlying patterns and relationships within the data. Key visualizations include:

- **Word Clouds:** Visual representations of frequently occurring terms in incident narratives.
- **Time Series Plots:** Trends in license expirations and inspection frequencies over time.
- **Histograms:** Distribution of inspection counts per elevator.
- **Crosstabs:** Relationships between alteration types and their statuses.

## 3. Analysis and Results

### 3.1 License Dataset Analysis

#### 3.1.1. Identifying a Unique Elevator Identifier

To effectively track each elevator throughout its lifecycle across multiple datasets, the **`ElevatingDevicesNumber`** was identified as the unique identifier. This variable is present in all primary datasets—**License**, **Inspection**, **Installed**, and **Altered**—ensuring consistency and facilitating seamless data merging. Verification confirmed that `ElevatingDevicesNumber` is unique within the **License** and **Installed** datasets, while it appropriately accommodates multiple records in the **Inspection** and **Altered** datasets, reflecting multiple inspections or alterations per elevator.

#### 3.1.2. Geographical Distribution of Elevators

An analysis of the **`LocationoftheElevatingDevice`** column revealed that the majority of elevators are located in the province of **Ontario (ON)**, Canada (**CA**). By extracting and standardizing the **State/Province** and **Country** information, it was confirmed that **ON, CA** is the predominant location, encompassing over 42,000 active licenses. This geographical concentration highlights the focus area for Rocket Elevator’s operational data.

*![Geographical Distribution of Elevators](../reports/figures/geographical_distribution.png)*
*Figure 1: Geographical Distribution of Active Elevator Licenses*

#### 3.1.3. Filtering Active Licenses

Focusing on operational relevance, the dataset was filtered to include only records with a **`LICENSESTATUS`** of **ACTIVE**. This filtering ensures that subsequent analyses pertain solely to currently operational elevators, excluding those that are expired, canceled, or otherwise inactive. Post-filtering, all 42,625 records maintained an **ACTIVE** status, indicating no inactive records were present in the initial dataset. See `Table 1` for evidence of inconsistencies in location data that were filtered or imputed.


*![Missing Location Data](./figures/missing_location_data.png)*
*Table 1: Examples of missing location data*


#### 3.1.4. Verifying Uniqueness Post-Filtering

Post-filtering verification confirmed that **`ElevatingDevicesNumber`** remains unique within the filtered **License** dataset. This uniqueness is crucial for maintaining data integrity and preventing ambiguities in further analyses and machine learning applications.

#### 3.1.5. License Expiry Trends

A time series analysis of **`LICENSEEXPIRYDATE`** was conducted to visualize the monthly count of license expirations. The analysis spanned from **November 2016** to **November 2017**, revealing fluctuations in expiration counts across different months. Notably, **December 2016** and **January 2017** exhibited higher expiration counts, peaking at **2,972** and **4,025** respectively. This trend analysis provides insights into renewal patterns and potential periods requiring heightened administrative attention.

*![License Expiry Trends](./figures/license_expiry_timeseries.png)*
*Figure 2: Monthly License Expirations*

#### 3.1.6. Expirations by Year-Month

A detailed table enumerating license expirations by **Year-Month** was created, displaying counts only for months with more than five expirations. This table underscores the temporal distribution of license renewals and expirations, facilitating targeted strategies for license management and forecasting future trends.

*![License Expiry Trends](./figures/expiry_table_styled.png)*
reports/figures/expiry_table_styled.png
*Table 1: License Expirations by Year-Month*

#### Key Takeaways

1. **Unique Identification:** `ElevatingDevicesNumber` serves as a reliable unique identifier across all datasets, ensuring accurate tracking and merging of elevator records.
2. **Dominant Geography:** The majority of elevators are operational in Ontario, Canada, which aligns with Rocket Elevator’s primary service region.
3. **Active Focus:** Filtering for **ACTIVE** licenses ensures that analyses remain relevant to currently operational elevators.
4. **Expiry Insights:** Monthly trends in license expirations highlight critical periods for renewal processes, aiding in proactive management and resource allocation.

#### Conclusion

The License Dataset analysis establishes a robust foundation for subsequent data integration and machine learning endeavors. By confirming the uniqueness of `ElevatingDevicesNumber` and understanding the geographical distribution and temporal trends of license expirations, Rocket Elevator is better positioned to leverage this data for predictive analytics and operational optimizations.

### 3.2 Installed Dataset Analysis

#### 3.2.1. Merging License and Installed Data

To create a comprehensive view of each elevator’s lifecycle, the **Installed** dataset (`installed.json`) was merged with the previously filtered **License** dataset containing only **ACTIVE** licenses. Utilizing **`ElevatingDevicesNumber`** as the unique identifier, an **inner join** was performed, resulting in a merged dataset of **42,625** records. This merge ensured that only elevators present in both datasets were retained, accounting for **100%** of the filtered License data and **90.82%** of the Installed data. This high overlap underscores the consistency and reliability of the unique identifier across datasets.

#### 3.2.2. Comparing Location Variables

A critical step involved comparing the location fields from both datasets: **`LocationoftheElevatingDevice`** (License) and **`Location of Device`** (Installed). Out of **42,625** merged records, **109** exhibited discrepancies between these two location fields. These mismatches were categorized into **Partial Mismatches** (74 instances), typically due to minor variations like abbreviations (e.g., "AV" vs. "AVE"), and **Complete Mismatches** (30 instances), indicating significant differences in address information. Additionally, **5** records had missing location data. Addressing these discrepancies is vital for ensuring data integrity in subsequent analyses.

#### 3.2.3. Additional Location-Based Filtering

To enhance location accuracy, further filtering was applied based on matching postal codes extracted from both location fields. This process eliminated **100** rows with non-matching postal codes, resulting in a refined dataset of **42,525** records. This stringent filtering ensures that only records with consistent geographical information are analyzed, thereby reducing potential errors in location-based insights.

#### 3.2.4. Filtering by Device Status

An additional filter was implemented to retain only elevators with a **`DeviceStatus`** of **"Active"**. This filter ensured that the analysis focused exclusively on currently operational elevators, excluding those marked as inactive or under review. Post-filtering, the dataset maintained **42,625** active records, aligning with the initial License dataset’s scope.

#### 3.2.5. Cleaning High-Cardinality Variables

The **`Device Type`** column exhibited high cardinality with numerous subcategories (e.g., "Passenger Elevator", "Freight Elevator-P", "Freight Elevator-E"). To streamline this variable for analysis and modeling, a cleaning process was undertaken to consolidate similar subcategories into broader categories:
- **Passenger Elevator:** Consolidated all variations related to passenger elevators.
- **Freight Elevator:** Merged subtypes of freight elevators.
- **Escalator** and **Dumbwaiter:** Retained as distinct categories.
- **Other Device:** Aggregated any remaining miscellaneous types.

This consolidation reduced complexity, facilitating more efficient data processing and enhancing the performance of machine learning models by minimizing the dimensionality of categorical variables.

#### Key Takeaways

1. **Robust Merging:** The successful merge of License and Installed datasets using `ElevatingDevicesNumber` ensured comprehensive coverage of active elevators.
2. **Location Integrity:** Identification and filtering of location mismatches enhanced the accuracy of geographical analyses.
3. **Operational Focus:** Filtering by `DeviceStatus` to retain only active elevators maintained the relevance of the dataset for current operational insights.
4. **Simplified Categorization:** Cleaning the high-cardinality `Device Type` variable streamlined the dataset, improving its suitability for advanced analytics and modeling.

#### Conclusion

The Installed Dataset analysis provided a detailed understanding of the operational landscape of Rocket Elevator’s installations. By meticulously merging datasets, ensuring location consistency, and simplifying categorical variables, the analysis established a solid foundation for further explorations. These steps are crucial for enabling accurate predictive analytics and informed decision-making in subsequent phases of the project.

### 3.3 Altered Dataset Analysis

#### 3.3.1. Merging License, Installed, and Altered Data

To achieve a holistic view of each elevator’s lifecycle, the **Altered** dataset (`altered.json`) was merged with the previously combined **License** and **Installed** datasets. Utilizing **`ElevatingDevicesNumber`** as the unique identifier, a **left join** was performed. This approach ensured that all records from the merged License+Installed dataset (**43,234** rows) were retained, even if there were no corresponding alteration records in the Altered dataset. The resulting **merged_altered_df** comprised **52,372** rows, indicating that **21,237** elevators had no alteration history. This comprehensive merge facilitates an integrated analysis of elevator installations and their subsequent modifications.

#### 3.3.2. Identifying Elevators with More Than Five Alterations

A critical analysis was conducted to identify elevators that underwent frequent modifications. By grouping the merged dataset by **`ElevatingDevicesNumber`** and counting the number of alteration records per elevator, **15 elevators** were identified with **more than five alterations**. These elevators accounted for **92** records in the dataset. Detailed examination of these elevators revealed patterns such as:

- **Frequent Minor Alterations:** Many alterations were categorized as **Minor B Alterations**, often concluding with statuses like “Closed” or “Passed,” indicating ongoing maintenance or incremental upgrades.
- **Consistent Contractors:** Repeated alterations were frequently associated with the same contractors, suggesting established maintenance relationships or recurring issues.
- **Geographical Concentration:** The affected elevators were predominantly located in specific regions, potentially correlating with building age, usage intensity, or local regulations.

This subset of elevators with high alteration frequencies warrants further investigation to understand the underlying causes, whether they pertain to structural issues, high usage demands, or compliance with evolving safety standards.

#### 3.3.3. Analyzing Alteration Type and Status Combinations

To comprehend the nature and outcomes of alteration requests, a **crosstab** analysis was performed between **`Alteration Type`** and **`Status of Alteration Request`**. The findings are as follows:

| Alteration Type            | Cancelled | Closed | Closed by Program | Complete | Conditionally Registered | Design Registered | On Hold | Open | Passed | Pending Follow Up | Rejected | Reopen |
|----------------------------|-----------|--------|-------------------|----------|--------------------------|-------------------|---------|------|--------|--------------------|----------|--------|
| **ED-Major Alteration**    | 40        | 0      | 29                | 9        | 237                      | 79                | 9       | 27   | 6,370  | 392                | 8        | 1      |
| **ED-Minor A Alteration**  | 188       | 0      | 71                | 13       | 668                      | 63                | 22      | 102  | 13,080 | 1,058              | 161      | 2      |
| **ED-Minor B Alteration**  | 172       | 43     | 99                | 43       | 0                        | 454               | 10      | 154  | 7,086  | 341                | 103      | 1      |

**Key Observations:**

1. **Dominance of "Passed" Status:**
   - **ED-Minor A Alterations** lead with **13,080** records marked as “Passed,” making it the most common successful alteration type.
   - **ED-Major Alterations** and **ED-Minor B Alterations** also show substantial “Passed” counts (**6,370** and **7,086** respectively), indicating effective completion of these requests.

2. **Design Registrations:**
   - **ED-Minor B Alterations** have a notably higher number of “Design Registered” statuses (**454**) compared to **ED-Minor A** (**63**) and **ED-Major** (**79**). This suggests that Minor B alterations often require additional design or planning phases.

3. **Pending Follow-Ups and Rejections:**
   - **ED-Minor A Alterations** exhibit a significant number of “Pending Follow Up” statuses (**1,058**), highlighting potential delays or ongoing reviews in the alteration process.
   - **Rejections** are minimal across all alteration types, with **161** for Minor A, **103** for Minor B, and **8** for Major Alterations, indicating a generally high approval rate for alteration requests.

4. **Cancelled and Closed Requests:**
   - A smaller proportion of requests were either “Cancelled” or “Closed,” which may reflect changes in project scope, funding reallocations, or other administrative decisions.

#### Key Takeaways

1. **Comprehensive Integration:** Merging the Altered dataset with License and Installed data created a unified framework for analyzing elevator modifications alongside their installation and licensing details.
2. **Frequent Alterations Indicators:** A small subset of elevators with more than five alterations may indicate underlying issues or high-demand usage, necessitating targeted maintenance strategies.
3. **Effectiveness of Alteration Processes:** The high number of “Passed” statuses across all alteration types reflects effective completion rates, while the presence of “Pending Follow Up” suggests areas for process improvement.
4. **Design Phase Importance:** The significant “Design Registered” count for Minor B alterations underscores the necessity of meticulous planning and design in minor modifications to ensure compliance and functionality.
5. **Minimal Rejections:** The low rejection rates across alteration types indicate strong adherence to regulatory standards and effective request submissions.

#### Conclusion

The Altered Dataset analysis provided invaluable insights into the modification history of Rocket Elevator’s installations. By merging alteration records with existing License and Installed data, a comprehensive view of each elevator’s operational and maintenance lifecycle was achieved. Key findings highlight that while the majority of alteration requests are successfully completed, a notable minority require further follow-ups or are in design phases, particularly among minor alterations. Identifying elevators with frequent alterations opens avenues for targeted investigations into potential causes, be it structural, usage-related, or procedural inefficiencies. Moving forward, integrating additional datasets such as **Inspection** records will further enrich the analysis, enabling the development of predictive models to enhance maintenance scheduling, improve compliance adherence, and optimize operational reliability.

### 3.4 Inspection Dataset Analysis

#### 3.4.1. Merging License, Installed, Altered, and Inspection Data

To achieve a comprehensive understanding of each elevator's operational lifecycle, the **Inspection** dataset (`inspection.csv`) was integrated with the previously merged **License**, **Installed**, and **Altered** datasets. Utilizing **`ElevatingDevicesNumber`** as the unique identifier, a **left join** was performed. This strategy ensured that all records from the merged License+Installed+Altered dataset (**43,234** rows) were retained, even if there were no corresponding inspection records. The resulting **`merged_inspection_df`** comprised **143,380** rows, indicating that **21,237** elevators had no associated inspection history. This extensive merge facilitates an integrated analysis of elevator installations, alterations, and their inspection histories.

#### 3.4.2. Cleaning the “Inspection Outcome” Variable

A critical aspect of data preparation involved refining the **`InspectionOutcome`** variable to streamline subsequent analyses. The initial distribution revealed a wide range of outcome categories, many of which had minimal representation. To simplify this variable:

1. **Frequency Analysis:** The frequency distribution of **`InspectionOutcome`** was assessed, identifying categories with fewer than **100** occurrences.
2. **Automated Grouping:** Instead of manually specifying which categories to merge, an automated approach was adopted. All categories falling below the defined threshold were consolidated into a single **"Other"** category.
3. **Implementation:** A function was created to map these rare categories dynamically, ensuring scalability and adaptability to potential future data variations.

Post-cleaning, the **`InspectionOutcome_Cleaned`** variable predominantly comprised common outcomes like **"Follow up"**, **"Passed"**, **"DC Follow up"**, and **"All Orders Resolved"**, with infrequent outcomes appropriately categorized under **"Other"**. This consolidation enhances the clarity of outcome analyses and reduces computational complexity.

#### 3.4.3. Calculating the Average Number of Inspections per Elevator

Understanding inspection frequency is pivotal for assessing maintenance rigor and operational reliability. To quantify this:

1. **Grouping and Counting:** The dataset was grouped by **`ElevatingDevicesNumber`**, and the number of inspection records per elevator was tallied.
2. **Metric Calculation:** The **average number of inspections per elevator** was computed, yielding a value of **3.32**.
3. **Distribution Insights:** Further analysis revealed that while the majority of elevators had between **1 to 4** inspections, a smaller subset exhibited significantly higher inspection counts, with some elevators undergoing up to **24** inspections.

This metric provides a high-level overview of inspection regularity, highlighting both standard practices and potential outliers warranting deeper investigation.

#### 3.4.4. Additional Insights: Distribution of Inspection Counts

Beyond the average, visualizing the distribution of inspections offers nuanced insights:

- **Histogram Analysis:** A histogram displayed a **skewed distribution**, with a concentration of elevators having **1 to 4** inspections and a long tail extending to higher counts.
- **Extremes Identification:** The analysis confirmed that no elevators had **zero** inspections, and the **maximum** number of inspections recorded for a single elevator was **24**.
- **Specific Counts:** Approximately **10,492** elevators had exactly **1** inspection, **8,500** had **2**, **7,500** had **3**, and **6,000** had **4** inspections. Elevators with **5 or more** inspections were markedly fewer, indicating that frequent inspections are not the norm.

*![Distribution of Number of Inspections per Elevator](../reports/figures/inspection_distribution.png)*
*Figure 3: Histogram depicting the distribution of inspection counts per elevator.*

#### Key Takeaways

1. **Comprehensive Integration:** Merging the Inspection dataset with existing License, Installed, and Altered data provided a unified framework for analyzing elevators' operational and maintenance histories.
2. **Outcome Simplification:** Cleaning the **`InspectionOutcome`** variable by grouping rare categories into **"Other"** streamlined outcome analyses, facilitating clearer insights and reducing analytical complexity.
3. **Inspection Frequency:** The average of **3.32** inspections per elevator, coupled with the distribution insights, underscores that most elevators undergo a moderate number of inspections, with few experiencing high-frequency inspections.
4. **Identification of Outliers:** Elevators with unusually high inspection counts (e.g., up to **24** inspections) may indicate underlying issues such as frequent malfunctions, compliance challenges, or high usage demands, necessitating targeted investigations.
5. **Data Quality Assurance:** The absence of duplicate keys in the merged datasets and manageable memory usage affirm the integrity and scalability of the data merging strategy.

#### Conclusion

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

### 3.5 Incident Data Analysis & Word Cloud Generation

#### 3.5.1. Data Loading and Initial Exploration

To analyze the **Incident Elevator Dataset** (`incident.json`), the dataset comprising **2,446** records across **46** columns was loaded using Pandas. Initial exploration revealed a substantial number of missing values, particularly in injury-related columns. Notably, the **"Reported occurrence narrative"** column, essential for textual analysis, had only **1** missing entry, which was subsequently addressed.

**Key Observations:**
- **Missing Values:** Most injury-related columns had **1,384** missing entries, indicating incomplete reporting or non-applicability for certain incidents.
- **Data Integrity:** The absence of duplicate keys in the **`ElevatingDevicesNumber`** column ensures reliable linkage for subsequent analyses.

#### 3.5.2. Data Cleaning

Effective text analysis necessitates thorough data cleaning to ensure accuracy and relevance. The cleaning process for the **"Reported occurrence narrative"** involved several steps:

1. **Handling Missing Values:** Missing narratives were filled with empty strings to facilitate uniform text processing.
2. **Text Normalization:**
   - **Lowercasing:** All text was converted to lowercase to maintain consistency.
   - **Punctuation Removal:** Punctuation marks were stripped to focus on meaningful words.
3. **Tokenization and Stop Words Removal:** Text was split into individual words (tokens), and common stop words (e.g., "the," "and," "is") were removed to highlight significant terms.
4. **Lemmatization:** Words were reduced to their base forms using the WordNet Lemmatizer, aiding in consolidating similar terms (e.g., "running" to "run").

The cleaned text was stored in a new column, **`cleaned_text`**, ensuring the original narratives remained unaltered for reference.

#### 3.5.3. Word Cloud Generation

A **word cloud** was generated to visualize the most frequent terms within the incident narratives, providing an intuitive overview of common themes and issues. The visualization highlighted prominent words such as:

- **Elevator**
- **Door**
- **Water**
- **Pit**
- **Injury**
- **Tripped**
- **Hit**
- **Fell**
- **Floor**
- **Got**

**Insights from the Word Cloud:**
- **Common Issues:** Terms like "elevator," "door," and "water" suggest frequent incidents related to elevator operations, door malfunctions, and water-related mishaps.
- **Safety Concerns:** Words such as "injury," "tripped," and "fell" indicate recurring safety hazards that may require targeted interventions.
- **Operational Challenges:** The presence of "pit" and "floor" points to structural or maintenance-related issues within the elevator systems.

*Figure 4: Word Cloud of Reported Occurrence Narratives*

*![Word Cloud of Reported Occurrence Narratives](../reports/figures/incident_wordcloud.png)*

#### 3.5.4. Frequency Analysis of Key Terms

To complement the visual insights from the word cloud, a frequency analysis was conducted using Python's `Counter`:

- **Top 10 Frequent Words:**
  1. **Elevator** (1,233 occurrences)
  2. **Door** (664 occurrences)
  3. **Water** (417 occurrences)
  4. **Pit** (317 occurrences)
  5. **Injury** (290 occurrences)
  6. **Tripped** (265 occurrences)
  7. **Hit** (248 occurrences)
  8. **Fell** (247 occurrences)
  9. **Floor** (239 occurrences)
  10. **Got** (234 occurrences)

**Interpretation:**
- The dominance of **"elevator"** underscores that most incidents are directly related to elevator functionality.
- **"Door"** and **"water"** suggest specific areas where elevator maintenance or operational protocols may need enhancement.
- Words like **"injury," "tripped,"** and **"fell"** highlight the critical safety aspects that necessitate immediate attention to prevent future occurrences.

#### 3.5.5. Additional Data Quality Checks

Beyond text analysis, additional data quality assessments were performed to ensure robustness:

- **Data Completeness:** Most critical columns related to incident specifics and outcomes were largely complete, with only minor missing values.
- **Consistency:** The **`ElevatingDevicesNumber`** was unique across the dataset, facilitating reliable integration with other datasets for comprehensive analyses.

#### 3.5.6. Key Takeaways

1. **Prevalence of Operational Issues:** The frequent occurrence of terms like "elevator" and "door" indicates common operational challenges that may benefit from targeted maintenance strategies.
2. **Safety Prioritization:** The high frequency of injury-related terms underscores the importance of enhancing safety measures and protocols to protect users and maintenance personnel.
3. **Maintenance Focus Areas:** Water-related incidents and structural terms like "pit" and "floor" suggest specific areas within elevator systems that may require focused maintenance or design improvements.
4. **Data-Driven Insights:** The combination of word cloud visualization and frequency analysis provides a dual approach to understanding incident narratives, facilitating both qualitative and quantitative insights.

#### 3.5.7. Conclusion

In this segment of the ETL project, the **Incident Elevator Dataset** was meticulously analyzed to extract meaningful insights through text cleaning and visualization. The generation of a word cloud, complemented by frequency analysis, illuminated prevalent themes and areas of concern within elevator incidents. These findings are instrumental in guiding maintenance priorities, enhancing safety protocols, and informing future operational strategies.

**Next Steps:**
- **Deeper Textual Analysis:** Implement more advanced natural language processing techniques, such as topic modeling, to uncover underlying themes and patterns within incident narratives.
- **Integration with Other Datasets:** Combine incident data with License, Installed, Altered, and Inspection datasets to explore correlations between operational issues and maintenance histories.
- **Predictive Analytics:** Develop predictive models to identify elevators at higher risk of incidents, enabling proactive maintenance and safety interventions.
- **Reporting Enhancements:** Create dashboards and automated reports to continuously monitor incident trends and facilitate real-time decision-making for operational teams.

By leveraging data-driven methodologies, Rocket Elevator can significantly enhance its operational reliability, safety standards, and customer satisfaction through informed and strategic interventions.

## 4. Discussion

### 4.1 Key Insights

The comprehensive analysis of the License, Installed, Altered, Inspection, and Incident datasets has unveiled several critical insights:

- **Unique Identification:** The **`ElevatingDevicesNumber`** effectively serves as a unique identifier across all datasets, ensuring accurate data merging and integrity.
- **Geographical Concentration:** A significant majority of elevators are operational in Ontario, Canada, aligning with Rocket Elevator’s primary service region.
- **License Expiration Trends:** License expirations peak during specific months, indicating periods that may require intensified administrative efforts for renewals.
- **Alteration Patterns:** A small subset of elevators undergo frequent alterations, suggesting potential issues or high-demand usage that necessitate targeted maintenance strategies.
- **Inspection Frequency:** On average, elevators undergo approximately **3.32** inspections, with a majority falling within the **1 to 4** inspections range, reflecting a balanced maintenance regimen.
- **Incident Hotspots:** Word cloud and frequency analysis of incident narratives highlight prevalent operational and safety challenges, emphasizing areas for improvement.

### 4.2 Implications for Rocket Elevator

These insights hold significant implications for Rocket Elevator’s operations:

- **Maintenance Optimization:** Understanding inspection frequencies and alteration patterns allows for optimized maintenance scheduling, reducing downtime and enhancing elevator reliability.
- **Resource Allocation:** Identifying peak license expiration periods and high-frequency alteration elevators enables strategic allocation of administrative and maintenance resources.
- **Safety Enhancements:** Insights from incident analyses inform the development of targeted safety protocols, minimizing injury risks and improving user safety.
- **Predictive Maintenance:** Leveraging integrated data facilitates the creation of predictive models to foresee maintenance needs, enabling proactive interventions.
- **Geographical Strategy:** Concentration of elevators in Ontario suggests focusing regional strategies and resources to support the largest operational hubs effectively.

## 5. Recommendations

Based on the analysis, the following recommendations are proposed to enhance Rocket Elevator’s operational efficiency and safety standards:

1. **Data Integration:**
   - Continue integrating diverse data sources to maintain a comprehensive and up-to-date dataset, facilitating deeper analyses and more accurate predictive models.
  
2. **Predictive Modeling:**
   - Develop machine learning models to predict inspection outcomes and maintenance needs, enabling proactive maintenance scheduling and resource allocation.
  
3. **Process Optimization:**
   - Analyze the causes behind "Pending Follow Up" statuses in alteration requests to streamline the approval process and reduce administrative delays.
  
4. **Targeted Maintenance Strategies:**
   - Investigate elevators with frequent alterations or high inspection counts to identify underlying issues and implement targeted maintenance or upgrades.
  
5. **Safety Protocol Enhancements:**
   - Utilize insights from incident analyses to develop and implement enhanced safety protocols, reducing injury risks and ensuring compliance with safety regulations.
  
6. **Resource Allocation:**
   - Allocate resources strategically during peak license expiration periods to ensure timely renewals and maintain operational continuity.
  
7. **Stakeholder Engagement:**
   - Enhance communication with stakeholders using data-driven insights, fostering transparency and informed decision-making across the organization.
  
8. **Continuous Monitoring:**
   - Implement real-time dashboards to monitor key metrics such as license expirations, inspection frequencies, and incident trends, facilitating timely interventions and strategic planning.

## 6. Conclusion

This project successfully integrated and analyzed multiple datasets related to Rocket Elevator’s operations, including licensing, installation, alterations, inspections, and incidents. By establishing **`ElevatingDevicesNumber`** as a unique identifier, we ensured accurate data merging and integrity across datasets. The analyses unveiled key insights into geographical distributions, license expiration trends, alteration patterns, inspection frequencies, and incident hotspots.

The findings highlight areas for operational improvements, such as optimizing maintenance schedules, enhancing safety protocols, and implementing predictive maintenance models. These insights empower Rocket Elevator to make informed, data-driven decisions that enhance operational efficiency, safety standards, and customer satisfaction.

Through strategic data integration and comprehensive analysis, Rocket Elevator is well-positioned to leverage its elevator data for sustained operational excellence and competitive advantage in the industry.

## 7. References

- **Datasets:**
  - License Dataset: `license.csv`
  - Installed Dataset: `installed.json`
  - Altered Dataset: `altered.json`
  - Inspection Dataset: `inspection.csv`
  - Incident Dataset: `incident.json`
  
- **Tools and Libraries:**
  - Python (Pandas, NLTK, WordCloud, Matplotlib)
  - MkDocs for documentation
  - CookieCutter Data Science Template for project structuring
  
- **Documentation:**
  - Project documentation files located in the `docs/` directory
  - Visualizations saved in `reports/figures/`
  
- **GitHub Repository:**
  - [AIC-103_Data_Science_Project](https://github.com/Gamikaru/AIC-103_Data_Science_Project)

---

**Note:** The placeholders for images and figures (e.g., *Figure 1*, *Figure 2*) should be replaced with actual image links corresponding to the generated visualizations saved in the `reports/figures/` directory. Ensure that these images are properly referenced and accessible within the report.