# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles in the US?

To find the five most in demand skills for the three most popular roles in the field of Data(Analyst, Engineer and Scientist). This helps anyone plan a roadmap to enter the field of data by giving a general analysis of what is currently most wanted by various companies.

View my notebook with detailed steps here: [skill_demand_project.ipynb] (skill_demand_project.ipynb)

### Data Visualization

```python
fig, ax = plt.subplots(len(job_titles), 1)

sns.set_theme(style = 'ticks')

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    #df_plot.plot(kind='barh', x='job_skills', y='skill_percent', ax=ax[i], title=job_title)
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue = 'skill_count', palette = 'dark:b_r')
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].set_title(job_title)
    ax[i].legend().remove()
    ax[i].set_xlim(0, 100)

    for n, value in enumerate(df_plot['skill_percent']):
        ax[i].text(value+1, n, f'{value:.2f}%', va='center')

    if i != len(job_titles) - 1:
        ax[i].set_xticks([])
        
fig.suptitle('Likelihood of a skill being required for a job posting')
plt.tight_layout()
plt.show()
```

### Results
![Top 5 skills for top 3 roles in Data](image.png)

### Insights

Data Analyst:

    Strong reliance on SQL (50.8%) for querying and data manipulation.
    Excel (40.58%) is still highly relevant for reporting and analysis.
    Tableau (28.48%) for dashboarding and visualization.

Data Engineer:

    Heavy emphasis on SQL (68.3%) and Python (64.89%) for managing data pipelines.
    Cloud technologies (AWS, Azure) and Spark highlight a need for distributed computing and cloud-based solutions.

Data Scientist:

    Python (72.04%) is the most essential tool for data science and machine learning.
    SQL (51.05%) remains crucial for data retrieval.
    R (44.23%) is prominent for statistical modeling.

Industry Implications:

    SQL remains a core skill across all data roles.
    Data Engineers require cloud and big data expertise, while Data Scientists focus more on Python and statistical tools.
    Data Analysts use business intelligence tools like Excel and Tableau to communicate insights.
    SAS is declining in demand but still relevant in some analyst and data science roles.

Recommendations for Job Seekers:

    Aspiring Data Analysts → Learn SQL, Excel, and Tableau.
    Aspiring Data Engineers → Gain expertise in SQL, Python, AWS, Azure, and Spark.
    Aspiring Data Scientists → Focus on Python, SQL, R, and machine learning.

## 2. How are in-demand skills trending for Data Analysts?

![Line chart showing the trends for top skills for Data Analysts.](image-1.png)

### Data Visualization:

```python
from matplotlib.ticker import PercentFormatter

df_plot = df_DA_US_percent.iloc[:, :5]
sns.lineplot(data=df_plot, dashes=False, legend='full', palette='tab10')
sns.set_theme(style='ticks')
sns.despine()

plt.title('Trending Top Skills for Data Analysts in the US')
plt.ylabel('Likelihood in Job Posting')
plt.xlabel('2023')
plt.legend().remove()
plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))

for i in range(5):
    plt.text(11.2, df_plot.iloc[-1, i], df_plot.columns[i], color='black')

plt.show()
```
### Insights

    SQL dominates job postings (~60%) but sees a slight decline mid-year. It's a must-have skill.

    Excel remains important but trends downward after August, possibly due to shifts toward advanced tools.

    Python and Tableau compete closely, with Python gaining slight preference.

    Power BI, though least in demand, shows gradual growth, hinting at rising adoption.

Takeaway for Job Seekers:

    Master SQL—it’s essential.

    Excel is still useful, but learning Python and BI tools boosts opportunities.

    Power BI is on the rise—gaining proficiency may provide a competitive edge.