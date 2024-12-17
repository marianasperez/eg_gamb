# eg_gamb
# Gambling Data Analysis

## Overview

This repository contains data related to gambling activities, including user information, betting activity, transactions, referral programmes, customer support interactions, and wallet transactions. The data is stored in CSV format and includes realistic transaction dates, bet information, and other metrics, designed for analysis in tools such as **Tableau**.

## Data Structure

The following tables are included in this repository:

### 1. **user.csv**
- **Description**: Contains information about users in the gambling system.
- **Columns**:
  - `id`: Unique identifier for each user.
  - `name`: Name of the user.
  - `created_at`: Date when the user account was created.

### 2. **wallet.csv**
- **Description**: Contains details about user wallets, each associated with a unique currency.
- **Columns**:
  - `id`: Unique identifier for each wallet.
  - `currency`: The currency type for the wallet (e.g., USD, EUR, BRL).
  - `created_at`: Date when the wallet was created.

### 3. **game.csv**
- **Description**: Contains information about the games available in the gambling system.
- **Columns**:
  - `id`: Unique identifier for each game.
  - `name`: Name of the game (e.g., Samurai Dogs).
  - `provider`: The provider of the game (e.g., Twist, Stake.com).
  - `created_at`: Date when the game was added to the system.

### 4. **bets.csv**
- **Description**: Contains details of the bets placed by users, including the game played, bet value, and the outcome.
- **Columns**:
  - `id`: Unique identifier for each bet.
  - `user_id`: Identifier of the user who placed the bet.
  - `game_id`: Identifier of the game that the bet was placed on.
  - `value`: The amount of the bet.
  - `multiplier`: The multiplier for the bet outcome.
  - `profit`: The profit made from the bet.
  - `created_at`: Date when the bet was placed.

### 5. **transaction.csv**
- **Description**: Contains details about wallet transactions, including deposits and withdrawals.
- **Columns**:
  - `wallet_id`: Unique identifier for the wallet.
  - `amount`: The amount of money involved in the transaction.
  - `transaction_type`: Type of transaction (`deposit` or `withdrawal`).
  - `transaction_date`: Date of the transaction.

### 6. **referral_program.csv**
- **Description**: Contains information about the referral programme, where users can refer others and receive bonuses.
- **Columns**:
  - `id`: Unique identifier for each referral record.
  - `referrer_user_id`: The user who made the referral.
  - `referred_user_id`: The user who was referred.
  - `referral_date`: Date of the referral.
  - `bonus_awarded`: Bonus received by the referrer.

### 7. **customer_support.csv**
- **Description**: Contains information about customer support tickets raised by users.
- **Columns**:
  - `id`: Unique identifier for each support interaction.
  - `user_id`: The user who raised the support ticket.
  - `support_ticket_id`: Identifier for the support ticket.
  - `issue_type`: Type of issue (e.g., account locked, deposit issue).
  - `resolution_status`: Status of the issue (resolved or unresolved).
  - `issue_timestamp`: Date and time when the issue was raised.

### 8. **transaction_history.csv**
- **Description**: Contains the history of transactions for users, including deposits and withdrawals.
- **Columns**:
  - `user_id`: Unique identifier for the user.
  - `transaction_date`: Date of the transaction.
  - `amount`: The amount of money involved in the transaction.
  - `transaction_status`: The status of the transaction (completed or pending).

### 9. **wallet_transaction.csv**
- **Description**: Contains detailed wallet transaction information.
- **Columns**:
  - `wallet_id`: Unique identifier for the wallet.
  - `transaction_type`: Type of transaction (deposit or withdrawal).
  - `amount`: The amount of money involved.
  - `transaction_date`: The date of the transaction.

### 10. **exchange_rate.csv**
- **Description**: Contains exchange rates for different currencies.
- **Columns**:
  - `currency`: Currency type (e.g., USD, EUR).
  - `rate`: The exchange rate for the currency.
  - `created_at`: Date when the exchange rate was recorded.

### 11. **deposit.csv** (New)
- **Description**: Contains deposit details, including `wallet_id`, `value`, and `created_at`.
- **Columns**:
  - `wallet_id`: Unique identifier for the wallet.
  - `value`: The amount deposited.
  - `created_at`: Date when the deposit was made.

### 12. **user_kyc.csv** 
- **Description**: Contains KYC (Know Your Customer) details with `user_id`, `kyc_level`, and `created_at`.
- **Columns**:
  - `user_id`: Unique identifier for the user.
  - `kyc_level`: The KYC level of the user.
  - `created_at`: Date when the KYC level was assigned.

### 13. **campaign.csv** 
- **Description**: Contains campaign details like `id`, `name`, `user_id`, and `created_at`.
- **Columns**:
  - `id`: Unique identifier for the campaign.
  - `name`: Name of the campaign.
  - `user_id`: The user associated with the campaign.
  - `created_at`: Date when the campaign was created.

### 14. **referral.csv** 
- **Description**: Tracks user referrals with `campaign_id` and `referral_user_id`.
- **Columns**:
  - `campaign_id`: Unique identifier for the campaign.
  - `referral_user_id`: Unique identifier for the user who made the referral.

### 15. **user_location.csv** 
- **Description**: Contains the geographical location of users, including city, country, and optional latitude/longitude for precise mapping.
- **Columns**:
  - `user_id`: Unique identifier for the user (links to `user.csv`).
  - `city`: The city where the user is located.
  - `country`: The country where the user is located.
  - `latitude`: Latitude for precise mapping.
  - `longitude`: Longitude for precise mapping.
  - `created_at`: Date when the location data was recorded.

## Getting Started

### Prerequisites

1. **Tableau** or another data analysis tool to visualise and analyse the data.
2. GitHub account to access the repository and clone/download the files.

### How to Load the Data into Tableau

1. **Clone or download the repository**:
   - Clone the repository using Git or download the ZIP file and extract it to your computer.

2. **Connect Tableau to the data**:
   - Open Tableau and go to **Data** > **Web Data Connector**.
   - Use the **raw URL** for each CSV file (available after uploading to GitHub).
   - Load the data from the raw URL into Tableau.

3. **Start analysing**:
   - Use Tableau to create visualisations like trends in bets, transaction volumes, user activity, and more.

## Conclusion

This dataset can be used for a variety of analytical tasks, including understanding user behaviour, tracking financial transactions, and analysing customer support trends in a gambling system. The data is designed to be realistic and is structured to provide valuable insights.
