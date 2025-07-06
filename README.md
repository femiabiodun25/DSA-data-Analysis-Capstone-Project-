# DSA-data-Analysis-Capstone-Project-documentation

## Project Title 
Data analysis project on kultra mega stores inventory And Amazon Products Review Analysis 

##Tools used 
- Sql server for Query
- .ms excel for data cleaning and visaulization 
## Data Analysis

``` SQL Query 

create database DSA_project
select *from [dbo].[KMS Sql Case Study(AutoRecovered)]

-----product category with highestsales?---

select product_category,sum(sales) as highestsales
from [dbo].[KMS Sql Case Study(AutoRecovered)]
group by product_category
order by highestsales desc

----top3 AND BOTTOM 3 REGION BY SALES----
SELECT TOP 3 REGION,SUM(SALES) AS SALES
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
GROUP BY REGION
ORDER BY SALES DESC

SELECT TOP 3 REGION,SUM(SALES) AS SALES
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
GROUP BY REGION
ORDER BY SALES ASC

---TOTAL SALES APPLICANT IN ONTARIO---

SELECT REGION,SUM(SALES) AS TOTALSALES
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
WHERE PRODUCT_SUB_CATEGORY='APPLIANCES'
AND REGION='ONTARIO' 
GROUP BY REGION 

select top 10 
	CUSTOMER_NAME, count(ORDER_ID) as totalorders, sum(sales) as totalsales,
	(select max(customer_segment) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as SegDetails,
	(select max(REGION) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as RegDetails
	from [dbo].[KMS Sql Case Study(AutoRecovered)]
	group by CUSTOMER_NAME
	ORDER BY TOTALSALES ASC

	---order by totalsales WHICH SHIPPING METHOD INCURE THE MOST SHIPPING COST---

	SELECT TOP 3 SHIP_MODE,
	SUM(SHIPPING_COST) AS TOTAL_SHIP_COST
	FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
	GROUP BY SHIP_MODE
	ORDER BY TOTAL_SHIP_COST DESC

	-----WHO IS TGHE MOST VALUABLE CUSTOMER WHAT PRODUCT OR SERVICE DID THEY BU
Select top 3
	CUSTOMER_NAME, sum(sales) as totalsales,
	(select max(PRODUCT_SUB_CATEGORY) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as PRODUCT_SUB_CATEGORY,
	(select max(PRODUCT_NAME) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as PRODUCT_DETAILS
	from [dbo].[KMS Sql Case Study(AutoRecovered)]
	group by CUSTOMER_NAME
	ORDER BY TOTALSALES ASC

	----SMALL BUSINESS WITH THE HIGHEST SALES----

	SELECT TOP 3 CUSTOMER_NAME,CUSTOMER_SEGMENT,
	SUM(SALES) AS TOTALSALES 
	FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
	WHERE CUSTOMER_SEGMENT='SMALL BUSINESS'
	GROUP BY CUSTOMER_NAME,CUSTOMER_SEGMENT 
	ORDER BY TOTALSALES

------CORPORATE CUSTOMER WITH MOST ORDER 2009-2012-----

SELECT TOP 10 
CUSTOMER_NAME,CUSTOMER_SEGMENT,ORDER_DATE,
COUNT(DISTINCT ORDER_ID) AS TOTALORDERS
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
WHERE CUSTOMER_SEGMENT ='CORPORATE'
AND ORDER_DATE BETWEEN '2009-01-01' AND '2012-12-31'
GROUP BY CUSTOMER_NAME,CUSTOMER_SEGMENT,ORDER_DATE
ORDER BY TOTALORDERS DESC

-----CONSUMER CUSTOMER WITH THE HIGHEST PROFIT----

SELECT TOP 1 
CUSTOMER_NAME,CUSTOMER_SEGMENT,
SUM(PROFIT) AS TOTAL_PROFIT
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
WHERE CUSTOMER_SEGMENT ='CONSUMER'
GROUP BY CUSTOMER_NAME,CUSTOMER_SEGMENT 
ORDER BY TOTAL_PROFIT DESC


-----CUSTOMER WHO RETURNED ITEMS AND WHAT SEGMENT THEY BELONG TO----

select  DISTINCT [dbo].[KMS Sql Case Study(AutoRecovered)].Order_ID, 	
			 [dbo].[KMS Sql Case Study(AutoRecovered)].Customer_Name,	
			[dbo].[KMS Sql Case Study(AutoRecovered)] .Customer_Segment,		
			[dbo].[Order_Status].[Status]
from [dbo].[KMS Sql Case Study(AutoRecovered)]
inner join [dbo].[Order_Status]
on [dbo].[Order_Status].Order_ID =[dbo].[KMS Sql Case Study(AutoRecovered)].Order_ID

SELECT *FROM [dbo].[Order_Status]



SELECT order_priority, ship_mode,
		count(Order_ID) as TotalOrder,
		round(sum(sales - profit),2) as [Estimated shipping Cost],
		avg(datediff(day,[order_date],[ship_date])) as avgshipdays
from [dbo].[KMS Sql Case Study(AutoRecovered)]
group by  order_priority, ship_mode
order by   order_priority, ship_mode desc;create database DSA_project
select *from [dbo].[KMS Sql Case Study(AutoRecovered)]

-----product category with highestsales?---

select product_category,sum(sales) as highestsales
from [dbo].[KMS Sql Case Study(AutoRecovered)]
group by product_category
order by highestsales desc

----top3 AND BOTTOM 3 REGION BY SALES----
SELECT TOP 3 REGION,SUM(SALES) AS SALES
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
GROUP BY REGION
ORDER BY SALES DESC

SELECT TOP 3 REGION,SUM(SALES) AS SALES
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
GROUP BY REGION
ORDER BY SALES ASC

---TOTAL SALES APPLICANT IN ONTARIO---

SELECT REGION,SUM(SALES) AS TOTALSALES
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
WHERE PRODUCT_SUB_CATEGORY='APPLIANCES'
AND REGION='ONTARIO' 
GROUP BY REGION 

select top 10 
	CUSTOMER_NAME, count(ORDER_ID) as totalorders, sum(sales) as totalsales,
	(select max(customer_segment) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as SegDetails,
	(select max(REGION) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as RegDetails
	from [dbo].[KMS Sql Case Study(AutoRecovered)]
	group by CUSTOMER_NAME
	ORDER BY TOTALSALES ASC

	---order by totalsales WHICH SHIPPING METHOD INCURE THE MOST SHIPPING COST---

	SELECT TOP 3 SHIP_MODE,
	SUM(SHIPPING_COST) AS TOTAL_SHIP_COST
	FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
	GROUP BY SHIP_MODE
	ORDER BY TOTAL_SHIP_COST DESC

	-----WHO IS TGHE MOST VALUABLE CUSTOMER WHAT PRODUCT OR SERVICE DID THEY BU
Select top 3
	CUSTOMER_NAME, sum(sales) as totalsales,
	(select max(PRODUCT_SUB_CATEGORY) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as PRODUCT_SUB_CATEGORY,
	(select max(PRODUCT_NAME) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as PRODUCT_DETAILS
	from [dbo].[KMS Sql Case Study(AutoRecovered)]
	group by CUSTOMER_NAME
	ORDER BY TOTALSALES ASC

	----SMALL BUSINESS WITH THE HIGHEST SALES----

	SELECT TOP 3 CUSTOMER_NAME,CUSTOMER_SEGMENT,
	SUM(SALES) AS TOTALSALES 
	FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
	WHERE CUSTOMER_SEGMENT='SMALL BUSINESS'
	GROUP BY CUSTOMER_NAME,CUSTOMER_SEGMENT 
	ORDER BY TOTALSALES

------CORPORATE CUSTOMER WITH MOST ORDER 2009-2012-----

SELECT TOP 10 
CUSTOMER_NAME,CUSTOMER_SEGMENT,ORDER_DATE,
COUNT(DISTINCT ORDER_ID) AS TOTALORDERS
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
WHERE CUSTOMER_SEGMENT ='CORPORATE'
AND ORDER_DATE BETWEEN '2009-01-01' AND '2012-12-31'
GROUP BY CUSTOMER_NAME,CUSTOMER_SEGMENT,ORDER_DATE
ORDER BY TOTALORDERS DESC

-----CONSUMER CUSTOMER WITH THE HIGHEST PROFIT----

SELECT TOP 1 
CUSTOMER_NAME,CUSTOMER_SEGMENT,
SUM(PROFIT) AS TOTAL_PROFIT
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
WHERE CUSTOMER_SEGMENT ='CONSUMER'
GROUP BY CUSTOMER_NAME,CUSTOMER_SEGMENT 
ORDER BY TOTAL_PROFIT DESC


-----CUSTOMER WHO RETURNED ITEMS AND WHAT SEGMENT THEY BELONG TO----

select  DISTINCT [dbo].[KMS Sql Case Study(AutoRecovered)].Order_ID, 	
			 [dbo].[KMS Sql Case Study(AutoRecovered)].Customer_Name,	
			[dbo].[KMS Sql Case Study(AutoRecovered)] .Customer_Segment,		
			[dbo].[Order_Status].[Status]
from [dbo].[KMS Sql Case Study(AutoRecovered)]
inner join [dbo].[Order_Status]
on [dbo].[Order_Status].Order_ID =[dbo].[KMS Sql Case Study(AutoRecovered)].Order_ID

SELECT *FROM [dbo].[Order_Status]



SELECT order_priority, ship_mode,
		count(Order_ID) as TotalOrder,
		round(sum(sales - profit),2) as [Estimated shipping Cost],
		avg(datediff(day,[order_date],[ship_date])) as avgshipdays
from [dbo].[KMS Sql Case Study(AutoRecovered)]
group by  order_priority, ship_mode
order by   order_priority, ship_mode desc;create database DSA_project
select *from [dbo].[KMS Sql Case Study(AutoRecovered)]

-----product category with highestsales?---

select product_category,sum(sales) as highestsales
from [dbo].[KMS Sql Case Study(AutoRecovered)]
group by product_category
order by highestsales desc

----top3 AND BOTTOM 3 REGION BY SALES----
SELECT TOP 3 REGION,SUM(SALES) AS SALES
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
GROUP BY REGION
ORDER BY SALES DESC

SELECT TOP 3 REGION,SUM(SALES) AS SALES
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
GROUP BY REGION
ORDER BY SALES ASC

---TOTAL SALES APPLICANT IN ONTARIO---

SELECT REGION,SUM(SALES) AS TOTALSALES
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
WHERE PRODUCT_SUB_CATEGORY='APPLIANCES'
AND REGION='ONTARIO' 
GROUP BY REGION 

select top 10 
	CUSTOMER_NAME, count(ORDER_ID) as totalorders, sum(sales) as totalsales,
	(select max(customer_segment) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as SegDetails,
	(select max(REGION) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as RegDetails
	from [dbo].[KMS Sql Case Study(AutoRecovered)]
	group by CUSTOMER_NAME
	ORDER BY TOTALSALES ASC

	---order by totalsales WHICH SHIPPING METHOD INCURE THE MOST SHIPPING COST---

	SELECT TOP 3 SHIP_MODE,
	SUM(SHIPPING_COST) AS TOTAL_SHIP_COST
	FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
	GROUP BY SHIP_MODE
	ORDER BY TOTAL_SHIP_COST DESC

	-----WHO IS TGHE MOST VALUABLE CUSTOMER WHAT PRODUCT OR SERVICE DID THEY BU
Select top 3
	CUSTOMER_NAME, sum(sales) as totalsales,
	(select max(PRODUCT_SUB_CATEGORY) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as PRODUCT_SUB_CATEGORY,
	(select max(PRODUCT_NAME) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as PRODUCT_DETAILS
	from [dbo].[KMS Sql Case Study(AutoRecovered)]
	group by CUSTOMER_NAME
	ORDER BY TOTALSALES ASC

	----SMALL BUSINESS WITH THE HIGHEST SALES----

	SELECT TOP 3 CUSTOMER_NAME,CUSTOMER_SEGMENT,
	SUM(SALES) AS TOTALSALES 
	FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
	WHERE CUSTOMER_SEGMENT='SMALL BUSINESS'
	GROUP BY CUSTOMER_NAME,CUSTOMER_SEGMENT 
	ORDER BY TOTALSALES

------CORPORATE CUSTOMER WITH MOST ORDER 2009-2012-----

SELECT TOP 10 
CUSTOMER_NAME,CUSTOMER_SEGMENT,ORDER_DATE,
COUNT(DISTINCT ORDER_ID) AS TOTALORDERS
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
WHERE CUSTOMER_SEGMENT ='CORPORATE'
AND ORDER_DATE BETWEEN '2009-01-01' AND '2012-12-31'
GROUP BY CUSTOMER_NAME,CUSTOMER_SEGMENT,ORDER_DATE
ORDER BY TOTALORDERS DESC

-----CONSUMER CUSTOMER WITH THE HIGHEST PROFIT----

SELECT TOP 1 
CUSTOMER_NAME,CUSTOMER_SEGMENT,
SUM(PROFIT) AS TOTAL_PROFIT
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
WHERE CUSTOMER_SEGMENT ='CONSUMER'
GROUP BY CUSTOMER_NAME,CUSTOMER_SEGMENT 
ORDER BY TOTAL_PROFIT DESC


-----CUSTOMER WHO RETURNED ITEMS AND WHAT SEGMENT THEY BELONG TO----

select  DISTINCT [dbo].[KMS Sql Case Study(AutoRecovered)].Order_ID, 	
			 [dbo].[KMS Sql Case Study(AutoRecovered)].Customer_Name,	
			[dbo].[KMS Sql Case Study(AutoRecovered)] .Customer_Segment,		
			[dbo].[Order_Status].[Status]
from [dbo].[KMS Sql Case Study(AutoRecovered)]
inner join [dbo].[Order_Status]
on [dbo].[Order_Status].Order_ID =[dbo].[KMS Sql Case Study(AutoRecovered)].Order_ID

SELECT *FROM [dbo].[Order_Status]



SELECT order_priority, ship_mode,
		count(Order_ID) as TotalOrder,
		round(sum(sales - profit),2) as [Estimated shipping Cost],
		avg(datediff(day,[order_date],[ship_date])) as avgshipdays
from [dbo].[KMS Sql Case Study(AutoRecovered)]
group by  order_priority, ship_mode
order by   order_priority, ship_mode desc;create database DSA_project
select *from [dbo].[KMS Sql Case Study(AutoRecovered)]

-----product category with highestsales?---

select product_category,sum(sales) as highestsales
from [dbo].[KMS Sql Case Study(AutoRecovered)]
group by product_category
order by highestsales desc

----top3 AND BOTTOM 3 REGION BY SALES----
SELECT TOP 3 REGION,SUM(SALES) AS SALES
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
GROUP BY REGION
ORDER BY SALES DESC

SELECT TOP 3 REGION,SUM(SALES) AS SALES
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
GROUP BY REGION
ORDER BY SALES ASC

---TOTAL SALES APPLICANT IN ONTARIO---

SELECT REGION,SUM(SALES) AS TOTALSALES
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
WHERE PRODUCT_SUB_CATEGORY='APPLIANCES'
AND REGION='ONTARIO' 
GROUP BY REGION 

select top 10 
	CUSTOMER_NAME, count(ORDER_ID) as totalorders, sum(sales) as totalsales,
	(select max(customer_segment) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as SegDetails,
	(select max(REGION) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as RegDetails
	from [dbo].[KMS Sql Case Study(AutoRecovered)]
	group by CUSTOMER_NAME
	ORDER BY TOTALSALES ASC

	---order by totalsales WHICH SHIPPING METHOD INCURE THE MOST SHIPPING COST---

	SELECT TOP 3 SHIP_MODE,
	SUM(SHIPPING_COST) AS TOTAL_SHIP_COST
	FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
	GROUP BY SHIP_MODE
	ORDER BY TOTAL_SHIP_COST DESC

	-----WHO IS TGHE MOST VALUABLE CUSTOMER WHAT PRODUCT OR SERVICE DID THEY BU
Select top 3
	CUSTOMER_NAME, sum(sales) as totalsales,
	(select max(PRODUCT_SUB_CATEGORY) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as PRODUCT_SUB_CATEGORY,
	(select max(PRODUCT_NAME) from [dbo].[KMS Sql Case Study(AutoRecovered)]) as PRODUCT_DETAILS
	from [dbo].[KMS Sql Case Study(AutoRecovered)]
	group by CUSTOMER_NAME
	ORDER BY TOTALSALES ASC

	----SMALL BUSINESS WITH THE HIGHEST SALES----

	SELECT TOP 3 CUSTOMER_NAME,CUSTOMER_SEGMENT,
	SUM(SALES) AS TOTALSALES 
	FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
	WHERE CUSTOMER_SEGMENT='SMALL BUSINESS'
	GROUP BY CUSTOMER_NAME,CUSTOMER_SEGMENT 
	ORDER BY TOTALSALES

------CORPORATE CUSTOMER WITH MOST ORDER 2009-2012-----

SELECT TOP 10 
CUSTOMER_NAME,CUSTOMER_SEGMENT,ORDER_DATE,
COUNT(DISTINCT ORDER_ID) AS TOTALORDERS
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
WHERE CUSTOMER_SEGMENT ='CORPORATE'
AND ORDER_DATE BETWEEN '2009-01-01' AND '2012-12-31'
GROUP BY CUSTOMER_NAME,CUSTOMER_SEGMENT,ORDER_DATE
ORDER BY TOTALORDERS DESC

-----CONSUMER CUSTOMER WITH THE HIGHEST PROFIT----

SELECT TOP 1 
CUSTOMER_NAME,CUSTOMER_SEGMENT,
SUM(PROFIT) AS TOTAL_PROFIT
FROM [dbo].[KMS Sql Case Study(AutoRecovered)]
WHERE CUSTOMER_SEGMENT ='CONSUMER'
GROUP BY CUSTOMER_NAME,CUSTOMER_SEGMENT 
ORDER BY TOTAL_PROFIT DESC


-----CUSTOMER WHO RETURNED ITEMS AND WHAT SEGMENT THEY BELONG TO----

select  DISTINCT [dbo].[KMS Sql Case Study(AutoRecovered)].Order_ID, 	
			 [dbo].[KMS Sql Case Study(AutoRecovered)].Customer_Name,	
			[dbo].[KMS Sql Case Study(AutoRecovered)] .Customer_Segment,		
			[dbo].[Order_Status].[Status]
from [dbo].[KMS Sql Case Study(AutoRecovered)]
inner join [dbo].[Order_Status]
on [dbo].[Order_Status].Order_ID =[dbo].[KMS Sql Case Study(AutoRecovered)].Order_ID

SELECT *FROM [dbo].[Order_Status]



SELECT order_priority, ship_mode,
		count(Order_ID) as TotalOrder,
		round(sum(sales - profit),2) as [Estimated shipping Cost],
		avg(datediff(day,[order_date],[ship_date])) as avgshipdays
from [dbo].[KMS Sql Case Study(AutoRecovered)]
group by  order_priority, ship_mode
order by   order_priority, ship_mode desc;
```




