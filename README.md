# eg_gamb
# Gambling Data Analysis

## Overview
This repository contains data related to gambling activities, including user information, betting activity, transactions, referral programmes, customer support interactions, and wallet transactions. The data is stored in CSV format and includes realistic transaction dates, bet information, and other metrics, designed for analysis in tools such as Tableau. The data has been uploaded manually to GitHub under **`eg_gamb`** and can be accessed for analysis, visualization, and reporting.

The repository also includes automation workflows to synchronize the data with **AWS S3** and a **Tableau** connection via **AWS Athena** for easy access and analysis.

## Data Structure

The following tables are included in this repository:

1. **user.csv**
   - Description: Contains information about users in the gambling system.
   - Columns: `id`, `name`, `created_at`.

2. **wallet.csv**
   - Description: Contains details about user wallets, each associated with a unique currency.
   - Columns: `id`, `currency`, `created_at`.

3. **game.csv**
   - Description: Contains information about the games available in the gambling system.
   - Columns: `id`, `name`, `provider`, `created_at`.

4. **bets.csv**
   - Description: Contains details of the bets placed by users, including the game played, bet value, and the outcome.
   - Columns: `id`, `user_id`, `game_id`, `value`, `multiplier`, `profit`, `created_at`.

5. **transaction.csv**
   - Description: Contains details about wallet transactions, including deposits and withdrawals.
   - Columns: `wallet_id`, `amount`, `transaction_type`, `transaction_date`.

6. **referral_program.csv**
   - Description: Contains information about the referral programme, where users can refer others and receive bonuses.
   - Columns: `id`, `referrer_user_id`, `referred_user_id`, `referral_date`, `bonus_awarded`.

7. **customer_support.csv**
   - Description: Contains information about customer support tickets raised by users.
   - Columns: `id`, `user_id`, `support_ticket_id`, `issue_type`, `resolution_status`, `issue_timestamp`.

8. **transaction_history.csv**
   - Description: Contains the history of transactions for users, including deposits and withdrawals.
   - Columns: `user_id`, `transaction_date`, `amount`, `transaction_status`.

9. **wallet_transaction.csv**
   - Description: Contains detailed wallet transaction information.
   - Columns: `wallet_id`, `transaction_type`, `amount`, `transaction_date`.

10. **exchange_rate.csv**
    - Description: Contains exchange rates for different currencies.
    - Columns: `currency`, `rate`, `created_at`.

11. **deposit.csv** (New)
    - Description: Contains deposit details, including wallet_id, value, and created_at.
    - Columns: `wallet_id`, `value`, `created_at`.

12. **user_kyc.csv**
    - Description: Contains KYC (Know Your Customer) details with user_id, kyc_level, and created_at.
    - Columns: `user_id`, `kyc_level`, `created_at`.

13. **campaign.csv**
    - Description: Contains campaign details like id, name, user_id, and created_at.
    - Columns: `id`, `name`, `user_id`, `created_at`.

14. **referral.csv**
    - Description: Tracks user referrals with campaign_id and referral_user_id.
    - Columns: `campaign_id`, `referral_user_id`.

15. **user_location.csv**
    - Description: Contains the geographical location of users, including city, country, and optional latitude/longitude for precise mapping.
    - Columns: `user_id`, `city`, `country`, `latitude`, `longitude`, `created_at`.

## Getting Started

To get started with this project, follow these steps:

## 1. **Data Upload Process**

The data is stored in CSV format and is manually uploaded to the GitHub repository. Each CSV file corresponds to a table that represents different aspects of gambling activities, such as user data, bet transactions, wallet information, and more. The tables and data are updated manually, and future improvements may include automation using Python scripts to update the data.

- **Automation**: Although the data was manually uploaded due to time constraints, an automation process using Python can be done in the future for regular data updates.
- **CSV Files**: The CSV files are in the repository under the **`eg_gamb`** directory.

## 2. **AWS S3 Setup and Policies**

To access the data from GitHub and S3, the following setup was completed:
- **AWS S3 Bucket**: Created a bucket named `my-github-csv-files` to store the CSV files.
- **IAM Policies**: AWS IAM policies, users, and roles were set up to allow the necessary permissions for data transfer between GitHub and S3.
  - Custom policy for S3 can be seen under  **`eg_gamb/S3_bucketpolicy`**

## 3. **Synchronization with AWS S3**

The CSV data from GitHub is automatically uploaded to **AWS S3** using a **GitHub Actions workflow** called **`sync-to-s3.yml`**  under the **`eg_gamb/.github/workflows**.

- **S3 Bucket**: The data is stored in an S3 bucket named **`my-github-csv-files`**. 
- **Automatic Updates**: Every time the CSV files in the GitHub repository are updated, the workflow ensures that the data in S3 is automatically refreshed.
  - Results for S3 Bucket can be seen under **`eg_gamb/S3 bucket & Objects.png`**
 
### 3.1 **CI/CD (Continuous Integration and Continuous Delivery) with GitHub Actions**

The GitHub Actions workflow automates the process of uploading data to **AWS S3**, making it an integral part of the **CI/CD pipeline** for this project. This approach ensures:
- **Continuous Integration**: Every change made to the repository (such as new or updated CSV files) triggers the GitHub Actions workflow. This allows for seamless integration of new data without manual intervention, ensuring that the data stored in S3 is always up to date with the latest changes made in the repository.
- **Continuous Delivery**: Once the data is pushed to GitHub, the workflow automatically deploys the updated CSV files to the S3 bucket. This ensures that Tableau and other connected services have access to the most recent data, without requiring manual uploads, thus reducing errors and ensuring timely delivery of data.

The **CI/CD** pipeline enhances the project’s scalability and ensures that updates to the data are deployed quickly, enabling smooth operations and analysis across various platforms (e.g., Tableau via Athena).
- **Workflow File**: You can see the details of the GitHub Actions workflow in the **`sync-to-s3.yml`** file under **`eg_gamb/.github/workflows`**.

## 4. **Connecting AWS Athena with Tableau**

To facilitate data analysis and reporting in Tableau, the following steps were taken:

- **Gambling Database**: A database named **gambling_db** was created in AWS **Athena** to store the data.
- **Raw and Clean Tables**: Two queries were created to define the raw and clean tables within the gambling database in Athena.
  - **Raw Tables**: These tables are directly created from the CSV data.
  - **Clean Tables**: Additional tables are created after data processing and cleaning.
- Query Examples can be seen under **`eg_gamb/Athena_queryexample`**
- Results can be seen under **`eg_gamb/Athena Data, Query & Tables.png`**
  
## 5. **Configuring Tableau with AWS Athena**

To connect Tableau with AWS Athena:

- **ODBC Connection**: Configured the **ODBC data source** for Amazon Athena. Download from https://docs.aws.amazon.com/athena/latest/ug/odbc-v2-driver.html
- **Keys**: Provided the necessary keys to authenticate and access Athena from Tableau.
- **Database Connection**: Connected Tableau to the `gambling_db` database in Athena to visualize and analyze the data.
  - Results can be seen under **`eg_gamb/Tableau & Athena Connection.png`**

## 6. **Dashboard Creation**

- A dynamic Tableau dashboard was created to visualise gambling data stored in AWS Athena, connecting to the `gambling_db` database via ODBC.
- This dashboard provides an interactive analysis of user behaviour, betting activity, customer support, and campaign performance. All visuals in the dashboard are interactive, allowing users to explore the data based on different user segments, games, and issue types.
- Interactive filters and drill-down capabilities allow users to explore specific data points and trends in greater detail.
- The connection to AWS Athena ensures the dashboard is automatically updated with the latest data from S3, offering real-time insights into gambling activities.

### 6.1 **BetInfogram (User Lv) - Dashboard Overview**
The **BetInfogram (User Lv)** dashboard offers insights into user engagement, betting behaviour, customer support issues, and campaign effectiveness. You can filter and drill down into specific data segments and categories to make informed decisions about user behaviour and operational efficiency.
- You can access the Dashboard via: https://public.tableau.com/views/BetInfogram/BetInfogram?:language=en-GB&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link 
- To upload the Dashboard under Tableau Public, the data needed to be extracted, as it does not allow Live Data.

### **Sections of the Dashboard:**

#### 1. **General User Information**
- **Total Users & Total Bets**: Displays the total number of users and the total amount of bets placed.
- **User Segmentation**: Users are categorised into **Low Bettors**, **Medium Bettors** and **High Bettors** based on their total bet amounts.
- **KYC Level Distribution**: Shows the number of users by **KYC Level**, from Level 1 to Level 3, indicating user verification status.

#### 2. **Bet Segmentation**
- **% of Bets by Amount**: Displays the percentage of bets placed by each user category and shows how much each segment contributes to the total betting amount.
- **Average Bet and Average Profit**: Shows the average bet amount and the average profit for both **Low** and **Medium Bettors**.

#### 3. **Top Users by Bet Amount**
- This section shows the **Top N users** based on their total bet amounts. You can dynamically filter this number (e.g., top 5, top 10) to see the most engaged users.
- The data is displayed in a **bar chart** ranking users by their total bet amount.

#### 4. **User Activity by Game**
- Shows user engagement across different games. It includes the number of users, the average bet amount, and average profit per game. The data is divided by game, helping to identify which games are most popular or profitable.

#### 5. **Customer Support Analysis**
- **User Tickets**: Displays the number of support tickets raised by users, broken down by **Issue Type** (e.g., account locked, deposit issue).
- **Resolution Status**: Shows the proportion of tickets that are **resolved** versus **unresolved**.
- **Top Users Raising Tickets**: Displays a leaderboard of the users with the most support tickets, helping to identify users who may be having recurring issues.

### 6.2 **Interactive Features**

All visuals are interactive:
- **Filters**: You can filter by **Date**, **User Categories** (Low, Medium Bettor), and **Campaigns** to drill deeper into specific data segments.
- **Top N Users**: The **Top N** filter allows you to dynamically adjust the number of top users displayed in the **Top Users by Bet Amount** section.
- **Tooltips**: Hovering over data points in any visual reveals more detailed insights such as exact values for bet amounts, profit, and issue types.
- Users can filter the data by **KYC Level**, **Betting Categories**, or **Games** to explore specific subsets of data.
- The **Top N Users** parameter enables the flexibility to adjust the number of top users displayed, from a focus on just the top 5 to a broader view of the top 20 or more.

These interactive features allow users to explore trends, make comparisons, and gain deeper insights into user behaviour and operational performance.

### 6.3 **Data Explanation**

- **User Information**: The data shows user behaviour and categorises users based on the total bet amount placed. This segmentation helps in understanding the activity levels of different users.
- **KYC Level Distribution**: Indicates the number of users who have completed the KYC verification process, providing insights into user trust levels.
- **Bet Segmentation**: The data shows how much each user category contributes to the total bet amount and the associated profits.
- **Customer Support**: The data tracks support tickets raised by users, categorising them by issue type and tracking the resolution status.
- **Top Users**: This section highlights the users who contribute the most to the platform in terms of bet amount, helping to identify high-value users.

### 7. **Future Improvements**

- **Automation**: As mentioned earlier, the process of uploading data and syncing with AWS S3 is currently done manually. Python scripts can be used for continuous data updates.
- **Data Integrity**: Future improvements will include adding data validation and cleaning processes to ensure the quality of the data.
- **Tableau Dashboards**: Enhancements to the Tableau dashboards can include more complex visualisations and automated reporting.

