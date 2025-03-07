# 📌 Basic Pandas Interview Questions with Answers

1. What is Pandas, and how is it different from NumPy?
✅ Answer: Pandas is a Python library for data analysis and manipulation.<br>
It is built on top of NumPy and provides DataFrames and Series to handle structured/tabular data.

|Feature	|Pandas|	NumPy|
|---------|-------|-------|
|Data Structure|	Series, DataFrame	|Arrays (1D, 2D, nD)|
|Data Type	|Supports mixed types|	Numeric only|
|Operations|	Filtering, Grouping, Merging	|Mathematical computations|
|Performance|	Slower for numerical tasks	|Faster for numerical tasks|

```
import pandas as pd
import numpy as np

# NumPy Array
arr = np.array([1, 2, 3, 4])

# Pandas Series
s = pd.Series(arr)
print(s)
```

2. What is the difference between a Pandas Series and DataFrame?
✅ Answer: Series is a one-dimensional labeled array.<br>
DataFrame is a two-dimensional table with rows and columns.
```
data = [10, 20, 30]
s = pd.Series(data)

df = pd.DataFrame({'Numbers': data})

print("Series:\n", s)
print("DataFrame:\n", df)
```

3. What is the difference between .loc[] and .iloc[]?
✅ Answer: .loc[] selects data by labels (column names, row index) <br>
.iloc[] selects data by integer index
```
df = pd.DataFrame({'Name': ['Alice', 'Bob'], 'Age': [25, 30]}, index=['A', 'B'])

print(df.loc['A'])   # Select by label
print(df.iloc[0])    # Select by index
```




# Intermediate Pandas Interview Questions with Answers
4. How do you handle missing values in Pandas?
✅ Answer:
Detect missing values: df.isnull() <br>
Drop missing values: df.dropna() <br>
Fill missing values: df.fillna(value)

```
df = pd.DataFrame({'A': [1, np.nan, 3], 'B': [4, 5, np.nan]})

df_filled = df.fillna(0)  # Replace NaN with 0
print(df_filled)
```

5. What is groupby() and how does it work?
✅ Answer:
groupby() is used for grouping data and performing aggregate functions.
```
df = pd.DataFrame({'Department': ['IT', 'HR', 'IT'],
                   'Salary': [50000, 45000, 60000]})

grouped = df.groupby('Department')['Salary'].mean()
print(grouped)
```

6. How do you merge two DataFrames?
```
df1 = pd.DataFrame({'ID': [1, 2], 'Name': ['Alice', 'Bob']})
df2 = pd.DataFrame({'ID': [1, 2], 'Salary': [50000, 60000]})

df_merged = pd.merge(df1, df2, on='ID')
print(df_merged)
```

7. What is a pivot table in Pandas?
```
df = pd.DataFrame({'Department': ['IT', 'HR', 'IT'],
                   'Salary': [50000, 45000, 60000]})

pivot = df.pivot_table(values='Salary', index='Department', aggfunc='mean')
print(pivot)
```
✅ Answer: A pivot table reshapes data and aggregates values.
```
df = pd.DataFrame({'Department': ['IT', 'HR', 'IT'],
                   'Salary': [50000, 45000, 60000]})

pivot = df.pivot_table(values='Salary', index='Department', aggfunc='mean')
print(pivot)
```

8. How do you apply a custom function to a DataFrame column?
How do you apply a custom function to a DataFrame column?
```
df['Bonus'] = df['Salary'].apply(lambda x: x * 0.1)
```


# Advanced Pandas Interview Questions with Answers

9. How do you improve Pandas performance for large datasets?
✅ Answer:
- Use vectorized operations instead of loops.
- Optimize memory by changing data types (.astype('float32')).
- Load large CSV files in chunks (pd.read_csv('file.csv', chunksize=10000)).

10. What is the difference between map(), apply(), and applymap()?
✅ Answer:
- map() → Used for Series
- apply() → Used for columns/rows
- applymap() → Used for entire DataFrame

11. How do you optimize memory usage in Pandas?
✅ Answer: Convert large data types to smaller ones using .astype().
```
df['ID'] = df['ID'].astype('int32')
df['Salary'] = df['Salary'].astype('float32')
```


# Project-Based Pandas Questions
12. How did you use Pandas in your project? Can you describe a real-world use case?
✅ How to Answer:<br>
"Since RGU-Blogs is a blog management system, Pandas could be used for analyzing user activity, post engagement, and comment trends." <br>

Example answer: <br>
- In the RGU-Blogs project, Pandas was used for analyzing blog engagement and user behavior.
- We stored blog posts, comments, and user activity logs in PostgreSQL.
- Using Pandas, I extracted and processed this data to generate insights like:
- 1. Most active users based on blog post count.
  2. Peak posting times by analyzing timestamps.
  3. Average comments per blog to measure engagement.
 ```
import pandas as pd
from django.db import connection

# Fetch data from PostgreSQL
query = "SELECT author_id, COUNT(*) as post_count FROM blogs GROUP BY author_id"
df = pd.read_sql(query, connection)

# Finding the most active user
most_active_user = df.sort_values('post_count', ascending=False).head(1)
print(most_active_user)
```


13. Have you handled large datasets in Pandas? If yes, how did you optimize performance?
✅ How to Answer:<br>
Explain dataset size and the techniques used to optimize performance.

Example answer: <br>
- In RGU-Blogs, handling large amounts of blog posts, comments, and user logs in PostgreSQL was a challenge.
- Instead of loading entire datasets into Pandas, I optimized performance by:
- Loading data in chunks using pd.read_sql_query(chunksize=10000).
- Selecting only necessary columns to reduce memory usage.
- Using astype() to optimize data types, reducing memory usage by 50%.
- Applying vectorized operations instead of loops."

```
chunk_size = 10000
query = "SELECT id, author_id, created_at FROM blogs"
for chunk in pd.read_sql_query(query, connection, chunksize=chunk_size):
    chunk['created_at'] = pd.to_datetime(chunk['created_at'])  # Optimizing timestamps
    print(chunk.head())
```


14. What challenges did you face while handling missing data in your project?
✅ How to Answer:<br>
Mention specific missing data issues and your approach to handle them.<br>

example answer:<br>
- In the RGU-Blogs project, missing data was a challenge in user profiles and blog metadata.
- Some users didn't provide bio information or profile pictures, and some blog posts had missing categories.
- 1. fillna() with default values for missing profile details.
  2. Forward fill (ffill) for missing blog categories.
  3. Dropping rows (dropna()) when critical data was missing.
 
```
df['author_bio'].fillna("No bio available", inplace=True)
df['category'].fillna(method='ffill', inplace=True)
df.dropna(subset=['post_title', 'post_content'], inplace=True)
```

15. How did you visualize or analyze the data after processing it with Pandas?
✅ How to Answer:<br>
Explain data visualization techniques and their impact.<br>
- I used Matplotlib and Seaborn to visualize blog statistics in the admin dashboard. Some key insights were
- Post frequency trends using time-series plots.
- User engagement analysis using bar charts
- Comment distribution per post using histograms.
```
import matplotlib.pyplot as plt
import seaborn as sns

df['created_at'] = pd.to_datetime(df['created_at'])
df.set_index('created_at').resample('M').count()['id'].plot(kind='line')

plt.title("Monthly Blog Post Trend")
plt.xlabel("Month")
plt.ylabel("Number of Posts")
plt.show()
```

16. Can you explain a specific place where you used Pandas groupby() or merge()?
✅ How to Answer:<br>
Mention a real example where data aggregation was required.<br>

Example answer
- In the RGU-Blogs project, I needed to find the average number of comments per blog post.
- I used groupby() to count comments per post and then merged it with the blog post dataset.

```
# Fetch comments count per blog
comment_counts = df_comments.groupby('post_id')['comment_id'].count().reset_index()

# Merge with blog posts
df = df_blogs.merge(comment_counts, on='post_id', how='left')
df['comment_id'].fillna(0, inplace=True)
```


17. How do you handle and clean messy data in real-world datasets?
 How to Answer:<br>
Mention data cleaning steps and techniques used.<br>

example answer:
- Blog post data contained duplicate entries, extra spaces, and inconsistent formatting. I cleaned it by:
1. Removing duplicates using drop_duplicates().
2. Stripping extra spaces from text columns.
3. Standardizing categorical values.
```
df.drop_duplicates(inplace=True)
df['post_title'] = df['post_title'].str.strip()
df['category'] = df['category'].str.lower()
```

18. Have you used Pandas with databases? How did you load data into Pandas from SQL?
✅ How to Answer:<br>
Mention how you connected PostgreSQL with Pandas.<br>
- I connected Pandas to PostgreSQL using Django ORM and raw SQL queries.
- This allowed me to analyze user activity efficiently.
```
from sqlalchemy import create_engine

engine = create_engine('postgresql://user:password@localhost/rgublogs')
df = pd.read_sql("SELECT * FROM blogs", con=engine)
```




