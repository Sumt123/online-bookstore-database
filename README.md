#   Online Bookstore Database Analysis
    This project presents a comprehensive SQL database solution for managing an online bookstore, alongside an in-depth analysis of its operational data. It demonstrates proficiency in database design, SQL querying for business intelligence, and the extraction of actionable insights from transactional data.

**Author:** Sumit Yadav
**GitHub:** [https://github.com/sumit123](https://github.com/sumit123)
**LinkedIn:** [https://www.linkedin.com/in/sumit-yadav-888a14284](https://www.linkedin.com/in/sumit-yadav-888a14284)

## Project Overview & Objectives
   This SQL project simulates a real-world online bookstore environment, providing a scalable and efficient database foundation for managing books, customers, and orders. My primary objective was to:
**Design and implement a relational database** (using SQL) that accurately models bookstore operations.
**Perform complex data retrieval and manipulation** to extract meaningful business intelligence.
**Translate raw data into actionable insights** for critical areas like sales performance, customer behavior, and inventory management.
**Demonstrate proficiency in advanced SQL concepts** relevant to Data Analyst, Business Analyst, and SQL Developer roles.
   
* **Target Audience:** This project is designed to showcase my skills to potential employers, particularly hiring managers and recruiters for Data Analyst, SQL Developer, or Business Intelligence roles. It highlights my ability to translate business requirements into database solutions and derive actionable insights from structured data.

##   Database Summary

 * **Total Books:** 500 unique titles.
 * **Total Customers:** 500 registered customers.
 * **Total Orders:** 500 completed orders.

##   Database Schema

   ## The database consists of the following tables:

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

   ## Key SQL Analysis & Business Insights
    This section highlights critical business insights derived from the database using advanced SQL queries, providing a strategic look into sales performance, customer 
 behavior, and inventory management. All insights were extracted using complex SQL queries involving joins, aggregations, and conditional logic.

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

     **Recommendation:** Prioritize marketing and procurement efforts on high-performing genres like Mystery and Science Fiction. Reassess inventory and promotional strategies for lower-selling genres like Fiction to optimize stock turnover and revenue.

     **SQL Used:** COUNT() distinct customers, JOIN Customers and Orders, GROUP BY Customer_ID, HAVING COUNT(DISTINCT MONTH(Order_Date)) > 1.
    
##   Customer Analysis

  * **Customer Retention:**
    * 98.8% of customers are repeat customers, having placed orders in multiple months (494 out of 500). This indicates a very high level of customer loyalty.

    **Recommendation:** Capitalize on this strong loyalty by implementing advanced loyalty programs or targeted promotions (e.g., exclusive discounts on future purchases) for repeat customers to further boost engagement and lifetime value.
    
  * **Customer Lifetime Value:**
       * The customer with the highest lifetime value is Kim Turner (Customer_ID: 457) with a total spending of 1398.90$. This represents the total amount spent by this customer across all their orders. High-value customers (those who spent over ₹150) are geographically diverse, located in key global cities including New York, London, Tokyo, and Sydney.

   **Recommendation:** Develop personalized marketing campaigns for these high-value segments, potentially tailoring offers based on their purchasing history or 
geographical location to maximize their lifetime value.   

  **SQL Used:** SUM() for Total_Amount, GROUP BY Customer_ID for lifetime value, JOIN with Customers table to get demographic info, ORDER BY for ranking, WHERE clause for filtering.
   
       
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
        * May 2023: 5110.81$
        * January 2024: 4904.57$
  * **Lowest Sales:**
        * June 2023: 1943.88$
        * December 2024: 865.58$ (Significant drop - further investigation needed)
  * **Year-over-Year Analysis:**
        * December:
            * 2022: 2513.36$
            * 2023: 2219.92$
            * 2024: 865.58$ (Strong downward trend)
  * **Significant Changes:**
        * The most notable change is the sharp decrease in sales in December 2024, which warrants further investigation to understand the cause.
    
    **SQL Used:** Date functions, GROUP BY month/year, SUM() for sales, possibly LAG() for year-over-year comparison if doing advanced trend analysis.
     
      [Doc1 sales monthly_cropped (1).pdf](https://github.com/user-attachments/files/19965189/Doc1.sales.monthly_cropped.1.pdf)

  * **Average Order Value:**
    * The average order value was calculated by dividing the total revenue (75628.66$) by the total number of orders (500).
    * The result is 151.26$.

##   Key Insights

  * **Genre Sales:** Mystery is the top-selling genre, with 504 books sold, followed by Science Fiction (447) and Fantasy (446). Fiction is the lowest-selling genre (225).
  * **Customer Spending:**  Customers who spent over 150$ are located in key global cities, including New York, London, Tokyo, and Sydney. This indicates that our higher-value customers are geographically diverse.
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

  **Query Performance Enhancement:**  To significantly enhance the efficiency of retrieving order information for specific customers, an index named idx_orders_customer_id 
    was added to the Customer_ID column of the Orders table. This optimization speeds up queries that filter or search based on customer ID, directly improving overall 
    database performance for customer-centric analysis.
    
   **SQL Used:** CREATE INDEX statement.
      
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
