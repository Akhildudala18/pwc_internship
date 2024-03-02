# Customer Retention 

## Table of contents
- [Problem Statement]
- [Data Sourcing]
- [Data Preparation]
- [Data Modeling]
- [Data Visualization]
- [Analysis and Insights]
  
# Problem Statement

- **Problem:** Churning customers using PhoneNow services were got in touch after they terminated the contract, and the Customer Retention manager wants to understand their customer profile and insights with a focus on retaining customers as well as approaching in advance who is at risk.
- **Objectives:** The purpose of this analysis is to create a Customer Retention Dashboard in Power BI for the Customer Retention Manager that reflects all relevant Key Performance Indicators (KPIs) and metrics to:
    - Self-exploratory the customer demographics and insights (churning & retaining).
    - Actively approach who is at risk with the risk level of specific customer
    - Contain many metrics and plots related to a single area of business for discussing with higher managers and generating further analysis.
    - Allows for minimal interaction.
    - Based on finding recommend improving customer retention.

# Data Sourcing

The dataset used for this analysis was provided by [Pwc Switzerland](https://www.pwc.ch/en/careers-with-pwc/students/virtual-case-experience.html) and available here: [Churn Dataset](https://github.com/calmk/PWC-Virtual-Case-Experience/blob/main/Task%203%3A%20Customer%20Retention/02%20Churn-Dataset.xlsx)

# Data Preparation

The dataset was loaded into Microsoft Power BI Desktop for modeling after transformation in Power Query.

### Metadata

The tabulation below shows the metadata of `Churn` dataset:

| File name | 02 Churn-Dataset  |
| --- | --- |
| Format | .xlsx |
| Size | 772KB |
| Fields | 23 |
| Entities | 7043 |

The tabulation below shows the `Churn` table with its field's names and their description:

| Field Name | Description | Data Type |
| --- | --- | --- |
| customerID | Represents the unique number of the customer in the dataset | Text  |
| gender | Describes the gender of the customer | Text |
| SeniorCitizen | Describes if the customer is a senior citizen | Text |
| Partner | Describes if the customer has a partner | Text |
| Dependents | Describes if the customer has a dependent | Text |
| tenure | Describes how long as a customer | Whole number |
| PhoneService | Describes if the customer has registered a phone service | Text |
| MultipleLines | Describes if the customer has registered multiple lines | Text |
| InternetService | Describes if the customer has registered for Internet service | Text |
| OnlineSecurity | Describes if the customer has registered for online security | Text |
| OnlineBackup | Describes if the customer has registered for online backup | Text |
| DeviceProtection | Describes if the customer has registered for device protection | Text |
| TechSupport | Describes if the customer has registered for tech support | Text |
| StreamingTV | Describes if the customer has registered to stream tv | Text |
| StreamingMovies | Describes if the customer has registered to stream movies | Text |
| Contract | Describes the length of the contract of the customer | Text |
| PaperlessBilling | Describes if the customer has registered for paperless billing | Text |
| PaymentMethod | Describes the payment method of the customer | Text |
| MonthlyCharges | Represents the monthly charge incurred by the customer | Decimal number |
| TotalCharges | Represents the total charge incurred by the customer | Decimal number |
| numAdminTickets | Represents the number of admin tickets opened by the customer | Whole number |
| numTechTickets | Represents the number of tech tickets opened by the customer | Whole number |
| Churn | Describes if the customer is at risk of churn | Text |
- **Relevant information about the** `Churn` **dataset:**
    - Customers who left within the last month
    - Services each customer has signed up for phone, multiple lines, internet, online security, online backup, device protection, tech support, and streaming TV and movies
    - Customer account information: how long as a customer, contract, payment method, paperless billing, monthly charges, total charges and number of tickets opened in the categories administrative and technical
    - Demographic info about customers – gender, age range, and if they have partners and dependents

### Data Cleaning

Data Cleaning for the dataset was done in Power Query as follows:

- Each of the columns in the table was validated to have the correct data type
- There are 11 `N/A` values in `TotalCharges` column. Those missing values were filled with the `MonthlyCharges` value of each row because those customers are new and their tenure is just 1. `Table.AddColumn(#"Changed Type", "Custom", each if [TotalCharges] = null then [MonthlyCharges] else [TotalCharges])`

### Data Transformation
A new table named `modified` was created by duplicating the `Churn dataset` table and unpivoting some columns to support a clear overview look. In the new table, I conducted transformation using M-formula, you can refer at below:

- Attribute of demographic info: `Table.Unpivot(#"Replaced Value1", {"SeniorCitizen", "Partner", "Dependents"}, "Attribute", "Value")`
- Attribute of services:
    - `Table.ReplaceValue(#"Renamed Columns","No internet service","No",Replacer.ReplaceText,{"OnlineSecurity", "OnlineBackup", "DeviceProtection", "TechSupport", "StreamingTV", "StreamingMovies"})`
    - `Table.Unpivot(#"Reordered Columns", {"PhoneService", "MultipleLines", "Internet", "OnlineSecurity", "OnlineBackup", "DeviceProtection", "TechSupport", "StreamingTV", "StreamingMovies"}, "Attribute", "Value.1")`


# Data Modeling

After the dataset was cleaned and transformed, it was ready to be modeled.

- A one-to-many (*:1) relationship was created between the `Churn dataset` and the `modified`,  tables using the `customerId` column in each of the tables
- A one-to-one (1:1) relationship was created between the `Churn dataset` and the `Probability`,  tables using the `customerId` column in each of the tables
- `Measure` was created to store all DAX measures for ensuring the organization


# Data Visualization
Data visualization for the datasets was done in Microsoft Power BI Desktop, the dashboard includes 3 main dashboards and 5 tooltip pages

- **Churn Profile**

- **Customer Profile**
![2024-03-02 (4)](https://github.com/Akhildudala18/pwc_internship/assets/122172355/65556ecb-0588-45d1-ad58-9b33a582d22c)
![2024-03-02 (5)](https://github.com/Akhildudala18/pwc_internship/assets/122172355/25cc3a48-a564-41e3-91c6-07e1b766542c)



## Dashboard type

Dashboard by the level of detail: **Tactical dashboard**

Dashboard by use-case: **Exploratory**

Target audience: **Customer** **Retention Manager**

## Key Performance Indicators and Metrics:
**About Customer Profile:**

- Number of retained and churned customers
- Retention & Churn Rate
- Total Admin & Tech ticket
- Total and monthly charge
- Demographic, Account and Service info

**About EDA Churn Profile:**

- Churn by each service
- Churn by tenure
- Churn by Contract type
- Total Admin & Tech tickets of churn customers


# Analysis and Insights
The purpose of this dashboard is to serve as self-exploratory for managers, but I still note some highlighted points that I recognize below:

- Month-to-Month contracts, lack of online security and tech support, and issues with Fiber Optic service are some of the reasons for customer churn.
- Only 16% of the customers are senior citizens, with almost double the churn rate compared to younger customers.
- The customers have varying contract lengths, with a lot of them only staying for a month and some for up to 72 months.
- Customers taking longer contracts tend to be more loyal and stay with the company for a longer period of time.
- Customers are more likely to churn when the monthly charges are high, and there is a higher chance of churn when the total charges are lower.



