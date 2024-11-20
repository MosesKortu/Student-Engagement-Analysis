# Student-Engagement-Analysis
This project analyzes student engagement in an online course, focusing on course completion percentages, forum posts, and student satisfaction scores. The analysis includes data manipulation, visualization, and statistical analysis using Python libraries such as pandas, NumPy, and Matplotlib.

# Table of Contents

# Installation
* Usage
*Data
Analysis
Results
Contributing
License
Installation

To run this project, you need to have Python installed along with the following libraries:

pandas
numpy
matplotlib
You can install these libraries using pip:

pip install pandas numpy matplotlib
Usage

Clone the repository:

git clone https://github.com/yourusername/student-engagement-analysis.git
cd student-engagement-analysis
Run the Python script:

python analysis.py
Data

The dataset contains the following columns:

Student_ID: Unique identifier for each student.
Course_Completion_Percentage: Percentage of the course completed by the student.
Forum_Posts: Number of posts made by the student in the course forum.
Student_Satisfaction_Score: Satisfaction score given by the student (out of 5).
Sample data:

Student_ID  Course_Completion_Percentage  Forum_Posts  Student_Satisfaction_Score
1           85                            10           4.5
2           90                            15           4.7
3           78                            5            3.9
4           88                            13           4.6
5           92                            20           4.8
6           79                            7            4.2
7           85                            8            4.3
8           95                            25           5.0
9           88                            12           4.6
10          91                            17           4.7
Analysis

Average Course Completion

Calculate the average course completion percentage:

avg_coursecompletion = data['Course_Completion_Percentage'].mean()
print(f"The average course completion is: {avg_coursecompletion}%")
Average Student Satisfaction Score

Calculate the average student satisfaction score:

avg_satisfaction_score = data['Student_Satisfaction_Score'].mean()
print(f"The average student satisfaction score is: {avg_satisfaction_score}")
High-Engagement Students

Identify students with more than 15 forum posts:

high_engagement = data[data['Forum_Posts'] > 15]
print(high_engagement[['Student_ID', 'Forum_Posts']])
Correlation Analysis

Calculate the correlation between course completion and student satisfaction:

correlation = data['Course_Completion_Percentage'].corr(data['Student_Satisfaction_Score'])
print(f"Correlation between course completion and student satisfaction: {correlation}")
Visualization

Bar Plot for Course Completion vs. Satisfaction Score
plt.figure(figsize=(10, 6))
plt.bar(data['Student_ID'], data['Course_Completion_Percentage'], alpha=0.6, label='Completion %')
plt.bar(data['Student_ID'], data['Student_Satisfaction_Score'] * 10, alpha=0.6, label='Satisfaction Score')
plt.xlabel('Student ID')
plt.ylabel('Percentage / Satisfaction Score')
plt.title('Course Completion vs Satisfaction Score')
plt.legend()
plt.show()
Scatter Plot of Forum Posts vs Satisfaction Score
plt.scatter(data['Forum_Posts'], data['Student_Satisfaction_Score'], color='blue', label='Forum Posts vs Satisfaction Score')
plt.xlabel('Forum Posts')
plt.ylabel('Student Satisfaction Score')
plt.title('Forum Posts vs Satisfaction Score')
plt.show()
Group by Engagement Level

Group students by engagement level and calculate average satisfaction score:

bins = [0, 60, 80, 100]
labels = ['Low', 'Medium', 'High']
data['Engagement_Level'] = pd.cut(data['Course_Completion_Percentage'], bins=bins, labels=labels)
engagement_group = data.groupby('Engagement_Level')['Student_Satisfaction_Score'].mean()
print(engagement_group)
Linear Regression

Perform linear regression to understand the relationship between engagement metrics:

X = np.array([data['Course_Completion_Percentage'], data['Forum_Posts']])
y = np.array(data['Student_Satisfaction_Score'])
X_transpose = X.T
beta = np.linalg.inv(X.dot(X_transpose)).dot(X).dot(y)
print(f"Regression Coefficients: {beta}")
Results

The average course completion percentage is 87.1%.
The average student satisfaction score is 4.53.
High-engagement students (more than 15 forum posts) tend to have higher satisfaction scores.
There is a strong positive correlation (0.97) between course completion and student satisfaction.
There is also a strong positive correlation (0.94) between course completion and forum posts.
Contributing

Contributions are welcome! Please fork the repository and submit a pull request.

License

This project is licensed under the MIT License.

