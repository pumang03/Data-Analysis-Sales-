# Data-Analysis-Sales-
VISUALISATION OF SALES DATASETS USING MS POWER BI:

Instructions to setup MySQL on your local computer:
1.Follow step in this video to install MySQL on your local computer https://www.youtube.com/watch?v=WuBcTJnIuzo

Steps performed:
1.Download the file Data.sql to your local computer and perform load operation on it, to load in the MySQL environment.

2.Data.sql contains 5 tables under sales schema: Customers,Date,Markets,Products,Transactions

3.Perform some Query Operations mentioned below.

4.Select Different Table and perform Cleaning operations as some of the table contains outliers.

5.Download MS Power BI Desktop from Microsoft store.

6.MS Power BI UI appears ,Click on Get Data->more to connect with the sales database, select database -> MYSQL database -> connect

7.Their appear a server and database, Here you have to enter server:localhost(database running on your local machine) database:sales(name of your database).

8.After you connect with the database you will see all the 5 tables in your navigator.

9.Select all your table and load it.Here Power BI connecting with MYSQL pulling all the records into Power BI environment from these table.

10.Now we will use Power Query to transform the data(formatting).

11.For the above process select the table you want to transform and click on the transform data at the top. Transform data will launch a Power Query editor where you will be able to Transform/Munging/Wrangling the data or ETL(Extract,Transform,Load).
     
NOTE: These changes will not reflect in your database.It will only be present in your Power Query.

 






LOAD OPERATION(Loading The Data Into Workbench):
1.Open MySQL Workbench->Server->Data Import -> check “Import From Self-Contained File”-> Select your file (Data.sql) from where you have downloaded->Start Import->Sales Database created at top left schema section.

NOTE: If you don’t see your Sales schema then refresh workbench.


QUERY DIFFERENT TABLES:
Show all customer records
SELECT * FROM customers;


Show total number of customers
SELECT count(*) FROM customers;


Show transactions for Chennai market (market code for Chennai is Mark001)
SELECT * FROM transactions where market_code='Mark001';


Show distinct product codes that were sold in Chennai
SELECT distinct product_code FROM transactions where market_code='Mark001';


Show transactions where currency is US dollars
SELECT * from transactions where currency="USD"


Show transactions in 2020 join by date table
SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;


Show total revenue in year 2020
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";


Show total revenue in year 2020, January Month.
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");


Show total revenue in year 2020 in Chennai
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";

