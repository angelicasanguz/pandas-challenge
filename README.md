# pandas-challenge
PyCity Schools Analysis
There are two documents with extension .csv called “schools_complete.csv” and “students_complete.csv”, where you have to analyze information of 15 Schools.
You will need showing information about student's math and reading scores, as well as various information on the schools they attend. 
Your responsibility is to aggregate the data to and showcase obvious trends in school performance.
 
Your final report should include each of the following:
#District Summary
Perform the necessary calculations and then create a high-level snapshot of the district's key metrics in a DataFrame.
Include the following:
•	Total number of unique schools
school_count = len(school_data_complete.school_name.unique())
•	Total students
student_count = school_data_complete.student_name.count()
•	Total budget
total_budget = sum(school_data_complete.budget.unique())
•	Average math score
average_math_score = school_data_complete.math_score.mean()
•	Average reading score
average_reading_score = school_data_complete.reading_score.mean()
•	% passing math (the percentage of students who passed math)
passing_math_count = school_data_complete[(school_data_complete["math_score"] >= 70)].count()["student_name"]
passing_math_percentage = passing_math_count / float(student_count) * 100
•	% passing reading (the percentage of students who passed reading)
passing_reading_count = school_data_complete[(school_data_complete["reading_score"] >= 70)].count()["student_name"]
passing_reading_percentage = passing_reading_count/ float(student_count) * 100
•	% overall passing (the percentage of students who passed math AND reading)
passing_math_reading_count = school_data_complete[
    (school_data_complete["math_score"] >= 70) & (school_data_complete["reading_score"] >= 70)].count()["student_name"]
overall_passing_rate = passing_math_reading_count /  float(student_count) * 100

Creating DataFrame with information previously got.
 
 
#School Summary
Perform the necessary calculations and then create a DataFrame that summarizes key metrics about each school.
Include the following:
•	School name
•	School type
school_names =school_data_complete.groupby(["school_name"])
school_types = school_names["type"].first()
•	Total students
per_school_counts = school_names["Student ID"].count()
•	Total school budget
per_school_budget = school_names["budget"].mean()
•	Per student budget
per_school_capita = per_school_budget / totalStudents
•	Average math score
per_school_math = school_names.math_score.mean()
•	Average reading score
per_school_reading = grouped_school.reading_score.mean()
•	% passing math (the percentage of students who passed math)
per_school_passing_math = school_students_passing_math / per_school_counts * 100
•	% passing reading (the percentage of students who passed reading)
per_school_passing_reading = school_students_passing_reading / per_school_counts * 100
•	% overall passing (the percentage of students who passed math AND reading)
students_passing_math_and_reading = school_data_complete[ (school_data_complete["reading_score"] >= 70) & (school_data_complete["math_score"] >= 70)

school_students_passing_math_and_reading = students_passing_math_and_reading.groupby(["school_name"]).size()
overall_passing_rate = school_students_passing_math_and_reading / per_school_counts * 100
 
 
 
#Highest-Performing Schools (by % Overall Passing)
Sort the schools by % Overall Passing in descending order and display the top 5 rows.
Save the results in a DataFrame called "top_schools".

top_schools = per_school_summary.sort_values(by=['Overall Passing Rate'], ascending=False)
top_schools.head(5)
 

Lowest-Performing Schools (by % Overall Passing)
Sort the schools by % Overall Passing in ascending order and display the top 5 rows.
Save the results in a DataFrame called "bottom_schools".

bottom_schools = per_school_summary.sort_values(by=['Overall Passing Rate'], ascending=True)
bottom_schools.head(5)
 
Math Scores by Grade
Perform the necessary calculations to create a DataFrame that lists the average math score for students of each grade level (9th, 10th, 11th, 12th) at each school.
  
 
Reading Scores by Grade
Create a DataFrame that lists the average reading score for students of each grade level (9th, 10th, 11th, 12th) at each school.
 
 
Scores by School Spending
Create a table that breaks down school performance based on average spending ranges (per student).
Use the code provided below to create four bins with reasonable cutoff values to group school spending.
spending_bins = [0, 585, 630, 645, 680]
labels = ["<$585", "$585-630", "$630-645", "$645-680"]



Use pd.cut to categorize spending based on the bins.
 
   
Use the following code to then calculate mean scores per spending range.
spending_math_scores = school_spending_df.groupby(["Spending Ranges (Per Student)"])["Average Math Score"].mean()
spending_reading_scores = school_spending_df.groupby(["Spending Ranges (Per Student)"])["Average Reading Score"].mean()
spending_passing_math = school_spending_df.groupby(["Spending Ranges (Per Student)"])["% Passing Math"].mean()
spending_passing_reading = school_spending_df.groupby(["Spending Ranges (Per Student)"])["% Passing Reading"].mean()
overall_passing_spending = school_spending_df.groupby(["Spending Ranges (Per Student)"])["% Overall Passing"].mean()
Use the scores above to create a DataFrame called spending_summary.
Include the following metrics in the table:
•	Average math score
•	Average reading score
•	% passing math (the percentage of students who passed math)
•	% passing reading (the percentage of students who passed reading)
•	% overall passing (the percentage of students who passed math AND reading)
 
 
Scores by School Size
Use the following code to bin the per_school_summary.
size_bins = [0, 1000, 2000, 5000]
labels = ["Small (<1000)", "Medium (1000-2000)", "Large (2000-5000)"]
Use pd.cut on the "Total Students" column of the per_school_summary DataFrame.
Create a DataFrame called size_summary that breaks down school performance based on school size (small, medium, or large).

  
Scores by School Type
Use the per_school_summary DataFrame from the previous step to create a new DataFrame called type_summary.
This new DataFrame should show school performance based on the "School Type".

 
References
Data generated by Mockaroo, LLCLinks to an external site., (2022). Realistic Data Generator. Data for this dataset was generated by edX Boot Camps LLC, and is intended for educational purposes only.

