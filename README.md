#   Online Bookstore Database
This README documents the analysis of the OnlineBookstore database.

**Author:** Sumit Yadav
**GitHub:** [https://github.com/sumit123](https://github.com/sumit123)
**LinkedIn:** [https://www.linkedin.com/in/sumit-yadav-888a14284](https://www.linkedin.com/in/sumit-yadav-888a14284)

##   Project Overview

    This SQL project provides a database solution for managing an online bookstore. It includes tables for storing information about books, customers, and orders, along with queries to retrieve and analyze data related to sales, customers, and inventory.

* **Purpose and Audience:**

* **Purpose:** This project was created to demonstrate my SQL proficiency and data analysis skills in a practical, business-oriented context. It showcases my ability to design a relational database, extract meaningful insights from data, and present findings in a clear and concise manner.
* **Target Audience:** The primary audience for this project is potential employers, particularly hiring managers and recruiters in the field of data analysis. It is intended to illustrate my capabilities in database management, data manipulation, and business intelligence, relevant to data analyst roles.


##   Database Summary

    * **Total Books:** The database contains 500 books.
    * **Total Customers:** The database contains 500 customers.
    * **Total Orders:** The database contains 500 orders.

##   Database Schema

    The database consists of the following tables:

    * **Books:** Stores information about books.
        * `Book_ID` (SERIAL PRIMARY KEY)
        * `Title` (VARCHAR(100))
        * `Author` (VARCHAR(100))
        * `Genre` (VARCHAR(50))
        * `Published_Year` (INT)
        * `Price` (NUMERIC(10, 2))
        * `Stock` (INT)
    * **Customers:** Stores information about customers.
        * `Customer_ID` (SERIAL PRIMARY KEY)
        * `Name` (VARCHAR(100))
        * `Email` (VARCHAR(100))
        * `Phone` (VARCHAR(15))
        * `City` (VARCHAR(50))
        * `Country` (VARCHAR(150))
    * **Orders:** Stores information about orders.
        * `Order_ID` (SERIAL PRIMARY KEY)
        * `Customer_ID` (INT, FOREIGN KEY referencing `Customers`)
        * `Book_ID` (INT, FOREIGN KEY referencing `Books`)
        * `Order_Date` (DATE)
        * `Quantity` (INT)
        * `Total_Amount` (NUMERIC(10, 2))

##   Book Analysis

    * **Genre Distribution:**
    The books in the database are categorized into the following genres: Biography, Fantasy, Non-Fiction, Fiction, Romance, Science Fiction, and Mystery. The distribution of books across these genres is as follows:
        * Biography: 13.0%
        * Fantasy: 14.2%
        * Non-Fiction: 13.4%
        * Fiction: 12.0%
        * Romance: 14.8%
        * Science Fiction: 16.8%
        * Mystery: 15.8%
      
 [Doc1_cropped (1).pdf](https://github.com/user-attachments/files/19965199/Doc1_cropped.1.pdf)


        * 58.4% of books were published after 1950.
       
    * **Price Analysis:**
        * The most expensive book is "Proactive system-worthy orchestration" (Book_ID: 340), priced at 49.98. The currency for book prices is not specified in the dataset.
        * The average book price is 27.37.
    * **Stock Levels:**
        * The book with the lowest stock is "Networked systemic implementation" (Book_ID: 44) with 0 units in stock. This book requires restocking if there is continued demand.
##   Customer Analysis

  * **Customer Retention:**
    * 98.8% of customers are repeat customers, having placed orders in multiple months (494 out of 500). This indicates a very high level of customer loyalty.
  * **Customer Lifetime Value:**
       * The customer with the highest lifetime value is Kim Turner (Customer_ID: 457) with a total spending of 1398.90 (currency unspecified). This represents the total amount spent by this customer across all their orders.
##   Order Analysis

  * **Total Revenue:**
        * The total revenue generated from all orders is 75628.66 (currency unspecified). This represents the sum of all sales in the bookstore.
  * **Most Frequently Ordered Book:**
        * The most frequently ordered book is "Robust tangible hardware" (Book_ID: 88), ordered 4 times.
  * **Monthly Sales Trend:**
  * * **Monthly Sales Trend:**
    * This section presents the monthly sales revenue trend, providing insights into sales performance over time.
    * **Overall Trend:**
        * Sales show a mix of increases and decreases, suggesting no clear linear trend but rather potential cyclical patterns.
    * **Peak Sales:**
        * May 2023: 5110.81
        * January 2024: 4904.57
    * **Lowest Sales:**
        * June 2023: 1943.88
        * December 2024: 865.58 (Significant drop - further investigation needed)
    * **Year-over-Year Analysis:**
        * December:
            * 2022: 2513.36
            * 2023: 2219.92
            * 2024: 865.58 (Strong downward trend)
    * **Significant Changes:**
        * The most notable change is the sharp decrease in sales in December 2024, which warrants further investigation to understand the cause.
     
      [Doc1 sales monthly_cropped (1).pdf](https://github.com/user-attachments/files/19965189/Doc1.sales.monthly_cropped.1.pdf)

  * **Average Order Value:**
    * The average order value was calculated by dividing the total revenue (75628.66) by the total number of orders (500).
    * The result is 151.26.

##   Key Insights

  * **Genre Sales:** Mystery is the top-selling genre, with 504 books sold, followed by Science Fiction (447) and Fantasy (446). Fiction is the lowest-selling genre (225).
  * **Customer Spending:** * **Customer Spending:** Customers who spent over 150 are located in key global cities, including New York, London, Tokyo, and Sydney. This indicates that our higher-value customers are geographically diverse.
  * **Stock Management:**
    * The current stock remaining for each book after fulfilling all orders is shown in the stock data.
    * The following books are currently out of stock (remaining quantity = 0):
        * "Networked systemic implementation" (Book ID: 44)
        * "Robust eco-centric capacity" (Book ID: 60)
        * ... (List a few important ones)
    * Low stock levels (less than 5 units) were observed for:
        * "Configurable modular throughput" (Book ID: 1)
        * "Configurable fault-tolerant interface" (Book ID: 199)
    * This information is essential for prioritizing restocking efforts.
      
##   Index Optimization

  * **Index Optimization:**
    * To enhance the efficiency of retrieving order information for specific customers, an index named `idx_orders_customer_id` was added to the `Customer_ID` column of the `Orders` table. This optimization speeds up queries that filter or search based on customer.
      
##   How to Use

1. **Database Setup:**
    * **Install a SQL Database System:** You'll need a SQL database system installed on your computer (e.g., MySQL, PostgreSQL, SQL Server, SQLite). If you don't have one, download and install one of these.
    * **Create the Database:**
        * Open your SQL database system's client or command-line interface.
        * Execute the following SQL command to create the database:
            ```sql
            CREATE DATABASE OnlineBookstore;
            ```
        * Then, select the database:
            ```sql
            USE OnlineBookstore; -- Or equivalent command
            ```
    * **Create the Tables:**
        * Copy the `CREATE TABLE` statements from your SQL file.
        * Paste them into your SQL client and execute them. This will create the `Books`, `Customers`, and `Orders` tables.
    * **Import the Data:**
        * This step depends on how your data is provided. If you have a separate data file (e.g., CSV), you'll need to use your database system's import tool or write `INSERT INTO` statements to load the data into the tables.
        * If the `INSERT INTO` statements are in your SQL file, simply execute them after creating the tables.
    2.  **Running Queries:**
        2.  **Running Queries:**
    * Connect to the `OnlineBookstore` database using your SQL client.
    * You can execute the provided `SELECT` queries to retrieve information from the database. For example:
        * To get all books:
            ```sql
            SELECT * FROM Books;
            ```
        * To find customers from a specific city:
            ```sql
            SELECT * FROM Customers WHERE City = '\[City Name]';
            ```
    * Feel free to modify these queries or write your own to analyze the data in different ways.
**Important Notes:**

* **Replace Placeholders:** You MUST replace the bracketed placeholders (e.g., `\[Number]`, `\[Book Title]`, `\[Amount]`) with the actual values obtained by running the SQL queries. I can't execute the queries myself; you need to do that within your SQL environment.
* **Data Import:** This README assumes that you have a way to import data into the tables. The SQL file only provides the table structure.
* **Further Analysis:** The provided queries are a starting point. You can extend them to perform more in-depth analysis based on your specific needs.
* **Visualization:** Consider adding charts or graphs (outside of the README itself) to visually represent the data and insights.
 
This README provides a comprehensive overview of your SQL project, presenting the key findings in a clear and concise manner. Remember to fill in the placeholders with the actual data!
