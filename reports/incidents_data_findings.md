

## 3.5. Incident Data Analysis & Word Cloud Generation

### 3.5.1. Data Loading and Initial Exploration

To analyze the **Incident Elevator Dataset** (`incident.json`), the dataset comprising **2,446** records across **46** columns was loaded using Pandas. Initial exploration revealed a substantial number of missing values, particularly in injury-related columns. Notably, the **"Reported occurrence narrative"** column, essential for textual analysis, had only **1** missing entry, which was subsequently addressed.

**Key Observations:**
- **Missing Values:** Most injury-related columns had **1,384** missing entries, indicating incomplete reporting or non-applicability for certain incidents.
- **Data Integrity:** The absence of duplicate keys in the **`ElevatingDevicesNumber`** column ensures reliable linkage for subsequent analyses.

### 3.5.2. Data Cleaning

Effective text analysis necessitates thorough data cleaning to ensure accuracy and relevance. The cleaning process for the **"Reported occurrence narrative"** involved several steps:

1. **Handling Missing Values:** Missing narratives were filled with empty strings to facilitate uniform text processing.
2. **Text Normalization:**
   - **Lowercasing:** All text was converted to lowercase to maintain consistency.
   - **Punctuation Removal:** Punctuation marks were stripped to focus on meaningful words.
3. **Tokenization and Stop Words Removal:** Text was split into individual words (tokens), and common stop words (e.g., "the," "and," "is") were removed to highlight significant terms.
4. **Lemmatization:** Words were reduced to their base forms using the WordNet Lemmatizer, aiding in consolidating similar terms (e.g., "running" to "run").

The cleaned text was stored in a new column, **`cleaned_text`**, ensuring the original narratives remained unaltered for reference.

### 3.5.3. Word Cloud Generation

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

*Figure 1: Word Cloud of Reported Occurrence Narratives*

![Word Cloud of Reported Occurrence Narratives](../reports/figures/incident_wordcloud.png)

### 3.5.4. Frequency Analysis of Key Terms

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

### 3.5.5. Additional Data Quality Checks

Beyond text analysis, additional data quality assessments were performed to ensure robustness:

- **Data Completeness:** Most critical columns related to incident specifics and outcomes were largely complete, with only minor missing values.
- **Consistency:** The **`ElevatingDevicesNumber`** was unique across the dataset, facilitating reliable integration with other datasets for comprehensive analyses.

### 3.5.6. Key Takeaways

1. **Prevalence of Operational Issues:** The frequent occurrence of terms like "elevator" and "door" indicates common operational challenges that may benefit from targeted maintenance strategies.
2. **Safety Prioritization:** The high frequency of injury-related terms underscores the importance of enhancing safety measures and protocols to protect users and maintenance personnel.
3. **Maintenance Focus Areas:** Water-related incidents and structural terms like "pit" and "floor" suggest specific areas within elevator systems that may require focused maintenance or design improvements.
4. **Data-Driven Insights:** The combination of word cloud visualization and frequency analysis provides a dual approach to understanding incident narratives, facilitating both qualitative and quantitative insights.

### 3.5.7. Conclusion

In this segment of the ETL project, the **Incident Elevator Dataset** was meticulously analyzed to extract meaningful insights through text cleaning and visualization. The generation of a word cloud, complemented by frequency analysis, illuminated prevalent themes and areas of concern within elevator incidents. These findings are instrumental in guiding maintenance priorities, enhancing safety protocols, and informing future operational strategies.

**Next Steps:**
- **Deeper Textual Analysis:** Implement more advanced natural language processing techniques, such as topic modeling, to uncover underlying themes and patterns within incident narratives.
- **Integration with Other Datasets:** Combine incident data with License, Installed, Altered, and Inspection datasets to explore correlations between operational issues and maintenance histories.
- **Predictive Analytics:** Develop predictive models to identify elevators at higher risk of incidents, enabling proactive maintenance and safety interventions.
- **Reporting Enhancements:** Create dashboards and automated reports to continuously monitor incident trends and facilitate real-time decision-making for operational teams.

By leveraging data-driven methodologies, Rocket Elevator can significantly enhance its operational reliability, safety standards, and customer satisfaction through informed and strategic interventions.

