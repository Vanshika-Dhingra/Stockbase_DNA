# Stockbase - Final Project Submission, DNA 2022
Stock-Base is a portmanteau of Stock screener and portfolio managing database.

## Table of Contents
- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
- [Installation](#installation)
- [Features](#features)
  
## Introduction

The wave of finance in the youth of our country is rising rapidly as we witnessed a pandemic and a year-long lockdown. There are a number websites which act as a good portfolio manager or a stock screener in the Indian finance arena, but there is yet to be an application/website which would provide the convince of being both, a screener AND a portfolio manager.

The goal of our project Stock-base is to integrate the features of a typical portfolio management system and an Indian stock screener, like [Google Finance](https://www.google.com/finance/?hl=en) and [Screener](https://www.screener.in) for example.

Stockbase would be a one-stop solution for keeping the records and updates of portfolio in check, while also acting as a good stock screener, saving people’s time from fruitlessly juggling between different websites for researching a stock. 

## Installation

### Prerequisites

- Python 3.8 or higher
- cryptography==3.4.7
- pprint==0.1
- requests==2.25.1
- json==2.0.9

### Installation

* Download the `10.mp4` file from [here](https://iiitaphyd-my.sharepoint.com/:v:/g/personal/aaryan_s_research_iiit_ac_in/EXjFogjN67JImOGp3uSpJdYB68Y7ZaS2qgvdrzU5fDUBsg?e=dINXhe).

* Load the create.sql file in the database folder to create the database.

* Insert data into the database using the insert.sql file in the database folder.

* Run the main.py file to start the application.

## Features


__Highlights__
- [x] User Authentication
- [x] Stock Screener
- [x] Portfolio Management
- [x] Stock Details
- [x] Stock Comparison
- [x] Stock Watchlist
- [x] Stock Search

### User Authentication

Authorises the user to access the application. The user can either login or register to access the application.

### Stock Screener

The stock screener is a feature which allows the user to search for stocks based on various parameters like market cap, price, etc. The user can also filter the stocks based on the parameters.

### Portfolio Management

The portfolio management feature allows the user to keep track of the stocks they own. The user can add stocks to their portfolio, update the quantity of stocks, and delete stocks from their portfolio.

### Stock Details

The stock details feature allows the user to view the details of a particular stock. The user can view the stock price, market cap, etc. of a stock.

### Stock Comparison

The stock comparison feature allows the user to compare the details of two stocks. The user can compare the stock price, market cap, etc. of two stocks.

### Stock Watchlist

The stock watchlist feature allows the user to add stocks to their watchlist. The user can add stocks to their watchlist, view the stocks in their watchlist, and delete stocks from their watchlist.

### Stock Search

The stock search feature allows the user to search for a stock. The user can search for a stock by entering the stock name or the stock symbol.

### App feedback

The app feedback feature allows the user to give feedback about the application. The user can give feedback about the application by entering their account ID, title, and comments.

#### Queries used (in order of appearance)

* Inserting feedback: Inserts feedback into the feedback table.
```sql
INSERT INTO feedback (account_id, title, comments) VALUES (%s, %s, %s);
```

* Deleting stock from watchlist: Deletes a stock from the watchlist table.
```sql
DELETE FROM watchlist WHERE serialNo = '%s' AND accountId = '%s' 
```

* Update Current Price: Updates the current price of a stock in the stock table.
```sql
UPDATE stock SET currentPrice = '%s' WHERE symbol = '%s'
```

* Fetch all stocks: Fetches all the stocks from the stock table.
```sql
SELECT * FROM stock
```

* Get total investment: Gets the total investment of done in a stock.
```sql
SELECT SUM(quantity*PurchasePrice) AS total_investment from transactions INNER JOIN comprisesof ON comprisesof.transactionID = transactions.transactionID WHERE comprisesof.securityCode = \'%s\';
```

* usernameStartsWithLetter: Checks if the username starts with a specified letter.
```sql
SELECT * FROM account WHERE username LIKE '%s';
```

* getTransactionWithMaxPurchasePrice: Gets the transaction with the maximum purchase price.
```sql
"SELECT * FROM Transactions WHERE purchasePrice = (SELECT MAX(purchasePrice) FROM Transactions)
```

* stocksWithStockPElessThanAValue: Gets the stocks with stock PE less than a specified value.
```sql
SELECT * FROM stock WHERE stockPE <= s;
```

* priceChangePositive: Gets the stocks with positive price change.
```sql
SELECT SecurityCode FROM stock WHERE currentPrice - prevClose > 0;
```

