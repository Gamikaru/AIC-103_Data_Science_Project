## 3.3. Altered Dataset Analysis

### 3.3.1. Merging License, Installed, and Altered Data

To achieve a holistic view of each elevator’s lifecycle, the **Altered** dataset (`altered.json`) was merged with the previously combined **License** and **Installed** datasets. Utilizing **`ElevatingDevicesNumber`** as the unique identifier, a **left join** was performed. This approach ensured that all records from the merged License+Installed dataset (**43,234** rows) were retained, even if there were no corresponding alteration records in the Altered dataset. The resulting **merged_altered_df** comprised **52,372** rows, indicating that **21,237** elevators had no alteration history. This comprehensive merge facilitates an integrated analysis of elevator installations and their subsequent modifications.

### 3.3.2. Identifying Elevators with More Than Five Alterations

A critical analysis was conducted to identify elevators that underwent frequent modifications. By grouping the merged dataset by **`ElevatingDevicesNumber`** and counting the number of alteration records per elevator, **15 elevators** were identified with **more than five alterations**. These elevators accounted for **92** records in the dataset. Detailed examination of these elevators revealed patterns such as:

- **Frequent Minor Alterations:** Many alterations were categorized as **Minor B Alterations**, often concluding with statuses like “Closed” or “Passed,” indicating ongoing maintenance or incremental upgrades.
- **Consistent Contractors:** Repeated alterations were frequently associated with the same contractors, suggesting established maintenance relationships or recurring issues.
- **Geographical Concentration:** The affected elevators were predominantly located in specific regions, potentially correlating with building age, usage intensity, or local regulations.

This subset of elevators with high alteration frequencies warrants further investigation to understand the underlying causes, whether they pertain to structural issues, high usage demands, or compliance with evolving safety standards.

### 3.3.3. Analyzing Alteration Type and Status Combinations

To comprehend the nature and outcomes of alteration requests, a **crosstab** analysis was performed between **`Alteration Type`** and **`Status of Alteration Request`**. The findings are as follows:

| Alteration Type          | Cancelled | Closed | Closed by Program | Complete | Conditionally Registered | Design Registered | On Hold | Open | Passed | Pending Follow Up | Rejected | Reopen |
|--------------------------|-----------|--------|-------------------|----------|--------------------------|-------------------|---------|------|--------|--------------------|----------|--------|
| **ED-Major Alteration** | 40        | 0      | 29                | 9        | 237                      | 79                | 9       | 27   | 6,370  | 392                | 8        | 1      |
| **ED-Minor A Alteration** | 188      | 0      | 71                | 13       | 668                      | 63                | 22      | 102  | 13,080 | 1,058              | 161      | 2      |
| **ED-Minor B Alteration** | 172      | 43     | 99                | 43       | 0                        | 454               | 10      | 154  | 7,086  | 341                | 103      | 1      |

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

### Key Takeaways

1. **Comprehensive Integration:** Merging the Altered dataset with License and Installed data created a unified framework for analyzing elevator modifications alongside their installation and licensing details.
2. **Frequent Alterations Indicators:** A small subset of elevators with more than five alterations may indicate underlying issues or high-demand usage, necessitating targeted maintenance strategies.
3. **Effectiveness of Alteration Processes:** The high number of “Passed” statuses across all alteration types reflects effective completion rates, while the presence of “Pending Follow Up” suggests areas for process improvement.
4. **Design Phase Importance:** The significant “Design Registered” count for Minor B alterations underscores the necessity of meticulous planning and design in minor modifications to ensure compliance and functionality.
5. **Minimal Rejections:** The low rejection rates across alteration types indicate strong adherence to regulatory standards and effective request submissions.

### Conclusion

The Altered Dataset analysis provided invaluable insights into the modification history of Rocket Elevator’s installations. By merging alteration records with existing License and Installed data, a comprehensive view of each elevator’s operational and maintenance lifecycle was achieved. Key findings highlight that while the majority of alteration requests are successfully completed, a notable minority require further follow-ups or are in design phases, particularly among minor alterations. Identifying elevators with frequent alterations opens avenues for targeted investigations into potential causes, be it structural, usage-related, or procedural inefficiencies. Moving forward, integrating additional datasets such as **Inspection** records will further enrich the analysis, enabling the development of predictive models to enhance maintenance scheduling, improve compliance adherence, and optimize operational reliability.

**Future Steps:**

1. **Deep Dive into High-Frequency Alterations:** Investigate the specific causes and contexts surrounding elevators with more than five alterations to identify patterns or systemic issues.
2. **Process Optimization:** Analyze the reasons behind “Pending Follow Up” statuses to streamline the alteration request and approval process.
3. **Predictive Maintenance Modeling:** Utilize the integrated dataset to build machine learning models that predict future alterations, thereby enabling proactive maintenance and resource allocation.
4. **Compliance and Safety Enhancements:** Assess the correlation between alteration types, statuses, and safety compliance to ensure elevators meet all regulatory standards consistently.

---

