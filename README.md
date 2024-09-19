# Student Performance Analysis

## Overview

This project analyzes student performance based on various factors such as **Gender**, **Ethnic Group**, **Parental Education**, **Test Preparation**, and more. The dataset includes information on students' weekly study hours, scores in Math, Reading, and Writing, and other demographic factors. The analysis was performed using **Python** libraries such as `pandas`, `matplotlib`, and `seaborn` to understand relationships and trends in the data.

## Dataset Description

The dataset contains the following fields:

- **Gender**: Student's gender (Male/Female)
- **EthnicGroup**: Ethnic background of the student (e.g., group A, group B, group C)
- **ParentEduc**: Parents' education level
- **LunchType**: Type of lunch the student receives (e.g., standard, free/reduced)
- **TestPrep**: Whether the student has completed a test preparation course (Yes/No)
- **ParentMaritalStatus**: Marital status of the student's parents
- **PracticeSport**: Whether the student practices any sport (Yes/No)
- **IsFirstChild**: Whether the student is the first child in the family (Yes/No)
- **NrSiblings**: Number of siblings the student has
- **TransportMeans**: The means of transport the student uses to travel to school
- **WklyStudyHours**: The number of hours the student studies per week
- **MathScore**: Student's score in Math
- **ReadingScore**: Student's score in Reading
- **WritingScore**: Student's score in Writing

## Data Analysis

### 1. **Data Cleaning**
   - Dropped unnecessary columns (e.g., unnamed columns).
   - Standardized the `WklyStudyHours` column by replacing inconsistencies in the string values.

### 2. **Gender Distribution**
   - Analyzed the distribution of male and female students.
   - Created a bar plot to show that the number of female students is greater than that of male students.

   ```python
   ax = sns.countplot(data=df, x="Gender")
   plt.title("Gender Distribution")
   ax.bar_label(ax.containers[0])
   plt.show()
   ```
![image](https://github.com/user-attachments/assets/34d851ea-da81-454c-8829-5685de08cfe5)


### 3. **Impact of Parental Education on Scores**
   - Grouped the data by parents' education and calculated the mean scores in **Math**, **Reading**, and **Writing**.
   - Visualized this relationship using a heatmap, showing that parents' education has a significant impact on student scores.
![image](https://github.com/user-attachments/assets/ff62c9ec-bfc0-4958-ab25-2a5750c1b70b)

   ```python
   gb = df.groupby("ParentEduc").agg({"ReadingScore":"mean", "MathScore":"mean", "WritingScore":"mean"})
   sns.heatmap(gb, annot=True)
   plt.title("Impact of Parental Education on Student Scores")
   plt.show()
   ```

### 4. **Effect of Parental Marital Status on Scores**
   - Grouped the data by parents' marital status and calculated mean scores.
   - A heatmap was used to show that marital status has negligible impact on student scores.

   ```python
   gb1 = df.groupby("ParentMaritalStatus").agg({"ReadingScore":"mean", "MathScore":"mean", "WritingScore":"mean"})
   sns.heatmap(gb1, annot=True)
   plt.title("Impact of Parents' Marital Status on Student Scores")
   plt.show()
   ```
![image](https://github.com/user-attachments/assets/6d9eba2d-14ae-4b26-aeb8-91778ea208fb)


### 5. **Score Distribution**
   - Plotted boxplots to visualize the distribution of **Math**, **Reading**, and **Writing** scores to understand the variability in students' performance.
   
   ```python
   sns.boxplot(data=df, x="MathScore")
   plt.show()
   ![image](https://github.com/user-attachments/assets/bb22eb19-e516-4a90-8142-f4314768fccd)

   sns.boxplot(data=df, x="ReadingScore")
   plt.show()
   ![image](https://github.com/user-attachments/assets/bb948432-035f-4b7b-a474-6a13b3c3883f)

   sns.boxplot(data=df, x="WritingScore")
   plt.show()
   ```
![image](https://github.com/user-attachments/assets/355eacab-4ce8-4968-98f3-49d2af6a7862)


### 6. **Ethnic Group Distribution**
   - Analyzed the distribution of students across different ethnic groups using both a pie chart and a countplot.
   
   ```python
   groups = ["group A", "group B", "group C", "group D", "group E"]
   counts = [df.loc[df["EthnicGroup"] == group].count()["EthnicGroup"] for group in groups]
   plt.pie(counts, labels=groups, autopct="%1.2f%%")
   plt.show()
![image](https://github.com/user-attachments/assets/d2b8438e-2cf3-48ea-8c4a-30b5c15d35a7)
   ax = sns.countplot(data=df, x="EthnicGroup")
   ax.bar_label(ax.containers[0])
   ```
![image](https://github.com/user-attachments/assets/a1fca150-88e3-4c34-ad0a-eb84f9a2812e)




## Results

- **Gender**: The dataset shows a higher proportion of female students compared to male students.
- **Parental Education**: Higher parental education correlates with better student performance in Math, Reading, and Writing.
- **Marital Status**: No significant impact of parents' marital status on student scores.
- **Ethnic Group**: The distribution of students across ethnic groups shows the largest group is "group C" followed by "group B".

## Requirements

- **Python 3.x** and the following libraries:
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `seaborn`

To install the necessary libraries, run:

```bash
pip install pandas numpy matplotlib seaborn
```

## How to Use

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/student-performance-analysis.git
   ```

2. Load and explore the dataset:

   ```python
   import pandas as pd
   df = pd.read_csv("path_to_dataset.csv")
   df.head()
   ```

3. Run the analysis by following the provided Python scripts.

## Conclusion

The analysis reveals the influence of parental education and weekly study hours on student performance, while other factors such as gender and parental marital status have less impact. This project can be extended by exploring additional factors such as the influence of sports or the effect of test preparation.

---

Let me know if you'd like to make any adjustments to this file!
