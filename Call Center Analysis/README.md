<H1> Call Center Analysis  
  


## Table of contents
- [Problem Statement]
- [Data Preparation]
- [Data Modeling]
- [Data Visualization]
- [Analysis and Insights]

# Problem Statement

- **Problem:** The manager at PhoneNow (a big telecom company) is seeking transparency and insight into the Call Center dataset to gain an accurate overview of long-term customer and agent behavior trends.
- **Objective:** The purpose of this analysis is to create a dashboard in Power BI for Call Center Manager that reflects all relevant Key Performance Indicators (KPIs) and metrics to:
    - Self-exploratory call trends
    - Overview of the agent’s performance and behaviors
    - Overview the customer satisfaction
    - Contain many metrics and plots related to a single area of business for discussing with higher managers and generating further analysis.
    - Allows for minimal interaction
- **Possible KPIs** include (but are not limited to):
    - Overall customer satisfaction
    - Overall calls answered/abandoned
    - Calls by time
    - Average speed of answer
    - Agents performance quadrant -> average handle time(talk duration) vs calls answered

# Data Sourcing

The Dataset used for this analysis was provided by [Pwc Switzerland](https://www.pwc.ch/en/careers-with-pwc/students/virtual-case-experience.html) and available here: [Call Center Dataset](https://github.com/calmk/PWC-Virtual-Case-Experience/blob/main/Task%202%3A%20Call%20Center%20Dashboard/01%20Call-Center-Dataset.xlsx)
# Data Preparation

The dataset was loaded into Microsoft Power BI Desktop for transformation in Power Query and modeling.

### Metadata

The tabulation below shows the metadata of `Call Center` dataset:

| File name |01 Call-Center-Dataset  |
| --- | --- |
| Format | .xlsx |
| Size | 249KB |
| Fields | 10 |
| Entities | 5000 |
| Time | January 1, 2021 - March 31, 2021 |

The tabulation below shows the `Call Center` table with its fields names and their description:

| Field Name | Description | Data Type |
| --- | --- | --- |
| Call Id | Represents every unique observation in the dataset | Text  |
| Agent | Describes the name of the agent | Text |
| Date | Describes the date of the call | Date |
| Time | Represents the time of the call | Date/Time |
| Topic | Describes the topic of the caller | Text |
| Answered (Y/N) | Describes if the call was answered or not | Text |
| Resolved | Describes if the problem was Resolved or not | Text |
| Speed of answer in seconds | Represents the speed of answer in seconds | Decimal number |
| AvgTalkDuration | Represents the average talk duration of a call | Time |
| Satisfaction rating | Represents the satisfaction rating of the agent during the call | Decimal number |

### Data Cleaning

Data Cleaning for the dataset was done in Power Query as follows:

- Unnecessary columns were removed
- Each of the columns in the table was validated to have the correct data type
- Unnecessary rows were removed


# Data Modeling

After the dataset was cleaned and transformed, it was ready to be modeled, but the dataset just included one table, so the Data Modeling is nothing much to modify

# Data Visualization
![2024-02-29 (3)](https://github.com/Akhildudala18/pwc_internship/assets/122172355/56a3fdd1-9428-43ae-862f-0ab87a3803b3)


Data visualization for the datasets was done in Microsoft Power BI Desktop and designed in PowerPoint, the dashboard includes:

- One main dashboard
- Six tooltip pages

### Dashboard type
Dashboard by the level of detail: **Tactical dashboard**

Dashboard by use-case: **Exploratory**

Target audience: **Team lead & Manager** (non-technical users)

### Key Performance Indicators and Metrics:

**About Calls and Agents:** 

- Overall calls answered/abandoned
- Calls received by time, day 
- Average speed of answer, handle duration
- Resolved rate by Agents, Topics
- Agent’s performance quadrant -> average handle time (talk duration) vs calls answered

**About Customer satisfaction:**

- Overall customer satisfaction
- Customer satisfaction distribution by Agents, Topics

  

# Analysis and Insights
The purpose of this dashboard is to serve as self-exploratory for managers, but I still note some highlighted points that I recognize below:

********************About Call trends:********************

- Customers tend to call more between 5:00 pm - 5:30 pm at 250 calls received with an abandoned rate is 18.40% (approximately to the average abandoned rate) and distributed mainly in the middle of the month
- The highest abandoned rate is 28.03% between 1:00 pm - 1:30 pm
- Customers have more problems with Streaming service
- The resolved rate is at a high rate (89,94%)

********************About performance of agents:********************

- The agent who satisfies customers most is Becky with a 12.02% of “Very good” rating
- The agent who has the highest resolved rate is Jim and he is effective with solving problems related to “Contract related” and “Admin Support”

********************About customer satisfaction:********************

- The average customer satisfaction is at an acceptable rate with 3.40, mainly comes from “Average” (30.04%) and “Good” (29.11%) rating
- The correlation between call answered and call resolved is strongly positive which resulted in a increase in the customer satisfaction rate











     



